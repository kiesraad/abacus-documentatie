# Installeren op Windows

Met deze methode installeer je Abacus op een Windows-computer.

**Let op:** Het beveiligingscertificaat wordt geïnstalleerd op Windows, en het bestand wordt in de map `tls` geplaatst in de installatiemap. Dit certificaat kun je daarna op alle computers installeren volgens de instructies in het hoofdstuk [Beveiligingscertificaat](./certificaat.md).

## Downloaden en installeren

Je downloadt Abacus via Rijkscloud SecureFileTransfer. Deze link krijg je van de Kiesraad Dubbelklik op het gedownloade bestand om het installatieprogramma te openen.

- Bij de pop-up sta je toe dat Abacus wijzigingen aan het apparaat aanbrengt.
- Het installatieprogramma kopieert alle bestanden, installeert Microsoft Visual C++ Redistributable en maakt het beveiligingscertificaat aan. Tot slot wordt de Abacus-service gestart.
- Nu kun je het installatieprogramma sluiten. Als je de Abacus-interface niet direct wil openen in de browser, zet dan eerst het vinkje uit.

> <i class="fa-solid fa-circle-exclamation"></i> **Let op**  
> De Abacus-service is nu actief en wordt automatisch opgestart wanneer de computer wordt aangezet.

## Starten

Bij deze installatiemethode worden twee snelkoppelingen op het bureaublad geplaatst:

- Met **Open Abacus in browser** open je de browserinterface.
- Met **Abacus data** open je de map met alle data, zoals de databasebestanden en back-ups.

**Let op:** Wanneer je de Abacus-server start, start Windows een zwart opdrachtvenster (command prompt). Je kunt dit venster minimaliseren, maar zorg ervoor dat het open blijft. Als je dit venster sluit wordt de Abacus-server gestopt.
