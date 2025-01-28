Here is the full code in markdown (README.md) format:

# JavaScript Promises and Asynchronous Operations

This repository provides solutions to a series of problems demonstrating the use of JavaScript Promises and asynchronous programming with `setTimeout`, `fs.readFile`, and other common operations.

```javascript
1. File Reading with Callbacks

In this example, we use the `fs.readFile` method to read the content of a file asynchronously using callbacks.
const fs = require('fs');
const filepath = 'example.txt';

fs.readFile(filepath, 'utf-8', (err, data) => {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
    }
});

2. Simple Promise to Add Two Numbers

A promise-based function that resolves the sum of two numbers after a delay.

function addPromise(a, b) {
    return new Promise((resolve, reject) => {
        const sum = a + b;

        setTimeout(() => {
            resolve(sum);
        }, 1000);
    });
}

addPromise(5, 3)
    .then((result) => {
        console.log("Sum:", result);
    })
    .catch((err) => {
        console.error("Error:", err);
    });

3. Using Promise.all to Handle Multiple Promises

This example demonstrates how to run multiple promises in parallel and handle their results using Promise.all.

function addNumbers(a, b) {
    return new Promise((resolve) => {
        const sum = a + b;
        setTimeout(() => {
            resolve(sum);
        }, 1000);
    });
}

Promise.all([addNumbers(5, 3), addNumbers(10, 7)])
    .then((results) => {
        console.log("Results of addition:", results);
    })
    .catch((err) => {
        console.error("Error:", err);
    });

4. Chained Promises with Sequential Execution

Here, we fetch data in a sequential manner, where each step waits for the previous one to complete before proceeding.

function getPromise1() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("DATA1");
            resolve("data1 retrieved");
        }, 2000);
    });
}

function getPromise2() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("DATA2");
            resolve("data2 retrieved");
        }, 2000);
    });
}

function getPromise3() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("DATA3");
            resolve("data3 retrieved");
        }, 2000);
    });
}

console.log("getting data1.....");
getPromise1()
    .then((res) => {
        console.log(res);
        console.log("getting data2.....");
        return getPromise2();
    })
    .then((res) => {
        console.log(res);
        console.log("getting data3.....");
        return getPromise3();
    })
    .then((res) => {
        console.log(res);
    });

5. Handling Rejected Promises (Error Handling)

This example demonstrates how to handle errors in promises with a reject operation.

function failingAPI() {
    return new Promise((resolve, reject) => {
        const success = false;

        if (success) {
            resolve('API call successful!');
        } else {
            reject('API call failed!');
        }
    });
}

failingAPI()
    .then((message) => {
        console.log(message);
    })
    .catch((error) => {
        console.error('Error occurred:', error);
    });

6. Delayed Promise with setTimeout

Here we create a promise that resolves after a specified delay (2 seconds in this case).

function delayedPromise() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Promise resolved after 2 seconds");
        }, 2000);
    });
}

delayedPromise()
    .then((message) => {
        console.log(message);
    })
    .catch((error) => {
        console.error("Error:", error);
    });

7. Chaining Multiple Tasks Sequentially

In this problem, multiple tasks are chained using promises, with each task depending on the result of the previous one.

function firstTask() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("First task completed");
            resolve("First task result");
        }, 1000);
    });
}

function secondTask(previousResult) {
    return new Promise((resolve) => {
        setTimeout(() => { 
            console.log("Second task completed with:", previousResult);
            resolve("Second task result");
        }, 1000);
    });
}

firstTask()
    .then((result) => {
        return secondTask(result);
    })
    .then((finalResult) => {
        console.log("Final result:", finalResult);
    })
    .catch((error) => {
        console.error("Error:", error);
    });

8. Reading File with Promise-Based API

This example demonstrates how to read a file asynchronously using a promise-based API with fs.readFile.

const fs = require("fs");

function readFilePromise(filePath) {
    return new Promise((resolve, reject) => {
        fs.readFile(filePath, "utf8", (err, data) => {
            if (err) {
                reject(err);
            } else {
                resolve(data);
            }
        });
    });
}

readFilePromise("example.txt")
    .then((data) => {
        console.log("File content:", data);
    })
    .catch((err) => {
        console.error("Error reading file:", err);
    });

9. File Reading with Promises

Here, we create a promise-based function to read a file asynchronously, similar to the previous problem but showcasing the promise syntax with error handling.

const fs = require("fs");

function readFilePromise(filePath) {
    return new Promise((resolve, reject) => {
        fs.readFile(filePath, "utf8", (err, data) => {
            if (err) {
                reject(err);
            } else {
                resolve(data);
            }
        });
    });
}

readFilePromise("example.txt")
    .then((data) => {
        console.log("File content:", data);
    })
    .catch((err) => {
        console.error("Error reading file:", err);
    });
}
