
Intruder 

Burp Suite Intruder Burp Suite Intruder একটি automated attack tool.
``` azedano 1.3 request 1.3 request 1.3 response observe ke 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3 change request 1.3

আমি সাধারণত Intruder ব্যবহার করি তখন
যখন manual repeater দিয়ে test করা সময়সাপেক্ষ হয়ে যায়

Repeated parameter testing এর জন্য
Bruteforce type scenario check করার জন্য.
IDOR parameter sequential কিনা বুঝতে
Rate limit বা input validation আছে কিনা দেখতে

Proxy থেকে request select থেকে request select করি.
Right click করে Send to Intruder দেই
Intruder tab এ গিয়ে Positions সেট করি

সব parameter বাদ দিয়ে
যেটা test করবো সেটাতে position রেখে দেই

Payload configuration

Payload section এ গিয়ে
Simple list বা Numbers ব্যবহার করি

ধরো id parameter হলে
1 থেকে 50 পর্যন্ত sequence দেই

Attack start করার পর
Response length
Status code
Content difference observe করি

Example

Original request ছিল
profile?id=1

Intruder দিয়ে payload সেট করলাম
id parameter এ 1 থেকে 20

Response observe করে দেখি
কিছু id তে আলাদা data আসছে

এটা clear indication দেয়
Access control ঠিকমতো implement করা হয়নি

observation

সব request 200 status দিচ্ছে
কিন্তু response size আলাদা
মানে data leak হচ্ছে

Fast with intruder manual testing কে fast.
আমি সব সময় Intruder result
Repeater দিয়ে manually verify করি
Real vulnerability বুঝতে
Automation এর সাথে manual logic দরকার


✍️ Written By
JISAN 
Cybersecurity Learner | Junior Penetration Tester.
Bangladesh 🇧🇩

