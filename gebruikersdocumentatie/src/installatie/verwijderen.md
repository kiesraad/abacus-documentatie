# Abacus verwijderen

Dit zijn de instructies voor het verwijderen van Abacus op Windows en Linux.

> <i class="fa-solid fa-circle-exclamation"></i> **Let op**  
> Als je de database, back-ups en logbestanden ook verwijdert, gaan alle gegevens verloren, inclusief de aangemaakte verkiezingen, gebruikers en logbestanden. Kopieer deze bestanden eerst naar een andere plek als je ze toch wil bewaren.

## Op Windows

Ga naar **Instellingen** → **Apps** → **Geïnstalleerde apps**. Zoek vervolgens naar Abacus en klik op de drie stipjes om de app te verwijderen. Klik op **Ja** als je ook de database, back-ups en logbestanden wil verwijderen.

## Op Linux

Stop de Abacus-service, schakel de service uit en verwijder de bestanden. Herlaad daarna de systemd-configuratie.

```
sudo systemctl disable --now abacus.service
sudo rm /etc/systemd/system/abacus.service
sudo rm /usr/lib/systemd/system/abacus.service
sudo systemctl daemon-reload
```

Verwijder nu Abacus, en eventueel ook de database, back-ups en logbestanden in /var/lib/abacus.

```
sudo rm /usr/local/bin/abacus
sudo rm -Rf /var/lib/abacus/
```
