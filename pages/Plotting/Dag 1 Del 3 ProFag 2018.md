
# Plotting
Hvis du fulgte ProFags installasjonsguide for Anaconda og Python, ble du bedt om å kjøre dette scriptet som gir et plot: 


```python
from pylab import *
t = linspace(0, 3, 30)
A = t**2
plot(t, A)
xlabel("tid")
ylabel("amplitude")

```

Nå skal vi legge til et print-statement så du ser hva variabelen t faktisk inneholder


```python
print(t)
```

**Oppgave** 

Endre t fra 30 til 10 punkter. Beskriv hva det gjorde med plottet ditt. 

### Didaktisk NB!
Elevene er vant til x og y. Hvis vi kaller det x og y i programmet så er det kjent, men de venner seg ikke til å tenke «friere» - at man kan bytte om på første- og andreaksen eller kalle det noe helt annet. Det kan derfor være lurt å gi variablene logiske navn og ikke være for bundet av matematisk notasjon. 
La oss prøve. Tenk f.eks. at du har data fra logging eller et eksperiment.


```python
tid = [1,2,3,4,5,6]     # Lager to lister, tid og posisjon
posisjon = [1.0, 2.4, 1.3, 0.2, 0.5, 2.0]
plot(tid,posisjon)      # Plotter tid på 1.aksen og posisjon på 2.aksen 
plot(posisjon,tid)      # Plotter posisjon på 1.aksen og tid på 2.aksen
```

Nå ser vi på hvordan vi kan endre på listen med tider. Tenk f.eks. at du egentlig målte hvert andre sekund. Vi prøver først med å ta 2*tid:


```python
nytid=2*tid
print("Tid= ", tid)
print("Nytid= ", nytid)
```

Du ser at dette ga en dobbelt så lang liste. Tanken var egentlig å lage denne listen: [2,4,6,8,10,12] 
Da må vi konvertere fra liste til vektor (array) før vi ganger med 2. 

### Programmerings NB! 
*liste* og *array* er to forskjellige datatyper. Vi kan oversette *array* til matrise eller vektor. Fordi de matematiske regneoperasjonene vi skal gjøre med *arrays* likner på vektorregning har vi valgt å kalle det vektor. I ProFag skal vi for det meste bruke vektorer og unngå lister. 



```python
nytid=array(tid)	#konverterer fra liste til vektor
nytid=2*nytid
print(nytid)
```

### Oppgaver
1) I ditt første plott lagde du variabelen t ved hjelp av kommandoen *linspace*. Lager denne kommandoen en vektor eller en liste?

2) Finn ut hvordan lage ulike vektorer ved hjelp av *zeros* og *ones*. Se f.eks. s. 80 i ProMod-boka. Hvis du vil bruke dette til å lage en vektor som er lik den som heter nytid i vårt program, trenger du kunnskap om løkker. Det kommer i neste økt, men vi gir en smakebit nedenfor. 

3) Hva skjer om du bytter ut kommandoen plot med kommandoen scatter?

4) Prøv deg med farger, linjestil og markeringer. Se eksempel under. 

#### Eksempel på plot med farger, linjestil og markeringer


```python
plot(tid,posisjon, "-.", color="cyan", marker="s")
```

#### Eksempel på bruk av løkke for å fylle en vektor med tall vi ønsker


```python
mertid=zeros(6,int)    #lager en vektor med 6 nuller
mertid[0]=2            #setter den første verdien til 2
for i in range(1,6):   #går gjennom løkken seks ganger
    mertid[i]=mertid[i-1]+2
print(mertid)
```

### Plot av sinusfunksjon
Husk at for å plotte må vi har to vektorer av samme dimensjon. 
For å plotte en sinusfunksjon trenger vi derfor å lage to vektorer. En som inneholder argumentene og en som inneholder funksjonsverdiene. Jo flere punkter vi velger i vektoren, desto glattere blir sinuskurven. 
Her velger vi å plotte sinus for en hel periode. Da trenger vi matematikkbiblioteket både for pi og for sinus. 
Les gjennom program linje for linje og forklar hva som blir gjort.


```python
from pylab import *
x= linspace(0, 2*math.pi, 100)  #vektor går fra 0 til 2pi, med 100 steg i mellom
sinus=sin(x)                    

plot(x, sinus, c="magenta")
```




    [<matplotlib.lines.Line2D at 0x8e315c0>]




![png](output_15_1.png)


### Didaktisk NB!
Elever har ikke alltid et like bevisst forhold til om vinkler gis i grader eller radianer. Det kan derfor være nyttig å vite hvoran python konverterer mellom de to. Eller du kan  gi elevene i oppgave å lage en funksjon i python som gjør denne konverteringen. 
Uansett hvilken tilnærming du velger i klassen: Her ser du hvordan du kan konvertere til radianer slik at den innebygde funksjonen *sin*  regner riktig når vinkelmålet blir gitt i grader. 



```python
from pylab import *

a = sin(math.radians(30))
print("Sinus av 30 grader =",a)

```

### Diskusjonsoppgaver
1) Det går fint an å bruke svært mye tid på å pynte på plot. Hvordan styre dette i klassen?
2) Hva er forskjellen på å plotte i Python og Geogebra? Diskuter fordeler og ulemper med å bruke disse programmene til plotting.

### Fordypningsoppgaver (sommer-moro?)
1) Lag en funksjon som plotter sinus. Funksjonen skal ta argumentene sinusplot(amplitude, k, faseforskyvning, likevektslinje, stil) 
eller skal de heller få programmet og forklare det og lage tilsvarende, men med noen andre argumenter?

2) bruk programmet fra oppgaven over og plot tre ulike sinusfunksjoner med ulik linjestil
a - i samme vindu
b - i tre vinduer som ligger ved siden av hverandre 

hint: se ProMod boka s. xxx

eller skal oppgaven være: 
Her ser du output fra et program ... (viser tre plot i samme vindu og tre plot ved siden av hverandre). De er laget ved hjelp av å definere en funksjon som tar følgende argument...

eller?

# Lese fra fil

