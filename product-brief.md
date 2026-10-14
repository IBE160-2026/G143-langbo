# Product Brief: Matplan

**Fredrik Aleksander Langbo · IBE160 Programmering med KI · Høsten 2026**

## Sammendrag

Matplan er en webapplikasjon for folk som vil ha hjelp til å velge måltider og holde oversikt over det de faktisk spiser. Den samler matforslag, oppskrifter, enkel måltidsplanlegging og en personlig matdagbok med kalorier, protein, karbohydrater og fett. Målet er å gjøre veien fra middagsidé til registrert måltid enklere og gi oversikt over egne kostholdsvaner.

Prosjektet videreutvikler en eksisterende løsning for middagsforslag. I IBE160 bygges den personlige registreringen og oppfølgingen, med strekkodeskanning, tolkning av fritekst og matbilder med KI, samt streaks for sammenhengende dager med oppnådde mål. KI-forslag skal kunne korrigeres og bekreftes før lagring. Den eksisterende oppskriftsdelen gir et konkret utgangspunkt for å undersøke om denne samlede arbeidsflyten gjør daglig matregistrering lettere.

## Problemet

I etablerte kostholdsapper som Lifesum og MyFitnessPal ligger funksjoner tilsvarende dem Matplan skal tilby, ofte bak abonnementer som kan være dyre for en student. Ved å bruke egne API-nøkler til KI-tjenester kan kostnaden bli lavere ved moderat bruk, avhengig av tjeneste og bruksmengde. Samtidig er det ønskelig å samle matforslag, oppskrifter, måltidsplanlegging og registrering av faktisk matinntak i én app. Matplan skal undersøke om denne kombinasjonen kan gi et rimeligere og mer sammenhengende alternativ, fra middagsidé til matdagbok og måloppfølging.


## Løsningen

Brukeren velger en oppskrift og legger den i en enkel måltidsplan. Etter måltidet registreres faktisk spist mengde direkte fra oppskriften. Annen mat kan legges inn manuelt, ved å skanne en strekkode, skrive en beskrivelse eller ta et bilde. En språkmodell eller modell med bildestøtte foreslår matvarer, mengder og næringsinnhold; brukeren kontrollerer forslaget før det føres i matdagboken.

Dashboardet viser dagssummer, personlige dagsmål og historikk. Streaks viser nåværende og lengste rekke av dager der brukerens valgte mål er nådd innenfor egne toleranseintervaller. Planlagte måltider telles først når de registreres som spist. KI-beregninger merkes som estimater, og manuell registrering er tilgjengelig ved manglende produktdata eller tjenestefeil.

## Hva som skiller løsningen

Alternativene er blant annet egne notater, regneark og etablerte kostholdsapper som Lifesum og MyFitnessPal, som også er inspirasjon for prosjektet. Matplans ambisjon er en enkel, sammenhengende arbeidsflyt fra egen oppskriftssamling til faktisk matinntak og måloppfølging. Prosjektet skal ikke konkurrere på størst produktdatabase. Den mulige verdien ligger i mindre dobbeltarbeid og valgfri registreringsmåte, og skal undersøkes gjennom brukertesting.

## Målgruppe

Primærbrukeren er en student som lager mat selv, ønsker middagsinspirasjon og vil følge egne mål uten omfattende manuell føring. Andre voksne med samme behov er en sekundær målgruppe. For brukeren betyr en vellykket løsning at et måltid er enkelt å registrere, og at dagens oversikt er lett å forstå og korrigere.

## Suksesskriterier

Følgende mål evalueres før prosjektlevering:

- **Enkel bruk:** Minst to av tre testpersoner fra målgruppen skal uten muntlig hjelp kunne velge en oppskrift, registrere spist mengde og finne dagens totalsum innen tre minutter.
- **Opplevd nytte:** Etter en kort utprøving skal minst to av tre testpersoner ønske å bruke løsningen igjen og kunne forklare hvilken del som gjør matregistrering enklere.
- **Pålitelig registrering:** Manuell føring, strekkode, fritekst og bilde skal hver demonstreres fra registrering til lagret måltid. Alle KI-forslag krever bekreftelse. Tester av mengdeberegning, redigering, sletting og streakgrenser skal bestå, og data skal beholdes etter omlasting.
- **Etterprøvbart studieprosjekt:** En annen person skal kunne starte og prøve løsningen med testdata ut fra README. Utviklingen med KI, sentrale valg og kvalitetssikring dokumenteres fortløpende i repoet gjennom BMAD-arbeidet.

## Omfang

**Første versjon** omfatter matforslag og oppskrifter, favoritter, enkel måltidsplan, personlig matdagbok med faktisk spist mengde, kalorier og makroer, dagsmål og historikk. Strekkodeskanning, registrering fra fritekst og matbilder samt streaks inngår. Lagring og tilgang avgrenses til riktig bruker, og grensesnittet tilpasses mobil og større skjerm. Integrasjonene holdes enkle: ett produkt, én tekstbeskrivelse eller ett bilde om gangen.

Brukeren velger hvilke mål og intervaller som teller for streaken. En avsluttet dag uten registrering eller måloppnåelse bryter rekken; pågående dag bryter den først når dagen er avsluttet. Historikken skiller manglende registrering fra registrert nullinntak.

**Eksisterende grunnlag og nytt arbeid:** Den eksisterende eksporten av middagsdelen inneholder 23 oppskrifter, ingredienssøk, tidsfilter, porsjonstilpasning, næringsanslag og prissammenligning fra lagrede Oda- og MENY-data. Dette er tidligere arbeid som kan gjenbrukes. Nyutviklingen i IBE160 omfatter den personlige måltidsplanen og matdagboken, lagring og tilgang, mål og historikk, strekkode, KI-tolkning av tekst og bilder samt streaks.

**Utenfor første versjon** ligger treningslogging, aktivitetsklokker, sosiale funksjoner, direkte integrasjon med andre kostholdsapper og automatisk oppdatering av butikkpriser. Endelig rammeverk, database og tjenesteleverandører velges i den videre planleggingen.

## Visjon

Hvis den første versjonen viser nytte, kan Matplan over to til tre år bli en personlig matassistent som knytter sammen preferanser, hverdagsplanlegging og erfaringer fra tidligere måltider. Videre utvikling kan gjøre oppskriftsforslagene mer relevante og registreringen enklere, basert på brukernes tilbakemeldinger. Brukeren skal fortsatt kunne forstå og korrigere grunnlaget for egen oversikt.
