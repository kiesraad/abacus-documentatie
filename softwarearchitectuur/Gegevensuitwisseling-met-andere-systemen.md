# Gegevensuitwisseling met andere systemen

Abacus wordt air-gapped en lokaal gedraaid. Gegevensuitwisseling gebeurt dus nooit over een netwerk.


## Importeren van data

### Verkiezingsdefinitie en kandidatenlijsten

De Kiesraad beheert `vapp-metadata.zip` met daarin de volgende bestanden:
- `MasterElectionTree.xml`: xml, maar geen EML_NL
- `parties.txt`: politieke partijen
- `cities.txt`: woonplaatsen in Nederland
- `nonEuropeanCities.txt`: woonplaatsen in Caribisch Nederland
- `metadata-version.txt`

Deze bestanden zijn onderdeel van OSV2020 PP, KS en U.

Het CSB van de verkiezing maakt met OSV2020 KS de volgende drie bestanden aan:
- de verkiezingsdefinitie (EML_NL 110a)
- de kandidatenlijsten (EML_NL 230b)
- de totaallijsten (EML_NL 230c): kandidatenlijsten met geboortedatum, adresgegevens kandidaten, gegevens gemachtigden (als van toepassing)

De xSB's (GSB, CSB, etc) lezen de verkiezingsdefinitie (OSV2020, Abacus) en de kandidatenlijsten (OSV2020, Abacus) of totaallijsten (OSV2020 CSB) in de uitslagensoftware in.

### Stembureaus

Stembureaus kunnen worden geïmporteerd d.m.v. een EML_NL 110b-bestand. Gemeentes gebruiken verschillende tools om deze aan te maken.


## Exporteren van data

### Stembureaus
Zie [Input- en output-bestanden Abacus](../use-cases/input-en-output/input-output-bestanden.md).

### Verkiezingsresultaten

Zie [Input- en output-bestanden Abacus](../use-cases/input-en-output/input-output-bestanden.md).
