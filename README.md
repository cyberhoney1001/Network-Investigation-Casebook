# Port-Investigation-Analysis

Starting this project I had only this goal- Scan a network for probable human flaws and errors and here's what I found and how I found it;

Investigation Machine: Kali Linux, 10.0.2.15
Vulnerable Machine: Metasploitable 2, 10.0.2.3

In my home lab network, I ensured my investigation machine was on the same network as the machine I am investigating. I used *bettercap* to check for all the ip adddresses in my network and ensured I had the correct IP Address of my vulnerable machine. I then pinged 10.0.2.3 to make sure the connection is strong and fast. 
I wanted to find any possible human weaknesses in the system, I was looking for weak passwords, shared accounts or misconfigured accounts. My first guess was to scan for any open ports in the machine.               #sudo nmap 10.0.2.3#        Then I found about 996 open ports, which means these ports were open for connetions and ready to recieve. Curious about what I would find on port 21, FTP- File Transfer Protocol , I decided to exxplore it. I checked which service version as running on the open port.        #sudo nmap -sV -p 21 10.0.2.3#       Found out that the service there was "vsftpd 2.3.4".
I tried to enter the open port.        #ftp 10.0.2.3#       I now need login details to enter into the system so I tried using brute-force to see whether it'd work, and it did. From Kali, I used the /usr/share/wordlists/metasploit and hydra to start the bruteforce. I found two login details that match- "service" and "user". Now I am inside the machine through the ftp port due to weak credentials like "service" and "user". *boom 1*  Used "pwd" and found I was in the home directory- not root, no privilges. I ran "ls" to list all the files in that directory and there was nothing useful to an attacker. I also wanted to test the integrity, so I tried creating a file but it was rejected. That felt like a total dead end but what else do I know about this open port? It used the vsftpd 2.3.4 service version.

I have no idea what that was so i decided to make my research. 
I searched the internet to learn about what "vsftpd 2.3.4" was and how I can exploit it. After gathering enough info especially that the machine I was investigating had a module I vcan use to e
