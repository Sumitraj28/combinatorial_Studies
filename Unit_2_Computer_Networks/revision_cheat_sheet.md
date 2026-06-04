# Unit II: Networks Revision Cheat Sheet

Your quick-reference pocket guide for computer networks revision.

---

## ⚡ 1. Networking Formulas Card

### Network Performance Delays
*   **Propagation Delay ($T_p$)**: Time for one bit to travel along the link.
    $$T_p = \frac{\text{Distance}}{\text{Propagation Speed}}$$
*   **Transmission Delay ($T_t$)**: Time to push all packet bits onto the link.
    $$T_t = \frac{\text{Packet Size (L)}}{\text{Bandwidth (B)}}$$
*   **Total Delay** = $T_{\text{transmission}} + T_{\text{propagation}} + T_{\text{queuing}} + T_{\text{processing}}$.

### Flow Control Efficiency
*   **Stop-and-Wait Efficiency ($\eta$)**:
    $$\eta = \frac{T_t}{T_t + 2 \times T_p} = \frac{1}{1 + 2a} \quad \text{where } a = \frac{T_p}{T_t}$$
*   **Sliding Window Efficiency ($\eta$)**: Let $W$ be the window size.
    $$\eta = \frac{W \times T_t}{T_t + 2 \times T_p} = \frac{W}{1 + 2a} \quad (\text{Maximum efficiency } = 100\%)$$

### Subnetting Formulas
*   **Number of Subnets** = $2^s$ (where $s$ is the number of borrowed network bits).
*   **Number of Total Hosts per Subnet** = $2^h$ (where $h$ is the number of remaining host bits).
*   **Number of Usable Hosts per Subnet** = $2^h - 2$ (subtracting Network ID and Broadcast ID).

---

## 📊 2. High-Yield Summary Tables

### Well-Known Port Numbers
| Protocol | Port Number | Transport Protocol | Use Case |
| :--- | :--- | :--- | :--- |
| **FTP Control**| `21` | TCP | Command channel for files |
| **FTP Data** | `20` | TCP | Data channel for file transfer |
| **SSH** | `22` | TCP | Secure remote terminal shell |
| **SMTP** | `25` | TCP | Email sending |
| **DNS** | `53` | UDP (Queries) / TCP (Zone)| Domain name mapping |
| **DHCP** | `67` (Server) / `68` (Client) | UDP | Automatic IP configuration |
| **HTTP** | `80` | TCP | Web pages |
| **POP3** | `110` | TCP | Email retrieval (downloads) |
| **IMAP** | `143` | TCP | Email syncing (keeps on server) |
| **HTTPS** | `443` | TCP | Secure web browsing |

### Routing Algorithms
| Feature | Distance Vector (e.g., RIP) | Link State (e.g., OSPF) |
| :--- | :--- | :--- |
| **Metric** | Hop Count (max 15 hops) | Cost based on bandwidth |
| **Table Exchange**| Sends **entire routing table** to **immediate neighbors** | Sends **local link status** to **all routers (flooding)** |
| **Convergence** | Slow. Suffers from Count-to-Infinity. | Very fast. Dijkstra runs locally. |
| **CPU/RAM Usage**| Low. Simple vector addition. | High. Must store complete topology graph. |

---

## 🧠 3. Memory Tricks & Mnemonics

*   **OSI Layers (Top to Bottom)**: **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing
    *   **A**pplication, **P**resentation, **S**ession, **T**ransport, **N**etwork, **D**ata Link, **P**hysical.
*   **OSI Layers (Bottom to Top)**: **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way
    *   **P**hysical, **D**ata Link, **N**etwork, **T**ransport, **S**ession, **P**resentation, **A**pplication.
*   **Protocol Data Units (PDUs)**: **D**on't **S**pill **P**izza **F**or **B**oys
    *   **D**ata (App/Pres/Sess), **S**egments (Transport), **P**ackets (Network), **F**rames (Data Link), **B**its (Physical).
*   **DHCP Process**: **D-O-R-A**
    *   **D**iscover, **O**ffer, **R**equest, **A**cknowledge.

---

## 🚨 4. High-Risk Confusion Zones

### 1. TCP vs. UDP Headers
*   **TCP Header**: Minimum **20 bytes** long. Includes sequence number, acknowledgment number, window size, flags (SYN, ACK, FIN, RST).
*   **UDP Header**: Fixed **8 bytes** long. Includes only Source Port, Destination Port, Length, and Checksum.

### 2. IP Address vs. MAC Address
*   **MAC (Physical) Address**: 48-bit (6 bytes) hexadecimal address burned into the Network Interface Card (NIC) at the factory. Used for node-to-node hops within the local network.
*   **IP (Logical) Address**: 32-bit (IPv4) or 128-bit (IPv6) address assigned dynamically by the software configuration. Used for end-to-end routing across separate networks.

### 3. SMTP vs. POP3 vs. IMAP
*   **SMTP**: Outgoing mail agent (**Push** protocol). Sends mail.
*   **POP3/IMAP**: Incoming mail agents (**Pull** protocols). Read mail.

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **Host Calculations**: When asked for **usable** hosts, always subtract 2: $2^h - 2$. The first IP address is the **Network ID** (all host bits 0) and the last is the **Broadcast ID** (all host bits 1).
*   **DHCP Transport**: DHCP runs over **UDP**, not TCP, because a joining host does not have an IP address yet and must broadcast its discovery messages.
*   **Ping Layer**: `ping` uses the **ICMP** protocol. ICMP is a Network Layer protocol, meaning ping operates at Layer 3, not the Application Layer!
*   **CSMA/CD vs CSMA/CA**: CSMA/CD is for wired networks (Ethernet). Wired cables can sense collisions directly. CSMA/CA is for wireless networks (802.11 WiFi) because wireless radios cannot transmit and receive on the same frequency at the same time to detect collisions.
