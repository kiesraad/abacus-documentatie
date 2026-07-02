# Pull Requests (PRs)

Het belangrijkste aan een goed PR-proces is dat het gebaseerd is op samenwerking en wederzijds vertrouwen. Hier moeten we alert op blijven, want asynchrone reviews in een tool zoals GitHub, dragen hier niet altijd aan bij.

Daarnaast is het belangrijk om het tempo in de feedback-loop te houden. Sync reviews en/of pair programmen zijn hier heel goed voor.

## Schrijven van een PR

Houd een PR klein en gericht op één onderwerp; splits ongerelateerde wijzigingen op. Grote mechanische wijzigingen (hernoemingen, herformatteren) gaan in een aparte PR, los van inhoudelijke wijzigingen. Lees de diff na voordat je een PR maakt en gebruik [Lefthook](GitHub-werkwijze.md) om formatting en linting lokaal af te vangen.

Beschrijf in de PR (zie ook het [PR-template](https://github.com/kiesraad/abacus/blob/main/.github/pull_request_template.md)):
- Wat is de scope van de wijzigingen? (voeg eventueel screenshots toe)
- Wat heb je getest? Met welke edge cases heb je expliciet rekening gehouden?
- Zijn er specifieke punten waarvan je wil dat de reviewers er zeker naar kijken?
- Zijn er specifieke mensen van wie je een review wil vanwege hun specialisatie?
- Heb je tips over hoe te testen? (bijvoorbeeld voor het inladen van specifieke data, hoe je bepaalde errors in de backend triggert, een link naar abacus-test.nl, etc.)

## Reviewen van een PR

In een review nemen we alle [kwaliteitsattributen](testen-en-kwaliteit.md#kwaliteitsattributen) uit "Testen en kwaliteit" mee:
- betrouwbaarheid
- bruikbaarheid
- beveiliging
- testbaarheid
- onderhoudbaarheid
- IT-bility (installatie, onderhoud, ondersteuning)

Let minstens op:
- scope van de wijzigingen
- kwaliteit van de code
- consistentie met omliggende code
- indeling van code in bestanden/componenten/modules
- edge cases
- test coverage
- documentatie (README, diagrammen, use cases)

Stel jezelf bij elke bevinding de vraag: verbetert het oplossen hiervan de betrouwbaarheid, beveiliging of onderhoudbaarheid genoeg om een nieuwe reviewronde te rechtvaardigen? Zo niet, vermeld dit dan duidelijk bij je opmerking of laat de opmerking geheel achterwege.

We werken liever met een paar grondige reviews dan met veel losse "drive-by" opmerkingen. Als je een PR reviewt, doe dan een volledige review in plaats van hier en daar een opmerking achter te laten.

## Comments en approvals op een PR

Als je alleen een gedeelte van de PR reviewt (bijv. alleen frontend), geef dat duidelijk aan in je commentaar.

Als je wijzigingen wil zien, gebruik je de "Request changes" optie. Als wijzigingen aan de PR niet noodzakelijk zijn, kies dan voor "Approve".

Resolven van comments gebeurt door de eigenaar van de PR. De eigenaar reageert bij wijzigingen aan de code met de commit hash en een eventuele toelichting. De commit message maakt ook duidelijk welke review comment(s) door de commit opgelost wordt.

De eigenaar van de PR beslist wanneer te mergen. Dit om te voorkomen dat er gemerged wordt wanneer er twee approvals zijn, maar de eigenaar van de PR nog wacht op een review van een specifiek persoon.
