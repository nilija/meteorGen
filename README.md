ava efikasno kreiranje Grid aplikacija na osnovu definisanih kolekcija.

---

## Koraci za Korišćenje

### 1. Kopiranje Radnog Foldera
Kopirajte sadržaj u radni folder. Nakon kopiranja, kreirajte opise kolekcija.

---

### 2. Kreiranje Opisa Kolekcija
Opis fajla za kreiranje kolekcije se nalazi u šablonu **`colfile.txt`**. Postoje dva načina za izmenu:

1. **Direktno uređivanje** fajla.
2. **Kreiranje novog fajla** pomoću skripti:
   - **`gen_txt`**
   - **`gen_txt_file`**

#### Unos Podataka:
- **Ime polja**: Unesite naziv polja.
- **Tip polja**: Dozvoljeni tipovi su:
  - `txt`
  - `mail`
  - `number`
  - `password`
  - `date`
  - `checkbox`
  - `radio`

---

### 3. Generisanje Projekta
1. Nakon formiranja `.txt` fajlova sa opisima kolekcija, pozovite skriptu **`mtemplateCopy`**:
   ```bash
   mtemplateCopy <ime-direktorijuma>
Skripta **`mtemplateCopy`** kopira:
- `.meteor`
- `node_module`
- Strukturu projekta i fajlove za generisanje.

---

### Korišćenje Skripte `mtemplateCopy`

Pokrenite skriptu sa sledećim argumentom:
```bash
mtemplateCopy <direktorijum na /home/x/meteor_gen/gen/ ispod kojeg će biti sajt>
```
#### Primer:

mtemplateCopy MyApp

- Napraviće sajt na:
  - **URL**: `http://localhost:3000`
  - **Lokacija**: `/home/x/meteor_gen/gen/MyApp`

---

### Dalji Koraci

1. **Pozivanje `mGenFirst`**:
   - Kreira osnovni kostur i stablo projekta.

2. **Pozivanje `mGen_c`**:
   - Generator čita fajl **`imekolekcije.txt`** (fajl imenovati prema kolekciji koja se generiše).
   - Analizira pojedinačne redove sa imenima polja.
   - Generiše odgovarajuće redove u odgovarajućim JavaScript fajlovima.

---

### Prethodni Zahtevi

Pre pokretanja, instalirajte paket **`line-reader`**:
```bash
npm install line-reader

### TO-DO
- Napraviti **Meteor** aplikaciju za kreiranje opisa kolekcije.

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
