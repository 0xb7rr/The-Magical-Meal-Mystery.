# RSA-challenge.
This write-up details the solution to a cryptography challenge involving ElGamal encryption. The challenge provided encrypted data and required participants to decrypt it to reveal a hidden message.

-------------------------------------------------------------------------------------------------------------------

**Executive Summary**
This write-up details the solution to a cryptography challenge involving ElGamal encryption. The challenge provided encrypted data and required participants to decrypt it to reveal a hidden message. The vulnerability exploited was a weak prime modulus that made the discrete logarithm problem tractable using the Pohlig-Hellman algorithm. By computing the private key and applying ElGamal decryption, we successfully recovered the flag.

-------------------------------------------------------------------------------------------------------------------

**1. Challenge Overview**
The challenge presented participants with a cryptographic puzzle disguised as a story about discovering a 'magical meal' hidden in an ancient papyrus. The challenge provided the following information:
•	A large prime number **p**
•	A generator **g**
•	A public key **h**
•	Two ciphertext components **c1** and **c2**
The goal was to decrypt the ciphertext to reveal the name of the magical meal, which would be wrapped in the flag format: **novruzCTF{meal_name}**

**2. Background: Understanding ElGamal Encryption**
ElGamal encryption is a public-key cryptosystem based on the difficulty of computing discrete logarithms. Here's how it 

works in simple terms:

**2.1 Key Generation**

10.	Choose a large prime number p
11.	Choose a generator g (a special number that can generate other numbers in the group)
12.	Choose a random private key x
13.	Compute public key: h = g^x mod p

- Think of it like this: The private key x is like a secret password. The public key h is created using that password, but in a way that makes it nearly impossible to figure out the original password just by looking at h.

**2.2 Encryption Process**

To encrypt a message **m**:
14.	Choose a random number **k**
15.	Compute: **c1 = g^k** mod **p**
16.	Compute: **c2 = m × h^k** mod **p**
17.	Send both *c1* and *c2* as the ciphertext

**2.3 Decryption Process**

To decrypt the ciphertext using the private key *x*:
18.	Compute the shared secret: **s = c1^x** mod **p**
19.	Find the modular inverse of **s: s_inv = s^(-1)** mod **p**
20.	Recover the message: **m = c2 × s_inv** mod **p**

- **The Problem:** We don't have the private key *x*. So how do we decrypt the message? That's where the vulnerability comes in.

