# My Methodology

## The Idea Behind the Investigation

This project is not actually about finding technical vulnerabilities.

I wanted to understand how human decisions and security practices can create opportunities for a technical attack.

So I followed the attack from the first thing anyone could see and tried to find out the path to compromise.

## My Investigation Process

### 1. Find the Target

First, I identified the vulnerable machine on my lab network.

I needed to know exactly which machine I was investigating before doing anything else by confirming the IP address of the machine I would be attacking.

### 2. See What Is Exposed

Next, I scanned the machine to find open ports and the services running on them.

This helped me answer:

> What can an attacker see on the machine?

### 3. Look Closer at Interesting Services

When I found an interesting service, I investigated it further.

I checked what software and version were running and researched whether that version had known security vulnerabilities I could exploit.

### 4. Look at Authentication

I then looked at how users could access the exposed services.

This was important because a system can have strong software but still be exposed if people use weak passwords or poor account practices.

Apparently, the service used weak and very common passwords— I found out using brute-force.

So the weakness would actually give an attacker access.

### 5. Check What Access Means

After gaining access, I checked what level of privilege I had.

I wanted to understand whether the weakness only gave limited access or could lead to full control of the system.

### 6. Test the Impact

I then safely tested what could be done with the access I obtained.

I focused on whether an attacker could:

- Access information
- Change information
- Gain higher privileges

### 8. Focus on the Human Factor

Finally, I asked the question that makes this project different:

> What could humans have done differently?

For each major weakness, I looked at the human decision, security practice, or organizational process that may have allowed the weakness to exist.

For example:

**Weak password**

→ What security practice allowed it or were the useers not properly informed?

**Vulnerable software**

→ Why was the software not updated or removed, is this a delibrate insider threat, does the 'organization' even pay attention to their outdated software at all?

This allowed me to look at cybersecurity as more than a technical problem.

It allowed me to examine the relationship between **people, technology, and security.**
