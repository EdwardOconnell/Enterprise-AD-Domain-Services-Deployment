
<div align="center">

<img src="./assets/eds-logo.png" alt="Ed's Professional Logo" width="200" />

# Enterprise Windows Domain & Identity Infrastructure

### Windows Server 2025 • VMware Workstation Pro • Active Directory

![Project Status](https://img.shields.io/badge/Status-In_Progress-orange?style=flat-square)
![Operating System](https://img.shields.io/badge/Windows_Server-2025-0078D4?style=flat-square)
![Hypervisor](https://img.shields.io/badge/Hypervisor-VMware_Workstation_Pro-607078?style=flat-square)

</div>

---

## Infrastructure Overview

This repository tracks the design, configuration, and testing of a Windows-based enterprise domain infrastructure deployed through VMware Workstation Pro.

The project establishes a simulated organizational network powered by Windows Server 2025, with Active Directory Domain Services (AD DS) serving as the foundation for centralized authentication, directory administration, and resource authorization.

The environment is intended to demonstrate practical systems engineering concepts through the integration of Windows networking services, user and computer account administration, security group design, policy-based configuration management, and PowerShell-driven automation.

Deployment activities will be supported by configuration records, implementation procedures, diagnostic testing, and technical evidence.

> **Current State: Implementation in Progress**
>
> Infrastructure components and configuration procedures will be documented as each deployment stage is completed. Planned functionality should not be interpreted as fully implemented or validated.

---

## Platform and Administrative Technologies

| Category | Platform / Technology |
|---|---|
| Virtual Machine Platform | VMware Workstation Pro |
| Server Operating System | Microsoft Windows Server 2025 |
| Endpoint Operating System | Windows 11 Enterprise |
| Directory Infrastructure | Active Directory Domain Services |
| Authentication Protocols | Kerberos / NTLM |
| Directory Administration | Active Directory Users and Computers |
| Hostname Resolution | Microsoft DNS Server |
| Network Address Distribution | Microsoft DHCP Server |
| Configuration Management | Group Policy Management |
| Authorization Model | Security Groups / RBAC |
| File System Security | NTFS Access Control Lists |
| Administrative Scripting | Windows PowerShell |
| Diagnostic Utilities | DCDIAG, NLTEST, GPRESULT, NSLOOKUP |
| Logging and Monitoring | Windows Event Viewer |

---

## Environment Design

The planned infrastructure uses a private VMware virtual network to reproduce core functions commonly found within an organization's Windows domain environment.

The deployment begins with a primary domain controller and a Windows client. Additional systems may be introduced to support expanded authentication, replication, and workstation policy testing.

### Virtual System Inventory

| Virtual Machine | Operating System | Intended Purpose |
|---|---|---|
| DC01 | Windows Server 2025 | Domain Services, DNS, Directory Management |
| CLIENT01 | Windows 11 Enterprise | Domain Membership and User Authentication |
| DC02 | Windows Server 2025 | Secondary Domain Controller / Replication Testing (Optional) |
| CLIENT02 | Windows 11 Enterprise | Additional Client Validation (Optional) |

### Proposed IP Addressing

| Network Parameter | Configuration |
|---|---|
| Virtual Network | VMware VMnet2 |
| Network Mode | Host-Only |
| Subnet | 192.168.100.0/24 |
| Primary Domain Controller | 192.168.100.10 |
| Preferred DNS Server | 192.168.100.10 |
| Client DHCP Pool | 192.168.100.100–192.168.100.199 |
| Internal Domain Namespace | corp.example.test |

The network design prioritizes separation from the physical LAN, predictable server addressing, and centralized resolution of domain resources.

VMware's built-in DHCP service will be disabled on the selected lab network before implementing Windows DHCP to prevent competing address assignments.

---

## Implementation Workstreams

### 01 — Virtualization and Network Foundation

The initial workstream establishes the computing environment required to host the Windows domain.

**Planned activities:**

- Install and configure VMware Workstation Pro.
- Provision virtualized server and endpoint systems.
- Allocate processor, RAM, and virtual disk resources.
- Configure a dedicated host-only virtual network.
- Establish consistent virtual NIC connectivity.
- Create recovery snapshots at deployment checkpoints.
- Verify communication between the virtual systems.

### 02 — Windows Server and Domain Services

This workstream introduces the server operating system and core Active Directory components.

**Planned activities:**

- Deploy Windows Server 2025.
- Assign a permanent hostname and IPv4 configuration.
- Install AD DS and required management tools.
- Establish a new Active Directory forest.
- Promote the Windows Server instance to a domain controller.
- Configure domain-integrated DNS.
- Examine domain controller health and service registration.
- Verify the availability of directory services.

### 03 — Directory Structure and Account Administration

A structured directory hierarchy will be designed to represent departments, administrative responsibilities, and security boundaries within a simulated enterprise.

**Planned activities:**

- Develop an organizational unit structure.
- Separate employee and administrative identities.
- Define departmental security groups.
- Provision domain user accounts.
- Organize computer objects.
- Configure appropriate group memberships.
- Establish delegated administration where applicable.
- Document naming conventions and account standards.

### 04 — Windows Networking Services

Domain operations rely on functional DNS resolution and consistent network addressing.

**Planned activities:**

- Examine Active Directory DNS zones.
- Verify domain service locator records.
- Test hostname and domain resolution.
- Install and authorize the Windows DHCP Server.
- Establish address pools and lease parameters.
- Configure DNS options for DHCP clients.
- Validate client network assignments.
- Diagnose potential addressing or resolution failures.

### 05 — Endpoint Domain Enrollment

Client computers will be integrated into the centralized Windows domain to evaluate authentication and policy processing.

**Planned activities:**

- Install Windows 11 Enterprise virtual endpoints.
- Configure client network interfaces.
- Direct clients to the internal domain DNS server.
- Register workstations with the Active Directory domain.
- Authenticate using domain user credentials.
- Validate domain membership and trust connectivity.
- Review domain logon functionality.
- Test name resolution and directory availability.

### 06 — Policy-Based Administration and Security

Group Policy will provide centralized configuration management and baseline security enforcement for domain-joined systems.

**Planned activities:**

- Create and organize Group Policy Objects.
- Establish account password requirements.
- Configure account lockout behavior.
- Apply workstation configuration policies.
- Implement Windows Firewall settings.
- Configure security-related audit policies.
- Apply policy settings to appropriate organizational units.
- Verify resultant policy configuration using GPRESULT.

### 07 — Identity Automation and Scripting

PowerShell will be used to demonstrate repeatable directory administration procedures and reduce reliance on manual account configuration.

**Planned activities:**

- Script organizational unit provisioning.
- Generate domain user accounts from structured input.
- Automate security group creation.
- Manage directory group membership.
- Develop employee onboarding operations.
- Implement account disabling and offboarding procedures.
- Export directory inventory reports.
- Validate scripts with error handling and execution results.

### 08 — Operational Testing and Troubleshooting

The final implementation workstream focuses on validating system functionality and documenting operational findings.

**Planned activities:**

- Execute domain controller diagnostic checks.
- Verify DNS service availability.
- Confirm Active Directory authentication.
- Examine applied Group Policy settings.
- Test assigned file system permissions.
- Inspect Windows security and system event logs.
- Investigate controlled configuration failures.
- Record remediation procedures and retest results.

---

## Deployment Tracking

Project milestones will be marked complete only after the related configuration and validation activities have been performed.

- [ ] VMware Hypervisor and Virtual Network Setup
- [ ] Windows Server Operating System Deployment
- [ ] Active Directory Forest and Domain Provisioning
- [ ] Directory Hierarchy and Organizational Unit Design
- [ ] Domain User and Security Group Configuration
- [ ] DNS Server Implementation and Testing
- [ ] Windows DHCP Scope Configuration
- [ ] Windows Client Domain Enrollment
- [ ] Group Policy Administration
- [ ] Security Baseline Implementation
- [ ] PowerShell Identity Management Automation
- [ ] Domain Infrastructure Health Verification
- [ ] Operational Troubleshooting Documentation
- [ ] Technical Evidence Collection

---

## Validation Strategy

Each deployed infrastructure component will undergo functional checks before being considered complete.

| Infrastructure Component | Planned Verification |
|---|---|
| Virtual Networking | IP connectivity and adapter configuration |
| Domain Controller | DCDIAG health assessment |
| Active Directory | Directory queries and domain availability |
| DNS | Forward lookup and SRV record resolution |
| DHCP | Lease allocation and DHCP option validation |
| Domain Membership | Secure channel verification |
| User Authentication | Interactive domain sign-in |
| Group Policy | GPRESULT and policy behavior testing |
| Access Management | Security group permission validation |
| PowerShell Automation | Script execution and resulting directory objects |
| Security Auditing | Event log review and event generation |

Test results, command outputs, and configuration screenshots will be retained as implementation evidence.

---

## Engineering Records and Evidence

The repository will progressively contain technical materials supporting the deployment.

These records may include:

- Virtual network topology diagrams.
- Windows Server installation notes.
- Active Directory configuration screenshots.
- Organizational unit and group structure records.
- DNS and DHCP configuration evidence.
- Domain-joined workstation verification.
- Group Policy configuration and reporting.
- PowerShell source code and execution results.
- Diagnostic command outputs.
- Troubleshooting observations and corrective actions.

The purpose of this evidence is to demonstrate how the environment was configured, what was tested, and whether the expected results were achieved.

---

## Planned Repository Organization

```text
Enterprise-Windows-Domain-Infrastructure/
|
|-- README.md
|
|-- assets/
|   `-- eds-logo.png
|
|-- architecture/
|   |-- virtual-network-diagram.png
|   `-- environment-design.md
|
|-- deployment/
|   |-- 01-virtualization.md
|   |-- 02-windows-server.md
|   |-- 03-directory-services.md
|   |-- 04-directory-structure.md
|   |-- 05-network-services.md
|   |-- 06-client-integration.md
|   |-- 07-group-policy.md
|   `-- 08-system-validation.md
|
|-- automation/
|   |-- directory-provisioning/
|   |-- account-management/
|   `-- reporting/
|
|-- evidence/
|   |-- virtualization/
|   |-- active-directory/
|   |-- dns-dhcp/
|   |-- workstations/
|   |-- security-policies/
|   `-- diagnostics/
|
`-- troubleshooting/
```

Folders and technical artifacts will be introduced as the corresponding implementation activities are completed.

---

## Security and Operational Boundaries

This infrastructure is intended exclusively for controlled educational and engineering validation.

The environment will use fictional organizational identities and isolated virtual networking.

Security practices incorporated into the project design include:

- Least-privilege administrative access.
- Separation of standard and privileged accounts.
- Group-based authorization.
- Managed workstation configurations.
- Account authentication controls.
- Security event monitoring.
- Controlled network exposure.
- Documentation of administrative changes.

Sensitive credentials, private keys, virtual machine disk images, and other confidential artifacts will not be included in the public repository.

---

## Current Development Status

**Project Phase: Infrastructure Implementation — In Progress**

The environment is being assembled and documented through a series of defined engineering milestones.

As configuration and testing progress, this repository will be expanded with implementation notes, PowerShell automation, troubleshooting records, and supporting technical evidence.

Completion of individual workstreams will be reflected in the deployment checklist.

---

<div align="center">

<img src="./assets/footer-logo.png" alt="Ed's Footer Logo" width="130" />

<strong>Edward O'Connell</strong>

<p><em>IT Infrastructure • Windows Server Administration • Enterprise Networking</em></p>

<p>IT professional with more than three years of hands-on experience in technical support, systems configuration, and IT infrastructure operations. Holds an associate degree in Cybersecurity and is currently pursuing a bachelor's degree in Cloud and Network Engineering, with career goals in systems administration, systems engineering, and related infrastructure roles.</p>

<p><a href="https://www.linkedin.com/in/edwardcoconnelliii/">Connect with me on LinkedIn</a></p>

</div>
