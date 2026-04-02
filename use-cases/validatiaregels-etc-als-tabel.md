# Validatieregels en plausibiliteitschecks voor invoer tellingen

__Dit overzicht is niet volledig. Het is een voorstel voor het gebruik van tabellen voor de regels en checks.__

## Validatieregels geven fouten

### Regels voor alle numerieke invoervelden (reeks F.0xx)

Er zijn geen regels omdat het niet mogelijk is om foute aantallen in te vullen in de frontend, dus er wordt een error vanuit de backend gegeven als er toch met de aantallen geknoeid is en ze niet toegestaan zijn.

### Regels voor extra onderzoek en controles (reeks F.1xx)

Deze regels zijn alleen van toepassing bij invoer voor de eerste zitting. De gerelateerde velden staan namelijk niet in corrigenda-PV's.

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.101 | 'Alleen bij extra onderzoek B1-1': één van beide vragen is beantwoord, en de andere niet                     | X |   |   |
| F.102 | 'Alleen bij extra onderzoek B1-1': meerdere antwoorden op 1 van de vragen                                    | X |   |   |
| F.111 | 'Verschillen met telresultaten van het stembureau': één of beide vragen zijn niet beantwoord                 | X |   |   |
| F.112 | 'Verschillen met telresultaten van het stembureau': meerdere antwoorden per vraag                            | X |   |   |
| F.121 | Over het proces-verbaal: Niet alle vragen bij 'Over het proces-verbaal' zijn beantwoord                      |   | X |   |
| F.122 | Over het proces-verbaal: Ongeldige combinatie van antwoorden: `wel corrigendum, geen inlegvel`               |   | X |   |
| F.131 | 'Controles en correcties': geen vinkjes bij de eerste twee vragen                                            |   | X |   |
| F.132 | 'Controles en correcties': Ongeldige set documenten (vraag 'gecorrigeerde telresultaten' = 'nee')            |   | X |   |
| F.133 | 'Controles en correcties': Ongeldig antwoord in eerste zitting (vraag 'op verzoek van het CSB'  is ingevuld) |   | X |   |
| F.134 | 'Controles en correcties': meer dan 1 antwoord op vraag 'zijn er gecorrigeerde telresultaten'                |   | X |   |

#### F.101: 'Alleen bij extra onderzoek B1-1': één van beide vragen is beantwoord, en de andere niet

> Invoerder: **Controleer je antwoorden** (F.101)

> Coördinator: **Beide vragen moeten beantwoord ofwel overgeslagen zijn** (F.101)  
> Als er extra onderzoek is gedaan, moeten beide vragen beantwoord worden.  
> Als er geen extra onderzoek is gedaan, moeten deze vragen overgeslagen worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.102: 'Alleen bij extra onderzoek B1-1': meerdere antwoorden op 1 van de vragen

> Invoerder: **Controleer je antwoorden** (F.102)

> Coördinator: **Er mag maar één antwoord per vraag worden gegeven** (F.102)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.111: 'Verschillen met telresultaten van het stembureau': één of beide vragen zijn niet beantwoord

> Invoerder: **Controleer je antwoorden** (F.111)

> Coördinator: **Bij beide vragen moet een antwoord gegeven worden** (F.111)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.112: 'Verschillen met telresultaten van het stembureau': meerdere antwoorden per vraag

> Invoerder: **Controleer je antwoorden** (F.112)

> Coördinator: **Er mag maar één antwoord per vraag worden gegeven** (F.112)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.121: Over het proces-verbaal: Niet alle vragen bij 'Over het proces-verbaal' zijn beantwoord

> Invoerder: **Controleer je antwoorden** (F.121)
> - Beantwoord de vragen over het papieren proces-verbaal.
> - Overleg met de coördinator als je twijfelt.

> Coördinator: **Er is niet correct aangegeven welke documenten zijn ingevoerd** (F.121)
> - Bekijk welke documenten aanwezig zijn.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)
[Voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=10078-124322)

#### F.122: Over het proces-verbaal: Ongeldige combinatie van antwoorden: `wel corrigendum, geen inlegvel`

> Invoerder: **Het inlegvel ontbreekt, maar hoort wel aanwezig te zijn** (F.122)
> - Overleg met de coördinator over het ontbrekende inlegvel.

> Coördinator: **Het inlegvel ontbreekt, maar hoort wel aanwezig te zijn** (F.122)
> - Zorg dat een correct ingevuld inlegvel wordt toegevoegd.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.131: 'Controles en correcties': geen vinkjes bij de eerste twee vragen

> Invoerder: **Controleer je antwoorden** (F.131)

> Coördinator: **De vragen op het inlegvel zijn niet volledig beantwoord** (F.131)
> - Zorg dat het inlegvel volledig is ingevuld.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.132: 'Controles en correcties': Ongeldige set documenten (vraag 'gecorrigeerde telresultaten' = 'nee')

> Invoerder: **Controleer je antwoorden** (F.132)  
> Er is een corrigendum, maar er zijn volgens de antwoorden op het inlegvel 'controles en correcties' geen gecorrigeerde telresultaten.
> - Overleg met de coördinator.

> Coördinator: **Onterecht corrigendum?** (F.132)  
> Er is een corrigendum, maar er zijn volgens de antwoorden op het inlegvel 'controles en correcties' geen gecorrigeerde telresultaten.
> - Als er geen gecorrigeerde telresultaten zijn, dan hoort er ook geen corrigendum te zijn.
> - Verwijder het corrigendum, of geef op het inlegvel aan dat er wel gecorrigeerde telresultaten zijn.
> - Geef daarna de invoer terug aan de invoerder.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.133: 'Controles en correcties': Ongeldig antwoord in eerste zitting (vraag 'op verzoek van het CSB' is ingevuld)

> Invoerder: **Controleer je antwoorden** (F.133)

> Coördinator: **Tijdens de eerste zitting kan er nog geen verzoek van het Centraal Stembureau zijn** (F.133)
> - Herstel de fout door op papier de juiste optie(s) aan te (laten) vinken.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.134: 'Controles en correcties': meer dan 1 antwoord op vraag 'zijn er gecorrigeerde telresultaten'

> Invoerder: **Controleer je antwoorden** (F.134)

> Coördinator: **Er mag maar 1 antwoord per vraag worden gegeven** (F.134)
> - Herstel de fout door op papier de juiste optie(s) aan te (laten) vinken.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)


### Regels voor totalen (reeks F.2xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.201 | stempassen + volmachten <> totaal toegelaten kiezers                                                       | X | X |   |
| F.202 | E.1 t/m E.n tellen niet op naar E                                                                          | X | X |   |
| F.203 | stemmen op kandidaten + blanco stemmen + ongeldige stemmen <> totaal aantal uitgebrachte stemmen           | X | X |   |
| F.204 | De som van lijsttotalen (E.1 t/m E.n) is groter dan 0 en (E = leeg of 0)                                   | X | X | X |

#### F.201: `stempassen + volmachten <> totaal toegelaten kiezers`

> Invoerder: **Controleer je antwoorden** (F.201)

> Coördinator: **A en B tellen niet op tot D** (F.201)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als het juiste getal bij D wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij D het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

Velden markeren: A, B en D

#### F.202: `E.1 t/m E.n tellen niet op naar E`

> Invoerder **Controleer je antwoorden** (F.202)

> Coördinator: **De stemmen op lijsten tellen niet op tot E** (F.202)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en H worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en H de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

Velden markeren: E.1 t/m E.n en E

#### F.203: `stemmen op kandidaten + blanco stemmen + ongeldige stemmen <> totaal aantal uitgebrachte stemmen`

> Invoerder: **Controleer je antwoorden** (F.203)

> Coördinator: **E, F en G tellen niet op tot H** (F.203)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als het juiste getal bij H wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij H het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

Velden markeren: E, F, G en H

#### F.204: `De som van lijsttotalen (E.1 t/m E.n) is groter dan 0 en (E = leeg of 0)`

> Invoerder: **Controleer je antwoorden** (F.204)

> Coördinator (CSO): **Het totaal aantal stemmen op kandidaten is niet ingevuld** (F.204)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en E.1 t/m E.n worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en E.1 t/m E.n de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

Velden markeren: E

> Coördinator (DSO): **Het totaal aantal stemmen op kandidaten is niet ingevuld** (F.204)  
> Controleer in rubriek 2.2 of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en E.1 t/m E.n worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en E.1 t/m E.n de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

Velden markeren: E



### Regels voor verschillen (reeks F.3xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.301 | "Vergelijk D&H": (checkbox D=H is aangevinkt, maar D<>H)                                                                            | X | X |   |
| F.302 | "Vergelijk D&H": (checkbox H>D is aangevinkt, maar H<=D)                                                                            | X | X |   |
| F.303 | "Vergelijk D&H": (checkbox H<D is aangevinkt, maar H>=D)                                                                            | X | X |   |
| F.304 | "Vergelijk D&H": Meerdere aangevinkt of geen enkele aangevinkt                                                                      | X | X |   |
| F.304 | (Als D = H) I en/of J zijn ingevuld                                                                                                 | X | X |   |
| F.306 | (Als H > D) `I <> H - D`                                                                                                            | X | X |   |
| F.307 | (Als H > D) J is ingevuld                                                                                                           | X | X |   |
| F.308 | (Als H < D) `J <> D - H`                                                                                                            | X | X |   |
| F.309 | (Als H < D) I is ingevuld                                                                                                           | X | X |   |
| F.310 | (Als D <> H en verklaring voor verschil niks aangevinkt of 'ja' en 'nee' aangevinkt)                                                | X | X |   |
| F.311 | (2.3.2 (verklaring voor verschil) = nee en 'vanwege een onverklaard verschil' in stap 'controles en correcties' is niet aangevinkt) |   | X |   |
| F.312 | totaal aantal kiezers = totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen                          |   |   | X |

#### F.301 "Vergelijk D&H": (checkbox D=H is aangevinkt, maar D<>H)

> Invoerder: **Controleer je antwoorden** (F.301)

> Coördinator (CSO): **De getallen die zijn ingevuld bij D en H zijn niet gelijk** (F.301)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of er een onverklaard verschil ontstaat.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

Veld markeren: foutmelding op 3.3.1 "Vergelijk D en H"

> Coördinator (DSO): **De getallen die zijn ingevuld bij D en H zijn niet gelijk** (F.301)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of er een onverklaard verschil ontstaat.
> - Pas zo nodig rubriek 2.3.2 aan, en volg de instructies over hertellen die daar staan.

Veld markeren: foutmelding op 2.3.1 "Vergelijk D en H"

#### F.302 "Vergelijk D&H": (checkbox H>D is aangevinkt, maar H<=D)

> Invoerder: **Controleer je antwoorden** (F.302)

> Coördinator (CSO): **Het getal dat is ingevuld bij H is niet groter dan D** (F.302)

Veld markeren: foutmelding op 3.3.1 "Vergelijk D en H"

> Coördinator (DSO): **Het getal dat is ingevuld bij H is niet groter dan D** (F.302)
> - Maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 2.3.1 "Vergelijk D en H"

#### F.303 "Vergelijk D&H": (checkbox H<D is aangevinkt, maar H>=D)

> Invoerder: **Controleer je antwoorden** (F.303)

> Coördinator (CSO): **Het getal dat is ingevuld bij H is niet kleiner dan D** (F.303)

Veld markeren: foutmelding op 3.3.1 "Vergelijk D en H"

> Coördinator (DSO): **Het getal dat is ingevuld bij H is niet kleiner dan D** (F.303)
> - Maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 2.3.1 "Vergelijk D en H"

#### F.304 "Vergelijk D&H": Meerdere aangevinkt of geen enkele aangevinkt

> Invoerder: **Controleer je antwoorden** (F.304)

> Coördinator (CSO): **Deze vraag moet precies één antwoord hebben** (F.304)

Veld markeren: foutmelding op 3.3.1 "Vergelijk D en H"

> Coördinator (DSO): **Deze vraag moet precies één antwoord hebben** (F.304)  
> Is op het proces-verbaal duidelijk aangegeven welk van de opties bedoeld is?
> - Zo ja: laat dat dan overnemen in Abacus.
> - Zo nee: maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 2.3.1 "Vergelijk D en H"

#### F.305 (Als D = H) I en/of J zijn ingevuld
> Invoerder: **Controleer je antwoorden** (F.305)

> Coördinator (CSO): **Controleer I en J** (F.305)  
> De getallen bij D en H zijn gelijk. Er zijn geen stemmen meer of minder geteld.
> - Herstel de fout door op papier I en/of J leeg te (laten) maken.

Veld markeren: I en/of J (als ingevuld)

> Coördinator (DSO): **Controleer I en J** (F.305)  
> De getallen bij D en H zijn gelijk. Er zijn geen stemmen meer of minder geteld.
> - Corrigeer de rekenfout door op een corrigendum I en/of J leeg te (laten) maken.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I en/of J (als ingevuld)

#### F.306 (Als H > D) `I <> H - D`

> Invoerder: **Controleer je antwoorden** (F.306)

> Coördinator (CSO): **Controleer aantal méér getelde stemmen (I)** (F.306)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

Veld markeren: I

> Coördinator (DSO): **Controleer aantal méér getelde stemmen (I)** (F.306)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I

#### F.307 (Als H > D) J is ingevuld

> Invoerder: **Controleer je antwoorden** (F.307)

> Coördinator (CSO): **Controleer of I en J verwisseld zijn** (F.307)
> - Herstel de fout door op papier het verschil op de juiste plek in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

Veld markeren: I, J

> Coördinator (DSO): **Controleer of I en J verwisseld zijn** (F.307)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I, J

#### F.308 (Als H < D) `J <> D - H`
> Invoerder: **Controleer je antwoorden** (F.308)

> Coördinator (CSO): **Controleer aantal minder getelde stemmen (J)** (F.308)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

Veld markeren: J

> Coördinator (DSO): **Controleer aantal minder getelde stemmen (J)** (F.308)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: J

#### F.309 (Als H < D) I is ingevuld
> Invoerder: **Controleer je antwoorden** (F.309)

> Coördinator (CSO): **Controleer of I en J verwisseld zijn** (F.309)
> - Herstel de fout door op papier het verschil op de juiste plek in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

Veld markeren: I, J

> Coördinator (DSO): **Controleer of I en J verwisseld zijn** (F.309)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I, J

#### F.310 (Als D <> H en verklaring voor verschil niks aangevinkt of 'ja' en 'nee' aangevinkt)

> Invoerder: **Controleer je antwoorden** (F.310)

> Coördinator: **Deze vraag moet precies één antwoord hebben** (F.310)

Veld markeren: foutmelding op 3.3.2 (CSO) of 2.3.2 (DSO)

#### F.311 (2.3.2 (verklaring voor verschil) = nee en 'vanwege een onverklaard verschil' in stap 'controles en correcties' is niet aangevinkt)

> Invoerder: **Controleer je antwoorden** (F.311)

> Coördinator: **Hertel onverklaard verschil** (F.311)  
> Er is een onverklaard verschil dat herteld moet worden.
> - Hertel de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op een corrigendum in.
> - Is er al herteld? Zorg dan dat het inlegvel 'controles en correcties' wordt ingevuld en toegevoegd aan het proces-verbaal van het stembureau.

Veld markeren: foutmelding op 2.3.2

#### F.312: `totaal aantal kiezers = totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen`

> Invoerder: **Controleer je antwoorden** (F.312)

> Coördinator: **D is niet gelijk aan H min I plus J** (F.312)  
> Controleer of de juiste getallen zijn overgenomen. Indien de optelling niet klopt kun je niet verder gaan met de invoer. Er is iets misgegaan met het opmaken of overdragen van het procesverbaal van het onderliggende niveau. Overleg met het CSB over de vervolgstappen.

Velden markeren: D, H, I en J
