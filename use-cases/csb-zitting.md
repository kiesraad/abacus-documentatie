# CSB: Zitting

Abacus ondersteunt op dit moment de rol CSB alleen voor gemeenteraadsverkiezingen (GR) en waterschapsverkiezingen (WS). Deze use cases gelden dus alleen voor GR en WS.

## Het centraal stembureau (CSB) stelt de verkiezingsuitslag vast (wolk)

__Hoofdscenario:__
1. [Het CSB controleert de GSB-resultaten en voert ze in.](#het-csb-controleert-de-gsb-resultaten-en-voert-ze-in-vlieger)
2. Het CSB voert het controleprotocol optellingen uit. (controleprotocol deel B)
3. [Het CSB stelt de zetelverdeling vast en wijst de gekozen kandidaten aan.](#het-csb-stelt-de-zetelverdeling-vast-en-wijst-de-gekozen-kandidaten-aan-vlieger)
4. De applicatie genereert de benodigde bestanden: PV P 22-2, tellingsbestanden EML 510d, EML 520.
5. Het CSB voert het controleprotocol zetelverdeling uit. (controleprotocol deel C)
6. Het CSB opent de zitting.
7. Het CSB stelt de uitslag vast o.b.v. de P 22-2: controleren op compleetheid, voorlezen, er zijn geen bezwaren, ondertekenen. En sluit daarmee de zitting.
8. Het CSB publiceert de P 22-2, EML 510d en EML 520 op de website van het vertegenwoordigend orgaan.
9. Het CSB stuurt alle PVs naar het vertegenwoordigend orgaan.
10. Het CSB deelt de EML 510d en EML 520 met de Kiesraad.
11. De voorzitter CSB geeft de benoemde leden schriftelijk kennis van hun benoeming.

__Uitbreidingen:__

1-7a. Het CSB moet nieuwe aantallen invoeren ter correctie van de eerder ingevoerde tellingen:  
&emsp; 1-8a1. Het CSB corrigeert de eerder ingevoerde aantallen in de applicatie. Er is dus geen tweede CSB-zitting.

7a. Er zijn bezwaren tijdens de zitting:  
&emsp; 7a1. Het CSB neemt de bezwaren op in het PV.  
&emsp; 7a2. Het CSB besluit dat geen van de bezwaren reden zijn tot een hertelling.  
&emsp;&emsp; 7a2a. Het CSB besluit dat een aantal stembureaus herteld moet worden:  
&emsp;&emsp;&emsp; 7a2a1. Het GSB voert de hertelling uit d.m.v. de corrigendum-flow.  
&emsp;&emsp;&emsp; 7a2a2. Het CSB stelt de nieuwe uitslag vast.  
&emsp;&emsp;&emsp; 7a2a3. Het CSB voegt de sectie "Hertelling" toe aan het oorspronkelijke PV.

9a. Het vertegenwoordigend orgaan besluit dat een hertelling nodig is ([Artikel V 4a Kieswet](https://wetten.overheid.nl/BWBR0004627/2026-01-01/#AfdelingIV_HoofdstukV_Paragraaf1_ArtikelV4a)):  
&emsp; 9a1. Het GSB doet de hertelling d.m.v. de corrigendum-flow.  
&emsp; 9a2. Het CSB stelt de nieuwe uitslag vast.  
&emsp; 9a3. Het CSB maakt een nieuwe P 22-2, EML 510d en EML 520 aan met alleen de nieuwe uitslag.  
&emsp; 9a4. Het CSB publiceert de nieuwe P 22-2, EML 510d en EML 520 op de website van het vertegenwoordigend orgaan.  
&emsp; 9a5. Het CSB stuurt alle PVs naar het vertegenwoordigend orgaan.  
&emsp; 9a6. Het CSB deelt de nieuwe EML 510d en EML 520 met de Kiesraad.

### Niet in scope

- Elektronische handtekening van documenten.
- CSB besluit tijdens de zitting tot spontane hertelling. Resulteert in samenvoegen van oud en nieuw P22. Vereist wel aanmaken van nieuwe verkiezingen (GR GSB en GR CSB) in Abacus.
- De benoemingsbrieven en de kennisgevingen tot geloofsbrief.


## Het CSB controleert de GSB-resultaten en voert ze in (vlieger)

NB. Bij GR is er één GSB. Bij WS zijn er meerdere GSB's - stappen die 'het GSB' noemen gelden bij WS _per GSB_.

__Hoofdscenario:__
1. Het CSB ontvangt het GSB PV incl. bijlagen (DSO: Na 31-1, CSO: Na 31-2) van de burgemeester.
2. Het CSB ontvangt alle overige documenten (PVs, onderliggende PVs, corrigenda, tellingsbestand EML 510b) van het GSB en controleert ze op volledigheid.
3. Het CSB stelt vast dat het GSB PV geen aanleiding geeft tot een terugverwijzing. (controleprotocol deel A)
4. [Het CSB voert de tellingen van het GSB in.](./csb-invoer.md#het-csb-voert-de-tellingen-van-het-gsb-in-vlieger)

__Uitbreidingen:__

3a. Het GSB PV geeft aanleiding tot een terugverwijzing:  
&emsp; 3a1. Het CSB verwijst terug naar het GSB.  
&emsp; 3a2. [Gemeentelijk stembureau (GSB) stelt uitkomst vast in volgende zitting (corrigenda)](gsb-volgende-zitting.md#gemeentelijk-stembureau-gsb-stelt-uitkomst-vast-in-volgende-zitting-corrigendum-wolk)  
&emsp; 3a3. (CSO) Het CSB voegt het Inlegvel Na 31-2 toe aan het PV Na 31-2.  
&emsp; 3a3. (DSO) Het CSB voegt het Inlegvel N 10-1 toe aan de PVs N 10-1 en voegt het Inlegvel Na 31-1 toe aan het het PV Na 31-1.


## Het CSB stelt de zetelverdeling vast en wijst de gekozen kandidaten aan (vlieger)

__Niveau:__ hoog-over, vlieger, 🪁

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. Het CSB markeert overleden kandidaten.
2. De applicatie stelt de zetelverdeling vast.
3. De applicatie wijst de gekozen kandidaten aan.
4. De applicatie rangschikt de kandidaten.

__Uitbreidingen:__

2a. Er zijn geen geldige stemmen uitgebracht op kandidaten:  
&emsp; 2a1. De applicatie toont een foutmelding om contact op te nemen met de Kiesraad.

2b. Er zijn minder beschikbare restzetels dan lijsten met gelijke overschotten of gemiddelden:  
&emsp; 2b1. Het CSB kent de restzetel bij loting toe.

2c. (art P 9) Een lijst heeft een meerderheid van stemmen, maar geen meerderheid van zetels:  
&emsp; 2c1. De applicatie kent de laatst toegewezen restzetel toe aan die lijst.  
&emsp; 2c1a. De laatst toegewezen restzetel was toegekend op basis van een gelijk gemiddelde of overschot:  
&emsp;&emsp; 2c1a1. Het CSB bepaalt bij loting bij welke lijst de restzetel wordt weggehaald.

2d. (art P 10 lijstuitputting) Er zijn meer zetels aan een lijst toegekend dan dat er kandidaten op de lijst staan:  
&emsp; 2d1. De applicatie berekent de zetelverdeling opnieuw met inachtneming van de lijstuitputting.  
&emsp; 2d1a. Er zijn te weinig kandidaten om alle aan lijsten toegewezen zetels te vullen:  
&emsp;&emsp; 2d1a1. De applicatie toont een foutmelding om contact op te nemen met de Kiesraad.

3a. Er zijn kandidaten met een gelijk aantal stemmen, hoger dan de voorkeursdrempel:  
&emsp; 3aa. Er zijn voldoende beschikbare zetels voor de kandidaten met gelijk aantal stemmen:  
&emsp;&emsp; 3aa1. Het CSB kent de zetels bij loting toe.  
&emsp; 3ab. Er zijn minder beschikbare zetels dan kandidaten met gelijk aantal stemmen:  
&emsp;&emsp; 3ab1. Het CSB kent de beschikbare zetel(s) bij loting toe.

4a. Er zijn niet-gekozen kandidaten met een aantal stemmen hoger dan de voorkeursdrempel:  
&emsp; 4a1. De niet-gekozen kandidaten worden gerangschikt o.b.v. de volgorde van de lijst.

### Buiten scope
- Er is een voorgestelde wetswijziging dat lijsten de kiesdeler moeten halen om een restzetel te kunnen krijgen. De minister is voornemens de vragen in het verslag wetsvoorstel te beantwoorden na de gemeenteraadsverkiezingen van 2026. Deze wetswijziging gaat dus niet in vóór GR 2026.
