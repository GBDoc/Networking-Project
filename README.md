
# 🌐 Network Design and Implementation – Netcore Systems Limited

![Networking](https://img.shields.io/badge/Domain-Computer%20Networking-blue)
![Cisco](https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer-049FD9)
![Project](https://img.shields.io/badge/Project-Network%20Engineering-success)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Project Overview

This project demonstrates the design, configuration, implementation, and testing of a departmental computer network for a fictional organisation, **Netcore Systems Limited**.

Developed as part of the 10alytics Networking Capstone Project (2026), the project involved designing a network infrastructure that connects three organisational departments: IT, Sales, and Human Resources (HR).

Using Cisco Packet Tracer, I designed a network topology, configured IP addressing, established communication between departments, implemented Access Control Lists (ACLs), and tested access to an internal HTTP server.

The project demonstrates practical understanding of fundamental networking concepts, network segmentation, routing, connectivity troubleshooting, and network access control.

---

## 🎯 Problem Statement

Netcore Systems Limited required a structured computer network to support communication and resource sharing across its IT, Sales, and HR departments.

The network needed to:

- Connect employees across the three departments.
- Provide appropriate IP addressing and default gateways.
- Enable interdepartmental network communication.
- Restrict unauthorised communication between selected departmental networks.
- Provide access to an internal HTTP server.
- Demonstrate successful network connectivity and access control through testing.

The objective was to design and implement a functional network infrastructure that meets these organisational requirements.

---

## 🏗️ Network Architecture

The network consists of three departmental LANs connected through a central router.

Each department has its own network segment and connected end-user devices.

### Departmental Network Structure

| Department | Network Address | Employees | Network Devices |
|---|---|---|---|
| IT | 192.168.10.0/24 | Stanley and David | Switch, PCs, Server |
| Sales | 192.168.20.0/24 | Grace and Beverly | Switch, PCs |
| HR | 192.168.30.0/24 | Nick and Jenny | Switch, PCs |

**Network topology components:**

- One central router.
- Departmental switches.
- Six employee workstations.
- One internal server.
- Three departmental IP networks.

### Network Topology

The implemented topology uses a centralised routing architecture, connecting the departmental networks through a central router.

The IT network also hosts an internal server providing HTTP services.

![Network Topology](screenshots/network-topology.png)

*Note: Replace the image path with the actual location of your network topology screenshot in the repository.*

---

## ⚙️ Technologies and Tools

The following technology and networking concepts were used in this project:

| Technology / Tool | Purpose |
|---|---|
| Cisco Packet Tracer | Network design, simulation, configuration and testing |
| Cisco IOS CLI | Router configuration and ACL implementation |
| IPv4 Addressing | Assigning IP addresses to network devices |
| Subnetting | Creating departmental network segments |
| Ethernet Switching | Connecting departmental endpoints |
| Routing | Enabling communication between network segments |
| Access Control Lists (ACLs) | Controlling traffic between departmental networks |
| ICMP (Ping) | Testing network connectivity |
| HTTP | Providing access to the internal web server |

---

## ✨ Key Features and Implementation

### 1. Network Topology Design

Designed a departmental network infrastructure connecting IT, Sales, and HR through a central router.

Each department has a dedicated LAN with connected employee workstations.

### 2. IP Address Configuration

Implemented IPv4 addressing using three departmental subnets:

- IT: `192.168.10.0/24`
- Sales: `192.168.20.0/24`
- HR: `192.168.30.0/24`

The documented configuration for Stanley's workstation includes:

| Configuration | Value |
|---|---|
| IPv4 Address | 192.168.10.5 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.10.1 |

The server is accessible through the internal address `192.168.10.2`.

### 3. Interdepartmental Connectivity Testing

Used ICMP ping commands to verify communication between departmental workstations.

**Successful connectivity test:**

A ping test from Nick's workstation in HR to Stanley's workstation in IT demonstrated successful connectivity.

Target IP: `192.168.10.5`

The recorded test received three replies out of four packets.

**Restricted connectivity test:**

A ping test from Beverly's workstation in Sales to Stanley's workstation in IT failed.

The test returned destination host unreachable messages, demonstrating the configured traffic restriction.

### 4. Access Control List (ACL) Implementation

Configured an extended ACL on the central router to restrict traffic originating from the Sales network to the IT network.

The ACL was named:

`Sales-ACL`

The documented ACL entries were:

```cisco
ip access-list extended Sales-ACL
 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
 permit ip any any
```

The ACL was applied inbound on interface `GigabitEthernet0/1`:

```cisco
interface gig0/1
 ip access-group Sales-ACL in
```

This configuration denies IP traffic from the Sales subnet (`192.168.20.0/24`) to the IT subnet (`192.168.10.0/24`), while permitting other IP traffic that reaches the ACL.

### 5. Internal HTTP Server Access

Configured and tested access to the internal HTTP server hosted within the IT network.

Beverly's workstation in Sales successfully accessed the server through its web browser using:

`http://192.168.10.2`

This demonstrated that the Sales workstation could access the HTTP service despite the restriction on direct IP traffic from Sales to IT.

---

## 🧪 Testing and Validation

The following tests were performed to validate the implemented network.

| Test | Source | Destination | Result |
|---|---|---|---|
| ICMP connectivity | Nick (HR) | Stanley (IT) | Successful: 3 replies out of 4 |
| ICMP connectivity | Beverly (Sales) | Stanley (IT) | Failed: 100% packet loss |
| HTTP access | Beverly (Sales) | Internal HTTP Server | Successful |
| ACL verification | Central Router | Sales-ACL | Configuration verified through CLI |

These tests demonstrate the implementation of network connectivity and departmental traffic restrictions.

---

## 📸 Project Screenshots and Evidence

The following screenshots document the network implementation and testing process.

### 1. Completed Network Topology

![Network Topology](screenshots/network-topology.png)

### 2. IP Address Configuration – Stanley's Workstation

![IP Configuration](screenshots/ip-configuration.png)

### 3. Successful Ping Test – HR to IT

![Successful Ping](screenshots/successful-ping.png)

### 4. Failed Ping Test – Sales to IT

![Failed Ping](screenshots/failed-ping.png)

### 5. Access Control List Configuration

![ACL Configuration](screenshots/acl-configuration.png)

### 6. Successful HTTP Server Access

![HTTP Server Access](screenshots/http-server.png)

*Replace the screenshot paths above with the actual image filenames and repository locations.*

---

## 🚀 Installation and Setup

### Prerequisites

To explore or reproduce this project, you will need:

- A computer running Windows, macOS, or Linux.
- Cisco Packet Tracer installed.
- The project `.pkt` file (if available).

### Step 1: Install Cisco Packet Tracer

Download and install Cisco Packet Tracer from Cisco Networking Academy:

https://www.netacad.com/cisco-packet-tracer

### Step 2: Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/YOUR_USERNAME/netcore-systems-network-capstone.git
```

### Step 3: Navigate to the Project Directory

```bash
cd netcore-systems-network-capstone
```

### Step 4: Open the Network Simulation

Locate the Cisco Packet Tracer project file:

```text
Netcore-Systems-Network-Topology.pkt
```

Open the file using Cisco Packet Tracer.

**Note:** The `.pkt` filename is a suggested filename. Replace it with the actual project filename if different.

---

## 💻 Usage and Testing Instructions

Once the project is open in Cisco Packet Tracer:

### 1. Inspect the Network Topology

Review the central router, departmental switches, workstations, and internal server.

### 2. Verify IP Configuration

Select an endpoint and navigate to:

`Desktop → IP Configuration`

Review its IPv4 address, subnet mask, and default gateway.

### 3. Test Network Connectivity

Open:

`Desktop → Command Prompt`

Run the following command to test connectivity to Stanley's workstation:

```bash
ping 192.168.10.5
```

### 4. Inspect the ACL Configuration

Access the central router CLI and execute:

```cisco
show access-lists
```

To inspect the ACL application on the interface:

```cisco
show ip interface gigabitEthernet 0/1
```

### 5. Test HTTP Server Access

From Beverly's workstation:

1. Open Desktop.
2. Select Web Browser.
3. Enter `http://192.168.10.2`.
4. Verify that the Netcore Systems Limited webpage loads.

---

## 📚 Skills Demonstrated

This project provided practical experience in:

- Network topology design and implementation.
- IPv4 addressing and subnetting.
- LAN configuration and network segmentation.
- Router and switch configuration.
- Cisco IOS command-line interface (CLI).
- Extended Access Control Lists (ACLs).
- Network access control.
- ICMP connectivity testing.
- HTTP server access and validation.
- Network troubleshooting and verification.
- Understanding network traffic filtering.

---

## 🔮 Potential Future Improvements

The following are proposed enhancements and are not features currently demonstrated in the project:

- Implement VLANs to improve departmental network segmentation.
- Introduce DHCP for automated IP address allocation.
- Configure secure remote network administration using SSH.
- Implement additional firewall and security controls.
- Introduce network monitoring and logging.
- Document and test a more comprehensive network security policy.
- Expand the topology to accommodate additional departments and employees.

---

## 🤝 Contributions

Contributions, suggestions, and constructive feedback are welcome.

If you would like to contribute:

1. Fork this repository.
2. Create a feature branch:

```bash
git checkout -b feature/your-feature-name
```

3. Commit your changes:

```bash
git commit -m "Add: description of changes"
```

4. Push your branch:

```bash
git push origin feature/your-feature-name
```

5. Open a Pull Request describing your changes.

---

## 👩‍💻 Author

**Dorcas Gbenro**

Networking | IT Infrastructure | Cybersecurity | GRC

Interested in network engineering, infrastructure security, and building practical IT solutions.

- GitHub: github.com
- LinkedIn: www.linkedin.com/in/dorcasgbenro

---

## 📄 Project Information

| Detail | Information |
|---|---|
| Project Name | Network Capstone Project |
| Organisation | Netcore Systems Limited |
| Programme | 10alytics |
| Project Year | 2026 |
| Project Domain | Computer Networking |
| Simulation Tool | Cisco Packet Tracer |
| Author | Dorcas Gbenro |

---

## ⭐ Acknowledgements

Special thanks to 10alytics for providing the opportunity to undertake this networking capstone project and develop practical skills in network design, configuration, implementation, and troubleshooting.

---

**If you find this project useful, consider giving the repository a ⭐.**
