# 📄 Dossier des documents PDF

Ce dossier contient tous les fichiers PDF des cours partagés avec les élèves.

## 🆕 Format multi-fichiers

Depuis décembre 2025, le système supporte **plusieurs fichiers par matière** :
- 🖼️ Slides (présentation)
- 📄 Document texte (support complet)
- 📝 Notes supplémentaires
- ✏️ Exercices
- ✅ Corrections

**📖 Consultez le [GUIDE-FORMAT-MULTI-FICHIERS.md](../GUIDE-FORMAT-MULTI-FICHIERS.md) pour la documentation complète.**

## Structure recommandée

Organisez les fichiers avec une convention de nommage claire :

```
docs/
├── chapitre1-intro-slides.pdf
├── chapitre1-intro-texte.pdf
├── chapitre1-intro-notes.pdf
├── chapitre2-hardware-slides.pdf
├── chapitre2-hardware-texte.pdf
├── tp1-enonce.pdf
├── tp1-correction.pdf
└── ...
```

## Ajout d'un nouveau document

### Nouveau format (recommandé) - Plusieurs fichiers

1. Placez vos fichiers PDF dans ce dossier
2. Ajoutez une entrée dans `data/files.json` :

```json
{
  "id": "chap1",
  "date": "2025-01-15",
  "category": "Informatique",
  "label": "Chapitre 1 – Introduction",
  "classes": ["5P-AMPC", "6P-AMPC"],
  "files": [
    {
      "type": "slides",
      "label": "Slides",
      "path": "docs/chapitre1-intro-slides.pdf"
    },
    {
      "type": "document",
      "label": "Document texte",
      "path": "docs/chapitre1-intro-texte.pdf"
    },
    {
      "type": "notes",
      "label": "Notes supplémentaires",
      "path": "docs/chapitre1-intro-notes.pdf"
    }
  ]
}
```

### Ancien format (toujours supporté) - Un seul fichier

```json
{
  "id": "nouveau-doc",
  "date": "2025-01-20",
  "category": "Informatique",
  "label": "Nouveau chapitre – Réseaux",
  "file": "docs/nouveau-chapitre-reseaux.pdf",
  "classes": ["6P-AMPC", "6T-TI"]
}
```

## Types de fichiers disponibles

| Type | Description | Icône |
|------|-------------|-------|
| `slides` | Présentation PowerPoint/PDF | 🖼️ |
| `document` | Support de cours complet | 📄 |
| `notes` | Notes supplémentaires, résumé | 📝 |
| `exercices` | Feuille d'exercices | ✏️ |
| `correction` | Correction des exercices | ✅ |

## Convention de nommage

**Format recommandé :** `chapitre{numero}-{titre}-{type}.pdf`

### Exemples ✅
```
chapitre1-intro-slides.pdf
chapitre1-intro-texte.pdf
chapitre1-intro-notes.pdf
tp1-reseaux-enonce.pdf
tp1-reseaux-correction.pdf
```

### À éviter ❌
```
Chapitre 1 Introduction.pdf
Exercices (1).pdf
TP_PRATIQUE_EXCEL.PDF
document final version2.pdf
```

## Bonnes pratiques

- ✅ Utilisez des noms de fichiers explicites sans espaces ni caractères spéciaux
- ✅ Préférez les tirets (`-`) aux underscores (`_`)
- ✅ Utilisez la casse minuscule pour les noms de fichiers
- ✅ Vérifiez que le PDF est accessible avant de le référencer
- ✅ Compressez les PDF volumineux pour optimiser le chargement
- ✅ Groupez les fichiers d'un même chapitre avec un préfixe commun

