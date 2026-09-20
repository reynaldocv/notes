---
layout: home
chapter: "Pre-concepts"
course: "Cryptography"
permalink: "crypto-00/"
---

# What is the cryptography?

Cryptography comes from two words: "kryptos" (hidden) and "graphein" (writing). The term was first used in the 19th century, but the practice of cryptography dates back thousands of years. It has evolved significantly over time, especially with the advent of computers and digital communication.

Cryptography is the study of techniques for secure communication in the presence of third parties called adversaries. It involves creating written or generated codes that allow information to be kept secret. Cryptography converts data into a format that is unreadable for an unauthorized user, allowing it to be transmitted without unauthorized entities decoding it back into a readable format, thus compromising the data.

# Security Goals of Cryptography
The primary goals of cryptography are to ensure the following:
- Confidentiality: Ensuring that information is accessible only to those authorized to have access.
- Integrity: Ensuring that information is accurate and complete, and has not been tampered with.
- Authentication: Verifying the identity of the parties involved in communication.

# Cryptographics Protocols 
Cryptographic protocols: These are formalized procedures that use cryptographic techniques to achieve specific security goals, such as secure communication, authentication, and data integrity. Examples include SSL/TLS for secure web browsing and PGP for secure email communication.

- Symmetric-key cryptography: The same key is used for both encryption and decryption. Examples include AES and DES.

- Asymmetric-key cryptography: Uses a pair of keys, one for encryption (public key) and one for decryption (private key). Examples include RSA and ECC.

- Hash functions: Hash functions are used for data integrity verification, password storage, and digital signatures. They are designed to be fast and efficient, but they are not reversible, meaning you cannot derive the original input from the hash output.  

- Digital signatures: A digital signature is a mathematical scheme for verifying the authenticity of digital messages or documents. It provides assurance that the message was created by a known sender and was not altered in transit. Digital signatures are widely used in software distribution, financial transactions, and in other cases where it is important to detect forgery or tampering.

- Key exchange protocols: These protocols allow two parties to securely share cryptographic keys over an insecure channel. Examples include Diffie-Hellman and Elliptic Curve Diffie-Hellman (ECDH).

- Zero Knowledge proofs: A zero-knowledge proof is a cryptographic method by which one party (the prover) can prove to another party (the verifier) that they know a value (e.g., a password), without revealing any information about the value itself. This is useful for authentication and privacy-preserving protocols.


