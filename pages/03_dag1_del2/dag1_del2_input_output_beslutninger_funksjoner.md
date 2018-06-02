---
layout: page
title: Input, output, beslutninger, funksjoner
sidebar_link: true
---

I denne delen skal vi bruke et eksempel som innebærer hvordan å koke et egg til å lære om konseptene input/output, beslutninger, og  funksjoner/prosedyrer.

## Input/Output

Man kan skrive mye kode, men programmet kommer ikke til å fortelle noe før man ber det om det. Den vanlige måten å fortelle noe ut fra et program er å bruke `print`-funksjonen. 


```python
a = 1 + 2

print(a)

# det kan være fint å skrive ut hva man skriver ut også 
print("a: ", a)

```

    3
    a:  3



```python
navn = input("Skriv inn navnet ditt: ")
print("Hello", navn, "!")
print("navn har type: ", type(navn))
```

    Skriv inn navnet ditt: henrik
    Hello henrik !
    navn har type:  <class 'str'>


I eksempelet under ber vi om at man skal gi noen inputs til programmet. Deretter ser vi hva vi kan gjøre med disse input'ene. 


```python
lest_input = input("Skriv inn et tall (prøv både en int, en float og noe som ikke er et tall): ")
print("lest_input har verdi ", lest_input, " og type ", type(lest_input))

float_input = float(lest_input)
print("float_input har verdi ", float_input, " og type ", type(float_input))

int_input = int(lest_input)
print("int_input har verdi ", int_input, " og type ", type(int_input))
```

    Skriv inn et tall (prøv både en int, en float og noe som ikke er et tall): 54
    lest_input har verdi  54  og type  <class 'str'>
    float_input har verdi  54.0  og type  <class 'float'>
    int_input har verdi  54  og type  <class 'int'>


Eksempelet illustrerer at input-funksjonen leser inn det man gir den som en streng. Det er opp til programmereren å velge hvordan denne strengen skal tolkes. Dersom vi sender inn noe som kan tolkes som et tall, så kommer *casting*-funksjonene `int()` og `float()` til å klare å gjøre dem om til tall-datatyper. I dette tilfellet vil vi få feilmeldinger dersom vi sender inn noe som ikke fungerer med casting-operatorene. `int`-funksjonen er ganske streng. 


## Beslutninger (if-else-setninger)
La oss begynne med det enkleste. Vi har testet en del, og vet at det tar omtrent 5 min å bløtkoke et egg, 7 min å mellomkoke et egg og 9 min å hardkoke et egg. 


```python
koketype = input("Hvordan vil du ha egget kokt? [bløt, medium, hard]: ")

if koketype == "bløt":
    print("Koketid: 5 minutter")
elif koketype == "medium":
    print("Koketid: 7 minutter")
elif koketype == "hard":
    print("Koketid: 9 minutter")
else:
    print("Gjenkjenner ikke koketype: ", koketype)
    
```

Vi kan komplisere dette mer. Det kan utledes en formel for tiden det tar å oppnå en viss temperatur i eggeplommen: 
$t = 0.15 \left(\frac{c}{\pi}\right)^2 \ln\left[ \frac{2(T_{vann}-T_0)}{T_{vann}-T_{plomme}}\right]$
der $c$ er eggets omkrets i cm, $T_{vann}$ er vanntemperaturen (om vi er ekstra nøye kan vi legge inn vannets kokepunkt som funksjon av høyde over havet). Nå kan vi stille et nytt spørsmål, memlig "hvor varm vil du ha eggeplommen?". 


```python
from pylab import *
# evt. from pylab import *
plommeTemperaturInput = input("Hvor varm vil du ha eggeplommen? [celsius]: ")
t
T_vann = 100
T_0 = 4
T_plomme = float(plommeTemperaturInput)
c = 2*pi*2 # cm
t = 0.15*(c/pi)**2*log(2*(T_vann-T_0)/(T_vann-T_plomme))
print("Du trenger å koke egget i %.1f minutter for å oppnå en plommetemperatur på %.1f grader, dersom det kommer rett fra kjøleskapet" % (t, T_plomme))

T_0 = 20
t = 0.15*(c/pi)**2*log(2*(T_vann-T_0)/(T_vann-T_plomme))
print("Du trenger å koke egget i %.1f minutter for å oppnå en plommetemperatur på %.1f grader, dersom det kommer fra romtemperatur" % (t, T_plomme))
```

## Funksjoner

Merk at i koden over så valgte vi å kopiere hele den linja som regner ut tiden egget skal ligge i gryta. Det er selvfølgelig helt unødvendig, og det er foretrukket å kopiere så lite kode som mulig.
Vi velger derfor å putte dette inn i en funksjon, slik at det blir litt enklere å få oversikt. Da kan vi også anvende funksjonen flere ganger.

La oss først se litt på funksjoner som sådan, før vi lager oss en funksjon som løser eggekokingen vår.


```python
def f(x):
    return x*x

def kritt(svamp):
    return svamp + 1

def settSammenOrd(arg1, arg2):
    return arg1 + " " + arg2

y = f(3)
z = kritt(3)
sammensattTekst = settSammenOrd("to", "ord")

print("y: ", y)
print("z: ", z)
print("sammensattTekst:", sammensattTekst)
```

    y:  9
    z:  4
    sammensattTekst: to ord


Over har vi laget en veldig enkel funksjon. Det er rett og slett annengradsfunksjonen. `def`-ordet er det som forteller python at vi lager en funksjon. `f` er her navnet på funksjonen. Navnet kunne godt vært noe annet, for eksempel `kritt`. La oss prøve å bruke den: Det fungerte fint. Vi kan bruke den igjen og igjen om vi skulle ønske det. La oss nå lage en litt mer sofistikert funksjon rent matematisk.


```python
def f(x, y=0.2):
    return x*y

print(f(4))
print(f(2, 3))
```

    0.8
    6


Over har vi brukt noe som heter et *keyword argument*. Det vil si et funksjonsargument som har en standardverdi. Dette er en nyttig måte å definere argumenter som ofte bruker en standardverdi, f. eks. linjefarger i plots. En annen fin ting med keyword arguments er at de øker lesbaheten i koden. Når man gjør et funksjonskall gjør man det eksplisitt hvilke vedier som tilordnes hvilket argument. 


```python
from pylab import *

def eggeTid(T_plomme, T_vann=100, T_0 = 4, c = 2*pi*2.5):
    return 0.15*(c/pi)**2*log(2*(T_vann-T_0)/(T_vann-T_plomme))

plommeTemperatur = float(input("Hvilken temperatur ønsker du i plommen? "))
tid = eggeTid(plommeTemperatur)

print("Du må koke egget i ", tid, "minutter")
print("Om du glemmer deg og venter ", eggeTid(plommeTemperatur+10)-tid, " minutter for lenge blir egget 10 grader for varmt")
```

    Hvilken temperatur ønsker du i plommen? 54
    Du må koke egget i  5.35820240827 minutter
    Om du glemmer deg og venter  0.919209217624  minutter for lenge blir egget 10 grader for varmt


Legg merke til at her har vi brukt vanlige matematiske operasjoner som gange `*`, dele `/` og minus `-`. I tillegg har vi brukt den naturlige logaritmen `log`. Logaritmen og mange andre funksjoner slik som `sin`, `cos`, `tan`, `exp` kommer av at vi har skrevet `from pylab import *`. Da importerer python en hel masse matematisk og annen hjelp til oss. 


```python
temperaturer = linspace(0, 90, 1000)
tider = np.zeros(len(temperaturer))
for i in range(len(temperaturer)):
    tider[i] = eggeTid(temperaturer[i])


plot(temperaturer, tider)
vlines(65, min(tider), max(tider), color="g", label="Bløtkokt")
vlines(85, min(tider), max(tider), color="r", label="Hardkokt")
xlabel("Temperatur (celsius)")
ylabel("Tid (minutter)")
legend()

show()
```


![png](output_18_0.png)


## Et par ord om biblioteker

Vi har brukt kommandoen `from pylab import *`. Dette er en kommando som importerer en rekke biblioteker. Som de sier selv: 
> To make PyLab an easy to use, well packaged, well integrated, and well documented, numeric computation environment so compelling that instead of having people go to Python and discovering that it is suitable for numeric computation, they will find PyLab first and then fall in love with Python.

pylab-importen sørger for at man importerer kjerneelementene i `numpy`, `scipy` og `matplotlib`. `numpy` tilbyr matematiske operasjoner på store *arrays* (ordnede samlinger av homogene data). `scipy` tilbyr alt mulig av vitenskapelige metoder, og baserer seg i stor grad på det som er tilgjengelig i `numpy`. `matplotlib` gjør at man kan plotte. 


