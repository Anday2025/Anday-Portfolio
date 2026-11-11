# Anday Portfolio

Personlig portefølje for Anday Semere med fokus på IT-drift, IT-infrastruktur, Microsoft Azure og IT-sikkerhet.

## Teknologier og funksjoner

- HTML5, CSS3 og vanilla JavaScript, uten rammeverk, backend, database eller byggetrinn.
- Norsk og engelsk med umiddelbart språkbytte. Norsk er standard, og valgt språk lagres i `localStorage` når nettleseren tillater det.
- Responsiv layout, sticky navigasjon, automatisk aktiv seksjonsmarkering, mobilmeny og tastaturfokus.
- Fast introduksjon, ekte portrett og fire fagområder.
- Fire prosjektkort med separate detaljsider og bekreftede GitHub-lenker. Job Tracker og CleanPlan har lenker til de publiserte applikasjonene på detaljsidene.
- Sertifiseringer og kontaktkort for e-post, LinkedIn og GitHub.

Porteføljen krever ingen API-nøkler, tilgangstokener eller miljøvariabler. Teknologiene som beskrives på prosjektsidene tilhører de respektive prosjektene; de er ikke avhengigheter i denne porteføljen.

## Filstruktur

```text
Anday-Portfolio/
├── .gitignore
├── README.md
├── index.html
├── azure-storage.html
├── azure-bicep.html
├── job-tracker.html
├── cleanplan.html
├── styles.css
├── script.js
└── assets/
    ├── favicon.svg
    ├── icons.svg
    └── images/
        └── anday.webp
```

`assets/images/anday.webp` er det ekte portrettbildet, optimalisert for nett med bevart fargeprofil. Bildet har norsk og engelsk alt-tekst. SVG-ikonene lagres lokalt; det brukes ingen eksterne skrifter eller JavaScript-biblioteker.

## Lokal kjøring

Kjør fra mappen som inneholder `index.html`:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Åpne http://127.0.0.1:8000 og stopp serveren med Ctrl+C. Bruk HTTP fremfor å åpne HTML-filene direkte, slik at eksterne SVG-symboler lastes pålitelig.

Uten JavaScript vises norsk innhold; språkbytte, mobilmeny og automatisk seksjonsmarkering krever JavaScript.

## Kontroll før opplasting

- `.gitignore` utelukker miljøfiler, private nøkler, lokal konfigurasjon, IDE-filer, operativsystemmetadata og midlertidige filer.
- Ikke legg hemmeligheter i HTML, CSS, JavaScript, SVG eller bilder. Disse filene skal være offentlige. Kontaktopplysningene og portrettet er bevisst synlige på nettsiden.
- Kontroller repositoryrot og staging med `git rev-parse --show-toplevel`, `git status --short` og `git diff --cached --name-only` før en senere commit/opplasting.
- Hvis prosjektet ligger inne i et overordnet Git-repository, gjelder `.gitignore` i prosjektmappen bare denne mappen og dens undermapper. Ignore-regler må også finnes i den overordnede Git-roten for lokale filer der.
- `.gitignore` fjerner ikke filer som allerede spores eller ligger i staging. Slike filer må tas ut av staging/sporing uten å slette de lokale originalene.

## Azure Static Web Apps – senere publisering

Dette er en ferdig statisk nettside. Alle HTML-lenker, CSS-/JavaScript-referanser og bilde-/SVG-stier er relative og bruker filnavnenes nøyaktige store og små bokstaver. Hver prosjektside er en faktisk `.html`-fil; ingen SPA-ruting eller backend er nødvendig.

Når filene over ligger direkte i roten av GitHub-repositoryet, kan følgende verdier brukes i en senere Azure Static Web Apps-konfigurasjon:

```yaml
app_location: "/"
api_location: ""
output_location: ""
skip_app_build: true
```

Hvis repositoryet i stedet inneholder undermappen `Anday-Portfolio/`, skal `app_location` peke til `Anday-Portfolio`. Ikke sett `output_location` til `dist` eller `build`: prosjektet lager ingen slik mappe. `assets/` skal følge med sammen med HTML-filene.

Se [Microsofts dokumentasjon om byggekonfigurasjon](https://learn.microsoft.com/en-us/azure/static-web-apps/build-configuration#skip-building-front-end-app). Eventuelle fremtidige deployment-hemmeligheter skal lagres i GitHub Actions Secrets, ikke i kildekoden.

Dette dokumentet oppretter ingen workflow, kobler ingen kontoer og utfører ingen publisering. Azure-ressurser og GitHub-opplasting håndteres først i et eget, godkjent steg.

## Manuell kontroll

- Åpne alle fem sider og kontroller interne lenker, prosjektlenker og kontaktkort.
- Test NO/EN på forsiden og detaljsidene, også etter omlasting.
- Kontroller sticky header, aktiv meny ved rulling og mobilmeny.
- Kontroller portrett, fagområdekort og øvrig layout på PC, nettbrett og mobil.
- Kontroller tastaturnavigasjon, fokusmarkering og hopp til innhold.

Oversettelsene finnes i `script.js`. Ved senere innholdsendringer bør både oversettelsene og det statiske norske HTML-innholdet oppdateres.
