# Investigation

## 1. Starting Point

The investigation began with one simple question:

> What can I discover about this machine from the network?

The target was an intentionally vulnerable machine inside my authorized laboratory environment.

Before starting the investigation, I confirmed that the target IP address was:

`10.0.2.3`

I used Bettercap to help confirm the target on the network.

## 2. Looking for Open Ports

I started with a basic Nmap scan:

```sudo nmap 10.0.2.3```

The scan showed several open ports.

The first port that caught my attention was:

Port 21 — FTP

I decided to investigate it further.

At this point, I did not know whether FTP would lead to a successful attack. I was simply following something interesting that I had discovered.

This was important because I wanted the investigation to follow the evidence rather than decide on an attack path before investigating the system.

## 3. Finding Out What Was Running on Port 21

I wanted to know what software was running behind the FTP service.

I used:

```sudo nmap -sV -p 21 10.0.2.3```

The scan identified the service as:

**vsftpd 2.3.4**

This gave me a specific piece of information to investigate instead of simply knowing that FTP was open.

### What This Told Me

The machine was running an old version of FTP server software.

I decided to investigate both the authentication system and the software itself.

## 4. Testing FTP Access

Because FTP was open and accepting connections, I investigated whether valid login credentials could provide access.

Using the available Kali wordlist, I tested credentials against the FTP service.

I found:

Username: user

Password: user

I then used these credentials to log in.

The login was successful.
<img width="770" height="335" alt="ftp password" src="https://github.com/user-attachments/assets/cdbe768d-3a9f-4e3f-b534-0492b5a0f719" />


### Why This Mattered

The credentials were extremely weak.

This showed that a technical attack did not necessarily need to begin with a sophisticated vulnerability.

Poor credential practices could provide an attacker with an initial entry point.

### 5. What Could I Access?

After logging into FTP, I checked my current location:

pwd

The result showed that I was in:

/home/user

I then listed the available files and directories:

ls

Nothing obviously sensitive or useful was exposed.

I also tested whether I could create a file using the echo command.

The attempt was rejected.

<img width="551" height="276" alt="documentation" src="https://github.com/user-attachments/assets/ca11b4c1-1eb6-4501-b489-f4290b2ddf4f" />


### What This Told Me

The weak credentials had given me access, but the account did not immediately give me full control of the system.

This was an important finding.

Getting into a system and controlling a system are not the same thing.

At this point, the FTP login appeared to be a dead end, so I continued by investigating the FTP service itself.

## 6. Investigating vsftpd 2.3.4

I researched:

vsftpd 2.3.4 vulnerabilities

During the research, I discovered that this specific version of vsftpd was associated with a known backdoor vulnerability.

This changed the direction of the investigation.

I now had two separate things to examine:

1. Weak authentication
2. Vulnerable FTP software

The first was a security practice issue.

The second raised a question about software maintenance:

> Why was vulnerable software still running and exposed?

## 7. Testing the Vulnerability

I used Metasploit to locate the relevant vsftpd 2.3.4 backdoor module.

Inside msfconsole, I searched for vsftpd and identified the relevant module:

/exploit/unix/ftp/vsftpd_234_backdoor

I configured the required options, including the target address, and ran the module against my authorized laboratory target.

Result

The exploit successfully triggered the backdoor.

A shell was spawned on the target machine.

I then used:

getuid

The result showed that the session had root-level access.

This was the point where the investigation moved from limited user access to full system compromise.

<img width="778" height="300" alt="documentation5" src="https://github.com/user-attachments/assets/1c6418b4-11cd-46ec-b94e-7db8e0605524" />

## 8. What Did Root Access Allow?

With root-level access, I entered a shell on the target system.

I then tested whether I could create a file on the compromised machine.

The file was successfully created.

I also transferred the test file from the target to my Kali machine.

### What This Demonstrated

The vulnerability was no longer theoretical.

The investigation demonstrated that the vulnerable FTP service could lead to:

Remote access → shell access → root privileges → ability to modify and retrieve files

This confirmed that the vulnerability could have a serious impact on the system.

## 9. The Human Factor

The technical investigation revealed more than one security problem.

**Weak Credentials**

The FTP account accepted:

Username: user

Password: user

These credentials were successfully used to gain access to the FTP service.

Human/Security Factor

Weak credential choices or inadequate password controls can make it easier for attackers to gain initial access.

### What Could Have Helped?

- Strong password requirements

- Removal of weak or unnecessary accounts

- Regular credential reviews

- Multi-factor authentication where appropriate

- Monitoring for suspicious authentication attempts

**Vulnerable Software**

The FTP service was running:

vsftpd 2.3.4

Research showed that this version had a known backdoor vulnerability.

Human/Security Factor

The vulnerability itself was a technical flaw in the software.

However, the continued presence of vulnerable and exposed software raises a human and organizational question:

> Was there an effective process for identifying, patching, replacing, or removing vulnerable software?

### What Could Have Helped?

- Regular vulnerability scanning

- Patch management

- Software inventory

- Removing unnecessary services

- Monitoring exposed services

- Assigning clear responsibility for system maintenance


**Least Privilege**

The initial FTP account did not provide root access.

This limited what I could do after the first login.

However, the vulnerable service later allowed the investigation to reach root-level access.

This demonstrates why least privilege is important:

> Users and services should only have the access they need to perform their tasks.

Least privilege cannot prevent every vulnerability, but it can reduce the damage an attacker can cause after gaining access.

## 10. What This Investigation Taught Me

This investigation changed the way I look at a security breach.

At first, the investigation looked like a technical problem:

Open FTP → vulnerable software → exploit → root

But looking deeper revealed another layer:

Weak credentials → initial access

Poor software maintenance → vulnerable service remains exploitable

Insufficient access controls → greater potential impact

The technical attack was only one part of the story.

The bigger lesson is that cybersecurity is not only about finding vulnerabilities.

It is also about understanding the people, decisions, processes, and security practices that determine whether those vulnerabilities remain exploitable.

---

## Investigation Takeaway

A simple technical attack can become much more damaging when human and organizational security practices create the conditions for it.

This investigation therefore supports the idea that effective cybersecurity needs both:

**Strong technical controls** and **strong human and security practices**.
