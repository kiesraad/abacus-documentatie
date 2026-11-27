# HSB: Invoer

Abacus ondersteunt op dit moment de rol HSB alleen voor Tweede Kamerverkiezingen (TK). Deze use cases gelden dus alleen voor TK.

## Het HSB voert de tellingen van het GSB in (vlieger)

__Niveau:__ hoog-over, vlieger, 🪁

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

N.B. Bij TK zijn er meerdere GSB's - de stappen 2, 3 en 4 worden uitgevoerd voor elk GSB.

1. De coördinator HSB stelt de invoer open.
2. [De coördinator HSB leest de resultaten van de GSB-zitting in als eerste invoer van het HSB.](#de-coördinator-hsb-leest-de-resultaten-van-de-gsb-zitting-in-als-eerste-invoer-van-het-hsb-zee)
3. De coördinator HSB laat de resultaten handmatig invoeren als tweede invoer.
4. De applicatie stelt vast dat beide invoeren gelijk zijn.
5. (parallel aan invoer resultaten) De coördinator HSB voert de locatie, startdatum en starttijd van de zitting in.
6. De applicatie slaat het definitieve resultaat op.

__Uitbreidingen:__

2-3a. Tijdens invoer is er reden om de handmatige invoer (tijdelijk) te stoppen:  
&emsp; 2-3a1. De coördinator HSB pauzeert de invoer.  
&emsp; 2-3a2. De applicatie blokkeert verdere handmatige invoer.

4a. De applicatie stelt vast dat beide invoeren niet gelijk zijn:  
&emsp; 4a1. [De coördinator HSB beoordeelt de verschillen tussen de twee invoeren.](#de-coördinator-hsb-beoordeelt-de-verschillen-tussen-de-twee-invoeren-zee)

_Zie ook de flowchart ["Afhandeling fouten en verschillen door coördinator"](./afhandeling-fouten-verschillen-coordinator.md)._

## De coördinator HSB leest de resultaten van de GSB-zitting in als eerste invoer van het HSB (zee)

__Niveau:__ gebruikersdoel, zee, 🌊

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De coördinator HSB leest het tellingsbestand van het GSB (EML 510b) in als eerste invoer.
2. De applicatie stelt vast dat het tellingsbestand geldig is.
3. De applicatie stelt vast dat de digitale handtekening van het tellingsbestand klopt met de publieke sleutel van het GSB.
4. De coördinator HSB stelt vast dat de hash van het tellingsbestand (EML 510b) klopt.

__Uitbreidingen:__

2a. Het tellingsbestand (EML 510b) is niet geldig:  
&emsp; 2a1. Het HSB lost in overleg met het GSB het probleem op en importeert alsnog een geldig bestand.  
&emsp;&emsp; 2a1a. Het HSB slaagt er niet in het probleem op te lossen:  
&emsp;&emsp;&emsp; 2a1a1. Het HSB doet de eerste invoer handmatig.

3a. De digitale handtekening is niet valide of klopt niet met de publieke sleutel van het GSB:  
&emsp; 3a1. Het HSB lost in overleg met het GSB het probleem op en importeert alsnog het bestand.  
&emsp;&emsp; 3a1a. Het HSB slaagt er niet in het probleem op te lossen:  
&emsp;&emsp;&emsp; 3a1a1. Het HSB gebruikt het tellingsbestand niet en doet de eerste invoer handmatig.

4a. De applicatie geeft aan dat de hash van het tellingsbestand (EML 510b) niet klopt:  
&emsp; 4a1. De coördinator HSB stelt vast dat de hash niet correct is overgenomen.  
&emsp;&emsp; 4a1a. De coördinator HSB stelt vast dat de hash correct is overgenomen:  
&emsp;&emsp;&emsp; 4a1a1. De coördinator HSB neemt contact op met het GSB.  
&emsp; 4a2. De coördinator HSB corrigeert de ingevoerde hash.

## De coördinator HSB beoordeelt de verschillen tussen de twee invoeren (zee)

__Niveau:__ gebruikersdoel, zee, 🌊

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De coördinator HSB vergelijkt de eerste en tweede invoer met het papieren PV (DSO: Na 31-1, CSO: Na 31-2).  
2. De coördinator HSB stelt vast dat de digitale invoer correct is, maar de handmatige invoer niet.
3. De coördinator HSB gooit de handmatige invoer weg.
4. De coördinator HSB laat opnieuw handmatig invoeren.

__Uitbreidingen:__

2a. De coördinator HSB stelt vast dat de digitale invoer incorrect is, maar de handmatige wel correct is:  
&emsp; 2a1. De coördinator HSB gooit de digitale invoer weg.  
&emsp; 2a2. De coördinator HSB laat een keer extra handmatig invoeren.  
&emsp; 2a3. HSB maakt hier een melding van in het PV (O 7).


2b. De coördinator HSB stelt vast dat zowel de digitale als de handmatige invoer niet correct zijn:  
&emsp; 2b1. De coördinator HSB gooit beide invoeren weg.  
&emsp; 2b2. De coördinator HSB laat twee keer opnieuw handmatig invoeren.

2c. Beide invoeren zijn handmatig gedaan:  
&emsp; 2c1. De coördinator HSB lost de verschillen op zoals beschreven in [De coördinator GSB beoordeelt de verschillen tussen de twee invoeren.](gsb-invoer.md#de-coördinator-gsb-beoordeelt-de-verschillen-tussen-de-twee-invoeren-zee)

3a. De coördinator HSB laat, in plaats van de handmatige invoer helemaal weg te gooien, alleen de afwijkende velden daarvan corrigeren door dezelfde invoerder:  
&emsp; 3a1. De applicatie bewaart de andere invoer als referentie en wist de afwijkende velden in de handmatige invoer, gemarkeerd met waarschuwing [W.002](./validatieregels-plausibiliteitschecks-tellingen.md#w002-bij-correctie-de-coördinator-heeft-velden-leeggemaakt-die-opnieuw-ingevuld-moeten-worden). (W.001 wordt bij een correctie-invoer niet getoond.)  
&emsp; 3a2. De invoerder corrigeert de gemarkeerde velden aan de hand van het PV.

_Zie ook de flowchart ["Afhandeling fouten en verschillen door coördinator"](./afhandeling-fouten-verschillen-coordinator.md)._
