# Java V — Formulari i misionit sekret

## Çfarë mëson

Formularë semantikë, validim HTML dhe tabela të dhënash.

Referencë tematike: kap. 5 të librit.

## Skenari

Një klub organizon një mision në kampus dhe kërkon regjistrime të sakta, pa dërguar të dhëna reale.

## Kërkesat për studentin

1. Ndërto formular me pseudonim 3–20 karaktere, email, grup 1–5 persona, kategori dhe pranim të rregullave.
2. Çdo kontroll ka label; radio-t kanë fieldset/legend. Përdor required, type, min/max dhe minlength/maxlength.
3. Krijo tabelë me tri orare; përdor caption, th dhe scope.
4. Butoni submit demonstron validimin vendas. Me të dhëna valide kalon te pranuar.html përmes GET; shpjego se kjo nuk ruan regjistrim në server.
5. Përdor vetëm të dhëna të sajuara; shëno se vlerat GET shfaqen në URL.

## Rastet e pranimit

- [x] Formulari bosh nuk kalon.
- [x] Email pa format email-i dhe grup 0 ose 6 nuk kalojnë.
- [x] Të dhënat valide çojnë te faqja e demonstrimit; tabela ka tituj kolonash.

## Çfarë realizova

Një faqe statike për regjistrim demonstrues të misionit:

- formular me `required`, `type="email"`, `minlength`/`maxlength` 3–20, `min`/`max` 1–5;
- çdo fushë ka `label`; kategoritë janë radio brenda `fieldset`/`legend`;
- tabelë me `caption`, `th` dhe `scope` për tre orare të sajuara;
- `method="get"` dhe `action="pranuar.html"`: validimi vendas bllokon të dhënat e gabuara; të dhënat valide shkojnë te faqja e demonstrimit, ku vlerat shfaqen nga URL.

Skedarët: `Fillimi/index.html`, `Fillimi/style.css`, `Fillimi/pranuar.html`, `README.md`. Nuk ka backend.

## Hapat e hapjes

1. Hap dosjen `Java5/Fillimi`.
2. Hap `index.html` në shfletues (dopio-klik, ose Live Server në VS Code/Cursor).
3. Provo dërgimin bosh, pastaj email pa `@` dhe grup `0` ose `6`.
4. Plotëso të dhëna valide (p.sh. `Aria`, `student@example.org`, `3`, Art, pranim) dhe dërgo. Shiko URL-në në `pranuar.html`.

Nuk kërkohet instalim pakete. Nëse do server lokal: `python -m http.server 8765` nga `Fillimi`, pastaj `http://127.0.0.1:8765/`.

## Testet

| Hyrje | Rezultat i pritur | Rezultat i marrë |
|---|---|---|
| Submit bosh | Formulari nuk kalon; shfletuesi tregon fushat e detyrueshme | `required` e ndalon dërgimin; mbetet në `index.html` |
| Email `jo-email` | Nuk kalon; kërkohet format email-i | `type="email"` e ndalon dërgimin |
| Persona `0` ose `6` | Nuk kalon; pranohen vetëm 1–5 | `min="1"` / `max="5"` e ndalon dërgimin |
| Pseudonim `ab` (2 karaktere) | Nuk kalon | `minlength="3"` e ndalon dërgimin |
| Të dhëna valide + GET | Shkon te `pranuar.html`; vlerat janë në URL | URL p.sh. `pranuar.html?pseudonimi=Aria&email=student%40example.org&persona=3&kategoria=art&rregullat=po` |
| Tabela | Tri orare me tituj kolonash | `caption` «Oraret e misioneve»; `th scope="col"` Ora / Misioni / Vendi |

## Reflektim individual

Pse required në frontend nuk provon që të dhënat në një sistem real janë të sigurta?

`required` (dhe `type`, `min`/`max`) punon vetëm në shfletues: ndihmon përdoruesin të mos dërgojë fusha bosh. Një kërkesë mund të ndryshohet ose të dërgohet jashtë formularit (p.sh. drejtpërdrejt te URL, ose me një klient tjetër). Prandaj një sistem real duhet t’i kontrollojë të dhënat edhe në server, të mos i besojë GET-it në URL dhe të mos ruajë të dhëna pa autorizim.

## Deklarim i AI dhe burimeve

- **AI:** Cursor ndihmoi për strukturën e `index.html`/`style.css`/`pranuar.html` dhe për këtë README. Unë e lexova kërkesën dhe e kontrollova validimin në shfletues.
- **Burime:** fletë e ushtrimit Java V; kap. 5 (formularë, validim HTML, tabela); stili vizual i javëve të mëparshme (system-ui, theks i gjelbër, skip-link).
- **Nuk u përdorën:** backend, baza të dhënash, biblioteka CSS/JS, `node_modules`. Të dhënat janë të sajuara.

## Dorëzimi dhe GitHub

Puno në JavaV/ të repository-t individual.
