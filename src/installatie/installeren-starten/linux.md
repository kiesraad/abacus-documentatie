# Linux

Met deze methode installeer je Abacus op een Linux-machine.

## Downloaden

- Op de hoofdpagina van de Abacus-repository klik je aan de rechterkant op [Releases](https://github.com/kiesraad/abacus/releases).
- Klik bij de bovenste release op `Assets` en klik vervolgens op het installatiebestand `abacus-linux-[versienummer].tar.gz` om het te downloaden.
- Pak de tarball uit:

```
tar -xvf abacus-linux-[versienummer].tar.gz ~/mapnaarkeuze/
```

## Installeren

Kopieer Abacus en het servicebestand naar de juiste mappen:

```
sudo cp abacus /usr/local/bin/abacus
sudo cp abacus.service /etc/systemd/system/abacus.service
```

Maak Abacus uitvoerbaar:

```
sudo chmod +x /usr/local/bin/abacus
```

Laad systemd opnieuw en schakel de service in, zodat Abacus direct start en bij het opstarten van het systeem wordt gestart:

```
sudo systemctl daemon-reload
sudo systemctl enable --now abacus.service
```

## Beheren

Zo bekijk je het service-logboek:

```
sudo journalctl -u abacus.service
```

Stop de Abacus-service:
```
sudo systemctl stop abacus.service
```

Start de Abacus-service:
```
sudo systemctl start abacus.service
```

De database vind je in `/var/lib/abacus/`.
