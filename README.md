# Retningslinjer

Felles regler og sjekklister for repoer, for både mennesker og kodeagenter. Retningslinjene er skrevet generelt,
uten navn på bestemte organisasjoner, domener eller tjenester, slik at de kan brukes i flere organisasjoner.

| Retningslinje | Gjelder |
|---|---|
| [naming.md](naming.md) | Navn på filer, mapper, kode, arbeidsflyter, tokens og ressurser |
| [documentation.md](documentation.md) | Hvordan dokumentasjon skrives og holdes oppdatert |
| [github-security.md](github-security.md) | Regelsett, GitHub Actions, avhengigheter og hemmeligheter |
| [web-security.md](web-security.md) | Sikkerhetshoder, CSP, Trusted Types og serverløse endepunkter |
| [infrastructure.md](infrastructure.md) | Infrastruktur som kode med OpenTofu, med Cloudflare som eksempel |
| [accessibility-ux.md](accessibility-ux.md) | Tilgjengelighet, visning, ytelse og visuelle tester |
| [agents.md](agents.md) | Oppsett for kodeagenter: `AGENTS.md`, `CLAUDE.md` og lokale retningslinjer |

## Ta i bruk i et repo

1. Kopier [templates/AGENTS.md](templates/AGENTS.md) til roten av repoet og fyll inn prosjektet og kommandoene.
2. Legg til `CLAUDE.md` med én linje: `@AGENTS.md`.
3. Legg regler som bare gjelder repoet, i `docs/guidelines/` i repoet. Lenk til retningslinjene her for resten, i
   stedet for å kopiere dem.
4. Følg [github-security.md](github-security.md) for regelsett og arbeidsflyter.

## Prinsipper

- **Uavhengig av verktøy.** Retningslinjene er vanlig Markdown. Verktøyspesifikke filer er bare tynne pekere hit.
- **Generelt her, spesielt lokalt.** Det som gjelder ett repo (stier, domener, tjenester), står i repoet.
- **Kontrollerbart.** Der det går, håndheves reglene av regelsett, arbeidsflyter eller tester, ikke bare av tekst.

## Endringer

Endringer går via pull request. Repoer som lenker hit, følger alltid siste versjon på `main`. En endring som krever
tiltak i repoene, beskrives i pull requesten.
