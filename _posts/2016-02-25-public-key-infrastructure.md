---
layout: post
title: Public Key Infrastructure
---
# References
[1] Introduction to Public Key Infrastructure, Springer

# Chapter 1: The purpose of PKI

- Enables the use of public key cryptography on open networks, especially the internet

- Main security goals
  - Confidentiality
    - Data is protected from unauthorized entities.
  - Integrity
    - Data could not be changed by unauthorized entities.
  - Authentication
    - Involved entities must prove who they are
  - Authenticity
    - Data integrity and additionally the origin of the data must be reliable.
  - Non-repudiation
    - Prevents involved entities from denying that they have performed some actions, e.g., some harmful actions.

- Secret key (or Symmetric) cryptosystems
  - Involved entities must agree on secret keys which are used to encrypt the plaintext and decrypt the ciphertext. The encryption and decryption keys can be different but they are still be computed from each other.
  - Examples: Data Encryption Standard (DES), Advanced Encryption Standard (AES)
  - Main disadvantage is that the secret keys still need to be exchanged between the entities.
  
- Public key (or Asymmetric) cryptosystems
  - Main idea is to have one key for encryption (the encryption key) and one for decryption (the decryption key). These keys cannot be computed from each other. The encrytion key can be made public, and thus it is also called the public key. The decryption key is also called the private key.
  - For example, if Alice wants to send Bob a secret message, she will encrypt the message by Bob's public key. On receiving the encrypted message, Bob will use his private key to decrypt the message.
  - Main advantage is that no exchange of secret keys are needed.

- RSA public key cryptosystems
  - The first and also the most widely used public key cryptosystems
  - The public key is a pair (n, e) where n is called RSA modulus and e encryption exponent. The private key is called the decryption exponent.
  - Main disadvantage is its performance

- Hybrid cryptosystems
  - The secret key cryptography is used for the message, and the public key cryptography is used for the secret key. 

- Digital signatures
  - Similar to public key cryptography in that there are two keys involved. One is the private key which is used to create the signature, and the other is the public (or verification) key which is used to verify the signature.
  - Can be used to prove the integrity and authenticity of the data
  - Also supports entity authentication and non-repudiation
  - Examples
    - RSA signature scheme: The most widely used digital signature scheme
	- Digital Signature Algorithm (DSA)
	- Elliptic Curve DSA (ECDSA)

- PKI responsibilities
  - Generate keys
  - Use keys for encrypting, decrypting, signing, and verifying
  - Publish public keys
  - Back up keys
  - Manage invalid keys

# Chapter 2: Certificates

- Certificates are data structures that bind public keys to entities and are signed by a trusted third-party. For example, if Alice wants to check the authenticity of Bob's public key, she has to have a certificate which binds the public key to Bob. Furthermore, the certificate issuer (the third party) must be trustworthy.

- Certificate standards
  - X.509
  - Attribute certificates
  - Card verifiable (CV) certificates
  - Pretty good privacy (PGP) certificates
  
# Chapter 4: Private keys

- The keys have their own life cycles. They can be in many states and can transit from one state to another.

- Storable keys are stored in volatile memory, and must be stored in some personal security environment (PSE) before being delivered.

- PSEs: protect private keys from unauthorized accesses
  - Software
    - PKCS#12
	- PKCS#8: almost always used with PKCS#12
	- Java keystore
  - Hardware
    - Smart cards
	- Hardware security modules
