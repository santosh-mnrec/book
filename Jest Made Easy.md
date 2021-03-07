
				 SANTOSH SINGH


>
Copyright © 2021 by Santosh Singh All rights reserved. No part of this publication may be reproduced, stored or transmitted in any form or by any means, electronic, mechanical, photocopying, recording, scanning, or otherwise without written permission from the publisher. It is illegal to copy this book, post it to a website, or distribute it by any other means without permission.



# Contents

- [Contents](#contents)
- [Introduction](#introduction)
  - [What Testing?](#what-testing)
- [Test Tools](#test-tools)
- [Jest Basics](#jest-basics)
  - [What is the JEST framework?](#what-is-the-jest-framework)
  - [Jest Characteristics](#jest-characteristics)
- [What are the main features of the JEST framework?](#what-are-the-main-features-of-the-jest-framework)
  - [Matchers](#matchers)
    - [Install Jest using yarn:](#install-jest-using-yarn)
    - [Or npm:](#or-npm)
  - [Running from the command line](#running-from-the-command-line)
- [Type of Test](#type-of-test)
    - [TDD (Test Driven Development)](#tdd-test-driven-development)
    - [BDD (Behavior Driven Development)](#bdd-behavior-driven-development)
  - [How to organize your test code](#how-to-organize-your-test-code)
- [Mocking](#mocking)
    - [Benefits of Mocking](#benefits-of-mocking)
      - [ISOLATION](#isolation)
      - [TEST DURATION](#test-duration)
    - [Jest mocks API](#jest-mocks-api)
      - [Function mock using jest.spyOn()](#function-mock-using-jestspyon)
      - [jest.fn()](#jestfn)
      - [Mock Return Values](#mock-return-values)
      - [Function mock using jest.spyOn()](#function-mock-using-jestspyon-1)
    - [Module mocks using jest.mock()](#module-mocks-using-jestmock)
    - [Mock some function of the module](#mock-some-function-of-the-module)
- [Jest Tips and Trics](#jest-tips-and-trics)
    - [using Object.definePoperty](#using-objectdefinepoperty)
    - [using jest.spyOn](#using-jestspyon)
- [Cookbook](#cookbook)
    - [How to mock JQuery event jest](#how-to-mock-jquery-event-jest)
  - [Example 2- How to mock window property using JEST](#example-2--how-to-mock-window-property-using-jest)
  - [How to mock DOM selector using JEST](#how-to-mock-dom-selector-using-jest)


<div style="page-break-after: always;"></div>


# Introduction


## What Testing?

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/e8be2532-0ada-4720-a5b1-64844daba2ef.jpg)

Fig 1

It’s **important** to ensure that the application should not result in any failures because it can be very expensive in the future or in the later stages of development. Proper **testing** ensures that bugs and issues are detected early in the life cycle of the product or application.


# Test Tools

There is a lot of testing available for javascript. We can select test tools as you require. In this book, I am covering the jest framework.

1.  **Test Environment**（[Mocha](https://mochajs.org/)、[Jasmine](https://jasmine.github.io/)、[Jest](https://facebook.github.io/jest/)、[Karma](https://karma-runner.github.io/1.0/index.html)）
2.  **Test structure** ([Mocha](https://mochajs.org/)、[Jasmine](https://jasmine.github.io/)、[Jest](https://facebook.github.io/jest/)、[Cucumber](https://github.com/cucumber/cucumber-jshttps://github.com/cucumber/cucumber-js)）
3.  **Assertion**（[Chai](http://chaijs.com/)、[Jasmine](https://jasmine.github.io/)、[Jest](https://facebook.github.io/jest/)、[Unexpected](http://unexpected.js.org/)）
4.  **Creation, display, and watch test result**（[Mocha](https://mochajs.org/)、[Jasmine](https://jasmine.github.io/)、[Jest](https://facebook.github.io/jest/)、[Karma](https://karma-runner.github.io/1.0/index.html)）

<div style="page-break-after: always;"></div>

# Jest Basics

## What is the JEST framework?

**Jest** is a JavaScript **test** runner, that is, a JavaScript library for creating, running, and structuring **tests**. **Jest** ships as an NPM package, you can install it in any JavaScript project. **Jest** is one of the most popular **tests** runner these days and the default choice for React projects

## Jest Characteristics

From the [JestJS.io](https://jestjs.io/) website, we can find four main characteristics of Jest:

-   **_Zero configs_**_:_ “Jest aims to work out of the box, config free, on most JavaScript projects.” This means you can simply install Jest as a dependency for your project, and with no or minimal adjustments, you can start writing your first test.
-   **_Isolated_**_:_ Isolation is a very important property when running tests. It ensures that different tests don’t influence each other’s results. For Jest, tests are executed in parallel, each running in its own process. This means they can’t interfere with other tests, and Jest acts as the orchestrator that collects the results from all the test processes.
-   **_Snapshots_**_:_ Snapshots are a key feature for front-end testing because they allow you to verify the integrity of large objects. This means you don’t have to write large tests full of assertions to check if every property is present on an object and has the right type. You can simply create a snapshot and Jest will do the magic. Later, we’ll discuss in detail how snapshot testing works.
-   **_Rich API_**_:_ Jest is known for having a rich API offering a lot of specific assertion types for very specific needs. Besides that, its [great documentation](https://jestjs.io/docs/en/getting-started) should help you get started quickly.

# What are the main features of the JEST framework?

> Faster, more reliable tests

Below are some features of the **JEST** framework

-   One of the advantages of **Jest** is speed.
-   **Jest** runs tests in parallel which makes running the whole test suite so much faster.
-   The coverage feature is impressive too

Let’s take a look at some basics of writing tests with Jest.

**Describe Blocks**

A describe block is used for organizing test cases in logical groups of tests. For example, we want to group all the tests for a specific class. We can further nest new describe blocks in an existing describe block. To continue with the example, you can add a describe block that encapsulates all the tests for a specific function of this class.

**“It” or “Test” Tests**

Furthermore, we use the _test_ keyword to start a new test case definition. It keyword is an alias for the _test_ keyword. Personally, I like to use _it_, which allows for a more natural language flow of writing tests. To give an example:

describe('Beverage()', () => {
  it('should be delicious', () => {
      expect(myBeverage.delicious).toBeTruthy();
  });
});

## Matchers

Next, let’s look at the matchers Jest exposes. A matcher is used for creating assertions in combination with the _expect_ keyword. We want to compare the output of our test with a value we expect the function to return.

Again, let’s look at a simple example where we want to check if an instance of a class is the correct class we expect. We place the test value in the _expect_ keyword and call the exposed matcher function _toBeInstanceOf(<class>)_ to compare the values. The test results in the following code:
```javascript
it('should be instance of Car', () => {
  expect(newTruck()).toBeInstanceOf(Car);
});
```
The complete list of exposed matchers can be found in the [Jest API reference](https://jestjs.io/docs/en/expect.html#tobevalue).

<div style="page-break-after: always;"></div>


#How to Setup Jest

In this chapter, I will explain to you how to set up the jest framework in
your application.Jest is a zero configuration testing framework but It also providesconfiguration to control the testing process.

### Install Jest using yarn:

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/cde94fd5-4f03-4ba8-aad7-caf4d295665a.png)
### Or npm:

```
npm install --save-dev jest
```
>Note: Jest documentation uses yarn commands, but npm will also work. Youcan compare yarn and npm commands in they arnd ocs,here.

Let’s get started by writing a test for a hypothetical function that adds two numbers. First, create a sum.js file:


![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/13582a06-d5f5-4ba5-8b5a-6162315c86c5.png)


Then, create a file named sum.test.js. This will contain our actual test:

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/2fae2735-b614-4a4e-aa6c-5748f8352f7c.png)
										Figure: sum. test.js

Add the following section to your package.json:

```json
{
"scripts": {
"test": "jest"
 }
}
```

Finally, run yarn test or npm run test and Jest will print this message:

```
PASS ./sum.test.js✓
adds 1 + 2 to equal 3 (5ms)
```

## Running from the command line

You can run Jest directly from the CLI (if it’s globally available in your PATH, e.g. by yarn global add jest or npm install jest —global) with a variety of useful options. Here’s how to run Jest on files matching my-test, using config.json as a configuration file and display a native OS notification after the run:

```
jest my-test --notify --config=config.json
```

<div style="page-break-after: always;"></div>


# Type of Test

 In this chapter, we will discuss the different type of testing methodolo-
gies.

### TDD (Test Driven Development)
TDD (Test Driven Development) is one of the software development methods.The concept is that you write a test before you implement a function.

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/27b9c0ab-1768-41cf-8d94-400fe5d3bdf6.png)


The steps of TDD are as follows.


1. Write a failing test:write tests according to the logic of the function.
2. Makethetestpass:writecodetomakethetestpassandconfirmitpasses
all the other tests.
3. Refactor the implementation:update and rewrite the code to increase
the quality of the product. Also, make sure it passes the new test and
passed tests.

### BDD (Behavior Driven Development)

BDD is another software development method. That designs tests and
expresses behaviour (required specification). In BDD, the test is thought ofas the first customer of the products and requires some specifications in the words of a human. That is why testing frameworks provide us with functions that allow us to write as you write a sentence. Suppose that there is a module called Calculator and it has add function as a
part of it.

```javascript
// In Calculator Module
const add = (x, y) => {
return x + y;
}
```
So you can write a unit test for this function as follows (Using jest for test framework).
![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/3918d78b-2fa1-49fb-8cf5-0c2b160728b7.png)


**describe**: describe function sum up some test cases as a module or a set of functions. In the first arguments, the string is used as the name of the module/folder (e.g. Calculator Module in the above case).
___
**it**: In it, a function, special functions called assertion is used.(e.g. expect() in above case ) Assertion functions validate if the result is the same as expected and notify the result to a framework. The framework checks the result and notifies users of detected failures. In the first arguments, the string is used to express the spec the function has (e.g. should add 2 numbers in the above
cases).

<div style="page-break-after: always;"></div>

##  How to organize your test code

The conventions for Jest, in order of best to worst in my opinion:

1. ==src/sum.test.js== mentioned first in theGettingStarteddocs and
is great for keeping tests (especially unit) easy to find next to
source files
2. ==src/__tests__/sum.test.js== lets you have multiple __tests__
directories so tests are still near original files without cluttering
the same directories
3. ==__tests__/sum.test.js== more like older test frameworks that
put all the tests in a separate directory; while Jest does support
it, it’s not as easy to keep tests organized and discoverable

<div style="page-break-after: always;"></div>

# Mocking

In this chapter, we will learn what is mocking and why we should use it
in our project.


>Mockingis a process used in unit testing when the unit being
testedhasexternaldependencies. Thepurposeofmockingistoisolate
andfocusonthecodebeingtestedandnotonthebehaviororstateof
externaldependencies.

### Benefits of Mocking

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/f8d083ff-e4ec-42ea-962b-bac1d3aabec9.png)

#### ISOLATION
One benefit of using mock objects is that tests can be more easily isolated from their dependencies, thus limiting your tests to a very small scope. Keeping
the scope of unit tests small can help you write short and focused tests. When mocking you are trading some additional test setup for mock object setup.However, if you keep the number of dependencies small your tests should be easier to understand and maintain when limiting the scope.

#### TEST DURATION
Mocking database interactions, file system access, and external services are a great way to speed up your tests. It is absolutely imperative that unit tests run
quickly.

##Mock supports in Jest

 In this chapter, we will understand how jest mocks the functions and module.
==Out of the box jest support mocks==. There are two way to mock the functions in jest

1. By creating a mock function to use in test code
2. Writingmanualmockto override a module dependency.

### Jest mocks API

The Jest testing framework comes with great mocking methods built-in for functions as well as modules. Let’s have a look at them all.

#### Function mock using jest.spyOn()

- Function mock using ```jest.fn()```
- Module mocks using ```jest.spyOn()```
- Module mocks using ```jest.mock()```



Let’s understand all these API with example.

#### jest.fn()

The simplest and most common way of creating a mock is ```jest.fn()``` method.If no implementation is provided, it will return the undefined value. There is
plenty of helpfulmethodsonreturnedJestmockto control its input, output and implementation. Let’s have a look at a few examples.

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/639e87e2-abea-4e1b-8167-491ce47b1894.png)

>When jest mock any function it keep track of calls in mock property

For example, instead of calling ```toHaveBeenCalledTimes```, you can use the following code snippet also
![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/decb6cb5-311c-480e-a097-893fa522f013.png)

#### Mock Return Values


Every mock function can also be used to inject test values into your code during a test

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/bc8a1bd5-7bc7-4c03-b8e4-07a882bd45f5.png)

#### Function mock using jest.spyOn()

Another method of creating a function mock is a **jest.spyOn()** method. Same like **jest.fn()** it creates a controlled mock. The key difference is the fact that by default it calls the original implementation. [It stores in memory the original implementation](https://github.com/facebook/jest/blob/e9aa321e0587d0990bd2b5ca5065e84a1aecb2fa/packages/jest-mock/src/index.js#L685) so in case it has been redefined, **jest.spyOn()** allows us to restore the initial implementation using

Let’s consider the following a simple javascript module. Which have four functions **sum**,**mul** and **div**.


Let’s consider the following a simple javascript module. Which have four
functionssum,mulanddiv.

```
calculator.js
```
![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/aa5302e0-5ff6-4f69-be75-c2c601f26542.png)

Before going to write the test for the above module. Let’s understand how to spy on any object method. Jest provides two way to spy on any object.
![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/43742afc-3f8b-457d-b9b5-252afb974f6c.png)

Now let’s write the test case for the calculator module using ```jest.spyOn```.
![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/a5818a0d-3646-4a61-aa2b-bb06f78dba0a.png)


Let’s understand the code line by line

1. First, we are creating the mock object using jest.spyOn function
2. when we called _jest.spyOn(calculator,’add’)_ method is called the original
implementation
3. In the second test case I am calling _mockImplementation_ on the mock
object so in this case, jest will not invoke the original method instead of
that it will return the mock function result.
4. Once you are done with the mock version of the method you can restore
the original function by calling _mockRestore_ on the mock object.

### Module mocks using jest.mock()

Just provides the fantastic feature for mocking the whole module by using [automock](https://jestjs.io/docs/en/configuration#automock-boolean) that you can enable globally or inside individual test files using **jest.mock()** method.

> [Tip] How to enable automock globally

> To enable automock globally you can create **jest.config.js** file and add following property in the configuration file

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/0c252e6a-f4d7-4a57-9988-6fd15d13252f.png)

_Now, all the import you do in your tests will automatically be mocked. Therefore, you will need to unmock the module you want to test. With this technique, you no longer need to define 10 lines of mock at the beginning of your file._

But in the demo, I will show you how to mock module inside individual test files using **jest.mock()** method.

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/1842f1f9-fb5d-4557-bfb0-820d92c8cff5.png)

jest.mock(..)

It works, but what if a module exports tens or hundreds of methods? Manually reassigning all of them would be cumbersome. Jest comes with a fantastic feature called [automock](https://jestjs.io/docs/en/configuration#automock-boolean) that you can enable globally or inside individual test files using jest.mock() method.

### Mock some function of the module

Let’s suppose you have the following javascript module in your code and you want only to mock **random** function.

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/e5224a70-cbd1-455c-ae0d-555bb8e89bff.png)

module.js

![](https://editor-cdn.reedsy.com/books/604359277ad874723891c7e1/images/1ee2f7b1-2ad9-4155-ba59-00f6fc1e31cd.png)

module.test.js

<div style="page-break-after: always;"></div>

# Jest Tips and Trics

In this chapter I will discuss some tips and trics about the JEST framework.
Jest Internally used  **JSDOM** . ** JSDOM** is a library which parses and interacts with assembled HTML just like a browser. The benefit to **JSDOM** is that it isn't actually a browser. Instead, it implements web standards like browsers do. You can feed it some HTML, and it will parse that HTML.

So if you want to mock any window/document variables then those variables are provided by `jsdom` by default which let's us to mock them using built-in `jest` methods  `jest.spyOn().mockImplementation()` and restore with `.mockRestore()`.

For example,Let's suppose you have following javascript function in your code

```javascript
const TestModule = (function () {
  const notification = () => {
    window.alert("DO SOME WORK")
  };
  return {
    notification: notification,
  };
})();
module.exports = TestModule;
```
In the above code snippet I am using `window.alert`. Now if you want to write the unit test for the above function you have to mock the `window.alert` function. 

You can mock any global object in two way

### using Object.definePoperty
```javascript
Object.defineProperty(global, "window", {
      value: {
        alert: jest.fn()
      }
    });
```
### using jest.spyOn

```javascript
jest.spyOn(window, 'alert').mockImplementation(() => {});
```

```javascript
const TestModule = require("../module");

describe("Mock window property", () => {
  it("should mock window alert function", () => {
    Object.defineProperty(global, "window", {
      value: {
        alert: jest.fn(),
      },
    });
    TestModule.notification();
    expect(window.alert).toBeCalled();
  });
});
```
>Output
```
  Mock window property
    √ should mock window alert function (3 ms)

-----------|---------|----------|---------|---------|-------------------
File       | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s
-----------|---------|----------|---------|---------|-------------------
All files  |     100 |      100 |     100 |     100 | 
 module.js |     100 |      100 |     100 |     100 | 
-----------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        4.225 s
Ran all test suites.


```

# Cookbook

###  How to mock JQuery event jest

```javascript

const $ = require("jquery");

const TestModule = (function () {
  const init = () => {
    $(document).ready(() => {
      console.log("DO SOME REAL WORK");
    });
  };
  return {
    init: init,
  };
})();
module.exports = TestModule;
```
> Solution

```javascript
const TestModule = require("../module");
const $ = require("jquery");
jest.mock(
  "jquery",
  () => {
    const m$ = { on: jest.fn(), ready: jest.fn() };
    return jest.fn(() => m$);
  },
  { virtual: true }
);
describe("Mock JQuery event", () => {
  it("should mock the jquery event", () => {
    $().ready.mockImplementationOnce((callback) => callback());
    $().on.mockImplementationOnce((event, handler) => handler());
    const logSypy = jest.spyOn(console, "log");
    TestModule.init();
    expect($().ready).toBeCalledTimes(1);
    expect(logSypy).toBeCalledWith("DO SOME REAL WORK");
  });
});
```
## Example 2- How to mock window property using JEST

```javascript
const $ = require("jquery");

const TestModule = (function () {
  const maximize = () => {
    //TODO...
    const h = document.documentElement.scrollHeight;
    return h;
  };
  return {
    maximize: maximize,
  };
})();
module.exports = TestModule;
```
>Solution
```javascript
const TestModule = require("../module");

describe("Mock window property", () => {
  it("should set height and width", () => {
    const scrollHeightSpy = jest
      .spyOn(document.documentElement, "scrollHeight", "get")
      .mockImplementation(() => 100);

    TestModule.maximize();
    expect(scrollHeightSpy).toHaveBeenCalled();
  });
});
```
## How to mock DOM selector using JEST

```javascript
module.exports = function main() {
  document.addEventListener('DOMContentLoaded', () => {
     console.log("TODO...");
  });
}
```

>Solution

```javascript
const main = require("../module");
describe("DOMContentLoaded", () => {
  it("should pass", () => {
    document.addEventListener = jest
      .fn()
      .mockImplementationOnce((event, callback) => {
        callback();
      });
    main();
    expect(document.addEventListener).toBeCalledWith(
      "DOMContentLoaded",
      expect.any(Function)
    );
  });
});
```

