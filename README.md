# Tracks All Finances — Deploy Guide

## File inclusi
- `index.html` — App completa (auth, PIN, biometria, home, storico, statistiche)
- `manifest.json` — Configurazione PWA
- `sw.js` — Service Worker (offline support)
- `icons/icon-192.png` — Icona app
- `icons/icon-512.png` — Icona app HD

---

## Deploy su Netlify (consigliato, gratuito)

1. Vai su **netlify.com** → "Add new site" → "Deploy manually"
2. Trascina l'intera cartella `tracksallfinances/` nella pagina
3. Netlify ti dà un URL tipo `https://tuo-nome.netlify.app`
4. Apri l'URL dal telefono → banner "Aggiungi a schermata Home" → installa!

## Deploy su Vercel

1. `npm i -g vercel`
2. Dalla cartella: `vercel --prod`
3. Segui le istruzioni

## Deploy su GitHub Pages

1. Crea repo GitHub, carica i file
2. Settings → Pages → Source: main branch / root
3. URL: `https://tuonome.github.io/tracksallfinances`

---

## Come funziona l'app

### Prima apertura
1. Schermata **Registrazione** → inserisci email + password
2. Creazione **PIN a 4 cifre** → confermalo
3. Entri nell'app

### Aperture successive
1. Il sistema prova la **biometria** (Face ID / Touch ID / impronta)
2. Se fallisce o non disponibile → inserisci il **PIN**

### Funzionalità
- **Home**: saldo C/C + Contanti, cerchio proporzionale, nuova transazione
- **Storico**: tutte le transazioni con filtri
- **Statistiche**: entrate/uscite del mese + grafico 6 mesi
- **Dati salvati** in localStorage (persistenti tra sessioni)
- **PWA**: installabile sul telefono, funziona offline

---

## Note sulla biometria
La biometria (WebAuthn) funziona solo su:
- HTTPS (non su http://)
- Browser moderni: Safari iOS 14+, Chrome Android 70+
- Dispositivi con sensore biometrico

Su localhost funziona solo su Chrome con flag `--allow-insecure-localhost`.
