---
layout: page
title: Oppgaver til input, output, beslutninger og funksjoner
---

Under følger først noen oppgaver fra ProFag, deretter oppgaver fra læreboka i programmering og modellering. Om du trenger å øve, kan der være lurt å gjøre innøvingsoppgavene fra læreboka før oppgavene fra ProFag. 

## Oppgaver fra ProFag 

### Temperaturkommentator

1. Lag en funksjon som konverterer temperatur fra Fahrenheit til Celsius: $T_C = \frac{5}{9} (T_F - 32)$, og bruk funksjonen til å konvertere en variabel du har definert i selve programmet. 

2. Modifiser programmet slik at det tar input fra brukeren. 

3. Endre funksjonen slik at den samtidig som den konverterer, også velger å si noe om temperaturen. 

> Dette er en oppgave som er ment som mengdetrening på å lage en vanlig funksjon, og for å minne på at man kan gjøre beslutninger (if-tester) inni en funksjon. Dessuten viser den veldig tydelig at funksjoner i programmering er annerledes enn funksjoner i matematikken. 

### Eggkoking på fjellet

1. Lag en funksjon som regner ut kokepunktet til vann i en gitt høyde over havet: Vi velger en forenklet modell: $T_C = 100 - 0,0032 h$, der $h$ oppgis i meter, og temperaturen kommer ut i celsius. Sjekk at funksjonen returnerer riktig verdi ved havnivå (100 C) og på Mount Everest (ca. 72 C). 

2. Vi skal nå koke egg. Tiden $t$ i minutter det tar å oppnå en plommetemperatur på $T_{plomme}$ kan modelleres som:
$$t = A\ln\left[ \frac{2(T_{vann}-T_0)}{T_{vann}-T_{plomme}}\right] $$
der $A$ er en konstant som kommer an på egget, $T_{vann}$ er vanntemperaturen i kjelen (typisk kokepunktet), $T_0$ er temperaturen i egget før det går i gryta og $T_{plomme}$ er temperaturen vi ønsker i plommen. For et vanlig egg er $$A=3,75$$ minutter en fornuftig verdi. Lag en funksjon som implementerer denne modellen, og sjekk at den gir rimelige resultater for bløtkokt (65 C) og hardkokt (85 C) egg. 

3. Endre funksjonen fra 2) slik at den tar inn høyde over havet og bruker funksjonen fra 1) til å regne ut temperaturen i vannet. Hva skjer om man ber om et hardkokt egg på Mount Everest? Kan du endre programmet slik at det oppfører seg penere?

4. (Krever at du kan plotte) Plot tiden det tar å koke egg som fuksjon av hvor varm man ønsker plommen. Plott flere linjer, der hver linje representerer en gitt høyde over havet. 

> I denne oppgaven ønsker vi å trene på å lage funksjoner. Både funksjoner som tar *ett* argument, og funksjoner som tar flere argumenter. I tillegg åpner denne oppgaven for å lage en fusjon som kaller på en annen funksjon. Det er et viktig konseptuelt steg å innse at man kan gjenbruke sine egne funksjoner inni nye fuksjoner. Da kan man i prinsippet lage hva som helst. 

> I denne oppgaven er tiden det tar å koke egg en løsning av varmeligningen, og denne løningen ligger nok over R2/Fysikk 2-nivå. Det man imidlertid kan gjøre her er å se på hva som skjer når kan ender med å få et negativt tall inn til logaritmen. Hva er den fysiske grunnen til at det ikke bør gå bra, og hva er den matematiske grunnen?

## Oppgaver fra ProMod-boka

### Innøving
```
# Input/Output
1.3
1.5

# Funksjoner
1.20
1.24
1.25
1.35

# Beslutninger
2.2
2.5
2.7
2.10 (Velg for eksempel eventyrspillet "Programmering i klasserommet")
```

### Fagspesifikke
```
1.27 (Kjemi)
1.33 (Matematikk)
1.34 (Fysikk)
1.36 (Matematikk R1)

2.12 (Fysikk)
2.15 (Biologi)
```
Det mangler en kjemioppgave under beslutninger. Hva med:

1. Lag et program som tar inn en kjemisk formel og skriver ut hva slags stoff det er snakk om. 
