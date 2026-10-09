# TryHackMe — [Room Name]

> **Platform:** TryHackMe
> **Category:** Linux / Enumeration / Privilege Escalation
> **Difficulty:** [Easy]
> **Status:** Completed / In Progress
> **Environment:** Authorized TryHackMe lab
>
> **Spoiler warning:** This write-up may contain hints and solutions.

## 1. Overview

The objective of this lab was to investigate a Linux machine by identifying exposed services, discovering a hidden web directory, testing authentication security, enumerating Linux users, and investigating privilege-escalation opportunities.

### Skills practiced

* Service enumeration
* Web directory discovery
* Username and password auditing
* Password hash analysis
* Linux user and permission enumeration
* Privilege escalation analysis

## 2. Lab Setup

* Connected to the TryHackMe network using the official OpenVPN configuration.
* Deployed the target machine.
* Recorded the target IP address: `[10.48.171.75]`

**Safety note:** All testing was performed against the authorized lab target.

## 3. Reconnaissance and Service Enumeration

### Objective

Identify open ports and determine which services are running.

### Methodology

1. Confirmed the target IP address.
2. Scanned the target for accessible services.
3. Investigated service versions and potential entry points.

### Findings

| Port   | Service   | Version   | Observation |
| ------ | --------- | --------- | ----------- |
| [22/tcp] | [ssh] | [OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)] | [Remote administration service is exposed. Review authentication settings and software patch status.]   |
| [80/tcp] | [http] | [Apache httpd 2.4.41 ((Ubuntu))] | [Web server is accessible. Review web configuration, security headers, and exposed content.]   |
| [139/tcp] | [netbios-ssn] | [Samba smbd 4] | [File-sharing related service is exposed. Review share permissions and access restrictions.]   |
| [445/tcp] | [netbios-ssn] | [Samba smbd 4] | [SMB service is accessible. Check for unauthorized share access and insecure configurations.]   |
| [8009/tcp] | [ajp13] | [Apache Jserv (Protocol v1.3)] | [AJP connector is exposed. Review whether remote access is necessary and whether access is restricted.]   |
| [8080/tcp] | [http] | [Apache Tomcat 9.0.7] | [Tomcat web service is accessible. Review the application, management interface exposure, and patch status.]   |

**Evidence:** The Nmap service-version scan of the target host 10.48.171.75 identified six open TCP ports: 22 (SSH), 80 (HTTP), 139 (NetBIOS/SMB), 445 (SMB), 8009 (AJP), and 8080 (HTTP/Tomcat). The detected services included OpenSSH 8.2p1, Apache HTTP Server 2.4.41, Samba 4, and Apache Tomcat 9.0.7.

The Nmap output serves as evidence of the accessible services and their detected versions. A sanitized screenshot of the terminal output can be included in the report.

**Lessons learned:** The reconnaissance and service enumeration process demonstrated how Nmap can identify open ports, detect running services, and collect software version information. The results revealed that the target provides remote administration, web hosting, file sharing, and application server services.

The findings highlighted the importance of reviewing exposed services, restricting unnecessary network access, securing SMB shares, reviewing AJP connector exposure, and keeping software updated. The scan also demonstrated that identifying an open port does not automatically confirm a vulnerability; additional investigation is necessary to verify potential security weaknesses.

## 4. Web Enumeration

### Objective

Identify web directories and investigate potentially interesting pages.

### Methodology

* Visited the web service.
* Inspected the available pages and links.
* Used an authorized directory-discovery method.
* Investigated the discovered directory.

### Findings

* Web server: [SERVICE]
* Hidden directory: [DIRECTORY]
* Interesting observations: [FINDINGS]

**Evidence:** [Insert screenshot with sensitive information removed.]

## 5. Authentication Testing

### Objective

Evaluate the security of the discovered login service.

### Methodology

* Identified the relevant authentication service.
* Performed password testing within the lab's authorized scope.
* Recorded the resulting account access and the evidence supporting it.

### Findings

* Username: `[REDACTED OR SPOILER]`
* Authentication service: `[SERVICE]`
* Security weakness: [EXPLAIN THE WEAKNESS]

**Security lesson:** Weak or reused passwords can expose accounts to unauthorized access. Strong unique passwords, rate limiting, and appropriate monitoring help reduce this risk.

## 6. Hash Analysis

### Objective

Understand password hashes and evaluate whether a recovered hash is resistant to guessing.

### Methodology

* Identified the hash format where possible.
* Distinguished a password hash from an encrypted password.
* Conducted authorized hash analysis in the lab.

### Findings

* Hash type: [HASH TYPE]
* Result: [REDACTED OR SPOILER]
* Lesson learned: [EXPLAIN]

**Security lesson:** Passwords should be stored using a suitable salted password-hashing scheme, such as Argon2id, scrypt, or appropriately configured bcrypt.

## 7. Linux Enumeration

### Objective

Understand the current account's permissions and identify potential security weaknesses.

### Areas investigated

* Current user and group memberships
* Other local users
* File and directory permissions
* Sudo permissions
* Scheduled tasks and services
* Potentially unsafe configurations

### Findings

* Current user: [USER]
* Other user discovered: [USER]
* Relevant permissions or configuration: [FINDING]

**Evidence:** [Add sanitized command output.]

## 8. Privilege Escalation Analysis

### Objective

Determine whether a configuration weakness could allow access to higher privileges.

### Analysis

* Suspected weakness: [WEAKNESS]
* Evidence: [EVIDENCE]
* Impact: [POTENTIAL IMPACT]
* Remediation: [HOW TO FIX IT]

**Security lesson:** Linux systems should follow least privilege, protect privileged scripts and files, and restrict unnecessary sudo permissions.

## 9. Questions and Answers

| Question                          | Answer                |
| --------------------------------- | --------------------- |
| Exposed services                  | [YOUR FINDINGS]       |
| Hidden web directory              | [YOUR ANSWER]         |
| Discovered username               | [YOUR ANSWER]         |
| Discovered password               | [REDACTED OR SPOILER] |
| Service used to access the server | [YOUR ANSWER]         |
| Other user discovered             | [YOUR ANSWER]         |
| Significance of the other user    | [YOUR EXPLANATION]    |
| Final password                    | [REDACTED OR SPOILER] |

## 10. What I Learned

* How to enumerate exposed services.
* How to investigate hidden web directories.
* How weak credentials create security risks.
* How Linux users, groups, and permissions work.
* How to identify and explain potential privilege-escalation weaknesses.
* How to document findings and recommend remediation.

## 11. Conclusion

This lab provided practical experience with Linux enumeration, authentication security, hash analysis, and privilege-escalation assessment.

The most important takeaway was learning how individual configuration weaknesses can combine to increase the risk to a system.

**Write-up completed by:** [YOUR GITHUB USERNAME]
**Lab:** [TRYHACKME ROOM URL]
