# Networking Fundamentals for DevOps

## 1. Networking Flow (Traffic Path)
A typical request travels through the following path before reaching your application:

1. **Client PC** – User’s browser sends the request
2. **Router** – Routes packets inside the local network
3. **Internet Gateway** – Connects private networks to the public internet
4. **Routing Table** – Decides where traffic should go
5. **Load Balancer** – Distributes traffic across multiple servers
6. **Application Servers (Target Group)** – Where application code runs

----------------------------------------------------------------------------

## 2. Essential DevOps Networking Concepts

### A. IP Addressing & CIDR
- **IP Address:** Unique identifier for a device (e.g., `192.168.1.1`)
- **Private IP:** Used inside private networks
- **Public IP:** Used on the internet
- **CIDR:** Defines IP ranges (e.g., `10.0.0.0/16`)
  - Smaller suffix → more IP addresses

### B. Common Ports & Protocols

| Protocol | Port | Description |
| :--- | :--- | :--- |
| SSH | 22 | Secure remote access |
| HTTP | 80 | Unencrypted web traffic |
| HTTPS | 443 | Encrypted web traffic |
| FTP | 21 | File transfer |
| MySQL | 3306 | Database port |
| Jenkins | 8080 | CI/CD service |

----------------------------------------------------------------------------

## 3. Networking Troubleshooting Commands

| Command | Example | Purpose |
| :--- | :--- | :--- |
| `ping` | `ping google.com` | Connectivity check |
| `telnet` | `telnet 10.0.0.5 80` | Port check |
| `curl` | `curl -Iv https://site.com` | HTTP debugging |
| `netstat` | `netstat -tulpn` | Open ports |
| `ip a` | `ip a` | Network interfaces |
| `dig` | `dig google.com` | DNS lookup |

----------------------------------------------------------------------------

## 4. SSH (Secure Shell)
Primary access method for Linux servers.

```bash
ssh -i key.pem user@public-ip

## 5. Load Balancing Types

- **L4 (Layer 4):**  
  Operates at the transport layer (TCP/UDP). Very fast.

- **L7 (Layer 7):**  
  Operates at the application layer (HTTP/HTTPS). Can route traffic based on URLs.

----------------------------------------------------------------------------

# Advanced Networking & Cloud Infrastructure

## 1. How Networking Works (The Big Picture)

Networking is the process of transporting data packets from source A to destination B.

- **Encapsulation:** Data is wrapped in protocol layers.
- **Addressing:**
  - IP addresses identify devices.
  - MAC addresses identify network interfaces.
- **Routing:** Routers use routing tables to find the best path.

----------------------------------------------------------------------------

## 2. OSI Model (Open Systems Interconnection)

As a DevOps engineer, you mostly deal with **Layers 3, 4, and 7**.

| Layer | Name | Data Unit | Responsibility | DevOps Context |
| :--- | :--- | :--- | :--- | :--- |
| 7 | Application | Data | HTTP/DNS | L7 Load Balancer, WAF |
| 6 | Presentation | Data | Encryption & formatting | SSL/TLS |
| 5 | Session | Data | Session control | Authentication |
| 4 | Transport | Segments | TCP/UDP | Ports |
| 3 | Network | Packets | Routing & IP | VPC, Subnets |
| 2 | Data Link | Frames | MAC addressing | Switches |
| 1 | Physical | Bits | Hardware | Cables/Fiber |

----------------------------------------------------------------------------

## 3. DNS (Domain Name System)

DNS is the phonebook of the internet.

- **A Record:** Maps to IPv4
- **AAAA Record:** Maps to IPv6
- **CNAME:** Alias record
- **MX Record:** Mail routing

----------------------------------------------------------------------------

## 4. VPC (Virtual Private Cloud)

A VPC is your private network in the cloud.

### Components
- **Subnets**
  - Public subnet → Internet access
  - Private subnet → Internal use
- **Internet Gateway**
- **Route Tables**

----------------------------------------------------------------------------

## 5. CIDR & Subnetting

CIDR defines IP ranges.

### Example

- `/32` → 1 IP  
- `/24` → 256 IPs  
- `/16` → 65,536 IPs  

### Private IP Ranges
- `10.0.0.0 – 10.255.255.255`
- `172.16.0.0 – 172.31.255.255`
- `192.168.0.0 – 192.168.255.255`

----------------------------------------------------------------------------

## 6. Subnetting Logic

Subnetting divides a large network into smaller ones.

### Reasons
- Security
- Performance
- Scalability

----------------------------------------------------------------------------

# 🌐 Networking Fundamentals: Journey of a Request

## 1. How Networking Works: The Request Journey

When you type `google.com` in your browser, the following happens:

### Phase A: DNS Resolution
- Local browser cache
- OS cache
- Router cache
- ISP DNS

----------------------------------------------------------------------------

### Phase B: TCP Handshake (3-Way)
- SYN
- SYN-ACK
- ACK

----------------------------------------------------------------------------

### Phase C: Data Initiation (OSI Flow)

| Layer | Name | Process |
| :--- | :--- | :--- |
| L7 | Application | HTTP request |
| L6 | Presentation | Encryption |
| L5 | Session | Session handling |
| L4 | Transport | Segments |
| L3 | Network | Packets |
| L2 | Data Link | Frames |
| L1 | Physical | Signals |
