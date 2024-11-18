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
