# Abacus releaseproces

## Een releasebranch aanmaken

- Maak een branch `release-MAJOR-MINOR` aan, bijvoorbeeld `release-1.1`.
- Voeg de nieuwe branch expliciet toe aan de [GitHub ruleset voor
  branches](https://github.com/kiesraad/abacus/settings/rules/500299).

## Wijzigingen backporten naar een releasebranch

(Voorbeelden voor versie 1.1)

- Pas eerst de `main`-branch aan via een pull request:
  - Volg het reguliere PR-proces, maar houd de wijzigingen zo klein mogelijk om
    het backporten naar de releasebranch eenvoudiger te maken.
  - Voeg het label `needs-backport/1.1` toe aan de PR.
- Maak een pull request om de mergecommit te backporten naar de releasebranch:
  - Maak een nieuwe branch aan op basis van de releasebranch.
  - `git cherry-pick <merge commit id>`
  - Open een PR met de releasebranch als doelbranch.
  - Voeg de releasemijlpaal '1.1 Herindelingsverkiezing 2026' toe aan de PR.
  - Verwijder het label `needs-backport/1.1` van de oorspronkelijke PR.
  - De issue kan na het samenvoegen worden gesloten.

## Een nieuwe release taggen

- Maak een Git-tag `vMAJOR.MINOR.PATCH` aan, bijvoorbeeld `v1.1.0`, volgens het
  principe van [Semantic Versioning](https://semver.org/). Push de tag naar
  GitHub.
  - Dit is momenteel beperkt tot repositorybeheerders. We kunnen overwegen een
    team van releasebeheerders aan te maken.
  - `git tag --sign v1.1.0`
  - `git push origin v1.1.0` (let op: "Bypassed rule violations" betekent dat
    push is gelukt, ook al lijkt de melding op een foutmelding).

## Release maken

- Wacht na aanmaken van een nieuwe tag totdat de releaseworkflow van GitHub
  Actions de uitvoerbare bestanden heeft gebouwd en getest. Dit zou een
  [GitHub-release](https://github.com/kiesraad/abacus/releases) moeten aanmaken.
- Bouw het installatieprogramma op een Windows-computer:
  - Kloon de Git-repository en check de tag uit.
  - Download de nieuwste Microsoft VC++ Redistributable via
    https://aka.ms/vc14/vc_redist.x64.exe.
  - Installeer de redistributable lokaal, zodat het Inno Setup-script het
    versienummer van Abacus kan bepalen.
  - Download het uitvoerbare Windows-bestand van Abacus van GitHub en hernoem het
    naar `abacus.exe`.
  - Controleer de hashes van de uitvoerbare bestanden (`Get-FileHash` in
    PowerShell).
  - Plaats de uitvoerbare bestanden (`abacus.exe`, `VC_redist.x64.exe`) in de map
    `.\packaging\windows` in de Git-repository van Abacus.
  - Compileer het Inno Setup-script met ondertekening ingeschakeld (verwijder de
    commentaarmarkeringen bij de configuratie voor ondertekening).
  - Bereken de hash van het gebouwde installatieprogramma: `Get-FileHash
    .\Output\abacussetup.exe`.
  - Hernoem het installatieprogramma `.\Output\abacussetup.exe` naar
    `abacus-windows-setup-v1.1.0.exe`.
- Bereken de SHA256-hashes opnieuw:
  - `sha56sum abacus-linux-v1.1.0.tar.gz abacus-windows-setup-v1.1.0.exe >
    SHA256SUMS`
- Upload het installatieprogramma en de bijgewerkte SHA256-hashes naar de
  GitHub-release en verwijder het gebouwde uitvoerbare Windows-bestand (dit is nu
  onderdeel van het installatieprogramma).
- Schrijf de releaseopmerkingen.
- Publiceer de release.
