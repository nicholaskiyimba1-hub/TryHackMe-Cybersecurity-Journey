CRYPTOGRAPHY CONCEPTS ROOM
Introduction

This room introduced me to the basic concepts of cryptography and how cryptography is used to protect information.

Before this room, I had learned about the CIA Triad, especially confidentiality and integrity. This room helped me understand some of the actual techniques used to protect information while it is being transmitted or stored.

The main concepts I learned were:

Plaintext and ciphertext
Keys and algorithms
Symmetric encryption
Asymmetric encryption
The key distribution problem
Certificates and Certificate Authorities
How HTTPS combines symmetric and asymmetric encryption

The room also included a practical Caesar cipher exercise, which helped me understand encryption rather than just reading about it.

Task 1: Introduction

Cryptography is basically about protecting information using mathematical techniques.

One of the main reasons we need cryptography is that data travelling across a network can potentially be observed or intercepted.

For example, when sensitive information such as login credentials or banking information is sent over the Internet, we don't want someone who intercepts the traffic to be able to read it.

Cryptography helps protect this information by transforming it into a form that is not understandable without the required key.

This connects directly to the CIA Triad that I learned in the previous room.

Cryptography can particularly help with:

Confidentiality — preventing unauthorized people from reading information.
Integrity — helping detect whether information has been changed.

The room uses the example of a medical clinic sending patient information over the Internet. Without protection, the information could potentially be read or modified while travelling between systems.

Task 2: Hiding Information — Symmetric Encryption

This task introduced the basic terminology used in cryptography.

Plaintext

Plaintext is the original readable information.

For example:

HELLO

or:

Patient name: Alice Smith

This is information in a form that we can understand.

Ciphertext

Ciphertext is the result after plaintext has been encrypted.

For example:

HELLO

could become:

KHOOR

The ciphertext is intended to look meaningless to someone who doesn't have the required key.

Key

A key is the secret value used by the encryption algorithm to encrypt or decrypt information.

I found this easier to understand using the lockbox analogy from the room.

The lock itself represents the algorithm, while the physical key represents the cryptographic key.

The important point is that the algorithm doesn't necessarily have to be secret.

The security should come from keeping the key secret.

Algorithm

An algorithm is the set of rules used to perform the encryption or decryption.

The basic process can be represented as:

Plaintext
    +
Encryption Algorithm
    +
Key
    ↓
Ciphertext

To decrypt it:

Ciphertext
    +
Decryption Algorithm
    +
Key
    ↓
Plaintext
Caesar Cipher

The room used the Caesar cipher to demonstrate these concepts.

The Caesar cipher shifts letters by a fixed number of positions in the alphabet.

For example, with a key of 3:

A → D
B → E
C → F

and so on.

Therefore:

HELLO

becomes:

KHOOR

To decrypt it, the letters are shifted backwards by three positions.

The important thing I learned from this example is the difference between the algorithm and the key.

The algorithm is:

Shift the letters by a certain number.

The key is:

The number used for the shift.

The Caesar cipher is obviously not suitable for protecting real information today because there are very few possible keys and they can easily be tested.

It was used in the room because it makes the relationship between the plaintext, algorithm, key, and ciphertext easy to understand.

Symmetric Encryption

The Caesar cipher is an example of symmetric encryption.

Symmetric encryption uses the same key for encryption and decryption.

              Same Secret Key
                    |
                    ↓
Plaintext → Encryption → Ciphertext
                         |
                         ↓
                    Decryption
                         |
                         ↓
                     Plaintext

Both Alice and Bob need to know the same secret key.

Advantages

Symmetric encryption is:

Fast
Efficient
Suitable for large amounts of data
Useful for files, disks, and network traffic
The Problem

The major problem is key distribution.

If Alice and Bob have never communicated before, how can Alice safely give Bob the secret key?

If Alice simply sends the key over the Internet, an attacker could intercept it.

This is the key distribution problem, which leads to the next task.

Secret Message Rescue Game

The room included a practical Caesar cipher game called the Secret Message Rescue game.

The exercise involved decrypting intercepted messages and encrypting new messages using different Caesar cipher keys.

This was useful because I had to actually apply the cipher rather than simply read how it works.

Room Flag

[Flag obtained from the Secret Message Rescue game]

Caesar Cipher Exercise

Using a key of 5:

CYBER

becomes:

HDGJW

The important lesson from the exercise was that the Caesar cipher demonstrates the basic concept of encryption, but it should not be considered secure encryption for real-world systems.

Task 3: Sharing Keys Safely — Asymmetric Encryption

The biggest problem with symmetric encryption is how to securely share the secret key.

This task introduced asymmetric encryption as a solution.

Instead of one key, asymmetric encryption uses two mathematically related keys:

Public key
Private key
Public Key

The public key can be shared with anyone.

There is no requirement to keep it secret.

For example, Bob can publish his public key on his website.

Private Key

The private key must remain secret.

Only Bob should have access to his private key.

The relationship can be summarized as:

Public Key
   ↓
Can be shared publicly


Private Key
   ↓
Must remain secret
Mailbox Analogy

The mailbox analogy helped me understand asymmetric encryption.

The public key is like the opening of a mailbox where anyone can put a letter.

The private key is like the key that opens the mailbox.

Alice can use Bob's public key to encrypt a message for Bob.

Bob then uses his private key to decrypt it.

Alice
  |
  | Bob's public key
  ↓
Encrypt message
  |
  ↓
Encrypted message
  |
  ↓
Bob
  |
  | Bob's private key
  ↓
Decrypt message
  |
  ↓
Original message

The important advantage is that Alice and Bob don't need to secretly exchange a shared key beforehand.

The Key Distribution Problem

This is what asymmetric encryption solves.

With symmetric encryption:

Alice ←──── secret key ────→ Bob

The problem is finding a secure way to transfer the secret key.

With asymmetric encryption:

Bob
│
├── Public key → can be shared
│
└── Private key → kept secret

Alice can use Bob's public key without needing Bob to send her a secret key first.

HTTPS and Hybrid Encryption

One of the most useful things I learned in this room was that HTTPS does not simply use asymmetric encryption for everything.

Instead, modern secure connections use a combination of asymmetric and symmetric cryptography.

The general idea is:

Asymmetric encryption
        ↓
Securely establish/shared secret
        ↓
Symmetric encryption
        ↓
Encrypt the actual session data

This works because asymmetric encryption is useful for establishing trust and securely negotiating secrets, while symmetric encryption is much faster for handling large amounts of data.

This is called a hybrid approach.

Certificates and Certificate Authorities

There is another problem:

How does my browser know that the public key actually belongs to the website I'm visiting?

This is where digital certificates and Certificate Authorities (CAs) come in.

A certificate contains information such as:

The website's domain
Its public key
Information about the certificate issuer
Validity information

A trusted Certificate Authority signs the certificate.

When I visit an HTTPS website, my browser can check the certificate and determine whether it is valid and trusted.

This is one of the things happening behind the padlock that I see in my browser.

Symmetric vs Asymmetric Encryption
Feature	Symmetric	Asymmetric
Number of keys	One shared key	Public + private key
Key sharing	More difficult	Public key can be shared
Speed	Fast	Slower
Main purpose	Bulk data encryption	Secure key exchange and other cryptographic functions
Example analogy	Lockbox	Mailbox

The most important thing I took away is that these two approaches are not competitors where one completely replaces the other.

Real systems can use both.

Task Questions
In asymmetric encryption, which key stays secret?

Private key

Alice encrypts a message using Bob's public key. Can only Bob's private key decrypt it?

Yay

What problem does asymmetric encryption solve?

The key distribution problem

After the initial asymmetric exchange in HTTPS, what encryption type handles bulk data?

Symmetric encryption

Task 4: Conclusion

This room gave me a foundation in how cryptography is used to protect information.

The main concepts I learned are:

Plaintext

The original readable information.

Ciphertext

The encrypted and unreadable form of the information.

Key

The secret value used by the cryptographic process.

Algorithm

The rules used to perform encryption and decryption.

The Two Main Types of Encryption
Symmetric Encryption

Uses one shared key.

One key
   ↓
Encrypt + Decrypt

It is fast and efficient, but safely sharing the key can be difficult.

Asymmetric Encryption

Uses two related keys.

Public key  → Can be shared
Private key → Must remain secret

It helps solve the key distribution problem but is slower than symmetric encryption.

What I Understand About HTTPS Now

Before this room, seeing the padlock in a browser mostly just meant to me that a website was "secure."

Now I have a better idea of what is happening.

A simplified version is:

Browser
   |
   | Asymmetric cryptography
   ↓
Securely establish session secrets
   |
   ↓
Symmetric cryptography
   |
   ↓
Protect the actual data being exchanged

This combination allows HTTPS to get the benefits of both approaches.

Key Takeaways

The main lessons I am taking from this room are:

Plaintext is readable information.
Ciphertext is the encrypted form.
A key controls the cryptographic operation.
An algorithm describes how the operation works.
Symmetric encryption uses the same key for encryption and decryption.
Symmetric encryption is fast but has a key distribution problem.
Asymmetric encryption uses a public key and a private key.
The private key must remain secret.
Asymmetric cryptography helps solve the key distribution problem.
HTTPS uses a combination of asymmetric and symmetric cryptography.
Certificates and Certificate Authorities help browsers establish trust in website identities.

The biggest thing I learned is that cryptography isn't just about "scrambling data." It is a system involving algorithms, keys, encryption, decryption, identity, and trust.

This gives me a much better understanding of what is happening behind the scenes when I use HTTPS and see that padlock in my browser.

Room completed.
