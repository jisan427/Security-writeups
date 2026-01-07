


Nmap Metasploit lab 

Target হিসেবে ব্যবহার করা হয়েছে
Metasploit lab machine
local IP
192.168.141.142

প্রথমে basic scan করি
target alive কিনা confirm করার জন্য

nmap -sn 192.168.141.142a

এতে দেখা যায়
host up আছে
এবং কিছু port open

Open port identification

এরপর default port scan করি

nmap -sS 192.168.141.142

Result এ দেখা যায়
21 FTP
22 SSH
23 Telnet
80 HTTP
445 SMB

Service version 

nmap -sV 192.168.141.142

OS detection

nmap -O 192.168.141.142

Aggressive scan

nmap -A 192.168.141.142

এতে
OS
service version
default scripts
সব output একসাথে পাওয়া যায়



✍️ Written By
JISAN 
Cybersecurity Learner | Junior Penetration Tester.
Bangladesh 🇧🇩

