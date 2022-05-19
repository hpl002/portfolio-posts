Series: web fundamentals
Tags: SSL, TLS, CA, Certificate, HTTPS, Authentication

Objectives:
1. SSL vs TLS
   1. TLS handshake
2. Symmetric and Asymmetric cryptography
3. HTTPS vs HTTP in laymans's terms
4. What are SSL/TLS Certificates, how are they issued, and by whom?
5. How are certificates verified?
6. Working with TLS?
   1. Reading certificates
   2. Debugging


## Glossary:
### SSL(Secure Socket Layer)
Encryption-based internet security protocol. Predecessor to TLS. SSL has several well known faults and is by all accounts not secure anymore. Most modern browsers will not support it.

### TLS(Transport Layer Security)@
TLS is very similar to SSL 3.0. The renaming was enforced due to change of ownership(netscape to IETF).

### Symmetric cryptography
The use of a single shared secret to share encrypted data between parties. In simple terms, the sender encrypts data using a password, and the recipient must know that password to access the data.

### asymmetric cryptography / public-key cryptography
Consists of a public and private key. The public key is well known to all interested parties, while the private key is only known to the owner of the pair. The generation of these pairs of keys are a product of cryptographic *one-way* functions. These functions may also be described as *trap door* functions.
 - Functions that are easy to compute on a given input, but practically impossible to inversely compute within a reasonable amount of time. The recipient uses their private key to unlock the encrypted inputs.

All parties have a public and private key. The sender will use the *intended recipients* public key to encrypt the data. The encrypted payload can only be decrypted by the *intended recipients* private key.

### Diffie-Hellman Key Exchange
*In the Diffie–Hellman key exchange scheme, each party generates a public/private key pair and distributes the public key. After obtaining an authentic copy of each other's public keys, Alice and Bob can compute a shared secret offline.*

Most often explained by the use of colors as opposed to actual (modular)arithmetic.

There are a three parties: Alice, Bob, and Eve. Alice and Bob are individuals that are trying to communicate with each other, while Eve is a third party that is trying to listen in. All communications between Alice and Bob will go via the public domain, which Eve also has free access to.

1. Alice and Bob must agree on a common shared color, say yellow(public key).
2. The shared public color is communicated in the public domain.
   1. Eve recognizes and remembers this color.
3. Alice picks a private color(Alice's private key), red.
4. Bob picks a private color(Alice's private key), blue.
5. Alice and Bob combine each of their private colors with equal parts of the public color.
   1. 50ml yellow + 50ml of their private color produces *some* new color.
   2. Alice and Bob have not produced the same color as they have different private colors
6. The resulting mixtures are shared via the public domain. Alice sends Bob her color, and vice versa.
   1. Eve takes note of these shared colors and now sits with 3 colors in total.
   2. Public color: yellow
   3. Alice's public color: some brown-ish color
   4. Bob's public color: some brown-ish color
   5. Even though Eve now holds all communication that has been shared, she is not able to to determine exactly which colors that were mixed and at what proportions(one way function).
8.  Once Bob has received Alice's Color he mixes in 50ml of his private color. Alice does the same on her end(but uses her own private color instead).
9.  Bob and Alice have now produced the exact same color on each of their ends, without sharing their private colors to each other or to Eve.
10. As is the case with Eve, Alice and Bob are not able to inversely determine their opposing parties private color as this too is practically impossible.

The key takeaway being that these are **one-way** functions. The fact that they cannot be inversed enables a simple and secure key exchange where the source and target can share information via a public domain and then compute a shared secret individually. This secret can the be used for symmetric encryption so that they do not have to repeat the same process.

### TLS handshake



# 1. SSL vs TLS
SSL is the predecessor to TLS. They therefore share the same fundamentals.

Privacy is ensured via encryption. All data is undecipherable(not interpretable) by third parties. All parties are authorized via an authentication handshake. This is to ensure that both the sender and receiver are who they claim to be. Lastly, all data is digitally signed in order to ensure data integrity. This is to ensure that the data is not tampered with before reaching the intended target.

SSL was updated and replaced by TLS in 1999.

## 1.1 TLS Handshake

### Why do we need TLS?
All data transmitted over HTTP is not encrypted and can therefore be read by anyone who manages to intercept the message. TLS effectively scrambles the data that is sent between client and server such that it holds no information for any interceptors.

# 2. HTTPS vs HTTP in laymans's terms
HTTP transfers data in plaintext. Any intercepting parties can read the data that is being sent from source to target. It is considered insecure and should not be used when sending any sensitive data.

HTTPS is the *secure* cousin of HTTPS(yes the S stands for secure). It is a combination of HTTP and TLS.



# Resources
1. https://en.wikipedia.org/wiki/Public-key_cryptography
2. https://www.sciencedirect.com/topics/computer-science/symmetric-cryptography
3. https://www.cloudflare.com/learning/ssl/what-is-ssl/
4. https://www.youtube.com/watch?v=GE3dsA5S7M8
5. https://www.youtube.com/watch?v=86cQJ0MMses
6. https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange
7. https://www.youtube.com/watch?v=YEBfamv-_do