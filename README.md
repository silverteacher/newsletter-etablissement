# Générateur de newsletter — Établissement

Page HTML interactive pour créer et prévisualiser une newsletter éducative, piloter son contenu depuis un fichier Excel, et l'exporter en PDF.

## Utilisation

1. Ouvrez `index.html` dans un navigateur (en local ou via GitHub Pages).
2. Cliquez sur **📂 Importer Excel (.xlsx)** et choisissez votre fichier rempli à partir de `modele_donnees.xlsx`.
   - Ou cliquez sur **📄 Utiliser data.json** pour charger l'exemple fourni.
3. La newsletter s'affiche avec le contenu importé.
4. Cliquez sur **⬇️ Exporter en PDF** pour générer un PDF propre du rendu final.

## Structure du fichier Excel (`modele_donnees.xlsx`)

- **Onglet "Contenu"** : titre, date d'édition, texte d'intro, nom et adresse de l'établissement, email de contact.
- **Onglet "Articles"** : une ligne par article (catégorie, public cible, titre, description, lien, couleur du tag).
- **Onglet "Evenements"** : une ligne par événement à venir (mois, jour, titre, description).

Éditez ces colonnes puis ré-importez le fichier dans `index.html`.

## Déploiement sur GitHub Pages

1. Allez dans **Settings > Pages** du dépôt.
2. Source : branche `main`, dossier `/ (root)`.
3. La page sera accessible à l'URL fournie par GitHub Pages (ex. `https://silverteacher.github.io/newsletter-etablissement/`).

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Page interactive (import Excel + rendu + export PDF) |
| `data.json` | Exemple de données par défaut |
| `modele_donnees.xlsx` | Modèle Excel à dupliquer et remplir |

## Notes techniques

- Lecture du fichier Excel en JavaScript via [SheetJS](https://sheetjs.com/), aucune donnée n'est envoyée à un serveur.
- Export PDF via [html2pdf.js](https://github.com/eKoopmans/html2pdf.js), qui capture fidèlement le rendu visuel (couleurs, mise en page).
- Aucun backend requis : compatible avec GitHub Pages en hébergement statique.
