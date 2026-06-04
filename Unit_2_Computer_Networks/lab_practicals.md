# Unit II: Computer Networks - Lab Practicals

This guide contains the step-by-step workbook and practical worksheets for **Practical 7: Subnetting**. It covers binary division math, subnet mask calculations, host range allocations, and detailed examples.

---

## 💻 Practical 7: Subnetting Workbook

### 1. Conceptual Quick-Start
Subnetting is the process of taking a single physical network range and dividing it into smaller, manageable sub-networks (subnets). 
In an IP address, we divide the 32 bits into two parts: the **Network Portion** (represented by 1s in the subnet mask) and the **Host Portion** (represented by 0s in the subnet mask).

```
IP Address:  192.168.1.130 (11000000.10101000.00000001.10000010)
Mask (/26):  255.255.255.192 (11111111.11111111.11111111.11000000)
                              |<- Network Portion ->| |<- Host ->|
```

*   **Subnet Bits ($s$)**: The number of bits borrowed from the default host portion.
*   **Host Bits ($h$)**: The remaining host bits.
*   **Subnet Block Size**: The interval spacing between subnets, calculated as:
    $$\text{Block Size} = 256 - \text{Decimal value of subnet octet} = 2^h$$

---

## 📝 Worksheet 1: Class C Subnetting

### Task: Subnet the network address `192.168.1.0` using a `/26` prefix.

#### Step 1: Analyze the Prefix
*   Default Class C prefix is `/24`.
*   Custom prefix is `/26`.
*   Number of borrowed bits ($s$) = $26 - 24 = 2$ bits.
*   Remaining host bits ($h$) = $32 - 26 = 6$ bits.

#### Step 2: Calculate Subnet Count & Host Count
*   **Number of Subnets** = $2^s = 2^2 = 4$ subnets.
*   **Total Hosts per Subnet** = $2^h = 2^6 = 64$ hosts.
*   **Usable Hosts per Subnet** = $2^h - 2 = 64 - 2 = 62$ hosts.

#### Step 3: Calculate Subnet Mask & Block Size
*   Subnet Mask in binary: `11111111.11111111.11111111.11000000`
    *   Octet 4 decimal value = $128 + 64 = 192$.
    *   Subnet Mask = `255.255.255.192`.
*   Block Size = $256 - 192 = 64$ addresses.

#### Step 4: Map Subnet Boundaries
Each subnet starts at increments of the Block Size ($64$):

| Subnet # | Subnet ID (Network ID) | First Usable Host IP | Last Usable Host IP | Broadcast IP |
| :--- | :--- | :--- | :--- | :--- |
| **0** | `192.168.1.0` | `192.168.1.1` | `192.168.1.62` | `192.168.1.63` |
| **1** | `192.168.1.64` | `192.168.1.65` | `192.168.1.126` | `192.168.1.127` |
| **2** | `192.168.1.128` | `192.168.1.129` | `192.168.1.190` | `192.168.1.191` |
| **3** | `192.168.1.192` | `192.168.1.193` | `192.168.1.254` | `192.168.1.255` |

---

## 📝 Worksheet 2: Class B Subnetting

### Task: Subnet the network address `172.16.0.0` using a `/22` prefix.

#### Step 1: Analyze the Prefix
*   Default Class B prefix is `/16`.
*   Custom prefix is `/22`.
*   Number of borrowed bits ($s$) = $22 - 16 = 6$ bits.
*   Remaining host bits ($h$) = $32 - 22 = 10$ bits.

#### Step 2: Calculate Subnet Count & Host Count
*   **Number of Subnets** = $2^s = 2^6 = 64$ subnets.
*   **Total Hosts per Subnet** = $2^h = 2^{10} = 1024$ hosts.
*   **Usable Hosts per Subnet** = $2^{10} - 2 = 1022$ hosts.

#### Step 3: Calculate Subnet Mask & Block Size
*   Subnet Mask in binary: `11111111.11111111.11111100.00000000`
    *   Octet 3 decimal value = $128 + 64 + 32 + 16 + 8 + 4 = 252$.
    *   Subnet Mask = `255.255.252.0`.
*   Block Size in the 3rd octet = $256 - 252 = 4$ blocks. (Interval is $4.0$).

#### Step 4: Map Subnet Boundaries
Each subnet starts at increments of $4.0$ in the 3rd octet:

| Subnet # | Subnet ID (Network ID) | First Usable Host IP | Last Usable Host IP | Broadcast IP |
| :--- | :--- | :--- | :--- | :--- |
| **0** | `172.16.0.0` | `172.16.0.1` | `172.16.3.254` | `172.16.3.255` |
| **1** | `172.16.4.0` | `172.16.4.1` | `172.16.7.254` | `172.16.7.255` |
| **2** | `172.16.8.0` | `172.16.8.1` | `172.16.11.254` | `172.16.11.255` |
| $\dots$ | $\dots$ | $\dots$ | $\dots$ | $\dots$ |
| **63** | `172.16.252.0` | `172.16.252.1` | `172.16.255.254` | `172.16.255.255` |

---

## ✍️ Self-Practice Exercises

Solve these problems to test your understanding:

1.  **Exercise 1**: You are given the IP address `192.168.10.115/28`. Find:
    *   Subnet Mask
    *   Network ID
    *   Broadcast ID
    *   Range of usable host IPs
    *   *Solution*: 
        *   Prefix `/28` means the mask is `255.255.255.240` (block size of 16).
        *   Multiples of 16 closest to 115 are $16 \times 7 = 112$ and $16 \times 8 = 128$.
        *   Network ID = `192.168.10.112`.
        *   Broadcast ID = `192.168.10.127`.
        *   Usable hosts range = `192.168.10.113` to `192.168.10.126`.

2.  **Exercise 2**: An organization requires 30 usable host IP addresses per subnet. What CIDR prefix and subnet mask should be chosen for their Class C network?
    *   *Solution*: 
        *   To support 30 usable hosts, we need $2^h - 2 \ge 30 \implies 2^h \ge 32 \implies h = 5$ bits.
        *   Network bits = $32 - 5 = 27$ bits.
        *   CIDR Prefix = `/27`.
        *   Subnet Mask = `255.255.255.224`.
