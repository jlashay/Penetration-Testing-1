# Penetration-Testing-1



Step 1: Google Dorking

Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:

* Karl Fitzgerald


How can this information be helpful to an attacker: 

* This could cause phishing attempts. Businesses normally have public information available online about the CEO and other higher contributors in their company. 



Step 2: DNS and Domain Discovery

Enter the IP address for demo.testfire.net into Domain Dossier and answer the following questions based on the results:
Where is the company located:

* Sunnyvale, CA 94085 US


What is the NetRange IP address: 

* 65.61.137.64 - 65.61.137.127  

What is the company they use to store their infrastructure:

* Rackspace Backbone Engineering 


What is the IP address of the DNS server:

* 65.61.137.117



Step 3: Shodan

What open ports and running services did Shodan find: 

* Port 80 , 443 & 8080



Step 4: Recon-ng
Install the Recon module xssed.
Set the source to demo.testfire.net.

-![setsource](https://github.com/jlashay/Penetration-Testing-1/blob/main/PENxssed%20source4.PNG)

Run the module.

-![runmodule](https://github.com/jlashay/Penetration-Testing-1/blob/main/PENxssedrun4.PNG)

Is Altoro Mutual vulnerable to XSS:
* Yes, it shows 1 new vulnerability found. 



Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

Command for Zenmap to run a service scan against the Metasploitable machine:

* nmap -sV 192.168.0.10


Bonus command to output results into a new text file named zenmapscan.txt:

* nmap -sV -oN zenmapscan.txt 192.168.0.10

-![zenmap](https://github.com/jlashay/Penetration-Testing-1/blob/main/PENbonus%20zenmap5.PNG)


Zenmap vulnerability script command:

* nmap -T4 -F --script ftp-vsftpd-backdoor 192.168.0.10 in zenmap
In zenmap there is a command for Samba = nmap -T4 -A -v --script samba-vuln-cve-2012-1182 192.168.0.10



Once you have identified this vulnerability, answer the following questions for your client:


What is the vulnerability:

* Port 139 & 445 is open and using Samba SMB.


Why is it dangerous: 

* This is dangerous because the service running on port 139 and 445 has known vulnerabilities and has been exploited. Port 139 and 445 are used for sommunitions to other servers. NETBIOS and SMB runs on these ports which allows communication for file sharing. This could potentially result in loss of integrity with files and also become subtle to malicious codes being stored in the files. 


What mitigation strategies can you recommendations for the client to protect their server:

* They should make sure all of their services have automatic updates when new versions or security protocols are released. Consider blocking certain inbound traffic to port 445 and 139, or make rules to accept only approved connections. They can also implement MAC address filtering, and also a Virtual Private Network. 
