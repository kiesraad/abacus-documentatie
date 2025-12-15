# Meewerken als ontwikkelaar

Ben je ontwikkelaar en wil je Abacus handmatig installeren en gebruiken? Lees dan deze README-bestanden in de [Abacus repository](https://github.com/kiesraad/abacus):

- [Backend](https://github.com/kiesraad/abacus/tree/main/backend#readme)
- [Frontend](https://github.com/kiesraad/abacus/tree/main/frontend#readme)

Ook vind je daar meer informatie over de functionaliteit, architectuur en security van Abacus.

## Abacus installeren met Docker Compose (Linux, macOS, Windows)

Als ontwikkelaar kun je ook Docker gebruiken om Abacus te starten. Hiermee start je de backend in watch mode. Assets worden geserveerd door de build tool `vite` en maken dus gebruik van Hot Module Reloading:

```sh
docker compose up
```
