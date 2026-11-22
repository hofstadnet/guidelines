# Websikkerhet

For nettsider og serverløse endepunkter.

## Hoder

- [ ] Content-Security-Policy med `default-src 'none'` og bare de kildene som trengs. Ingen `'unsafe-inline'` eller
      `'unsafe-eval'`.
- [ ] Ingen innebygd kode i HTML: skript og stilark ligger i egne filer. En kontroll i bygget stopper brudd.
- [ ] Trusted Types: `require-trusted-types-for 'script'`, og bare smale policyer med navn.
- [ ] HSTS med `includeSubDomains`, `X-Content-Type-Options: nosniff`, `Referrer-Policy`, `Permissions-Policy`,
      `Cross-Origin-Opener-Policy` og `Cross-Origin-Resource-Policy`.
- [ ] Rammer: `frame-ancestors 'none'` med mindre siden skal kunne bygges inn.
- [ ] Rapporter om brudd (`report-uri` og `report-to`) går til et eget endepunkt som ikke lagrer personopplysninger.

## Kode i nettleseren

- [ ] Ingen `innerHTML`, `outerHTML`, `insertAdjacentHTML` eller `document.write`. Elementer bygges med DOM-metoder.
- [ ] Tredjeparter (skript, rammer, skrift) lastes bare når de trengs, og helst først når brukeren ber om det.
- [ ] Ingen informasjonskapsler uten at det er nødvendig og beskrevet i personvernerklæringen.

## Serverløse endepunkter

- [ ] Bare metodene som trengs. Andre metoder avvises med 405.
- [ ] Ingen parametere fra forespørselen bestemmer hvor data hentes fra.
- [ ] Størrelsen på innkommende data er begrenset.
- [ ] Rate limiting per IP.
- [ ] Svar mellomlagres når det går, så trafikk ikke går videre til andre tjenester.
- [ ] Logger inneholder ikke IP, nettleserinfo, spørrestrenger eller innhold fra brukeren.
- [ ] Ingen hemmeligheter i koden. Trengs de, ligger de som secrets i plattformen.

## Domene

- [ ] DNSSEC, CAA med bare utstederne som brukes, og varsling ved nye sertifikater (Certificate Transparency).
- [ ] Domener som ikke sender e-post, har SPF uten avsendere, DMARC `p=reject` og «null MX» der det passer.
- [ ] Domenet er verifisert hos tjenester som ellers kan la andre ta i bruk underdomener (for eksempel GitHub Pages).
