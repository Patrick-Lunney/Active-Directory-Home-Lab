# Configuration Details: AD-LAB-SERVER (Domain Controller)

This document outlines the detailed configuration steps for the `AD-LAB-SERVER` virtual machine, which functions as the primary Domain Controller (DC) for the `patrick.local` domain.

---

### 1. VM Hardware Specifications

The virtual machine was provisioned in VMware Workstation with the following resources:

* **Memory:** 4 GB RAM
* **Processors:** 2 CPU Cores
* **Hard Disk:** 60 GB
* **Network Adapter:** Connected to a private, isolated network (`VMnet2` - Host-only)
* **Installation Media:** Windows Server 2022 Evaluation ISO

---

### 2. Operating System Installation

The OS was installed using a clean, custom installation method. The "Desktop Experience" version was chosen to ensure the full graphical user interface was available for administration.

* **Edition:** Windows Server 2022 Datacenter Evaluation (Desktop Experience)

---

### 3. Initial Server Configuration

Before installing Active Directory, two critical pre-configurations were performed:

1.  **Computer Name:** The server's randomly generated hostname was changed to `DC01` to follow a standard naming convention.
2.  **Static IP Address:** The server was configured with a static IP address of `192.168.172.10` and its DNS was set to loopback (`127.0.0.1`) in preparation for its role as a DNS server.

---

### 4. Active Directory Installation & Promotion

The server was configured as the first Domain Controller in a new forest.

* **Role Installation:** The "Active Directory Domain Services" role was installed via Server Manager.

* **Domain Promotion:** The server was promoted using the AD DS Configuration Wizard.
    * A new forest was created with the root domain name **`patrick.local`**.
    * The Domain Name System (DNS) server role was installed and configured alongside AD DS.
    * A Directory Services Restore Mode (DSRM) password was set for disaster recovery purposes.
    * All prerequisite checks passed successfully before the final installation.

---

### 5. Active Directory Object Management

A logical structure was built within Active Directory to simulate a corporate environment.

* **Organizational Units (OUs):** A top-level OU (`_Melbourne_Office`) was created, with departmental OUs (`_IT`, `_Sales`, `_Marketing`) nested inside.

* **Users & Groups:** A sample user account (`p.lunney`) was created in the `_IT` OU. A security group (`SG_IT_Admins`) was also created, and the user was added as a member to demonstrate permission management.
