---
layout: page
title: Tilfeldige tall
---
På kursdag 1 fikk vi ikke tid til å vise dere noe om tilfeldige tall. I dagens læreplaner er det spesielt i matematikkens sannsynlighetsregning at vi får vi bruk for dette. Tilfeldige bevegelser og utvalg har generelt blitt oppfattet som for krevende å regne på i andre fagområder på skolenivå. Men kanskje dette kan endre seg når vi får inn mer programmering i fagene. Tenk på diffusjon, radioaktivitet og smittespredning. Programmering med tilfeldige tall og statistisk analyse kan åpne en ny verden av motiverende og virkelighetsnære problemstillinger.

## Tre kommandoer: randint  uniform  shuffle

>randint : velger tilfeldige heltall  
uniform: velger tilfeldige flyttall/desimaltall   
shuffle: blander elementene i en liste eller array tilfeldig

Vi prøver å bruke disse tre kommandoene: 


```python
from pylab import *
tilfeldigetall1 = randint(0,10) #velger ett tilfeldig heltall mellom 0 og 10
print(tilfeldigetall1)

tilfeldigetall2 = uniform(0,10) #velger ett tilfeldig flyttall mellom 0 og 10
print(tilfeldigetall2)

tilfeldigetall3 = randint(0, 100, 10) #velger 10 tilfeldige heltall mellom 0 og 100
print(tilfeldigetall3)

tilfeldigetall4 = uniform(0, 100, 10) #velger 10 tilfeldige flyttall mellom 0 og 100
print(tilfeldigetall4)

liste_med_dyr = ["hest", "ku", "bjørn", "ørret", "rev"]
shuffle(liste_med_dyr)
print(liste_med_dyr)

```

## Oppgave
1) Under ser du et lite program. Forklar linje for linje hva dette programmet gjør. 


```python
svar=42
tall=0
forsøk=0
while svar != tall:
    tall=int(input("Hvilket tall mellom 0 og 100 tenker jeg på? "))
    forsøk+=1
    if tall>svar:
        print ("Tallet skal være mindre, prøv igjen \n")
    elif tall<svar:
        print("Tallet skal være større, prøv igjen \n")
print("\n Det er rett! Hurra! Du brukte:", forsøk, "forsøk \n")

```

2) Endre dette programmet så det tar et tilfeldig tall som svar. Hvor mange forsøk brukte du på å gjette tallet?

## Kaste terning
Nå lager vi et program som kaster terning. 
Forklar hva hver linje i programmet gjør. Hvorfor kan det være lurt å bruke en funksjon her?



```python
from pylab import *
def terningkast():    
    return randint(1,7)

print(terningkast())
```

Hvis du ser på s. 104 i ProMod-boka, finner du et program om relativ frekvens og sannsynlighet. Lag dette programmet og gjør underveisoppgave 6.2 nederst på siden. 



# Oppgaver
1. Lag plottet på s. 103
2. Lag et program som trekker et tilfeldig navn fra en liste (for eksempel en klasseliste)

## Oppgaver fra ProMod - innøving
```
6.1  
6.4  
6.5  
6.7 
```

## Oppgaver fra ProMod - knyttet til fagene
```
6.9  
6.10  
6.11  
6.12  
6.13  
```


## Fordypningsmateriale: Terningkast og fordelinger

Hvor mange ganger må vi kaste en terning for å få en sekser? Vel, det kan vi jo regne på, men vi kan også trekke tilfeldige tall for å gjøre et veldig godt estimat. 


```python
from pylab import *

antallOyne = 0
antallKast = 0
while antallOyne != 6:
    antallOyne = randint(1, 7)
    antallKast += 1
print("Fikk en sekser etter %d kast" % antallKast)
```

Antallet kast vi trenger er tilfeldig. Det vet vi fra yatsy. Men på hvilken måte er det tilfeldig? La oss så simulere fordelingen av antall kast vi trenger for å kaste en sekser. 


```python
from pylab import *

N = 1000
antallKastVektor = zeros(N)
for forsok in range(N):
    antallOyne = 0
    antallKast = 0
    while antallOyne != 6:
        antallOyne = randint(1, 7)
        antallKast += 1
    antallKastVektor[forsok] = antallKast
hist(antallKastVektor, bins=int(max(antallKastVektor)-1), align='left')
xlabel("Antall kast for å få en sekser")
ylabel("Frekvens")
show()
```

Nå kan vi tenke litt på hva det er som skjer her. Det vanligste er å få sekseren på ett kast. Hvorfor det? Hvilken fordeling følger antallet kast man trenger for å få en sekser? (Hint: Argumentere ut ifra valgtre. Hvilke sannsynligheter eksisterer for det førsre kastet, andre kastet osv.)

Videre kan vi se på antallet seksere vi får dersom vi kaster mange ganger. Altså, ikke hvor mange ganger vi må kaste for å få en sekser, men hvor mange seksere vi får om vi kaster et gitt antall ganger. (Programmet under kan bli tregt dersom `M*N` blir for stor. Da kan du bruker Kernel -> Interrupt i menyen på toppen for å avbryte)


```python
from pylab import *

N = 10000 # Antall forsøk
M = 10 # Antall terningkast per forsøk

antallSeksereVektor = zeros(N)
for forsok in range(N):
    antallSeksere = 0
    for kast in randint(1, 7, M):
        if kast == 6:
            antallSeksere += 1
    antallSeksereVektor[forsok] = antallSeksere
hist(antallSeksereVektor, bins=int(max(antallSeksereVektor)-1), align='left')
xlabel('Antall seksere av %d kast' % M)
ylabel('Frekvens')
show()

```

Her kan vi eksperimentere med å endre på antallet terningkast per forsøk og antallet forsøk. Hvilken fordeling er det vi i trekker fra i dette numeriske eksperimentet? Hva skjer med denne fordelingen når M blir stor?

## PS

I `numpy.random`-modulen finnes det mye mer enn det vi har vist fram her. Spesielt så lar den deg trekke tilfeldige tall fra en hel rekke sannsynlighetsfordelinger. Du kan lese mer om dette i [dokumentasjonen](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.random.html).
