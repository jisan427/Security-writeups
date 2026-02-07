-----information gathering----
  --tool--
nikto -host url
whatweb url
whois url

  ----url base---
subdomain -d domain.com /usr/share/wordlist/folder -t 10>sub.text
cat sub.txt | httpx -status-code>200.txt
ffuf -u url/FUZZ -w /usr/share/seclists/folder -t 10>ffuf.txt
cat ffuf.txt | httpx -status-code>f200.txt
cat domain-folder | waybackurls >wayback.txt
paramspider -d domain.com

cat wayback.txt  | httpx -status-code >w200.txt
nuclei -url

-------webiste------
dnsview
dnsdumb
lopseg

----zonetransfer----
   dig -t ns/mx/other zonetransfer.me/domain
   dig asfr zonetransfer.me/domain @ns-server
   host -t ns/mx/AA/AAAA zonetransfer.me/domain
   host -l zonetransfer.me/domain ns-server
   nsloolup

   ----commandline----   
nmap -sV sC -Pn -n -p-
sudo enum4linux -a ip
netdiscover
smbclient -L ////ip//
msfconsole