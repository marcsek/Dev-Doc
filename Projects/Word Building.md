# Hlavná charakteristika

Pôvodne program naprogramovaný v jazyku python, táto verzia by mala mať formu **webstránky**. Bude spĺňať všetky funkcionality predošlého programu a zároveň ich bude aj dopĺňať. 

#### Pod novými funkciami si predstavujem:
- **[[#Vlastný účet]]**
- **[[#Ukladanie súborov na cloud]]**
- **[[#Funkcionalita detí a rodičov]]**
- **[[#Štatistika aktivity používateľa]]**


***
## Vlastný účet

Každý používateľ si bude ***musieť*** pred používaním ostatných funkcionalít stránky vytvoriť účet. Na výber bude mať z viacerých možnosti ako sú: **Lokálna autentifikácia (meno, heslo)**, **Google autentifikácia**, **GitHub autentifikácia** a **Twitter autentifikácia**.

#### Dáta ktoré budú od používateľa vyžadované sú:
- Meno `predovšetkým na prehladnosť medzi ostatnými používateľmi`
- Email `unikátny identifikátor používateľa, zasielanie emailov`
- Heslo `overenie identity používateľa`

K dispozícii bude mať používateľ aj **"Nastavenia účtu"**, kde si bude môcť zmeniť základné nastavenia svojho účtu.

***
## Ukladanie súborov na cloud

Používateľ bude po novom ukladať svoje databázové súbory `(primárne .xlsx)` v cloudovom úložisku webstránky. Z jeho súboru si potom server sám vyextrahuje jednotlivé dátové páry a uloží ich vo svojom vlastnom dátovom formáte. 

To pre používateľa znamená hlavne, že sa mu samotný  databázový súbor nebude na cloud ukladať, takže si ich ***nebude môcť spätne stiahnuť z cloud úložiska***.

><span style="color:#C69026">**⚠️ Upozornenie**</span>
>Predtým sa museli súbory ukladať do konkrétnej zložky v mieste úložiska programu, tento spôsob už viac nebude podporovaný.

***
## Funkcionalita detí a rodičov

Budú existovať dva typy účtov **"Rodič"** a **"Dieťa"**, každý rodičovský účet si bude môcť pridávať pod seba detské účty. To mu umožní mať kontrolu nad niektorými funkcionalitami jednotlivých detských účtov. 

#### Oprávnenia rodiča na detskom účte:
- Možnosť pridávať/vytvárať nové zdroje dátových párov pre deti.
- Kontrola nad aktivitou na detských účtoch.
- V [[#Štatistika aktivity používateľa |štatistike používateľa]] si bude môcť okrem svojich štatistík pozrieť aj tie, jeho detí.

Dieťa však bude stále môcť mať svoje vlastné zdroje dát ku ktorým nebudem mať rodič prístup.

***
## Štatistika aktivity používateľa

Používateľ bude mať prehľad o jeho predošlej aktivite. Pomocou viacerých grafov `(napr. heatmap, column alebo radar)` pri ktorých bude môcť filtrovať nad rôznymi obdobiami a parametrami ako napr. typ alebo jazyk materiálu slovnej zásoby. 

Každý [[#Funkcionalita detí a rodičov |rodičovský účet]] bude mať okrem svojich vlastných štatistík, štatistiku aj všetkých k nemu prislúchajúcich detských účtov.

</br>

---
# Technické špecifikácie

Celá štruktúra programu bude používať ako hlavný jazyk [javascript](https://www.javascript.com/), výhradne používaný s [typescriptom](https://www.typescriptlang.org/).  Bude rozdelený na [[#Frontend|frontendovú]] a [[#Backend|backendovú]] aplikáciu. Frontend bude používať [React.js](https://reactjs.org/) postavený pomocou [Vite.js](https://vitejs.dev/). Backend bude používať ako hlavný framework [Express.js](https://expressjs.com/) spolu s nástrojom [tRPC 10.x](https://trpc.io/) na ľahké integrovanie API na frontende.

Spolu budú tvoriť jednu **"monorepo"**, pomocou ktorej budú môcť zdieľať prostriedky `napr. configy pre ESLint, Typescript alebo Prettier`. Ďalej to uľahčí aj proces vývoju a deploymentu. Ako nástroj na tvorbu monorepo bude použitá [turborepo](https://turbo.build/repo).


---
## Frontend 

Základom frontednu je [React.js](https://reactjs.org/), [typescript](https://www.typescriptlang.org/), [Vite.js](https://vitejs.dev/), [TanStack Query](https://tanstack.com/query/v4), [tailwindcss](https://tailwindcss.com/). Bude obsahovať vlastnú malú komponentovú knižnicu ktorej základom bude [Headless UI](https://headlessui.com/) a [React Aria](https://react-spectrum.adobe.com/react-aria/). 

---
## Backend 

Základom backendu je [Express.js](https://expressjs.com/) a [tRPC 10.x](https://trpc.io/). Na OAuth 2.0 autentifikáciu sa používa [Passport.js](https://www.passportjs.org/).  Schémy ktoré budú zdieľané medzi backendom a frontendom budú tvorené pomocou knižnice [zod](https://zod.dev/). Na autentifikáciu sa bude používať jednoduchý access token [JWT](https://jwt.io/), ktorý sa bude na klientovi ukladať do `HttpOnly` cookie.

#### Databáza
Bude tvorená SQL databázou [PostgreSQL](https://www.postgresql.org/), na [[#Backend|backende]] bude generovaná a pristupovaná pomocou ORM [Prisma](https://www.prisma.io/) .

*Takúto podobu bude mať "Prisma schema":*

![[DatabaseBluePrint.png]]

***
## Zoznam funkcii a ich stav dokončenia

| Sekcia | Funkcia | Dokončenosť |
| :----    | :-------  | :------: |
| Frontend + Backend | [[#Vlastný účet]] |❌|
| Frontend + Backend | [[#Ukladanie súborov na cloud]] |❌|
| Frontend + Backend | [[#Funkcionalita detí a rodičov]] |❌|
| Frontend + Backend | [[#Štatistika aktivity používateľa]] |✅|