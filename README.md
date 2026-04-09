# network-port-scan
Nmap network scan project
# Network Port Scan using Nmap and Wireshark

## Objective

To scan the local network and identify open ports in order to understand network exposure and potential security risks.

## Tools Used

* Nmap
* Wireshark
* Kali Linux

## Steps Performed

### 1. Identifying IP Range

The local IP address was obtained using:
ip a

IP Address: 192.168.124.130/24
Network Range: 192.168.124.0/24

---

### 2. Performing TCP SYN Scan

The following command was used:
sudo nmap -sS 192.168.124.0/24 -oN scan.txt

This scan identified active devices and open ports.

---

### 3. Performing Detailed Scan

The following command was used:
sudo nmap -A 192.168.124.0/24 -oN detailed_scan.txt

This provided:

* Service versions
* OS detection
* Additional details

---

### 4. Wireshark Packet Capture

Wireshark was used to capture network packets during scanning.

Steps:

1. Open Wireshark
2. Select interface (eth0)
3. Start capture
4. Run Nmap scan
5. Stop capture
6. Save file as capture.pcapng

---

## Results

### Active Devices Found

* 192.168.124.1
* 192.168.124.2
* 192.168.124.254
* 192.168.124.130 (Host System)

---

### Device Analysis

#### 192.168.124.1

Open Ports:

* 3306 (MySQL)
* 5000 (RTSP / AirPlay)
* 7000 (RTSP / AirPlay)

Details:

* MySQL service is accessible but requires authentication
* Ports 5000 and 7000 are associated with Apple AirPlay services

---

#### 192.168.124.2

* All ports closed

---

#### 192.168.124.254

* All ports filtered (likely firewall protected)

---

#### 192.168.124.130 (Host System)

* All ports closed

---

## Wireshark Analysis

* TCP SYN packets were observed during the Nmap scan
* Target devices responded with SYN-ACK packets for open ports
* Closed ports responded with RST packets
* Packet capture confirmed communication between scanner and target hosts

---

## Security Risks

* Open MySQL port (3306) may allow unauthorized access if weak credentials are used
* RTSP/AirPlay services (ports 5000, 7000) may expose media streaming services
* Open ports increase the attack surface of a network

---

## Conclusion

The network scan successfully identified active devices and open ports. One device had multiple open ports, indicating potential security risks, while other devices were secured with closed or filtered ports. Wireshark analysis helped visualize the network communication during scanning.

---
