# Kompleksan Proces Generisanja Aplikacije

Ovaj dokument sadrži uputstva za korišćenje četiri skripte: **`gen_txt`**, **`mtemplateCopy`**, **`mGenFirst`**, i **`mGen_c`**. Skripte omogućavaju automatizaciju generisanja aplikacijske strukture u okviru projekta na osnovu unetih kolekcija i polja.

---

## Pregled Skripti i Procesa

1. **`gen_txt`**: Kreira `.txt` fajlove sa podacima o kolekcijama i njihovim poljima.
2. **`mtemplateCopy`**: Inicijalizuje projektne šablone i poziva naredne skripte za generisanje koda.
3. **`mGenFirst`**: Generiše osnovne fajlove za kolekcije, rutere i publikacije.
4. **`mGen_c`**: Generiše kompletne šablone, uključujući UI i internacionalizaciju (`i18n`).

---

## Detaljno Uputstvo

### 1. **`gen_txt`** - Definisanje Kolekcija i Polja

Ova skripta generiše `.txt` fajlove koji definišu kolekcije i njihova polja.

#### Koraci:
1. Pokrenite skriptu:
   ```bash
   node gen_txt.js
