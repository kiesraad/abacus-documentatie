# Beveiligingscertificaat

Abacus wordt geïnstalleerd met een TLS-beveiligingscertificaat, zodat alle gebruikers Abacus veilig kunnen gebruiken in de browser.

Het certificaat wordt automatisch geïnstalleerd tijdens de installatie van Abacus. Daarna installeer je het certificaat zelf op de clients, zodat alle clients `https` gebruiken en een veilige verbinding hebben met de server.

## Certificaat kopiëren

Eerst kopieer je het certificaat naar de clients.

- Op de server open je de installatiemap van Abacus. Voor Windows is dit standaard `C:\Gebruikers\<gebruikersnaam>\AppData\Roaming\Abacus` en voor Linux `/usr/local/bin/abacus`.
- Ga naar de map `tls`.
- Het bestand `ca.cer` is het certificaat voor Windows en webbrowsers, en het bestand `ca.pem` is het certificaat voor Linux. Er zijn twee manieren om het certificaat op de client te zetten:
  - Kopieer het naar een USB-stick en vervolgens naar een handige map op de client.
  - Typ in de browser `http://<ip-van-Abacus-server>/ca.cer` of `http://<ip-van-Abacus-server>/ca.pem` (dus bijvoorbeeld `http://192.168.1.10/ca.cer`) en druk op enter. Hiermee download je het certificaat direct van de Abacus-server.

## Certificaat installeren op Windows

Installeer het beveiligingscertificaat op de client door erop te dubbelklikken. Vervolgens klik je op **Certificaat installeren...**  en je twee keer op **Volgende**. Tot slot selecteer je **Voltooien**.

Als je wilt controleren of je het juiste bestand gebruikt, controleer je de SHA256-hash van het bestand via de commandline:

`certutil -hashfile C:\pad\naar\certificaat\ca.cer SHA256`

Deze hash kun je vergelijken met de SHA256-fingerprint die je in de command prompt ziet wanneer je de Abacus-server opstart.

**Let op:** mogelijk lukt het hiermee niet om het certificaat in de browser te gebruiken. Firefox gebruikt bijvoorbeeld een eigen certificaatbeheerder. Als het nog niet werkt, installeer je het certificaat in de browser volgens de instructies hieronder.

## Certificaat installeren op Linux

Voor verschillende Linux-distributies bestaan meerdere manieren om het certificaat te installeren. Hier wordt alleen de methode voor Debian en Ubuntu beschreven.

Kopieer het certificaat naar de map `/usr/local/share/ca-certificates`. Controleer de SHA256-hash van het bestand via de commandline:

```
openssl x509 -in ca.pem -noout -fingerprint -sha256
```

Vervolgens voeg je het certificaat toe aan de systeembrede certificaatset:

```
sudo update-ca-certificates
```

**Let op:** mogelijk lukt het hiermee niet om het certificaat in de browser te gebruiken. Firefox gebruikt bijvoorbeeld een eigen certificaatbeheerder. Als het nog niet werkt, installeer je het certificaat in de browser volgens de instructies hieronder.

## Installeren in de browser

Het is ook mogelijk om het beveiligingscertificaat te installeren in de browser die je gebruikt.

### Microsoft Edge

- Ga naar **Instellingen** → **Privacy, zoeken en services** → **Privacy** → **Certificaten beheren**.
- Klik op **Door u geïnstalleerd**, klik naast **Vertrouwde certificaten** op **Importeren** en selecteer het bestand `ca.cer`.
- Klik op **Openen** om het bestand direct te installeren.
- Vergelijk de SHA256-hash in het grijze vak met de SHA256-fingerprint die je in de command prompt ziet wanneer je de Abacus-server start.

### Google Chrome

- Ga naar **Instellingen** → **Privacy en beveiliging** → **Beveiliging** → **Certificaten beheren**.
- Klik op **Geïnstalleerd door jou**, klik naast **Vertrouwde certificaten** op **Importeren** en selecteer het bestand `ca.cer`.
- Klik op **Openen** om het bestand direct te installeren.
- Vergelijk de SHA256-hash in het grijze vak met de SHA256-fingerprint die je in de command prompt ziet wanneer je de Abacus-server start.

### Firefox

- Ga naar **Instellingen** → **Privacy en Beveiliging**. Helemaal onderaan de pagina klik je op **Geavanceerde instellingen**.
- Onder **Certificaten** klik je op **Certificaten beheren**. Klik op **Importeren...** en selecteer het bestand `ca.cer`.
- Vink **Deze CA vertrouwen voor het identificeren van websites** aan.
- Klik op **Weergeven** om de gegevens van het certificaat te bekijken in de browser. Vergelijk de SHA256-hash met de SHA256-fingerprint die je in de command prompt ziet wanneer je de Abacus-server start.
- Klik op **OK** om het certificaat te importeren.
