# MD Viewer

Visualiseur Markdown standalone hébergé sur GitHub Pages — aucune installation, aucun serveur.

**[→ Ouvrir l'app](https://nvalettepro-sudo.github.io/markdown_viewer/)**
https://nvalettepro-sudo.github.io/markdown_viewer/

## Fonctionnalités

- **Éditeur / aperçu** en temps réel avec split-pane redimensionnable
- **Import .md / .txt** par bouton ou glisser-déposer
- **Import PDF** — extraction du texte et conversion automatique en Markdown
- **Import URL** — récupère une page web et la convertit en Markdown propre
- **Export** `.md` ou `.html` standalone
- **Frontmatter YAML** affiché sous forme de tableau de métadonnées
- Thème **sombre / clair**
- Coloration syntaxique des blocs de code (highlight.js)

## Raccourcis clavier

| Raccourci | Action |
|-----------|--------|
| `Ctrl+O` | Ouvrir .md |
| `Ctrl+P` | Ouvrir PDF |
| `Ctrl+U` | Importer URL |
| `Ctrl+S` | Exporter .md |
| `Ctrl+E` | Exporter .html |
| `Ctrl+B` | Gras |
| `Ctrl+I` | Italique |

## Stack

Fichier HTML unique, zéro dépendance locale. Librairies chargées via CDN :

- [marked](https://marked.js.org/) — parsing Markdown
- [highlight.js](https://highlightjs.org/) — coloration syntaxique
- [PDF.js](https://mozilla.github.io/pdf.js/) — extraction PDF
- Google Fonts — JetBrains Mono + Crimson Pro
