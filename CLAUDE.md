# Portfolio Wachoo — CLAUDE.md

## Fichier principal
`wachoo-portfolio-v4.html` — single-page HTML/CSS/JS inline, ~750 lignes.

## Identité
- **Qui :** Adam "Wachoo", étudiant ingénieur EPITA ING1, ancien MPSI/MP, spécialisation visée SC-IA
- **Double cursus :** Licence Maths Paris-Saclay en parallèle
- **Objectif actuel :** Stage IA / Data — Été 2026
- **Esthétique :** "Néoclassicisme Digital" — dark mode uniquement, peintures Renaissance en fond, citations stoïciennes, symboles math flottants

## Stack du portfolio
- HTML/CSS/JS vanilla (pas de framework)
- Bilingue FR/EN via `<span class="fr">` / `<span class="en" style="display:none">` + toggle JS
- IntersectionObserver pour scroll reveal (`.rv` → `.vis`)
- Animations CSS `@keyframes fu` (fade-up), `clip-reveal`, `kenburns`, `drift`, `pulse`

## Typographie (5 registres)
- **Cinzel** → monumental (hero h1, topbar-name, proj-num, ody-year, metric-num)
- **Playfair Display** → éditorial (s h2, proj-title, ody-title, contact h2)
- **Cormorant Garamond** → poétique (hero-quote, proj-quote, painting blockquote, pass-icon, pass-sub)
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
1. **Topbar** — fixe, logo "Wachoo" cliquable (retour haut), nav links + toggle FR/EN
2. **Scroll progress bar** — ligne terra 3px fixe, z-index 101
3. **Hero** (s-art-wrap: school-of-athens) — citation Sénèque, h1 clip-reveal, tagline, badge, liens
4. Meander
5. **Section I — Projets** (s-art-wrap: creation-of-adam, `.s.s-wide`, id="projets")
   - 3 projets majeurs en grille 2 colonnes (`1fr 1fr`, gap 4rem)
   - 3 projets mineurs en grille 3 colonnes (`.proj-minor-grid`)
   - Metrics bar (4 cartes avec compteurs animés)
6. Meander
7. **Section II — L'Odyssée** (s-art-wrap: wanderer, id="parcours") — 6 étapes timeline
8. Meander
9. **Section III — Au-delà du code** (s-art-wrap: vitruvian-man, id="passions") — grille 8 cellules
10. Meander
11. **Skills bar** — 3 catégories (Langages, Frameworks, IA & Data) — pas de peinture
12. Meander
13. **Section IV — Contact** (s-art-wrap: colosseum, id="contact") — liens principaux + projets
14. Meander + Footer

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
| creation-of-adam.jpg | Fond section projets | 447K |
| wanderer.jpg | Fond section parcours | 227K |
| vitruvian-man.jpg | Fond section passions | 438K |
| colosseum.jpg | Fond section contact | 653K |
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
- **Konami Code** — ↑↑↓↓←→←→BA : peintures 60% opacity 5s + halo terra

## Composants CSS notables
- `.proj-tag-row` — flex wrapper pour tag + statut, alignés à 22px de hauteur
- `.proj-oneliner` — encadré avec label flottant "Concrètement" / "In practice"
- `.feat-tech` — détail technique au hover des features (color clay, max-height transition)
- `.proj-minor-grid` — grille 3 colonnes pour projets secondaires
- `.metrics-bar` — 4 metric cards dans la section projets (dans le s-art-wrap)
- `.hero-badge` — badge "RECHERCHE STAGE" en terra
- `.skills-inner` — encadré avec fond semi-transparent pour compétences
- `.s-art` — `top:-10%; height:120%` pour absorber le parallax sans bandes sombres
- `.scroll-progress` — barre terra fixe en haut

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
- Prompts 1-5 : Création initiale — descriptions projets, skills bar, hero, meta tags, liens, badges statut, parcours resserré, responsive, animations stagger
- Prompts 6-9 : Skills bar déplacée, projets aérés, feat-tech hover, Stage UPHF enrichi, topbar nav, IDs ancrage, scroll-margin
- Ajout liens Vies2s + Dashboard Trading
- Correction feat-tech visible/invisible (cycle), ajout hero-links
- Refonte consolidée : s-wide 1100px, features raccourcies, one-liner label flottant, proj-num clay, citations plus apparentes, contact refait avec liens projets
- Phase 1 restructuration : Cinzel pour titres, hero simplifié (badge + liens), 3 majeurs + 3 compacts, metrics bar, images compressées (7.8MB→2.7MB), prefers-reduced-motion
- Correction typo : ajout Playfair Display, 4 registres typographiques distincts
- Téléchargement 3 screenshots projets (hygee, trading, vies2s)

### Session 2 (18 mars 2026)
- Phase 2 : Screenshots intégrés puis retirés — les liens live suffisent
- Phase 3 Tier 1 : scroll progress bar, active nav highlight, Ken Burns, stagger, math drift
- Fix : Ken Burns plus visible (scale 1.10, 20s), math drift amplifié, active nav getBoundingClientRect
- Phase 3 Tier 2 : parallax, méandre SVG (annulé → retour CSS), compteurs, 3D tilt, boutons magnétiques
- Fix fond : `.s-art` top:-10% height:120% pour absorber le parallax
- Restauration continuité : metrics remis dans le s-art-wrap des projets
- Phase 3 Tier 3 : grain pellicule (supprimé), clip-path reveal hero, hover passions, Konami Code
- Logo "Wachoo" cliquable, scroll reset au refresh
- `.proj-tag-row` flex wrapper, tags/statuts alignés à height:22px

## TODO (prochaines sessions)
- [ ] Envisager : "Choose your path" (recruteur vs dev), project modals, données live
