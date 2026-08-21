# Security Recommendations

The recommendations below are based on the weaknesses discovered during the investigation.

The goal is not simply to fix the technical problems.

The goal is to reduce the chance of the same problems happening again.

---

## 1. Remove Unnecessary FTP Services

If FTP is not required, it should be disabled or removed.

Every exposed service creates another possible entry point for an attacker.

### If File Transfer Is Required

Use a more secure service server that protects authentication and data in transit.


## 2. Strengthen Password Practices

The discovered credentials were extremely weak.

Organizations should:

- Require strong passwords
- Prevent the use of common passwords
- Remove unused accounts
- Review accounts regularly
- Use multi-factor authentication where appropriate

## 3. Patch Vulnerable Software

The target was running a version of vsftpd associated with a known vulnerability.

Organizations should:

- Keep an inventory of software
- Regularly check for vulnerabilities
- Apply security updates promptly
- Remove software that is no longer supported
- Disable services that are no longer needed


## 4. Apply Least Privilege

Users and services should receive only the permissions they need.

This can reduce the damage caused when an account or service is compromised.

For example:

> An FTP service should not need unnecessary administrative privileges.


## 5. Monitor Exposed Services

Organizations should regularly review:

- Open ports
- Running services
- Internet-facing systems
- Unnecessary services
- Changes to network configurations

What is not needed should not remain exposed.

## 6. Make Security Responsibility Clear

Security maintenance should have clear ownership.

Someone should be responsible for knowing:

- What software is running
- Which systems need updates
- Which services are exposed
- Which accounts exist
- Which vulnerabilities need attention

Security problems are easier to ignore when nobody clearly owns them.


## 7. Design Security Around People

Technical controls should support people instead of assuming that people will never make mistakes.

Security teams should make secure behavior:

- Easy to understand
- Easy to follow
- Difficult to accidentally bypass

This can include clear policies, useful training, good defaults, and controls that reduce the impact of mistakes.

---

# Priority

| Recommendation | Priority | Reason |
|---|---|---|
| Remove unnecessary FTP | High | Reduces attack surface |
| Fix weak credentials | Critical | Prevents easy initial access |
| Patch vulnerable software | Critical | Removes known attack path |
| Apply least privilege | High | Limits damage after compromise |
| Review exposed services | High | Reduces attack surface |
| Improve security ownership | High | Helps prevent weaknesses from being ignored |
| Design security around people | High | Reduces human-related security risks |

---

# Final Recommendation

The strongest lesson from this investigation is that no single control is enough.

Security should combine:

**Secure technology**, **Good security processes** and **Human-centered controls**

The goal is not to build a system that assumes humans will never make mistakes.

The goal is to build a system that remains safer even when mistakes happen.
