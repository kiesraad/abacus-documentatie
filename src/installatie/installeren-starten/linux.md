# Linux

Met deze methode installeer je Abacus op een Linux-machine.

## Downloaden

- Je downloadt Abacus via Rijkscloud SecureFileTransfer. Deze link krijg je van de Kiesraad.
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

Laad systemd opnieuw en schakel de service in:

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
