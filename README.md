# La lettre de la DRANE — Générateur de newsletter

Générateur de newsletter interactive piloté par Excel, avec export PDF. Conçu pour la Délégation de région académique au numérique éducatif (DRANE Hauts-de-France).

## Utilisation

1. Ouvrez `index.html` dans un navigateur (idéalement Google Chrome — voir la section export PDF ci-dessous).
2. Cliquez sur **📂 Importer Excel (.xlsx)** et choisissez votre fichier rempli à partir de `modele_donnees.xlsx`.
   - Ou cliquez sur **📄 Utiliser data.json** pour charger l'exemple fourni.
3. La newsletter s'affiche avec le contenu importé. Utilisez les filtres (Tous / Enseignants / Élèves / Parents) pour prévisualiser un public en particulier.
4. Cliquez sur **🖨️ Exporter en PDF** pour générer un PDF propre du rendu final.

## Structure du fichier Excel (`modele_donnees.xlsx`)

- **Onglet "Contenu"** : titre, sous-titre, date d'édition, texte d'intro, email de contact.
- **Onglet "Articles"** : une ligne par article (catégorie, publics ciblés séparés par une virgule, titre, description, lien, couleur du tag).
- **Onglet "Evenements"** : une ligne par événement à venir (mois, jour, titre, description). Si cet onglet est vide ou ne contient que des lignes vides, la section "Événements à venir" est automatiquement masquée dans la newsletter.

Éditez ces colonnes puis ré-importez le fichier dans `index.html`.

## Exporter en PDF (recommandé avec Google Chrome)

Le bouton **🖨️ Exporter en PDF** déclenche l'impression native du navigateur (`window.print()`). Cette méthode a été retenue plutôt qu'une librairie JavaScript de conversion, car elle seule garantit que les liens restent réellement cliquables dans le PDF final — Chrome génère le PDF directement à partir du rendu réel de la page, sans passer par une image intermédiaire.

**Étapes détaillées (Google Chrome) :**

1. Importez vos données (Excel ou `data.json`).
2. Cliquez sur **🖨️ Exporter en PDF**. La fenêtre d'impression de Chrome s'ouvre.
3. Dans le champ **Destination**, sélectionnez **Enregistrer au format PDF** (et non une imprimante physique).
4. Cliquez sur **Plus de paramètres** pour déployer les options avancées.
5. Activez impérativement la case **Graphiques d'arrière-plan** (parfois nommée *Background graphics*). Sans cette option, les fonds violets, les tags colorés et les bordures des cartes n'apparaîtront pas dans le PDF — seul le texte brut sera visible.
6. Vérifiez que la **mise en page** est bien réglée sur **Portrait**.
7. Cliquez sur **Enregistrer**, choisissez l'emplacement du fichier, puis validez.

**Pourquoi Chrome plutôt qu'un autre navigateur ?** Chrome respecte le mieux les règles CSS d'impression utilisées ici (`break-inside: avoid`, gestion des sauts de page entre catégories et cartes). Firefox et Safari fonctionnent aussi, mais peuvent occasionnellement mal gérer certains sauts de page sur les grilles de cartes ; en cas de rendu imparfait sur un autre navigateur, essayez d'abord avec Chrome avant de signaler un problème de mise en page.

**Astuce :** un bandeau d'aide rappelant ces réglages apparaît automatiquement dans la page dès qu'une newsletter est chargée.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Page interactive (import Excel + rendu + export PDF) |
| `data.json` | Exemple de données par défaut |
| `modele_donnees.xlsx` | Modèle Excel à dupliquer et remplir |
| `logo_drane.jpg` | Logo DRANE Hauts-de-France (en-tête) |
| `logo_academie_lille.jpg` | Logo Académie de Lille (en-tête) |

## Notes techniques

- Lecture du fichier Excel en JavaScript via [SheetJS](https://sheetjs.com/), aucune donnée n'est envoyée à un serveur.
- Export PDF via l'impression navigateur native (`window.print()`), pour préserver des liens hypertextes réellement cliquables.
- Aucun backend requis : compatible avec GitHub Pages en hébergement statique.
- Si un logo ne se charge pas, un message explicite apparaît directement dans la page (nom du fichier attendu) plutôt qu'une icône cassée silencieuse.
