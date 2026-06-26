# markdown_viewer
Aperçu du projet
MD Viewer est une application HTML mono-fichier, sans aucune dépendance, hébergée sur GitHub Pages. Tout (structure HTML, CSS et JavaScript) est inclus index.html. Aucune étape de compilation, aucun gestionnaire de paquets, aucun outil de regroupement de modules n'est nécessaire.

URL en direct : https://nvalettepro-sudo.github.io/markdown_viewer/

Développement
Ouvrir index.htmldirectement dans un navigateur ou exécuter localement :

python3 -m http.server 8080
Aucune installation, aucune compilation. Les modifications index.htmlsont immédiatement testables en actualisant le navigateur.

Architecture
L'application est un éditeur Markdown à volets divisés avec aperçu en direct. Toute la logique se trouve dans un seul <script>bloc en bas de la fenêtre index.html.

Sections clés (marquées par ══des commentaires dans le code source) :

Section	Responsabilité
Variables CSS /[data-theme]	Thème clair/sombre via propriétés CSS personnalisées
parseFrontmatter/frontmatterToHTML	Analyse les métadonnées de type YAML ( ---bloc) et les affiche sous forme de tableau de métadonnées
render()	Markdown avec délai d'affichage (150 ms) → HTML via marked.js + highlight.js
convertPDF()	Extraction de texte PDF en deux étapes via PDF.js : calibration des tailles de police → déduction des niveaux de titres → génération de Markdown
fetchURL()	Cascade de proxys CORS (corsproxy.io → allorigins.win × 2) avec un délai d'expiration de 12 secondes par proxy
htmlToMarkdown()	Convertisseur HTML vers Markdown basé sur le DOM : supprime la navigation, le pied de page et les publicités, trouve les barres obliques <main>(/) <article>, et convertit les nœuds de manière récursive.
exportHTML()	Génère un fichier HTML autonome avec CSS intégré
redimensionnement du séparateur	Redimensionnez la fenêtre éditeur/aperçu en la faisant glisser via mousedown/ mousemove/mouseup
Dépendances CDN externes (aucune copie locale — tout est chargé depuis cdnjs.cloudflare.com) :

marked9.1.6 — Analyse Markdown
highlight.js11.9.0 — Coloration syntaxique
pdf.js3.11.174 — Extraction de texte PDF (avec Web Worker)
Polices Google — JetBrains Mono + Crimson Pro
Contraintes
Pas de frameworks, pas de npm — un seul fichier HTML déployable suffit.
Limitation CORS : l’importation d’URL repose sur des proxys publics ; elle échouera pour les sites qui les bloquent. L’utilisation d’une cascade de proxys est la solution de contournement prévue.
Heuristique PDF : La détection des titres convertPDF()est basée sur la taille de la police (médiane × multiplicateurs). Elle est approximative par conception.
Déploiement GitHub Pages : push vers main— Pages est index.htmlautomatiquement servie à la racine du dépôt.
