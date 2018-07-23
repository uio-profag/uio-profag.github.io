---
layout: page
title: Diverse tips
---

På denne siden legger vi ut småtips til ting dere kan ha nytte av.

## Python-programmering på telefon og nettbrett
Det er mulig å programmere python på telefon og nettbrett, og det finnes flere forskjellig løsninger. Felles for disse er at du risikerer at ting vi se litt annerledes ut enn ved programmering på vanlig datamaskin. Særlig gjelder dette ved bruke av grafiske elementer, slik som plots. Det er også vanlig at grafisk funksjonalitet oppleves som ustabil. 

Du kan installere en app, slik som Pythonista 3 (iOS, $10). Pythonista har pylab installert, så her vil ting fungere slik som beskrevet i ProMod-boka. Pythonista oppleves som stabil, men merk at plots ikke er interaktive. Vi har foreløpig ikke funnet noen gratis app med `pylab`-støtte.

Et annet alternativ, er [repl.it](https://repl.it), eller en annen tilsvarende nettbasert tjeneste. repl.it har også en klasseromsfunksjon som er gratis så lenge man tåler at det som legges ut ligger åpent på nettet. Merk at i repl.it finnes ikke pylab. Man vil allikevel gjenfinne alle funksjonene fra pylab enten i `matplotlib`, `numpy` eller `scipy`. MEN: det er ikke direkte støtte for plotting her, så i stedet kan man lagre med `matplotlib.pyplot.savefig`:
```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 2, 100)
y = x**2
plt.plot(x, y)
plt.savefig("plot.png")
``` 

## Tekst-editorer på datamaskin

Det finnes mange forskjellige tekst-editorer, og like mange meninger om hvilken som er den beste. I ProFag har vi brukt Spyder for å være sikre på at ting ser likt ut hos alle. Når man underviser et helt semester er det ikke nødvendig med så strenge restriksjoner. Her anbefaler vi å la studentene velge selv. De som har programmert for lenge siden har kanskje brukt VIM eller Emacs. Det er ikke nødvendig å anbefale disse editorene til elever, for de stammer fra tide før man fikk pene grafiske brukergrensesnitt. Et par tekst-editorer vi har gode erfaringer med er [Visual Studio Code](https://code.visualstudio.com) (gratis) og [Sublime Text 3](https://www.sublimetext.com/) ($80). Begge disse editorene har god støtte for utvidelsespakker og er behagelige å bruke, så de kan trygt anbefales til elever som søker råd. 

## Linting
Linting er en prosess der kode blir sjekket for feil. Det være seg logiske feil og stilmessige feil. I praksis er det et program som ser over koden og spytter ut en rekke feilmeldinger dersom man har gjort noe galt. Det er mange tekst-editorer som har innebygget linting-funksjonalitet. For eksempel [Visual Studio Code](https://code.visualstudio.com). 

Vi i ProFag tenker ikke det er nødvendig for elevene å lære seg om linting i første omgang, men det kan være et nyttig verktøy for deg som lærer for å være sikker på at du skriver kode som er konsekvent og lett å lese for andre. For å komme i gang med linting av Python-kode med Visual Studio Code kan du navigere deg fra [python-siden til Visual Studio Code](https://code.visualstudio.com/docs/languages/python).

## Dokumentasjon 
Python har en omfattende [dokumentasjon](https://docs.python.org/3/). Dokumentasjon kan være litt krevende å lese i starten, litt som å lete i bilmanualen for å finne ut hvordan å få bilen til å starte når det lyser en lampe du aldri har sett før. Men når du først knekker koden er dokumentasjonen svært behagelig å forholde seg til. 

