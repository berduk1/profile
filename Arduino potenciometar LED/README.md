Logika programa
1. Analogni ulaz
int sensorValue = analogRead(potPin);

Arduino čita napon na A0.

ADC pretvara napon u vrijednost:

0–1023

Vrijednost se sprema u:

sensorValue

2. Serial Monitor
Serial.begin(9600);

Pokreće serijsku komunikaciju između Arduina i računala.

Serial.println(sensorValue);

Šalje trenutno očitanje u Serial Monitor.

To omogućuje praćenje promjene vrijednosti potenciometra.

3. Threshold

Koristimo prag:

500

if (sensorValue < 500)

Ako je očitanje manje od 500:

LED = ON

Ako nije:

LED = OFF

if / else
if (condition) {
    action;
} else {
    otherAction;
}

U ovom projektu:

sensorValue < 500 ?
        |
   +----+----+
   |         |
  YES        NO
   |         |
 LED ON    LED OFF
Tok sustava

Potenciometar
↓
promjenjivi napon
↓
A0
↓
analogRead()
↓
0–1023
↓
if / else
↓
D8
↓
LED ON / OFF

Što potenciometar predstavlja?

U ovoj vježbi potenciometar glumi analogni senzor.

Mi ručno mijenjamo ulazni signal.

Kasnije se potenciometar može zamijeniti stvarnim senzorom, npr.:

LDR
temperaturnim senzorom
senzorom vlage
drugim analognim senzorom

Programska logika ostaje vrlo slična.

Ključni pojmovi
analogRead()

Čita analogni ulaz i vraća vrijednost 0–1023.

if

Izvršava naredbu ako je uvjet zadovoljen.

else

Izvršava alternativnu naredbu ako uvjet nije zadovoljen.

threshold

Granična vrijednost prema kojoj program donosi odluku.

Serial.begin(9600)

Pokreće serijsku komunikaciju na 9600 baud.

Serial.println()

Šalje podatak računalu / Serial Monitoru.

Što sam praktično napravio
ponovno sam samostalno složio velik dio breadboard spojeva
potenciometrom sam generirao analogni signal
Arduino je očitao signal na A0
program je usporedio očitanje s pragom
LED se uključivala i isključivala ovisno o položaju potenciometra
Glavna ideja

Ova vježba predstavlja osnovni princip automatiziranog sustava:

SENSOR / INPUT
→ MEASUREMENT
→ DECISION
→ OUTPUT / ACTUATOR
