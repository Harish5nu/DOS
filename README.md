# 🌐 DoS & DDoS - TCP SYN Flood Attack

A TCP SYN Flood is a type of **Denial-of-Service (DoS)** or **Distributed Denial-of-Service (DDoS)** attack where the attacker sends many SYN requests to a target server with the intention of overwhelming the system and exhausting its resources.

---

## 🚨 What is a SYN Flood Attack?

TCP uses a **3-way handshake**:
1. Client sends **SYN**
2. Server replies with **SYN-ACK**
3. Client replies with **ACK**

In a SYN flood:
- The attacker sends multiple **SYN** packets with spoofed or unreachable IP addresses.
- The server waits for the **ACK** that never arrives.
- This leads to a backlog of **half-open connections**, consuming system resources and making the server **unresponsive** to legitimate users.

---

## 💣 DoS vs DDoS

| DoS (Denial of Service)         | DDoS (Distributed Denial of Service)     |
|---------------------------------|-------------------------------------------|
| Single attacker                 | Multiple devices (botnet) attack at once |
| Easier to detect & block        | Harder to block due to scale             |
| Less bandwidth consumption      | High volume, often in the gigabits/sec   |

---

## 🛠️ Example Commands

### 🔹 Using `hping3` (Linux/Kali)

#### ⚠️ Legal Warning
> Only use on authorized systems. Unauthorized use is illegal and unethical.

### 🧪 Basic TCP SYN Flood (DoS)
```bash
hping3 -S -p 80 -c 10000 <target-ip>
```

### 🎯SYN Flood with Spoofed Source

```bash
hping3 -S -p 80 -a 1.2.3.4 -c 10000 <target-ip>
```

### 🌐DDoS-Like SYN Flood (Randomized IPs)
```bash
hping3 -S --flood --rand-source -p 80 <target-ip>
```
