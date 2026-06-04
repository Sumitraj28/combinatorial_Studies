# Unit II: Computer Networks - MCQ Bank

Master Unit 2 with these 50 solved, high-probability Multiple Choice Questions covering physical structures, reference models, subnetting, routing, and key protocols.

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
