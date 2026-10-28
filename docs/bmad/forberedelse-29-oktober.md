# Matplan forberedelse til PRD 29 oktober 2026

Fredrik Aleksander Langbo · Gruppe G143 · IBE160 Programmering med KI

Forberedelsen samler research, behovshypoteser, diskusjonstemaer og konkrete krav til Matplan. Målet på torsdag er å kunne arbeide videre med et begrunnet Product Requirements Document (PRD). Lærerens beskjed krever research på forhånd, men sier uttrykkelig at PRD-en ikke må være ferdig. Ingen egen innleveringsfrist 29. oktober er bekreftet. [Beskjed publisert 26. oktober](https://himolde.instructure.com/courses/4498/discussion_topics/68671).

## Kort prosjektpresentasjon

Matplan er en webapplikasjon for studenter som vil finne middager og registrere hva de faktisk spiser. Brukeren kan velge en oppskrift, planlegge et måltid og føre faktisk spist mengde i en matdagbok. Andre måltider registreres manuelt, via strekkode eller med KI-forslag fra tekst og bilde. Forslag kontrolleres og bekreftes før lagring. Dagssummer, egne mål og historikk gir oversikt over registreringene.

Prosjektet bygger på eksisterende oppskrifter og en fungerende lokal demo. PRD-arbeidet skjer derfor delvis etter implementasjonen; dokumentasjonen skal ikke fremstille dette som en plan som fantes før koden. Produktbriefen ligger i kursrepoet G143-langbo, commit 418f750. Formuleringen «godkjent brief» i eldre arbeidsdokumenter viser til Fredriks godkjenning og dokumenterer ikke faglærerens godkjenning.

## Hva vi skal undersøke

| Behovshypotese | Hva vi trenger å lære | Hvordan undersøke det |
|---|---|---|
| Dobbeltføring mellom oppskrift og matdagbok skaper friksjon | Hvor brukeren i dag gjentar informasjon, og hvor ofte | Be tre studenter beskrive siste faktiske måltidsregistrering |
| En samlet arbeidsflyt gjør registrering enklere | Om brukeren finner veien fra oppskrift til registrert mengde | Observer hovedoppgaven uten muntlig veiledning |
| Valg mellom manuell registrering, tekst, bilde og kode er nyttig | Hvilken metode brukeren velger i ulike situasjoner | Vis konkrete oppgaver og spør hvorfor metoden velges |
| Egne API-nøkler kan gi lavere kostnad ved moderat bruk | Faktisk bruksmengde, tjenestekostnad og terskel for oppsett | Logg antall kall og kostnad uten nøkler eller privat matinnhold; sammenlign senere med et relevant abonnement |
| Mål og streaks motiverer brukeren | Om visningen oppleves nyttig, forvirrende eller pressende | Spør nøytralt etter testen; undersøk behov for å skjule streaks |

Dette er hypoteser fra produktbriefen, ikke funn fra gjennomførte intervjuer. Et lavere prisnivå eller bedre brukeropplevelse er ennå ikke påvist.

## Lignende løsninger

Leverandørenes offentlige hjelpesider er kontrollert 27. oktober 2026. Sammenligningen gjelder dokumenterte funksjoner, ikke egen praktisk utprøving av konkurrentene.

| Løsning | Dokumentert funksjon | Betydning for Matplan |
|---|---|---|
| MyFitnessPal | Premium har strekkodeskanning. Ukjente produkter kan legges inn manuelt. [Kilde](https://support.myfitnesspal.com/hc/en-us/articles/360032624771-How-to-use-the-Barcode-Scanner) | Strekkode er ikke en unik funksjon. Manglende produkt og feil treff må kunne håndteres. |
| MyFitnessPal Meal Planner | Premium+ lar brukeren planlegge og føre et måltid fra planen til dagboken med dato og porsjoner. Hjelpesiden oppgir seks tilgjengelige land; Norge er ikke på listen. [Kilde](https://support.myfitnesspal.com/hc/en-us/articles/34603055097869-How-to-use-the-Meal-Planner) | Koblingen plan–dagbok finnes allerede. Matplans verdi må undersøkes gjennom enkelhet og relevans for målgruppen. |
| Lifesum | AI Tracking er en Premium-funksjon med tekst, bilde og andre registreringsverktøy. Klassisk registrering er også tilgjengelig. [Kilde](https://help.lifesum.com/en/article/ai-tracking-how-does-it-work-15sw7rk/) | Flere registreringsmåter er ikke i seg selv et konkurransefortrinn. Matplan prioriterer en tydelig kontroll før lagring. |
| Notater eller regneark | Mulig alternativ som brukeren selv kan organisere | Ta med som sammenligningsgrunnlag i intervju; ikke anta at alle trenger en ny app. |

Konklusjon for PRD-en: Undersøk om Matplan gir mindre dobbeltarbeid og forståelig kontroll over registreringene. Ikke lov unike funksjoner, bedre nøyaktighet eller lavere pris uten målinger. Ingen nye funksjoner legges til bare fordi en konkurrent har dem.

## Forslag til prioritering

Produktbriefens førsteversjon beholdes. Prioriteringen under bestemmer rekkefølge på avklaring og kvalitetssikring, ikke hvilke avtalte funksjoner som fjernes.

1. Oppskrift → plan → faktisk spist mengde → korrekt dagssum. Dette er hovedflyten og grunnlaget for brukertesten.
2. Redigering, sletting, lagring og avgrensning mellom brukere. Feil her svekker hele oversikten.
3. Strekkode og KI-forslag med manuell reserveflyt. Det skal alltid være mulig å fortsette når integrasjonen svikter.
4. Mål, historikk og streaks. Regler og språk må være forståelige, særlig forskjellen på manglende føring og eksplisitt registrert nullinntak.

Treningslogging, klokker, sosiale funksjoner, automatisk prisoppdatering og integrasjon med andre kostholdsapper forblir utenfor førsteversjonen. Offentlig drift er ikke et bekreftet krav.

## Hovedscenario og akseptanse

En student velger en middag, legger én porsjon i planen og spiser en halv porsjon. Planleggingen endrer ikke dagboken. Når studenten velger «registrer som spist», vises dato, måltidstype og mengde til kontroll. Først etter bekreftelse lagres måltidet og dagssummen oppdateres. Studenten kan rette eller slette registreringen, og omlasting beholder dataene.

| Krav | Konkret akseptanse | Tilknytning til eksisterende PRD |
|---|---|---|
| Plan og faktisk inntak skilles | Planlegg et måltid og kontroller uendret sum. Bekreft halv porsjon og kontroller halvparten av oppskriftens næring. | K02–K03 |
| KI krever kontroll | Generer forslag, endre mengde og avbryt: ingen oppføring. Gjenta og bekreft: én oppføring med korrigert mengde. | K05 |
| Manglende data blir ikke null | Ukjent vare eller ufullstendig næring gir forklaring og manuell utfylling. | K04 |
| Matdagboken kan rettes | Endre mengde, kontroller sum, slett, kontroller sum igjen og last siden på nytt. | K03, K08 |
| Data tilhører riktig bruker | Konto B skal ikke kunne lese eller endre konto As oppføringer. | K08 |
| Streak har tydelige regler | Uferdig dag i dag bryter ikke rekken før dagen er slutt; historikken skiller manglende føring fra eksplisitt null. | K06–K07 |

Full kravliste og avgrensning finnes i [PRD-utkastet](prd.md). Akseptansekriteriene over er kontrolloppgaver, ikke en erklæring om at alle er kjørt i denne forberedelsen.

## Spørsmål og brainstorming til torsdag

| Tema | Anbefalt utgangspunkt | Hva må avklares |
|---|---|---|
| Målgruppe | Studenter som lager mat og ønsker enkel registrering | Stemmer dette med Fredriks erfaring og testpersonene? |
| Hovedverdi | Mindre dobbeltføring fra oppskrift til faktisk inntak | Er dette viktigere enn rask registrering av tilfeldig mat? |
| API-oppsett | Behold egen nøkkel som i briefen | Klarer målgruppen å konfigurere dette uten hjelp? |
| KI-usikkerhet | Vis estimat og krev kontroll | Forstår brukeren hva modellen faktisk har anslått? |
| Streak | Behold valgbare mål og intervaller | Bør visningen kunne skjules? Dette er et forslag, ikke et vedtatt nytt krav. |
| Kursprosessen | Beskriv ærlig at demoen allerede eksisterer | Hvordan ønsker faglærer at videre BMAD-arbeid dokumenteres? |
| Leveranse | Bruk det tildelte kursrepoet | Hvilken PRD-mal, mappe og eventuell frist skal brukes? |

Spør faglærer også om produktbriefen er faglig godkjent og om endelig frist og format for prosjekt og refleksjonsrapport. Dette er spørsmål klargjort for timen; ingen melding er sendt.

## Intervju og brukertest

Testen kan gjennomføres senere og er ikke et bekreftet krav før torsdag. Bruk tre voksne testpersoner fra målgruppen og fiktive måltider. Før bare anonyme notater P1–P3, ikke personlige kostholdsopplysninger.

Før demoen, spør: Hvordan bestemte du siste middag? Har du registrert matinntak før? Hva gjorde du sist, og hvor stoppet det opp? Hvilken informasjon måtte du skrive flere ganger? Unngå å spørre «ville ikke denne appen vært nyttig?».

Gi deretter oppgaven: «Finn en middag du kunne tenke deg å lage, registrer at du har spist en halv porsjon, og vis dagens kalorier.» Start tidtaking når oppgaven er gitt. Ikke veiled; noter eventuell hjelp. Stopp ved korrekt dagsoversikt.

Etterpå: Hva var uklart? Hva ville du gjort annerledes? Ville du brukt løsningen igjen, og hvorfor eller hvorfor ikke? Prøv deretter å rette en mengde og avbryte et KI-forslag. Dette undersøker forståelse av kontrollen, ikke kvaliteten på et personlig kosthold.

| Person | Dato og enhet | Tid på hovedoppgave | Uten hjelp | Korrekt sum | Vil bruke igjen | Observasjon og forbedring |
|---|---|---|---|---|---|---|
| P1 | Ikke gjennomført | — | — | — | — | — |
| P2 | Ikke gjennomført | — | — | — | — | — |
| P3 | Ikke gjennomført | — | — | — | — | — |

Effektmål fra briefen: minst to av tre fullfører uten hjelp innen tre minutter; minst to av tre ønsker å bruke løsningen igjen og kan beskrive nytten. Behold også negative funn. Fysisk kameraskanning prøves separat med faktisk etikett, avvist tillatelse og ukjent kode.

## Klart til torsdag

- [x] Gjeldende produktbrief og tidligere PRD gjennomgått.
- [x] Begge lokale repoer oppdatert fra GitHub 27. oktober; begge var allerede oppdatert.
- [x] Konkurrentresearch med primærkilder og konkrete konsekvenser for kravene.
- [x] Behovshypoteser, hovedscenario og akseptansekriterier klargjort.
- [x] Researchspørsmål, brainstorming og testopplegg klargjort.
- [ ] Fredrik legger til egen viktigste frustrasjon og eventuell mottatt tilbakemelding.
- [ ] Avklar lærerens PRD-format, leveringssted og eventuell frist i timen.

Ta frem denne filen, [produktbriefen](../../product-brief.md) og [PRD-utkastet](prd.md). For demonstrasjon følger oppstarten [demoens README](https://github.com/flangbo-himolde/matplan-ibe160/blob/main/demo/README.md); bruk fiktive eksempeldata. Hovedoppgaven kan vises manuelt uten KI-nøkkel. Ikke bruk tid på ny funksjonalitet før behov og prioriteringer er avklart.

## Arbeidslogg for denne forberedelsen

27. oktober 2026: Codex hentet siste Git-status, gjennomgikk eksisterende brief, PRD og arbeidsliste, undersøkte konkurrentenes offisielle dokumentasjon og laget denne forberedelsen. Fredriks personlige erfaringer og brukerintervjuer er ikke konstruert. Det er ikke gjort kodeendringer, kjørt nye produkttester eller foretatt formell innlevering. Den tidligere produktbriefen er beholdt uendret.
