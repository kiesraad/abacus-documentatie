# Netwerk inrichten

Voordat je Abacus installeert is het belangrijk dat het netwerk goed is ingericht. Dit netwerk kun je op dezelfde manier opzetten als bij OSV2020, en je kunt Abacus en OSV2020 dan ook op dezelfde computer draaien. 

## Netwerk zonder internet

Je installeert Abacus op één computer die dient als server. De andere computers zijn clients en maken via de browser verbinding met de Abacus-server. Abacus mag alleen gebruikt worden in een netwerk dat niet verbonden is met het internet. Dit noemen we ook wel een *airgapped* netwerk. Volg daarom deze richtlijnen:

- Installeer de meest recente updates van het besturingssysteem voordat je de verbinding met het internet verbreekt.
- De computers die je gebruikt moeten worden aangesloten op een bedraad lokaal netwerk en mogen op geen enkele manier verbonden zijn met het internet.
Zorg dat alle aanwezige draadloze communicatiemodules zoals wifi en Bluetooth zijn gedeactiveerd.
- Op de computers zelf zet je de wifi-functie uit zodat er ook op die manier geen internetverbinding kan worden gemaakt.
- Zorg dat de datum en tijd van alle computers kloppen. Als de datum en tijd afwijken, kan dit onder andere leiden tot problemen met inloggen.

Meer informatie over de vereisten voor de computer en het besturingssysteem vind je in de [Aansluit- en gebruiksvoorschriften Wet programmatuur verkiezingsuitslagen](https://www.kiesraad.nl/verkiezingen/adviezen-en-publicaties/publicaties/2025/10/23/aansluit--en-gebruiksvoorschriften-wet-programmatuur-verkiezingsuitslagen) op de website van de Kiesraad.

## Testen

Wanneer Abacus op de server draait, noteer je dit IP-adres. Open vervolgens de browser op je client en ga naar dit IP-adres om te testen of de browser verbinding maakt met de Abacus-server. Maak ook een bladwijzer in de browser zodat je Abacus snel weer kunt openen. Dit doe je voor alle client-computers.

**Let op:** omdat er geen SSL-certificaat aanwezig is, staat in het IP-adres alleen *http* en niet *https*. Als je browser hier een beveiligingswaarschuwing over geeft, accepteer dan het risico en ga verder.
