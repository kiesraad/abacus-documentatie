# Back-ups

Het kan handig zijn om een back-up te maken van de database in Abacus om dataverlies te voorkomen.

## Back-up maken

Back-up de bestanden als volgt:

- Zorg ervoor dat er geen invoerders bezig zijn met invoeren.
- Stop Abacus als de applicatie nog draait. Als je bezig bent met een zitting, wordt deze hervat zodra je Abacus weer start.
- Ga naar de map waarin Abacus is geïnstalleerd. In deze map staan ook de databasebestanden.
- Maak op een andere locatie een map aan met een handige naam en **kopieer** alle bestanden met `db.sqlite` in de naam naar deze map. **Let op:** verplaats de bestanden niet! Controleer na het kopiëren van de bestanden of de oorspronkelijke bestanden nog in de installatiemap staan.

## Back-up terugzetten

Als je de bestanden weer nodig hebt, kun je ze vanuit de back-uplocatie weer kopiëren naar de installatiemap.

- Zorg dat Abacus is gestopt en let erop dat er geen gebruikers ingelogd zijn.
- Verwijder alle bestanden met `db.sqlite` in de naam uit de installatiemap.
- Kopieer de back-upbestanden naar de installatiemap.
