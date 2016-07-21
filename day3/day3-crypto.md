# Cryptography

### Cybersecurity First Principles

* __Information Hiding__: Information hiding is any attempt to prevent people from being able to see information. It can be hiding the content of a letter, or it can be applied to hiding how the letter is delivered. Both ways can prevent people from being able to see the information. This lesson looks at how information can be rendered **meaningless** for eavesdroppers using cryptography.

## Cryptography

Cryptography is about hiding the meaning of a message (it is NOT about hiding the message)
* Literally from Greek kryptos, meaning secret and graphia meaning writing
* Grounded in mathematics

### Terms

* `Plaintext/cleartext` – message without any changes, as it is intended to be read
* `Ciphertext` – message that has been changed so its meaning is concealed
* `Encryption/enciphering` – changing plaintext to ciphertext
* `Decryption/deciphering` – changing ciphertext back into plaintext
* `Key` – secret value needed to encrypt and/or decrypt
* `Cryptographic Algorithm/cipher` – a standard sequence of computational steps to encrypt or decrypt a message using a key
* `Cryptanalysis` – practice of analyzing encrypted messages to reveal the plaintext without knowing the key
* `Strength` – determines how much effort and how long it takes to break a ciphertext

### Pre-digital era, Classical Ciphers

Classical algorithms for cryptography are based on two simple operation, Transposition and Substitution.

* `Transposition ciphers` – rearrange the order of the characters of plaintext
  * Also called permutation ciphers
  The arrangement becomes the key
  * Example: [Zig-Zag cipher](https://en.wikipedia.org/wiki/Rail_fence_cipher)

* `Substitution ciphers` – replace the characters with something else (e.g. another character or number)
  * The replacement function becomes the key
  * Example: [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher)

### Cryptool 2

To learn about classical algorithms for cryptography we will use `Cryptool 2` in this module. In the sprit of using open source software, this tool has a very permissive license for its use, distribution and modification. Download and install this educational tool here:
* https://www.cryptool.org/en/ct2-downloads

General information about the features of this tool are available here:
* https://www.cryptool.org/en/cryptool2

### Lab Assignments
Using Cryptool 2, complete the following assignments
* [Caesar, Hill, Vigenère, XOR and Vernam, Transposition and Substitution](./crypto-resources/ryptology-lab-sheet.pdf)
* [Analyzing encrypted texts](./crypto-resources/cryptanalysis-lab-sheet2.pdf)

## Additional Resources

* Khan Academy, [Journey into cryptography](https://www.khanacademy.org/computing/computer-science/cryptography)

* Crypto Challenges with Cryptool: https://www.mysterytwisterc3.org/en/
