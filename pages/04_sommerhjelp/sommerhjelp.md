---
layout: page
title: Hjemmeøving og orakel 
sidebar_link: false
---

Mellom kursdagene tilbyr vi hjelp med programmering og utvikling av undervisningsopplegg. Dere vil fort erfare at programmering kan være frustrerende, og det blir mange `SyntaxError` og `IndexError` i begynnelsen. Programmering skal være logisk og fornuftig, men dette inntrykket kan fort forsvinne når du skriver
``` Python
fil = open("test.txt", "w")
fil.write("hei")
```
og finner ut at filen `test.txt` er tom etter at programmet har kjørt. Derfor finnes orakeltjenesten, som drives av én som brukt de fire siste årene av livet sitt på å gjøre alle mulige dumme programmeringsfeil.

Orakeltjenesten består av et [Piazza-forum](https://piazza.com/uio.no/summer2018/profag) hvor dere kan stille spørsmål, kommentere og besvare hverandres spørsmål og dele nyttige ressurser.

Vi håper at Piazza blir en nyttig arena for alle som enten skal undervise i Programmering og Modellering X eller bare ønsker å lære mer om realfaglig programmering. Og vi gleder oss til å se hva dere finner på for elevene deres!

Ta gjerne kontakt på [e-post](mailto:anjohan@uio.no) hvis du har problemer med å komme inn på Piazza.

*Hilsen Cathrine, Knut og Anders*

>Til dere som lurer på hvorfor `test.txt` forblir tom: Filen må lukkes for å garantere at teksten blir skrevet. Det er derfor best å bruke en `with`-blokk, dvs.
>``` Python
>with open("test.txt", "w") as fil:
>	fil.write("hei")
>```
>Da lukkes filen automatisk. Dette er første gang Python blir lagt for hat i introduksjonskurset på UiO.

<div class="card module-links col-centered">
    <div class="card-header">
        <h2>Ekstramateriale</h2>
    </div>
    <div class="card-body">
        <a href="./skriv_til_fil" class="btn btn-outline-primary materials-links">Skrive til fil</a>
		<a href="./tilfeldige_tall" class="btn btn-outline-primary materials-links">Tilfeldige tall</a>
        <a href="./diverse_tips" class="btn btn-outline-primary materials-links">Diverse tips</a>
    </div>
</div> 
