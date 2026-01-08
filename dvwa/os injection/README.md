
--------------OS Command Injection------------

OS: Kali Linux
Web Application: DVWA
Web Server: Apache
DVWA URL:http://localhost/dvwa

Security Level: 🔴 High

🎯 Vulnerability Name
OS Command Injection 

🔍 Lab Location
DVWA → Command Injection

এখানে একটি input box আছে
যেখানে IP address দিয়ে Ping command run করা হয়।


🔎 Normal Behaviour Test
প্রথমে normal input দেই:

127.0.0.1

✔️ Ping result আসে
➡️ বোঝা যায় backend এখনো OS command ব্যবহার করছে


Injection attempts whooping (High level) Failed examples
আমি আগে Low level payload try করি:

127.0.0.1; whoami

❌ কাজ করে না
➡️ Output আসে না / error message দেয়

তারপর চেষ্টা করি:

127.0.0.1 && whoami


❌  block হয়ে যায়

➡️ এখানেই বোঝা যায়
Input filtering- High security level চালু আছে.


🔎 Bypass Strategy (আমি কীভাবে ভাবলাম)
আমি বুঝলাম:

Direct shell operator block
কিন্তু application এখনো ping command ব্যবহার করছে
IPv4 validation ঠিকভাবে করা হয়নি
That is why I injection bypass / logical bypass newline য়ে ভাবি।


Injection (Bypass) Successfully inserted
✔️ Payload:
127.0.0.1
whoami

(একই input field এ newline ব্যবহার করে)

🔥 Result:
Ping output এর নিচে আমি পাই:

www-data

➡️ এখানে প্রমাণ হয়
newline properly sanitize করা হয়নি


🔓 Further Exploitation
✔️ System info বের করা
Payload:

127.0.0.1
uname -a

➡️ Server kernel information পাওয়া যায়


✔️ Sensitive file read
Payload:

127.0.0.1
cat /etc/passwd

🔥 Output এ /etc/passwd file content দেখা যায়

➡️ OS command execution sambhavier High security level হলেও.


🧠 Vulnerability কেন রয়ে গেছে?
যদিও security level High ছিল, তবুও:

Input validation incomplete
Newline (\n) properly filter করা হয়নি
OS command ব্যবহার করা হয়েছে
Secure alternative approach ব্যবহার করা হয়নি
👉 Filter থাকলেও logic flaw থেকে গেছে।


🚨 Real-World Impact
যদি production server এ এমন bug থাকে:

🔥 Server compromise
🐚 Reverse shell নেওয়া সম্ভব
📂 Sensitive file leak
🔑 Credential exposure
High security থাকলেও 100% safe নয় — এটা এই lab থেকে শেখা যায়।


