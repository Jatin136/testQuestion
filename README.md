# testQuestion
Write a function `wrap` that accepts a function `func` as an argument and returns a new function. Let's assume we save the returned function to a variable named `wrapped`. `wrapped` should do the following:

- Return result of `func` unless:
  - `func` throws an error, then return null.
  - Once `func` has thrown an error, always return `null` and do not execute `func` when `wrapped` is called.
- `wrapped` should maintain compatibility with `func`. In other words, `wrapped` should accept arguments the same as `func`.

The code you write should pass the following test cases. Be mindful that your implementation of `wrap` should be generic and pass an arbitrary number of test cases.

// TODO: define function according to spec above
// const wrap = (func) => {
// };

let count = 0;
const countThenThrow = () => {
    if (++count === 3) {
        throw new Error("Called too many times");
    }
    return true;
};

const wrappedCount = wrap(countThenThrow);

const throwOnGross = (food) => {
    if (food === "peach") {
        throw new Error(`${food} is gross`);
    }
    return `${food} is yummy`;
};

const wrappedGross = wrap(throwOnGross);

wrappedCount(); // true
wrappedCount(); // true
wrappedCount(); // null
wrappedCount(); // null

wrappedGross("apple");  // "apple is yummy"
wrappedGross("banana"); // "banana is yummy"
wrappedGross("peach");  // null
wrappedGross("apple");  // null

// for solution check index.js file
