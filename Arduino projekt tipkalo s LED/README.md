# Arduino projekt 03: Upravljanje LED-icom pomoću tipkala

## Opis projekta

U ovom projektu Arduino Uno očitava stanje tipkala i na temelju tog ulaznog signala upravlja vanjskom LED-icom.

Kada je tipkalo pritisnuto, LED-ica se uključuje. Kada je tipkalo otpušteno, LED-ica se isključuje.

Za tipkalo se koristi način `INPUT_PULLUP`, kojim se aktivira unutarnji pull-up otpornik mikrokontrolera. Zbog toga za stabiliziranje ulaznog pina nije potreban dodatni vanjski otpornik.

## Ciljevi projekta

* upoznati rad s digitalnim ulazom
* spojiti tipkalo na Arduino Uno
* očitati stanje tipkala funkcijom `digitalRead()`
* koristiti način `INPUT_PULLUP`
* upravljati digitalnim izlazom na temelju ulaznog signala
* koristiti programske uvjete `if` i `else`
* razumjeti obrnuto logičko ponašanje pull-up spoja

## Potrebne komponente

* Arduino Uno
* breadboard
* jedna LED-ica
* jedan otpornik od 220 Ω ili 330 Ω
* jedno tipkalo
* Dupont žice
* USB kabel

## Korišteni pinovi

| Arduino pin | Namjena                    |
| ----------- | -------------------------- |
| D8          | digitalni izlaz za LED-icu |
| D2          | digitalni ulaz za tipkalo  |
| GND         | zajednička masa sklopa     |

## Spoj LED-ice

```text
Arduino D8
    │
otpornik 220 Ω ili 330 Ω
    │
anoda LED-ice
    │
LED-ica
    │
katoda LED-ice
    │
Arduino GND
```

Duža nožica LED-ice predstavlja anodu, dok kraća nožica predstavlja katodu.

Otpornik ograničava struju kroz LED-icu i štiti LED-icu i digitalni izlaz Arduina.

## Spoj tipkala

```text
Arduino D2
    │
tipkalo
    │
Arduino GND
```

Tipkalo je postavljeno preko središnjeg kanala breadboarda. D2 i GND spojeni su na suprotne kontakte tipkala.

Tipkalo se ne spaja na 5 V jer se koristi unutarnji pull-up otpornik.

## Programski kod

Datoteka: `tipkalo_led.ino`

```cpp
const int LED_PIN = 8;
const int BUTTON_PIN = 2;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  int stanjeTipkala = digitalRead(BUTTON_PIN);

  if (stanjeTipkala == LOW) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}
```

## Objašnjenje programa

Konstante:

```cpp
const int LED_PIN = 8;
const int BUTTON_PIN = 2;
```

određuju da je LED-ica spojena na pin D8, a tipkalo na pin D2.

U funkciji `setup()` pin D8 postavlja se kao izlaz:

```cpp
pinMode(LED_PIN, OUTPUT);
```

Pin D2 postavlja se kao ulaz s uključenim unutarnjim pull-up otpornikom:

```cpp
pinMode(BUTTON_PIN, INPUT_PULLUP);
```

U funkciji `loop()` Arduino očitava trenutačno stanje tipkala:

```cpp
int stanjeTipkala = digitalRead(BUTTON_PIN);
```

Ako je očitano stanje `LOW`, tipkalo je pritisnuto i LED-ica se uključuje:

```cpp
if (stanjeTipkala == LOW) {
  digitalWrite(LED_PIN, HIGH);
}
```

Ako tipkalo nije pritisnuto, očitano stanje je `HIGH` i LED-ica se isključuje:

```cpp
else {
  digitalWrite(LED_PIN, LOW);
}
```

## Logika načina INPUT_PULLUP

| Stanje tipkala  | Stanje pina D2 | LED-ica  |
| --------------- | -------------- | -------- |
| nije pritisnuto | `HIGH`         | ugašena  |
| pritisnuto      | `LOW`          | upaljena |

Logika je obrnuta zato što pritisnuto tipkalo povezuje ulazni pin D2 s GND-om.

## Rezultat

Nakon učitavanja programa LED-ica je ugašena. Pritiskom tipkala LED-ica se uključuje, a nakon otpuštanja ponovno se gasi.

Reakcija se događa gotovo trenutačno jer Arduino neprekidno očitava stanje digitalnog ulaza.

## Provjera rada

Projekt ispravno radi ako:

* LED-ica ne svijetli kada tipkalo nije pritisnuto
* LED-ica svijetli dok je tipkalo pritisnuto
* LED-ica se gasi nakon otpuštanja tipkala
* ulazni pin ne mijenja stanje nasumično
* program se uspješno kompajlira i učitava

## Najčešće pogreške

### LED-ica uopće ne svijetli

Potrebno je provjeriti:

* polaritet LED-ice
* spoj između pina D8 i otpornika
* spoj katode LED-ice s GND-om
* je li upotrijebljen odgovarajući pin u programu
* je li program uspješno učitan

### LED-ica stalno svijetli

Mogući uzroci:

* pin D2 stalno je povezan s GND-om
* tipkalo je pogrešno okrenuto
* korišteni su pogrešni kontakti tipkala

### Tipkalo nema učinka

Potrebno je provjeriti:

* je li tipkalo postavljeno preko središnjeg kanala breadboarda
* jesu li D2 i GND spojeni na suprotne kontakte
* koristi li program pin D2
* je li postavljen način `INPUT_PULLUP`

## Što sam naučio

U ovom projektu naučio sam:

* razlikovati digitalni ulaz i digitalni izlaz
* pravilno postaviti tipkalo na breadboard
* koristiti funkciju `digitalRead()`
* koristiti unutarnji pull-up otpornik
* razumjeti stanja `HIGH` i `LOW`
* koristiti uvjete `if` i `else`
* upravljati izlazom na temelju ulaznog signala
* objasniti put struje kroz LED granu

## Moguće nadogradnje

* uključivanje i isključivanje LED-ice svakim novim pritiskom
* uklanjanje titranja kontakata tipkala, odnosno debounce
* brojanje pritisaka tipkala
* prikaz stanja u Serial Monitoru
* upravljanje dvjema LED-icama
* izrada pješačkog semafora
* dodavanje buzzera

## Fotografija projekta

Fotografiju sklopa spremiti u:

```text
images/tipkalo_led.jpg
```

U README datoteku dodati:

```markdown
![Arduino projekt s tipkalom i LED-icom](images/tipkalo_led.jpg)
```

