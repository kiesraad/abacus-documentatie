# Netwerk inrichten

Voordat je Abacus installeert is het belangrijk dat het netwerk goed is ingericht. Dit netwerk kun je op dezelfde manier opzetten als bij OSV2020, en je kunt Abacus en OSV2020 dan ook op dezelfde computer draaien.

Je installeert Abacus op één computer die dient als server. De andere computers zijn clients en maken via de browser verbinding met Abacus.

## Netwerk zonder internet

Abacus mag alleen gebruikt worden in een netwerk dat niet verbonden is met het internet. Dit noemen we ook wel een *airgapped* netwerk. Volg daarom deze richtlijnen:

- Zorg ervoor dat de computers die je gebruikt zijn aangesloten op een bedraad lokaal netwerk dat op geen enkele manier verbonden is met het internet.
- Op de computers zelf zet je wifi uit zodat er ook op die manier geen internetverbinding kan worden gemaakt.
- Zorg dat de de datum en tijd van alle computers kloppen. Als de datum en tijd afwijken, kan dit leiden tot problemen met inloggen en andere foutmeldingen.

## Testen

Wanneer Abacus op de server draait, kopieer je het IP-adres. Open vervolgens de browser op je client en ga naar het IP-adres om te testen of de browser verbinding maakt met de Abacus-server. Maak ook een bladwijzer in de browser zodat je Abacus snel weer kunt openen. Dit doe je voor alle client-computers.

**Let op:** omdat er geen certificaat aanwezig is, staat in het IP-adres alleen *http* en niet *https*. Als je browser hier een beveiligingswaarschuwing over geeft, accepteer dan het risico en ga verder.
