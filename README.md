# The Magical Meal Mystery.
- This write-up details the solution to a cryptography challenge involving ElGamal encryption. The challenge provided encrypted data and required participants to decrypt it to reveal a hidden message.
- Challange Link: https://canyouhack.org/events/novruzctf-2026

⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⡠⢤⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡴⠟⠃⠀⠀⠙⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⠋⠀⠀⠀⠀⠀⠀⠘⣆⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠾⢛⠒⠀⠀⠀⠀⠀⠀⠀⢸⡆⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣶⣄⡈⠓⢄⠠⡀⠀⠀⠀⣄⣷⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣿⣷⠀⠈⠱⡄⠑⣌⠆⠀⠀⡜⢻⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⡿⠳⡆⠐⢿⣆⠈⢿⠀⠀⡇⠘⡆⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢿⣿⣷⡇⠀⠀⠈⢆⠈⠆⢸⠀⠀⢣⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⣿⣿⣿⣧⠀⠀⠈⢂⠀⡇⠀⠀⢨⠓⣄⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⣿⣿⣿⣦⣤⠖⡏⡸⠀⣀⡴⠋⠀⠈⠢⡀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⣾⠁⣹⣿⣿⣿⣷⣾⠽⠖⠊⢹⣀⠄⠀⠀⠀⠈⢣⡀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡟⣇⣰⢫⢻⢉⠉⠀⣿⡆⠀⠀⡸⡏⠀⠀⠀⠀⠀⠀⢇
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢨⡇⡇⠈⢸⢸⢸⠀⠀⡇⡇⠀⠀⠁⠻⡄⡠⠂⠀⠀⠀⠘
⢤⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠛⠓⡇⠀⠸⡆⢸⠀⢠⣿⠀⠀⠀⠀⣰⣿⣵⡆⠀⠀⠀⠀
⠈⢻⣷⣦⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⡿⣦⣀⡇⠀⢧⡇⠀⠀⢺⡟⠀⠀⠀⢰⠉⣰⠟⠊⣠⠂⠀⡸
⠀⠀⢻⣿⣿⣷⣦⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⢧⡙⠺⠿⡇⠀⠘⠇⠀⠀⢸⣧⠀⠀⢠⠃⣾⣌⠉⠩⠭⠍⣉⡇
⠀⠀⠀⠻⣿⣿⣿⣿⣿⣦⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣞⣋⠀⠈⠀⡳⣧⠀⠀⠀⠀⠀⢸⡏⠀⠀⡞⢰⠉⠉⠉⠉⠉⠓⢻⠃
⠀⠀⠀⠀⠹⣿⣿⣿⣿⣿⣿⣷⡄⠀⠀⢀⣀⠠⠤⣤⣤⠤⠞⠓⢠⠈⡆⠀⢣⣸⣾⠆⠀⠀⠀⠀⠀⢀⣀⡼⠁⡿⠈⣉⣉⣒⡒⠢⡼⠀
⠀⠀⠀⠀⠀⠘⣿⣿⣿⣿⣿⣿⣿⣎⣽⣶⣤⡶⢋⣤⠃⣠⡦⢀⡼⢦⣾⡤⠚⣟⣁⣀⣀⣀⣀⠀⣀⣈⣀⣠⣾⣅⠀⠑⠂⠤⠌⣩⡇⠀
⠀⠀⠀⠀⠀⠀⠘⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡁⣺⢁⣞⣉⡴⠟⡀⠀⠀⠀⠁⠸⡅⠀⠈⢷⠈⠏⠙⠀⢹⡛⠀⢉⠀⠀⠀⣀⣀⣼⡇⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣿⣿⣿⣿⣿⣿⣿⣿⣽⣿⡟⢡⠖⣡⡴⠂⣀⣀⣀⣰⣁⣀⣀⣸⠀⠀⠀⠀⠈⠁⠀⠀⠈⠀⣠⠜⠋⣠⠁⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢿⣿⣿⣿⡟⢿⣿⣿⣷⡟⢋⣥⣖⣉⠀⠈⢁⡀⠤⠚⠿⣷⡦⢀⣠⣀⠢⣄⣀⡠⠔⠋⠁⠀⣼⠃⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣿⣿⡄⠈⠻⣿⣿⢿⣛⣩⠤⠒⠉⠁⠀⠀⠀⠀⠀⠉⠒⢤⡀⠉⠁⠀⠀⠀⠀⠀⢀⡿⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠙⢿⣤⣤⠴⠟⠋⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠑⠤⠀⠀⠀⠀⠀⢩⠇⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀

<img width="975" height="479" alt="image" src="https://github.com/user-attachments/assets/fb1aace2-6abe-44be-9d76-f026d75a64f8" />

-------------------------------------------------------------------------------------------------------------------

**Executive Summary**
- This write-up details the solution to a cryptography challenge involving ElGamal encryption. The challenge provided encrypted data and required participants to decrypt it to reveal a hidden message. The vulnerability exploited was a weak prime modulus that made the discrete logarithm problem tractable using the Pohlig-Hellman algorithm. By computing the private key and applying ElGamal decryption, we successfully recovered the flag.

<img width="975" height="305" alt="image" src="https://github.com/user-attachments/assets/d63174a8-7c07-49a5-9086-d687040a6a38" />

-------------------------------------------------------------------------------------------------------------------

**1. Challenge Overview**
- The challenge presented participants with a cryptographic puzzle disguised as a story about discovering a 'magical meal' hidden in an ancient papyrus. The challenge provided the following information:
-------------------------------------------------------------------------------------------------------------------
<img width="975" height="553" alt="image" src="https://github.com/user-attachments/assets/dc8149b1-6674-4ea0-b2fc-339ac7fb13ff" />

-------------------------------------------------------------------------------------------------------------------

•	A large prime number **p**
•	A generator **g**
•	A public key **h**
•	Two ciphertext components **c1** and **c2**

The goal was to decrypt the ciphertext to reveal the name of the magical meal, which would be wrapped in the flag format: **novruzCTF{meal_name}**

-------------------------------------------------------------------------------------------------------------------
<img width="975" height="532" alt="image" src="https://github.com/user-attachments/assets/55c1acfa-1a27-4039-887f-2b50ebce7dc4" />

-------------------------------------------------------------------------------------------------------------------

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

-------------------------------------------------------------------------------------------------------------------

**3. Identifying the Vulnerability**
   
- The security of ElGamal encryption relies on the Discrete Logarithm Problem (DLP). Given g, h, and p, it should be computationally impossible to find x where h = g^x mod p. However, this challenge has a critical weakness: the prime p - 1 has a special structure that makes it vulnerable to the Pohlig-Hellman algorithm.
  
**3.1 What is the Pohlig-Hellman Algorithm?**

- The Pohlig-Hellman algorithm is a method for solving the discrete logarithm problem when p - 1 can be factored into small prime factors.
  
- **Simple analogy:** Imagine you're trying to crack a combination lock with 1,000,000 possible combinations. That would take forever. But what if the lock was poorly designed and you could test each digit separately? Instead of trying all million combinations, you'd only need to try 10 options for each of 6 digits—much easier!
Similarly, if *p - 1* breaks down into small factors, the Pohlig-Hellman algorithm can solve the discrete logarithm problem by breaking it into smaller, easier sub-problems and then combining the results.

**3.2 Why This Challenge is Vulnerable**

Looking at the prime *p* provided in the challenge, we can factor *p - 1*. When we do, we find that it factors into relatively small primes. This means:

***•	The discrete logarithm problem becomes solvable
•	We can recover the private key x
•	Once we have x, we can decrypt the message***
Key Insight: A strong ElGamal implementation should use a safe prime *(where p - 1 = 2q and q is also a large prime)* to prevent this attack. This challenge intentionally uses a weak prime to make it solvable.

-------------------------------------------------------------------------------------------------------------------

**4. Solution Methodology**

- Our approach to solving this challenge follows these high-level steps:

21.	Extract the given data ***(p, g, h, c1, c2)*** from the challenge
22.	Solve for the private key *x* using the Pohlig-Hellman algorithm
23.	Decrypt the ciphertext using the recovered private key
24.	Convert the result to text to reveal the flag

- We'll use Python with the pycryptodome and sympy libraries, which provide built-in functions for cryptographic operations and the discrete logarithm problem.

-------------------------------------------------------------------------------------------------------------------
**5. Step-by-Step Solution**

- Step 1: Data Extraction
First, we need to extract all the values from the challenge. These are typically very large numbers:

```
p = 1905671816403772611477075447515791022372594380344434356222414517909417652709503859707116441682578631751 
g = 35184372088891 
h = 516040377462955752574346949927976425016812503608111809810810609404241010158862043385306853745074259882 
c1 = 1325105302324133202030863283172149567672069489633456911926998051053347443881714632147496615921683435710 
c2 = 1105652739004198834387911095412299689766266872864244844677769021917226737321429032589227873083116104228
```

**Step 2: Understanding the Relationship**

- We know that the public key h was created using: **h = g^x** mod *p*
Our goal is to find x. This is the discrete logarithm problem: given ***g, h, and p, find x.***

**Step 3: Solving for *x* Using Pohlig-Hellman**

- Python's sympy library has a built-in function called discrete_log that automatically uses the Pohlig-Hellman algorithm when appropriate:
  
<pre>from sympy.ntheory.residue_ntheory import discrete_log  x = discrete_log(p, h, g)</pre>

- What happens here: The function factors *p - 1*, recognizes the small prime factors, and efficiently computes *x* using the Pohlig-Hellman algorithm. This would be impossible if *p - 1* had only large prime factors.

**Step 4: Decrypting the Message**

- Now that we have the private key x, we can decrypt the ElGamal ciphertext using the standard decryption formula:

<pre>m = c2 × (c1^x)^(-1) mod p</pre>

**Breaking this down:**

•	First, compute the shared secret: shared_secret = c1^x mod p
•	Find its modular inverse: inv = shared_secret^(-1) mod p
•	Multiply by c2: m = c2 × inv mod p

**In Python code:**

<pre>from Crypto.Util.number import inverse  shared_secret = pow(c1, x, p) m = (c2 * inverse(shared_secret, p)) % p</pre>

**Step 5: Converting to Text**

- The decrypted message *m* is currently a very large number. We need to convert it back to readable text. In cryptography, text is often encoded as numbers using *ASCII* or *UTF-8*:

<pre>from Crypto.Util.number import long_to_bytes  meal = long_to_bytes(m).decode('utf-8').strip() print(f"The magical meal is: {meal}") print(f"Flag: novruzCTF{{{meal}}}")</pre>
-------------------------------------------------------------------------------------------------------------------

**6. Complete Code Implementation**

- Here's the complete Python script that solves the challenge:

<pre>
  from Crypto.Util.number import long_to_bytes, inverse from sympy.ntheory.residue_ntheory import discrete_log  # 1. Data from the papyrus p = 1905671816403772611477075447515791022372594380344434356222414517909417652709503859707116441682578631751 g = 35184372088891 h = 516040377462955752574346949927976425016812503608111809810810609404241010158862043385306853745074259882 c1 = 1325105302324133202030863283172149567672069489633456911926998051053347443881714632147496615921683435710 c2 = 1105652739004198834387911095412299689766266872864244844677769021917226737321429032589227873083116104228  print("[+] Solving Discrete Log with Pohlig-Hellman...")  try:     # 2. Find the private key x     # This solves g^x = h (mod p)     x = discrete_log(p, h, g)     print(f"[+] Found Private Key x: {x}")      # 3. Decrypt ElGamal     # formula: m = c2 * (c1^x)^-1 mod p     shared_secret = pow(c1, x, p)     m = (c2 * inverse(shared_secret, p)) % p      # 4. Convert to string     meal = long_to_bytes(m).decode('utf-8').strip()     print(f"\n[!] Success! The magical meal is: {meal}")     print(f"Flag: novruzCTF{{{meal}}}")  except Exception as e:     print(f"[-] Error: {e}")
</pre>


**6.1 Required Libraries**

Before running the script, install the required Python libraries:

<pre>
  pip install pycryptodome sympy
</pre>

-------------------------------------------------------------------------------------------------------------------
**7. Results and Flag**

- When we run the script, it successfully:

25.	Computes the private key x using Pohlig-Hellman
26.	Decrypts the ciphertext
27.	Converts the result to readable text
28.	Reveals the magical meal name

**Expected Output:**
```
[+] Solving Discrete Log with Pohlig-Hellman...
[+] Found Private Key x: [computed value]
[!] Success! The magical meal is: [meal_name] Flag: novruzCTF{[meal_name]}
```

***Note: The actual meal name and private key value have been redacted to preserve the integrity of the challenge for others who may attempt it.***
-------------------------------------------------------------------------------------------------------------------

**8. Key Takeaways**

***8.1 Security Lessons***

•	Prime selection matters: Using a weak prime (where p-1 has small factors) makes ElGamal vulnerable to Pohlig-Hellman attacks
•	Safe primes are crucial: Production systems should use safe primes where p = 2q + 1 and both p and q are large primes
•	Parameter generation is critical: Proper cryptographic implementations must carefully generate and validate their parameters

**8.2 Attack Techniques Learned**

•	Pohlig-Hellman algorithm: A powerful technique for solving discrete logarithm problems when the modulus has specific weaknesses
•	Cryptanalysis workflow: Identify algorithm → Find vulnerability → Exploit weakness → Recover plaintext
•	Tool utilization: Using existing libraries (sympy, pycryptodome) to implement complex mathematical attacks efficiently

**8.3 Real-World Relevance**

- This challenge demonstrates a real vulnerability that has affected cryptographic implementations in the past. Some notable examples include:

•	Weak parameter generation in some TLS implementations
•	Improperly configured Diffie-Hellman key exchanges
•	Legacy systems using outdated cryptographic standards

- Understanding these attacks helps security professionals audit systems and ensure proper cryptographic hygiene.
-------------------------------------------------------------------------------------------------------------------

- I hope this write up helped you <3
