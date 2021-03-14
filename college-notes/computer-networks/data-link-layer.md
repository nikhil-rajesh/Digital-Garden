# Data Link Layer

**PDU -** Frame

### Sub-divided into

* Logical Link Control \(LLC\)
* Medium Access Control \(MAC\)

### Services

* Unacknowledged Connectionless \(UC\)
* Acknowledged Connectionless \(AC\)
* Acknowledged Connection Oriented \(ACO\)

> Acknowledged - Acknowledge that the frame is successfully received in the other side  
> Connectionless - No persisting connection

{% hint style="info" %}
**LAN - UC**  
LAN is connection between 2-way switches and Bit Error Rate \(BER\) is low. 

**WLAN - AC**  
WLAN is wireless, BER is high. So need to acknowledge.

**WAN - ACO**  
WAN BER is low, but have to pass to other layers. In LAN its just forwarding, so no connection to upper layers. Therefore need to keep a active connection and verify frames.
{% endhint %}

### Functions

* [Framing](data-link-layer.md#framing)
  * Identify boundaries of frames
* Addressing
  * MAC addressing
* Error Control
  * Check if frame is corrupted before passing to Network Layer
* Flow Control
  * Techniques used to control data flow when there is bandwidth differnece between sender and receiver
* Medium Access Control

### Framing

* **Time Gap** 
  * Receive each frame with a time gap. Not practically possible. 
* **Character Count**
  * Character count of frame at start of each frame. If error is there, all data will be corrupted. 
* **Byte Stuffing**
  * Specify a start symbol and end symbol at the start and end of frame. Problem occurs if data contains the start symbol or end symbol. Can be solved by having a delimited before using the start symbol in data. 
* **Bit Stuffing**
  * Before start of frame add flag \(01111110\). If 5 consecutive 1's appear in data add 0 after that, to prevent flag appearing in the data. 

