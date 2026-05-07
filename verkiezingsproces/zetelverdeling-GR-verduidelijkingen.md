# Verduidelijkingen zetelverdeling

## Was als het totaal aantal geldige stemmen 0 is?

Dit is niet expliciet in de wet geregeld. Voorkeursoplossing is een error teruggeven.

OSV2020 geeft in dit geval een zetelverdeling waarin 0 zetels worden toegewezen. In dat opzicht kun je dit geval ook zien als een variant op de situatie waarin er onvoldoende verkozen kandidaten zijn om alle zetels toe te kunnen wijzen.

## Wat als er minder kandidaten zijn dan zetels?

Dan moeten alle kandidaten benoemd worden en is er geen volledige gemeenteraad. Als minder dan de helft van de zetels gevuld kunnen worden, komt er een nieuwe verkiezing (maar dat is buiten beschouwing van onze software). Een alternatieve oplossing, is het geven van een error, zodat het buiten abacus geregeld kan worden. Deze situatie is namelijk niet specifiek in de wet geregeld.

## Is de volgorde relevant voor loting bij gelijke overschotten, gemiddelden of voorkeurstemmen?

Als voor verdeling van restzetels lijsten een gelijk overschot of gemiddelde hebben, dan bepaalt het lot. Het is mogelijk dat er meer lijsten met een gelijk overschot of gemiddelde zijn, dan dat er beschikbare zetels zijn. Een gelijkaardige situatie kan zich voordoen bij een gelijk aantal voorkeurstemmen tijdens het aanwijzen van de kandidaten.

De volgorde van het aanwijzen maakt hier uit. Het PV moet melding maken van de loting en de resultaten van de loting. Dit betekent dat het van belang is om te weten welke restzetel naar welke lijst is gegaan. Dit geldt ook voor de weergave van de loting waar de zetels aan kandidaten worden toegewezen. Bij kandidaten is het daarnaast ook van belang voor de rangschikking, aangezien kandidaten niet samen één plek kunnen delen. Degene die eerst een zetel krijgt, komt boven de andere kandidaat in de rangschikking te staan. Dit is belangrijk voor eventuele tussentijdse benoemingen.

De resultaten van deze lotingen kunnen wel op hetzelfde scherm ingevoerd worden.

## Wat als je op basis van art. P 9 (volstrekte meerderheid) een zetel weg moet halen bij de partij met de volstrekte meerderheid aan stemmen?

Deze situatie kan niet voorkomen. Als je de volstrekte meerderheid aan stemmen hebt, kun je nooit twee zetels tekort komen voor de volstrekte meerderheid aan zetels. Dus ofwel heeft de partij met de volstrekte meerderheid aan stemmen een restzetel gekregen en daarmee een volstrekte meerderheid aan zetels, ofwel haalt P9 een restzetel weg van een andere partij om die aan de partij met de volstrekte meerderheid aan stemmen te geven.

## Op welk punt mogen we overleden kandidaten buiten beschouwing laten?

Overleden kandidaten moet meegenomen worden voor lijstuitputting (art. P 10) wordt verwerkt. Dus na het toepassen van art. P 9 (volstrekte meerderheid).

## Op welk punt moeten we lijstuitputting toepassen?

De wet schrijft voor dat lijstuitputting onderdeel is van zetelverdeling, dus vóór het aanwijzen van kandidaten.

Dit betekent ook dat bij lijstuitputting, de applicatie terug moet gaan naar de toekenning van de zetel waar de lijstuitputting voor wordt vastgesteld tijdens de aanwijzing van de kandidaten. Vanaf dat punt moet de applicatie dan de zetelverdeling opnieuw berekenen. Let wel: dit komt (vrijwel?) nooit voor. Realistischer scenario is lijstuitputting nadat kandidaten hun zetel weigeren.

## Wanneer mogen we lijsten uitsluiten die geen vrije kandidaten hebben?

Dit mag bij het herverdelen van zetels o.b.v. lijstuitputting. Artikel P 10 zegt ook "[...] gaan de overblijvende zetel of zetels door voortgezette toepassing van die bepalingen over op één of meer van de overige lijsten, waarop kandidaten voorkomen aan wie geen zetel is toegewezen." Voorwaarde is wel dat dat Abacus duidelijk aangeeft waarom Abacus bepaalde lijsten heeft uitgesloten.

Dus na het toepassen van art. P  9 (volstrekte meerderheid) en het buiten beschouwing laten van overleden kandidaten, worden zetels waarvoor een lijst geen kandidaat heeft, weggehaald. Die zetels worden herverdeeld waarbij lijsten waarvan het aantal kandidaten gelijk is aan het aantal toegewezen zetels worden uitgesloten.

## Hoe werkt lijstuitputting in combinatie met art. P 9 (volstrekte meerderheid)?

In principe maakt het niet uit hoe de lijstuitputting ontstaat, je keert altijd terug naar de situatie zoals die 'net voor' de lijstuitputting was.

Dus als lijst A de laatste restzetel heeft gekregen, maar lijst B een volstrekte meerderheid aan stemmen maar niet aan zetels heeft, dan wordt de laatste restzetel weggehaald bij lijst A en toegekend aan lijst B. Als dat tot lijstuitputting bij lijst B leidt, dan herverdeel je de vrijgekomen zetels vanaf het moment van lijstuitputting. De laatste restzetel komt daarmee bij lijst A o.b.v. dezelfde berekening als waarmee die zetel eerder aan lijst A was toegekend.

Omdat artikel P 10 bewust achter artikel P 9 is gezet, mogen we niet al bij de toepassing van artikel P 9 controleren op lijstuitputting voor de lijst met de volstrekte meerderheid aan stemmen.

Wat betreft het proces-verbaal hoort dan in de tabel komen te staan dat de laatste restzetel aan lijst A is toegekend, waarbij onder de tabel de uitleg in een regel wordt beschreven, namelijk dat P 9 is toegepast, maar tot lijstuitputting heeft geleid, waardoor de restzetel alsnog naar lijst A is gegaan.

## Kan een lijst een negatief overschot hebben?

Nee, voor de berekening van het overschot wordt het aantal stemmen gedeeld door de kiesdeler, zoals wordt besproken in Bijlage 2 van [dit Kamerstuk](https://zoek.officielebekendmakingen.nl/kst-34377-3.html). Of anders gezegd: het stemtotaal van de lijst verminderd met de kiesdeler maal het
aantal volle zetels van de lijst.

Een zetel toegekend o.b.v. artikel P 9 wordt dus niet meegenomen in de berekening van het overschot. Daarmee is er geen scenario mogelijk waarin een lijst een negatief overschot heeft.

### Kan een lijst die een zetel heeft gekregen o.b.v. P 9 extra zetels krijgen vanwege lijstuitputting?

Ja, dat kan. P 9 wordt toegepast om bij de 'originele' zetelverdeling in het kader van evenredigheid recht te doen aan het gegeven dat die lijst een meerderheid van de stemmen heeft, maar niet een meerderheid van de zetels. Het doel hiervan is om de verdeling van de zetels zoveel mogelijk te laten aansluiten bij de verdeling van de stemmen. Wanneer vervolgens blijkt dat een lijst niet voldoende kandidaten heeft om alle toegewezen zetels te vullen, dan moet er worden gekeken naar een nieuwe verdeling, waarbij het doel is gewisseld van 'evenredigheid' naar 'compleetheid van de gemeenteraad bij aanvang'. De wetgever wijst de verdeling van de restzetels aan als te volgen methode. Als dit ertoe leidt dat de grootste partij nog een zetel hoort te krijgen, omdat zij volgens de restzetelverdeling in aanmerking komen, dan is dat het gevolg. Dat in een eerder stadium P 9 is toegepast, maakt dan niet uit. In deze situatie zou dat dus betekenen dat de meerderheidspartij zowel via P 9 als via P 10 een zetel krijgt.

### Mogen we eerst de kandidatenlijsten rangschikken en daarna de aanwijzing van de gekozen kandidaten doen?

Nee, volgens de wet moet het rangschikken echt als laatste gebeuren.
