# Validatieregels en plausibiliteitschecks voor invoer tellingen

## Definities

**[Fout](#validatieregels-geven-fouten)**:
Een fout wijst op een probleem in het papieren proces-verbaal. Dit probleem moet opgelost worden voordat een tweede invoerder aan de slag gaat. Als een proces-verbaal gecorrigeerd wordt, moet het proces-verbaal twee keer opnieuw ingevoerd worden.

**[Waarschuwing](#plausibiliteitschecks-geven-waarschuwingen)**:
Een waarschuwing wijst op een opmerkelijke uitkomst in het papieren proces-verbaal. Dit moet het GSB verklaren, anders kan dit resulteren in een nieuwe zitting.

### Meerdere fouten en waarschuwingen in 1 response

Een request naar de backend kan meerdere fouten en waarschuwingen teruggeven.

In de user interface behandelen we die als volgt:

- Voor de stappen **vóór** de hoogste stap waar de gebruiker invoer voor heeft gedaan: als er fouten zijn dan tonen we bij die stap in de navigatiebalk een fout-icoon, als er alleen waarschuwingen zijn dan tonen we bij die stap in de navigatiebalk een waarschuwings-icoon ([voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=137-4359&t=6BRGJQMHbKwihTCh-4)).
- Fouten of waarschuwingen **voorbij** de hoogste stap waar de gebruiker invoer voor heeft gedaan, tonen we niet.
- Zijn er fouten of waarschuwingen in de huidige stap, dan tonen we alle fouten en waarschuwingen ([voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=2871-9169&t=FtsIfhKtOeDxlo9v-4)).
  - We tonen van elke melding de titel, het nummer en de toelichting.
  - Omdat het handelingsperspectief voor alle meldingen hetzelfde is, tonen we deze maar één keer.
  - We markeren alle invoervelden waar een foutmelding of waarschuwing op is. Gaat melding 1 over veld A, B en C, en melding 2 over veld C en D, dan markeren we dus A, B, C en D. Mocht er voor een invoerveld zowel een foutmelding als een waarschuwing zijn, dan wordt alleen de foutmelding markering getoond.

### Bijzonderheden
Voor het aantal kiesgerechtigden geven we een waarschuwing, nooit een fout. Dit is omdat het aantal kiesgerechtigden niet gecorrigeerd kan worden d.m.v. een corrigendum.

## Validatieregels geven fouten

Validatieregels vragen de gebruiker de invoer extra te controleren. Ze resulteren in een niet-blokkerende foutmelding. De foutmelding wordt getoond als de regel evalueert naar `TRUE`.

De foutmelding die wordt getoond bestaat uit vier onderdelen:

- titel
- nummer
- toelichting
- handelingsperspectief

Titel, nummer en toelichting zijn uniek voor iedere foutmelding. Het handelingsperspectief is voor alle meldingen gelijk, en is als volgt:

Invoerder (GSB CSO, GSB DSO, CSB; bij fouten):
> - Heb je iets niet goed overgenomen? Herstel de fout en ga verder.
> - Heb je alles gecontroleerd en komt je invoer overeen met het papier? Ga dan verder.

Coördinator (GSB CSO, GSB DSO; bij fouten)
> - Controleer of de invoer in Abacus goed is overgenomen van het papieren proces-verbaal.
> - Zit de fout ook in het papieren proces-verbaal? Los de fout dan daar op.

Voor sommige meldingen geldt een specifiek handelingsperspectief. Dit is vermeld met bulletpoints. In dat geval zal het standaard handelingsperspectief niet getoond worden.

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
| F.133 | 'Controles en correcties': Ongeldig antwoord in eerste zitting (vraag 'op verzoek van het CSB' is ingevuld)  |   | X |   |
| F.134 | 'Controles en correcties': meer dan 1 antwoord op vraag 'zijn er gecorrigeerde telresultaten'                |   | X |   |

#### F.101 'Alleen bij extra onderzoek B1-1': één van beide vragen is beantwoord, en de andere niet

> Invoerder (GSB CSO): **Controleer je antwoorden** (F.101)

> Coördinator (GSB CSO): **Beide vragen moeten beantwoord ofwel overgeslagen zijn** (F.101)  
> Als er extra onderzoek is gedaan, moeten beide vragen beantwoord worden.  
> Als er geen extra onderzoek is gedaan, moeten deze vragen overgeslagen worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.102 'Alleen bij extra onderzoek B1-1': meerdere antwoorden op 1 van de vragen

> Invoerder (GSB CSO): **Controleer je antwoorden** (F.102)

> Coördinator (GSB CSO): **Er mag maar één antwoord per vraag worden gegeven** (F.102)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.111 'Verschillen met telresultaten van het stembureau': één of beide vragen zijn niet beantwoord

> Invoerder (GSB CSO): **Controleer je antwoorden** (F.111)

> Coördinator (GSB CSO): **Bij beide vragen moet een antwoord gegeven worden** (F.111)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.112 'Verschillen met telresultaten van het stembureau': meerdere antwoorden per vraag

> Invoerder (GSB CSO): **Controleer je antwoorden** (F.112)

> Coördinator (GSB CSO): **Er mag maar één antwoord per vraag worden gegeven** (F.112)

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.121 Over het proces-verbaal: Niet alle vragen bij 'Over het proces-verbaal' zijn beantwoord

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.121)
> - Beantwoord de vragen over het papieren proces-verbaal.
> - Overleg met de coördinator als je twijfelt.

> Coördinator (GSB DSO): **Er is niet correct aangegeven welke documenten zijn ingevoerd** (F.121)
> - Bekijk welke documenten aanwezig zijn.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)
[Voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=20761-58052&t=gt3BuM41FB9Rkna7-11)

#### F.122 Over het proces-verbaal: Ongeldige combinatie van antwoorden: `wel corrigendum, geen inlegvel`

> Invoerder (GSB DSO): **Het inlegvel ontbreekt, maar hoort wel aanwezig te zijn** (F.122)
> - Overleg met de coördinator over het ontbrekende inlegvel.

> Coördinator (GSB DSO): **Het inlegvel ontbreekt, maar hoort wel aanwezig te zijn** (F.122)
> - Zorg dat een correct ingevuld inlegvel wordt toegevoegd.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.131 'Controles en correcties': geen vinkjes bij de eerste twee vragen

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.131)

> Coördinator (GSB DSO): **De vragen op het inlegvel zijn niet volledig beantwoord** (F.131)
> - Zorg dat het inlegvel volledig is ingevuld.
> - Geef daarna de invoer terug aan de invoerder zodat deze vraag opnieuw beantwoord kan worden.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.132 'Controles en correcties': Ongeldige set documenten (vraag 'gecorrigeerde telresultaten' = 'nee')

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.132)  
> Er is een corrigendum, maar er zijn volgens de antwoorden op het inlegvel 'controles en correcties' geen gecorrigeerde telresultaten.
> - Overleg met de coördinator.

> Coördinator (GSB DSO): **Onterecht corrigendum?** (F.132)  
> Er is een corrigendum, maar er zijn volgens de antwoorden op het inlegvel 'controles en correcties' geen gecorrigeerde telresultaten.
> - Als er geen gecorrigeerde telresultaten zijn, dan hoort er ook geen corrigendum te zijn.
> - Verwijder het corrigendum, of geef op het inlegvel aan dat er wel gecorrigeerde telresultaten zijn.
> - Geef daarna de invoer terug aan de invoerder.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.133 'Controles en correcties': Ongeldig antwoord in eerste zitting (vraag 'op verzoek van het CSB' is ingevuld)

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.133)

> Coördinator (GSB DSO): **Tijdens de eerste zitting kan er nog geen verzoek van het Centraal Stembureau zijn** (F.133)
> - Herstel de fout door op papier de juiste optie(s) aan te (laten) vinken.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.134 'Controles en correcties': meer dan 1 antwoord op vraag 'zijn er gecorrigeerde telresultaten'

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.134)

> Coördinator (GSB DSO): **Er mag maar 1 antwoord per vraag worden gegeven** (F.134)
> - Herstel de fout door op papier de juiste optie(s) aan te (laten) vinken.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

### Regels voor totalen (reeks F.2xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.201 | stempassen + volmachten <> totaal toegelaten kiezers                                                     | X | X | X |
| F.202 | E.1 t/m E.n tellen niet op naar E                                                                        | X | X | X |
| F.203 | stemmen op kandidaten + blanco stemmen + ongeldige stemmen <> totaal aantal uitgebrachte stemmen         | X | X | X |
| F.204 | De som van lijsttotalen (E.1 t/m E.n) is groter dan 0 en E = leeg of 0                                   | X | X | X |

#### F.201 `stempassen + volmachten <> totaal toegelaten kiezers`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer je antwoorden** (F.201)

> Coördinator (GSB CSO): **A en B tellen niet op tot D** (F.201)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als het juiste getal bij D wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij D het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **A en B tellen niet op tot D** (F.201)  
> Controleer in rubriek 2.3 of er een onverklaard verschil opgelost wordt als het juiste getal bij D wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij D het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **A en B tellen niet op tot D** (F.201)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: A, B en D

#### F.202 (Als F.204 niet getoond wordt) `E.1 t/m E.n tellen niet op naar E`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer je antwoorden** (F.202)

> Coördinator (GSB CSO): **De stemmen op lijsten tellen niet op tot E** (F.202)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en H worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en H de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **De stemmen op lijsten tellen niet op tot E** (F.202)  
> Controleer in rubriek 2.3 of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en H worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en H de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **De stemmen op lijsten tellen niet op tot E** (F.202)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: E.1 t/m E.n en E

#### F.203 (Als F.204 niet getoond wordt) `stemmen op kandidaten + blanco stemmen + ongeldige stemmen <> totaal aantal uitgebrachte stemmen`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer je antwoorden** (F.203)

> Coördinator (GSB CSO): **E, F en G tellen niet op tot H** (F.203)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als het juiste getal bij H wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij H het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **E, F en G tellen niet op tot H** (F.203)  
> Controleer in rubriek 2.3 of er een onverklaard verschil opgelost wordt als het juiste getal bij H wordt ingevuld.
> - Zo ja: herstel op papier de optelfout door bij H het juiste getal in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **E, F en G tellen niet op tot H** (F.203)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: E, F, G en H

#### F.204 `De som van lijsttotalen (E.1 t/m E.n) is groter dan 0 en E = leeg of 0`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer je antwoorden** (F.204)

> Coördinator (GSB CSO): **Het totaal aantal stemmen op kandidaten is niet ingevuld** (F.204)  
> Controleer in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting) of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en E.1 t/m E.n worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en E.1 t/m E.n de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **Het totaal aantal stemmen op kandidaten is niet ingevuld** (F.204)  
> Controleer in rubriek 2.3 of er een onverklaard verschil opgelost wordt als de juiste getallen bij E en E.1 t/m E.n worden ingevuld.
> - Zo ja: herstel op papier de optelfout door bij E en E.1 t/m E.n de juiste getallen in te vullen.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **Het totaal aantal stemmen op kandidaten is niet ingevuld** (F.204)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Veld markeren: E

### Regels voor verschillen (reeks F.3xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.301 | "Vergelijk D&H": (Als checkbox D=H is aangevinkt) `D<>H`                                                                        | X | X |   |
| F.302 | "Vergelijk D&H": (Als checkbox H>D is aangevinkt) `H<=D`                                                                        | X | X |   |
| F.303 | "Vergelijk D&H": (Als checkbox H<D is aangevinkt) `H>=D`                                                                        | X | X |   |
| F.304 | "Vergelijk D&H": Meerdere aangevinkt of geen enkele aangevinkt                                                                  | X | X |   |
| F.305 | (Als D = H) I en/of J zijn ingevuld                                                                                             | X | X |   |
| F.306 | (Als H > D) `I <> H - D`                                                                                                        | X | X |   |
| F.307 | (Als H > D) J is ingevuld                                                                                                       | X | X |   |
| F.308 | (Als H < D) `J <> D - H`                                                                                                        | X | X |   |
| F.309 | (Als H < D) I is ingevuld                                                                                                       | X | X |   |
| F.310 | (Als D <> H) Verklaring voor verschil niks aangevinkt of zowel 'ja' als 'nee' aangevinkt                                        | X | X |   |
| F.311 | 2.3.2 Verklaring voor verschil = nee en 'vanwege een onverklaard verschil' in stap 'controles en correcties' is niet aangevinkt |   | X |   |
| F.312 | totaal aantal kiezers <> totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen                     |   |   | X |

#### F.301 "Vergelijk D&H": (Als checkbox D=H is aangevinkt) `D<>H`

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.301)

> Coördinator (GSB CSO): **De getallen die zijn ingevuld bij D en H zijn niet gelijk** (F.301)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of er een onverklaard verschil ontstaat.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **De getallen die zijn ingevuld bij D en H zijn niet gelijk** (F.301)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of er een onverklaard verschil ontstaat.
> - Pas zo nodig rubriek 2.3.2 aan, en volg de instructies over hertellen die daar staan.

Veld markeren: foutmelding op 3.3.1 (CSO) of 2.3.1 (DSO) "Vergelijk D en H"

#### F.302 "Vergelijk D&H": (Als checkbox H>D is aangevinkt) `H<=D`

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.302)

> Coördinator (GSB CSO): **Het getal dat is ingevuld bij H is niet groter dan D** (F.302)

> Coördinator (GSB DSO): **Het getal dat is ingevuld bij H is niet groter dan D** (F.302)
> - Maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 3.3.1 (CSO) of 2.3.1 (DSO) "Vergelijk D en H"

#### F.303 "Vergelijk D&H": (Als checkbox H<D is aangevinkt) `H>=D`

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.303)

> Coördinator (GSB CSO): **Het getal dat is ingevuld bij H is niet kleiner dan D** (F.303)

> Coördinator (GSB DSO): **Het getal dat is ingevuld bij H is niet kleiner dan D** (F.303)
> - Maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 3.3.1 (CSO) of 2.3.1 (DSO) "Vergelijk D en H"

#### F.304 "Vergelijk D&H": Meerdere aangevinkt of geen enkele aangevinkt

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.304)

> Coördinator (GSB CSO): **Deze vraag moet precies één antwoord hebben** (F.304)

> Coördinator (GSB DSO): **Deze vraag moet precies één antwoord hebben** (F.304)  
> Is op het proces-verbaal duidelijk aangegeven welk van de opties bedoeld is?
> - Zo ja: laat dat dan overnemen in Abacus.
> - Zo nee: maak een corrigendum waarin de juiste optie geselecteerd wordt.

Veld markeren: foutmelding op 3.3.1 (CSO) of 2.3.1 (DSO) "Vergelijk D en H"

#### F.305 (Als D = H) I en/of J zijn ingevuld
> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.305)

> Coördinator (GSB CSO): **Controleer I en J** (F.305)  
> De getallen bij D en H zijn gelijk. Er zijn geen stemmen meer of minder geteld.
> - Herstel de fout door op papier I en/of J leeg te (laten) maken.

> Coördinator (GSB DSO): **Controleer I en J** (F.305)  
> De getallen bij D en H zijn gelijk. Er zijn geen stemmen meer of minder geteld.
> - Corrigeer de rekenfout door een corrigendum te (laten) maken waarop I en/of J leeg zijn.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I en/of J (als ingevuld)

#### F.306 (Als H > D) `I <> H - D`

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.306)

> Coördinator (GSB CSO): **Controleer aantal méér getelde stemmen (I)** (F.306)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **Controleer aantal méér getelde stemmen (I)** (F.306)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I

#### F.307 (Als H > D) J is ingevuld

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.307)

> Coördinator (GSB CSO): **Controleer of I en J verwisseld zijn** (F.307)
> - Herstel de fout door op papier het verschil op de juiste plek in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **Controleer of I en J verwisseld zijn** (F.307)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I, J

#### F.308 (Als H < D) `J <> D - H`
> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.308)

> Coördinator (GSB CSO): **Controleer aantal minder getelde stemmen (J)** (F.308)
> - Herstel de fout door op papier het juiste getal in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **Controleer aantal minder getelde stemmen (J)** (F.308)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: J

#### F.309 (Als H < D) I is ingevuld
> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.309)

> Coördinator (GSB CSO): **Controleer of I en J verwisseld zijn** (F.309)
> - Herstel de fout door op papier het verschil op de juiste plek in te (laten) vullen.
> - Controleer ook of het verschil nog volledig verklaard is.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **Controleer of I en J verwisseld zijn** (F.309)
> - Corrigeer de rekenfout in een corrigendum.
> - Kijk ook of het corrigeren van de fout een onverklaard verschil introduceert (zie 2.3.2).
> - Hertel dan de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op het corrigendum in.

Veld markeren: I, J

#### F.310 (Als D <> H) Verklaring voor verschil niks aangevinkt of zowel 'ja' als 'nee' aangevinkt

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (F.310)

> Coördinator (GSB CSO, GSB DSO): **Deze vraag moet precies één antwoord hebben** (F.310)

Veld markeren: foutmelding op 3.3.2 (CSO) of 2.3.2 (DSO)

#### F.311 2.3.2 Verklaring voor verschil = nee en 'vanwege een onverklaard verschil' in stap 'controles en correcties' is niet aangevinkt

> Invoerder (GSB DSO): **Controleer je antwoorden** (F.311)

> Coördinator (GSB DSO): **Hertel onverklaard verschil** (F.311)  
> Er is een onverklaard verschil dat herteld moet worden.
> - Hertel de stembiljetten en het aantal toegelaten kiezers. Hertel tot de fout gevonden is, of alles één keer herteld is.
> - Vul nieuwe telresultaten op een corrigendum in.
> - Is er al herteld? Zorg dan dat het inlegvel 'controles en correcties' wordt ingevuld en toegevoegd aan het proces-verbaal van het stembureau.

Veld markeren: foutmelding op 2.3.2

#### F.312 `totaal aantal kiezers <> totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen`

> Invoerder (CSB): **Controleer je antwoorden** (F.312)

> Coördinator (CSB): **D is niet gelijk aan H min I plus J** (F.312)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: I en J

### Regels voor kandidaten en lijsttotalen (reeks F.4xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.401 | `Er zijn (stemmen op kandidaten of het lijsttotaal van corresponderende E.x is groter dan 0) en het totaal aantal stemmen op een lijst = leeg of 0` | X | X | X |
| F.402 | (Als F.401 niet getoond wordt) `Totaal aantal stemmen op een lijst <> som van aantal stemmen op de kandidaten van die lijst`                        | X | X | X |
| F.403 | (Als F.401 niet getoond wordt) `Totaal aantal stemmen op een lijst komt niet overeen met het lijsttotaal van corresponderende E.x`                  | X | X | X |

#### F.401 `Er zijn (stemmen op kandidaten of het lijsttotaal van corresponderende E.x is groter dan 0) en het totaal aantal stemmen op een lijst = leeg of 0`
> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer het totaal van de lijst. Is dit veld op het papieren proces-verbaal ook leeg? Dan kan je verdergaan** (F.401)

> Coördinator (GSB CSO): **Het totaal van de lijst is niet ingevuld** (F.401)  
> Controleer of het proces-verbaal tijdens het telproces volledig is ingevuld (controleer ook E.{x} in rubriek 3.2 (eerste zitting) of 2.2 (volgende zitting)).  
> Kijk of het corrigeren van de fout een onverklaard verschil wegneemt in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting).
> - Zo ja: corrigeer de optelfout op het papieren proces-verbaal.
> - Zo nee: onderzoek wat er fout is gegaan en tel zo nodig de stembiljetten en het aantal toegelaten kiezers opnieuw. Begin bij deze lijst, en hertel tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **Het totaal van de lijst is niet ingevuld** (F.401)  
> Kijk of het corrigeren van de fout een onverklaard verschil in rubriek 2.3 wegneemt.
> - Zo ja: maak een corrigendum en corrigeer daarin de optelfout. Corrigeer ook rubriek 2.3 in het corrigendum.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw. Begin bij deze lijst, en hertel tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **Het totaal van de lijst is niet ingevuld** (F.401)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: totaal van de lijst
N.b. anders dan de andere foutmeldingen, tonen we deze foutmelding _bij invoerders_ onderaan de pagina, onder het totaal-veld ([Voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=6128-28260&t=R2mG7PyAWfHk3c8S-11))  
Het standaard handelingsperspectief wordt bij deze foutmelding niet getoond.

#### F.402 (Als F.401 niet getoond wordt) `Totaal aantal stemmen op een lijst <> som van aantal stemmen op de kandidaten van die lijst`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer ingevoerde aantallen** (F.402)  
> De opgetelde stemmen op de kandidaten en het ingevoerde totaal zijn niet gelijk.

> Coördinator (GSB CSO): **De stemmen op kandidaten tellen niet op tot het lijsttotaal** (F.402)  
> Controleer of het proces-verbaal tijdens het telproces volledig is ingevuld.  
> Reken de optelling in het papieren proces-verbaal na.  
> Kijk of het corrigeren van de fout een onverklaard verschil wegneemt in rubriek 3.3 (eerste zitting) of 2.3 (volgende zitting).
> - Zo ja: corrigeer de optelfout op het papieren proces-verbaal.
> - Zo nee: onderzoek wat er fout is gegaan en tel zo nodig de stembiljetten en het aantal toegelaten kiezers opnieuw. Begin bij deze lijst, en hertel tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (GSB DSO): **De stemmen op kandidaten tellen niet op tot het lijsttotaal** (F.402)  
> Reken de optelling in het papieren proces-verbaal na.  
> Kijk of het corrigeren van de fout een onverklaard verschil in rubriek 2.3 wegneemt.
> - Zo ja: maak een corrigendum en corrigeer daarin de optelfout. Corrigeer ook rubriek 2.3 in het corrigendum.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw. Begin bij deze lijst, en hertel tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **De stemmen op kandidaten tellen niet op tot het lijsttotaal** (F.402)  
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: geen (laat alleen foutmelding zien op de pagina)

#### F.403 (Als F.401 niet getoond wordt) `Totaal aantal stemmen op een lijst komt niet overeen met het lijsttotaal van corresponderende E.x`

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer het totaal van de lijst** (F.403)  
> Als het totaal overeenkomt met het papieren proces-verbaal, controleer dan ook de waarde bij E.{x} bij [Aantal kiezers en stemmen]().

> Coördinator (GSB CSO): **Controleer het totaal van de lijst en E.{x} in rubriek 3.2 (eerste zitting) of 2.2 (volgende zitting)** (F.403)
> - Controleer wat er fout is gegaan in rubriek 3.2 (eerste zitting) of 2.2 (volgende zitting) en herstel de fout.
> - Pas zo nodig rubriek 3.3.2 (eerste zitting) of 2.3.2 (volgende zitting) aan, en volg de instructies over hertellen die daar staan.

> Coördinator (GSB DSO): **Controleer het totaal van de lijst en E.{x} in rubriek 2.2** (F.403)  
> Kijk of het corrigeren van de fout een onverklaard verschil in rubriek 2.3 wegneemt.
> - Zo ja: maak een corrigendum en corrigeer daarin de optelfout. Corrigeer ook rubriek 2.3 in het corrigendum.
> - Zo nee: tel de stembiljetten en het aantal toegelaten kiezers opnieuw. Begin bij deze lijst, en hertel tot de fout gevonden is, of alles één keer herteld is.

> Coördinator (CSB): **Controleer het totaal van de lijst en E.{x} in rubriek 2.2** (F.403)
> Je kan niet verder met dit proces-verbaal. Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Velden markeren: totaal van de lijst

---

## Plausibiliteitschecks geven waarschuwingen

Plausibiliteitschecks vragen de gebruiker de invoer extra te controleren. Ze resulteren in een niet-blokkerende waarschuwing. De waarschuwing wordt getoond als de check evalueert naar `TRUE`.

De foutmelding die wordt getoond bestaat uit dezelfde onderdelen als bij de validatieregels. Het handelingsperspectief voor alle plausibiliteitschecks is als volgt:

Invoerder (GSB CSO, GSB DSO, CSB; bij waarschuwingen):
> - Heb je iets niet goed overgenomen? Herstel de fout en ga verder.
> - Heb je alles gecontroleerd en komt je invoer overeen met het papier? Ga dan verder.

Coördinator (GSB CSO, GSB DSO; bij fouten)
> Er is geen standaard handelingsperspectief voor de coördinator.

### Checks voor alle velden (reeks W.0xx)

| code  | check | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| W.001 | (Bij tweede invoer) Niet alle ingevoerde waardes van de tweede invoer zijn gelijk aan die van de eerste invoer | X | X | X |

#### W.001 (Bij tweede invoer) Niet alle ingevoerde waardes van de tweede invoer zijn gelijk aan die van de eerste invoer

> Invoerder (GSB CSO, GSB DSO, CSB): **Extra controle nodig** (W.001)  
> De gemarkeerde velden zijn anders dan in de eerste invoer.

> Coördinator (GSB CSO, GSB DSO, CSB): W.001 is er alleen voor invoerders
> Voor de coördinator hebben we het scherm 'verschillen oplossen'.

Velden markeren: alle velden met een verschil

[Voorbeeld in Figma](https://www.figma.com/design/zZlFr8tYiRyp4I26sh6eqp/Kiesraad---Abacus-optelsoftware?node-id=130-10813&t=zTY4ajWtsFkiTOYP-11)

### Checks voor extra onderzoek en controles (reeks W.1xx)

Geen checks.

### Checks voor totalen (reeks W.2xx)

| code  | check | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| W.201 | Aantal blanco stemmen is groter dan of gelijk aan 3% van het totaal aantal uitgebrachte stemmen                                                      | X | X |   |
| W.202 | Aantal ongeldige stemmen is groter dan of gelijk aan 3% van het totaal aantal uitgebrachte stemmen                                                   | X | X |   |
| W.203 | Verschil tussen totaal aantal toegelaten kiezers en totaal aantal uitgebrachte stemmen is groter dan of gelijk aan 2% en groter dan of gelijk aan 15 | X | X |   |
| W.204 | Totaal aantal uitgebrachte stemmen leeg of 0                                                                                                         | X | X | X |
| W.205 | Aantal kiesgerechtigden = leeg of 0                                                                                                                  |   |   | X |
| W.206 | Aantal kiesgerechtigden is kleiner dan aantal stempassen                                                                                             |   |   | X |

#### W.201 aantal blanco stemmen is groter dan of gelijk aan 3% van het totaal aantal uitgebrachte stemmen

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (W.201)

> Coördinator (GSB CSO, GSB DSO): **Het aantal blanco stemmen (F) is erg hoog** (W.201)
> - Hertel de blanco stemmen of geef een verklaring voor het hoge aantal.
> - Geef in elk geval aan wat je hebt gedaan in het proces-verbaal van het GSB (rubriek 1.2).

Veld markeren: F

#### W.202 Aantal ongeldige stemmen is groter dan of gelijk aan 3% van het totaal aantal uitgebrachte stemmen

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (W.202)

> Coördinator (GSB CSO, GSB DSO): **Het aantal ongeldige stemmen (G) is erg hoog** (W.202)
> - Hertel de ongeldige stemmen of geef een verklaring voor het hoge aantal.
> - Geef in elk geval aan wat je hebt gedaan in het proces-verbaal van het GSB (rubriek 1.2).

Veld markeren: G

#### W.203 Verschil tussen totaal aantal toegelaten kiezers en totaal aantal uitgebrachte stemmen is groter dan of gelijk aan 2% en groter dan of gelijk aan 15

- 2% of meer: abs(toegelaten kiezers - uitgebrachte stemmen) / uitgebrachte stemmen \>= 0.02
- 15 of meer: abs(toegelaten kiezers - uitgebrachte stemmen) \>= 15

_N.B. Voor "2% of meer" delen we door uitgebrachte stemmen, consistent met de berekening van W.201 (blanco stemmen) en W.202 (ongeldige stemmen). Het is dus niet nodig de 2% ook te berekenen door te delen door toegelaten kiezers._

> Invoerder (GSB CSO, GSB DSO): **Controleer je antwoorden** (W.203)

> Coördinator (GSB CSO, GSB DSO): **Groot verschil tussen D en H** (W.203)  
> Er is een groot verschil tussen het aantal toegelaten kiezers (D) en het aantal uitgebrachte stemmen (H).
> - Tel het stembureau in zijn geheel nogmaals. Dit hoeft niet als er al twee keer geteld is met precies dezelfde uitkomst per lijst.
> - Verklaar in het proces-verbaal van het GSB (rubriek 1.2) zo goed mogelijk wat de oorzaak van de opmerkelijke uitkomst is.
> - Schrijf ook op welke stappen het GSB heeft gezet om deze te hertellen en onderzoeken.

Velden markeren: D en H

#### W.204 Totaal aantal uitgebrachte stemmen leeg of 0

> Invoerder (GSB CSO, GSB DSO, CSB): **Controleer je antwoorden** (W.204)

> Coördinator  (GSB CSO, GSB DSO): **Het totaal aantal uitgebrachte stemmen (H) is nul** (W.204)  
> Controleer of het stembureau is opgenomen in de vóór de verkiezing gepubliceerde lijst.
> - Zo ja: verklaar in het proces-verbaal van het GSB (rubriek 1.2) waarom in dit stembureau geen stemmen zijn uitgebracht.
> - Zo nee: verwijder het stembureau uit Abacus. Het proces-verbaal moet niet ingevoerd worden.

> Coördinator (CSB): **Het totaal aantal uitgebrachte stemmen (H) is nul** (W.204)  
> Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Veld markeren: H

#### W.205 `Aantal kiesgerechtigden = leeg of 0`

> Invoerder (CSB): **Controleer je antwoorden** (W.205)

> Coördinator (CSB): **Het aantal kiesgerechtigden (Z) is niet ingevuld** (W.205)  
> Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Veld markeren: Z

#### W.206 (Als W.205 niet getoond wordt) `Aantal kiesgerechtigden is kleiner dan aantal stempassen`

> Invoerder (CSB): **Controleer je antwoorden** (W.206)

> Coördinator (CSB): **Het aantal kiesgerechtigden (Z) is kleiner dan het aantal stempassen (A)** (W.206)  
> Controleer of er iets is misgegaan bij het opmaken of overdragen van het proces-verbaal van het onderliggende niveau.  
> Blijft de fout? Overleg dan met het CSB over de vervolgstappen.

Veld markeren: Z

### Checks voor verschillen (reeks W.3xx)

Geen checks.

### Checks voor kandidaten en lijsttotalen (reeks W.4xx)

Geen checks.
