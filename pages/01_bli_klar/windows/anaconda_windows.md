---
layout: page
title:  "Installasjon av Anaconda for Windows"
---
Denne nettsiden fungerer ikke så bra med Internet Explorer, anbefaler å bruke Chrome, Firefox eller Safari. 

## Last ned Anaconda 
Last ned Anaconda fra [Anaconda][anaconda]{:target="_blank"} sitt nettsted. ![Download]({{ "download_button.png" }})-knapp finnes øverst i høyre hjørne. Etter å ha klikket på denne lander du på en side med flere nedlastingsvalg. 
Vanligvis vil nettstedet se hvilket operativsystem du har. Dersom den ikke gjør det velger du manuelt mellom MacOS, Windows eller Linux. 

Under ser du nettsidene du vil møte under nedlastingen. (Klikk på pilene for å navigere i bildeserien)
{% include carousel.html 
id="downloadCarousel"
images="
anaconda_page.png,
anaconda_download.png,
anaconda_download_2.png
" %}

Velg Python 3.6-versjonen og klikk på den grønne download-knappen (dette gir deg 64-bit versjonen, som så å si alltid er riktig). Før nedlasting kan det hende du blir bedt om å registrere deg, da er det bare å klikke på 
{% include button.html button_name="No Thanks" button_class="btn-outline-secondary btn-sm" %}. 

## Installer anaconda
Deretter installerer du Anaconda ved å åpne (kjøre) den nedlastede filen. Velg å kun installere for din egen bruker ("Just me") om det er på egen maskin og du ikke har administratorrettigheter. Dersom installeren allikevel ber om administratorrettigheter: ta kontakt med lokal IT-support, som vanlig ved installasjon av programmer. Dersom du har nødvendige tilganger, skal du se følgende bilder underveis i prosessen: 

{% include carousel.html 
id="myCarousel" 
images="
installation_1.png, 
installation_2.png,
installation_3.png,
installation_4.png,
installation_5.png,
installation_6.png,
installation_7.png,
installation_8.png,
installation_9.png" 
%}

## Åpne Spyder
Anaconda er en stor pakke som inneholder mye forskjellig. Det viktigste den inneholder er et svært godt utvalg av Python-pakker (ofte kalt bibioteker). Anaconda tilbyr flere forskjellige innganger til å bruke disse pakkene. Vi skal bruke *Spyder*.

Vi skal åpne Spyder gjennom *Anaconda-Navigator*. Når vi åpner Anaconda-Navigator (på samme måte som ethert annet program på datamaskinen) kan vi velge mellom flere alternativer under *Home*: jupyterlab, notebook, qtconsole, spyder, glueviz etc. Vi skal som nevnt bruke Spyder, og klikker derfor på {% include button.html button_name="Launch" button_class="btn-outline-primary btn-small" %}-knappen i boksen til nettopp `Spyder`. 

{% include carousel.html 
id="anacondaCarousel"
images="
open_anaconda_nav.png,
open_spyder.png"
%}
Over vises hvordan du åpner Anaconda og deretter åpner *Spyder*. 

Når du åpner spyder for første gang kan det hende det dukker opp en beskjed om at spyder ikke er oppdatert. Denne kan ignoreres foreløpig, men det er også trygt oppdatere Spyder. 

## Sjekk at anaconda-installasjonen fungerer som den skal 
Det er vanlig å bruke symbolet `>>` om *konsoll*, dvs. *det stedet der du gir python-kommandoer*, altså at du gir en instruksjon til python-interpreteren på maskinen. Dette svarer til det stedet i Anaconda der du kan skrive inn kommandoer direkte (se bilde). I Anaconda sin konsoll vil det vi nettopp har kalt `>>` se ut som `ln [1]:`, men der tallet inne i klammene vil variere etter hvor mange kommandoer du har kjørt side du startet Spyder. 

Den første sjekken er `>> print("Hello, World!")` (trykk enter for å kjøre kommandoen). 

{% include figure.html file="spyder_1.png" caption="Spyder. Til venstre er en kode-editor, nede til høre er det en IPython-konsoll. I Spyder skriver du kommandoer bak <code class='highlighter rouge'>ln [1]:</code>, eller kjører en hel fil, som egentlig tilsvarer å sende inn filen linje for linje til IPython-konsollen." %}

Dersom dette har gått bra printes `Hello, World!` i konsollen. 


### Er anaconda installert med nødvendige pakker?
Kopier innholdet i kodesnutten under, og legg det inn i et nytt script i Anaconda (i venstre del av vinduet). Kjør deretter scriptet ved å trykke på den grønne play-knappen. Det vi ønsker å sjekke her er at du får importert bibliotekene som ligger i `pylab`, og gjøre et par tester på at noe av det inni bibliotekene fungerer. 

{% highlight python %}
from pylab import *
t = linspace(0, 3, 100)
A = t**2
plot(t, A)
xlabel("tid")
ylabel("amplitude")
{% endhighlight %}

Første gang en fil kjøres kommer følgende vindu opp: 

{% include figure.html width="w-100" file="spyder_3.png" caption="Anbefalte innstillinger er slik som på dette bildet." %}


Dersom alt har gått bra skal du nå få opp en figur som viser plottet av funksjonen $$A = t^2$$. Dersom dette ikke fungerer bør du ha fått opp en feilmelding.  

Dersom du skulle få behov for å installere moduler som mangler, gjør du det i "Environments" i Anaconda-Navigator (Men det er lite trolig at det blir nødvendig). 

#### Installere pygame
Må gjøres med pip
#### Installere scipy-special
Kan gjøres med conda

### Innstillinger i Anaconda
Det er mange innstillinger i Anaconda, og mange ting er smak og behag. For at alle skal ha samme oppsett når vi er på kurs, slik at vi unngår unødig feilsøking, har vi følgende forslag til innstillinger: 

Sett "Remove all variables before execution", fordi det sørger for at samme script git samme resultat hver gang. Om du velger å beholde variable kan du i enkelte tilfeller få svært uventet oppførsel. For at dette skal bli standard oppfølsel må du også ordne dette under "Preferences".

{% include figure.html width="w-100" file="spyder_settings_1.png" caption="Kjøreinnstillinger" %}

Du kan velge om du vil at figurer skal dukke opp *inline*, altså sammen med programoutput, eller om du vil at de skal dukke opp i egne vinduer. I det siste tilfellet har du anledning til å interagere med figurene (zoom, pan etc.). Dette er en instilling du kan variere etter behov. Noen ganger lager du mange figurer som skal se ut slik som de kommer ut av plot-kommandoen -- da er *inline* mest effektivt. Andre ganger skal du kanskje studere figurer mer nøye, og trenger å interagere med dem. Alternativet du bruker da er (selv om navnet ikke avslører oppførselen) *Automatic*.

{% include figure.html width="w-100" file="spyder_settings_2.png" caption="Innstillinger for IPython-konsollen" %}

Etter å ha valgt *Automatic* kan du sjekke at alt er i orden. Figuren skal nå komme opp i et eget vindu. Det kan hende du må restarte Spyder for at endringen skal tre i kraft. 

{% include figure.html width="w-100" file="plot_separate_window.png" caption="Når du plotter med automatic skal det se omtrent slik ut, altså at plottet dukker opp i et eget vindu foran Spyder-vinduet." %}

### Det var det hele
Dersom alt har gått bra med installasjonen og testingen ned hit, så har du oppsettet klart for kurset. Vi sees.

[anaconda]: https://www.anaconda.com/
