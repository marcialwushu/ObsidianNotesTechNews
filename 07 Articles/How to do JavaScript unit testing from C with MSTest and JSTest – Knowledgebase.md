---
link: {{link}}
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
date: July 24, 2022 (Sun)
---
# Highlights


---
# How to do JavaScript unit testing from C with MSTest and JSTest – Knowledgebase
I wanted to run regular MSTest unit test written in C# to assert JavaScript code. There are several ways to accomplish this, but in this case I use JSTest.

Just add JSTest to your C# testproject with NuGet, now you can write tests like:

**Test class**

```
using JSTest;
using JSTest.ScriptLibraries;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using TestProject1.Helpers;

namespace TestProject1
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            var script = new TestScript();

            // Arrange: Append the JavaScript code to test.
            string scriptContents = (new AssemblyHelper().GetContentsEmbededResourceFile("TestProject1.MvcApplication1.Scripts.Person.js"));
            script.AppendBlock(scriptContents);

            // Arrange: Append the JSTest asser library, so we can assert the test code.
            script.AppendBlock(new JsAssertLibrary());

            // Append "Act" JavaScript code.
            script.AppendBlock("var person1 = new Person('John Do', 32, 'Software Engineer');");

            // Assert.
            script.RunTest(@"assert.equal('Jonh Do test', person1.sayName());");
        }
    }
}
```

Running this test within Microsoft Visual Studio 2010 will result in a passed test.

**JavaScript code to test**

```
function Person(name, age, job)
{
    var privateField1 = 'test';
    this.name = name;
    this.age = age;
    this.job = job;
    this.privilegedMethod = function () { return privateField1; }
};

Person.prototype.sayName = function ()
{
    return this.name + ' ' + this.privilegedMethod();
};
```

**Notes**

– The privilegedMethod is used to access private fields on the Person class.

– You can set breakpoints in the JavaScript code!!

**C# helper class**

```
using System;
using System.IO;
using System.Reflection;

namespace TestProject1.Helpers
{
    public class AssemblyHelper
    {
        /// <summary>
        /// Read the contents of an embededresourcefile with the given name.
        /// </summary>
        /// <param name="resourceName">Name of the resource.</param>
        /// <returns></returns>
        public string GetContentsEmbededResourceFile(string resourceName)
        {
            if (string.IsNullOrWhiteSpace(resourceName)) { throw new ArgumentNullException("resourceName"); }

            string contents = string.Empty;
            using (Stream stream = Assembly.GetExecutingAssembly().GetManifestResourceStream(resourceName))
            using (var reader = new StreamReader(stream))
            {
                contents = reader.ReadToEnd();
            }
            return contents;
        }
    }
}
```

**Microsoft Visual Studio 2010**

[![image](https://www.roelvanlisdonk.nl/wp-content/uploads/2012/05/image_thumb7.png "image")](https://www.roelvanlisdonk.nl/wp-content/uploads/2012/05/image7.png)