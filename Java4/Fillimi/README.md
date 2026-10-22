# Java IV — Festivali që përshtatet në çdo ekran

## Çfarë mëson

Flexbox, Grid, media queries dhe pamje responsive.

Referencë tematike: kap. 6–7 të librit.

## Skenari

Programi i një festivali shkencor duhet të lexohet si në telefon ashtu edhe në ekran të gjerë.

## Kërkesat

1. Krijo gjashtë karta aktivitetesh dhe një menu fleksibile.
2. Përdor Grid: një kolonë nën 600 px, dy nga 600 deri në 899 px dhe tri nga 900 px.
3. Kartat kanë titull, kategori, orar dhe lidhje detajesh; teksti i gjatë nuk duhet të dalë jashtë.
4. Përdor imazh fleksibël dhe mos përdor lartësi fikse për tekstin.
5. Testo në 360, 768 dhe 1280 px; ruaj rezultatet në README.

## Rastet e pranimit

- [x] Në 360/768/1280 px shfaqen përkatësisht 1/2/3 kolona.
- [x] Nuk ka scroll horizontal në faqen e plotë.
- [x] Menuja mbetet e përdorshme me tastierë.

## Sfida e transferimit

Një titull 100-karakterësh duhet të përshtatet pa prishur kartën. Kjo sfidë është formuese; nuk jep bonus jashtë rubrikës.

Titulli i kartës së parë ka 100 karaktere. Me `overflow-wrap: anywhere` dhe `minmax(0, 1fr)` teksti mbështillet brenda kartës; karta nuk zgjerohet dhe faqja nuk merr scroll horizontal.

## Çfarë realizova

Një faqe statike me programin e Festivalit të Shkencës në Kampus:

- menu me Flexbox që mbështillet në ekran të ngushtë;
- gjashtë karta aktivitetesh (kategori, titull, orar, lidhje detajesh);
- Grid me 1 / 2 / 3 kolona sipas gjerësisë;
- ilustrim SVG që zvogëlohet me `max-width: 100%` dhe `height: auto`;
- teksti pa lartësi fikse, që rritet sipas përmbajtjes.

Skedarët: `index.html`, `style.css`, `README.md`. Nuk ka JavaScript.

## Hapat e hapjes

1. Hap dosjen `Java4/Fillimi`.
2. Hap `index.html` në shfletues (dopio-klik, ose Live Server në VS Code/Cursor).
3. Në DevTools (F12) zgjidh Toggle device toolbar dhe vendos gjerësinë 360, pastaj 768, pastaj 1280.
4. Provo Tab për të ecur nëpër menu dhe Enter për të hapur një lidhje.

Nuk kërkohet instalim pakete, as server. Nëse do server lokal: `python -m http.server 8765` nga kjo dosje, pastaj `http://127.0.0.1:8765/`.

## Testet

| Hyrje | Rezultat i pritur | Rezultat i marrë |
|---|---|---|
| Viewport 360 px | 1 kolonë; pa scroll horizontal | 1 kolonë (`grid-template-columns: 1fr`); `scrollWidth` = 360; pa overflow |
| Viewport 768 px | 2 kolona; pa scroll horizontal | 2 kolona (`repeat(2, minmax(0, 1fr))`); `scrollWidth` = 768; pa overflow |
| Viewport 1280 px | 3 kolona; pa scroll horizontal | 3 kolona (`repeat(3, minmax(0, 1fr))`); pa overflow; kartat në tre pozicione X |
| Titull 100 karakterësh në kartën e parë | Teksti mbështillet; karta nuk prishet | Titulli 100 karaktere; `overflow-wrap: anywhere`; nuk del jashtë kartës |
| Tab / Enter në menu | Fokus i dukshëm; lidhjet hapin seksionin | Lidhjet janë `<a href="#...">`; Tab lëviz nga njëra te tjetra; Enter/klik çon te karta ose te detajet |
| Klik «Shiko detajet» | Shkon te përshkrimi i aktivitetit | URL bëhet p.sh. `#detaje-moti` dhe faqja lëviz te seksioni |

## Reflektim individual

Kur do të zgjidhje Flexbox dhe kur Grid?

**Flexbox** e përdora për menu dhe për bllokun hero (tekst + imazh). Këto janë rreshta ose kolona të një drejtimi: lidhjet e menusë duhet të rreshtohen, të mbështillen dhe të mbajnë hapësirë të barabartë. Flexbox është i përshtatshëm kur nuk di sa elemente do të ketë dhe do që të rrjedhin natyrshëm.

**Grid** e përdora për gjashtë kartat. Këtu kemi një rrjetë dy-dimensionale: kolona dhe rreshta që ndryshojnë sipas gjerësisë (1, 2 ose 3 kolona). Grid e bën këtë me `grid-template-columns` dhe media query, pa i grupuar kartat me dorë.

Në përmbledhje: Flexbox për shirit, menu dhe rresht me dy pjesë; Grid për katalog, galeri ose program me karta të rregullta.

## Deklarim i AI dhe burimeve

- **AI:** Cursor (Grok) ndihmoi për strukturën e `index.html`/`style.css`, për media query-t 600/900 px, për titullin 100-karakterësh dhe për këtë README. Unë e lexova kërkesën, e hapa faqen dhe e kontrollova në 360/768/1280 px.
- **Burime:** fletë e ushtrimit Java IV; kap. 6–7 (Flexbox, Grid, media queries); stili vizual i javëve të mëparshme (system-ui, theks i gjelbër, skip-link).
- **Nuk u përdorën:** imazhe të jashtme, biblioteka CSS/JS, `node_modules`.

## Dorëzimi dhe GitHub

Puno në JavaIV/ të repository-t individual. Dorëzo kodin, asetet lokale dhe README.md me: çfarë realizove, hapat e hapjes, hyrje → rezultat i pritur → rezultat i marrë për testet, përgjigjen e reflektimit dhe deklarimin e AI/burimeve. Për React dorëzo edhe package.json dhe lockfile; mos dorëzo node_modules/ ose dist/.
