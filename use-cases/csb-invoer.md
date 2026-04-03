# CSB: Invoer

## Het CSB voert de tellingen van het GSB in (vlieger)

__Niveau:__ hoog-over, vlieger, 🪁

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De coördinator CSB stelt de invoer open.
2. [De coördinator CSB leest de resultaten van de laatste GSB-zitting in als eerste invoer van het CSB.](#de-coördinator-csb-leest-de-resultaten-van-de-laatste-gsb-zitting-in-als-eerste-invoer-van-het-csb-zee)
3. Het CSB voert de resultaten handmatig in als tweede invoer.
4. De applicatie stelt vast dat beide invoeren gelijk zijn.
5. (parallel aan invoer resultaten) De coördinator CSB voert de locatie, startdatum en starttijd van de zitting in.
6. De applicatie slaat het definitieve resultaat op.

__Uitbreidingen:__

4a. De applicatie stelt vast dat beide invoeren niet gelijk zijn:  
&emsp; 4a1. [De coördinator CSB beoordeelt de verschillen tussen de twee invoeren.](#de-coördinator-csb-beoordeelt-de-verschillen-tussen-de-twee-invoeren-zee)

## De coördinator CSB leest de resultaten van de laatste GSB-zitting in als eerste invoer van het CSB (zee)

__Niveau:__ gebruikersdoel, zee, 🌊

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De coördinator CSB leest het tellingsbestand (EML 510b) in als eerste invoer.
2. De coördinator CSB stelt vast dat de hash van het tellingsbestand (EML 510b) klopt.

__Uitbreidingen:__

1a. De CSB-applicatie draait op een andere machine dan de GSB-applicatie:  
&emsp; 1a1. De coördinator CSB zet het tellingsbestand (EML 510b) op de machine met de CSB-applicatie.  
&emsp; 1a2. De coördinator CSB leest het tellingsbestand (EML 510b) in.

1b. Het is niet mogelijk het tellingsbestand (EML 510b) te importeren:  
&emsp; 1b1. Het CSB lost in overleg met het GSB het probleem op en importeert alsnog het bestand.  
&emsp;&emsp; 1b1a. Het CSB slaagt er niet in het probleem op te lossen:  
&emsp;&emsp;&emsp; 1b1a1. Het CSB doet de eerste invoer handmatig.

2a. De hash van het tellingsbestand (EML 510b) klopt niet:  
&emsp; 2a1. De coördinator CSB stelt vast dat de hash niet correct is overgenomen.  
&emsp;&emsp; 2a1a. De coördinator CSB stelt vast dat de hash correct is overgenomen:  
&emsp;&emsp;&emsp; 2a1a1. De coördinator CSB neemt contact op met het GSB.  
&emsp; 2a2. De coördinator CSB corrigeert de ingevoerde hash.

## De coördinator CSB beoordeelt de verschillen tussen de twee invoeren (zee)

__Niveau:__ gebruikersdoel, zee, 🌊

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De coördinator CSB vergelijkt de eerste en tweede invoer met het papieren PV (DSO: Na 31-1, CSO: Na 31-2; evt. Na 14-2).  
2. De coördinator CSB stelt vast dat de digitale invoer correct is, maar de handmatige invoer niet.
3. De coördinator CSB gooit de handmatige invoer weg.
4. De coördinator CSB laat opnieuw handmatig invoeren.

__Uitbreidingen:__

2a. De coördinator CSB stelt vast dat de digitale invoer incorrect is, maar de handmatige wel correct is:  
&emsp; 2a1. De coördinator CSB gooit de digitale invoer weg.  
&emsp; 2a2. De coördinator CSB laat een keer extra handmatig invoeren.

2b. De coördinator CSB stelt vast dat zowel de digitale als de handmatige invoer niet correct zijn:  
&emsp; 2b1. De coördinator CSB gooit beide invoeren weg.  
&emsp; 2b2. De coördinator CSB laat twee keer opnieuw handmatig invoeren.

2c. Beide invoeren zijn handmatig gedaan:  
&emsp; 2c1. De coördinator CSB gooit de incorrecte invoer(en) weg.  
&emsp; 2c2. De coördinator CSB laat de invoer(en) opnieuw handmatig invoeren.
