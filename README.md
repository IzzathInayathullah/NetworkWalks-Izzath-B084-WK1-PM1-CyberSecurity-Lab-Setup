# NetworkWalks-Izzath-B084-WK1-PM1-CyberSecurity-Lab-Setup

## 1. Project Overview

This project documents the setup and basic network verification of a beginner cybersecurity home lab using Kali Linux running inside Oracle VirtualBox on a Windows 11 host.

The purpose of this lab is to become familiar with a virtualized Linux environment, basic networking commands, connectivity testing, and technical documentation for a cybersecurity portfolio.

## 2. Project Objectives

- Set up and document a Kali Linux virtual machine.
- Identify the operating system and basic system resources.
- Inspect network interfaces, IP addresses, routing, and DNS configuration.
- Perform basic connectivity tests.
- Capture screenshots showing the actual lab configuration and test results.
- Document troubleshooting observations and solutions.
- Publish the project documentation on GitHub.

## 3. Lab Environment

| Component | Description |
|---|---|
| Host operating system | Microsoft Windows 11 |
| Virtualization software | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Project type | Beginner cybersecurity home lab |
| Documentation platform | GitHub |

The exact versions, allocated memory, and network settings will be recorded after verifying the actual configuration.

## 4. System Information

The following commands were used to inspect the Kali Linux environment.

### Identify the operating system

```bash
cat /etc/os-release
```

### Check the Linux kernel

```bash
uname -r
```

### Check the current user

```bash
whoami
```

### Check available memory

```bash
free -h
```

### Check disk usage

```bash
df -h
```

These commands help identify the operating system, kernel version, logged-in user, available memory, and disk space.

## 5. Network Configuration

### Display network interfaces and IP addresses

```bash
ip -br address
```

This command provides a concise overview of network interfaces and their assigned IP addresses.

### Display the routing table

```bash
ip route
```

The routing table helps identify the default gateway and routes available to the virtual machine.

### Inspect DNS configuration

```bash
cat /etc/resolv.conf
```

This displays the configured DNS resolver information.

## 6. Connectivity Testing

### Test DNS resolution

```bash
getent hosts example.com
```

If DNS resolution is working, the command should return one or more IP addresses for the domain.

### Test HTTPS connectivity

```bash
curl -I --max-time 10 https://example.com
```

A successful response may include an HTTP status line such as `HTTP/2 200` or another valid HTTP response. Results can vary depending on connectivity and the remote server.

### Test the default gateway

First, identify the gateway using:

```bash
ip route
```

If a default gateway is listed, replace `GATEWAY_IP_ADDRESS` with its actual IP address:

```bash
ping -c 4 GATEWAY_IP_ADDRESS
```

A failed ping does not necessarily mean the network is broken, because some systems block ICMP traffic.

**Note:** Record the actual results of each test. Do not mark a test as successful unless it has been performed and verified.

## 7. Virtual Machine Network Safety

Virtual machine network settings should match the purpose of the lab.

- **NAT:** Useful when Kali needs outbound internet access through the host.
- **Host-only networking:** Useful for communication between the host and virtual machines on a dedicated virtual network.
- **Internal networking:** Useful for communication between virtual machines on the same isolated internal network.

NAT by itself should not be treated as a guarantee of complete isolation. For security testing, use an isolated lab network and test only systems you own or have explicit permission to assess.

Take a VirtualBox snapshot before making significant configuration changes so that you can restore a known working state if needed.

## 8. Screenshots and Evidence

Screenshots will be added to the `screenshots/` directory as the lab activities are completed.

Planned screenshots:

| Filename | Evidence |
|---|---|
| `01-virtualbox-kali-vm.png` | Kali virtual machine in VirtualBox |
| `02-kali-desktop.png` | Kali Linux desktop |
| `03-system-information.png` | Operating system and system information |
| `04-network-configuration.png` | Network interfaces and IP addresses |
| `05-routing-information.png` | Routing table |
| `06-connectivity-test.png` | Actual DNS or connectivity test results |
| `07-virtualbox-network-settings.png` | VirtualBox network configuration |

Only genuine screenshots from the actual lab will be included. Filenames may be adjusted to match the screenshots captured.

## 9. Troubleshooting

### No IP address is displayed

Check the interface status using:

```bash
ip -br address
```

Confirm that the virtual network adapter is enabled in VirtualBox and that the selected network mode is appropriate.

### No default route is displayed

Run:

```bash
ip route
```

Review the virtual machine's network adapter configuration and check whether the network has provided a route.

### DNS resolution fails

Run:

```bash
getent hosts example.com
```

Then inspect the DNS configuration:

```bash
cat /etc/resolv.conf
```

Confirm that the virtual machine has working network connectivity before investigating DNS further.

### Internet connectivity fails

Check the IP address and routing table, then test DNS resolution and HTTPS connectivity separately. This helps distinguish between IP configuration, routing, DNS, and remote-server issues.

## 10. Learning Outcomes

This project provides practical experience with:

- Kali Linux system inspection.
- Linux command-line fundamentals.
- IP addressing and network interfaces.
- Routing and default gateways.
- DNS resolution and basic connectivity testing.
- Virtual machine network configuration.
- Cybersecurity lab documentation and evidence collection.
- Git and GitHub portfolio management.

## 11. Project Limitations

This is a beginner lab focused on system identification and basic network verification. It does not represent a complete penetration test, security audit, or production security assessment.

Results depend on the actual virtual machine configuration, network settings, and connectivity available during testing.

## 12. Author

**Name:** Izzath Inayathullah

**Project:** Lab Setup (for Cyber Security & Ethical Hacking practice)


**Repository:** NetworkWalks-Izzath-B084-WK1-PM1-CyberSecurity-Lab-Setup
