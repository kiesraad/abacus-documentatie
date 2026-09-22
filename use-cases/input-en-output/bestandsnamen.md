# Bestandsnamen Abacus

Dit document beschrijft van bestanden die Abacus genereert hoe de namen zijn opgebouwd aan de hand van variabelen, transformaties en templates.

De template bepaalt welke variabelen met welke transformaties er in de bestandsnaam opgenomen worden.

Als voorbeeld: `osv4-3_telling_{election_id|lower}.csv` beschrijft dat de `election_id` variabele ingevoegd moet worden, waar de `lower` transformatie op uitgevoerd is, met als resultaat `osv4-3_telling_ps2023_drenthe.csv`.

Over het algemeen is een bestandsnaam opgebouwd uit variabelen die zijn gescheiden door een `_`, waarbij de spaties in de variabelen vervangen zijn door een `-`.

## Variabelen

De volgende variabelen worden gebruikt in de bestandsnamen.

| Variabele naam  | in EML 110a | In Abacus  | Voorbeelden  |
|---|---|---|---|
| `election_name` | `ElectionIdentifier/ElectionName` | `election.official_name` | `Algemeen bestuur van het waterschap Aardenboezem 2027`<br>`Provinciale Staten Drenthe 2023` |
| `election_id`  | `ElectionIdentifier@Id` | `election.election_id`  | `PS2023_Drenthe`<br>`GR2026_sHertogenbosch`<br>`TK2022` |
| `region` | `RegionName` | `election.authority_region` | `Limburg` |
| `region_category` | `@RegionCategory` *) | ? | `GEMEENTE` `PROVINCIE` `KIESKRING` |
| `timestamp` | nvt | nvt | `20260831-111904` |

*) `region_category` moet `OPENBAAR_LICHAAM` in plaats van `GEMEENTE` zijn voor Bonaire, Saba en Sint Eustatius. 

## Transformaties

De volgende transformaties kunnen uitgevoerd worden op de variabelen.

| Transformatie | Uitleg | Voorbeelden |
|---|---|---|
| `lower` | Kleine letters | `PS2023_Drenthe` wordt `ps2023_drenthe` |
| `hyphen` | Kleine letters, verwijder accenten, verwijder leestekens (geen letter, cijfer of `-`), vervang spatie met `-` | `'s-Hertogenbosch` wordt `s-hertogenbosch` <br> `Súdwest-Fryslân` wordt `sudwest-fryslan` |

## Bestanden

### Uitwisseling

#### Verkiezingsdefinitie (EML 110a)
Wordt niet gegenereerd door Abacus.

#### Kandidatenlijsten (EML 230b)
Wordt niet gegenereerd door Abacus.

#### Stembureaulijst (EML 110b)
Hiervoor is een extra transformatie nodig, omdat de bestandsnamen op een andere manier worden opgebouwd.

| Transformatie | Uitleg | Voorbeelden |
|---|---|---|
| `slugify` | vervang spatie met `_`, verwijder leestekens (geen letter, cijfer of `-`) | `Algemeen bestuur van het waterschap Aardenboezem 2027` wordt `Algemeen_bestuur_van_het_waterschap_Aardenboezem_2027` |

Template:
```
abacus-exporteren_stemgebieden-{election_name|slugify|lower}-eml_110b_stembureaus-{timestamp}.zip
└── Stembureaus_{election_id}_{region|slugify}.eml.xml
```

Voorbeeld:
```
abacus-exporteren_stemgebieden-algemeen_bestuur_van_het_waterschap_aardenboezem_2027-eml_110b_stembureaus-20260831-111904.zip
└── Stembureaus_AB2027_Aardenboezem_Nieuwstrand.eml.xml
```


#### Publieke sleutel (certificaat)
```
public_key_abacus_{election_id|lower}_{region_category|lower}_{region|hyphen}.crt
```

Voorbeelden:
```
public_key_abacus_ab2027_amstelgooienvecht_gemeente_de-ronde-venen.crt
```

```
public_key_abacus_tk2021_gemeente_eemsdelta.crt
```

### Teluitslagen

#### GSB eerste zitting (EML 510b)
```
definitieve-documenten_{election_id|lower}_{region_category|lower}_{region|hyphen}-{timestamp}.zip
├── Model_Na31-1.pdf (voor DSO)
├── Model_Na31-2.pdf (voor CSO)
├── osv4-3_telling_{election_id|lower}.csv
└── Telling_{election_id}.zip
    ├── Telling_{election_id}.eml.xml
    └── Telling_{election_id}.eml.xml.signature
```

Voorbeeld:
```
definitieve-documenten_tk2026_gemeente_utrecht-20260310-1355.zip
├── Model_Na31-2.pdf
├── osv4-3_telling_tk2026.csv
└── Telling_TK2026.zip
    ├── Telling_TK2026.eml.xml
    └── Telling_TK2026.eml.xml.signature
```


#### GSB volgende zitting (EML 510b)
```
correctie_{election_id|lower}_{region_category|lower}_{region|hyphen}-{timestamp}.zip
├── Leeg_Model_P2a.pdf
├── Model_Na14-2.pdf
├── osv4-3_telling_{election_id|lower}.csv
└── Telling_{election_id}.zip
    ├── Telling_{election_id}.eml.xml
    └── Telling_{election_id}.eml.xml.signature
```

Voorbeeld:
```
correctie_gr2026_purmerend_gemeente_purmerend-20251125-144536
├── Leeg_Model_P2a.pdf
├── Model_Na14-2.pdf
├── osv4-3_telling_gr2026_purmerend.csv
└── Telling_GR2026_Purmerend.zip
    ├── Telling_GR2026_Purmerend.eml.xml
    └── Telling_GR2026_Purmerend.eml.xml.signature
```

#### CSB-zitting Totaaltelling (EML 510d)
```
definitieve-documenten_{election_id|lower}_{region_category|lower}_{region|hyphen}-{timestamp}.zip
├── osv4-3_telling_{election_id|lower}.csv
└── Totaaltelling_{election_id}.zip
    ├── Totaaltelling_{election_id}.eml.xml
    └── Totaaltelling_{election_id}.eml.xml.signature
```

Voorbeelden:
```
definitieve-documenten_gr2026_shertogenbosch_gemeente_s-hertogenbosch-20260921-084113.zip
├── osv4-3_telling_gr2026_shertogenbosch.csv
└── Totaaltelling_GR2026_sHertogenbosch.zip
    ├── Totaaltelling_GR2026_sHertogenbosch.eml.xml
    └── Totaaltelling_GR2026_sHertogenbosch.eml.xml.signature
```

Let op: 's-Hertogenbosch wel of niet met streepje

#### CSB-zitting Resultaat (EML 520) 
```
vaststelling-uitslag_{election_id|lower}_{region_category|lower}_{region|hyphen}-{timestamp}.zip
├── Model_P22-2.pdf
└── Resultaat_{election_id}.zip
    └── Resultaat_{election_id}.eml.xml
```

Voorbeeld:
```
vaststelling-uitslag_ab2023_amstelgooienvecht_waterschap_amstel-gooi-en-vecht-20230103-160614.zip
├── Model_P22-2.pdf
└── Resultaat_AB2023_AmstelGooienVecht.zip
    └── Resultaat_AB2023_AmstelGooienVecht.eml.xml
```

#### CSB-zitting P22-2 bijlage 1 (Stemmen per lijst en per kandidaat)
```
model-p22-2-bijlage_{election_id|lower}_{region_category|lower}_{region|hyphen}-{timestamp}.zip
└── Model_P22-2_bijlage.pdf
```

Voorbeeld:
```
model-p22-2-bijlage_ab2020_rivierenpolder_waterschap_rivier-en-polder-20260918-100815.zip
└── Model_P22-2_bijlage.pdf
```
