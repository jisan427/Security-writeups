

Nikto Tool

Nikto is a web server scanning tool. Nikto is source.

* I have used Nikto. I see that Nikto does not exploit any vulnerability. I see that Nikto only detects the vulnerabilities.


🌐 আমি আমার নিজের মেশিনে localhost server ল্যাব সেটআপ করেছি ।

URL:
http://127.0.0.1

Web Server: Apache

▶️ আমি যেভাবে Nikto Scan করেছি
আমি terminal খুলে নিচের command টা চালিয়েছি:

nikto host http://127.0.0.1



host মানে target host
127.0.0.1 মানে আমার localhost

Observaion
1. Server Information Leak

Server: Apache/2.4.x

I observed the attackers performed an attack. The specific attack caused a leakage of the server version. The Hale system protected the server.


2. Missing Security Headers

 X-Frame-Options,
 X-Content-Type-Options,
 Content-Security-Policy

Clickjacking
XSS risk
MIME sniffing attack হতে পারে

3. Unnecessary / Test Files
Nikto কিছু file detect করেছে যেমন:

/phpinfo.php
/test.php

📌 এই ধরনের file থাকলে:

Server configuration leak, হয়
Attack surface বাড়ে

3. Directory Listing Enabled
/backup/
/old/

📌 Directory listing enable থাকলে:

Sensitive file leak হতে পারে

⚠️ আমার Observation অনুযায়ী Risk
Server version leak
Medium
Missing headers
Test files
Directory listing


✍️ Written By
 JISAN 
Cybersecurity Student| Junior Penetration Tester.
Bangladesh 🇧🇩
