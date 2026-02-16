Real ip find
🔎 Shodan (generic example)
ssl.cert.subject.CN:"rapfame.app"  200

🌐 AlienVault OTX API (generic hostname)
curl -s "https://otx.alienvault.com/api/v1/indicators/hostname/EXAMPLE_DOMAIN/url_list?limit=100&page=1"

🗂️ URLScan (generic domain query)
curl -s "https://urlscan.io/api/v1/search/?q=domain:EXAMPLE_DOMAIN&size=100"

📜 Wayback CDX (generic)
curl -s "https://web.archive.org/cdx/search/cdx?url=EXAMPLE_DOMAIN&fl=original&collapse=urlkey"

🛡️ Nmap (নিজের ল্যাব IP)
nmap --script ssl-cert -p 443 YOUR_LAB_IP

🛡️ favicon hash বের করা (নিজের domain)
curl -s https://example.com/favicon.ico | md5sum

🌐 4️⃣ Censys Certificate Search

Censys

censys search services.tls.certificates.leaf_data.subject.common_name: example.com