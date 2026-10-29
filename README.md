# MULTIVERS — Pràctica React 6

Aplicació en React que consulta una **API pública real** per mostrar personatges de Rick and Morty. Sense cookies, sense backend propi i sense dades inventades.

## Com executar el projecte

1. Obre aquesta carpeta amb Visual Studio Code.
2. Obre un terminal a dins i executa:

   ```bash
   npm install
   npm run dev
   ```
3. Obre al navegador l'adreça que et mostra Vite (normalment `http://localhost:5173`).

> Cal tenir Node.js instal·lat i connexió a Internet. Si l'API no està disponible, l'aplicació mostrarà un error.

## L'API

- Web: https://rickandmortyapi.com/
- Endpoint utilitzat: `https://rickandmortyapi.com/api/character/`
- Documentació: https://rickandmortyapi.com/documentation
- No requereix clau ni registre.
- Retorna un objecte amb `info` (pàgines i comptador) i `results` (array de personatges).
- Accepta `page`, `name`, `status`, `species` com a paràmetres per cercar a **tota l'API**.
- Cada pàgina retorna fins a 20 personatges.

## Coneixements de classe aplicats

- `useState`: guardar personatges, favorits, filtres, càrrega i errors.
- **NOU** `useEffect`: carregar dades quan es munta l'aplicació i cada vegada que canvien els filtres o la pàgina.
- **NOU** `fetch()`, `async/await`, `try/catch/finally`, `response.ok`, `response.json()`.
- `map()`: mostrar llistes de targetes.
- `filter()`: afegir o eliminar favorits sense duplicats.
- `props`: passar dades i funcions als components.
- `onChange`, `onSubmit`, `onClick`: cercador, filtres, botons i favorits.
- JSX condicional: càrrega, error, cap resultat, llistat, etc.

## Components

```text
src/
├── App.jsx                   # Estats, useEffect, fetch i funcionalitat
├── App.css                   # Estils
├── index.css                 # Estils globals
├── main.jsx
└── components/
    ├── Capcalera.jsx         # Títol i comptadors
    ├── Filtres.jsx           # Cercador i 2 selectors
    ├── LlistatPersonatges.jsx# map(), component reutilitzat per favorits
    ├── TargetaPersonatge.jsx # Cada targeta i botó favorit
    ├── Paginacio.jsx         # Següent / anterior
    └── PeuPagina.jsx
```

## Funcionament dels filtres

El nom s'aplica en prémer **Cerca** o Enter. L'estat i l'espècie s'apliquen immediatament. Les cerques es fan a l'API (no només als 20 elements de la pàgina visible). Quan canvies de filtre es torna a la pàgina 1.

Els favorits es guarden amb `useState`. **Es perdran en refrescar la pàgina** perquè la pràctica no fa servir cookies, `localStorage` ni cap base de dades.

## Detalls tècnics

- L'API retorna `404` si la cerca no té resultats: ho tractem com una llista buida.
- La resta d'errors de xarxa apareixen en pantalla.
- El disseny s'adapta a ordinador, tauleta i mòbil.
- Els noms, les imatges i les dades provenen de la Rick and Morty API; pertanyen als seus titulars.
