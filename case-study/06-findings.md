# Findings

## What I Found

The investigation revealed several weaknesses that worked together to create a path from network access to full system compromise.

The most important findings were:

1. An exposed FTP service
2. Extremely weak login credentials
3. Vulnerable FTP software
4. Successful remote exploitation

---

## Finding 1 — Exposed FTP Service

### What I Found

Port 21 was open on the target machine and was running an FTP service.

The service was identified using Nmap.

```
Port: 21
Service: FTP
Version: vsftpd 2.3.4
```

## Finding 2 - Extremely Weak Credentials

### What I Found

The FTP service accepted the following:

```
Username: user
Password: user
```

<img width="770" height="335" alt="ftp password" src="https://github.com/user-attachments/assets/56a60ac9-0f99-4438-99dc-5eaec3ca2f31" />


## Finding 3 - Vulnerable FTP Software

### What I Found

The FTP service was running:

```
vsftp 2.3.4
```
Research showed that this version was associated with a known backdoor vulnerability.

<img width="789" height="344" alt="documentation4" src="https://github.com/user-attachments/assets/efd20138-f479-4a51-850e-66951ea99f64" />


## Finding 4 - Root Level Access was achieved

### What I Found

After exploiting the vulnerable FTP service, I obtained a shell on the target.

I used:
```
getuid
```
The result showed that the session had root level access.

<img width="778" height="300" alt="documentation5" src="https://github.com/user-attachments/assets/69959801-7b97-495b-96e7-b6b9bd7a29c9" />

