# Configuration Details: AD-LAB-SERVER (Domain Controller)

This document outlines the detailed configuration steps for the `AD-LAB-SERVER` virtual machine, which functions as the primary Domain Controller (DC) for the `patrick.local` domain.

---

### 1. VM Hardware & OS Specifications

- **Memory**: 4 GB RAM
- **Processors**: 2 Cores
- **Hard Disk**: 60 GB
- **Network Adapter**: Connected to a private, isolated network (`VMnet2` - Host-only)
- **Installation Media**: Windows Server 2022 Evaluation ISO
- **Operating System**: Windows Server 2022 Datacenter (Desktop Experience)

*(For detailed hardware settings, see screenshots `SERVER-01` through `SERVER-05`)*

---

### 2. Initial System Configuration

Before installing Active Directory, the server was configured with a static identity on the network.

- **Hostname**: `DC01`
- **Workgroup**: `WORKGROUP` (Default)
- **Network Interface**: Ethernet0
- **Static IPv4 Address**: `192.168.172.10`
- **Subnet Mask**: `255.255.255.0`
- **Default Gateway**: *(Not Configured)*
- **Preferred DNS Server**: `127.0.0.1` (Loopback Address)

*Evidence: [SERVER-07-Initial-Properties.PNG](../screenshots/SERVER-07-Initial-Properties.PNG)*

---

### 3. Active Directory Domain Services (AD DS) Installation

The core AD DS role was installed using the "Add Roles and Features" wizard in Server Manager.

| Feature Installed | Status |
|---|---|
| Active Directory Domain Services | Succeeded |
| Group Policy Management | Succeeded |
| Remote Server Administration Tools | Succeeded |
| AD DS and AD LDS Tools | Succeeded |
| Active Directory Module for Windows PowerShell | Succeeded |

*Evidence: [SERVER-08-ADDS-Role-Selection.PNG](../screenshots/SERVER-08-ADDS-Role-Selection.PNG), [SERVER-10-ADDS-Install-Success.PNG](../screenshots/SERVER-10-ADDS-Install-Success.PNG)*

---

### 4. Domain Controller Promotion

The server was promoted to the first Domain Controller in a new forest.

| Configuration | Setting |
|---|---|
| Deployment Operation | Add a new forest |
| Root Domain Name | `patrick.local` |
| Forest Functional Level | Windows Server 2016 |
| Domain Functional Level | Windows Server 2016 |
| DNS Server Role | Enabled |
| Global Catalog (GC) | Enabled |
| DSRM Password | Set for recovery purposes |
| NetBIOS Domain Name | `PATRICK` |

*Evidence: [SERVER-11-AD-Deployment-Config.PNG](../screenshots/SERVER-11-AD-Deployment-Config.PNG), [SERVER-12-AD-DC-Options.PNG](../screenshots/SERVER-12-AD-DC-Options.PNG)*

---

### 5. Active Directory Structure & Objects

A logical structure was built in "Active Directory Users and Computers" to simulate a corporate environment.

#### Organizational Units (OUs)
- `_Melbourne_Office`
  - `_IT`
  - `_Sales`
  - `_Marketing`

*Evidence: [SERVER-16-OU-Structure-Created.PNG](../screenshots/SERVER-16-OU-Structure-Created.PNG)*

#### User Accounts
| Display Name | User Logon Name | Location (OU) |
|---|---|---|
| Patrick Lunney | `p.lunney@patrick.local` | `_IT` |

#### Security Groups
| Group Name | Group Scope / Type | Members |
|---|---|---|
| `SG_IT_Admins` | Global / Security | Patrick Lunney (`p.lunney`) |

*Evidence: [SERVER-18-Group-Membership-Confirmation.PNG](../screenshots/SERVER-18-Group-Membership-Confirmation.PNG)*
