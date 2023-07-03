---
title: Encryption and Decryption
date: 2023-07-03 10:36:00 +09:00
categories: [Computer Science, Security]
tags: [encryption, decryption, cs, security] # TAG names should always be lowercase
---

![](https://velog.velcdn.com/images/jw01987/post/cb958d11-d43f-4671-bc54-9a457637dec6/image.jpg)

## Encryption

Encryption is the process of converting original information into an encrypted form.  
Encryption typically involves using specific algorithms and keys.

## Decryption

Decryption is the process of restoring encrypted data to its original form.  
To decrypt encrypted data, the same algorithm and key used during encryption are required.  
Using the correct key for decryption allows obtaining the original data before encryption.

## Encryption Algorithms

> What is a specific algorithm?

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Simple_symmetric_encryption.png/640px-Simple_symmetric_encryption.png)

### Symmetric Key Encryption

- Symmetric key encryption is an algorithm that uses the same key for both encryption and decryption.
- Data is encrypted using a key and decrypted using the same key.
  - Examples include AES, DES, 3DES, Blowfish.

![](https://www.okta.com/sites/default/files/styles/tinypng/public/media/image/2021-03/asymmetric-encryption.png?itok=hn1fyqg-)

### Asymmetric Key Encryption

- Asymmetric key encryption is an algorithm that uses different keys for encryption and decryption.
- It involves using a pair of keys: a public key for encryption and a private key for decrypting data encrypted with the corresponding public key.
  - Examples include RSA, DSA, ECC.

![](https://www.okta.com/sites/default/files/media/image/2021-05/HashingAlgorithm.png)

### Hash Functions

- Hash functions produce a fixed-length output regardless of the size of the input data.
- They are one-way functions, meaning the hash value cannot be reversed to obtain the original data.
- The same data will always generate the same hash value.
  - Examples include MD5, SHA-1, SHA-256, SHA-3.
