---
layout: page
title: Løkker
sidebar_link: false
---
# Løkker og iterasjon

I dette avsnittet skal vi se nærmere på løkker og iterasjon over lister. Det finnes to typer løkker i Python, for-løkker og while-løkker. For-løkker brukes gjerne dersom man på forhånd vet hvor langt man vil iterere basert på en teller. Eksempel:


```python
for i in range(0, 10):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9


Denne løkken vil, som vi ser, telle _fra_ 0, og _til, men ikke med_ 10. I motsetning til for-løkker, vil while-løkker kjøre så lenge en tilstand er sann. For eksempel:


```python
a = ""
while(a != "xxx"):
    a = a + "x"
    print(a)
```

    x
    xx
    xxx


Som vi ser printes "x", "xx" og "xxx", men når verdien av a ikke lenger tilfredsstiller testen til løkken avsluttes programmet.

### Underveisoppgave 1 – Enkel for-løkke med liste

a) Definer en liste som inneholder følgende verdier: 6, -4, 7, -2, 8, -3, 9, -11.

b) Bruk en for-løkke til å iterere igjennom alle verdiene i listen og finn den minste verdien. Skriv ut den minste verdien. Gjør dette uten å bruke Python sin innebygde min-funksjon.

c) Bruk en ny for-løkke tilsvarende oppgave b, men finn og skriv ut den største verdien.

## Anvendelser

Løkker brukes for å gjenta en eller flere handlinger et gitt antall ganger. Enkelte funksjoner krever av natur at man benytter seg av løkker, som for eksempel en summeformel:


```python
def sumTil(x):
    verdi = 0
    for i in range(1, x+1):
        verdi = verdi + i
    return verdi

print(sumTil(5))
```

    15


I programmet over har vi skrevet en funksjon _summer(x)_ som summerer tallene fra 1 til og med x. Merk at vi i løkken sier _x+1_, ettersom _range_ gir verdiene til, men _ikke med_ den andre parameteren.

Vi kan også bruke løkker for å teste funksjoner med argumenter over et gitt spekter. Dette kan være spesielt nyttig om man ønsker å plotte tallene til en graf. For eksempel:


```python
from pylab import *

def f(x):
    return x**2

verdier = []
for i in arange(-2, 2, 0.5):
    verdier.append(f(float(i)))
    
print(verdier)
```

    [4.0, 2.25, 1.0, 0.25, 0.0, 0.25, 1.0, 2.25]


Her har vi skrevet en funksjon som beregner _f(x) = x^2_. Denne kjøres i en løkke for x mellom -2 og 2, og vi øker telleren med 0.5 for hvert steg. Merk at vi har importert _pylab_ og brukt funksjonen _arange_ i stedet for _range_. Årsaken til dette er at den innebygde _range_-funksjonen ikke er i stand til å håndtere annet enn heltall, mens vi i dette tilfellet ønsker å flytte oss kun 0.5 for hvert steg i løkken.

### Underveisoppgave 2 – Plotting av tredjegradspolynom

a) Definer en funksjon som beregner
_f(x) = 2x^3 + x^2 + 3x + 5_.

b) Skriv en løkke som tester funksjonen for x mellom -10 og 10, med steglengde på 0.5. Husk å lagre verdiene i en liste for hvert steg i løkken.

c) Plot verdiene fra beregningene til en graf.

Løkker er også nyttige om man ønsker å iterere over lister eller arrayer/vektorer. Ettersom telleren i en for-løkke kan settes til å gå fra 0 til listens lengde vha. _len_-funksjonen, kan vi løpe gjennom lister som vi ikke vet lengden av når vi programmerer, som for eksempel en liste som fylles inn av bruker i konsollen. Eksempel:


```python
tast = input("Skriv inn noe, avslutt ved å taste 0: ")
innhold = []

while tast != "0":
    innhold.append(tast)
    tast = input("Skriv mer: ")
    
print("Du tastet:")
for i in range(0, len(innhold)):
    print(innhold[i])
```

I programmet over ser vi to løkker. Den første er en while-løkke som fortsetter å kjøre inntill bruker skriver inn 0, og lagrer det bruker har tastet i en liste. Den andre løkken er en for-løkke som løper gjennom og skriver ut det brukeren har tastet. Merk at løkken er satt til å løpe fra 0 til _len(innhold)_. Sistnevnte funksjonskall returnerer størrelsen på listen.


```python

```
