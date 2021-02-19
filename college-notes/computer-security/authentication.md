---
description: Process in which a principal proves his/her identity it claims to be
---

# Authentication

## One way Authentication

### Password Based Authentication

* Password can be sent in clear format
  * Can be intercepted by eavesdropper \(unencrypted\)
* Hashed password can be sent
  * Hashed password can be intercepted and replayed later by attacker \(Replay Attack\)

#### Challenge Response Protocol

Used to mitigate Replay attack. Password is not sent, but we can prove we have the password.

```go
// C is Client & S is Server

C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    f(passwd, R); f is one-way

C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    H(passwd || R); H is hash

C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    Epasswd( R); Secret key encryption

C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce Encrypt(R)
C ------> S    R; after decrypting
```

{% hint style="info" %}
* Nonces are random and non-recurring
* Freshness of nonce thwarts replay attack
* Size of nonce is large, 256 bits
* Sender and receiver do not keep track of the nonces generated or received
{% endhint %}

### Certificate Based Authentication

