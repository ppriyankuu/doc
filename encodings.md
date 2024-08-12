# Encodings
Bytes are cool but highly unreadable. Imagine telling someone
```javascript
    Hey, my name is 00101011101010101020
```

It’s easier to encode data so it is more human readable . Some common encodings include...
 - Ascii
 - Hex
 - Base64
 - Base58 

## ASCII
`1 character = 7 bits`
Every byte corresponds to a text on the computer . 
Here is a complete list - [click me!!!](https://www.w3schools.com/charsets/ref_html_ascii.asp#:~:text=The%20ASCII%20Character%20Set&text=ASCII%20is%20a%207%2Dbit,are%20all%20based%20on%20ASCII)

Bytes to ASCII
```javascript
    function bytesToAscii(byteArray) {
    return byteArray.map(byte => String.fromCharCode(byte)).join('');
    }

    // Example usage:
    const bytes = [72, 101, 108, 108, 111]; // Corresponds to "Hello"
    const asciiString = bytesToAscii(bytes);
    console.log(asciiString); // Output: "Hello"
```

ASCII to Bytes
```javascript
    function bytesToAscii(byteArray) {
    return byteArray.map(byte => String.fromCharCode(byte)).join('');
    }

    // Example usage:
    const bytes = [72, 101, 108, 108, 111]; // Corresponds to "Hello"
    const asciiString = bytesToAscii(bytes);
    console.log(asciiString); // Output: "Hello"
```

Uint8Array to ASCII
```javascript
    function bytesToAscii(byteArray) {
    return new TextDecoder().decode(byteArray);
    }

    // Example usage:
    const bytes = new Uint8Array([72, 101, 108, 108, 111]); // Corresponds to "Hello"
    const asciiString = bytesToAscii(bytes);
    console.log(asciiString); // Output: "Hello"
```

ASCII to Uint8Array
```javascript
    function asciiToBytes(asciiString) {
    return new Uint8Array([...asciiString].map(char => char.charCodeAt(0)));
    }

    // Example usage:
    const ascii = "Hello";
    const byteArray = asciiToBytes(ascii);
    console.log(byteArray); // Output: Uint8Array(5) [72, 101, 108, 108, 111]
```

## Hex
`1 character = 4 bits`
A single hex character can be any of the 16 possible values: `0-9` and `A-F`.
Array to Hex
```javascript
    function arrayToHex(byteArray) {
    let hexString = '';
    for (let i = 0; i < byteArray.length; i++) {
        hexString += byteArray[i].toString(16).padStart(2, '0');
    }
    return hexString;
    }

    // Example usage:
    const byteArray = new Uint8Array([72, 101, 108, 108, 111]); // Corresponds to "Hello"
    const hexString = arrayToHex(byteArray);
    console.log(hexString); // Output: "48656c6c6f"
```

Hex to Array
```javascript
    function hexToArray(hexString) {
    const byteArray = new Uint8Array(hexString.length / 2);
    for (let i = 0; i < byteArray.length; i++) {
        byteArray[i] = parseInt(hexString.substr(i * 2, 2), 16);
    }
    return byteArray;
    }

    // Example usage:
    const hex = "48656c6c6f";
    const byteArrayFromHex = hexToArray(hex);
    console.log(byteArrayFromHex); // Output: Uint8Array(5) [72, 101, 108, 108, 111]
```
Reference : [click me!!!](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)


## Base64
`1 character = 6 bits`
Base64 encoding uses 64 different characters (A-Z, a-z, 0-9, +, /), which means each character can represent one of 64 possible values.

[Encode](https://www.base64encode.org/) <br />
[Decode](https://www.base64decode.org/)

## Base58
It is similar to Base64 but uses a different set of characters to avoid visually similar characters and to make the encoded output more user-friendly
Base58 uses 58 different characters:
 - Uppercase letters: `A-Z` (excluding I and O)
 - Lowercase letters: `a-z` (excluding l)
 - Numbers: `1-9` (excluding 0)

Encode
```javascript
    const bs58 = require('bs58');

    function uint8ArrayToBase58(uint8Array) {
    return bs58.encode(uint8Array);
    }

    // Example usage:
    const byteArray = new Uint8Array([72, 101, 108, 108, 111]); // Corresponds to "Hello"
    const base58String = uint8ArrayToBase58(byteArray);
    console.log(base58String); // Output: Base58 encoded string
```

Decode
```javascript
    const bs58 = require('bs58');

    function base58ToUint8Array(base58String) {
    return bs58.decode(base58String);
    }

    // Example usage:
    const base58 = base58String; // Use the previously encoded Base58 string
    const byteArrayFromBase58 = base58ToUint8Array(base58);
    console.log(byteArrayFromBase58); // Output: Uint8Array(5) [72, 101, 108, 108, 111]
```