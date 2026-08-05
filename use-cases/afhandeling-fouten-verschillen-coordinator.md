# Afhandeling fouten en verschillen door coördinator

Deze flowchart beschrijft hoe de coördinator (GSB of CSB) invoer met fouten of verschillen afhandelt.

Als de eerste invoer fouten bevat, moeten die opgelost worden. Dit betekent dat de tweede invoer alleen kan starten, nadat alle fouten die gedetecteerd zijn tijdens de eerste invoer, zijn opgelost.

Als de tweede invoer fouten bevat, heeft die dus per definitie verschillen met de eerste invoer. In dat geval moet de coördinator eerst de verschillen oplossen. Als de coördinator besluit de tweede invoer te behouden, dan moet als volgende stap de fouten opgelost worden.

Bij het oplossen van verschillen kan de coördinator er, in plaats van de afwijkende invoer helemaal opnieuw te laten doen, ook voor kiezen om alleen de afwijkende velden te laten corrigeren door de oorspronkelijke invoerder van die invoer. Bij de correctie worden de velden met verschillen leeggemaakt en gemarkeerd met waarschuwing. De invoerder kan in de correctie-invoer niet zien of nieuwe invoer afwijkt ten opzichte van de andere invoer. Komt de gecorrigeerde invoer na de correctie nog steeds niet overeen met de bewaarde invoer, dan moet de coördinator de verschillen opnieuw oplossen.

Correctie is alleen mogelijk voor een handmatige invoer. Een digitale invoer (bij het CSB is de eerste invoer geïmporteerd uit het tellingbestand van het GSB) kan niet gecorrigeerd worden, Abacus toont dan een melding. Alleen handmatig opnieuw invoeren is mogelijk.

Correctie is verder alleen mogelijk als de invoer die bewaard wordt zelf geen fouten bevat. Bevat de te bewaren invoer fouten, dan wordt de correctie-optie niet aangeboden en wordt er een melding getoond. Na bevestigen wordt de bewaarde invoer de eerste invoer en moeten de fouten daarin opgelost worden.

Een gecorrigeerde invoer kan wél nieuwe fouten bevatten. Daardoor kan ook de eerste invoer fouten bevatten op het moment dat de coördinator verschillen oplost. Ook dan geldt de regel hierboven: de invoer met fouten kan niet bewaard worden in combinatie met een correctie van de tweede invoer.


```mermaid
flowchart TD
    %% elements
    klaar-voor-eerste-invoer((klaar voor 1ste invoer))
    eerste-invoer-bezig(1ste invoer bezig)
    fouten{fouten?}
    invoer-met-fouten-en-waarschuwingen-1(invoer met fouten en waarschuwingen)
    fout-oplossen{fout oplossen}

    klaar-voor-tweede-invoer(klaar voor 2de invoer)
    tweede-invoer-bezig(2de invoer bezig)
    verschil-oplossen{verschil oplossen}
    verschil-met-eerste-invoer{verschil met 1ste invoer}
    invoer-met-fouten-en-waarschuwingen-2(invoer met verschillen)

    tweede-invoer-corrigeren(2de invoer corrigeren)
    eerste-invoer-corrigeren(1ste invoer corrigeren)
    gecorrigeerde-invoer-gelijk{invoer gelijk aan bewaarde invoer?}

    invoer-definitief((invoer definitief))

    %% flow
    klaar-voor-eerste-invoer --invoerder 1 pakt op --> eerste-invoer-bezig

    fouten -- nee --> klaar-voor-tweede-invoer
    
    subgraph sg-eerste-invoer[eerste invoer]
    eerste-invoer-bezig -- invoer afgerond --> fouten
    fouten -- ja --> invoer-met-fouten-en-waarschuwingen-1
    end

    invoer-met-fouten-en-waarschuwingen-1 --> fout-oplossen
    fout-oplossen -- terug naar de teltafel of corrigendum maken (en invoer opnieuw down) --> klaar-voor-eerste-invoer

    fout-oplossen -- lid GSB corrigeert PV, terug naar oorspronkelijke invoerder --> eerste-invoer-bezig

    
    klaar-voor-tweede-invoer -- invoerder 2 pakt op --> tweede-invoer-bezig

    subgraph sg-tweede-invoer[tweede-invoer]
    tweede-invoer-bezig -- invoer afgerond --> verschil-met-eerste-invoer
    verschil-met-eerste-invoer -- ja --> invoer-met-fouten-en-waarschuwingen-2
    end

    invoer-met-fouten-en-waarschuwingen-2 --> verschil-oplossen
    verschil-oplossen -- bewaar 1ste invoer, laat 2de opnieuw invoeren --> klaar-voor-tweede-invoer
    verschil-oplossen -- bewaar 2de invoer, 2de invoer wordt 1ste invoer --> fouten
    verschil-oplossen -- verwijder 1ste en 2de invoer --> klaar-voor-eerste-invoer

    subgraph sg-correctie[correctie]
    eerste-invoer-corrigeren
    tweede-invoer-corrigeren
    end

    verschil-oplossen -- bewaar 2de invoer, laat 1ste corrigeren (niet mogelijk wanneer 2de invoer fouten bevat of de 1ste invoer digitaal is) --> eerste-invoer-corrigeren
    verschil-oplossen -- bewaar 1ste invoer, laat 2de corrigeren (niet mogelijk wanneer 1ste invoer fouten bevat) --> tweede-invoer-corrigeren

    tweede-invoer-corrigeren -- correctie afgerond --> gecorrigeerde-invoer-gelijk
    eerste-invoer-corrigeren -- correctie afgerond --> gecorrigeerde-invoer-gelijk
    gecorrigeerde-invoer-gelijk -- ja (dus ook zonder fouten) --> invoer-definitief
    gecorrigeerde-invoer-gelijk -- nee (gecorrigeerde invoer kan fouten bevatten) --> verschil-oplossen

    verschil-met-eerste-invoer -- nee --> invoer-definitief

    %% styling
    classDef greyFill fill:#eee,stroke:#bbb;
    class sg-eerste-invoer,sg-tweede-invoer,sg-correctie greyFill;
    classDef yellowFill fill:#ffc943,stroke:#e8a302;
    class klaar-voor-eerste-invoer,invoer-definitief yellowFill;
```
