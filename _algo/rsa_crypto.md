---
title: RSA Crypto
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


RSA (Rivest-Shamir-Adleman) is a widely used asymmetric encryption algorithm that uses a pair of keys for encryption and decryption. The keys are created using the RSA algorithm and consist of a private key, which is kept secret, and a public key, which is shared with others.

Here is an example of how to use the RSA algorithm for encryption and decryption in JavaScript:

```js
const crypto = require("crypto");

function rsaEncrypt(data, key) {
  let buffer = Buffer.from(data);
  let encrypted = crypto.publicEncrypt(key, buffer);
  return encrypted.toString("hex");
}

function rsaDecrypt(data, key) {
  let buffer = Buffer.from(data, "hex");
  let decrypted = crypto.privateDecrypt(key, buffer);
  return decrypted.toString("utf8");
}
```

In this example, the `rsaEncrypt` function takes a data string and a public key as arguments and returns the encrypted version of the data. The `rsaDecrypt` function takes an encrypted data string and a private key as arguments and returns the decrypted version of the data. Both functions use the crypto module of Node.js, which provides cryptographic functionality for encrypting and decrypting data.