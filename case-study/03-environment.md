# Environment

## Laboratory Setup

This investigation was conducted in an isolated virtual laboratory environment designed for cybersecurity practice and authorized testing.

The environment consisted of two virtual machines:

| System | Role | IP Address |
|---|---|---|
| Kali Linux | Investigation machine | 10.0.2.15 |
| Metasploitable 2 | Intentionally vulnerable target | 10.0.2.3 |

## Investigation Machine

### Kali Linux

Kali Linux was used as the investigation machine.

It provided the tools used for:

- Network discovery
- Port scanning
- Service enumeration
- Vulnerability research
- Controlled security testing

## Target Machine

### Metasploitable 2

Metasploitable 2 was used as the target system.

It is an intentionally vulnerable virtual machine designed for security training and controlled penetration-testing practice.

The system was selected because it provides a controlled environment in which exposed services and known security weaknesses can be investigated without targeting real-world systems.

## Network Configuration

The two virtual machines communicated through the laboratory's virtual network.

```text
┌─────────────────────┐
│     Kali Linux      │
│  Investigation VM   │
│     10.0.2.15       │
└──────────┬──────────┘
           │
           │ Virtual Network
           │
┌──────────▼──────────┐
│   Metasploitable 2  │
│      Target VM      │
│     10.0.2.3        │
└─────────────────────┘
