---
title: AES Crypto
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


The AES (Advanced Encryption Standard) algorithm is a widely used symmetric encryption algorithm that uses a fixed-size key to secure data. It is considered to be very secure and is the standard encryption algorithm used by the US government.

Here is an example of how to implement the AES algorithm for encryption and decryption in JavaScript:

Here is a detailed example of how to implement the AES (Advanced Encryption Standard) algorithm for encryption and decryption in JavaScript:

```js
const crypto = require("crypto");

const BLOCK_SIZE = 16;

function pad(data) {
  let padding = BLOCK_SIZE - (data.length % BLOCK_SIZE);
  return data + String.fromCharCode(padding).repeat(padding);
}

function unpad(data) {
  let padding = data.charCodeAt(data.length - 1);
  return data.slice(0, -padding);
}

function aesEncrypt(data, key) {
  let iv = crypto.randomBytes(BLOCK_SIZE);
  let cipher = crypto.createCipheriv("aes-256-cbc", key, iv);
  let encrypted = cipher.update(pad(data), "utf8", "hex");
  encrypted += cipher.final("hex");
  return iv.toString("hex") + encrypted;
}

function aesDecrypt(data, key) {
  let iv = Buffer.from(data.slice(0, BLOCK_SIZE * 2), "hex");
  let encrypted = data.slice(BLOCK_SIZE * 2);
  let decipher = crypto.createDecipheriv("aes-256-cbc", key, iv);
  let decrypted = decipher.update(encrypted, "hex", "utf8");
  decrypted += decipher.final("utf8");
  return unpad(decrypted);
}

let data = "Hello, world!";
let key = crypto.randomBytes(32);
let encrypted = aesEncrypt(data, key);
let decrypted = aesDecrypt(encrypted, key);
console.log(decrypted); // "Hello, world!"
```

In this example, the aesEncrypt function takes a data string and a key as arguments and returns the encrypted version of the data. The aesDecrypt function takes an encrypted data string and a key as arguments and returns the decrypted version of the data.

The pad and unpad functions are helper functions that are used to pad and unpad the data to the block size of the AES algorithm. This is necessary because AES works on blocks of data and the data must be padded if it is not a multiple of the block size.

