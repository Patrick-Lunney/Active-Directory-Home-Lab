# Configuration Details: AD-LAB-CLIENT (Workstation)

This document outlines the detailed configuration steps for the `AD-LAB-CLIENT` virtual machine, which functions as a standard user workstation joined to the `patrick.local` domain.

---

### 1. VM Hardware & OS Specifications

- **Memory**: 2 GB RAM
- **Processors**: 2 Cores
- **Hard Disk**: 60 GB
- **Network Adapter**: Connected to the private `VMnet2` (Host-only) network.
- **Installation Media**: Windows 10 Enterprise (22H2) Evaluation ISO
- **Operating System**: Windows 10 Enterprise
- **Version**: 22H2

*Evidence: [CLIENT-06-OS-Specifications.PNG](../screenshots/CLIENT-06-OS-Specifications.PNG)*

---

### 2. Initial System Configuration

Before joining the domain, the client was configured with a standard local user account and a unique hostname.

- **Initial Setup**: Configured with a local user account (`PatrickLunney`) to complete the installation process.
- **Hostname**: The randomly generated computer name was changed to `CLIENT01` to follow a standard naming convention.

---

### 3. Domain Integration

The client workstation was successfully integrated into the `patrick.local` Active Directory domain.

#### DNS Configuration
The client's network adapter was configured to use the Domain Controller as its primary DNS server, enabling it to locate the domain.

| Setting | Value |
|---|---|
| Preferred DNS Server | `192.168.172.10` |

#### Domain Join Process
The computer was joined to the `patrick.local` domain using the domain administrator's credentials.

| Action | Result |
|---|---|
| Domain Join | Success |
| Confirmation | Received "Welcome to the patrick.local domain." message |

*Evidence: [CLIENT-07-Domain-Join-Success.PNG](../screenshots/CLIENT-07-Domain-Join-Success.PNG)*

---

### 4. Final Verification

The final test confirmed end-to-end functionality. The client machine was logged into using a domain user account (`p.lunney`) created on the Domain Controller.

| Test | Command | Result |
|---|---|---|
| Domain User Login | `whoami` | `patrick\p.lunney` |
| FQDN Verification | System Properties | Full Computer Name: `CLIENT01.patrick.local` |

*Evidence: [CLIENT-08-Domain-Login-Proof.PNG](../screenshots/CLIENT-08-Domain-Login-Proof.PNG)*
