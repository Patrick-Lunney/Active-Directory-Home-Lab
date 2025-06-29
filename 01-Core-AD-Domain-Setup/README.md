# Module 1: Core Active Directory Domain Setup

### Objective
This document outlines the foundational setup of a complete Active Directory environment. The goal was to deploy a Domain Controller and a client workstation in an isolated virtual network, establishing a centrally managed identity and access management system from scratch.

### High-Level Process
1.  **Environment Setup:** Two virtual machines (`AD-LAB-SERVER` and `AD-LAB-CLIENT`) were created in VMware Workstation on a dedicated, isolated "Host-only" network.
2.  **Server Configuration:** Windows Server 2022 was installed, configured with a static IP, and the Active Directory Domain Services (AD DS) and DNS roles were installed.
3.  **Domain Promotion:** The server was promoted to a Domain Controller, creating a new forest and root domain named `patrick.local`.
4.  **AD Management:** A logical company structure was built using Organizational Units (OUs), and a sample user and security group were created to demonstrate identity management.
5.  **Client Integration:** The Windows 10 client machine was configured and successfully joined to the `patrick.local` domain.
6.  **Verification:** Final success was verified by logging into the client machine using the domain user account authenticated by the server.

### Final Configuration
* **Domain:** `patrick.local`
* **Domain Controller:** `DC01` (`192.168.172.10`)
* **Client Workstation:** `CLIENT01`

### Detailed Documentation
For a step-by-step breakdown of the configuration for each machine, please see the detailed documentation below:

* **[View Server Configuration Details](configs/SERVER-Configuration.md)**
* **[View Client Configuration Details](configs/CLIENT-Configuration.md)**
