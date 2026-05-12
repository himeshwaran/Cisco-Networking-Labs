# 🚀 Cisco Packet Tracer – Implement Basic Connectivity

This lab demonstrates how to configure basic connectivity between switches and PCs in a small LAN using Cisco Packet Tracer.

---

## 🗂 Addressing Table

| Device | Interface | IP Address     | Subnet Mask     |
|--------|-----------|----------------|-----------------|
| S1     | VLAN 1    | 192.168.1.253  | 255.255.255.0   |
| S2     | VLAN 1    | 192.168.1.254  | 255.255.255.0   |
| PC1    | NIC       | 192.168.1.1    | 255.255.255.0   |
| PC2    | NIC       | 192.168.1.2    | 255.255.255.0   |

---

## 🎯 Objectives
1. Configure switches (S1, S2) with hostnames, passwords, and banners.  
2. Assign IP addresses to PCs.  
3. Configure switch management interfaces (VLAN 1).  
4. Verify connectivity using `ping` and `show` commands.  

---

## ⚙️ Step‑by‑Step Procedure

### Part 1: Switch Configuration
```bash
# Set hostname
Switch> enable
Switch# configure terminal
Switch(config)# hostname S1

# Console password
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login

# Privileged EXEC password
S1(config)# enable secret class

# MOTD banner
S1(config)# banner motd # Authorized access only. Violators will be prosecuted. #

# Save configuration
S1# copy running-config startup-config
```

### Part 2: PC Configuration
``` bash
PC1 → IP: 192.168.1.1, Mask: 255.255.255.0

PC2 → IP: 192.168.1.2, Mask: 255.255.255.0

```

### 3: Switch Management Interface
```bash
# Configure VLAN 1 on S1
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.253 255.255.255.0
S1(config-if)# no shutdown

# Configure VLAN 1 on S2
S2(config)# interface vlan 1
S2(config-if)# ip address 192.168.1.254 255.255.255.0
S2(config-if)# no shutdown
copy running-config startup-config

```
### Part 4: Connectivity Verification
```bash
PC1> ping 192.168.1.2
PC1> ping 192.168.1.253
PC1> ping 192.168.1.254
```

![image alt](https://github.com/himeshwaran/Cisco-Networking-Labs/blob/main/basic%20connection%20and%20switch%20interface%20management/images/config%20switch.png)

![image alt](https://github.com/himeshwaran/Cisco-Networking-Labs/blob/main/basic%20connection%20and%20switch%20interface%20management/images/finalconfig.png)


