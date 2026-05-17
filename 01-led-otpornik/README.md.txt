# LED/dioda + otpornik u Falstadu

## Cilj

Nauciti kako spojiti LED/diodu i zastititi je otpornikom.

## Komponente

- LED/dioda
- otpornik 220 ohma
- izvor 5 V
- spojne zice

## Spoj

```text
+5 V -> otpornik 220 ohma -> LED/dioda -> 0 V / ground

## Izračun

U_izvor = 5 V
U_dioda = 0,7 V
R = 220 ohma

U_otpornik = 5 V - 0,7 V = 4,3 V
I = 4,3 V / 220 ohma = 0,0195 A = 19,5 mA

U_izvor = 5 V
U_LED = oko 2 V
R = 220 ohma

U_otpornik = 5 V - 2 V = 3 V
I = 3 V / 220 ohma = 0,0136 A = 13,6 mA

## Kako radi

Struja prolazi kroz otpornik koji ogranicava struju i stiti LED/diodu.

U serijskom spoju struja je ista kroz sve elemente. Napon se dijeli po elementima. Otpornik ogranicava struju.

## Sto sam naucio

Krug mora biti zatvoren.
Mora postojati razlika potencijala, npr. +5 V prema 0 V.
Otpornik ogranicava struju.
LED/dioda se ne spaja direktno na izvor bez otpornika.

## Slika simulacije 
![LED/dioda + otpornik u Falstadu](slike/led-otpornik-falstad.png.png) 
