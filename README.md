# meteorGen   ----------------------------> za Unix/UBUNTU
Meteor, generator Grid aplikacija

Kopira se u radni folder.
po kopiranju kreirajte opise kolekcija.

Opis fajla za kreiranje kolekcije je u template colfile.txt,
moze se direktno intervenisati u fajlu ili kreirati novi, sa drugim imenom
pozivanjem scripta  gen_txt ili gen_txt_file
Unesite ime polja:
Unesite tip polja (txt, mail, number, password, date, checkbox, radio):

Po formiranju txt fajlova sa opisom kolekcija - poziva se script mtemplateCopy,
koji kopira .meteor, node_module i strukturu - projekat i fajlove putem kojih se vrsi generisanje

Korišćenje - mtemplateCopy <direktorijum na /home/x/meteor_gen/gen/ ispod kojeg će biti sajt>
   Primer:   mtemplateCopy MyApp - napraviće sajt http://localhost:3000 na /home/x/meteor_gen/gen/MyApp

Zatim se poziva mGenFirst, kreira kostur, stablo projekta.

Zatim mGen_c, generator čita imekolekcije.txt (imenovati fajl kao kolekciju koja se generiše),
čita pojedinačne redove sa imenima polja i generiše redove u odgovarajućim fajlovima JS.

Prethodno je potrebno instalirati paket line-reader: npm install line-reader

TO-DO
meteor app za kreiranje opisa kolekcije

------------------------------------------------------------------

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
#### 1. Pokrenite skriptu:
   ```bash
   node gen_txt.js
   ```
### 2. Unesite osnovne informacije o kolekciji:
- **Naziv kolekcije** (jedna reč, npr. `users`).
- **Naslov aplikacije** i naslove modalnih prozora (npr. za dodavanje, pregled, uređivanje, brisanje).
- **Poruke uspeha** za različite operacije (dodavanje, uređivanje, brisanje).
- **Dodajte polja** sa njihovim imenima i tipovima:
  - Dozvoljeni tipovi: `txt`, `mail`, `number`, `password`, `date`.

### Na kraju unosa, skripta kreira `.txt` fajl.
Primer `.txt` fajla:

```plaintext
collection=users
title=User Management
modalTitleAdd=Add User
modalTitleView=View User
modalTitleEdit=Edit User
modalTitleDelete=Delete User
growlSuccessAdd=User successfully added!
growlSuccessEdit=User successfully updated!
growlSuccessDelete=User successfully deleted!
---
username,txt
email,mail
password,password
age,number
```
### 2. **`mtemplateCopy`** - Definisanje Projektnog Šablona

Skripta `mtemplateCopy` koristi `.txt` fajlove kreirane pomoću `gen_txt` za generisanje osnovne projektne strukture. Skripta automatski poziva `mGenFirst` i `mGen_c`.

### Koraci:

1. Pokrenite skriptu:
   ```bash
   node mtemplateCopy.js

Skripta automatski prepoznaje `.txt` fajlove i započinje generisanje:
- Poziva **`mGenFirst`** za osnovne fajlove.
- Poziva **`mGen_c`** za dodatne šablone i kod.

---

### Rezultat:
- Svi potrebni fajlovi i šabloni za definisane kolekcije su generisani.

### 3. **`mGenFirst`** - Generisanje Osnovnih Fajlova

Skripta **`mGenFirst`** kreira osnovne fajlove za kolekcije, rutere i publikacije.

#### Koraci:
1. Pokrenite skriptu:
   ```bash
   node mGenFirst.js
Skripta generiše sledeće fajlove:
- `collections/{collection}.js`
- `client/routers/{collection}.js`
- `server/publications/{collection}.js`
### 4. **`mGen_c`** - Kompletno Generisanje Strukture

Ova skripta proširuje funkcionalnost generisanjem šablona za korisnički interfejs i internacionalizaciju.

#### Koraci:
1. Pokrenite skriptu:
   ```bash
   node mGen_c.js
Skripta generiše:
- **HTML šablone za UI**: `client/views/{collection}.html`
- **JS logiku**: `client/views/{collection}.js`
- **Internacionalizaciju**: `client/lib/i18n_{collection}.js`

---

### **Celokupan Scenario**

#### Definisanje Kolekcija i Polja:
1. Pokrenite **`gen_txt`**:
   ```bash
   node gen_txt.js
1. **Unesite podatke i kreirajte `.txt` fajlove.**

---

### Generisanje Projektnog Šablona:
1. Pokrenite **`mtemplateCopy`**:
   ```bash
   node mtemplateCopy.js

Skripta automatski poziva:
- **`mGenFirst`**
- **`mGen_c`**

---

### Ručno Pokretanje Skripti (po potrebi):
1. **Generisanje osnovnih fajlova**:
   ```bash
   node mGenFirst.js

### Generisanje kompletne strukture:
Pokrenite skriptu:
```bash
node mGen_c.js
```
### Prethodni Zahtevi i Instalacija

1. Potrebna je **Node.js** verzija 14 ili novija.
2. Instalirajte potrebne pakete:
   ```bash
   npm install prompt
### Struktura Projekta

Po završetku, projekat će sadržavati sledeće ključne direktorijume i fajlove:

```bash
collections/
client/routers/
client/views/
server/publications/
client/lib/
```
### Napomene
- Proverite da su svi `.txt` fajlovi validni pre pokretanja skripti.
- Za pitanja i podršku, možete se obratiti dokumentaciji projekta.
