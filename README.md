# LeetCode: Sleep Function (JavaScript)

## Problem Description

Implement a function `sleep(millis)` that resolves a promise after `millis` milliseconds. This is a common interview question to test your understanding of asynchronous programming and promises in JavaScript.

**LeetCode Prompt:**

> Given a positive integer `millis`, write an asynchronous function that sleeps for `millis` milliseconds. It should resolve with no value after the specified time has passed.

## Approach

The solution uses JavaScript's built-in `setTimeout` function, which executes a callback after a specified delay. By wrapping `setTimeout` inside a Promise, we can create an asynchronous function that can be awaited.

## Implementation

```js
async function sleep(millis) {
  new Promise((res, rej) => {
    setTimeout(function () {
      res(200);
    }, millis);
  });
}
```

### Explanation

- The function `sleep` is declared as `async`, which means it returns a Promise.
- Inside, a new Promise is created. The `setTimeout` function is used to delay the execution for `millis` milliseconds.
- After the delay, the promise is resolved (with the value `200` in this code, but typically it should resolve with no value).
- **Note:** The current implementation is missing a `return` statement for the Promise. The correct implementation should be:

```js
async function sleep(millis) {
  return new Promise((res) => setTimeout(res, millis));
}
```

## Usage

You can use the `sleep` function with `await` in an async function:

```js
async function demo() {
  console.log("Start");
  await sleep(2000); // Sleep for 2 seconds
  console.log("End after 2 seconds");
}

demo();
```

## Example

```js
sleep(200).then(() => console.log("Slept for 200ms"));
```

## Notes

- The function is useful for delaying execution in asynchronous code, such as in testing, retry logic, or simulating network latency.
- Always ensure to return the Promise from the function so that it can be awaited or chained.

## References

- [MDN Web Docs: setTimeout](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout)
- [MDN Web Docs: Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [LeetCode Problem: Sleep](https://leetcode.com/problems/sleep/)
