# Human Factor Analysis

## Why I Looked at the Human Factor

I did not want this investigation to end with:

> "I found a vulnerability and exploited it."

I wanted to ask a bigger question:

> **Where did humans fit into this attack?**

The technical investigation showed me how I got from an exposed FTP service to root access.

The human-factor analysis helped me look at why those opportunities existed in the first place.

---

## 1. The Weak Password

One of the first things I discovered was that the FTP service accepted:

```
Username: service
Password: user
```
These credentials gave me access to the FTP service.

What does this have to do with humans?

A password is not a technical vulnerability by itself.

Someone chose the password.

Someone created or managed the account.

Someone decided what password rules were required.

That means the technical access point was connected to a human and security-management decision.

### What could have been different?

The organization could have:

- Required stronger passwords

- Blocked common or predictable passwords

- Removed accounts that were no longer needed

- Regularly reviewed user accounts

- Added stronger authentication where appropriate


### My takeaway

The first step into the system did not require an advanced attack.

A basic security weakness was enough to provide access.


---

2. The Vulnerable Software

The FTP service was running:

**vsftpd 2.3.4**

I researched this version and found that it was associated with a known backdoor vulnerability.

I then tested the vulnerability in my authorized lab and successfully gained root access.

Was this "human error"?

Not exactly.

The vulnerability itself was a technical problem in the software.

But that is not where the problem ends.

Software does not decide whether it should remain installed.

People do.

Someone has to:

- Know what software is running

- Know whether it is vulnerable

- Check for security updates

- Decide whether it should remain in use

- Remove or replace software when necessary

### My takeaway

The risk increases when the people and processes responsible for maintaining the system fail to identify and fix it.

---

3. The Exposed FTP Service

Port 21 was open and the FTP service was available to the network.

An open port is not automatically a vulnerability.

But every exposed service gives an attacker something to investigate.

The human question

> Did the system actually need this service to be exposed?



If FTP was unnecessary, disabling it could have removed the entire attack path.

This is a reminder that security is sometimes about making a simple decision:

> "Do we actually need this?"



### My takeaway

Sometimes reducing risk starts with removing something that does not need to be there.

---

4. The Jump From User to Root

My first FTP login did not give me root access.

I was limited to:

```
/home/user
```

I could not immediately perform privileged actions.

That limitation was good.

But after exploiting the vulnerable FTP service, I obtained root-level access.

This showed me something important:

> Limiting what an account can do is useful, but it cannot replace other security controls.

What could have reduced the damage?

The principle of least privilege should be applied to users and services.

A compromised service should not have more access than it needs.

Other controls such as service isolation and network segmentation could also reduce the damage caused by a successful attack.

### My takeaway

We should not only ask:

> "How do we stop attackers from getting in?"

We should also ask:

> "What happens if they get in anyway?"

---

5. What Humans Could Have Changed

- Weak FTP credentials →	Stronger password and account controls
- FTP exposed on the network →	Remove or disable it if unnecessary
- Vulnerable vsftpd version	→ Patch, replace, or remove vulnerable software
- Known vulnerability remained exploitable	→ Regular vulnerability checks
- Root access after exploitation →	Least privilege and service isolation
- 
---

## Final Takeaway

The technical attack showed me how the system was compromised.

The human-factor analysis made me ask why the system was in a position to be compromised so easily.

For me, that is the real lesson of this investigation:

> Cybersecurity is not only about securing machines. It is about securing the relationship between people, technology, and the decisions made around them.
