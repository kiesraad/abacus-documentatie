# Verschillen in de zetelverdeling tussen OSV2020 en Abacus

Er zijn twee verschillen in de implementatie van zetelverdeling tussen OSV2020 en Abacus:
1. Verdeling van restzetels bij minder dan 19 zetels en toepassing van zowel P 9 als P 10
2. Toewijzing restzetels aan uitgeputte lijsten na lijstuitputting

De verschillen en gevolgen ervan staan hieronder beschreven.

Deze verschillen komen overeen met de uitzonderingen die in de [differential fuzzer](https://github.com/kiesraad/abacus/blob/main/backend/apportionment/fuzz/fuzz_targets/differential_osv2020.rs) gedefineerd zijn. Deze fuzzer vergelijkt de uitkomsten van zetelverdeling tussen OSV2020 en Abacus.

## Verdeling van restzetels bij minder dan 19 zetels en toepassing van zowel P 9 als P 10

Als bij minder dan 19 zetels zowel artikel P 9 (volstrekte meerderheid) als P 10 (lijstuitputting) van de Kieswet worden toegepast, dan beschouwt OSV2020 de restzetel die vanwege P 9 is hertoegewezen, als onderdeel van de beperking dat een lijst maar één restzetel toegewezen kan krijgen bij grootste overschotten en bij grootste gemiddelden met afwijking. Abacus doet dit niet.

Er zijn dus uiterst zeldzame situaties waarin Abacus een restzetel toe zou wijzen aan de lijst met de volstrekte meerderheid, waar OSV2020 dat niet zou doen. Als zowel P 9 als P 10 worden toegepast tijdens de zetelverdeling, dan laat Abacus een duidelijke melding zien om contact op te nemen met de Kiesraad.


## Toewijzing restzetels aan uitgeputte lijsten na lijstuitputting

Tijdens zetelverdeling worden eerst alle zetels toegekend, daarna wordt lijstuitputting toegepast voor lijsten met meer zetels dan kandidaten. Deze vrijgekomen zetels gaan over naar andere lijsten door voortgezette toepassing van de regels voor het toewijzen van restzetel.

Bij het toewijzen van deze vrijgekomen zetels controleren OSV2020 en Abacus op een verschillend moment of de lijst waaraan een vrijgekomen zetel is toegewezen, beschikbare kandidaten heeft. OSV2020 wijst eerst alle vrijgekomen zetels toe en controleert dit pas aan het einde. Hierbij komen mogelijk weer zetels vrij vanwege lijstuitputting. OSV2020 blijft deze stappen herhalen totdat alle zetels zijn toegekend. (Of totdat er geen kandidaten meer zijn die in aanmerking komen voor een zetel.) Abacus daarentegen sluit al tijdens het toewijzen van de vrijgekomen zetels lijsten uit die geen beschikbare kandidaten meer hebben.

Deze verschillen in aanpak leiden niet tot een verschil in de uitkomst van de zetelverdeling. Ze leiden mogelijk wel tot een verschil in hoe vaak het CSB een loting uit moet voeren. Omdat OSV2020 eerst zetels toewijst en dan pas op lijstuitputting controleert, zal OSV2020 bij gelijke gemiddelden of overschotten om een loting vragen tussen lijsten, zelfs als geen of maar één van de lijsten nog beschikbare kandidaten hebben. Abacus zal in dat geval niet om een loting vragen, omdat Abacus nooit een vrijgekomen zetel zal toewijzen aan een lijst die daar geen beschikbare kandidaat voor heeft.
