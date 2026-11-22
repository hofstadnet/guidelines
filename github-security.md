# GitHub-sikkerhet

## Organisasjon og repo

- [ ] Medlemmer har lesetilgang som standard. Skrivetilgang gis per repo eller team.
- [ ] Actions må være låst til commit-SHA (organisasjonsinnstilling).
- [ ] `GITHUB_TOKEN` har bare lesetilgang som standard, og arbeidsflyter kan ikke godkjenne pull requests.
- [ ] Secret scanning med push protection, Dependabot-varsler og sikkerhetsoppdateringer, og privat rapportering av
      sårbarheter er slått på.
- [ ] Offentlige repoer bruker gratis CodeQL og OpenSSF Scorecard.

## Regelsett for `main`

- [ ] Endringer krever pull request. Force-push og sletting er blokkert.
- [ ] Påkrevde sjekker: bygg eller test, `dependency-review` og `workflow-security` (zizmor).
- [ ] CodeQL-funn med høy alvorlighet eller mer stopper merge.
- [ ] Når en påkrevd jobb får nytt navn, oppdateres regelsettet i samme operasjon som merge.

## Arbeidsflyter

- [ ] Actions er låst til commit-SHA, med versjonen i en kommentar.
- [ ] `permissions: contents: read` på toppnivå. Jobber som trenger mer, ber om det selv.
- [ ] `actions/checkout` har `persist-credentials: false`.
- [ ] Verdier fra hendelser (titler, branch-navn, kommentarer) brukes via `env`, aldri direkte i `run`.
- [ ] `set -o pipefail` når utdata sendes videre med rør, så feil ikke skjules.
- [ ] Planlagte kjøringer som finner problemer, oppretter én issue og sjekker først om en åpen finnes.

## Avhengigheter

- [ ] Installasjon fra låsefil uten installasjonsskript (for npm: `npm ci --ignore-scripts`).
- [ ] Signaturkontroll av pakkene i bygget (for npm: `npm audit signatures`).
- [ ] Dependabot én gang i måneden, gruppert per økosystem, med `cooldown` på minst 7 dager.
- [ ] Automatisk merge bare for patch og minor, og bare når alle påkrevde sjekker er grønne. Major-versjoner og
      avhengigheter som endrer infrastruktur, merges manuelt.

## Hemmeligheter

- [ ] Ingen hemmeligheter i repoet. `.gitignore` stopper `.env` og nøkkelfiler.
- [ ] Hemmeligheter ligger som secrets, og bare jobbene som trenger dem, får dem.
- [ ] Endringer i produksjon (for eksempel apply av infrastruktur) kjører i et miljø med påkrevd godkjenning og bare
      fra `main`.
- [ ] Tokens har minst mulig tilgang og utløpsdato, og en planlagt jobb varsler før de utløper.
- [ ] Tjenestetokens eies av organisasjonen eller kontoen, ikke av en person, der tjenesten støtter det.
