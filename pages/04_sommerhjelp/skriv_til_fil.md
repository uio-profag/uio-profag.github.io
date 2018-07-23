---
layout: page
title: Skrive til fil
---

På første kursdag lærte du å lese fra fil. For å skrive til fil trenger du å bruke løkker. Nedenfor ser du et eksempel. Før du går gjennom eksemplet kan du forsøke å lage programmet selv. 
I ProMod-boka avsnitt 5.3 kan du lese mer om å skrive til fil. Legg merke til at du må først åpne en fil med et filnavn du velger. Deretter skriver du inn linje for linje med kommandoen `file.write`. Til slutt lukker du filen.  

Prøv å lag et program til denne instruksen før du ser på løsningen under: 
Lag et program med en funksjon som regner ut posisjon ved hjelp av en bevegelseslikning for konstant akselerasjon. Funksjonen skal ta startfart og akselerasjon som argument. Deretter skal programmet regne ut posisjon for N tidsverdier mellom 0 og 10 og plotte resulatet i en veigraf. Til slutt skal data for tid og posisjon skrives til en fil. 


```python
from pylab import *

def regnutposisjon(tid, startfart, akselerasjon):     #funksjon med bevegelsesformel
    return startfart*tid + 0.5*akselerasjon*tid**2


N = 100      # antall tidsverdier
tidmatrise = linspace(0, 10, N) #velger tid fra 0 til 10 sekunder
v0 = 0        # velger startfart 0 m/s
a = 1.6       # velger akselerasjon 1.5 m/s^2
i = 0
posisjon = zeros(N, float) # posisjon er en matrise med N utregnede verdier
#print(tidmatrise)
#print(posisjon)

for i in range(N):
    posisjon[i]=regnutposisjon(tidmatrise[i],v0,a)

#print(tidmatrise,posisjon)
plot(tidmatrise,posisjon,color="magenta")
xlabel("Tid/s")
ylabel("Posisjon/m")

#Nå skal programmet skrive til filen tidogpos.txt
fil=open("tidogpos.txt", "w")
fil.write("Tid           Posisjon \n")
for i in range(N):
    fil.write(str(tidmatrise[i]))
    fil.write("          ")
    fil.write(str(posisjon[i])+ '\n')
    
fil.close()

```

Nå har du fått en fil som heter *tidogpos.txt*. Åpne filen og se på den. Den er kanskje ikke så pen... 

### Oppgave
1. Hva kan du gjøre for at filen skriver ut verdier med bare to desimaler og at alle tallverdien kommer på samme sted under hverandre? 

2. På den første kursdagen leste vi bare inn filer som hadde tallverdier i to kolonner. Nå har du en første linje med tekst. Du kan velge å hoppe over denne linjen når du leser fra filen. Hvordan gjør du det? 

3. Du kan eventuelt bruke en løkke for å lese inn før du plotter. Gjør dette. Les inn verdiene og legg dem i to vektorer `tid` og `posisjon`. Plott veigrafen. Se i ProMod-boka hvis du trenger hjelp. 

4. Du skal nå modellere et fallende (og veldig raskt) termometer. Modifiser programmet slik at det også skriver til fil temperaturen som vises på et termometer som faller uten luftmotstand fra 100 meter. Det er en varm sommerdag, med havnivåtemperatur på 26$^\circ$C og vi antar at lufttemperaturen endrer seg som ved adiabatisk kompresjon, altså -10$^\circ$C/km, slik at temperaturen er lavere i høyden. 

## PS
Du kan også skrive til fil uten selv å måtte skrive løkker ved å bruke `numpy.savetxt`-funksjonen. Du kan lese om hvordan den brukes på [dokumentasjonssiden](https://docs.scipy.org/doc/numpy-1.14.5/reference/generated/numpy.savetxt.html) til `numpy.savetxt`
