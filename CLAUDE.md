# Portfolio Wachoo — CLAUDE.md

## Fichier principal
`index.html` — single-page HTML/CSS/JS inline, ~760 lignes.

## Identité
- **Qui :** Adam "Wachoo", étudiant ingénieur EPITA ING1, ancien MPSI/MP, spécialisation visée SC-IA
- **Double cursus :** Licence Maths Paris-Saclay en parallèle
- **Objectif actuel :** Stage IA / Data — Été 2026
- **Esthétique :** "Néoclassicisme Digital" — dark mode uniquement, peintures classiques en fond, citations stoïciennes, symboles math flottants

## Stack du portfolio
- HTML/CSS/JS vanilla (pas de framework)
- Bilingue FR/EN via `<span class="fr">` / `<span class="en" style="display:none">` + toggle JS
- IntersectionObserver pour scroll reveal (`.rv` → `.vis`)
- Animations CSS `@keyframes fu` (fade-up), `clip-reveal`, `kenburns`, `drift`, `pulse`

## Typographie (5 registres)
- **Cinzel** → monumental (hero h1, topbar-name, proj-num, ody-year, metric-num, hero-badge-title, stele-top)
- **Playfair Display** → éditorial (s h2, proj-title, ody-title, contact h2)
- **Cormorant Garamond** → poétique (hero-quote, proj-quote, painting blockquote, pass-icon, pass-sub, stele-body)
- **Inter** → body text (descriptions, features, labels, tout le reste)
- **JetBrains Mono** → code/tech (stack-chip, feat-tech)

## Palette CSS (variables)
```
--bg: #1a1714       --text: #e8e2d8     --terra: #c4845c
--bg-2: #23201b     --text-2: #bfb6a8   --olive: #8a9e68
--bg-card: #262220  --text-3: #8a7e6d   --rust: #c4785c
--border: #3d3830   --text-4: #5c5347   --clay: #b8956e
--border-lt: #33302a
```

## Structure des sections (ordre dans le HTML)
1. **Topbar** — fixe, logo "Wachoo" cliquable, nav: Projets/Parcours/Passions/Compétences/Contact + toggle FR/EN
2. **Scroll progress bar** — ligne terra 3px fixe, z-index 101
3. **Hero** (s-art-wrap: school-of-athens, opacity 0.30) — citation Sénèque, h1 clip-reveal, tagline + hero-sub, badge, liens
4. Meander
5. **Section I — Projets** (s-art-wrap: creation-of-adam, opacity 0.14, `.s.s-wide`, id="projets")
   - 3 projets majeurs en grille 2 colonnes (`1fr 1fr`, gap 4rem)
   - 3 projets mineurs en grille 3 colonnes (`.proj-minor-grid`)
   - Metrics bar (4 cartes avec compteurs animés)
6. Meander
7. **Section II — L'Odyssée** (s-art-wrap: wanderer, opacity 0.14, id="parcours") — 6 étapes timeline
8. Meander
9. **Section III — Au-delà du code + Compétences** (s-art-wrap: consummation-of-empire, opacity 0.35)
   - Passions (id="passions") — grille 8 cellules avec hover enrichi
   - Stèles de compétences (id="competences") — 3 colonnes marbre avec stagger reveal
10. Meander
11. **Section IV — Contact** (s-art-wrap: death-of-socrates, opacity 0.38, id="contact") — liens principaux + projets
12. Meander + Footer

## Les 6 projets
| # | Nom | Tag | Status | Layout | Liens |
|---|-----|-----|--------|--------|-------|
| I | Hygée — App santé chronique féminine | Santé | En production | Majeur | App live, GitHub front+back |
| II | Bot Trading Gold (XAU/USD) | Finance | Paper trading | Majeur | Dashboard live, repo privé |
| III | Vies2s — Association jeunes | Asso | Actif sept. 2025 | Majeur | Plateforme live |
| IV | Stage UPHF — Arithmétique modulaire | Recherche | Terminé 2024 | Compact | — |
| V | Agent IA — Gardien productivité | Auto | En service | Compact | — |
| VI | Fine-tuning Qwen 2.5 2B | IA | En cours | Compact | — |

## Images (`img/`)
| Fichier | Usage | Taille |
|---------|-------|--------|
| school-of-athens.jpg | Fond hero (opacity 0.30) | 984K |
| creation-of-adam.jpg | Fond section projets (opacity 0.14) | 447K |
| wanderer.jpg | Fond section parcours (opacity 0.14) | 227K |
| consummation-of-empire.jpg | Fond passions + compétences (opacity 0.35) | 648K |
| death-of-socrates.jpg | Fond section contact (opacity 0.38) | 392K |
| marble-texture.jpg | Texture marbre des stèles compétences | 136K |
| vitruvian-man.jpg | Ancien fond passions (non utilisé) | 438K |
| colosseum.jpg | Ancien fond contact (non utilisé) | 653K |
| hygee-screenshot.png | Non intégré (liens live suffisent) | 61K |
| trading-screenshot.png | Non intégré (liens live suffisent) | 35K |
| vies2s-screenshot.png | Non intégré (liens live suffisent) | 39K |

## Liens réels
- GitHub : https://github.com/Wachoox
- LinkedIn : https://www.linkedin.com/in/adam-wachoo-45338b378
- App Hygée : https://endometriosis-frontend-henna.vercel.app
- Frontend repo : https://github.com/Wachoox/endometriosis-frontend
- Backend repo : https://github.com/Wachoox/endometriosis-backend
- Dashboard Trading : https://smcbot.duckdns.org/dashboard.html
- Plateforme Vies2s : https://vies2s-app.vercel.app/
- Email : adamwachoo19@gmail.com

## Animations en place
### Tier 1 — Essentielles
- **Scroll progress bar** — ligne terra 3px, z-index 101, JS scroll listener
- **Active nav highlight** — `.tb-nav.active` en terra, `getBoundingClientRect`
- **Ken Burns** — `.s-art img` zoom 20s alternate, kenburns/kenburns2 (pair/impair)
- **Stagger features** — `.proj .feat li` et `.stack-chip` cascade au scroll reveal via `fu`
- **Math symbols drift** — CSS custom properties `--dx`, `--dy`, `--rot`, `--drift-duration`

### Tier 2 — Impressionnantes
- **Parallax peintures** — JS `requestAnimationFrame` sur `.s-art`, facteur 0.08
- **Compteurs animés** — `data-target` sur metric-num, ease-out cubic 1.5s (24/7 = texte statique)
- **3D tilt projets** — perspective 1000px, ±3deg au mousemove sur `.proj`
- **Boutons magnétiques** — `.hero-link`, `.cl`, `.proj-link`, `.tb-nav` facteur 0.2

### Tier 3 — Signature
- **Clip-path reveal** — hero h1 "WACHOO" se dévoile gauche→droite, cubic-bezier
- **Hover passions** — symbole scale(1.2) + terra, cellule translateY(-3px)
- **Stèles stagger** — 3 stèles apparaissent en cascade (0s, 0.15s, 0.3s) au scroll reveal
- **Stèles hover** — bordure dorée renforcée + box-shadow + translateY(-2px) au survol
- **Konami Code** — ↑↑↓↓←→←→BA : peintures 60% opacity 5s + halo terra

## Composants CSS notables
- `.hero-badge` — 2 lignes : `.hero-badge-title` (Cinzel 1.3rem terra) + `.hero-badge-sub` (0.7rem text-2)
- `.hero-tag` — tagline courte 1.05rem + `.hero-sub` (parcours 0.72rem text-2)
- `.proj-tag-row` — flex wrapper pour tag + statut, alignés à 22px de hauteur
- `.proj-oneliner` — encadré avec label flottant "Concrètement" / "In practice"
- `.feat-tech` — détail technique au hover des features (color clay, max-height transition)
- `.proj-minor-grid` — grille 3 colonnes pour projets secondaires
- `.metrics-bar` — 4 metric cards dans la section projets (dans le s-art-wrap)
- `.steles-wrap` — 3 stèles de marbre (Langages, Frameworks, IA & Data) sous consummation-of-empire, padding resserré
- `.stele` — texture marbre + overlay rgba(20,18,14,0.72), fronton Cinzel, corps Cormorant Garamond
- `.s-art` — `top:-10%; height:120%` pour absorber le parallax sans bandes sombres
- `.scroll-progress` — barre terra fixe en haut
- text-shadow sur hero-quote, hero-sub, hero-badge-title, hero-badge-sub pour lisibilité

## Contraintes à respecter
- **Bilingual FR/EN** obligatoire pour tout texte visible
- **Dark mode uniquement** — pas de thème clair
- **Pas de stats de trading** (PF, WR, R:R) — jamais
- **Pas de screenshots** dans les cartes projets — les liens live suffisent
- **prefers-reduced-motion** supporté (désactive toutes les animations + masque scroll-progress)
- Les fonts sont chargées via `<link>` preconnect (pas `@import`)
- `scroll-margin-top: 4rem` sur les `section[id]` pour offset topbar fixe
- Scroll forcé en haut au chargement (ignore le hash dans l'URL)

## Historique des sessions
### Session 1 (17-18 mars 2026)
- Création initiale, descriptions projets, skills bar, hero, meta tags, liens, badges
- Refonte consolidée : s-wide 1100px, one-liner, 3 majeurs + 3 compacts, metrics bar
- Phase 1 restructuration : Cinzel, images compressées (7.8MB→2.7MB), prefers-reduced-motion

### Session 2 (18 mars 2026)
- Phase 3 Tier 1-3 : scroll progress, active nav, Ken Burns, stagger, math drift, parallax, compteurs, 3D tilt, boutons magnétiques, clip-path reveal, hover passions, Konami Code
- Hero refait : tagline courte + hero-sub + badge 2 lignes (Cinzel 1.3rem) + text-shadow
- Peintures : vitruvian-man → consummation-of-empire, colosseum → death-of-socrates
- Fichier renommé : wachoo-portfolio-v4.html → index.html

### Session 3 (19 mars 2026)
- Passions + Compétences fusionnées sous le même s-art-wrap (consummation-of-empire)
- Skills bar remplacée par 3 stèles de marbre (texture marble-texture.jpg + overlay sombre)
- Stèles : fronton Cinzel, corps Cormorant Garamond, stagger reveal + hover lueur
- Lien "Compétences" ajouté dans la topbar nav (id="competences")
- Padding resserré entre passions et stèles (section passions padding-bottom:2rem, steles-wrap padding-bottom:2.5rem)

## TODO (prochaines sessions)
- [ ] Envisager : "Choose your path" (recruteur vs dev), project modals, données live
