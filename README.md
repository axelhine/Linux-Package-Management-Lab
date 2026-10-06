# Google Cybersecurity Certificate Lab: Linux Package Management & System Auditing

## Project Overview
This repository contains documentation from a practical lab completed as part of the **Google Cybersecurity Certificate**. Executed within a Debian-based Qwiklabs virtual environment, the objective was to securely provision, verify, and decommission network security applications via the Linux Bash shell using the **Advanced Package Tool (APT)**.

Maintaining strict control over installed software is a critical component of risk management. By accurately managing the lifecycles of command-line utilities, security teams can ensure operational readiness while minimizing a system's attack surface.

## Key Skills & Tools Demonstrated
* **Environment:** Qwiklabs Virtual Machine (Debian-based Linux)
* **Package Manager:** APT (Advanced Package Tool)
* **Privilege Management:** `sudo` (Superuser Do)
* **Security & Network Tools:** 
  * `nload` (Real-time network traffic and bandwidth monitoring)
  * `tcpdump` (Command-line packet analysis and capture)
* **Core Competencies:** Software provisioning, dependency resolution, attack surface reduction (uninstallation), and active system auditing.

---

## Lab Execution & Operational Walkthrough

### 1. Provisioning the `nload` Utility
The first objective was to install the `nload` network traffic monitor using elevated privileges. APT successfully resolved the dependencies and configured the package.
```bash
sudo apt install nload
```

### 2. Verifying Application Options
Following installation, the command line syntax and help menu for `nload` were accessed to verify operational readiness. The output confirmed the installation of `nload version 0.7.4` and detailed configuration parameters for network device monitoring and traffic unit displays.
```bash
nload -h
```

### 3. Decommissioning Software (Attack Surface Reduction)
To simulate system hardening and compliance enforcement, the application was removed. Removing unused software is a fundamental governance practice to eliminate unpatched vulnerabilities and free up disk space.
```bash
sudo apt remove nload -y
```
To verify the removal was successful, the application was called again, appropriately returning an error confirming the binary was stripped from the system:
```bash
nload -h
```

### 4. Provisioning Packet Analysis Tools
The critical packet analyzer `tcpdump` was provisioned next. During this installation, the APT package manager automatically resolved and installed required underlying dependencies, such as the `libpcap0.8` library.
```bash
sudo apt install tcpdump -y
```

### 5. Restoring the Baseline and System Auditing
The `nload` tool was reintroduced to the environment to establish a dual-tool monitoring baseline. Finally, an inventory audit was conducted to verify the active status of the system's packages.
```bash
sudo apt install nload -y
apt list --installed
```

---

## Result & Business Impact
* **Controlled Environment Hardening:** Successfully demonstrated the ability to precisely scale security tooling up and down using `sudo`, enforcing the principle of least privilege and strict attack surface management.
* **Automated Dependency Resolution:** Safely navigated Linux software installations by allowing APT to handle underlying shared libraries automatically, ensuring system stability.
* **Audit Readiness:** By utilizing the `apt list --installed` command, demonstrated the ability to generate reliable software inventories—a critical operational requirement for internal security compliance and external risk assessments.
