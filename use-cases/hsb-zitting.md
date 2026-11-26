# HSB: Zitting

Abacus ondersteunt op dit moment de rol HSB alleen voor Tweede Kamerverkiezingen (TK). Deze use cases gelden dus alleen voor TK.

## Het hoofdstembureau (HSB) stelt uitkomst vast (wolk)

__Niveau:__ hoog-over, wolk, ☁️

__Hoofdscenario:__
1. [Het HSB controleert de GSB-resultaten en voert ze in.](#het-hsb-controleert-de-gsb-resultaten-en-voert-ze-in-vlieger)
2. [De coördinator HSB maakt het PV (O 7) en het tellingsbestand EML 510c aan.](#de-coördinator-hsb-maakt-het-pv-o-7-en-het-tellingsbestand-eml-510c-aan-zee)
3. Het HSB voert het controleprotocol (handmatige controle optellingen software) uit en stelt geen verschillen vast.
4. Het HSB stelt de totalen van het HSB vast o.b.v. het PV (O 7): controleren op compleetheid, ondertekenen. En sluit daarmee de zitting.
5. Het HSB stelt het tellingsbestand EML 510c beschikbaar aan het hogere stembureau voor de uitslagvaststelling.
6. Het HSB stelt het PV HSB (O 7) vast, publiceert het PV en brengt het over naar het hogere stembureau.

__Uitbreidingen:__

3a. Het HSB stelt verschillen vast d.m.v. het controleprotocol (handmatige controle optellingen software):  
&emsp; 3a1. Het HSB controleert de resultaten van het controleprotocol.  
&emsp; 3a2. Het HSB vindt een fout in de resultaten van het controleprotocol en corrigeert deze.  
&emsp;&emsp; 3a2a. Het HSB vindt geen fout en bevestigt een verschil tussen de controles en de resultaten van de
applicatie:  
&emsp;&emsp;&emsp; 3a2a1. Het HSB neemt contact op met de Kiesraad en vult sectie 2.5 (Uitkomst controleprotocol) van het PV O 7 aan met de verschillen.

4a. Het HSB stelt een probleem vast met het PV:  
&emsp; 4a1. Het HSB corrigeert het probleem.


## Het HSB controleert de GSB-resultaten en voert ze in (vlieger)

Niveau: hoog-over, vlieger, 🪁

N.B. Bij TK zijn er meerdere GSB's - stappen die 'het GSB' noemen gelden bij TK _per GSB_.

__Hoofdscenario:__
1. Het HSB ontvangt het GSB PV incl. bijlagen (DSO: Na 31-1, CSO: Na 31-2) van de burgemeester.
2. Het HSB ontvangt alle overige documenten (PV's, onderliggende PV's, corrigenda, tellingsbestand EML 510b) van het GSB en controleert ze op volledigheid.
3. Het HSB stelt vast dat het GSB PV geen aanleiding geeft tot een terugverwijzing. (controleprotocol deel A)
4. [Het HSB voert de tellingen van het GSB in.](./hsb-invoer.md#het-hsb-voert-de-tellingen-van-het-gsb-in-vlieger)

__Uitbreidingen:__

3a. Het GSB PV geeft aanleiding tot een terugverwijzing:  
&emsp; 3a1. Het HSB informeert het CSB door sectie 1.2 van het PV (O 7) in te vullen. Het CSB gaat het probleem onderzoeken.  


## De coördinator HSB maakt het PV (O 7) en het tellingsbestand EML 510c aan (zee)

__Niveau:__ gebruikersdoel, zee, 🌊

### Hoofdscenario en uitbreidingen

__Hoofdscenario:__

1. De applicatie stelt vast dat alle stembureaus definitieve invoer hebben.
2. De coördinator HSB sluit de invoerfase af.
3. De applicatie stelt vast dat de gegevens van de zitting zijn ingevuld.
4. De coördinator HSB genereert het PV (O 7), het tellingsbestand (EML 510 c) en diens digitale handtekening.

__Uitbreidingen:__

3a. De gegevens van de zitting zijn nog niet ingevuld:  
&emsp; 3a1. De coördinator HSB voert de locatie, startdatum en starttijd van de zitting in.
