# Instruks til Claude Code: oppdatering av Svev-nettsiden

## Kontekst

Dette er nettsiden til Svev, en Oslo-basert trio som spiller nordisk folkemusikk, tidligmusikk og elektronikk. Siden ligger på GitHub Pages.

Siden har to publikum, og de skal håndteres på hver sin side.

**Forsiden er en artistside.** Den skal presentere musikken på musikkens premisser. Den skal ikke selge, ikke prise, ikke forklare hvordan et innslag passer inn i et middagsprogram. Ingen call-to-action-bokser, ingen "book oss i dag".

**Bookingsiden er salgsverktøyet.** Der ligger formater, pris og praktisk informasjon.

Den viktigste besøkende er likevel den samme på begge sider: en norsk arrangements- eller kommunikasjonsansvarlig som har fått en lenke i en e-post. Det hun leter etter på forsiden er ikke argumenter, men tegn på at dette er et ekte, aktivt og seriøst ensemble: video fra en faktisk sal, navngitte spillesteder, ordentlige bilder. Kvaliteten på utførelsen er salgsargumentet. Én diskré lenke videre til booking er alt forsiden trenger å si om den siden av saken.

## Før du endrer noe

Les gjennom repoet og gi meg en kort oppsummering av hva som finnes: filstruktur, hvordan HTML og CSS er organisert, hvordan videokarusellen er bygget, hvilke assets som ligger der. Ikke begynn å skrive kode før jeg har sagt ok til planen.

## Ønsket resultat

Fire sider, flat struktur:

- `index.html` — forside, norsk, standard
- `booking.html` — bookingside, norsk
- `en/index.html` — forside, engelsk
- `en/booking.html` — bookingside, engelsk

Språkvelger øverst til høyre på alle fire. Enkel tekstlenke, ikke flagg. Legg inn `hreflang`-tagger som peker sidene til hverandre.

## Forsiden

Rekkefølge ovenfra:

1. Video, stor, øverst. Dette er det viktigste elementet på siden.
2. Én setning om hva Svev er, i bandets eget språk.
3. Navnene på de tre musikerne.
4. Lydfilene, som i dag.
5. **Live** — en liste over hvor trioen har spilt, med årstall. Dette er den delen en booker leser nøyest, men den skal skrives som en konsertoversikt, ikke som referanser i en salgspresentasjon.
6. Kontakt, med e-postadresse. Under den, én enkelt lenke: "Booking og forespørsler til arrangementer".

Teksten om bandet beholdes som den er, inkludert "experimental elements". Dette er artistsiden, og det ordet hører hjemme her.

Ingenting om pris, varighet, riggetid eller formater skal ligge på forsiden.

## Bookingsiden

Innholdet ligger ferdig i `svev-bookingside.md`, som jeg legger i repoet. Bruk den som kilde til tekst og struktur. Alt i klammer `[slik]` er plassholdere jeg fyller ut selv — la dem stå tydelig markert, ikke finn på innhold der.

Pristabellen skal være lett å lese på mobil. Ikke bruk en HTML-tabell som krever horisontal scrolling; stable radene i stedet på små skjermer.

## Tekniske krav

**Open Graph-tagger på alle sider.** Dette er viktigere enn det høres ut som. Lenken blir limt inn i e-poster og Teams-meldinger, og forhåndsvisningen der er ofte det første noen ser. Sett `og:title`, `og:description`, `og:image` (bruk bandbildet, minst 1200×630) og `og:url`. Legg inn tilsvarende Twitter-card-tagger.

**Videoen.** Den skal oppdateres senere, så bygg spilleren slik at filen er lett å bytte ut. Karusellen slik den er i dag lastet ikke da jeg testet siden utenfra — undersøk om den krever JavaScript som feiler, og forenkle den hvis den gjør det. Et enkelt `<video>`-element med `poster`-bilde er bedre enn en karusell som kan knekke. Hvis videofilen er over 20 MB, ikke legg den i git: bruk Vimeo eller YouTube og bygg inn.

**Lydfilene** skal ha `preload="none"` så de ikke laster på mobil før noen trykker play.

**Mobil først.** Halvparten leser dette på telefon i en pause.

**Ingen byggesteg, ingen rammeverk, ingen eksterne avhengigheter.** Ren HTML og CSS som GitHub Pages serverer direkte. Én felles CSS-fil for alle sider.

**Tilgjengelighet:** alt-tekst på bilder, ekte kontrast, semantiske overskriftsnivåer.

## Design

Behold den rolige, nedtonede tonen som er der i dag. Ikke gjør den til en typisk bedriftsside med knallfarget call-to-action-knapp. Målgruppen bestiller nettopp fordi uttrykket er dempet og seriøst, og siden skal se ut som musikken høres ut.

På forsiden skal lenken til booking være til stede, men underordnet. En vanlig tekstlenke nær kontaktinformasjonen, ikke en knapp og ikke over folden.

På bookingsiden kan det være tydeligere. Der vet leseren allerede hva hun er ute etter, og da er klarhet en tjeneste.

## Arbeidsmåte

Gjør dette i steg, med en commit per steg, ikke som én stor omskrivning:

1. Oppsummering av eksisterende struktur, og forslag til plan
2. Ny felles CSS og sidemal
3. Norsk forside
4. Norsk bookingside
5. Engelske versjoner
6. Open Graph, hreflang, metadata
7. Gjennomgang på mobilbredde

Kjør `python3 -m http.server` underveis så jeg kan se resultatet lokalt før noe pushes.

## Ikke rør

- Eksisterende lydfiler og bilder, med mindre du bare flytter dem
- Git-historikk
- `CNAME`, hvis den finnes

## Senere, ikke nå

Vi skal etter hvert over på domenet `svev.no`. Nevn gjerne hva som må gjøres i repoet når vi kommer dit, men ikke gjør det ennå.
