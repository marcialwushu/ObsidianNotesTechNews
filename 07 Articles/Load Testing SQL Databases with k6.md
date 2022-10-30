---
link: {{link}}
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
date: July 24, 2022 (Sun)
---
# Highlights
{{highlights}}

---
# Load Testing SQL Databases with k6
This short tutorial shows how to run a k6 test for load testing a database.

In performance testing, we often trigger load tests that simulate realistic user flows, particularly those that are most commonly seen in production. This type of acceptance testing usually interacts with various parts of our infrastructure: web servers, microservices, databases, etc.

But what if you want to test the performance or scalability of an infrastructure resource in isolation?

In many cases, internal components use custom protocols, and the testing tool needs to support those protocols to test the resource individually. Luckily, with k6, you can use or create [extensions](https://k6.io/docs/ecosystem/) that allow you to test different protocols, such as ZMTQ, SQL, Avro, MLLP, etc.

One of the components that you might want to test separately is the database. Databases play an essential role in the performance of our applications, and they can be the bottleneck when experiencing a high volume of users.

Load testing the database directly could provide you with better insights about the database performance in advance. As a result, you could thoroughly plan out your database architecture and determine how to scale it properly.

In this tutorial, let’s explore how to load test a database using the [xk6-sql extension](https://github.com/grafana/xk6-sql). For simplicity, the tests will be executed using SQLite3 but the extension supports the following relational databases:

-   PostgreSQL
-   MySQL
-   SQLite3
-   Microsoft SQL Server

## Build

In this section, you will install all the required components and build a k6 binary for SQL.

### Install the C Compiler for SQLite3

A C compiler is required if you are using SQLite3. Simply install the build-essential package if you are using Debian-based operating system. For Windows users, download the [tdm-gcc compiler](https://jmeubank.github.io/tdm-gcc/), extract it and place it in any directory that you prefer. Then, add the path of the bin folder to Environment Variable as follows:

  [![Edit System Variable](https://k6.io/blog/static/8e3f6a0828309e589636541443458f1e/7842b/windows-edit-system-variable.png "Edit System Variable")](https://k6.io/blog/static/8e3f6a0828309e589636541443458f1e/e4a89/windows-edit-system-variable.png)

### Install the Golang Toolchain

Head over to Golang’s installation page and download the installer based on the operating system of your machine. Once you have installed, run the following command to verify the version.

You should get information related the version number of Go as well as your system architecture:

```
go version go1.16.4 windows/amd64
```

### Build the k6 binary including the SQL extension

For non-SQLite database, run the following command to build the k6 binary:

```
xk6 build master --with github.com/grafana/xk6-sql
```

You need to set CGO\_ENABLED to 1 when building for SQLite3 to ensure that C compiler is used:

```
CGO_ENABLED=1 xk6 build master --with github.com/grafana/xk6-sql
```

On Windows platform, you need set it explicitly, using set first to call the build command:

```
set CGO_ENABLED=1xk6 build master --with github.com/grafana/xk6-sql
```

You should see the following output on your console:

```
2021/06/17 14:29:43 [INFO] Temporary folder: C:\Users\wfng\AppData\Local\Temp\buildenv_2021-06-17-1429.3590000392021/06/17 14:29:43 [INFO] Writing main module: C:\Users\wfng\AppData\Local\Temp\buildenv_2021-06-17-1429.359000039\main.go2021/06/17 14:29:43 [INFO] Initializing Go module2021/06/17 14:29:43 [INFO] exec (timeout=10s): C:\Program Files\Go\bin\go.exe mod init k6go: creating new go.mod: module k6go: to add module requirements and sums:        go mod tidy2021/06/17 14:29:44 [INFO] Pinning versions2021/06/17 14:29:44 [INFO] exec (timeout=0s): C:\Program Files\Go\bin\go.exe get -d -v go.k6.io/k6@mastergo: downloading go.k6.io/k6 v0.32.1-0.20210616133500-9f3dd60fbdc1go get: added go.k6.io/k6 v0.32.1-0.20210616133500-9f3dd60fbdc12021/06/17 14:30:50 [INFO] exec (timeout=0s): C:\Program Files\Go\bin\go.exe get -d -v github.com/grafana/xk6-sqlgo get: added github.com/grafana/xk6-sql v0.0.0-20210517160107-d222ad8b93eb2021/06/17 14:30:52 [INFO] Build environment ready2021/06/17 14:30:52 [INFO] Building k62021/06/17 14:30:52 [INFO] exec (timeout=0s): C:\Program Files\Go\bin\go.exe mod tidy2021/06/17 14:30:56 [INFO] exec (timeout=0s): C:\Program Files\Go\bin\go.exe build -o C:\Users\wfng\Documents\k6_test\k6.exe -ldflags -w -s -trimpath2021/06/17 14:31:15 [INFO] Build complete: .\k6.exe2021/06/17 14:31:15 [INFO] Cleaning up temporary folder: C:\Users\wfng\AppData\Local\Temp\buildenv_2021-06-17-1429.359000039
```

After that, you should have a new k6 binary in your working directory. Since I am building on the Windows platform, I got the k6.exe executable file.

## k6 Script

You need to write a JavaScript file in order to perform load testing with k6. Let’s have a look at an example of a simple test script for load testing API via HTTP:

```
import http from 'k6/http';import { sleep } from 'k6';export default function () {  http.get('https://test.k6.io');  sleep(1);}
```

Each test script requires a default function which will be executed over and over again during testing. The script above makes a GET call to our own k6 test API and sleeps for a second on each execution for a single VU.

For load testing a database, all you need to do is to import the SQL module that you have created earlier and write the corresponding code inside the default function.

Create a new JavaScript file called script.js in the same directory as your k6 binary file.

### Import SQL module

You can import your newly created SQL module by adding this line to script.js:

```
import sql from 'k6/x/sql';
```

The naming is based on what has been defined in the [Go file](https://github.com/grafana/xk6-sql/blob/master/sql.go). In this case, it is defined as k6/x/sql.

### Connect to database

You can easily connect to your database by calling the sql.open function:

```
const db = sql.open('sqlite3', './test.db');
```

It accepts two input parameters:

-   type - the type of database (mysql, postgres, sqlite3, sqlserver)
-   name - the name of the database

### Setup and Teardown the database

Before executing a SQL command, let’s explore a little more about the [k6 test life cycle](https://k6.io/docs/using-k6/test-life-cycle/). It typically follows this structure:

```
// 1. init code (call once per VU)export function setup() {  // 2. setup code (call once at the beginning of test)}export default function (data) {  // 3. VU code}export function teardown(data) {  // 4. teardown code (call once at the end of test)}
```

You can add in any init code right before the setup, default function and teardown. Init code serves as the initialization and will be called once for each virtual user (VU).

Also, you can specify a setup function which is called once at the beginning of the test where VU is 0. On the other hand, teardown is called once at the end of the test.

As explained earlier, the default function serves as the VU code which will be executed continuously during testing.

**Execute SQL command**

After connecting to the database, you can use the db object and call the exec to run any SQL command.

For example, as part of the setup process, before the “load” runs, you can create a new table and insert a few rows of data into the table as follows:

```
export function setup() {  db.exec(`CREATE TABLE IF NOT EXISTS person (           id integer PRIMARY KEY AUTOINCREMENT,           email varchar NOT NULL,           first_name varchar,           last_name varchar);`);  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('johndoe@email.com', 'John', 'Doe');"  );  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('marysue@email.com', 'Mary', 'Sue');"  );  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('dorydoe@email.com', 'Dory', 'Doe');"  );}
```

And you should not forget to clean up the database at the end of the test with the teardown function. This example deletes the table and closes the database connection:

```
export function teardown() {  db.exec('DELETE FROM person;');  db.exec('DROP TABLE person;');  db.close();}
```

### Query data from database

You can easily query the output with the query function. Let’s use it as part of load testing to determine how many iterations you can get when querying the database:

```
export default function () {  const results = sql.query(db, 'SELECT * FROM person;');}
```

As usual, you can run the check statement to determine the output. Let’s do a simple check on the total rows of data in the database:

```
import sql from 'k6/x/sql';import { check } from 'k6';// additional...export default function () {  const results = sql.query(db, 'SELECT * FROM person;');  check(results, {    'is length 3': (r) => r.length === 3,  });}
```

The **complete script code** is as follows:

```
import sql from 'k6/x/sql';import { check } from 'k6';const db = sql.open('sqlite3', './test.db');export function setup() {  db.exec(`CREATE TABLE IF NOT EXISTS person (           id integer PRIMARY KEY AUTOINCREMENT,           email varchar NOT NULL,           first_name varchar,           last_name varchar);`);  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('johndoe@email.com', 'John', 'Doe');"  );  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('marysue@email.com', 'Mary', 'Sue');"  );  db.exec(    "INSERT INTO person (email, first_name, last_name) VALUES('dorydoe@email.com', 'Dory', 'Doe');"  );}export function teardown() {  db.exec('DELETE FROM person;');  db.exec('DROP TABLE person;');  db.close();}export default function () {  const results = sql.query(db, 'SELECT * FROM person;');  check(results, {    'is length 3': (r) => r.length === 3,  });}
```

## Running the test

Once we have the completed script, you can run the test. Let’s start running the load test for 5 seconds:

```
k6 run script.js --duration 5s
```

By default, it is using just one virtual user (VU) but you can modify it via \--vus flag. You should see the following output:

```
          /\      |‾‾| /‾‾/   /‾‾/     /\  /  \     |  |/  /   /  /    /  \/    \    |     (   /   ‾‾\   /          \   |  |\  \ |  (‾)  |  / __________ \  |__| \__\ \_____/ .io  execution: local     script: script.js     output: -  scenarios: (100.00%) 1 scenario, 1 max VUs, 35s max duration (incl. graceful stop):           * default: 1 looping VUs for 5s (gracefulStop: 30s)running (05.1s), 0/1 VUs, 34467 complete and 0 interrupted iterationsdefault ✓ [======================================] 1 VUs  5s     ✓ is length 3     █ setup     █ teardown     checks...............: 100.00% ✓ 34467       ✗ 0     data_received........: 0 B     0 B/s     data_sent............: 0 B     0 B/s     iteration_duration...: avg=143.57µs min=0s med=0s max=43.24ms p(90)=519.2µs p(95)=985.47µs     iterations...........: 34467   6812.032587/s     vus..................: 1       min=1         max=1     vus_max..............: 1       min=1         max=1
```

In this case, it shows that the database can handle about 6812 queries per second and average time of 144µs per iteration.

### Scale the load

In the previous test, you have specified just a single virtual user. Let’s scale it up to 10 and see how SQLite performs. Run the following command:

```
k6 run script.js --duration 5s --vus 10
```

You should get the following result:

```
running (05.1s), 00/10 VUs, 43228 complete and 0 interrupted iterationsdefault ✓ [======================================] 10 VUs  5s    ✓ is length 3    █ setup    █ teardown    checks...............: 100.00% ✓ 43228      ✗ 0    data_received........: 0 B  0 B/s    data_sent............: 0 B  0 B/s    iteration_duration...: avg=1.16ms min=0s med=0s max=136.03ms p(90)=522.5µs p(95)=570.15µs    iterations...........: 43228   8446.461494/s    vus..................: 10   min=10      max=10    vus_max..............: 10   min=10      max=10
```

Let’s continue the test and set the VU to 100 this time.

```
k6 run script.js --duration 5s --vus 100
```

The output is as follows:

```
default ✓ [======================================] 100 VUs  5s    ✓ is length 3    █ setup    █ teardown    checks...............: 100.00% ✓ 97490      ✗ 0    data_received........: 0 B  0 B/s    data_sent............: 0 B  0 B/s    iteration_duration...: avg=5.07ms min=0s med=506.55µs max=140.07ms p(90)=18.13ms p(95)=28.58ms    iterations...........: 97490   19034.709634/s    vus..................: 100  min=100     max=100    vus_max..............: 100  min=100     max=100
```

It indicates that SQLite is capable of supporting 100 users with an average duration of 5.07ms per transaction.

For actual use cases, you should continue to scale it up to the point where it will congest your database and cause it to breakdown. This allows you to have a better idea on the **maximum limit of your database**.

> If you are new to k6, check out how to configure the [load options](https://k6.io/docs/getting-started/running-k6/#using-options) in the script or run a [stress test](https://k6.io/docs/test-types/stress-testing/) with k6.

## About k6 Extensions

For your information, you can combine multiple extensions and build your own custom k6 binary. For example, you can use the following command to build a k6 binary for both sql and redis:

```
xk6 build v0.32.0 --with github.com/dgzlopes/xk6-redis --with github.com/grafana/xk6-sql
```

Simply head over to the [bundle builder page](https://k6.io/docs/ecosystem/bundle-builder/) to generate the corresponding command based on your own use cases.

With this tutorial, I wanted to show you how easy it is to load test your database or other dependencies separately with k6. If you have any questions or are interested in building an extension, join the k6 community on [Slack](https://k6.io/slack).