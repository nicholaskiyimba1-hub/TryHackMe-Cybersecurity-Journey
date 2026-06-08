# PACKETS AND FRAMES WRITEUP

## DEFINITION

Paclets and frames refer to small pieces of data that can be sent and reasssembled at the destination computer to form a large piece of data.

This is simply done by puttung the frame inside the packet. The main reason as to why this is done is because it the most efficient way to transfer large amonunts of data which done thruogh the spiting of the dsta into small pieces called packets.
A packet contains the Header which holds the,
**PACKETS**

packet's time to live (prevents the packet from clogging up the network)

The check sum which provides the integrity checking for for the protocols like the TCP/IP.If this data was changed, the value will be different from what was expected and therefore corrupt.

The source IP  Address, which is the device  IP address wheere the data is coing from so the packets knows whee to return to.

The destination IP Address, which is the device IP  where the packet is going. this keps the packet knowing where is heading.

**FRAME,** 

This contains the source MAC Address ( identifies the evice from which the packet packet is coming.

                         Destination MAC Address ( identifies the device to which the packet is heading.)

## TCP ( TRANSMISSION CONTROL PROTOCOL)

This consists of layers similar to the OSI Model. **These layers include;** 

Application layer

Transport layer

Internet layer 

Network interface layer.

As the piece of data of travels through these layers, data is added to each layer, a process caled encapsulation and the vise versa is decapsulation

TCP garantees that any data sent will be recieved onthe other end, a process called **The three way handshake**

## THE THREE WAY HANDSHAKE

This refers to the process used to establish a connection between 2 devices

**Below are messages used during the 3 way handshake**

**SYN MESSAGE**

This is the  initial packet sent during the handshake to initiate the connection between the cleint and the reciever and snycronise the 2 devices together.

**SYN/ACK MESSAGE**

This the packet send fromt the reciever to the client acknowledging the connection and snycronisation between the 2 devices.

**ACK MESSAGE**

This message is either used by the client or the server to acknowledge that a series of messages or packets have been sent and recieved succesfully

**DATA MESSAGE**

Once the connection has been established, the data is sen via the DATA message.

**FIN MESSAGE**

This packet is used to cleanly close the connection after it has been complete.

**RST MESSAGE**

This message abruptly ends the connection which means that there was some sort of a problem that occured during the process.

## PORTS

This refers to the places on the computer where we can send and recive data. In computing, ports are numerical values between **0 and 65,535**


Also note that ports from **0 to 1024** are known as **common ports**

**SOME OF THE PORTS ARE SHOWN BELOW**

|**PROTOCOL**|                                                         **PORT**|                                                                  **DESCRIPTION**|
|------------|-----------------------------------------------------------------|---------------------------------------------------------------------------------|
|**File Transfer Protocol (FTP)**|                  21                         |This this protocol is uesed by file sharing applications built on a client server model meaning you can download files from a central location|
|**Secure Shell(SSH)**|22|This protocol is used to securely log in to sysstem via a text based interface for management.|
|**Hyper Text Transfer Prptocol (HTTP)**|80|This protocol powers the World Wide Web. Your web browser uses this protocol to downlod text, images, and videos of web pages.|
|**Hyper Text Transfer Protocol Secure (HTTPS)**|443|This protoco does exactly as the above, however, securely using encryption.|
|**Server Message Block (SMB)**|445|This protocol is similar to the file transfer protocol (FTP) However, for it it allows to share devices forexamle printers.|
|**Remote Desktop Protocol (RDP)**|3389|This protocol is a secure means of logging into a system using Visual Desktop Interface.(As opposed to the text based limitations of SSH)|


