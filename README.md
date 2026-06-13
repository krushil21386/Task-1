# Task 1: Basic Network Scanning with Nmap

## Objective

The objective of this task was to perform basic network reconnaissance using Nmap (Network Mapper). The scan was conducted to identify active devices on the network, discover open ports, determine running services, and analyze the security significance of the detected services.

---

# Introduction to Nmap

Nmap (Network Mapper) is a popular open-source network scanning and security auditing tool. It is widely used by network administrators, cybersecurity professionals, and penetration testers to:

* Discover hosts on a network
* Identify open ports
* Detect running services and their versions
* Gather operating system information
* Assess the security posture of systems

Nmap helps administrators understand which services are exposed to the network and identify potential security risks.

---

# Environment

* Operating System: Kali Linux
* Tool Used: Nmap 7.99
* Target: Localhost (127.0.0.1)
* Network Range: 10.92.9.22/24

---

# Step 1: Verify Nmap Installation

## Command

```bash id="6q4tzl"
nmap --version
```

## Purpose

This command verifies that Nmap is properly installed and displays information about the installed version and supported libraries.

## Output Summary

* Nmap Version: 7.99
* Platform: x86_64 Linux
* Nsock Engines Available:

  * epoll
  * poll
  * select

## Analysis

The successful execution of this command confirmed that Nmap was correctly installed and ready for use.

---

# Step 2: Host Discovery Scan

## Command

```bash id="f2hy6s"
nmap -sn 10.92.9.22/24
```

## Purpose

The `-sn` option performs a ping scan to identify active hosts on the network without scanning ports.

## Output Summary

The scan discovered three active hosts:

| IP Address | Status |
| ---------- | ------ |
| 10.92.9.22 | Active |
| 10.92.9.38 | Active |
| 10.92.9.37 | Active |

A total of 256 IP addresses were checked.

## Analysis

Host discovery is usually the first step of network reconnaissance. It helps identify devices currently connected to the network and available for communication. This information can be useful for network inventory management and security assessments.

---

# Step 3: Service Version Detection

## Command

```bash id="4qqzpg"
nmap -sV localhost
```

## Purpose

The `-sV` option attempts to determine the version of services running on open ports.

## Output Summary

| Port | Protocol | State | Service | Version                 |
| ---- | -------- | ----- | ------- | ----------------------- |
| 22   | TCP      | Open  | SSH     | OpenSSH 10.3p1 Debian 2 |
| 80   | TCP      | Open  | HTTP    | Apache httpd 2.4.67     |

## Analysis

The scan revealed two open ports:

### Port 22 - SSH

SSH (Secure Shell) is used for secure remote access to Linux systems. It allows administrators to manage servers remotely using encrypted communication.

### Port 80 - HTTP

HTTP (HyperText Transfer Protocol) is used for serving web pages. The scan detected an Apache web server running on this port.

Version detection is important because outdated software may contain vulnerabilities that attackers can exploit.

---

# Step 4: Aggressive Scan

## Command

```bash id="mynvhf"
nmap -A -T4 localhost
```

## Purpose

The `-A` option enables advanced detection features:

* Operating System Detection
* Version Detection
* Script Scanning
* Traceroute

The `-T4` option increases scan speed.

## Output Summary

The scan identified:

* Linux Operating System
* OpenSSH 10.3p1
* Apache HTTP Server 2.4.67
* Apache Default Web Page

Additional information:

```text id="4w4s4k"
Apache2 Debian Default Page: It works
```

## Analysis

Aggressive scanning provides detailed information about a target system. Such information helps administrators understand exposed services and verify system configurations.

The scan also confirmed that the target machine is running Linux and hosting a web server through Apache.

---

# Step 5: Open Ports Scan

## Command

```bash id="9rhm4k"
nmap -p- --open localhost
```

## Purpose

This command scans all TCP ports and displays only ports that are open.

## Output Summary

| Port   | State | Service |
| ------ | ----- | ------- |
| 22/tcp | Open  | SSH     |
| 80/tcp | Open  | HTTP    |

## Analysis

Only two ports were open on the system. This indicates a relatively small attack surface because only essential services are exposed.

---

# Security Significance of Open Ports

## Port 22 (SSH)

### Function

Provides secure remote administration.

### Advantages

* Encrypted communication
* Secure remote access
* File transfer support

### Security Considerations

* Use strong passwords.
* Prefer SSH key authentication.
* Disable unused accounts.
* Monitor login attempts.

---

## Port 80 (HTTP)

### Function

Serves web pages and web applications.

### Advantages

* Enables website hosting.
* Supports browser-based applications.

### Security Considerations

* Keep Apache updated.
* Validate user inputs.
* Use HTTPS where possible.
* Regularly review server logs.

---

# Findings

1. Nmap was successfully installed and verified.
2. Three active hosts were discovered on the network.
3. Two open ports were identified on the local machine.
4. SSH service was running on Port 22.
5. Apache web server was running on Port 80.
6. The operating system was detected as Linux.
7. No unexpected open ports were discovered.

---

# Conclusion

This task demonstrated the use of Nmap for network reconnaissance and service enumeration. Multiple scans were performed to discover active hosts, identify open ports, detect service versions, and gather operating system information. The results showed that the target machine was running Linux with SSH and Apache web services enabled on Ports 22 and 80 respectively. Understanding open ports and running services is essential for maintaining network security and identifying potential vulnerabilities.

---

## Author

Krushil Patel

B.Tech Information Technology

Charotar University of Science and Technology (CHARUSAT)
