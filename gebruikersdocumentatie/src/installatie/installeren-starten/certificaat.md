# Beveiligingscertificaat

Abacus wordt geïnstalleerd met een TLS-beveiligingscertificaat, zodat alle gebruikers Abacus veilig kunnen gebruiken in de browser.

Het certificaat wordt automatisch geïnstalleerd tijdens de installatie van Abacus. Daarna zorg je zelf dat het certificaat ook wordt geïnstalleerd op alle clients, die dan `https` gebruiken en een veilige verbinding hebben met de server.

## Installeren op Windows

- Op de server open je de installatiemap van Abacus (standaard is dit `C:\Gebruikers\<gebruikersnaam>\AppData\Roaming\Abacus`) en ga je naar de map `tls`.
- Het bestand `ca.cer` is het certificaat voor Windows en webbrowsers. Kopieer het en zet het op een USB-stick.
- Op de client dubbelklik je op het certificaat om het te installeren.

Als je wilt controleren of je het juiste bestand gebruikt, controleer je de SHA256-hash van het bestand via de commandline:

`certutil -hashfile C:\pad\naar\certificaat\ca.cer SHA256`

Deze hash kun je vergelijken met de *SHA256 fingerprint* die je in de command prompt ziet wanneer je de Abacus-server opstart.

**Let op:** mogelijk lukt het hiermee niet om het certificaat in de browser te gebruiken. Firefox gebruikt bijvoorbeeld een eigen certificaatbeheerder. Als het nog niet werkt, installeer je het certificaat in de browser volgens de instructies hieronder.

## Installeren op Linux

Voor verschillende Linux-distributies bestaan meerdere manieren om het certificaat te installeren. Hier wordt alleen de methode voor Debian en Ubuntu beschreven.

- Op de server ga je naar de map `tls` in de installatiemap van Abacus.
- Het bestand `ca.pem` is het certificaat voor Linux. Kopieer het en zet het op een USB-stick.
- Op de client kopieer je het bestand naar de map `/usr/local/share/ca-certificates`. Controleer de SHA256-hash van het bestand via de commandline:

```
openssl x509 -in ca.pem -noout -fingerprint -sha256
```

- Vervolgens voeg je het certificaat toe aan de systeembreede certificaatset:

```
sudo update-ca-certificates
```

**Let op:** mogelijk lukt het hiermee niet om het certificaat in de browser te gebruiken. Firefox gebruikt bijvoorbeeld een eigen certificaatbeheerder. Als het nog niet werkt, installeer je het certificaat in de browser volgens de instructies hieronder.

## Installeren in de browser

Het is ook mogelijk om het beveiligingscertificaat alleen te installeren in een browser.

### Microsoft Edge

- Ga naar **Instellingen** → **Privacy, zoeken en services** → **Privacy** → **Certificaten beheren**.
- Klik op **Door u geïnstalleerd**, klik naast **Vertrouwde certificaten** op **Importeren** en selecteer het bestand `ca.cer`.
- Klik op **Openen** om het bestand direct te installeren.
- Vergelijk de SHA256-hash in het grijze vak met de fingerprint die je ziet wanneer je de Abacus-server start.

### Google Chrome

- Ga naar **Instellingen** → **Privacy en beveiliging** → **Beveiliging** → **Certificaten beheren**.
- Klik op **Geïnstalleerd door jou**, klik naast **Vertrouwde certificaten** op **Importeren** en selecteer het bestand `ca.cer`.
- Klik op **Openen** om het bestand direct te installeren.
- Vergelijk de SHA256-hash in het grijze vak met de fingerprint die je ziet wanneer je de Abacus-server start.

### Firefox

- Ga naar **Instellingen** → **Privacy en Beveiliging**. Helemaal onderaan de pagina klik je op **Geavanceerde instellingen**.
- Onder **Certificaten** klik je op **Certificaten beheren**. Klik op **Importeren...** en selecteer het bestand `ca.cer`.
- Vink **Deze CA vertrouwen voor het identificeren van websites** aan.
- Klik op **Weergeven** om de gegevens van het certificaat te bekijken in de browser. Vergelijk de SHA256-hash met de fingerprint die je ziet wanneer je de Abacus-server start.
- Klik op **OK** om het certificaat te importeren.
