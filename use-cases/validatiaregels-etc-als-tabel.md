# Validatieregels en plausibiliteitschecks voor invoer tellingen

__Dit overzicht is niet volledig. Het is een voorstel voor het gebruik van tabellen voor de regels en checks.__

## Validatieregels geven fouten

### Regels voor totalen (reeks F.2xx)

| code  | regel | GSB CSO | GSB DSO | CSB |
| ----- | ----- | :-----: | :-----: | :-: |
| F.201 | stempassen + volmachten <> totaal toegelaten kiezers                                                       | X | X |   |
| F.202 | E.1 t/m E.n tellen niet op naar E                                                                          | X | X |   |
| F.203 | stemmen op kandidaten + blanco stemmen + ongeldige stemmen <> totaal aantal uitgebrachte stemmen           | X | X |   |
| F.204 | De som van lijsttotalen (E.1 t/m E.n) is groter dan 0 en (E = leeg of 0)                                   | X | X | X |
| F.205 | totaal aantal kiezers = totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen |   |   | X |

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


#### F.205: `totaal aantal kiezers = totaal aantal uitgebrachte stemmen - meer getelde stemmen + minder getelde stemmen`

> Invoerder: **Controleer je antwoorden** (F.204)

> Coördinator: **D is niet gelijk aan H min I plus J** (F.204)  
> Controleer of de juiste getallen zijn overgenomen. Indien de optelling niet klopt kun je niet verder gaan met de invoer. Er is iets misgegaan met het opmaken of overdragen van het procesverbaal van het onderliggende niveau. Overleg met het CSB over de vervolgstappen.

Velden markeren: D, H, I en J
