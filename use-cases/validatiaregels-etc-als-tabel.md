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
