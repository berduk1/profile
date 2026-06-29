# Cyber 04 – HTTP i HTTPS

## Cilj

Cilj vježbe bio je provjeriti DNS razrješavanje domene, TCP dostupnost portova 80 i 443 te pregledati HTTP i HTTPS odgovor servera.

## Korištene naredbe

```powershell
nslookup example.com
Test-NetConnection example.com -Port 80
Test-NetConnection example.com -Port 443
curl -I http://example.com
curl -I https://example.com


