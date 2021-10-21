# Read: 14 - BCrypt

## Intro to password hashing

A strong password storage strategy is critical to mitigating data breaches that put the reputation of any organization in danger. Hashing is the foundation of secure password storage.

![](https://lucidoutsourcing.com/__media/password_hashing.png)

### Storing Passwords is Risky and Complex

A simple approach to storing passwords is to create a table in our database that maps a username with a password.The security strength and resilience of this model depends on how the password is stored. The most basic, but also the least secure, password storage format is cleartext.

Storing passwords in cleartext is the equivalent of writing them down in a piece of digital paper. If an attacker was to break into the database and steal the passwords table, the attacker could then access each user account.The attack could come from within the organization. A rogue software engineer with access to the database could abuse that access power, retrieve the cleartext credentials, and access any account.

A more secure way to store a password is to transform it into data that cannot be converted back to the original password. This mechanism is known as hashing.

### What's Hashing About?

hashing refers to "chopping something into small pieces" to make it look like a "confused mess".

In cryptography, a hash function is a mathematical algorithm that maps data of any size to a bit string of a fixed size. We can refer to the function input as message or simply as input. The fixed-size string function output is known as the hash or the message digest.As stated by OWASP, hash functions used in cryptography have the following key properties:

- It's easy and practical to compute the hash, but "difficult or impossible to re-generate the original input if only the hash value is known."
- It's difficult to create an initial input that would match a specific desired output.

### Encryption VS. Hashing

![Encrypting](https://images.ctfassets.net/23aumh6u8s0i/3xP2opDfoin34ScJZMBQB5/bd706f86ade6ad72513eea23d22b039b/encryption-flow)
![Hashing](https://images.ctfassets.net/23aumh6u8s0i/ES2U6Gx7w0yVF9Asidr26/75531c3695f09272142b543a94acc0de/hash-flow)

Commonly used hashing algorithms include Message Digest (MDx) algorithms, such as MD5, and Secure Hash Algorithms (SHA), such as SHA-1 and the SHA-2 family that includes the widely used SHA-256 algorithm.

### Using Cryptographic Hashing for More Secure Password Storage

The irreversible mathematical properties of hashing make it a phenomenal mechanism to conceal passwords at rest and in motion. Another critical property that makes hash functions suitable for password storage is that they are deterministic.

A deterministic function is a function that given the same input always produces the same output. This is vital for authentication since we need to have the guarantee that a given password will always produce the same hash; otherwise, it would be impossible to consistently verify user credentials with this technique.

### Limitations of Hash Functions

Hashing seems pretty robust. But if an attacker breaks into the server and steals the password hashes, all that the attacker can see is random-looking data that can't be reversed to plaintext due to the architecture of hash functions. An attacker would need to provide an input to the hash function to create a hash that could then be used for authentication, which could be done offline without raising any red flags on the server.

The attacker could then either steal the cleartext password from the user through modern phishing and spoofing techniques or try a brute force attack where the attacker inputs random passwords into the hash function until a matching hash is found. Additionally, through a rainbow table attack, an attacker can use a large database of precomputed hash chains to find the input of stolen password hashes. A hash chain is one row in a rainbow table, stored as an initial hash value and a final value obtained after many repeated operations on that initial value. Since a rainbow table attack has to re-compute many of these operations, we can mitigate a rainbow table attack by boosting hashing with a procedure that adds unique random data to each input at the moment they are stored. This practice is known as adding salt to a hash and it produces salted password hashes.

"The trick is to ensure the effort to “break” the hashing exceeds the value that the perpetrators will gain by doing so. None of this is about being “unhackable”; it’s about making the difficulty of doing so not worth the effort." - Troy Hunt

### Summary

- The core purpose of hashing is to create a fingerprint of data to assess data integrity.
- A hashing function takes arbitrary inputs and transforms them into outputs of a fixed length.
- To qualify as a cryptographic hash function, a hash function must be pre-image resistant and collision resistant.
- Due to rainbow tables, hashing alone is not sufficient to protect passwords for mass exploitation. To mitigate this attack vector, hashing must integrate the use of cryptographic salts.
- Password hashing is used to verify the integrity of your password, sent during login, against the stored hash so that your actual password never has to be stored.
- Not all cryptographic algorithms are suitable for the modern industry. At the time of this writing, MD5 and SHA-1 have been reported by Google as being vulnerable due to collisions. The SHA-2 family stands as a better option.

## bcrypt overview - why you should use BCrypt to hash passwords

![](https://media.vlpt.us/images/kylexid/post/7106e7cb-7571-4f33-833b-06d493d5a132/Z63W8.png)

### Hashed password solutions fall short

#### Plain text passwords

plain text password makes use of only letters. Should a hacker gain access to passwords such as these, they can easily pose as a user on your system. Often, plain text passwords are replicated across other logins as well, as users don’t want to have to remember multiple passwords for different sites or applications. That just gives a hacker access to those applications as well.

#### One way hash

With a one-way hash password, here, a password has a hashing algorithm applied to it to make it more secure. While in theory, this is a far better password solution, hackers have found ways around this system as the algorithm used is not exactly a one-way option at all. Hackers can just continue to guess passwords until they gain access to your resources.

#### ‘Salting’ the password

A ‘salt’ adds a very long string of bytes to the password. So even though a hacker might gain access to one-way hashed passwords, they should not be able to guess the ‘salt’ string. In theory, this is a great way to secure your data, but if a hacker has access to your source code, they will easily be able to find the ‘salt’ string for passwords.

#### Random ‘salt’ for each user

As an alternative, a random ‘salt’ string could be added for each user, created on the generation of the user account. This will increase encryption significantly as hackers will have to try to find a password for a single user at a time. Again, even though it means they will have to spend more time cracking the passwords for multiple users, they will still be able to gain access to your resources. It just takes longer.

### The BCrypt Solution

BCrypt is based on the Blowfish block cipher cryptomatic algorithm and takes the form of an adaptive hash function.
BCrypt is able to adjust the cost of hashing. With Key Factor changes, the hash output can be influenced. In this way, BCrypt remains extremely resistant to hacks, especially a type of password cracking called rainbow table.
It compensates for these powerful computers and slows down hashing speed significantly. Ultimately slowing down the cracking process until it’s no longer a viable strategy.
If you have sensitive data or information that you need to be protected, ensuring it is secured correctly is vital.Only BCrypt offers a truly robust solution.

## jBCrypt

jBCrypt is a Java™ implementation of OpenBSD's Blowfish password hashing code, as described in "A Future-Adaptable Password Scheme" by Niels Provos and David Mazières.

This system hashes passwords using a version of Bruce Schneier's Blowfish block cipher with modifications designed to raise the cost of off-line password cracking and frustrate fast hardware implementation. The computation cost of the algorithm is parametised, so it can be increased as computers get faster. The intent is to make a compromise of a password database less likely to result in an attacker gaining knowledge of the plaintext passwords.

jBCrypt is licensed under a ISC/BSD licence (see the LICENSE file for details) and ships with a set of JUnit unit tests to verify correct operation of the library and compatibility with the canonical C implementation of the bcrypt algorithm.

The API is very simple:

```
// Hash a password for the first time
String hashed = BCrypt.hashpw(password, BCrypt.gensalt());

// gensalt's log_rounds parameter determines the complexity
// the work factor is 2\*\*log_rounds, and the default is 10
String hashed = BCrypt.hashpw(password, BCrypt.gensalt(12));

// Check that an unencrypted password matches one that has
// previously been hashed
if (BCrypt.checkpw(candidate, hashed))
System.out.println("It matches");
else
System.out.println("It does not match");
```

![](https://th.bing.com/th/id/OIP.2Z-Adu1_aSUbgDk8atLmiwHaEo?pid=ImgDet&rs=1)

---

## Resources

1. [Intro to password hashing](https://auth0.com/blog/hashing-passwords-one-way-road-to-security/)
2. [bcrypt overview](https://medium.com/@danboterhoven/why-you-should-use-bcrypt-to-hash-passwords-af330100b861)
3. [jBcrypt](https://www.mindrot.org/projects/jBCrypt/)
