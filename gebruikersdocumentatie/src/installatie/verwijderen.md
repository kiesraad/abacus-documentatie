# Abacus verwijderen

## Op Windows

Ga naar **Instellingen** → **Apps** → **Geïnstalleerde apps**. Zoek vervolgens naar Abacus en klik op de drie stipjes om de app te verwijderen. Klik op **Ja** als je ook de databasebestanden wil verwijderen.

## Op Linux

Stop de Abacus-service, schakel de service uit en verwijder de bestanden. Herstart daarna systemd.

```
sudo systemctl disable --now abacus.service
sudo rm /etc/systemd/system/abacus.service
sudo rm /usr/lib/systemd/system/abacus.service
sudo systemctl daemon-reload
```

Verwijder nu Abacus, en eventueel ook de databasebestanden in /var/lib/abacus.

```
sudo rm /usr/local/bin/abacus
sudo rm -Rf /var/lib/abacus/
```
