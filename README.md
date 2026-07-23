# X-TREME MASTER v50.1 AI Ultimate + Terminski Plan

Statična web aplikacija za proračun i terminsko planiranje krovišta, statičku analizu i vizualizaciju (Three.js), s AI funkcijama preko Google Gemini API-ja.

## Struktura

```
.
├── index.html      # cijela aplikacija (HTML + CSS + JS u jednoj datoteci)
├── _headers        # Cloudflare Pages HTTP headeri
└── README.md
```

## Kako radi AI dio

Aplikacija koristi **Google Gemini API** direktno iz preglednika (client-side fetch). Korisnik unosi svoj Gemini API ključ u polje na vrhu stranice ("Unesi Gemini API Ključ..."). Ključ se sprema samo lokalno u `localStorage` preglednika (`xtreme_gemini_api_key`) — nikad ne ide na server niti u repo.

Ključ možeš dobiti besplatno na: https://aistudio.google.com/app/apikey

Koristi se za:
- Gemini 2.5 Flash — stručno mišljenje / upozorenja / email ponude
- Imagen 4.0 — generiranje slike krova
- Gemini 2.5 Flash TTS — glasovni odgovor ("Pitaj Horvata")

## Deploy na Cloudflare Pages

### Opcija A — preko GitHub (preporučeno)

1. Kreiraj novi repo na GitHubu i uploadaj sadržaj ovog zipa (ili `git push`).
2. Idi na [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**.
3. Odaberi repo.
4. Build postavke:
   - **Framework preset:** None
   - **Build command:** (ostavi prazno)
   - **Build output directory:** `/`
5. Klikni **Save and Deploy**.

Gotovo — Cloudflare će servirati `index.html` kao statičku stranicu na `*.pages.dev` domeni (i može se spojiti custom domena kasnije).

### Opcija B — direktan upload (bez GitHuba)

1. Cloudflare Dashboard → **Workers & Pages** → **Create application** → **Pages** → **Upload assets**.
2. Povuci ovaj folder (ili zip) i uploadaj.
3. Deploy.

### Opcija C — Wrangler CLI

```bash
npm install -g wrangler
wrangler pages deploy . --project-name=xtreme-master
```

## Napomena

Nema build koraka, nema npm ovisnosti — čista statička stranica, radi odmah nakon uploada.
