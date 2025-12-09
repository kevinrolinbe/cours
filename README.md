# 📚 Documents de cours - Site statique

Mini-site hébergé via GitHub Pages permettant de partager aux élèves les PDF des cours et le journal de classe.

## 🎯 Objectif

Fournir une interface simple et efficace pour que les élèves puissent :
- Accéder aux documents de cours en fonction de leur classe
- Consulter le journal de classe avec les activités quotidiennes
- Rechercher rapidement un document spécifique

## 📁 Architecture du projet

```
/
├── index.html              # Page principale unique
├── data/                   # Fichiers JSON
│   ├── files.json         # Liste des documents avec métadonnées
│   ├── journal-5p-ampc.json
│   ├── journal-6p-ampc.json
│   ├── journal-5t-ti.json
│   └── journal-6t-ti.json
└── docs/                   # Fichiers PDF des cours
    ├── chapitre1-intro.pdf
    ├── chapitre2-hardware.pdf
    └── chapitre3-os.pdf
```

## ✨ Fonctionnalités

### 1. Sélection de classe
Menu déroulant proposant 4 classes :
- 5P AMPC (5e Professionnel – AMPC)
- 6P AMPC (6e Professionnel – AMPC)
- 5T TI (5e Technique – TI)
- 6T TI (6e Technique – TI)

### 2. Liste des documents filtrée
- Affichage dynamique des documents selon la classe sélectionnée
- **Groupement par catégorie** pour une meilleure lisibilité
- **Tri automatique** par date de publication
- Badges affichant la date des documents

### 3. Barre de recherche
- Recherche en temps réel dans les titres et catégories
- Debouncing (300ms) pour optimiser les performances
- Affichage du nombre de résultats par catégorie

### 4. Journal de classe
- Chargement automatique du journal correspondant à la classe
- Entrées triées par date décroissante
- Formatage des dates en français (ex: "lundi 5 septembre 2025")
- Design amélioré avec cartes pour chaque entrée

### 5. Mise en cache intelligente
- **Cache localStorage** pour réduire les requêtes réseau
- Durée du cache : **1 heure**
- Indicateurs dans la console pour suivre l'utilisation du cache
- **Bouton "Actualiser les données"** pour vider le cache et recharger manuellement
- Fonction `clearCoursCache()` également disponible en console

## 🔧 Optimisations techniques

### Performance
- ✅ Mise en cache avec localStorage
- ✅ Debouncing sur la recherche
- ✅ Chargement lazy des journaux
- ✅ Cache-busting avec timestamp

### Sécurité
- ✅ Échappement HTML pour prévenir XSS
- ✅ Attributs `rel="noopener"` sur les liens externes

### UX/UI
- ✅ Groupement par catégorie
- ✅ Compteurs de documents
- ✅ Messages d'état clairs
- ✅ Design responsive
- ✅ Émojis pour une meilleure lisibilité

## 📝 Structure des données

### files.json
```json
[
  {
    "id": "1",
    "date": "2025-01-15",
    "category": "Informatique",
    "label": "Chapitre 1 – Introduction à l'informatique",
    "file": "docs/chapitre1-intro.pdf",
    "classes": ["5P-AMPC", "6P-AMPC", "5T-TI", "6T-TI"]
  }
]
```

### journal-*.json
```json
{
  "classId": "5P-AMPC",
  "entries": [
    {
      "date": "2025-09-05",
      "content": "Chapitre 1 – Introduction à l'informatique."
    }
  ]
}
```

## 🚀 Utilisation

### En développement
1. Ouvrir `index.html` dans un navigateur
2. Sélectionner une classe
3. Tester la recherche

### En production (GitHub Pages)
1. Push sur la branche principale
2. Le site sera automatiquement déployé
3. Accès via : `https://[username].github.io/cours/`

## 🛠️ Maintenance

### Ajouter un nouveau document
1. Placer le PDF dans `/docs/`
2. Ajouter une entrée dans `data/files.json` :
   ```json
   {
     "id": "4",
     "date": "2025-01-20",
     "category": "Informatique",
     "label": "Chapitre 4 – Les réseaux",
     "file": "docs/chapitre4-reseaux.pdf",
     "classes": ["5P-AMPC", "6P-AMPC"]
   }
   ```

### Ajouter une entrée au journal
1. Ouvrir le fichier `data/journal-[classe].json`
2. Ajouter une entrée dans le tableau `entries` :
   ```json
   {
     "date": "2025-09-12",
     "content": "Description de l'activité du jour."
   }
   ```

### Vider le cache
Pour forcer le rechargement des données (utile après une mise à jour) :
- Ouvrir la console du navigateur (F12)
- Taper : `clearCoursCache()`
- Recharger la page

## 🎨 Technologies utilisées

- **HTML5** : Structure sémantique
- **CSS3** : Styles modernes avec flexbox
- **JavaScript (ES6+)** : Logique client-side
- **LocalStorage API** : Mise en cache
- **Fetch API** : Chargement des données JSON

## 📄 Licence

Voir le fichier [LICENSE.md](LICENSE.md)

---

💡 **Astuce** : Le cache est automatiquement invalidé après 1 heure. Pour les mises à jour urgentes, utilisez `clearCoursCache()` dans la console.

