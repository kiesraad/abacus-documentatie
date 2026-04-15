# Zetelverdeling beslisboom


## 19 of meer zetels

lijstuitputting kan voorkomen in de gele stappen


```Mermaid
flowchart

    flow_start@{ shape: sm-circ }
    flow_end@{ shape: sm-circ }

    classDef lijstuitputting fill:#ffc943,stroke:#e8a302

    vaststellen_kiesdeler(vaststellen kiesdeler)

    toedeling_volledige_zetels(toedeling volledige zetels)
    class toedeling_volledige_zetels lijstuitputting

    zetels_over{zetels over}

    stelsel_grootste_gemiddelden(stelsel grootste gemiddelden -> stap, niet stelsel)

    gelijk_gemiddelde{gelijk<br/>gemiddelde}

    loting(loting)
    toekennen_restzetels(toekennen restzetels)
    class toekennen_restzetels lijstuitputting
    volstrekte_meerderheid{volstrekte<br/>meerderheid}

    hertoekenning_zetel(hertoekennen zetel)
    class hertoekenning_zetel lijstuitputting

    flow_start --> vaststellen_kiesdeler
    vaststellen_kiesdeler --> toedeling_volledige_zetels

    toedeling_volledige_zetels --> zetels_over

    zetels_over --->|Nee| volstrekte_meerderheid

    zetels_over -->|Ja| stelsel_grootste_gemiddelden

    stelsel_grootste_gemiddelden --> gelijk_gemiddelde
    
    gelijk_gemiddelde -->|Nee| toekennen_restzetels

    gelijk_gemiddelde -->|Ja| loting

    toekennen_restzetels --> zetels_over

    loting --> toekennen_restzetels

    volstrekte_meerderheid -->|Ja| hertoekenning_zetel

    volstrekte_meerderheid -->|Nee| flow_end

    hertoekenning_zetel --> flow_end


```
