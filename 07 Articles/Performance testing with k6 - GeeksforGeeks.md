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
# Performance testing with k6 - GeeksforGeeks
**What is Performance and Load Testing?**

Performance Testing is the process of analyzing the quality and capability of a product. Load testing is a subset of performance testing where we analyze the behavior of the application under normal or peak load conditions.

**What is k6?**

k6 is an open-source load testing tool for testing the performance of APIs, microservices, and websites.

**Prerequisites:** Install the [k6](https://k6.io/docs/getting-started/installation) tool.

**Write Your Performance Test Script:** Scripts must contain, at the very least, a default function — this defines the entry point for your VUs, similar to the main() function in many other languages. The code inside the default function is called “VU code”, and is run over and over for as long as the test is running.

k6 works with the concept of virtual users (VUs), which run scripts. Duration is a string specifying the total duration a test should be run.

When creating a new load test, the first thing that you’ll often do is define the HTTP requests that will be used to test your system. A simple example that just performs a GET request looks like this:

-   Javascript

## Javascript

`import{ sleep } from` `'k6'``;`

`import http from` `'k6/http'``;`

`export let options = {`

    `duration :` `'1m'``,`

    `vus : 50,`

`};`

`export` `default` `function``() {`

    `sleep(3);`

`}`

**You can run the test locally using the following command. Just make sure to install** [**k6**](https://k6.io/docs/getting-started/installation) **first.**

```
$ k6 run performance-test.js

```

**This produces the following output:**

```
          /\      |‾‾|  /‾‾/  /‾/
     /\  /  \     |  |_/  /  / /
    /  \/    \    |      |  /  ‾‾\
   /          \   |  |‾\  \ | (_) |
  / __________ \  |__|  \__\ \___/ .io

  execution: local
     script: performance-test.js
     output: -

  scenarios: (100.00%) 1 executors, 50 max VUs, 1m30s max duration (incl. graceful stop):
           * default: 50 looping VUs for 1m0s (gracefulStop: 30s)


running (1m02.5s), 00/50 VUs, 1000 complete and 0 interrupted iterations
default ✓ [======================================] 50 VUs  1m0s


    data_received..............: 711 kB 11 kB/s
    data_sent..................: 88 kB  1.4 kB/s
    http_req_blocked...........: avg=8.97ms   min=1.37µs   med=2.77µs   max=186.58ms p(90)=9.39µs   p(95)=8.85ms
    http_req_connecting........: avg=5.44ms   min=0s       med=0s       max=115.8ms  p(90)=0s       p(95)=5.16ms
    http_req_duration..........: avg=109.39ms min=100.73ms med=108.59ms max=148.3ms  p(90)=114.59ms p(95)=119.62ms
    http_req_receiving.........: avg=55.89µs  min=16.15µs  med=37.92µs  max=9.67ms   p(90)=80.07µs  p(95)=100.34µs
    http_req_sending...........: avg=15.69µs  min=4.94µs   med=10.05µs  max=109.1µs  p(90)=30.32µs  p(95)=45.83µs
    http_req_tls_handshaking...: avg=0s       min=0s       med=0s       max=0s       p(90)=0s       p(95)=0s
    http_req_waiting...........: avg=109.31ms min=100.69ms med=108.49ms max=148.22ms p(90)=114.54ms p(95)=119.56ms
    http_reqs..................: 1000   15.987698/s
    iteration_duration.........: avg=3.11s    min=3.1s     med=3.1s     max=3.3s     p(90)=3.12s    p(95)=3.15s
    iterations.................: 1000   15.987698/s
    vus........................: 50     min=50 max=50
    vus_max....................: 50     min=50 max=50

```

[**HTTP-specific built-in metric:**](https://k6.io/docs/using-k6/metrics)

<table><tbody><tr><td><strong>METRIC NAME</strong></td><td><strong>DESCRIPTION</strong></td></tr><tr><td>http_reqs</td><td>How many HTTP requests has k6 generated, in total.</td></tr><tr><td>http_req_blocked</td><td>Time spent blocked (waiting for a free TCP connection slot) before initiating the request. float</td></tr><tr><td>http_req_connecting</td><td>Time spent establishing TCP connection to the remote host. float</td></tr><tr><td>http_req_tls_handshaking</td><td>Time spent handshaking TLS session with remote host</td></tr><tr><td>http_req_sending</td><td>Time spent sending data to the remote host. float</td></tr><tr><td>http_req_waiting</td><td>Time spent waiting for response from remote host (a.k.a. \”time to first byte\”, or \”TTFB\”). float</td></tr><tr><td>http_req_receiving</td><td>Time spent receiving response data from the remote host. float</td></tr><tr><td>http_req_duration</td><td>&nbsp;Total time for the request. It’s equal to http_req_sending + http_req_waiting + http_req_receiving. float</td></tr></tbody></table>

**Summary export:** You can also make k6 output detailed statistics in a CSV format by using the –out/-o option for k6 run, like this:

```
$ k6 run --out csv=my_test_result.csv script.js

```