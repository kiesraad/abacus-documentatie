# Zetelverdeling flowchart


## 19 of meer zetels

Lijstuitputting kan voorkomen in de gele stappen.

Als er er geen restzetels zijn, dus alle zetels toegekend worden tijdens "toedeling volledige zetels", dan zal een partij met een volstrekte meerderheid aan stemmen ook al de volstrekte meerderheid aan zetels hebben.


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

    restzetels{"restzetel(s)?"}

    bereken_partijen_met_grootste_gemiddelde("bereken partij(en) met grootste gemiddelde")
    voldoende_restzetels{voldoende<br/>restzetels?}
    loting_grootste_gemiddelden(loting)
    toekennen_restzetels("toekennen restzetel(s)")
    class toekennen_restzetels lijstuitputting

    restzetels_na_gemiddelden{"restzetel(s) over?"}

    volstrekte_meerderheid{lijst met<br/>>50% stemmen,<br/>maar niet zetels?}
    laatste_restzetels_samen{laatste restzetels<br/>samen?}
    loting_abs_meerderheid(loting)
    herverdeling_laatste_restzetel(herverdeling laatste restzetel)
    class herverdeling_laatste_restzetel lijstuitputting

    %% flow
    flow_start --> vaststellen_kiesdeler
    vaststellen_kiesdeler --> toedeling_volledige_zetels
    toedeling_volledige_zetels --> restzetels

    restzetels -->|Nee| flow_end
    restzetels -->|Ja| bereken_partijen_met_grootste_gemiddelde

    subgraph grootste_gemiddelden["grootste gemiddelden"]
        bereken_partijen_met_grootste_gemiddelde --> voldoende_restzetels
        voldoende_restzetels -->|Ja| toekennen_restzetels
        voldoende_restzetels -->|Nee| loting_grootste_gemiddelden
        loting_grootste_gemiddelden --> toekennen_restzetels        
    end
    class grootste_gemiddelden greyFill;

    toekennen_restzetels --> restzetels_na_gemiddelden

    restzetels_na_gemiddelden --->|Nee| volstrekte_meerderheid
    restzetels_na_gemiddelden --->|Ja| bereken_partijen_met_grootste_gemiddelde

    subgraph absolute_meerderheid["absolute meerderheid"]
        volstrekte_meerderheid -->|Ja| laatste_restzetels_samen
        laatste_restzetels_samen -->|Ja| loting_abs_meerderheid
        laatste_restzetels_samen -->|Nee| herverdeling_laatste_restzetel
        loting_abs_meerderheid --> herverdeling_laatste_restzetel
    end
    class absolute_meerderheid greyFill;

    volstrekte_meerderheid --->|Nee| flow_end
    herverdeling_laatste_restzetel ---> flow_end

```

## minder dan 19 zetels

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

    restzetels{"restzetel(s)?"}

    bereken_overschotten_van_partijen("bereken overschotten<br/>van partijen")
    gelijke_overschotten{onvoldoende<br/>restzetels<br/>bij gelijk<br/>overschot?}
    loting_grootste_overschotten(loting)
    gelijke_overschotten_ronde1("toekennen restzetel(s)")
    class gelijke_overschotten_ronde1 lijstuitputting

    restzetels_na_overschotten{"restzetel(s)<br/>over?"}

    bereken_gemiddelden_van_partijen(bereken gemiddelden<br/>van partijen)
    gelijke_gemiddelden{"onvoldoende<br/>restzetels<br/>bij gelijk<br/>gemiddelde?"}
    loting_grootste_gemiddelden_1(loting)
    restzetels_grootste_gemiddelden_1("toekennen restzetel(s)")
    class restzetels_grootste_gemiddelden_1 lijstuitputting

    restzetels_na_gemiddelden_1{"restzetel(s)<br/>over?"}

    bereken_partijen_met_grootste_gemiddelde("bereken partij(en) met grootste gemiddelde")
    voldoende_restzetels{voldoende<br/>restzetels?}
    loting_grootste_gemiddelden_2(loting)
    restzetels_grootste_gemiddelden_2("toekennen restzetel(s)")
    class restzetels_grootste_gemiddelden_2 lijstuitputting


    restzetels_na_gemiddelden_2{"restzetel(s)<br/>over?"}

    volstrekte_meerderheid{lijst met<br/>>50% stemmen,<br/>maar niet zetels?}
    laatste_restzetels_samen{laatste restzetels<br/>samen?}
    loting_abs_meerderheid(loting)
    herverdeling_laatste_restzetel(herverdeling laatste restzetel)
    class herverdeling_laatste_restzetel lijstuitputting

    %% flow
    flow_start --> vaststellen_kiesdeler
    vaststellen_kiesdeler --> toedeling_volledige_zetels

    toedeling_volledige_zetels --> restzetels
    restzetels --->|Nee| flow_end
    restzetels -->|Ja| bereken_overschotten_van_partijen

    subgraph grootste_overschotten["grootste overschotten"]
        bereken_overschotten_van_partijen --> gelijke_overschotten
        gelijke_overschotten -->|Nee| gelijke_overschotten_ronde1
        gelijke_overschotten -->|Ja| loting_grootste_overschotten
        loting_grootste_overschotten --> gelijke_overschotten_ronde1        
    end
    class grootste_overschotten greyFill;

    gelijke_overschotten_ronde1 --> restzetels_na_overschotten
    restzetels_na_overschotten -->|Nee| volstrekte_meerderheid
    restzetels_na_overschotten -->|Ja| bereken_gemiddelden_van_partijen

    subgraph grootste_gemiddelden_1["grootste gemiddelden - 1"]
        bereken_gemiddelden_van_partijen --> gelijke_gemiddelden
        gelijke_gemiddelden -->|Nee| restzetels_grootste_gemiddelden_1
        gelijke_gemiddelden -->|Ja| loting_grootste_gemiddelden_1
        loting_grootste_gemiddelden_1 --> restzetels_grootste_gemiddelden_1
    end
    class grootste_gemiddelden_1 greyFill;

    restzetels_grootste_gemiddelden_1 --> restzetels_na_gemiddelden_1
    restzetels_na_gemiddelden_1 -->|Nee| volstrekte_meerderheid
    restzetels_na_gemiddelden_1 -->|Ja| bereken_partijen_met_grootste_gemiddelde

    subgraph grootste_gemiddelden_2["grootste gemiddelden - 2"]
        bereken_partijen_met_grootste_gemiddelde --> voldoende_restzetels
        voldoende_restzetels -->|Ja| restzetels_grootste_gemiddelden_2
        voldoende_restzetels -->|Nee| loting_grootste_gemiddelden_2
        loting_grootste_gemiddelden_2 --> restzetels_grootste_gemiddelden_2      
    end
    class grootste_gemiddelden_2 greyFill;

    restzetels_grootste_gemiddelden_2 --> restzetels_na_gemiddelden_2

    restzetels_na_gemiddelden_2 -->|Ja| bereken_partijen_met_grootste_gemiddelde
     restzetels_na_gemiddelden_2 -->|Nee| volstrekte_meerderheid

    subgraph absolute_meerderheid["absolute meerderheid"]
        volstrekte_meerderheid -->|Ja| laatste_restzetels_samen
        laatste_restzetels_samen -->|Ja| loting_abs_meerderheid
        laatste_restzetels_samen -->|Nee| herverdeling_laatste_restzetel
        loting_abs_meerderheid --> herverdeling_laatste_restzetel
    end
    class absolute_meerderheid greyFill;

    volstrekte_meerderheid --->|Nee| flow_end
    herverdeling_laatste_restzetel ---> flow_end

```