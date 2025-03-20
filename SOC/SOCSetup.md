# Malware Analysis Lab Setup

This guide covers everything from hardware selection to essential tools. You need to first define the scope for your lab which can be from following

## 1. Define Your Lab Scope
- **Static Analysis**
- With Static analysis you can study the code of malware without running it. This means, researchers are looking at how the malware is built and what it's designed to do, all without actually letting it execute on a computer.
- **Dynamic Analysis**
- With Dynamic analysis, the researchers can execute malware in a controlled environment in oder to analyse the malware sample.
- **Memory Forensics**
- Using Memory Forensics, we can investigate system memory dumps to determine the malicious actions which were done on a particular system
- **Network Analysis**
- Here, the researchers can actively observe malware communication happening in a network.

## 2. Hardware & Virtualization
- **Recommended Specs:** 16GB RAM, 500GB+ SSD, Multi-core CPU
- **Virtualization Software:** VMware Workstation, VirtualBox
- **Cloud Infrastructure:** Use subscription based AWS instances as sandbox.
- **Network Isolation:** Use an **air-gapped system** or **segmented network**

## 3. Virtual Machine Setup
- **Base OS:**
  - Windows 10/11
  - Linux (Ubuntu/Kali)
  - Legacy systems (Windows 8 or older for older malware)
- **Security Measures:**
  - Use **Snapshots & Cloning** to revert systems quickly
  - Configure **Host-Only Network** or **NAT with firewall rules**

## 4. Essential Tools
### Static Analysis
- [PeStudio](https://www.winitor.com/) - PE file analysis
- [Exeinfo PE](http://www.exeinfo.xn.pl/) - Packer detection
- [BinText](https://www.mcafee.com/enterprise/en-us/threat-intelligence/mcafee-labs.html) - String extraction
- [Ghidra](https://ghidra-sre.org/) / [IDA Free](https://hex-rays.com/ida-free/) - Disassembly

### Dynamic Analysis
- [Cuckoo Sandbox](https://cuckoosandbox.org/) - Automated malware detonation
- [Process Hacker](https://processhacker.sourceforge.io/) - Process monitoring
- [ProcMon](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) - System behavior analysis
- [Wireshark](https://www.wireshark.org/) - Network traffic monitoring
- [Fakenet-NG](https://github.com/fireeye/flare-fakenet-ng) - Simulating internet services

### Reverse Engineering
- [Radare2](https://rada.re/n/) - Open-source disassembler
- [x64dbg](https://x64dbg.com/) - Debugger

### Memory Forensics
- [Volatility](https://github.com/volatilityfoundation/volatility) - Memory dump analysis
- [Rekall](https://github.com/google/rekall) - Memory forensic framework

## 5. Security Best Practices
- **Disable** Shared Folders, Clipboard Sharing, Drag-and-Drop
- **Isolate Network** (Use Tails/Whonix for safe outbound analysis)
- **Use Firewalled & Restricted Internet Access**

## 6. Automate & Monitor
- **Cuckoo Sandbox** for automated malware detonation
- **ELK Stack / Splunk** for centralized logging
- **Sysmon + Sigma Rules** for detecting suspicious activities
