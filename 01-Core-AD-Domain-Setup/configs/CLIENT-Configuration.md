# Configuration Details: AD-LAB-CLIENT (Workstation)

This document outlines the detailed configuration steps for the `AD-LAB-CLIENT` virtual machine, which functions as a standard user workstation joined to the `patrick.local` domain.

---

### 1. VM Hardware Specifications

The virtual machine was provisioned in VMware Workstation with the following resources:

* **Memory:** 2 GB RAM
* **Processors:** 2 CPU Cores
* **Hard Disk:** 60 GB
* **Network Adapter:** Connected to the private `VMnet2` (Host-only) network.
* **Installation Media:** Windows 10 Enterprise (22H2) Evaluation ISO

*(See screenshots `CLIENT-01` through `CLIENT-05` for detailed hardware settings.)*

---

### 2. Operating System Installation & Verification

A clean installation of Windows 10 Enterprise was performed. The installation required an internet connection (via a temporary NAT network setting) to complete the license activation for the 90-day evaluation period. The OS version was verified in system settings to confirm a modern build was installed, despite a cosmetic glitch with the desktop watermark.

* **Edition:** Windows 10 Enterprise Evaluation
* **Version:** 22H2

---

### 3. Domain Integration

Once installed, the client VM was moved to the isolated `VMnet2` network. To join the domain, two key steps were performed:

1.  **DNS Configuration:** The client's preferred DNS server was manually set to the static IP address of the Domain Controller (`192.168.172.10`). This allows the client to find the `patrick.local` domain on the network.
2.  **Domain Join:** The computer was joined to the `patrick.local` domain using domain administrator credentials. This was confirmed by the "Welcome to the patrick.local domain" message.

---

### 4. Final Verification

The ultimate test of the lab environment was to log into the client machine using a domain user account (`p.lunney`) created on the Domain Controller, rather than a local account. This test was successful.

The `whoami` command was used in the Command Prompt to provide definitive proof of a successful domain login, displaying the `patrick\p.lunney` user context.
