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
* [Addressing](data-link-layer.md#addressing-link-layer-address)
  * MAC addressing
* [Error Control](data-link-layer.md#error-control)
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

### Addressing \(Link Layer Address\)

Called as **MAC/Physical Address.**  
Size is **48 bits.**  
First 24 bits - **Organization Unique Identifier** \(Assigned by IEEE to company\)  
Last 24 bits - **Organization Assigned Portion** \(Company assign to device\)  
1st bit 0 - **Unicast**  
1st bit 1 - **Multicast**

### **Error Control**

* **Error Detection**
  * **Cyclic Redundancy Check\(CRC\) or Polynomial Code**
    * **Hardware Implementation \(faster\)**
    * **Implemented in Data Link Layer**
  * **Checksum**
    * **Software Implementaion**
    * **Implemented in Transport Layer**
* **Error Correction**
  * **Hamming Code** 

### **Cyclic Redundancy check**

Add additional data \(Frame check sequence\) to the transmitted data. Addtional data is the remainder when transmitted data is divided by \(XOR\) using a generator \(divisor polynomial\). 

Additional data size = degree of generator polynomial

#### \*\*\*\*

