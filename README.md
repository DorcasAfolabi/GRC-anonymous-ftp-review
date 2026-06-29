# GRC-anonymous-ftp-risk assessment
GRC Anonymous FTP Risk Assessment

## Overview

This project documents the assessment of an anonymous FTP login vulnerability within a controlled lab environment using Kali Linux and Metasploitable 2.

The objective of the exercise was to identify the risk associated with anonymous FTP access, evaluate its impact on confidentiality and compliance, and recommend appropriate security controls.



Lab Environment

## Component	                Description
Attacker Machine        	Kali Linux
Target Machine	          Metasploitable 2
Network Configuration   	Same Virtual Network
Service Tested          	FTP
FTP Port	                TCP 21



## Assessment Steps

## 1. Service Discovery

An Nmap scan was performed against the target machine to identify exposed services and open ports.

The scan identified FTP running on TCP port 21.

Evidence:



## 2. Authentication Assessment

The FTP service was accessed using anonymous authentication.

Username used:

anonymous

No password was required to gain access.

Evidence:



## 3. Authorization Assessment

After successful authentication, directory enumeration was performed using the following commands:

ls
dir

The FTP server returned an empty directory listing.

Evidence:



## Finding

### Finding ID

GRC-FTP-001

## Finding Title

Anonymous FTP Authentication Enabled

## Description

The FTP service allowed unauthenticated users to establish authenticated sessions using the username “anonymous” without requiring valid credentials.

Although no files were exposed during testing, the configuration creates unnecessary organizational risk because future uploads or permission changes could expose sensitive information.



# Risk Assessment

## Category	               Assessment
Likelihood                	High
Impact            	        High
Overall Risk Rating	        High

## Justification

Anonymous FTP access bypasses normal authentication controls and violates the principle of least privilege. Unauthorized users may gain access to internal resources without accountability or traceability.



# Compliance Impact

The configuration conflicts with security requirements found in:

* ISO 27001 Access Control requirements
* NIST Cybersecurity Framework Identity Management controls
* PCI DSS access restriction requirements where applicable

The following security principles are violated:

* Least Privilege
* Authentication and Access Control
* Secure Configuration Management



## Risk Statement

Unauthorized users may gain access to organizational FTP services through anonymous authentication, potentially resulting in unauthorized disclosure, modification, or misuse of organizational information assets.



## Recommended Controls

1. Disable anonymous FTP access.
2. Replace FTP with SFTP where possible.
3. Require authentication for all remote services.
4. Restrict access using firewall rules.
5. Conduct periodic vulnerability scans.
6. Perform regular configuration reviews and audits.
7. Enable centralized logging and monitoring.



## Conclusion

This assessment demonstrates how insecure service configurations can create governance, risk, and compliance concerns even when immediate exploitation is not observed.

From a GRC perspective, anonymous access represents a failure of access control governance and should be remediated as part of an organization’s secure configuration management program.
