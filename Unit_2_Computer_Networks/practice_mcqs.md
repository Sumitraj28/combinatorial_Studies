# Unit II: Computer Networks - MCQ Bank

Master Unit 2 with these 105 solved, high-probability Multiple Choice Questions covering physical structures, reference models, subnetting, routing, and key protocols.

---

## 🔷 Topic 1: Topologies, Media & Reference Models

#### Q1. Which network topology requires the maximum amount of cabling and interfaces, providing high redundancy and fault isolation?
- A) Bus Topology
- B) Star Topology
- C) Mesh Topology
- D) Ring Topology
- **Answer: ✅ C**
- **Explanation**: A fully-connected mesh topology requires $N(N-1)/2$ duplex physical lines and $N-1$ ports per node. This makes it highly reliable but extremely expensive.

#### Q2. Which transmission medium is completely immune to Electromagnetic Interference (EMI) and radio frequency interference?
- A) Shielded Twisted Pair (STP)
- B) Fiber Optic Cable
- C) Coaxial Cable
- D) Unshielded Twisted Pair (UTP)
- **Answer: ✅ B**
- **Explanation**: Fiber optic cables transmit data as light pulses through glass or plastic cores. Since they don't carry electrical currents, they are completely immune to electromagnetic interference.

#### Q3. In the ISO OSI Reference Model, which layer is responsible for translating data, encrypting/decrypting sensitive fields, and compressing text?
- A) Application Layer
- B) Session Layer
- C) Presentation Layer
- D) Transport Layer
- **Answer: ✅ C**
- **Explanation**: Layer 6 (Presentation) acts as the data translator, formatter, and encryption engine (e.g., handling SSL/TLS, ASCII, JPEG).

#### Q4. The term "Frame" represents the Protocol Data Unit (PDU) of which layer?
- A) Transport Layer
- B) Network Layer
- C) Data Link Layer
- D) Physical Layer
- **Answer: ✅ C**
- **Explanation**: The PDUs are: segments/datagrams in Transport (Layer 4), packets in Network (Layer 3), frames in Data Link (Layer 2), and raw bits in Physical (Layer 1).

#### Q5. Which of the following is NOT true regarding the TCP/IP reference model compared to the OSI model?
- A) TCP/IP has fewer layers (4 layers)
- B) TCP/IP's Application layer combines OSI's Application, Presentation, and Session layers
- C) OSI was developed first and is a theoretical model, while TCP/IP is a practical implementation model
- D) TCP/IP defines a strict Session layer
- **Answer: ✅ D**
- **Explanation**: The TCP/IP model has no Session layer. Session and Presentation duties are handled directly within the application programs themselves at the TCP/IP Application layer.

---

## 🔷 Topic 2: Data Link & Media Access Control

#### Q6. What is the length of a physical MAC address in standard Ethernet?
- A) 32 bits
- B) 48 bits
- C) 64 bits
- D) 128 bits
- **Answer: ✅ B**
- **Explanation**: A MAC address (physical address) is 48 bits (6 bytes) long, represented in hexadecimal (e.g., `00:0a:95:9d:68:16`).

#### Q7. Which media access control protocol is used in wireless networks (802.11 WiFi)?
- A) CSMA/CD
- B) CSMA/CA
- C) Token Ring
- D) ALOHA
- **Answer: ✅ B**
- **Explanation**: Wireless radios cannot transmit and receive on the same frequency simultaneously to detect collisions. Thus, wireless networks use Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA), while wired Ethernet uses CSMA/CD (Collision Detection).

#### Q8. Under Stop-and-Wait flow control, what is the maximum link utilization if the propagation delay ($T_p$) is $40\text{ ms}$ and the packet transmission delay ($T_t$) is $20\text{ ms}$?
- A) $50\%$
- B) $20\%$
- C) $33.3\%$
- D) $100\%$
- **Answer: ✅ B**
- **Explanation**: 
  - $\text{Efficiency } \eta = \frac{T_t}{T_t + 2T_p}$
  - $\eta = \frac{20}{20 + 2(40)} = \frac{20}{20 + 80} = \frac{20}{100} = 20\%$.

#### Q9. Cyclic Redundancy Check (CRC) is primarily used for:
- A) Encryption
- B) Flow Control
- C) Error Detection
- D) Routing
- **Answer: ✅ C**
- **Explanation**: CRC is a mathematical division-based technique used by the Data Link layer to check if bits were corrupted during transmission.

---

## 🔷 Topic 3: Network Layer & Routing

#### Q10. What is the default subnet mask for Class B IP addresses?
- A) `255.0.0.0`
- B) `255.255.0.0`
- C) `255.255.255.0`
- D) `255.255.255.240`
- **Answer: ✅ B**
- **Explanation**: Class B ranges from `128` to `191` in the first octet and uses a 16-bit network prefix, yielding a default subnet mask of `255.255.0.0` (/16).

#### Q11. Which IP address represents a loopback test address?
- A) `192.168.1.1`
- B) `127.0.0.1`
- C) `10.0.0.1`
- D) `255.255.255.255`
- **Answer: ✅ B**
- **Explanation**: The entire `127.0.0.0/8` subnet is reserved for local host loopback testing.

#### Q12. Address Resolution Protocol (ARP) operates to:
- A) Map an IP address to a physical MAC address
- B) Map a domain name to an IP address
- C) Route packets to a default gateway
- D) Translate private IPs to public IPs
- **Answer: ✅ A**
- **Explanation**: ARP queries the local network to find the MAC address corresponding to a known target IP address. DNS maps domain names to IP addresses.

#### Q13. Link State routing protocols (e.g., OSPF) are characterized by:
- A) Periodically sending their entire routing table to neighbors
- B) Using Hop Count as the sole metric
- C) Flooding link state updates to all routers to build a complete topology graph
- D) Susceptibility to the Count-to-Infinity problem
- **Answer: ✅ C**
- **Explanation**: Link State routers flood state info, allowing every router to maintain an identical database of the network map and calculate optimal paths locally via Dijkstra's algorithm. Distance Vector protocols send entire tables to neighbors and converge slowly.

#### Q14. What is CIDR?
- A) A routing table compression utility
- B) Classless Inter-Domain Routing, allowing flexible subnet masks without fixed class bounds
- C) A secure physical transmission protocol
- D) An IP network address range for dynamic allocation
- **Answer: ✅ B**
- **Explanation**: CIDR replaces classful boundaries (A, B, C) with a prefix length (e.g. `/22`), allowing efficient allocation of IP address spaces.

#### Q15. Network Address Translation (NAT) is used to:
- A) Assign dynamic IPs to clients joining the network
- B) Translate domain names to IP addresses
- C) Map multiple private IP addresses in a local network to a single public IP address
- D) Encrypt packets in a tunnel
- **Answer: ✅ C**
- **Explanation**: NAT allows an organization to use cheap private IP addresses internally and translates them to one or more registered public IP addresses when sending packets over the internet.

---

## 🔷 Topic 4: Transport Layer Protocols

#### Q16. Which field is NOT present in a UDP header?
- A) Source Port
- B) Length
- C) Acknowledgment Number
- D) Checksum
- **Answer: ✅ C**
- **Explanation**: The UDP header is only 8 bytes long, containing only Source Port, Destination Port, Length, and Checksum. Acknowledgment numbers are used by TCP for reliability.

#### Q17. The 3-way handshake sequence in TCP connection establishment is:
- A) SYN $\to$ ACK $\to$ SYN-ACK
- B) SYN $\to$ SYN-ACK $\to$ ACK
- C) SYN $\to$ ACK-SYN $\to$ FIN
- D) ACK $\to$ SYN $\to$ SYN-ACK
- **Answer: ✅ B**
- **Explanation**: The client sends a SYN packet, the server replies with a SYN-ACK packet, and the client sends an ACK to establish the connection.

#### Q18. Which Transport protocol is most suitable for low-latency live audio streaming?
- A) TCP
- B) UDP
- C) HTTP
- D) FTP
- **Answer: ✅ B**
- **Explanation**: Live streaming requires low latency. UDP is connectionless and has no retransmission delays (unreliable), making it ideal. TCP's packet loss recovery mechanisms would cause audio lag.

#### Q19. Port numbers are representable by how many bits?
- A) 8 bits
- B) 16 bits
- C) 32 bits
- D) 48 bits
- **Answer: ✅ B**
- **Explanation**: Port numbers are 16-bit values, spanning from `0` to `65535`.

#### Q20. TCP Congestion Control uses which state first during a new connection?
- A) Congestion Avoidance
- B) Fast Recovery
- C) Slow Start
- D) Fast Retransmit
- **Answer: ✅ C**
- **Explanation**: TCP starts in the Slow Start phase, doubling the congestion window size (cwnd) every RTT until it hits the threshold (ssthresh).

---

## 🔷 Topic 5: Application Layer Protocols

#### Q21. Which protocol dynamically assigns IP addresses, subnet masks, gateways, and DNS server IPs to network hosts?
- A) DNS
- B) ARP
- C) DHCP
- D) NAT
- **Answer: ✅ C**
- **Explanation**: DHCP (Dynamic Host Configuration Protocol) automates the configuration of TCP/IP settings for joining network clients.

#### Q22. The DORA process in DHCP stands for:
- A) Domain, Origin, Route, Address
- B) Discover, Offer, Request, Acknowledge
- C) Directory, Operation, Reply, Allocation
- D) Default, Option, Record, ARP
- **Answer: ✅ B**
- **Explanation**: DHCP client broadcasts a **Discover** packet; servers reply with IP **Offers**; client **Requests** one offer; server sends an **Acknowledgment**.

#### Q23. Which protocol is stateless and typically runs on port 80?
- A) HTTPS
- B) SMTP
- C) HTTP
- D) FTP
- **Answer: ✅ C**
- **Explanation**: HTTP is a stateless protocol (each request is processed independently) running over TCP port 80. HTTPS runs on port 443.

#### Q24. What is the port number for the Domain Name System (DNS)?
- A) Port 21
- B) Port 25
- C) Port 53
- D) Port 80
- **Answer: ✅ C**
- **Explanation**: DNS queries run on UDP port 53. If the answer size exceeds 512 bytes, it can fallback to TCP port 53.

#### Q25. Which email retrieval protocol is preferred if a user wants to view their emails from multiple devices synchronously?
- A) SMTP
- B) POP3
- C) IMAP
- D) FTP
- **Answer: ✅ C**
- **Explanation**: IMAP synchronizes emails dynamically and keeps them stored on the mail server. POP3 downloads messages to a single device and deletes them from the server.

#### Q26. FTP (File Transfer Protocol) uses how many separate ports for control and data?
- A) 1 Port
- B) 2 Ports
- C) 3 Ports
- D) Variable ports
- **Answer: ✅ B**
- **Explanation**: FTP separates command traffic (Port 21: Control connection) from actual data transfers (Port 20: Data connection).

---

## 🔷 Topic 6: Subnetting Math Practice

#### Q27. A network address is given as `192.168.1.0/26`. What is the subnet mask?
- A) `255.255.255.0`
- B) `255.255.255.192`
- C) `255.255.255.128`
- D) `255.255.255.224`
- **Answer: ✅ B**
- **Explanation**: A `/26` mask has 26 consecutive 1s in binary. 
  - Octet 1-3: 24 bits (`255.255.255`).
  - Octet 4: 2 bits (`11000000` in binary = $128 + 64 = 192$).
  - Hence, the mask is `255.255.255.192`.

#### Q28. For the subnet `10.0.0.0/29`, how many usable host IP addresses are available per subnet?
- A) 8
- B) 6
- C) 14
- D) 30
- **Answer: ✅ B**
- **Explanation**: A `/29` mask leaves $32 - 29 = 3$ host bits.
  - Total host addresses = $2^3 = 8$.
  - Usable host addresses = $2^3 - 2 = 6$ (subtracting Network ID and Broadcast ID).

#### Q29. Given the IP address `192.168.5.150/26`, what is the Network ID?
- A) `192.168.5.0`
- B) `192.168.5.128`
- C) `192.168.5.64`
- D) `192.168.5.192`
- **Answer: ✅ B**
- **Explanation**: A `/26` split creates subnets block sizes of $64$ ($256 - 192 = 64$):
  - Subnet 0: `0` to `63`
  - Subnet 1: `64` to `127`
  - Subnet 2: `128` to `191`
  - Since host IP `150` lies in the range $[128, 191]$, the network ID is `192.168.5.128`.

#### Q30. For the IP subnet block `172.16.0.0/22`, what is the broadcast address?
- A) `172.16.0.255`
- B) `172.16.3.255`
- C) `172.16.255.255`
- D) `172.16.4.255`
- **Answer: ✅ B**
- **Explanation**: A `/22` has $32-22 = 10$ host bits.
  - Total IPs = $2^{10} = 1024$.
  - $1024$ IPs represent exactly 4 full `/24` subnets (from `172.16.0.0` to `172.16.3.255`).
  - Thus, the broadcast address is `172.16.3.255`.

---

## 🔷 Topic 7: Network Security & Cryptography

#### Q31. In asymmetric cryptography, if Alice wants to encrypt a message to send to Bob securely:
- A) Alice encrypts using her private key
- B) Alice encrypts using Bob's public key
- C) Alice encrypts using Bob's private key
- D) Alice encrypts using a shared password key
- **Answer: ✅ B**
- **Explanation**: To ensure confidentiality, Alice encrypts with Bob's public key. Only Bob possesses the corresponding private key required to decrypt it.

#### Q32. RSA is an example of which cryptographic system?
- A) Symmetric Key Cryptography
- B) Asymmetric Key Cryptography
- C) Hash function
- D) Message Authentication Code (MAC)
- **Answer: ✅ B**
- **Explanation**: RSA (Rivest-Shamir-Adleman) is an asymmetric algorithm based on prime factorization.

#### Q33. A firewall is designed to:
- A) Store backups of network logs
- B) Filter incoming and outgoing network traffic based on rules
- C) Accelerate routing throughput
- D) Automatically assign IP addresses
- **Answer: ✅ B**
- **Explanation**: Firewalls inspect packets and block unauthorized network access based on security policies.

#### Q34. A Virtual Private Network (VPN) provides security across public networks by:
- A) Forcing connection-oriented TCP
- B) Creating a secure, encrypted tunnel
- C) Doubling bandwidth capacity
- D) Assigning physical MAC addresses
- **Answer: ✅ B**
- **Explanation**: VPNs encrypt communications and wrap packets in tunnel headers, ensuring privacy and data integrity over public networks.

#### Q35. Non-repudiation in cryptography means:
- A) The message cannot be intercepted
- B) The sender cannot deny sending the message
- C) The message is compressed
- D) The receiver must reply to the sender
- **Answer: ✅ B**
- **Explanation**: Digital signatures provide non-repudiation: since only the sender possesses their private key, they cannot deny initiating the signature.

---

## 🔷 Topic 8: General Conceptual Review

#### Q36. What is the default transmission rate calculation for a TDM circuit transmitting 8-bit slots at 4000 frames per second?
- A) $32\text{ kbps}$
- B) $500\text{ kbps}$
- C) $32\text{ bps}$
- D) $500\text{ bps}$
- **Answer: ✅ A**
- **Explanation**: 
  - $\text{Bit rate} = \text{Frame rate} \times \text{Bits per frame}$
  - $\text{Bit rate} = 4000 \times 8 = 32,000\text{ bps} = 32\text{ kbps}$.

#### Q37. In packet switching compared to circuit switching:
- A) A dedicated physical path is reserved
- B) Resource utilization is lower
- C) Packets share links dynamically, which can cause queuing delays and packet loss
- D) Call setup is always required
- **Answer: ✅ C**
- **Explanation**: Packet switching breaks data into packets and routes them dynamically. This increases resource efficiency but introduces queuing delays and packet loss under heavy load, unlike circuit switching which reserves dedicated channels.

#### Q38. Which layer performs packet routing and network congestion control?
- A) Data Link Layer
- B) Network Layer
- C) Transport Layer
- D) Session Layer
- **Answer: ✅ B**
- **Explanation**: Layer 3 (Network) handles routing and routing congestion management.

#### Q39. What type of cable uses a core surrounded by outer shielding and is used for cable broadband?
- A) UTP
- B) Coaxial
- C) Fiber optic
- D) Shielded twisted pair
- **Answer: ✅ B**
- **Explanation**: Coaxial cables have a central conductor shielded by metal braiding, which is common in cable TV/broadband networks.

#### Q40. Which protocol retrieves email but leaves a copy on the server, synchronization-free?
- A) SMTP
- B) POP3
- C) IMAP
- D) HTTP
- **Answer: ✅ B**
- **Explanation**: POP3 retrieves mail by downloading it. Unlike IMAP, it does not keep client modifications synchronized back to the server.

#### Q41. In an IP network, what is the default gateway address?
- A) The loopback IP address
- B) The IP address of the local DNS server
- C) The IP address of the router interface that connects the local subnet to external networks
- D) The client's physical MAC address
- **Answer: ✅ C**
- **Explanation**: The default gateway is the entry point used by local machines to send packets to other subnets.

#### Q42. Which network topology forms a single line with terminator ends?
- A) Bus
- B) Star
- C) Mesh
- D) Ring
- **Answer: ✅ A**
- **Explanation**: Bus topology links nodes to a central backbone line capped with terminators.

#### Q43. What is the loopback test IP range?
- A) `10.0.0.0 - 10.255.255.255`
- B) `192.168.0.0 - 192.168.255.255`
- C) `127.0.0.0 - 127.255.255.255`
- D) `172.16.0.0 - 172.31.255.255`
- **Answer: ✅ C**
- **Explanation**: The entire `127.0.0.0/8` subnet is reserved for loopback testing.

#### Q44. The Transport Layer uses what identifier to deliver data segments to correct software processes?
- A) IP Address
- B) MAC Address
- C) Port Number
- D) Process ID
- **Answer: ✅ C**
- **Explanation**: Port numbers map connections to specific application endpoints at Layer 4.

#### Q45. Which protocol utilizes 128-bit addresses?
- A) IPv4
- B) IPv6
- C) MAC
- D) DNS
- **Answer: ✅ B**
- **Explanation**: IPv6 expands address sizes to 128 bits to accommodate more devices.

#### Q46. What does a "denial of service" (DoS) attack attempt to accomplish?
- A) Steal user credentials
- B) Intercept private communications
- C) Make a network resource unavailable to legitimate users by flooding it with traffic
- D) Modify files on the server
- **Answer: ✅ C**
- **Explanation**: DoS/DDoS attacks flood a server/network resource with requests, exhausting its capacity and rendering it unavailable.

#### Q47. The CSMA/CD protocol acts to:
- A) Prevent collisions before they occur
- B) Detect collisions in wired networks and broadcast a jam signal to trigger backoff timers
- C) Encrypt data transmissions
- D) Route packets
- **Answer: ✅ B**
- **Explanation**: CSMA/CD senses wired lines for collisions during transmissions, halts immediately, and broadcasts a jam signal to trigger random backoff timers.

#### Q48. Symmetric key algorithms (e.g., AES) are preferred over asymmetric ones (e.g., RSA) for bulk data encryption because:
- A) They are much faster and computationally lighter
- B) They do not require key exchanges
- C) They are more secure against quantum computers
- D) They support digital signatures
- **Answer: ✅ A**
- **Explanation**: Symmetric key systems are computationally faster, making them ideal for encrypting bulk data, while asymmetric systems are used for key exchanges and digital signatures.

#### Q49. Which network device is a Layer 3 device that routes packets between different networks?
- A) Hub
- B) Switch
- C) Router
- D) Bridge
- **Answer: ✅ C**
- **Explanation**: Routers examine IP headers (Layer 3) to route packets across subnets. Hubs operate at Layer 1, and switches operate at Layer 2.

#### Q50. What is the transmission rate if a signal encodes 4 bits per symbol and has a baud rate of 2000 baud?
- A) $500\text{ bps}$
- B) $2000\text{ bps}$
- C) $8000\text{ bps}$
- D) $16000\text{ bps}$
- **Answer: ✅ C**
- **Explanation**: 
  - $\text{Bit rate} = \text{Baud rate} \times \text{Bits per symbol}$
  - $\text{Bit rate} = 2000 \times 4 = 8000\text{ bps}$.

---

## 🔷 Topic 9: Expanded Problem Bank (Advanced Math & Detailed Protocols)

#### Q51. A host wants to transmit a file of size $1.5\text{ megabytes}$ ($1.5 \times 10^6\text{ bytes}$) over a point-to-point link of bandwidth $10\text{ Mbps}$ ($10 \times 10^6\text{ bits per second}$). If the distance is $2000\text{ km}$ and signal speed in the medium is $2 \times 10^8\text{ m/s}$, calculate the total time taken for the file to be completely received.
- A) $1.21\text{ seconds}$
- B) $1.20\text{ seconds}$
- C) $1.51\text{ seconds}$
- D) $1.50\text{ seconds}$
- **Answer: ✅ A**
- **Explanation**:
  - **Transmission Delay** ($T_t$) = $\frac{\text{File Size}}{\text{Bandwidth}} = \frac{1.5 \times 10^6\text{ bytes} \times 8\text{ bits/byte}}{10 \times 10^6\text{ bps}} = \frac{12 \times 10^6}{10 \times 10^6} = 1.2\text{ seconds}$.
  - **Propagation Delay** ($T_p$) = $\frac{\text{Distance}}{\text{Speed}} = \frac{2 \times 10^6\text{ m}}{2 \times 10^8\text{ m/s}} = 0.01\text{ seconds}$.
  - **Total Delay** = $T_t + T_p = 1.2 + 0.01 = 1.21\text{ seconds}$.

#### Q52. A sender and receiver are connected by a link with a propagation delay of $50\text{ ms}$ and a bandwidth of $1\text{ Gbps}$. What is the Bandwidth-Delay Product (BDP) in bits, representing the maximum volume of data that can fill the transmission pipe?
- A) $50,000,000\text{ bits}$
- B) $100,000,000\text{ bits}$
- C) $5,000,000\text{ bits}$
- D) $500,000\text{ bits}$
- **Answer: ✅ A**
- **Explanation**:
  - $\text{BDP} = \text{Bandwidth} \times \text{Propagation Delay}$
  - $\text{BDP} = 10^9\text{ bps} \times 50 \times 10^{-3}\text{ s} = 50 \times 10^6\text{ bits} = 50,000,000\text{ bits}$.

#### Q53. In a Go-Back-N sliding window protocol, sequence numbers are represented by $k = 4$ bits. What is the maximum sender window size ($W_s$)?
- A) 16
- B) 15
- C) 8
- D) 7
- **Answer: ✅ B**
- **Explanation**:
  - In Go-Back-N, the sender window size $W_s$ must satisfy $W_s \le 2^k - 1$.
  - With $k = 4$, $2^4 - 1 = 16 - 1 = 15$.
  - This prevents the receiver from confusing a retransmitted window with a new window.

#### Q54. In a Selective Repeat sliding window protocol, sequence numbers are represented by $k = 3$ bits. What is the maximum sender window size ($W_s$)?
- A) 8
- B) 7
- C) 4
- D) 3
- **Answer: ✅ C**
- **Explanation**:
  - In Selective Repeat, the sender and receiver window sizes are equal, and the maximum window size is $W_s = 2^{k-1}$.
  - With $k = 3$, $2^{3-1} = 2^2 = 4$.

#### Q55. If a Hamming code uses 4 data bits and 3 redundant parity bits to construct a 7-bit codeword, what is the minimum Hamming distance ($d_{\min}$) required to correct up to 2-bit transmission errors?
- A) 2
- B) 3
- C) 4
- D) 5
- **Answer: ✅ D**
- **Explanation**:
  - To correct up to $t$ errors, the minimum Hamming distance of the code must satisfy: $d_{\min} \ge 2t + 1$.
  - Given $t = 2$, we have $d_{\min} \ge 2(2) + 1 = 5$.

#### Q56. In the standard IEEE 802.3 Ethernet frame, what is the purpose of the Start Frame Delimiter (SFD) byte?
- A) It provides error detection for the preamble.
- B) It indicates the length of the payload.
- C) It is a fixed pattern `10101011` marking the exact beginning of the frame addressing fields.
- D) It carries collision detection flags.
- **Answer: ✅ C**
- **Explanation**:
  - The Ethernet preamble consists of 7 bytes of alternating `1`s and `0`s (`10101010`) used for clock synchronization.
  - The 8th byte is the SFD (`10101011`), signaling the receiver that the next byte is the Destination MAC address.

#### Q57. An IP packet of total size $4000\text{ bytes}$ (including a $20\text{-byte}$ header) must travel over a link with an MTU (Maximum Transmission Unit) of $1500\text{ bytes}$. What is the fragmentation offset value in the second fragment?
- A) 0
- B) 185
- C) 1480
- D) 740
- **Answer: ✅ B**
- **Explanation**:
  - The link MTU is $1500\text{ bytes}$. Allowing $20\text{ bytes}$ for the IP header, the maximum data payload size in each fragment is $1500 - 20 = 1480\text{ bytes}$ (which is divisible by 8, as required for the Fragment Offset).
  - Fragment 1: Payload size = $1480\text{ bytes}$. Fragment Offset = $0$.
  - Fragment 2: Payload size = $1480\text{ bytes}$. Fragment Offset = $\frac{1480}{8} = 185$.
  - Fragment 3: Payload size = $4000 - 20 - 1480 - 1480 = 1020\text{ bytes}$. Fragment Offset = $\frac{2960}{8} = 370$.

#### Q58. In an IPv4 header, the value of the Internet Header Length (IHL) field is binary `0110` (6 in decimal). What is the total length of the IPv4 header in bytes?
- A) $6\text{ bytes}$
- B) $20\text{ bytes}$
- C) $24\text{ bytes}$
- D) $30\text{ bytes}$
- **Answer: ✅ C**
- **Explanation**:
  - The IHL field represents the length of the IP header in units of 32-bit (4-byte) words.
  - Header Length = $\text{IHL value} \times 4\text{ bytes} = 6 \times 4 = 24\text{ bytes}$.

#### Q59. What happens to the Time-to-Live (TTL) field in an IPv4 header when a packet is processed by a router?
- A) It is incremented by 1. If it hits 255, the packet is discarded.
- B) It is decremented by 1. If it reaches 0, the packet is discarded and an ICMP "Time Exceeded" message is sent back to the sender.
- C) It is left unchanged unless the network is congested.
- D) It is set to the hop count calculated by OSPF.
- **Answer: ✅ B**
- **Explanation**:
  - Routers decrement the TTL field by 1 to prevent packets from circulating endlessly in routing loops.
  - If TTL drops to 0, the router drops the packet and sends an ICMP Type 11 (Time Exceeded) message to the source.

#### Q60. Which of the following fields present in the IPv4 header was removed in the IPv6 header to simplify header processing?
- A) Version
- B) Payload Length
- C) Source Address
- D) Header Checksum
- **Answer: ✅ D**
- **Explanation**:
  - The Header Checksum field was eliminated in IPv6.
  - Since lower layers (Data Link: CRC) and upper layers (Transport: TCP/UDP checksum) already perform error checking, removing it at Layer 3 avoids recalculating the checksum at every hop, speeding up routing.

#### Q61. A TCP SYN Flood attack exploits which vulnerability in TCP connection establishment?
- A) The client sends too many ACK packets, filling the server's input stream.
- B) The server allocates system resources (half-open connection state) upon receiving a SYN, waiting for an ACK that never arrives.
- C) The server is forced to perform slow asymmetric decryption operations.
- D) The client dynamically adjusts the sliding window size to 0.
- **Answer: ✅ B**
- **Explanation**:
  - During a SYN flood, the attacker sends multiple SYN packets with spoofed source IPs.
  - The server replies with SYN-ACKs and allocates memory in its connection queue (SYN backlog) for these "half-open" connections, exhausting resources and blocking legitimate users.

#### Q62. Which of the following represents the correct sequence of TCP flags during normal connection teardown?
- A) FIN $\to$ ACK $\to$ FIN-ACK $\to$ ACK
- B) FIN $\to$ ACK $\to$ FIN $\to$ ACK
- C) RST $\to$ RST-ACK $\to$ FIN $\to$ ACK
- D) FIN $\to$ SYN $\to$ ACK $\to$ FIN
- **Answer: ✅ B**
- **Explanation**:
  - TCP is a full-duplex protocol, so each direction of the connection must be closed independently.
  - Node A sends a FIN, Node B acknowledges it (ACK).
  - Later, Node B sends its own FIN, and Node A acknowledges it (ACK).

#### Q63. Which mechanism is used to resolve the "Silly Window Syndrome" caused by a sender transmitting data in tiny, single-byte segments?
- A) Nagle's Algorithm
- B) Clark's Solution
- C) Slow Start
- D) Karn's Algorithm
- **Answer: ✅ A**
- **Explanation**:
  - Silly Window Syndrome can be caused by the sender (sending 1 byte of data wrapped in 40 bytes of header) or the receiver (advertising tiny window updates).
  - **Nagle's Algorithm** fixes the sender problem by buffering small outgoing packets and waiting to send them until a full-sized segment can be formed or an ACK is received.
  - **Clark's Solution** fixes the receiver problem by preventing the receiver from advertising small window updates.

#### Q64. When TCP detects packet loss via three duplicate ACKs (Fast Retransmit), how does its congestion control algorithm react?
- A) It resets the congestion window (cwnd) to 1 MSS and enters Slow Start.
- B) It halves the congestion window (cwnd), sets ssthresh to the new cwnd, and enters Congestion Avoidance.
- C) It doubles the congestion window size.
- D) It halts transmission completely and terminates the connection.
- **Answer: ✅ B**
- **Explanation**:
  - Three duplicate ACKs suggest the network is still transferring some packets (mild congestion). Thus, TCP performs a multiplicative decrease by halving `cwnd` and enters Congestion Avoidance (Fast Recovery).
  - A timeout suggests severe congestion, in which case TCP resets `cwnd` to 1 MSS and restarts with Slow Start.

#### Q65. A network manager has the network address `192.168.1.0/24`. They need to create four subnets: Subnet A (120 hosts), Subnet B (60 hosts), Subnet C (30 hosts), and Subnet D (10 hosts). Which subnetting strategy is required?
- A) Fixed Length Subnet Masking (FLSM)
- B) Supernetting
- C) Variable Length Subnet Masking (VLSM)
- D) Dynamic Host Allocation
- **Answer: ✅ C**
- **Explanation**:
  - Since the subnets require vastly different numbers of hosts, FLSM would waste addresses.
  - VLSM allows applying different subnet masks to each subnet (e.g., Subnet A uses `/25` for 128 IPs, Subnet B uses `/26` for 64 IPs, Subnet C uses `/27` for 32 IPs, Subnet D uses `/28` for 16 IPs).

#### Q66. An ISP aggregates the following four CIDR blocks: `200.10.0.0/24`, `200.10.1.0/24`, `200.10.2.0/24`, and `200.10.3.0/24`. What is the single aggregated prefix advertised by the ISP?
- A) `200.10.0.0/22`
- B) `200.10.0.0/23`
- C) `200.10.1.0/22`
- D) `200.10.0.0/21`
- **Answer: ✅ A**
- **Explanation**:
  - The 3rd octets in binary are:
    - 0: `00000000`
    - 1: `00000001`
    - 2: `00000010`
    - 3: `00000011`
  - The first 6 bits of the 3rd octet are identical (`000000xx`).
  - Thus, the network prefix changes from 24 bits to $24 - 2 = 22$ bits, yielding `200.10.0.0/22`.

#### Q67. A router receives a packet with destination IP `198.162.5.85`. Its routing table contains the following entries. Which entry will the router match to forward the packet?
- Entry 1: `198.162.0.0/16` via Interface 1
- Entry 2: `198.162.5.0/24` via Interface 2
- Entry 3: `198.162.5.64/26` via Interface 3
- Entry 4: `0.0.0.0/0` via Interface 4
- A) Entry 1
- B) Entry 2
- C) Entry 3
- D) Entry 4
- **Answer: ✅ C**
- **Explanation**:
  - The router uses **Longest Prefix Match** to select the most specific route.
  - The destination IP `85` in binary is `01010101`.
  - For Entry 3 (`198.162.5.64/26`), the subnet range is `64` to `127` (since /26 has a block size of 64). `85` falls in this range.
  - Entry 3 has the longest prefix mask (/26 is longer than /24 and /16), so it is selected.

#### Q68. The "Split Horizon" heuristic prevents routing loops in Distance Vector networks by:
- A) Restricting routers from learning paths with hop counts higher than 15.
- B) Halting routing updates during network topology convergence.
- C) Stopping a router from advertising a route back out the same interface it used to learn that route.
- D) Periodically clearing CAM tables.
- **Answer: ✅ C**
- **Explanation**:
  - If Router A learns from Router B that a path to Network X exists, Router A will not advertise this path back to Router B. This avoids cyclic loops where B thinks it can reach X through A, while A thinks it can reach X through B.

#### Q69. In the OSPF routing protocol, how is the default interface cost calculated to determine link weights for Dijkstra's algorithm?
- A) $\text{Cost} = \text{Hop Count}$
- B) $\text{Cost} = \frac{10^8}{\text{Bandwidth in bps}}$
- C) $\text{Cost} = \text{Propagation Delay in ms} \times 2$
- D) $\text{Cost} = \text{Randomized backoff}$
- **Answer: ✅ B**
- **Explanation**:
  - OSPF uses a metric called Cost, inversely proportional to interface bandwidth.
  - $\text{Cost} = \frac{\text{Reference Bandwidth (100 Mbps)}}{\text{Interface Bandwidth}}$.
  - A faster link (e.g., 1 Gbps) has a lower cost than a slower link (e.g., 10 Mbps), prioritizing high-speed links.

#### Q70. Which of the following statements is true regarding the Border Gateway Protocol (BGP)?
- A) It is an Interior Gateway Protocol (IGP) based on Link State routing.
- B) It operates over UDP port 520.
- C) It is a Path Vector protocol used for routing between Autonomous Systems (AS) on the Internet.
- D) It uses hop count as its primary metric.
- **Answer: ✅ C**
- **Explanation**:
  - BGP is the routing protocol of the global Internet, classified as an Exterior Gateway Protocol (EGP).
  - It uses a Path Vector algorithm to prevent routing loops between Autonomous Systems and runs reliably over TCP port 179.

#### Q71. During a DNS query sequence, which server is queried immediately if the Local DNS Resolver has a cache miss?
- A) Authoritative Name Server
- B) Top-Level Domain (TLD) Server
- C) Root Name Server
- D) Primary Domain Controller
- **Answer: ✅ C**
- **Explanation**:
  - When resolving a domain name, the Local DNS Resolver first queries a **Root Name Server** (`.`).
  - The root server redirects the resolver to the appropriate TLD server (e.g., `.com`), which in turn redirects it to the Authoritative server.

#### Q72. A system administrator wants to map an alias domain name (e.g., `www.example.com`) to the canonical domain name (e.g., `example.org`). Which type of DNS Resource Record must be created?
- A) A Record
- B) AAAA Record
- C) CNAME Record
- D) MX Record
- **Answer: ✅ C**
- **Explanation**:
  - **A Record** maps a hostname to an IPv4 address.
  - **AAAA Record** maps a hostname to an IPv6 address.
  - **CNAME (Canonical Name) Record** maps an alias domain name to another domain name.
  - **MX (Mail Exchanger) Record** specifies the mail server for the domain.

#### Q73. In a large enterprise network, how can a client obtain an IP address from a DHCP server located on a completely different IP subnet?
- A) By broadcasting a DORA discover message across the WAN router.
- B) By using a DHCP Relay Agent (helper address) on the local router to forward broadcast DHCP requests as unicast packets to the server.
- C) By setting its static IP to `127.0.0.1` temporarily.
- D) DHCP cannot operate across subnet boundaries.
- **Answer: ✅ B**
- **Explanation**:
  - DHCP messages are initially sent as local broadcasts, which routers do not forward.
  - A **DHCP Relay Agent** configured on the local router intercepts these broadcasts and forwards them as unicast packets directly to the remote DHCP server's IP address.

#### Q74. Which of the following features was introduced in HTTP/1.1 to optimize connection performance compared to HTTP/1.0?
- A) Server Push
- B) Header Compression (HPACK)
- C) Persistent Connections (Keep-Alive by default)
- D) Binary Frame Stream Multiplexing
- **Answer: ✅ C**
- **Explanation**:
  - HTTP/1.0 opened a new TCP connection for every single request/response pair, creating massive handshake overhead.
  - HTTP/1.1 introduced **persistent connections**, keeping the TCP connection open for multiple requests by default. HTTP/2.0 introduced multiplexing, binary framing, and header compression.

#### Q75. In the modern TLS 1.3 cryptographic handshake, how is the symmetric session key established?
- A) The client encrypts a pre-master secret using the server's RSA public key.
- B) The client and server run a Diffie-Hellman key exchange during the initial handshake exchange.
- C) The server sends the raw key to the client encrypted with rot13.
- D) The key is derived directly from the MAC address.
- **Answer: ✅ B**
- **Explanation**:
  - TLS 1.3 deprecated static RSA key exchange to achieve **Forward Secrecy**.
  - Instead, it uses ephemeral Diffie-Hellman key exchange, allowing the client and server to securely calculate a shared secret key without ever transmitting it over the wire.

#### Q76. Which SMTP command is used by a mail client to initiate the SMTP envelope containing the sender's email address?
- A) HELO
- B) RCPT TO
- C) MAIL FROM
- D) DATA
- **Answer: ✅ C**
- **Explanation**:
  - `HELO` / `EHLO` starts the SMTP session.
  - `MAIL FROM` specifies the sender's address (envelope sender).
  - `RCPT TO` specifies the recipient's address.
  - `DATA` initiates the transmission of the actual email body.

#### Q77. An IP packet is fragmented. The first fragment contains bytes 0 to 1479 of the payload. What is the value of the More Fragments (MF) flag in this first fragment?
- A) MF = 0
- B) MF = 1
- C) MF = 255
- D) MF = 185
- **Answer: ✅ B**
- **Explanation**:
  - The More Fragments (MF) flag is a 1-bit field in the IP header.
  - `MF = 1` indicates that more fragments of the original packet follow.
  - `MF = 0` indicates that this is the last fragment.

#### Q78. A switch is configured to forward frames immediately after reading the Destination MAC address (first 6 bytes of the frame), without checking for errors. Which switching method is this?
- A) Store-and-Forward
- B) Cut-Through
- C) Fragment-Free
- D) Adaptive Switching
- **Answer: ✅ B**
- **Explanation**:
  - **Cut-Through switching** reads only the destination MAC and immediately starts forwarding the frame, providing the lowest latency but forwarding corrupted frames.
  - **Store-and-Forward** buffers the entire frame and validates the FCS checksum before forwarding, ensuring zero-error propagation.
  - **Fragment-Free** reads the first 64 bytes (the minimum size of an Ethernet frame) to filter out collision fragments before forwarding.

#### Q79. How does replacing a network Hub with a Layer 2 Switch affect the collision and broadcast domains of a network?
- A) It increases the number of collision domains and decreases the number of broadcast domains.
- B) It breaks the single collision domain into multiple dedicated collision domains (one per port) while keeping a single broadcast domain.
- C) It creates a single collision domain and multiple broadcast domains.
- D) It has no effect on either domain.
- **Answer: ✅ B**
- **Explanation**:
  - Hubs share bandwidth; all ports belong to one collision domain and one broadcast domain.
  - Switches isolate ports; each port is its own collision domain (preventing collisions between devices on different ports). However, broadcasts (like ARP requests) are still forwarded to all ports, keeping a single broadcast domain.

#### Q80. In VLAN tagging (IEEE 802.1Q), how many bytes are inserted into the original Ethernet frame header to identify the VLAN ID?
- A) 2 bytes
- B) 4 bytes
- C) 8 bytes
- D) 16 bytes
- **Answer: ✅ B**
- **Explanation**:
  - IEEE 802.1Q inserts a 4-byte VLAN tag into the Ethernet frame header (between the Source MAC address and EtherType fields).
  - This tag contains a 12-bit VLAN Identifier (VID), supporting up to $2^{12} = 4096$ VLANs.

#### Q81. A noisy channel has a bandwidth of $4\text{ kHz}$ and a Signal-to-Noise Ratio (SNR) of $31$ (or roughly $15\text{ dB}$). According to the Shannon Capacity Theorem, what is the maximum theoretical channel capacity?
- A) $120\text{ kbps}$
- B) $20\text{ kbps}$
- C) $4\text{ kbps}$
- D) $8\text{ kbps}$
- **Answer: ✅ B**
- **Explanation**:
  - **Shannon Capacity Formula**: $C = B \log_2(1 + \text{SNR})$
  - Given $B = 4000\text{ Hz}$ and $\text{SNR} = 31$:
  - $C = 4000 \log_2(1 + 31) = 4000 \log_2(32) = 4000 \times 5 = 20,000\text{ bps} = 20\text{ kbps}$.

#### Q82. According to Nyquist's theorem, what is the maximum bit rate for a noiseless channel with a bandwidth of $3\text{ kHz}$ transmitting a signal with 4 signal levels?
- A) $6\text{ kbps}$
- B) $12\text{ kbps}$
- C) $24\text{ kbps}$
- D) $3\text{ kbps}$
- **Answer: ✅ B**
- **Explanation**:
  - **Nyquist Bit Rate Formula**: $\text{Bit Rate} = 2 \times B \times \log_2(L)$
  - Given $B = 3000\text{ Hz}$ and $L = 4$ levels:
  - $\text{Bit Rate} = 2 \times 3000 \times \log_2(4) = 6000 \times 2 = 12,000\text{ bps} = 12\text{ kbps}$.

#### Q83. How does Slotted ALOHA improve on the maximum throughput of Pure ALOHA?
- A) By enforcing carrier sensing.
- B) By synchronizing time into slots, restricting nodes to only transmit at the beginning of a time slot.
- C) By adding parity bits to frames.
- D) By utilizing Token passing rings.
- **Answer: ✅ B**
- **Explanation**:
  - In Pure ALOHA, a packet can collide with any packet sent within a vulnerable period of $2T_f$.
  - In Slotted ALOHA, the vulnerable period is halved to $1T_f$ because transmissions are aligned to slot boundaries. This doubles the maximum throughput from $18.4\%$ to $36.8\%$.

#### Q84. The maximum efficiency of a Pure ALOHA channel occurs at a channel traffic load ($G$) of:
- A) $G = 1.0$
- B) $G = 0.5$
- C) $G = 2.0$
- D) $G = 0.184$
- **Answer: ✅ B**
- **Explanation**:
  - The throughput equation for Pure ALOHA is $S = G \cdot e^{-2G}$.
  - Differentiating with respect to $G$ and setting it to 0 yields maximum throughput when $G = 0.5$.
  - At $G = 0.5$, $S = 0.5 \cdot e^{-1} \approx 18.4\%$.

#### Q85. The maximum efficiency of a Slotted ALOHA channel occurs at a channel traffic load ($G$) of:
- A) $G = 0.5$
- B) $G = 1.0$
- C) $G = 2.0$
- D) $G = 0.368$
- **Answer: ✅ B**
- **Explanation**:
  - The throughput equation for Slotted ALOHA is $S = G \cdot e^{-G}$.
  - Differentiating with respect to $G$ yields maximum throughput when $G = 1.0$.
  - At $G = 1.0$, $S = 1.0 \cdot e^{-1} \approx 36.8\%$.

#### Q86. What is the key difference between the Leaky Bucket and Token Bucket traffic policing algorithms?
- A) Leaky Bucket allows bursty traffic, while Token Bucket enforces a constant, smooth output rate.
- B) Leaky Bucket enforces a constant output rate, discarding or queuing bursts, while Token Bucket allows bursts up to the capacity of the accumulated tokens.
- C) Leaky Bucket operates at Layer 3, while Token Bucket operates at Layer 2.
- D) Token Bucket does not use buffers.
- **Answer: ✅ B**
- **Explanation**:
  - **Leaky Bucket** acts like a bucket with a small hole, releasing data at a constant rate regardless of input bursts (ideal for traffic shaping).
  - **Token Bucket** accumulates tokens over time. If a burst arrives, it can be transmitted immediately as long as tokens are available, allowing for bursts.

#### Q87. An administrator uses the `ping` utility to check network connectivity. Which ICMP message types are exchanged?
- A) ICMP Type 3 (Destination Unreachable) and Type 11 (Time Exceeded).
- B) ICMP Type 8 (Echo Request) and Type 0 (Echo Reply).
- C) ICMP Type 5 (Redirect) and Type 4 (Source Quench).
- D) ICMP Type 9 and Type 10.
- **Answer: ✅ B**
- **Explanation**:
  - `ping` sends an ICMP Type 8 (Echo Request) packet.
  - The target host replies with an ICMP Type 0 (Echo Reply) packet if reachable.

#### Q88. What is the purpose of the TCP Keep-Alive mechanism?
- A) It prevents the client's physical link from going into power-saving mode.
- B) It periodically transmits empty segments to verify if an inactive connection is still active or if the peer has crashed.
- C) It automatically renegotiates Diffie-Hellman keys.
- D) It doubles the congestion window size.
- **Answer: ✅ B**
- **Explanation**:
  - If a connection is idle for long periods without sending data, routers or firewalls might silently drop the state.
  - TCP Keep-Alive sends probe segments to check if the connection is still alive, preventing inactive connections from consuming resources on servers.

#### Q89. In a TCP segment, the Maximum Segment Size (MSS) option parameter:
- A) Includes the size of the IP and TCP headers.
- B) Specifies the maximum amount of TCP user data payload in a single segment.
- C) Is dynamically updated during the congestion avoidance phase.
- D) Represents the size of the receiver's socket buffer.
- **Answer: ✅ B**
- **Explanation**:
  - MSS specifies the largest block of payload data that a device can receive in a single TCP segment.
  - It does not count the headers (typically 40 bytes total for TCP + IP), only the application payload.

#### Q90. The UDP checksum calculation includes a "pseudo-header" containing fields from which layer?
- A) Application Layer (HTTP payload length)
- B) Network Layer (Source and Destination IP addresses)
- C) Data Link Layer (MAC addresses)
- D) Physical Layer (baud rate)
- **Answer: ✅ B**
- **Explanation**:
  - To protect against routing delivery errors, UDP constructs a 12-byte pseudo-header containing the Source IP, Destination IP, Protocol (17), and UDP Length.
  - This ensures that if a packet is misrouted to the wrong destination IP, the checksum will fail.

#### Q91. For the network prefix `10.0.0.0` with subnet mask `255.240.0.0`, how many subnets are created, and how many usable hosts are available per subnet?
- A) 16 subnets, 1,048,574 usable hosts.
- B) 8 subnets, 524,286 usable hosts.
- C) 32 subnets, 2,097,150 usable hosts.
- D) 64 subnets, 4,194,302 usable hosts.
- **Answer: ✅ A**
- **Explanation**:
  - `10.0.0.0` is a Class A network (default mask `/8` = `255.0.0.0`).
  - The mask `255.240.0.0` in binary has 12 consecutive 1s (`11111111.11110000.00000000.00000000`).
  - Borrowed bits ($s$) = $12 - 8 = 4$ bits. Subnets = $2^4 = 16$.
  - Host bits ($h$) = $32 - 12 = 20$ bits. Usable hosts = $2^{20} - 2 = 1,048,576 - 2 = 1,048,574$ per subnet.

#### Q92. What is the directed broadcast address for the IP subnet `172.16.64.0/18`?
- A) `172.16.64.255`
- B) `172.16.127.255`
- C) `172.16.255.255`
- D) `172.16.191.255`
- **Answer: ✅ B**
- **Explanation**:
  - A `/18` mask leaves $32 - 18 = 14$ host bits.
  - Block size in the 3rd octet = $2^{24 - 18} = 2^6 = 64$.
  - Subnet starts at `172.16.64.0`. The next subnet starts at `172.16.128.0`.
  - Thus, the broadcast address of this subnet is `172.16.127.255`.

#### Q93. An host has the IP address `172.30.150.25` and subnet mask `255.255.240.0`. What is its Network ID?
- A) `172.30.128.0`
- B) `172.30.144.0`
- C) `172.30.150.0`
- D) `172.30.0.0`
- **Answer: ✅ B**
- **Explanation**:
  - The mask `255.255.240.0` (/20) has a block size of 16 in the 3rd octet ($256 - 240 = 16$).
  - Subnets start at: `0, 16, 32, ..., 128, 144, 160`.
  - The 3rd octet of the host IP is `150`, which falls between `144` and `159`.
  - Thus, the Network ID is `172.30.144.0`.

#### Q94. In CSMA/CD, if a node experiences its 4th consecutive collision during transmission, what is the maximum backoff time it could select, measured in slot times?
- A) 4 slot times
- B) 8 slot times
- C) 15 slot times
- D) 31 slot times
- **Answer: ✅ C**
- **Explanation**:
  - The binary exponential backoff algorithm selects a random integer $r$ in the range $[0, 2^n - 1]$, where $n$ is the collision count.
  - For $n = 4$, the range is $[0, 2^4 - 1] = [0, 15]$.
  - The maximum backoff value is 15 slot times.

#### Q95. Why does single-mode fiber optic cable have much lower dispersion compared to multi-mode fiber?
- A) It uses a thicker core, allowing light to propagate in a straight line.
- B) Its core is extremely narrow, allowing only a single mode (ray) of light to propagate, eliminating modal dispersion.
- C) It is completely shielded by copper braiding.
- D) It operates at lower frequencies.
- **Answer: ✅ B**
- **Explanation**:
  - Multi-mode fiber has a thicker core, allowing light rays to travel along different paths (modes) at different speeds, causing **modal dispersion** (signal spreading).
  - Single-mode fiber has a tiny core ($9\mu\text{m}$) that restricts propagation to a single path, removing modal dispersion.

#### Q96. Coaxial cables used for thin Ethernet (10Base2) and cable television have what standard characteristic impedances?
- A) 50 Ohm and 75 Ohm respectively
- B) 100 Ohm and 120 Ohm respectively
- C) 50 Ohm and 100 Ohm respectively
- D) 75 Ohm and 120 Ohm respectively
- **Answer: ✅ A**
- **Explanation**:
  - 50 Ohm coaxial cable (like RG-58) is used for digital transmission (Ethernet).
  - 75 Ohm coaxial cable (like RG-6) is optimized for analog transmissions and cable television distributions.

#### Q97. Which of the following IP address ranges is designated for multicast transmissions?
- A) `224.0.0.0` to `239.255.255.255`
- B) `240.0.0.0` to `255.255.255.254`
- C) `192.0.0.0` to `223.255.255.255`
- D) `128.0.0.0` to `191.255.255.255`
- **Answer: ✅ A**
- **Explanation**:
  - Class D IP addresses (`224.0.0.0/4`) are reserved for IP multicast.
  - Class E (`240.0.0.0/4`) is reserved for experimental use.
  - Class C (`192.0.0.0` to `223.255.255.255`) is for unicast.

#### Q98. A "Socket" in computer networking is defined as:
- A) The physical port on a switch.
- B) The combination of an IP Address and a Port Number.
- C) The software library that implements encryption.
- D) The system call used to allocate RAM.
- **Answer: ✅ B**
- **Explanation**:
  - A socket represents an endpoint of a two-way communication link between two programs running on the network.
  - It is uniquely identified by combining the IP address (Layer 3) and the port number (Layer 4).

#### Q99. What is the loopback address in the IPv6 protocol?
- A) `127.0.0.1`
- B) `::1`
- C) `fe80::1`
- D) `ff02::1`
- **Answer: ✅ B**
- **Explanation**:
  - In IPv6, the loopback address is represented as `0:0:0:0:0:0:0:1`, which is abbreviated as `::1`.
  - `127.0.0.1` is the IPv4 loopback address.

#### Q100. How does Port Address Translation (PAT / NAT Overload) differ from Static NAT?
- A) Static NAT translates private IPs to IPv6, while PAT translates to IPv4.
- B) Static NAT maps one private IP to one public IP, whereas PAT maps multiple private IPs to a single public IP by modifying source port numbers in packets.
- C) PAT operates at Layer 2.
- D) PAT requires two public IP addresses.
- **Answer: ✅ B**
- **Explanation**:
  - Static NAT is a 1-to-1 mapping.
  - PAT (Port Address Translation) is a many-to-1 mapping, allowing thousands of internal hosts with private IPs to share a single public IP by tracking traffic using unique source port numbers.

#### Q101. In the OSPF Neighbor State Machine, which state indicates that bidirectional communication has been established and the DR/BDR election has occurred?
- A) Init State
- B) 2-Way State
- C) ExStart State
- D) Full State
- **Answer: ✅ B**
- **Explanation**:
  - In OSPF, **2-Way state** confirms that both routers have seen each other's Hello packets (bidirectional communication).
  - This is the point where the Designated Router (DR) and Backup Designated Router (BDR) election takes place.

#### Q102. Which of the following is an IMAP-specific command that is NOT supported in the POP3 protocol?
- A) USER
- B) PASS
- C) LIST
- D) SELECT
- **Answer: ✅ D**
- **Explanation**:
  - IMAP allows users to manage multiple folders (mailboxes) directly on the mail server.
  - The `SELECT` command is used in IMAP to select a specific folder (e.g., Inbox, Sent) for viewing. POP3 has no concept of server-side folders.

#### Q103. A client receives an HTTP response status code of `403 Forbidden`. What does this indicate?
- A) The server encountered an internal database error.
- B) The requested resource has moved permanently to a new URL.
- C) The server understood the request, but refuses to authorize access.
- D) The client's request contains invalid syntax.
- **Answer: ✅ C**
- **Explanation**:
  - `403 Forbidden` indicates the server knows who you are but you don't have the permissions to access the resource.
  - `401 Unauthorized` means authentication is required.
  - `404 Not Found` means the resource does not exist.

#### Q104. How does DNS Cache Poisoning (DNS Spoofing) exploit resolvers to hijack traffic?
- A) By flooding the resolver with ICMP packets to crash it.
- B) By returning forged IP addresses in DNS responses before the authoritative server can reply, caching the fake mapping in the resolver.
- C) By modifying the physical host's MAC address table.
- D) By disabling the resolver's recursive flag.
- **Answer: ✅ B**
- **Explanation**:
  - DNS cache poisoning occurs when an attacker sends fake DNS replies to a resolver.
  - If the resolver accepts the spoofed response, it caches the incorrect IP mapping, directing all future users to the attacker's malicious server.

#### Q105. In physical layer signaling, what is the key characteristic of Manchester encoding?
- A) A binary `0` is represented by no transition, and a binary `1` by a transition at the start of the bit interval.
- B) A transition always occurs at the middle of each bit interval, where the direction of the transition determines the binary value.
- C) It uses three voltage levels (+V, 0, -V) to represent data.
- D) It does not provide self-synchronization.
- **Answer: ✅ B**
- **Explanation**:
  - In Manchester encoding, there is always a mid-bit transition (e.g., high-to-low for `0`, low-to-high for `1`).
  - This guaranteed transition provides self-synchronization (the receiver can extract the clock signal from the data stream).
