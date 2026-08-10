# Evaluatie Abacus tijdens GR26

Abacus is tijdens GR26 gebruikt bij 14 gemeenten. Het [evaluatieadvies van de gemeenteraadsverkiezingen](https://www.kiesraad.nl/documenten/2026/07/03/evaluatieadvies-gemeenteraadsverkiezingen-2026) bevat een paragraaf over Abacus: 

```
Afgelopen gemeenteraadsverkiezing hebben 14 gemeenten met een centrale stemopneming de invoer van het gsb
uitgevoerd met Abacus. De gemeenten hebben het gebruik van Abacus als heel positief ervaren. Er hebben
zich bij deze gedeeltelijke introductie geen problemen voorgedaan. De Kiesraad neemt de verbeterpunten
mee in de verdere ontwikkeling van de software. 
```

Het doel van dit document is een terugblik op het gebruik van Abacus en een inventarisatie van de mogelijke verbeterpunten. Het is geschreven vanuit het perspectief van het ontwikkelteam.

## Opzet evaluatie 

Het doel van de inzet van Abacus tijdens de gemeenteraadsverkiezingen was het op kleine schaal toepassen van de software, om zo ervaring op te doen en te leren. 

Door bij 14 gemeenten, van klein tot groot, de software te gebruiken is er de kans om goed te leren en alle keuzes die in het ontwerp- en bouwproces zijn gemaakt nogmaals te toetsen. 

De informatie voor de evaluatie komt uit drie bronnen: 

* Observaties van het Abacus-team tijdens gebruik
* Focusgroep gericht op Abacus
* Vragen in de vragenlijst

Daarnaast is er input ontvangen vanuit de NVVB, in de vorm van [een brief aan de minister](https://nvvb.nl/media/filer_public/ea/f7/eaf7b771-bef1-4393-aab8-4a706161872d/evaluatie_nvvb_def.pdf). Ook hierin werden suggesties gedaan voor het vervolg. De brief is te vinden op de site van de NVVB en voor de volledigheid als bijlage opgenomen. 

## Selectie gemeenten

De deelnemende gemeenten hebben zich naar aanleiding van een oproep in de nieuwsbrief verkiezingen grotendeels zelf aangemeld. Enkele gemeenten zijn in het voortraject intensief betrokken geweest, maar de meesten kenden Abacus vooraf niet. De criteria waren; de gemeente moet mee willen doen, Abacus moet passen in het proces en het geheel moet een afspiegeling zijn van de gemeenten, qua grootte. 

De verscheidenheid aan gemeenten heeft ervoor gezorgd dat er een breed beeld is ontstaan van de toepassing van Abacus. Er waren zowel gemeenten met veel eigen kennis als gemeenten waar dit veel minder het geval was. Door de aanmelding op initiatief te doen was er veel aandacht en enthousiasme, waardoor het beeld mogelijk positief kleurt. 

## Verbeterpunten Abacus

Wat naar voren komt is dat de gebruikers vooral de nadruk leggen op het doorontwikkelen van Abacus zodat een zo volledig mogelijke reeks van verkiezingsonderdelen met deze software kan worden ondersteund. De eigen waarneming van het team brengt meer en diepgaandere kleine en grote verbeteringen naar voren. 

De meest voorkomende verbeterpunten die worden genoemd zijn: 

- Oplossen verschillen tussen eerste en tweede invoer: Abacus verplicht conform de WPV twee handmatige invoeren in de software. Waar in OSV2020 bij een verschil één van de twee invoeren als definitief kan worden gekozen, moest in Abacus de afwijkende invoer opnieuw worden gedaan. Dat kost extra tijd, deelnemers verzoeken dit anders op te lossen.
- EML2csv integreren: Abacus bevatte het bestand nog niet om met Excel de resultaten te bekijken. De EML moest nu met een aparte tool handmatig worden geconverteerd. De wens is om het csv-bestand automatisch vanuit Abacus te kunnen genereren.
- Read only rol: Abacus heeft nog geen read only pagina om de voortgang op een beamer te kunnen tonen, zonder dat continu opnieuw moet worden ingelogd met een coördinator account.
- Voortgangsscherm bij meer dan 50 stembureaus wordt wat minder overzichtelijk. 
- Verklaringen invoeren bij waarschuwingen: Abacus geeft uitgebreide foutmeldingen en waarschuwingen. De verklaringen hierover kunnen echter niet via Abacus worden ingevoerd.

## Lessen uit de voorbereiding

Deelnemende gemeenten waardeerden de intensieve en persoonlijke voorbereiding, de bereikbaarheid en aanwezigheid van het ontwikkelteam. Dit maakt het toepassen van nieuw instrumentarium toegankelijker en vertrouwder: als de Kiesraad ter plaatse is, dan hebben ze er vertrouwen in.

Hierbij wordt terecht aangegeven dat dit bij een bredere toepassing niet schaalbaar is. De ondersteuning moet worden opgenomen in de reguliere voorbereiding van de verkiezingen zoals die door de Kiesraad standaard wordt gedaan. 

## Conclusies in meer detail

De conclusies uit de verschillende bronnen zijn hieronder in meer detail opgenomen. Waar mogelijk zijn de bronnen zelf ook toegankelijk voor de volledige context. 

### Focusgroep

Onderdeel van de focusgroepen die voor de evaluatie van de gemeenteraadsverkiezingen zijn georganiseerd was een groep specifiek over Abacus. [Het verslag hiervan is als bijlage toegevoegd.](evaluatieonderzoeken/rapportage-focusgroepen-gemeenten-gemeenteraadsverkiezingen-2026-1.pdf) De belangrijkste conclusies zijn positief, met enkele opmerkingen en suggesties: 

* Oplossen verschillen zoals in de GR26 versie van Abacus leidt tot tijdverlies
* Statusscherm stembureaus is onoverzichtelijk bij grotere hoeveelheden stembureaus
* Managementinformatie is nu niet in de applicatie beschikbaar
* Voorbereiding volgende verkiezing vraagt om een schaalbare aanpak

### Vragenlijst 

De vragenlijst die naar alle gemeenten is gestuurd bevatte ook vragen over Abacus. 12 gemeenten hebben gereageerd. De conclusies hieruit zijn als bijlage toegevoegd. De belangrijkste conclusies zijn positief, met enkele suggesties: 

* Oplossen van verschillen: 25% waardeert dit als slecht
* Weergave van fouten en waarschuwingen: 8% waardeert dit als slecht
* Maken van het GSB proces verbaal: 8% waardeert dit als slecht 

### Brief NVVB

De NVVB kijkt in de evaluatiebrief positief terug op de eerste toepassing van Abacus en heeft twee punten die ze voor de landelijke uitrol als essentieel beschouwt: 

* EML2CSV integreren in de software
* Gedegen opleidingsplan en een strategie om te komen tot een succesvolle landelijke uitrol

### Eigen aanwezigheid ter plaatse

Het ontwikkelteam is ter plaatse geweest bij alle gemeenten en heeft een overzicht gemaakt van grote en kleine verbeteringen die mogelijk zijn. De belangrijkste hieruit zijn hieronder opgenomen. 

#### Grote verbeteringen

- EML2csv integreren in Abacus (Epic kiesraad/abacus#3053)
- Backups vanuit de applicatie mogelijk maken (Issue kiesraad/abacus#3231)
- Verschillen oplossen; correctie optie (route die je gebruikt als je fouten hebt) (Issue kiesraad/abacus#3230)
- Read only rol (voortgang bijhouden, met name voorkomen beamerprobleem met uitloggen) (Issue kiesraad/abacus#3234)
- Voortgangsscherm kan duidelijker bij meer dan 50 stembureaus (Issue kiesraad/abacus#3234)
- Verklaringen invoeren bij waarschuwingen uit het controleprotocol (Issue kiesraad/abacus#3239)
- Waarschuwingen als 'afgehandeld' kunnen markeren om ze bij te houden (Issue kiesraad/abacus#3239)
- De keyboard hints worden niet/nauwelijks opgemerkt. Daardoor duurt het relatief lang voordat invoerders hun muis links laten liggen → Eenvoudige onboarding opnemen in de applicatie. Benoemen in de training. (Issue kiesraad/abacus#3238)
- Abacus als service (i.i.g. Utrecht)  (Issue kiesraad/abacus#3237)

