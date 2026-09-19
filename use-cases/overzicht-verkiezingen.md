# Overzicht verkiezingen

__Let op:__ Dit document beschrijft alleen de verkiezingen die op dit moment door Abacus ondersteund worden.

## Verkiezingen

| Verkiezingen       | ElectionCategory | ElectionSubcategory        | GSB        | HSB | CSB          |
| ------------------ | ---------------- | -------------------------- | ---------- | --- | ------------ |
| Gemeenteraad       | GR               | GR1 (minder dan 19 zetels) |  gemeente  |  -  |  gemeente    |
| Gemeenteraad       | GR               | GR2 (19 of meer zetels)    |  gemeente  |  -  |  gemeente    |
| Waterschappen      | AB               | AB1 (minder dan 19 zetels) |  gemeente  |  -  |  waterschap  |
| Waterschappen      | AB               | AB2 (19 of meer zetels)    |  gemeente  |  -  |  waterschap  |
| Provinciale Staten | PS               | PS1 (geen kieskringen)     |  gemeente  |  -  |  +           |
| Provinciale Staten | PS               | PS2 (kieskringen)          |  gemeente  |  +  |  +           |

"-": niet van toepassing.  
"+": nog niet ondersteund door Abacus.

### Gemeenteraadsverkiezingen
- Er is één GSB en één CSB.

### Waterschapsverkiezingen
- Waterschappen hebben 4 geborgde zetels en een aantal verkozen zetels. In de verkiezingsdefinitie (`NumberOfSeats`) staat het aantal verkozen zetels.
- Er zijn op dit moment geen waterschappen met minder dan 19 verkozen zetels.
- Er zijn meerdere GSBs voor elk CSB.
- Een aantal gemeenten vallen in meerdere waterschappen en richten dus meerdere GSBs in, nl. één voor elk waterschap.

### Provinciale Statenverkiezingen
- De volgende provincies hebben kieskringen (PS2): Gelderland (2 kieskringen), Noord-Holland (3 kieskringen), Zuid-Holland (4 kieskringen), Noord-Brabant (2 kieskringen), Limburg (2 kieskringen).
- PS1: Er zijn meerdere GSBs voor elk CSB.
- PS2: Er zijn meerdere GSBs voor elk HSB. Er zijn 2-4 HSBs voor elk CSB.
