# Perfectly Secret Encryption

Observing the ciphertext should have no effect on the knowledge of the adversary 

A _posteriori_ likelihood that some message m was sent \(even given the ciphertext that was seen\) should be no diferent from the a _priori_ probability that m would be sent.

{% hint style="info" %}
An encryption scheme **\(Gen, Enc, Dec\)** over a message space M is perfectly secret if for every probability distribution over M, every message **m ∈ M**, and every ciphertext **c ∈ C** for which **Pr\[C = c\] &gt; 0** :   
                                                **Pr\[M = m \| C = c\] = Pr\[M = m\]**
{% endhint %}

A scheme is perfectly secret if the distributions over plaintexts and ciphertexts are _independent._

## Perfect Indistinguishability

{% hint style="info" %}
An encryption scheme **\(Gen, Enc, Dec\)** over a message space M is perfectly indistiguishable if and only if for every probability distribution over M, for every **m, m′ ∈ M**, and every **c ∈ C**,   
                                                         __**Pr\[EncK\(m\) = c\] = Pr\[EncK\(m′\) = c\]**
{% endhint %}

{% hint style="warning" %}
Session 5 - Proving _Perfectly Secret = Perfectly Indistinguishable_  
Session 6 - Proving _Perfectly Indistinguishable = Perfectly Secret_  
Session 7 - 
{% endhint %}

