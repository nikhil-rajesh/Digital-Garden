# Bottom-Up Parser

## LR\(0\)

{% hint style="info" %}
Grammar without Shift-Reduce Conflict
{% endhint %}

\(0\) means no lookahead.

Shift input symbol to stack  
If possible Reduce  
Repeat

{% hint style="info" %}
Will have problems if wrong prodcution is reduced \(Multiple production for same non-terminal\). Solved using lookaheads.
{% endhint %}

> **Grammar**  
> S' → S$  
> S → cAd  
> A → a

### DFA

![](../../../.gitbook/assets/screenshot_20210217_121657.png)

## SLR

{% hint style="info" %}
Grammar Without Reduce-Reduce Conflict, but can have Shift-Reduce Conflict
{% endhint %}

> **Grammar**  
> S → E$  
> E → T + E  
> E → T  
> T → x

> First\(E\) = {x}           Follow\(E\) = {$}  
> First\(T\) = {x}           Follow\(T\) = {+, $}

In case of shift reduce conflict,   
Reduce if next symbol in input is inside the Follow\(\) of production.  
Otherwise Shift.

![DFA](../../../.gitbook/assets/signal-2021-02-17-130646_002.jpeg)

![Parsing Table](../../../.gitbook/assets/signal-2021-02-17-130646_001.jpeg)

#### Example

![](../../../.gitbook/assets/screenshot_20210217_123824.png)

Reduce if next symbol in input is in Follow\(E\), otherwise shift.

## LR\(1\)

{% hint style="info" %}
Grammar can have both Shift-Reduce and Reduce-Reduce Conflicts
{% endhint %}



