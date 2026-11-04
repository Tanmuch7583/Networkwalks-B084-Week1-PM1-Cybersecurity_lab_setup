# Networkwalks-B084-Week1-PM1-Cybersecurity_lab_setup
<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.3-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Tanaka%20Mushedhe%20-C00000?style=flat-square" />
</p>

---



## 📌 Project Overview

As part of the Cybersecurity at Networkwalks programme, I undertook this project to set up my first virtual cybersecurity laboratory using Oracle VirtualBox and Kali Linux.

The objective was to establish a controlled virtual environment for learning Linux, understanding virtual networking, and preparing for future cybersecurity and penetration-testing exercises.

The laboratory uses a dedicated NAT Network to provide network connectivity and support communication between additional virtual machines that may be introduced in future exercises.

This project also provided an opportunity to develop practical troubleshooting skills while documenting the challenges encountered during setup.


## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

---

## 🏗️ Lab Architecture

<img width="1346" height="616" alt="1-screenshot-title-image" src="https://github.com/user-attachments/assets/b5eb3c29-4eab-44b5-9701-0dd39f531cdb" />


Additional target machines can be added to the same virtual network in future projects.

---

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 11         |
| 🧠 Host RAM        | 16 GB               |
| ⚡ Processor       | Intel Core i7      |
| 🧰 Hypervisor      | VirtualBox 7.2  |
| 🐉 Security OS     | Kali Linux 2026.3  |
| 🧠 Kali RAM        | 3072 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 10.0.0.1           |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

---

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled

<img width="1917" height="1077" alt="image" src="https://github.com/user-attachments/assets/e8e9812b-8eee-49a4-8c54-bf694f2688c9" />


A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.


---

## Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM was allocated:

```text
RAM: 3072 MB
```
<img width="1920" height="980" alt="image" src="https://github.com/user-attachments/assets/a77b63cc-7da2-403c-b901-fb40c3fec232" />

---


A shared folder was also configured for transferring required files between the host operating system and the Kali VM.



---

## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 10.0.0.1
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

<img width="1920" height="980" alt="image" src="https://github.com/user-attachments/assets/5e562e4e-2c7e-4e5d-9196-4f28870f77e0" />


---

## Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Snapshot name:

```text
My Fresh Kali Linux Kali - Network Setup
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

<img width="1917" height="607" alt="image" src="https://github.com/user-attachments/assets/6fbc4d76-8228-42a3-90db-591b6151323a" />



---

# 🔎 Lab Verification

| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | Correct Kali IP displayed       |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution        | `nslookup networkwalks.com`     | Domain resolves                 |
| 🧰 Verify Nmap                | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot            | Restore snapshot and run `ip a` | Baseline configuration restored |




### Example Results

```text
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
10.0.0.1
```

---


## Problem 1: Kali Linux ISO Flagged by Windows Security

During the download of the Kali Linux ISO image from the official Kali Linux website, Windows Security flagged the downloaded file as a potential virus and displayed a "Virus detected" warning.

This interrupted the download process and initially prevented me from proceeding with the installation.

**Troubleshooting approach:**

1. Verified that the ISO file was downloaded from the official Kali Linux website.
2. Opened Windows Security and navigated to the Protection History section to review the detected threat.
3. Identified the detection associated with the Kali Linux ISO file.
4. After verifying the download source, selected the option to allow the flagged file through Windows Security.
5. Confirmed that the ISO file was accessible and proceeded with the Kali Linux installation.

**Outcome:** I was able to access the downloaded Kali Linux ISO image and proceed with setting up the virtual machine.

> **Important:** Allowing a flagged file should only be considered after independently verifying its authenticity and integrity. Antivirus detections should not be dismissed without investigation.

## Problem 2: Internet Connectivity Failure Inside the Kali Virtual Machine

After successfully setting up Kali Linux in Oracle VirtualBox, I encountered a network connectivity issue. The virtual machine was unable to establish internet connectivity.

I investigated the issue using the Kali Linux terminal and applied the following NetworkManager configuration command:

**Solution implemented:**

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

After applying the command, I restarted the network connection and tested internet connectivity again.

**Outcome:** Internet connectivity was successfully restored after applying the configuration and restarting the network connection.

> **Important:** Network connection names may differ between systems. Use `nmcli connection show` to identify the correct connection profile before executing the command. The `ipv4.dad-timeout` setting relates to duplicate address detection, so this workaround may not apply to every network connectivity issue.

---

# 💡 What I Learned

Through this project, I gained practical experience setting up and configuring a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple virtual machines connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

I learned that a clean snapshot should be created **before performing risky or experimental activities**.

This provides a known-good recovery point for future cybersecurity exercises.

### 5. Troubleshooting and Documentation

I learned that technical challenges such as antivirus detection and network connectivity failures require systematic investigation and troubleshooting.

I also learned that documenting commands, configurations, screenshots, problems, and solutions is an important part of maintaining a professional cybersecurity project.

---

### 6. Practical Problem-Solving

Beyond the technical configuration, I learned the importance of troubleshooting unfamiliar issues, researching possible solutions, testing configuration changes, and documenting the outcomes.

The experience reinforced that setting up a cybersecurity laboratory involves more than installing tools; it requires an understanding of the underlying operating system, networking, and virtualisation concepts.


# 🔐 Security & Ethical Use

This laboratory is intended strictly for educational purposes, cybersecurity training, and authorised experimentation.

All practical security testing should be conducted within controlled environments or on systems for which permission has been granted.

---

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **Kali Linux Download Verification:** [Official Documentation](https://www.kali.org/docs/introduction/download-official-kali-linux-images/)

---

# 👤 Author

**[Tanaka Mushedhe]**  
Cybersecurity Learner | Cybersecurity at Networkwalks – Cohort B084

LinkedIn: [Tanaka Mushedhe]

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub

