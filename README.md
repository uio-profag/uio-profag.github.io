# UiO Profag nettsider

I dette repositoriet ligger nettsidene til profag. Nettadressen er uio-profag.github.io.

Nettsidene er satt opp med en venstremarg med hovedlenker og et innholdsfelt til høyre. 

**TLDR;** Alt innhold som skal vises i innholdsfeltet ligger i `pages`-mappen. Standard måte å endre innhold på er å redigere markdown-filen som hører til den sesjonen du ønsker å endre innholdet for. Eller å bytte ut pdf-filen med slidesene. Eller å bytte ut en eventuell separat markdown-fil med oppgaver. For at bilder ol. som er lagt inn i markdown-filer skal fungere, så må de lastes opp i github med riktig relativ bane. Markdown eksportert fra Jupyter notebook gjør dette riktig av seg selv så lenge man legger markdown-fila i samme mappe som de andre filene som følger med markdown-eksporten. Terskelen for å spørre @henriasv om ting bør være lav, for om noe ser vrient ut er det sannsynligvis bare en eller annen litt rar konvensjon et sted.  
**/TLDR;**

Alt innhold som skal vises i innholdsfeltet ligger i `pages`-mappen. Der ligger det for det første én fil som heter `index.md`. Den inneholder materialet som kommer i innholdsfeltet når man åpner uio-profag.github.io. I `pages`-mappen ligger det også undermapper, som tilsvarer oppføringene i venstremargen. Inne i hver undermappe ligger det en fil med `<undermappenavn_nivå1>.md`. Denne filen skal settes opp manuelt slik at den lenker til innhold i et nytt nivå med undermapper, for eksempel `input_output_beslutninger_funksjoner`, som ligger under `Dag 1`. Når lenker fra `<undermappenavn_nivå1>.md` først er satt opp vil alle endringer på nettsiden handle om å endre innhold i markdown-filer eller å bytte ut pdf-filer eller bytte ut eventuelt andre filer vi velger å bruke. 

Syntaksen for å legge inn en kursmodul fra `<undermappenavn_nivå1>.md` (f. eks `dag1.md`) er litt rar:

{% include module_links.html  
title="<modulnavn>"  
forelesningsnotat="<relativ_filbane>"  
pdf-slides="<relativ_filbane>"  
oppgaver="<relativ_filbane>"  
published="<true/false>"  
%}
  
For eksempel:

{% include module_links.html  
title="Del 3: Plotting, lesing fra fil"  
forelesningsnotat="./plotting_les_fra_fil/plotting_les_fra_fil"  
pdf-slides="./plotting_les_fra_fil/plotting_les_fra_fil_slides.pdf"  
oppgaver="./plotting_les_fra_fil/plotting_les_fra_fil_oppgaver"  
published=true  
%}

Merk at markdown-filer går inn uten `.md`-endelse, mens filer som skal lastes ned (e.g. pdf) går inn *med* filendelse. `published=true` fører til at innholdet faktisk lenkes opp, mens `published=false`fører til at modulen på nettsiden er en boks der det står at det kommer noe senere. 

For å få en side til å dukke opp i venstremargen, legg til `sidebar_link: true` i *front matter* (mellom -----   ------). I utgangspunktet øsnker vi dette for kategorier av typen `Bli klar til kurs`, `Dag 1`, `Dag 2` og `Sommerhjelp`, altså ikke for delsesjoner innenfor samme kursdag. 


Nettsidene er basert på [Hydeout](https://github.com/fongandrew/hydeout)

