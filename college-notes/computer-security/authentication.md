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

//1
C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    f(passwd, R); f is one-way

//2
C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    H(passwd || R); H is hash

//3
C ------> S    identity of C
C <------ S    throws a challenge in the form of nonce R
C ------> S    Epasswd( R); Secret key encryption

//4
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

```go
//1
C -----> S    (certificate)
               S checks the validity period, name of the user,
               verifies the signature of CA
C <----- S    (random nonce R)
C -----> S    (EncrPvt.A(R))

//2
C -----> S    (certificate)
               S checks the validity period, name of the user,
               verifies the signature of CA
C <----- S    (EncrPub.A(R))
C -----> S    (the nonce R sent by A to B)
```

## Mutual Authentication

### Shared secret-based authentication

```go
A -------> B    (identity of A, Ra)
A <------- B    (EK (Ra), Rb)
A -------> B    (EK (Rb))
```

#### Flaw - Parallel Session attack

```go
C -------> B    identity of A and Nonce Ra
C <------- B    EK(Ra), Rb
C -------> A    identity of B and Rb
C <------- A    EK(Rb), Rc
C -------> B    EK(Rb)

C has successfully impersonated A to B
```

{% hint style="info" %}
Also called as **Reflection attack**
{% endhint %}

#### Solution

```go
A -------> B    identity of A, Ra
A <------- B    EK(Ra), EK(Rb )
A -------> B    DK (EK(Rb )) and send Rb to B
```

### Asymmetric key based Authentication



