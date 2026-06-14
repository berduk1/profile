# Cyber 02 - Portovi i osnovna mrežna provjera

## Cilj vježbe

Cilj ove vježbe bio je razumjeti što su mrežni portovi i kako se pomoću osnovnih naredbi može provjeriti mrežna komunikacija računala.

## Osnovni pojmovi

IP adresa označava uređaj u mreži.

Port označava uslugu ili aplikaciju na uređaju.

Primjer:

```text
IP adresa = gdje je uređaj
Port = koja se usluga koristi
```

Adresa s portom često izgleda ovako:

```text
IP_adresa:port
```

Primjer:

```text
142.250.x.x:443
```

To znači da se komunikacija odvija prema nekom serveru preko porta 443.

## Primjeri poznatih portova

|  Port | Usluga |
| ----: | ------ |
| 20/21 | FTP    |
|    22 | SSH    |
|    25 | SMTP   |
|    53 | DNS    |
|    80 | HTTP   |
|   110 | POP3   |
|   143 | IMAP   |
|   443 | HTTPS  |
|  3389 | RDP    |

## Korištene naredbe

U vježbi su korištene sljedeće naredbe:

```powershell
Test-NetConnection google.com -Port 443
```

```cmd
netstat -ano
```

## Test-NetConnection

Naredba `Test-NetConnection google.com -Port 443` provjerava može li računalo uspostaviti TCP vezu prema domeni `google.com` na portu 443.

Port 443 koristi se za HTTPS promet.

Ako rezultat pokaže:

```text
TcpTestSucceeded : True
```

to znači da je veza prema tom portu uspješna.

## netstat

Naredba `netstat -ano` prikazuje aktivne mrežne veze i portove.

U rezultatu se mogu vidjeti:

* lokalna adresa i port,
* udaljena adresa i port,
* stanje veze,
* PID procesa.

Primjer oblika zapisa:

```text
Local Address        Foreign Address        State
192.168.1.x:51532    142.250.x.x:443        ESTABLISHED
```

To znači da lokalno računalo koristi jedan privremeni lokalni port i komunicira s udaljenim serverom preko porta 443.

## Slika vježbe

![Portovi i netstat vježba](image/portovi-netstat.png)

## Zaključak

IP adresa pokazuje gdje se uređaj nalazi u mreži.

Port pokazuje koja se usluga ili aplikacija koristi na tom uređaju.

Port 443 koristi se za HTTPS promet, port 53 za DNS, port 80 za HTTP, a port 22 za SSH.

Naredba `Test-NetConnection` može provjeriti je li određeni port dostupan.

Naredba `netstat` prikazuje aktivne mrežne veze i pomaže razumjeti kako računalo komunicira s drugim uređajima i serverima.

Ova vježba je osnovni uvod u razumijevanje portova, što je važno za kasniji rad s alatima kao što su Wireshark, Nmap i sigurnosni alati za mrežnu analizu.

