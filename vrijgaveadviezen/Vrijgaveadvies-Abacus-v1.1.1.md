# Vrijgaveadvies Abacus v1.1.1

## Inhoudsopgave

- Advies
- Beperkingen Abacus
- Terugvaloptie
- Uitgevoerde testwerkzaamheden
- Aandachts- en verbeterpunten testproces


## Advies

TODO als alle andere TODOs zijn gedaan

scope gebruik: Herindelingsverkiezing Hilversum-Wijdemeren 2026


## Beperkingen Abacus

### Twee keer handmatig invoeren door CSB

Abacus laat niet toe om de eerste invoer van de resultaten van het GSB te importeren d.m.v. een EML-bestand. Beide invoeren moeten dus handmatig gebeuren. In de volgende release van Abacus zal deze import-mogelijkheid wel beschikbaar zijn.

### Strengere interpretatie vierogenpricipe
De implementatie van het vierogenprincipe bij invoer is strenger in Abacus dan in OSV2020-U. Als de eerste en tweede invoer van tellingen niet gelijk zijn, dan moet in Abacus de foutieve invoer volledig opnieuw gedaan worden. Dit creëert extra werk ten opzichte van gebruik van OSV2020-U, waarin als één van de twee invoeren correct zijn, het mogelijk is die invoer als de definitieve invoer aan te duiden.

Dit is gevolg van een ontwerpkeuze in Abacus, die ondertussen herzien is. De implementatie van het nieuwe ontwerp zal beschikbaar zijn in de volgende release van Abacus.

### Beperkte invoermogelijkheid tekstvelden processen-verbaal
Er zijn gedeeltes van de processen-verbaal die in Abacus ingevoerd zouden kunnen worden, maar waarvoor dat nog niet mogelijk is. Een voorbeeld hiervan is de presentielijst. Gevolg is dat gemeenten deze gedeeltes buiten Abacus om in moeten vullen.

### Geen benoemings- en geloofsbrieven
Voor Abacus is de ontwerpkeuze gemaakt om de applicatie geen benoemings- en geloofsbrieven te laten genereren. Dit is iets dat OSV2020-U wel doet. Deze keuze is afgestemd met de gemeente Hilversum.


## Terugvaloptie

De gemeente Hilversum heeft tijdens de GSB- en CSB-zittingen ter plaatse uitgebreide ondersteuning vanuit de Kiesraad. Bij eventuele calamiteiten bij het gebruik van Abacus zullen zij de gemeente bijstaan bij het oplossen van deze problemen, of indien nodig bij het overschakelen op een fallback optie. Hiervoor is OSV2020-U beschikbaar.


## Uitgevoerde testwerkzaamheden

### Relevante kwaliteitsattributen

In het ["Testen en kwaliteit"](https://github.com/kiesraad/abacus/blob/a1d4bf958a1038be5ea6e002f17fc800a67d45bb/documentatie/ontwikkelproces/testen-en-kwaliteit.md)-document staan de belangrijkste kwaliteitsattributen voor Abacus. Deze vallen uiteen in twee groepen: externe en interne kwaliteitsattributen. Externe kwaliteitsattributen zijn attributen waar gebruikers direct iets van merken. Interne kwaliteitsattributen zijn attributen die vooral impact hebben op het ontwikkelteam.

In de beschrijving hieronder van de uitgevoerde testwerkzaamheden wordt vooral aandacht gegeven aan de tests die raken aan de externe kwaliteitsattributen:
- Betrouwbaarheid: kun je de software in de meeste situaties vertrouwen?
- Bruikbaarheid: is de software makkelijk te gebruiken? (voor alle bedoelde gebruikers, dus ook installatie, controleerbaar door burger, etc.)
- Beveiliging: biedt de software voldoende bescherming tegen ongewenst gebruik?

Deze zijn namelijk het belangrijkst voor de beslissing of Abacus v1.1.1 goed genoeg is voor de beperkte uitrol.


### Testwerkzaamheden tijdens ontwikkeling

Tijdens de ontwikkeling werd er continu getest:

- review met "approval" van minstens twee teamleden
- [linting en geautomatiseerde tests op meerdere niveaus](https://github.com/kiesraad/abacus-documentatie/blob/1c2e47bca15e20d9cf9f748b481e2ea384d9b265/ontwikkelproces/test-tooling.md) in onze ["Build, lint & test"-pipeline](https://github.com/kiesraad/abacus/actions/workflows/build-lint-test.yml)
- exploratief testen

Om de ondersteuning van verschillende besturingssystemen te testen, draait er een [wekelijkse release-pipeline](https://github.com/kiesraad/abacus/actions/workflows/weekly-e2e-tests.yml). Hierin werd de applicatie gedraaid op Windows en Linux en de end-to-end tests op Chrome en Firefox voor beide besturingssystemen. Als aanvulling hierop wordt er binnen het team gebruik gemaakt van verschillende besturingssystemen en browsers. Tot slot bouwt deze pipeline sinds begin augustus ook de Windows installer.

Om de gebruiksvriendelijkheid en aansluiting op het proces te valideren, waren er regelmatig demo's met stakeholders en met de vaste gebruikersgroep.

### Testwerkzaamheden specifiek voor de release

#### Exploratief testen

Het team heeft op twee momenten de nodige sessies exploratief testen uitgevoerd. De [eerste reeks](https://github.com/kiesraad/abacus/issues/3047) in mei/begin juni toen het mogelijk was de volledige CSB-zitting te doorlopen, maar nog niet alle varianten van zetelverdeling waren geïmplementeerd. De [tweede reeks](https://github.com/kiesraad/abacus/issues/3057) in juli 2026, nadat zetelverdeling ook volledig was geïmplementeerd.

Tijdens deze sessies werden zowel de functionaliteit voor het GSB als het CSB getest. Voor het GSB lag de nadruk op vaststellen dat we geen regressies hadden geïntroduceerd. Voor het CSN lag de nadruk op vaststellen dat Abacus deze zitting goed ondersteunt.

#### Zetelverdeling

Het berekenen van de zetelverdeling en de aanwijzing van de gekozen kandidaten is complex. Deze berekening gebeurt in een aparte module van Abacus, die daarom ook de nodige [extra aandacht](https://github.com/kiesraad/abacus/issues/3361) heeft gekregen.

We hebben uitgebreide geautomatiseerde tests gebouwd voor zetelverdeling. De testdekking is meer dan 95%. Deze dekking is gevalideerd door middel van mutation testing en een extra review.

Daarnaast maken we gebruik van fuzz testing. Hierin worden voor willekeurig gegenereerde teluitslagen de zetelverdeling berekend. Ten eerste hebben we tests die de eigenschappen van de zetelverdeling controleren, bijv. geen enkele lijst heeft meer zetels dan het aantal kandidaten op de lijst. Ten tweede hebben we een test die voor dezelfde teluitslag het resultaat van Abacus met dat van OSV2020-U vergelijkt.

Tot slot hebben we Abacus de zetelverdeling van alle gemeentes van GR26 laten berekenen en die vergeleken met de daadwerkelijk uitslag zoals bepaald door OSV2020-U.

#### Ketentest

We hebben een verkiezingsdefinitie en kandidatenlijsten gegenereerd met OSV2020-KS in Abacus geladen en een CSB-zitting doorlopen. Hetzelfde is met OSV2020-U gedaan. Dit gaf ons de mogelijkheid de output-documenten van beide met elkaar te vergelijken.

We hebben ook de verschillende output-bestanden (GSB eerste zitting, GSB volgende zitting, CSB) ge-upload naar de acceptatie-omgeving van het Platform Teluitslagen.


### Beveiligingsonderzoek

TODO als rapport beschikbaar is


### Wettelijke toets

TODO als rapport beschikbaar is


## Aandachts- en verbeterpunten testproces

Naar aanleiding van de aandachts- en verbeterpunten van de vorige release hebben we regelmatiger exploratief getest. We hebben ook een feature freeze ingesteld aan het einde van de ontwikkelperiode, waardoor we minder overlap hadden tussen ontwikkeling en het release-testen. Beide hebben geholpen om iets meer rust te hebben in het team tegen het moment van oplevering voor het beveiligingsonderzoek en de wettelijke toets.
