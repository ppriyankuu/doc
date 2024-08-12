# Bits and Bytes
### What is a Bit?
A bit is the smallest unit of data in a computer and can have one of the two values : 0 or 1.
Think of it as a light switch that can either be OFF(0) or ON(1).

###  What is a Byte?
A byte is a group of `8` bits. It’s the standard unit of data used to represent a single character in memory. Since each bit can be either 0 or 1, a byte can have `2^8` (256) possible values, ranging from 0 to 255.

### Array of Bytes
```javascript
    const bytes = [202, 244, 1, 23];
    console.log(bytes);
```

### UInt8Array
A better way to represent an array of bytes is to use a `Uint8Array` in JS.
```javascript
    let bytes = new Uint8Array([0, 255, 127, 128]);
    console.log(bytes);
```

## Why use `UInt8Array` over `native arrays`?
- They use less space. Every number take 64 bits (8 bytes). But every value in a `Uint8Array` takes 1 byte.
- UInt8Array Enforces constraints - It makes sure every element doesn’t exceed 255.


What do you think happens to the first element here? Does it throw an error?
```javascript
    let uint8Arr = new Uint8Array([0, 255, 127, 128]);
    uint8Arr[1] = 300;
```