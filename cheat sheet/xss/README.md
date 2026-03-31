---nuclei---
#basic scan
nuclei -u https://target.com
#template scan
nuclei -u https://target.com -t nuclei-templates/
#severity
nuclei -u https://target.com -severity high,critical
#sql
nuclei -u https://target.com -tags sqli
#xss
nuclei -l live.txt -tags xss -o xss.txt
#cve
nuclei -u https://target.com -t cves/
#sencitive file check
nuclei -u https://target.com -t exposures/
#safe scan
nuclei -u https://target.com -c 50 -rate-limit 20
#debug & verbos
nuclei -u https://target.com -v
nuclei -u https://target.com -debug
#proxy
nuclei -u https://target.com -proxy http://127.0.0.1:8080
#advance
subfinder -d target.com | httpx | nuclei -severity medium,high,critical