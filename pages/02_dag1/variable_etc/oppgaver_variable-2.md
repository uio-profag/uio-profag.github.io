
# Variable

## Oppgaver om aritmetikk — innøving

1. Overbevis deg om rekkefølgen uttrykkene under beregnes i. Programmer hvert uttrykk og sjekk at det ble riktig. 

    a) ${\tt 2+3*4+6/2}$

    b) ${\tt 1/2{**}3{**}2}$

    c) ${\tt 1/(1+1/(1+2))}$

    d) ${\tt (1+2{**}3){**}(5-3*2)}$
    
    e) ${\tt 2{**}{-1}*3}$

2. Gi variablene $a$, $b$ og $c$ verdier med tilordningene $a=1$, $b=2$ og $c=3.0$. Hva er verdien av $a$ etter at hver av de følgende operasjonene er utført i Python? Regn for hånd først!

a) ${\tt a = a/c}$

b) ${\tt a = b{**}+c}$

c) ${\tt a = b/c*c/b}$

## Oppgaver fra ProMod

### Om to-tallsystemet

2.1  
2.4

## Løsning av andregradsligning

1. Skriv et Python-program som løser andregradsligningen $ax^2+bx+c=0$ ved hjelp av formelen
$$
x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.
$$
Programmet skal lese inn de tre koeffiesientene $a$, $b$ og $c$ og skrive ut de to røttene. Test programmet på noen eksempler.


2. Kan du identifisere tilfeller der $a,b,c$-formelen bryter sammen? Utvid programmet slik at det oppfører seg fornuftig også i disse situasjonene. (I denne oppgaven må du bruke kunnskap fra de senere leksjonene.)

## Oppgave om avrundingsfeil

1. Regn ved hjelp av Python ut verdien av uttrykket $f(x)=1/\bigl(\sqrt{x^2+1}-x\bigr)$ for $x=10^8$. 


2. Hvis vi ganger med det konjugerte uttrykket $\sqrt{x^2+1}+x$ i teller og nevner og forenkler med tredje kvadratsetning
ser vi at $f(x)$ alternativt kan skrives som $g(x)=\sqrt{x^2+1}+x$. Regn ut $g\bigl(10^8\bigr)$ også og sammenlign de to svarene.
Bruk en annen kilde som for eksempel Wolfram Alpha til å sjekke hva som er riktig svar. Kan du forklare resultatene?
