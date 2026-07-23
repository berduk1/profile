# 08 – Realni izvori i transformacija izvora

## Cilj projekta

Cilj projekta bio je razumjeti realne naponske i strujne izvore te pokazati ekvivalentnost dvaju modela pomoću transformacije izvora.

U vježbi su izrađena dva Falstad kruga:

1. realni naponski izvor
2. realni strujni izvor

Oba kruga testirana su s istim opterećenjem.

---

## Teorija

Idealni naponski izvor održava zadani napon.

Realni naponski izvor može se prikazati kao idealni naponski izvor sa serijskim unutarnjim otporom.

Idealni strujni izvor održava zadanu struju.

Realni strujni izvor može se prikazati kao idealni strujni izvor s paralelnim unutarnjim otporom.

Ta dva prikaza mogu biti ekvivalentna.

---

## Transformacija izvora

Zadan je realni naponski izvor:

```text
V = 10 V
R = 2 kΩ

I = V / R

I = 10 V / 2000 Ω
I = 0.005 A
I = 5 mA

10 V izvor + 2 kΩ serijski otpor
=
5 mA izvor + 2 kΩ paralelni otpor
