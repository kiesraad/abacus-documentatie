# Bevindingenproces release-testen

Voor het release-testen maken we één of meer epics aan met issues voor de testsessies. Dit document beschrijft hoe we omgaan met bevindingen gevonden tijdens het release-testen.

De resultaten van een testsessie voeg je als comment toe aan een issue:
- wat je hebt getest,
- bevindingen,
- open vragen,
- dingen die verder getest moeten worden.

Daarna debrief je de testsessie met een ander teamlid. Voor elke bevinding gebruik je onderstaande stappen om te beslissen je of de bevinding vóór de release opgelost moeten worden.

## Beslissing en proces aanmaken issue voor bevinding

Dit proces doorloop je voor elke bevinding samen met je debriefer. Bij twijfel kun je altijd een derde persoon betrekken.

### Stap 1: maximize en generalize

Bedenk of er een variant van de bevinding is die ernstiger is (maximize) of meer gebruikers raakt (generalize). (zie https://bbst.courses/rimgen/) Je wil de criteria hieronder toepassen op de meest impactvolle versie van je bevinding.

### Stap 2: doorloop de criteria

- hoe vaak kan het voorkomen?
	- bij welke verkiezingen?
	- bij welke GSB's/HSB's/CSB's?
	- bij alle onderliggende SB's of alleen specifieke?
	- bij welke rollen?
- hoe ernstig is het als het voorkomt?
	- detecteerbaarheid: hoe snel na voordoen is het te detecteren? hoe makkelijk is het te detecteren?
	- oplosbaarheid: kan het opgelost worden door de gebruiker en/of is er een workaround? hoe ingewikkeld of moeilijk zijn die?
	- impact: op een schaal van "geen geldig verkiezingsresultaat mogelijk" tot "een keer extra moeten klikken"
- wat zou de benodigde effort voor de fix zijn? (grootte, complexiteit)

### Stap 3: neem de beslissing

Op basis van de impact van de bevinding en de benodigde effort voor een fix, beslis je of deze bevinding opgelost moet worden voor de release.

Als niet, dan hoef je verder niets te doen.

Als wel, dan doe je het volgende aan:
- Maak een issue aan, hang het aan de milestone van de release.
- Leg in het issue de context en reproductiestappen duidelijk vast, en de fix die je met je debriefer hebt besproken. Zo is de afweging die jullie hebben gemaakt te volgen.
- post het issue in het abacus-kanaal, zodat iedereen op de hoogte is en vragen of aanvullingen aan het issue toe kan voegen.
