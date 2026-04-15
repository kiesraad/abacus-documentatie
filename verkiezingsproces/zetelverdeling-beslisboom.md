# Zetelverdeling flowchart


## 19 of meer zetels

Lijstuitputting kan voorkomen in de gele stappen.


```Mermaid
flowchart
    %% styling
    classDef lijstuitputting fill:#ffc943,stroke:#e8a302
    classDef greyFill fill:#eee,stroke:#bbb;

    %% elements
    flow_start@{ shape: sm-circ, label: "start" }
    flow_end@{ shape: framed-circle, label: "end" }

    vaststellen_kiesdeler(vaststellen kiesdeler)

    toedeling_volledige_zetels(toedeling volledige zetels)
    class toedeling_volledige_zetels lijstuitputting

    zetels_over{"zetel(s) over?"}

    bereken_partijen_met_grootste_gemiddelde("bereken partij(en) met grootste gemiddelde")

    voldoende_restzetels{voldoende<br/>restzetels?}
    loting_grootste_gemiddelden(loting)
    toekennen_restzetels("toekennen restzetel(s)")
    class toekennen_restzetels lijstuitputting
    volstrekte_meerderheid{lijst met<br/>>50% stemmen,<br/>maar niet zetels?}
    laatste_restzetels_samen{laatste restzetels<br/>samen?}
    loting_abs_meerderheid(loting)

    herverdeling_laatste_restzetel(herverdeling laatste restzetel)
    class herverdeling_laatste_restzetel lijstuitputting

    %% flow
    flow_start --> vaststellen_kiesdeler
    vaststellen_kiesdeler --> toedeling_volledige_zetels

    toedeling_volledige_zetels --> zetels_over

    zetels_over --->|Nee| volstrekte_meerderheid

    zetels_over --->|Ja| bereken_partijen_met_grootste_gemiddelde

    subgraph grootste_gemiddelden["stelsel grootste gemiddelden"]
        bereken_partijen_met_grootste_gemiddelde --> voldoende_restzetels
        voldoende_restzetels -->|Ja| toekennen_restzetels
        voldoende_restzetels -->|Nee| loting_grootste_gemiddelden
        loting_grootste_gemiddelden --> toekennen_restzetels        
    end
    class grootste_gemiddelden greyFill;

    toekennen_restzetels --> zetels_over

    volstrekte_meerderheid -->|Ja| laatste_restzetels_samen

    laatste_restzetels_samen -->|Ja| loting_abs_meerderheid
    laatste_restzetels_samen -->|Nee| herverdeling_laatste_restzetel

    loting_abs_meerderheid --> herverdeling_laatste_restzetel

    volstrekte_meerderheid --->|Nee| flow_end

    herverdeling_laatste_restzetel ---> flow_end

```
