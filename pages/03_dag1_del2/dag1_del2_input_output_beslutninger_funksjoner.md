
# Input, output, beslutninger, funksjoner
*Kursdag 1, del 2*

I denne delen skal vi bruke et eksempel som innebærer hvordan å koke et egg til å lære om konseptene input/output, beslutninger, og  funksjoner/prosedyrer.

## Input/Output

Programmer forteller oss ikke hva de gjør med mindre vi ber dem om det. Altså at vi ber om en eller annenn form for output. Den vanlige måten å fortelle noe ut fra et program er å bruke `print`-funksjonen.


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

    Skriv inn navnet ditt: Anders
    Hello Anders !
    navn har type:  <class 'str'>


Man kan også gjøre litt mer sofistikert output. Det gjøres med såkalt printf-syntaks. Det innebærer at man lager en streng der noen av tegnene inne i strengen koder for hvordan en variabel skal settes inn på det stedet i strengen. For eksempel kan manskrive `print("%d" % 4)`, eller `print("%d og %d" % (3, 4))`. Hovedfordelen med denne måten å gjøre ting på er at man kan kontrollere antallet desimaler, hvor stor plass et tall skal ta, og hvorvidt output skal komme på normalform. `"%10.4f" % variabel` ber om et flyttall som skal ta opp 10 tegn med plass, og ha 4 desimaler.


| Symbol        | Betydning    | 
    | ---  |     --- |
| %d      | heltall |
| %m.nf   | flyttall <br>som tar opp m tegn med n desimaler      |
| %m.ne    | tall på standardform <br>som tar opp m tegn med n gjeldende siffer      | 
| %m.ng    | printf velger mellom f og g      | 


```python
print("%d og %d" % (3, 4))
variabel = 230.574683646734
print("%10.4f" % variabel)
print("%8.4f" % variabel)
print("%8.2f" % variabel)
print("%8.4e" % variabel)
```

    3 og 4
      230.5747
    230.5747
      230.57
    2.3057e+02


Vi kan også lage programmet slik at det ber om at brukeren gir noe input som programmet skal bruke. I eksempelet under ber vi om at man skal gi noen inputs til programmet. Deretter ser vi hva vi kan gjøre med disse inputs'ene.


```python
lest_input = input("Skriv inn et tall (prøv både en int, en float og noe som ikke er et tall): ")
print("lest_input har verdi ", lest_input, " og type ", type(lest_input))

float_input = float(lest_input)
print("float_input har verdi ", float_input, " og type ", type(float_input))

float_casted_to_int = int(float(lest_input))
print("float_casted_to_int har verdi ", float_casted_to_int, " og type ", type(float_casted_to_int))

int_input = int(lest_input)
print("int_input har verdi ", int_input, " og type ", type(int_input))
```

    Skriv inn et tall (prøv både en int, en float og noe som ikke er et tall): 57
    lest_input har verdi  57  og type  <class 'str'>
    float_input har verdi  57.0  og type  <class 'float'>
    float_casted_to_int har verdi  57  og type  <class 'int'>
    int_input har verdi  57  og type  <class 'int'>


Eksempelet illustrerer at input-funksjonen leser inn det man gir den som en streng. Det er opp til programmereren å velge hvordan denne strengen skal tolkes. Dersom vi sender inn noe som kan tolkes som et tall, så kommer *casting*-funksjonene `int()` og `float()` til å klare å gjøre dem om til tall-datatyper. I dette tilfellet vil vi få feilmeldinger dersom vi sender inn noe som ikke fungerer med casting-operatorene. `int`-funksjonen er ganske streng. Den vil kun oversette en streng til et heltall dersom det er det den ser. Men dersom man har et flyttall synes den det er greit å oversette det til et heltall. Også dersom flyttallet ikke egentlig er et heltall. I så fall tar den bare vekk desimalene. 

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

    Hvordan vil du ha egget kokt? [bløt, medium, hard]: medium
    Koketid: 7 minutter


Vi kan komplisere dette mer. Det kan utledes en formel for tiden det tar å oppnå en viss temperatur i eggeplommen: 
$$t = 0.15 \left(\frac{c}{\pi}\right)^2 \ln\left[ \frac{2(T_{vann}-T_0)}{T_{vann}-T_{plomme}}\right] $$
der $c$ er eggets omkrets i cm, $T_{vann}$ er vanntemperaturen (om vi er ekstra nøye kan vi legge inn vannets kokepunkt som funksjon av høyde over havet). Nå kan vi stille et nytt spørsmål, memlig "hvor varm vil du ha eggeplommen?". 


```python
from pylab import *
# evt. from pylab import *
plommeTemperaturInput = input("Hvor varm vil du ha eggeplommen? [celsius]: ")
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

    Hvor varm vil du ha eggeplommen? [celsius]: 72
    Du trenger å koke egget i 4.6 minutter for å oppnå en plommetemperatur på 72.0 grader, dersom det kommer rett fra kjøleskapet
    Du trenger å koke egget i 4.2 minutter for å oppnå en plommetemperatur på 72.0 grader, dersom det kommer fra romtemperatur


## Funksjoner

Merk at i koden over så valgte vi å kopiere hele den linja som regner ut tiden egget skal ligge i gryta. Det er selvfølgelig helt unødvendig, og det er foretrukket å kopiere så lite kode som mulig.
Vi velger derfor å putte dette inn i en funksjon, slik at det blir litt enklere å få oversikt. Da kan vi også anvende funksjonen flere ganger.

La oss først se litt på funksjoner som sådan, før vi lager oss en funksjon som løser eggekokingen vår.


```python
def f(x):
    return x**2

def g(x): 
    return x**3

def minFunksjon(argument):
    for i in range(10):
        argument = str(argument) + str(i)
    return argument


def settSammenOrd(arg1, arg2):
    return arg1 + " " + arg2

y = f(3)
z = g(3)
sammensattTekst = settSammenOrd("to", "ord")

print("y: ", y)
print("z: ", z)
print("minFunksjon: ", minFunksjon("Hei"))
print("sammensattTekst:", sammensattTekst)
```

    y:  9
    z:  27
    minFunksjon:  Hei0123456789
    sammensattTekst: to ord


Over har vi laget en veldig enkel funksjon. Det er rett og slett annengradsfunksjonen. `def`-ordet er det som forteller python at vi lager en funksjon. `f` er her navnet på funksjonen. Navnet kunne godt vært noe annet, for eksempel `minFunksjon`. La oss prøve å bruke den: Det fungerte fint. Vi kan bruke den igjen og igjen om vi skulle ønske det. La oss nå lage en litt mer sofistikert funksjon rent matematisk.


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

print("Du må koke egget i %.2f minutter" % tid)
print("Om du glemmer deg og venter %.2f minutter for lenge blir egget 10 grader for varmt" % (eggeTid(plommeTemperatur+10)-tid))
```

    Hvilken temperatur ønsker du i plommen? 72
    Du må koke egget i 7.22 minutter
    Om du glemmer deg og venter 1.66 minutter for lenge blir egget 10 grader for varmt


Legg merke til at her har vi brukt vanlige matematiske operasjoner som gange `*`, dele `/` og minus `-`. I tillegg har vi brukt den naturlige logaritmen `log`. Logaritmen og mange andre funksjoner slik som `sin`, `cos`, `tan`, `exp` kommer av at vi har skrevet `from pylab import *`. Da importerer python en hel masse matematisk og annen hjelp til oss. 

Som et frampek til neste økt som skal dreie seg om ploting og arrays, viser vi fram at når vi har laget en funksjon blir det også enkelt å lage plots. 


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


![png](output_20_0.png)


Plottet over viser hvor lang tid det tar å koke et egg om man ønsker en spesifikk plommetemperatur. Standardtemperatur for bløtkokt og hardkokt egg er markrt med henholdsvis grønn og rød strek.  
