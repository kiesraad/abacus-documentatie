# Checklist release-testen

Voordat we een nieuwe release opleveren voor de wettelijke toets en het beveiligingsonderzoek (pen test), testen we die release. Deze checklist bevat de testideeën die voor (vrijwel) elke release relevant zijn. De intentie van de checklist is dus niet om volledig te zijn, maar om een startpunt te bieden voor de scope van de releasetest.

## Op een dev build
- volledig doorlopen proces (van aanmaken eerste beheerder t/m downloaden output-bestanden)
- tests op basis van de use cases
- fuzzers langere tijd draaien
- vergelijking output met OSV2020-U
- modellen langs juridisch expert
- weinig geraakte functionaliteit, zoals backups, session timeouts, ...
- simulatie van een zitting

### Ketentest
- importeren verkiezingsdefinities en kandidatenlijsten van OSV2020-KS of e-KS
- upload van output-bestanden naar Platform Uitwisseling
- upload van output-bestanden naar Platform Teluitslagen

Bij voorkeur met speciale karakters (streepjes, spaties, apostrof, diakrieten) in gemeentenamen e.d.


## Op de release build
- installatie op Windows en op Linux
- volledig doorlopen proces (van aanmaken eerste beheerder t/m downloaden output-bestanden)
- geen dev features aanwezig, zoals testdata, /dev page, storybook, ...
- release features zoals aanwezig, zoals airgap, TLS, embedded typst, memory-serve, ...
