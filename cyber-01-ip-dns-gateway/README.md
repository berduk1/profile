# Cyber 01 - IP, DNS, Gateway i osnovne mrežne naredbe

## Cilj vježbe

Cilj ove vježbe bio je razumjeti osnovne mrežne pojmove: IP adresu, default gateway, DNS server i osnovne naredbe za provjeru mrežne povezanosti.

## Korištene naredbe

```bash
ipconfig
ping google.com
nslookup google.com
```

## Pojmovi

### IP adresa

IP adresa je adresa uređaja u mreži. Računalo koristi IP adresu kako bi moglo komunicirati s drugim uređajima.

Primjer lokalne IP adrese:

```text
192.168.1.x
```

### Default gateway

Default gateway je uređaj preko kojeg računalo izlazi iz lokalne mreže prema internetu. U kućnoj mreži to je najčešće router.

Ako računalo želi komunicirati s adresom koja nije u lokalnoj mreži, promet šalje prema gatewayu.

### DNS server

DNS server prevodi naziv domene u IP adresu.

Primjer:

```text
google.com -> IP adresa Google servera
```

U kućnoj mreži DNS server i default gateway često imaju istu lokalnu adresu jer router obavlja obje funkcije.

## Što sam vidio u vježbi

Naredba `ipconfig` prikazala je mrežne podatke računala, uključujući IPv4 adresu, default gateway i DNS server.

Naredba `ping google.com` testirala je može li računalo doći do Googleove domene.

Naredba `nslookup google.com` pokazala je koji DNS server računalo koristi i koje IP adrese pripadaju domeni `google.com`.

## Zaključak

Default gateway je izlaz iz lokalne mreže prema internetu.

DNS server prevodi nazive domena u IP adrese.

U kućnoj mreži gateway i DNS server često mogu imati istu adresu jer router radi kao gateway i kao DNS posrednik.

Ovo je osnovni prvi korak u razumijevanju mreža i kasnijeg rada s alatima kao što su Wireshark, Nmap i SIEM sustavi.

