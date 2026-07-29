# I BUFF YOU

Web app mobile-first per coordinare lo scambio di buff tra giocatori.  
Ogni giocatore si prenota come donatore o richiedente di buff (Scienza/Costruzione) su slot orari. Il sistema abbina automaticamente le coppie.

**URL live:** `https://{USERNAME}.github.io/i-buff-you/`

---

## Stack

- HTML + CSS + JavaScript (single file, no build step)
- [Supabase](https://supabase.com) — autenticazione + database PostgreSQL
- GitHub Pages — hosting gratuito

---

## Struttura temporale

- Timezone di gioco: **UTC-2** (fisso)
- 6 slot da 4 ore per giornata (Slot 0 = 00:00–04:00 UTC-2)
- Visibili: oggi, domani, dopodomani (in tempo UTC-2)
- Slot passati nascosti automaticamente

---

## Gestione utenti (solo Admin)

### Creare un nuovo utente

1. Vai su [Supabase Dashboard](https://supabase.com) → progetto `i-buff-you`
2. **Authentication → Users → Add user → Create new user**
3. Compila:
   - **Email:** `nickname@ibuffyou.game`  
     *(usa il nickname del giocatore come parte prima della @)*
   - **Password:** scegli una password temporanea
   - Spunta **"Auto Confirm User"** se presente
4. Il profilo viene creato automaticamente dal trigger
5. Comunica al giocatore: **nickname** (parte prima della @) + **password**

Esempio: email `mario@ibuffyou.game` → il giocatore accede con username `mario`

### Disattivare/riattivare un utente

Accedi all'app come admin → **Impostazioni ⚙ → GESTIONE UTENTI** → bottone Disattiva/Attiva

### Impostare un utente come Admin

Nel SQL Editor di Supabase:
```sql
UPDATE profiles SET role = 'admin'
WHERE display_name = 'NicknameUtente';
```

---

## Aggiornare l'app

1. Modifica `index.html` in locale
2. `git add index.html && git commit -m "descrizione modifica"`
3. `git push`
4. GitHub Pages si aggiorna automaticamente in ~30 secondi

---

## Storico versioni

| Data | Versione | Descrizione |
|------|----------|-------------|
| 2026-07-29 | v1.0 | Release iniziale — login, slot UTC-2, matching donatore/richiedente, 6 lingue, tema dark/light, pannello admin |
