---
layout: page
title:  "Installasjon av Anaconda for MacOS"
---

## Last ned Anaconda 
Last ned Anaconda fra [Anaconda][anaconda]{:target="_blank"} sitt nettsted. {% include button.html button_name="Download" button_class="btn-success" %}-knapp finnes øverst i høyre hjørne. Etter å ha klikket på denne lander du på en side med flere nedlastingsvalg. 
Vanligvis vil nettstedet se hvilket operativsystem du har. Dersom det ikke gjør det velger du manuelt mellom MacOS, Windows eller Linux. 

{% include figure.html file="download_site_small.jpg" caption="Nedlastingssiden til Anaconda." %}

Velg Python 3.6-versjonen og klikk på den grønne download-knappen (dette gir deg 64-bit versjonen, som så å si alltid er riktig). Før nedlasting kan det hende du blir bedt om å registrere deg, da er det bare å klikke på 
{% include button.html button_name="No Thanks" button_class="btn-outline-secondary btn-sm" %}. 

## Installer Anaconda
Anaconda installeres med en vanlig installer (dobbeltklikke på den nedlastede filen). Dersom installeren ber om administratorrettigheter: ta kontakt med lokal IT-support, som vanlig ved installasjon av programmer. Dersom du har nødvendige tilganger skal du se noe som ligner på bildene under underveis i prosessen. Du kan trykke *Continue* og *Install* hele veien. Det er ikke nødvendig å installere Microsoft VSCode, selv om installeren lurer på om du har lyst. 

{% include carousel.html 
id="myCarousel" 
images="
installer1_annotated.png, 
installer2_annotated.png,
installer3_annotated.png,
installer4_annotated.png" 
%}

## Åpne Spyder
Anaconda er en stor pakke som inneholder mye forskjellig. Det viktigste den inneholder er et svært godt utvalg av Python-pakker. Anaconda tilbyr flere forskjellige innganger til å bruke disse pakkene. På kurset skal vi bruke *Spyder*.

Du åpner *Spyder* gjennom *Anaconda-Navigator*. Når du åpner Anaconda-Navigator (som nå skal ligge i *Applications*-mappen) kan du velge mellom flere alternativer under *Home*: jupyterlab, notebook, qtconsole, spyder, glueviz etc. Siden vi skal bruke *Spyder* på kurset, klikker du på {% include button.html button_name="Launch" button_class="btn-outline-primary btn-small" %}-knappen i boksen til nettop *Spyder*. 

{% include figure.html file="anaconda-navigator_annotated.png" caption="Her velger du på hvilken måte du vil bruke Anaconda. Velg <i>Spyder</i>" %}

Når du åpner Spyder for første gang kan det hende det dukker opp en beskjed om at spyder ikke er oppdatert. Denne kan du ignorere foreløpig. 

{% include figure.html width="w-75" file="incoming_connections.png" caption="Python vil ha lov til å bli kontaktet fra internett. For våre formål går det fint å blokkere denne forespørselen." %}

{% include figure.html width="w-50" file="update_spyder.png" caption="Spyder kan være utdatert. Foreløpig kan du ignorere det." %}

## Sjekk at anaconda-installasjonen fungerer som den skal 
Det er vanlig å bruke symbolet `>>` om *konsoll*, dvs. *det stedet der du gir python-kommandoer*, altså at du gir en instruksjon til python-interpreteren på maskinen. Dette svarer til det stedet i Anaconda der du kan skrive inn kommandoer direkte (se bilde). I Anaconda sin konsoll vil det vi nettopp har kalt `>>` se ut som `ln [1]:`, men der tallet inne i klammene vil variere etter hvor mange kommandoer du har kjørt side du startet Spyder. 

Den første sjekken er å kjøre `>> print("Hello, World!")` (trykk enter for å kjøre kommandoen)

{% include figure.html file="spyder-window.png" caption="Spyder. Til venstre er en kode-editor, nede til høre er det en IPython-konsoll" %}

Dersom dette har gått bra printes `Hello, World!` i terminalen. 


### Er anaconda installert med nødvendige pakker?
Når vi skal kjøre mer enn en linje med kode er det bedre å legge koden i en fil enn å skrive den rett inn i konsollen. Dette gjør vi med *editoren* på venstre side i Spyder. Kopier innholdet i kodesnutten under, og legg det inn i et nytt script i Anaconda. Kjør deretter scriptet ved å trykke på den grønne play-knappen. Det vi ønsker å sjekke her er at du får importert bibliotekene som ligger i `pylab`, og gjøre et par tester på at noe av det inni bibliotekene fungerer. 

{% highlight python %}
from pylab import *
t = linspace(0, 3, 100)
A = t**2
plot(t, A)
xlabel("tid")
ylabel("amplitude")
{% endhighlight %}

Første gang en fil kjøres kommer følgende vindu opp: 

{% include figure.html width="w-50" file="first_run.png" caption="Anbefalte innstillinger er slik som på dette bildet." %}

Dersom alt har gått bra skal du nå få opp en figur som viser $$A = t^2$$. Dersom dette ikke fungerer bør du ha fått opp en feilmelding.  

Dersom du skulle få behov for å installere moduler som mangler, gjør du det i "Environments" (Men det er lite trolig at det blir nødvendig). 

{% include figure.html width="w-100" file="install_packages.png" caption="Pakke-installasjon. Bruk søkefeltet oppe til høyre for å søke opp pakker." %}

#### Én annerledes installasjon: pygame
I læreboka i Programmering og modellering brukes et bibliotek som heter `pygame`. Pygame er litt spesielt, for det finnes ikke som pakke i Anaconda. Derfor må vi installere den med noe som heter `pip`:   
Skriv `>> /Applications/anaconda3/bin/pip install pygame` i programmet *Terminal*.

### Innstillinger i Anaconda
Det er mange innstillinger i Anaconda, og mange ting er smak og behag. For at alle skal ha samme oppsett når vi er på kurs, slik at vi unngår unødig feilsøking, har vi følgende forslag til innstillinger: 

Særlig viktig er det å sette ``Remove all variables before execution'', fordi det sørger for at samme script git samme resultat hver gang. Om du velger å beholde variable kan det i enkelte tilfeller føre til svært uventet oppførsel. 

{% include figure.html width="w-75" file="run_settings.png" caption="Kjøreinnstillinger" %}

Du kan velge om du vil at figurer skal dukke opp *inline*, altså sammen med programoutput i konsollen, eller om du vil at de skal dukke opp i egne vinduer. I det siste tilfellet har du anledning til å interagere med figurene (zoom, pan etc.). Dette er en innstilling som kan varieres etter behov. Noen ganger ønsker man mange figurer som er ferdig laget -- da er *inline* mest effektivt. Andre ganger ønsker du kanskje å studere figurer mer nøye, og trenger å interagere. Alternativet du bruker da er (selv om navnet ikke avslører oppførselen) *Automatic*.

{% include figure.html width="w-75" file="graphics_setting.png" caption="Innstillinger for IPython-konsollen" %}

Etter å ha valgt *Automatic* kan du sjekke at alt er i orden ved å kjøre scriptet på nytt (trykke på play). Figuren skal nå komme opp i et eget vindu. Det kan hende du må restarte Spyder for at endringen skal tre i kraft. 

### Det var det hele
Dersom alt har gått bra med installasjonen og testingen ned hit, så har du oppsettet klart for kurset. Vi sees.


[anaconda]: https://www.anaconda.com/
