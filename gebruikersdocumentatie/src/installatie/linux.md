# Installeren op Linux

Met deze methode installeer je Abacus op een Linux-computer.

De installatiemethode voor Linux werkt op alle gangbare (recente) Linux-distributies en zijn getest op Ubuntu (24.04 en 26.04) en Debian (13/trixie).

> <i class="fa-solid fa-circle-exclamation"></i> **Let op**  
> Het beveiligingscertificaat wordt tijdens de installatie in de map `/var/lib/abacus/tls` geplaatst. Dit certificaat kun je daarna op alle computers installeren volgens de instructies in het hoofdstuk [Beveiligingscertificaat](./certificaat.md).

## Downloaden

Je downloadt Abacus via het overdrachtsplatform Uitwisseling. Pak de tarball uit:

```
tar -xvf abacus-linux-[versienummer].tar.gz -C ~/mapnaarkeuze/
```

## Installeren

Ga naar de map met de uitgepakte bestanden en kopieer Abacus en het servicebestand naar de juiste mappen:

```
cd ~/mapnaarkeuze/abacus-linux-[versienummer]
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
