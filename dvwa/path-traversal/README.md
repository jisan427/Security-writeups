

 ------------Path Traversal-------------


Operating System: Kali Linux
Web Application: DVWA (Damn Vulnerable Web Application).
Web Server: Apache
DVWA URL:http://localhost/dvwa

DVWA Security Level: 🔴 High

🎯 Vulnerability Name
Path Traversal (Directory Traversal)

🧠 Path Traversal কী?
Path Traversal vulnerability 

Application user-এর দেওয়া file path ঠিকমতো validate করে না
Attacker ../ ব্যবহার করে intended directory ছাড়িয়ে
system এর অন্য sensitive file access করতে পারে
যেমন:

/etc/passwd
application config file
source code

🔍 Lab Location (DVWA এর ভিতরে)
আমি DVWA dashboard থেকে যাই:

DVWA → File Inclusion


(High level-এ Path Traversal এই অংশের মধ্যেই test করা যায়)

এখানে একটি file parameter আছে, যেটা দিয়ে server থেকে file load হয়।

Here, we have one file parameter, which is known as এখানে, and it is the file load which comes out of server.


🔎 Normal Behaviour Test
প্রথমে normal file load করি:

file=include.php

✔️ Page ঠিকভাবে load হয়
➡️ বোঝা যায় backend user-provided file path ব্যবহার হচ্ছে.


❌ Simple Traversal Attempt (Fail -High Level)
Low / Medium level  // means এ যেটা কাজ করে, High level  // means এ সেটা try করি

../../../../etc/passwd

❌ Result:

Error message
অথবা কিছুই দেখায় না
➡️ বুঝলাম:

../ properly filter করা হয়েছে
Direct traversal block করা

🔎 Analysis (আমি কী বুঝলাম)
আমি লক্ষ্য করলাম:

Application কিছু নির্দিষ্ট string block করছে
কিন্তু পুরো path normalization সঠিকভাবে করা হয়নি
Encoding / bypass এর সুযোগ থাকতে পারে
তাই আমি encoded traversal নিয়ে test করার সিদ্ধান্ত নেই।


Successful Bypass (High Security) 1.
✔️ Payload (URL Encoding ব্যবহার করে):
..%2f..%2f..%2f..%2fetc%2fpasswd

🔥 Result:
Response Content Response এ /etc/passwd file:

root:x:0:0:root:/root:/bin/bash
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

➡️ এখানেই confirm হয়
Determinations level of high security থাকা সত্ত্বেও Path Traversal possible.




