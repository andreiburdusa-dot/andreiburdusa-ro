# Deploy Flux Viv pe andreiburdusa.ro

## ✅ Status curent
- **index.html** — GATA cu Flux Viv integrat
- **4 coloane vii** — Eseuri, Investigații, Colaborări, Radio
- **Design** — Responsive, consistent cu site, dark mode support
- **Funcție** — Agregare de linkuri cu date + titluri + descrieri

---

## 🚀 Pași de deploy (5 minute)

### 1. Backup și pull repo
```bash
cd /path/to/andreiburdusa-ro
git pull origin principal
# sau dacă ai local changes:
git stash
git pull origin principal
```

### 2. Înlocuiește index.html
```bash
cp /path/to/download/index.html ./
```

### 3. Commit și push
```bash
git add index.html
git commit -m "Add Flux Viv — live content aggregator (4 coloane: eseuri, investigații, colaborări, radio)"
git push origin principal
```

### 4. Verificare Netlify
- Merge automat
- Site live în ~30 secunde
- Verifi pe: https://andreiburdusa.ro (trebuie să vezi 4 coloane sub HERO)

---

## 📝 Cum actualizezi conținutul

### Pentru NOI INTRĂRI:

1. **Deschide `index.html`** în editor favorit (VS Code, Sublime, etc.)
2. **Caută coloana corespunzătoare** (CTRL+F / CMD+F):
   - `<!-- COLOANĂ 1: ESEURI`
   - `<!-- COLOANĂ 2: INVESTIGAȚII`
   - `<!-- COLOANĂ 3: COLABORĂRI`
   - `<!-- COLOANĂ 4: RADIO`

3. **Copie templateul** din `FLUX-VIV-TEMPLATE.html`

4. **Adaug noul card** în coloana potrivită, ÎNAINTE de `</div>` care închide coloana

5. **Editează**:
   - `flux-date` → data (format: "21 AUG 2026")
   - `flux-card-title` → titlul
   - `flux-card-desc` → descrierea (1-2 linii, max 120 caractere)
   - `href` → URL articol/doem/playlist

6. **Push**:
   ```bash
   git add index.html
   git commit -m "Add to Flux Viv: [titlu intrării noi]"
   git push origin principal
   ```

---

## 🎯 Exemple de intrări (copy-paste ready)

### Eseu nou pe andreiburdusa.site
```html
<div class="flux-card">
  <div class="flux-date">21 AUG 2026</div>
  <h4 class="flux-card-title">Lentila și Relația</h4>
  <p class="flux-card-desc">De ce ființa noastră nu este doar proces. Trei straturi: acțiuni, imagini, relații.</p>
  <a href="https://andreiburdusa.site/articles/lentila-si-relatie.html" class="flux-card-link">Citește →</a>
</div>
```

### Investigație pe aequus.news
```html
<div class="flux-card">
  <div class="flux-date">20 AUG 2026</div>
  <h4 class="flux-card-title">Peisajul Politic Român la 31 August</h4>
  <p class="flux-card-desc">Instituții sub asediu. PSD pasează legi cu vulnerabilități constituționale.</p>
  <a href="https://aequus.news/articles/titlu.html" class="flux-card-link">Citește →</a>
</div>
```

### Doem pe mirelamares.art
```html
<div class="flux-card">
  <div class="flux-date">18 AUG 2026</div>
  <h4 class="flux-card-title">Și mâine ce-i — Suno AI Dire Straits</h4>
  <p class="flux-card-desc">Stil Mark Knopfler, voce baritone, guitară atmosferică, 4:24.</p>
  <a href="https://mirelamares.art" class="flux-card-link">Ascultă →</a>
</div>
```

### Playlist pe ADN FM
```html
<div class="flux-card">
  <div class="flux-date">21 AUG 2026</div>
  <h4 class="flux-card-title">Romanța Iubirilor Abia Pierdute — Reggae</h4>
  <p class="flux-card-desc">Playlist update. Reggae jamaican, versuri din seria elegiacă, orkestrație minimalistă.</p>
  <a href="https://adn-fm.ro" class="flux-card-link">Ascultă →</a>
</div>
```

---

## ⚙️ Reguli rapide de editare

| Element | Format | Exemplu |
|---------|--------|---------|
| **Data** | UPPERCASE | 21 AUG 2026 |
| **Titlu card** | Max 70 caractere | "Lentila și Relația" |
| **Descriere** | 1-2 linii, max 120 caractere | "De ce ființa noastră..." |
| **Link text** | Citește → / Ascultă → | Depends on category |
| **URL** | Complet, https:// | https://andreiburdusa.site/... |

---

## 🎨 Design & Styling

**Fără modificări CSS necesare** — totul e deja stilat. Dacă vrei să schimbi:

- Culori → caută `:root` în `<style>` din `<head>` (variabile `--gold`, `--cream`, etc.)
- Layout coloane → caută `.flux-grid` în style
- Spacing → caută `.flux-card` padding/margin

**NU edita CSS dacă nu ești sigur** — poti strica responsive design.

---

## 📊 Structura Flux Viv în HTML

```
<!-- FLUX VIV SECTION -->
<section id="flux-viv">
  <div class="section-inner">
    <!-- HEADER -->
    <div class="section-header">...</div>
    
    <!-- GRID 4 COLOANE -->
    <div class="flux-grid">
      
      <!-- COLOANĂ 1: ESEURI -->
      <div class="flux-column">
        <div class="flux-header">...</div>
        <div class="flux-card">...</div>
        <div class="flux-card">...</div>
      </div>
      
      <!-- COLOANĂ 2: INVESTIGAȚII -->
      <div class="flux-column">
        ...
      </div>
      
      <!-- COLOANĂ 3: COLABORĂRI -->
      <div class="flux-column">
        ...
      </div>
      
      <!-- COLOANĂ 4: RADIO -->
      <div class="flux-column">
        ...
      </div>
      
    </div>
  </div>
</section>
```

---

## 🔄 Workflow zilnic

### Când publici eseu pe andreiburdusa.site:
1. Pub pe site
2. Deschide `index.html`
3. Găsește coloana ESEURI
4. Adaug card cu link către articol
5. Push (git add → commit → push)

### Când publici pe aequus.news:
1. Pub pe site
2. Copy titlu + descriere scurtă
3. Deschide `index.html`
4. Găsește coloana INVESTIGAȚII
5. Adaug card
6. Push

### Pentru doeme + radio:
Same workflow, coloana COLABORĂRI sau RADIO.

---

## ⚠️ Troubleshooting

| Problemă | Soluție |
|----------|---------|
| Flux Viv nu apare după push | Așteaptă 30-60 sec (Netlify build time) |
| Linkul nu merge | Verifi URL complet (cu https://) |
| Card arată ciudat | Verifi că ai închis toate `<div>` și `</a>` tags |
| Stil stricat | Reload pagina (CMD+SHIFT+R / CTRL+SHIFT+R) |

---

## 📄 Fișiere din ZIP

- **index.html** — Versiunea finală, gata de upload
- **FLUX-VIV-TEMPLATE.html** — Template pentru copy-paste rapid
- **DEPLOY-ANDREIBURDUSA-RO.md** — Acest fișier (instrucțiuni)

---

## ✨ Next steps (opțional)

După ce Flux Viv e live, poți considera:
1. **Automation**: Script Python care citește din RSS feeds și genereaza carduri automat
2. **Sorting**: Sort cards by date (newest first) — CSS `order` property
3. **Search/Filter**: Butoane pentru filtrare pe categorie (JS simple)
4. **Mobile drawer**: Sidebar drawer pe mobile (CSS media query + JS toggle)

Pentru acum: **Flux Viv e manual dar simplu** — 2 minute pe intrare, nicio complexitate.

---

**Status**: ✅ Gata de publicare  
**Data**: 21 august 2026  
**Responsabil**: Copy-paste index.html + push pe GitHub
