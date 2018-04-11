# Secure Communications

## Exam Outcome

Demonstrate an understanding of basic cryptography principles, techniques, and tools.

## Encryption 101

Source:  401.4, Module 18

Cryptography is the art and science of hiding the meaning of a communication from unintended recipients.

Encryption:  Coding a message in such a way that its meaning is concealed.
Decryption:  The process of  transforming an encrypted message into its original form.
Plaintext:  A message in its original form.
Ciphertext:  A message in it encrypted form.

Goals of cryptography:

1. Authentication
2. Integrity
3. Non-repudiation

### Types of Cryptosystems

1. Symmetric - single key
2. Asymmetric - two keys (public and private)
3. Hash - one-way transformation

## Encryption 102

Source:  401.4, Module 19

### Symmetric, Asymmetric, and Hashing Cryptosystems

#### DES

Data Encryption Standard, released March 17th, 1975.  Uses a 64-bit block cipher.  56-bit key size.  Not considered secure by today's measures.

#### Triple DES

Triple DES can be configured to use either 2 or 3 unique keys, yielding a key strength of either 112 bit (2 keys) or 168 bit (3 keys).

#### AES

Advanced encryption standard; employs 4 basic transformations: AddRoundKey, SubBytes, ShiftRows, and MixColumns.

#### RSA

#### MD5

Takes variable length input and outputs 128-bit unique fingerprint.

#### Steganography Review

Simply put, steganography means data hiding.  Data can be hiddin in a variety of formats includng images, Word and text documents.

Types of stego:

1. Injection
2. Substitution
3. File generation

## SSL/TLS

Reference: 401.3, pg. 67

SSL/TLS is a protocol for encrypting network traffic. Operates on port 443. Provides encryption, server identity verification and data integrity.

High level overview of how it works:
- Client connects to server
- Server indicates need for SSL
- Client and server exchange crypto keys
- Secure session begins

