
🚀 FFUF Tool 


🧠 FFUF হলো একটি fast web fuzzer,

Hidden directory / file খুঁজতে
Parameter discovery করতে
Subdomain brute-force করতে
Web application enumeration করতে
👉 Pentesting আর bug bounty তে এটা খুব জনপ্রিয় tool।


🎯 কেন FFUF ব্যবহার করা হয়?
Web application-এ অনেক সময়:

Hidden admin panel
Backup file
Unlisted API endpoint
থাকে যেগুলো UI দিয়ে দেখা যায় না।

FFUF এই hidden resource গুলো খুঁজে বের করতে সাহায্য করে।


🔍 Basic Directory Bruteforce (আমার প্রথম টেস্ট)
আমি একটি website-এর hidden directory খোঁজার জন্য:

ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -t 20

✔️ Output উদাহরণ:
admin [Status: 200]
uploads [Status: 301]
backup [Status: 403]

➡️ এখানে আমি বুঝি কিছু hidden path আছে। hidden path গুলো এখানে লুকানো।


🔎 Status Code Filter করা
আমি শুধু 200 status code দেখতে চাইলে:

ffuf -u http://example.com/FUZZ -w wordlist.txt -mc 200

➡️ Noise কমে যায়।


📂 File Extension Bruteforce
PHP file খোঁজার জন্য:

ffuf -u http://example.com/FUZZ -w wordlist.txt -e .php,.txt,.bak

➡️ Backup বা sensitive file পাওয়া যেতে পারে।


🔍 Parameter Discovery
আমি parameter খুঁজতে ব্যবহার করি:

ffuf -u http://example.com/index.php?FUZZ=test -w params.txt

➡️ Hidden GET parameter detect করা যায়।


🌐 Subdomain Bruteforce
ffuf -u http://FUZZ.example.com -w subdomains.txt

➡️ Unknown subdomain পাওয়া যায়।

