# Cryptography

## Types of Attacks

- **Cryptanalysis:** Attacker tries to crack the cipher by exploiting weaknesses in the algorithm or implementation.
- **Brute Force:** Attacker tries every possible key combination until the correct one is found.

## Types of Encryption

- **Symmetric:** Same key is used for encryption and decryption.
  - Examples: DES, AES
- **Asymmetric:** Different keys are used for encryption and decryption.
  - Example: RSA

## Block vs Stream Cipher

- **Block Cipher:** Data is divided into fixed-size blocks and each block is encrypted/decrypted separately.
  - Examples: DES, AES
- **Stream Cipher:** Data is encrypted/decrypted one byte or bit at a time.

## DES (Data Encryption Standard)

- Symmetric block cipher
- 64-bit block size
- 56-bit key size (relatively short and insecure over time)
- **Triple DES:** Improved variant that applies DES three times with different keys

## AES (Advanced Encryption Standard)

- Symmetric block cipher (also known as Rijndael)
- 128-bit block size
- Stronger key sizes: 128, 192, or 256 bits

## RSA (Rivest–Shamir–Adleman)

- Asymmetric encryption algorithm
- Public key used for encryption, private key for decryption
- Widely used for secure data transmission and key exchange

## Other Concepts

- **Diffie-Hellman Key Exchange:** Secure method for exchanging cryptographic keys over an insecure channel
- **Digital Signature:** Verifies the authenticity and integrity of digital data
- **Digital Certificate:** Contains public key and identity information, issued by a trusted Certificate Authority (CA)
- **SSL/TLS Handshake Protocol:** Establishes a secure connection between client and server, involving cipher suite negotiation, key exchange, and identity verification using digital certificates.
