# Pikënisja — Java V

Lexo ../README.md. Skedarët e zgjidhjes janë në këtë folder: `index.html`, `style.css`, `pranuar.html`.

## Hyrjet

- Pseudonim (3–20 karaktere)
- Email i sajuar
- Numër personash (1–5)
- Kategori: Art ose Shkencë
- Pranim i rregullave të demonstrimit

## Daljet

- Në të dhëna të gabuara: mesazh validimi i shfletuesit; nuk ndryshon faqja
- Në të dhëna valide: kalim te `pranuar.html` me GET; vlerat shfaqen në URL
- Tabela statike me tre orare misioni

## Rast normal

Pseudonim `Aria`, email `student@example.org`, 3 persona, Art, rregullat e pranuara → `pranuar.html` me parametrat në URL.

## Rast kufitar 1

Formulari bosh, ose email pa `@`, ose grup `0`/`6`, ose pseudonim me 2 karaktere → dërgimi bllokohet.

## Rast kufitar 2

Pseudonim 3 ose 20 karaktere dhe grup 1 ose 5: vlerat në kufi pranohen dhe kalojnë te faqja e demonstrimit.
