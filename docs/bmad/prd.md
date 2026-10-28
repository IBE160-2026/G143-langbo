# Kravgrunnlag – Matplan

Til PRD-arbeidet 29. oktober: [Research, behovshypoteser, prioritering, akseptansescenarioer og testplan](forberedelse-29-oktober.md), utarbeidet 27. oktober 2026. Kravlisten nedenfor er det eksisterende utgangspunktet. «Godkjent brief» viser her til Fredriks godkjenning; faglærerens godkjenning er ikke bekreftet.

Dato: 13. oktober 2026. Etterfølgende strukturering av [godkjent brief](../../product-brief.md), uten å endre briefens omfang. Ingen nye brukerintervjuer er gjennomført.

## Behov og hovedflyt

Primærbrukeren er en student som lager mat og ønsker enklere oversikt over faktisk matinntak. Antatt problem: oppskrift, planlegging og matregistrering krever dobbeltarbeid når de skjer hver for seg. Dette er en hypotese som må undersøkes i brukertesten, ikke et påvist behov hos tre intervjuede personer.

Brukeren finner en oppskrift, planlegger måltidet og registrerer faktisk spist mengde. Andre matvarer registreres manuelt, med strekkode, fritekst eller bilde. Brukeren kontrollerer forslagene før lagring og følger dagsmål og historikk.

## Krav og akseptanse

| ID | Krav | Akseptansekriterium |
|---|---|---|
| K01 | Matforslag og oppskrifter | 23 eksisterende oppskrifter kan åpnes; ingredienssøk, tidsfilter, favoritter og porsjonstilpasning er tilgjengelig. |
| K02 | Måltidsplan | Måltid knyttes til dato og porsjoner; planen endrer ikke dagssummer før faktisk inntak bekreftes. |
| K03 | Matdagbok | Registrering støtter dato, måltidstype, gram/ml/porsjoner og fire næringsverdier; oppføringer kan endres og slettes. |
| K04 | Strekkode | Én kode leses og slås opp; brukeren velger mengde og bekrefter. Manglende produkt eller næringsdata gir forståelig alternativ. |
| K05 | KI fra tekst/bilde | Én beskrivelse eller ett bilde gir redigerbare estimater. Et forslag alene skal aldri bli en dagbokoppføring. |
| K06 | Personlige mål | Brukeren kan velge dagsmål, intervaller og hvilke mål som teller i streaken. |
| K07 | Historikk og streak | Nåværende og lengste rekke følger valgte intervaller. Dagens uferdige mål bryter ikke før dagen avsluttes. Nullinntak og manglende registrering skilles. |
| K08 | Brukeravgrensning | Konto A kan ikke hente eller endre konto Bs måltider, planer eller favoritter. Data består etter omlasting. |
| K09 | Innstillinger for KI | Hver bruker legger inn egen leverandør, modell og nøkkel. Nøkkelen returneres ikke i datavisning eller lagres i repoet. |
| K10 | Tilgjengelig demo | Ny klone skal kunne startes etter README, med fiktive eksempeldata; grensesnittet skal fungere på mobilbredde og stor skjerm. |
| K11 | Tidligere prisgrunnlag | Lagrede Oda-/MENY-priser er merket som anslag/observasjoner med dato; de fremstår ikke som automatisk oppdaterte priser. |

K09 konkretiserer brukerens senere ønske om egen innstillingsside. Det endrer ikke løftet om kontrollerbare KI-forslag. Målene som vises ved kontooppretting er eksempeltall, ikke personlige kostholdsråd.

## Effektmål fra briefen

- Minst to av tre testpersoner velger oppskrift, registrerer mengde og finner dagsummen uten muntlig hjelp innen tre minutter.
- Minst to av tre ønsker å bruke løsningen igjen og kan forklare nytten.
- Alle fire registreringsmåter demonstreres; mengdeberegning, redigering, sletting og streakgrenser kontrolleres.

De to første målene er ikke evaluert. Automatiske tester og Codex-styrt nettlesertest er ikke en erstatning for test med målgruppen.

## Avgrensning og gjenbruk

Oppskrifter, ingredienssøk, porsjoner og lagrede priser kommer fra tidligere eksport. Nytt arbeid i demoen er personlig plan/dagbok, innlogging, lagring per bruker, KI- og strekkodeflyt, mål og streaks. Den gamle Flask-prototypen ligger i roten av arbeidsrepoet flangbo-himolde/matplan-ibe160; den er ikke den gjeldende produktarkitekturen. Demoens kode ligger foreløpig i arbeidsrepoet, ikke i dette kursrepoet.

Trening, klokker, sosiale funksjoner, integrasjoner med andre kostholdsapper og automatisk prisoppdatering inngår ikke. Offentlig drift og mobiltilgang over internett er ikke etablert. Det er ikke gjennomført klinisk eller ernæringsfaglig validering.
