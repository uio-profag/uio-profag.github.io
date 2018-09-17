---
layout: page
title: Programmering styrker fagene
---
## Introduksjon

Det er tre hovedaspekter ved hvordan programmering kan styrke realfagene.

- Mengdetrening.
- Utdyping.
- Utviding.

### Mengdetrening
Mengdetrening går ut på at elevene møter samme formel, sammenheng eller konsept i flere sammenhenger. For eksempel kan de programmere formler fra fysikk, kjemi og matematikk slik at de kanskje lettere forstår og husker disse formlene. Programmet nedenfor er et eksempel på hvordan elevene kan lage en funksjon som regner ut pH i en løsning.


```python
from pylab import *

def kons_til_pH(konsentrasjon):
    pH = -log10(konsentrasjon)
    return pH

konsentrasjon = float(input("Hva er konsentrasjonen til oksoniumioner? "))

print("pH-en i en løsning der konsentrasjonen av H+ er:", konsentrasjon,
      "mol/l er:", kons_til_pH(konsentrasjon))
```

    Hva er konsentrasjonen til oksoniumioner? 1e-7
    pH-en i en løsning der konsentrasjonen av H+ er: 1e-07 mol/l er: 7.0


Et annet eksempel er å programmere en bevegelseslikning fra fysikk:


```python
def s(v,v_0, t):
    return 0.5*(v + v_0)*t

print(s(10,2,5))
```

    30.0


Eleven får også mengdetrening i algebra når de skal omforme formler og likninger slik at de kan programmeres og brukes som funksjoner. 

### Utdyping
Når en først har lagd programmene, kan en i tillegg eksperimentere med formler og likninger lettere enn om en hadde måttet regne mye hver gang. Dette gjør at elevene lettere kan tolke, både kvalitativt og kvantitativt, ulike fenomener og sammenhenger. Et eksempel på dette, er hvordan de kan utforske Bohrs formel for energinivåene i hydrogenatomet uten å få masse kalkulatorfeil og andre regnefeil hver gang de tester et nytt energinivå (det er ikke alltid lett å få så små tall som Plancks og Bohrs konstant til å bli riktig på kalkulatoren!).


```python
# Konstanter
B = 2.18E-18
h = 6.636E-34
c = 3e8

#Energinivåer
n = int(input("Skriv inn en verdi for n:")) #skallet det eksiteres fra
m = int(input("Skriv inn en verdi for m:")) #skallet det eksiteres til

#Bohrs formel
def Bohr(n,m):
    f = B/h *(1/ m**2 - 1/n **2)
    bl = c/f            # bølgelengde i meter
    bl_nm = bl*1E9      # bølgelengde i nanometer
    return bl_nm

print("Bølgelengden til fotonet fra n =",n,"til m =",m,"er: %.0f" % Bohr(n,m),"nm") 
```

    Skriv inn en verdi for n:6
    Skriv inn en verdi for m:3
    Bølgelengden til fotonet fra n = 6 til m = 3 er: 1096 nm


Dette programmet kan også utvides slik at en går igjennom alle energinivåer det er mulig å deeksitere til.


```python
#Konstanter
B = 2.18E-18
h = 6.636E-34
c = 3e8

#Energinivå elektronet skal deeksitere fra
n = int(input("Skriv inn en verdi for n:"))

#Bohrs formel
def Bohr(n,m):
    f = B/h *(1/ m**2 - 1/n **2)
    bl = c/f            # bølgelengde i meter
    bl_nm = bl*1E9      # bølgelengde i nanometer
    return bl_nm

for m in range(n-1 ,0,-1):
    print("Bølgelengden til fotonet fra n =",n,"til m =",m,": %.0f" % Bohr(n,m),"nm")
```

    Skriv inn en verdi for n:6
    Bølgelengden til fotonet fra n = 6 til m = 5 : 7472 nm
    Bølgelengden til fotonet fra n = 6 til m = 4 : 2630 nm
    Bølgelengden til fotonet fra n = 6 til m = 3 : 1096 nm
    Bølgelengden til fotonet fra n = 6 til m = 2 : 411 nm
    Bølgelengden til fotonet fra n = 6 til m = 1 : 94 nm


### Utdviding
I programmering og modellering kan vi utvide realfagene ved å bruke og studere formler vi ikke møter i de øvrige realfagene. Dette kan gi en dypere og bedre forståelse av flere sider ved de naturvitenskapelige fagene. I tillegg kan både lærere og elever i større grad styre hva de vil undersøke nærmere, og dette kan være svært motiverende! Sammenhenger og likheter mellom de naturvitenskapelige fagene kan også komme lettere fram når en bruker samme verktøy til å studere fenomener fra ulike fagfelt som fysikk, biologi og kjemi.

I tillegg kan vi gjøre en del ting vi tidligere ikke kunne, som å løse analytisk uløselige likninger, studere statistiske, tilfeldige fenomener (slik som diffusjon) eller lese av og behandle store mengder data. Eksempelet nedenfor leser av en datafil som inneholder energinivåene til hydrogenatomet gitt i elektronvolt. Det samme kan en da i praksis gjøre for alle atomer og molekyler, og da trenger en ikke lenger være prisgitt at det finnes en formel for det en ønsker å finne ut!


```python
# Brukerparametre
filename = "levels.dat"     # Datafil med energinivåer
n = 2                       # Skallet det deeksiteres fra
m = 1                       # Skallet det deeksiteres til

def read_file(filename):
    file = open(filename, "r")
    levels = []
    for line in file:
        level = line.split()
        if level[0].isdigit():  # Er elementet tall eller har det bokstaver i seg?
            levels.append((level[0], level[1]))
    return levels

def energy_level(filename, n, m):
    global energy
    levels = read_file(filename)
    energy = float(levels[n-1][1]) - float(levels[m-1][1])  # Energi til skall n minus energi til skall m
    return energy

energy_level(filename, n,m)

print("Energien til fotonet som emitteres når et elektron deeksiterer fra skall", n,
      "til skall", m, "er:", energy, "eV.")
```

Fila programmet leser av, kan du finne [her](https://akershusfk-my.sharepoint.com/:f:/g/personal/haan1709_akershus-fk_no/EmQFyczni-lFqM6GWu5sAkIBOkKEuYtS08JUrlcPLWx2xg). Det er derimot ikke alltid like lett å bruke slike filer direkte fra nettet. Noen ganger må en gjøre litt innsats i å rydde opp i fila slik at den blir grei å lese for et program.
