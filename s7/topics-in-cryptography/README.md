# Topics In Cryptography

## Kerchoff's Principle

Kerckhoff's principle is the concept that a Cryptographic system should be designed to be secure, even if all its details, except for the key, are publicly known.

#### Arguments in favor of Kerchoff's Principle

* Easier to maintain secrecy of a short key than of a whole algorithm
* If key is exposed, its easier to replace key than replace the algorithm
* In case many pairs of people have to encrypt their communication, its easier to use multiple keys and same algorithm.

#### Reason's for Kerchoff's Principle

* Open algorithm will undergo public scrutiny and are likely to be stronger.
* Security flaws will be revealed by ethical hackers.
* If security of algorithm relies on secrecy, then reverse engineering of code poses a serious threat to security.

## Attack Scenarios

* Ciphertext only 
* Known-plaintext
* Chosen-plaintext
* Chosen-ciphertext

