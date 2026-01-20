---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7 Documentation Reorganisation Kit

**{2 herinneringen pour analyser et réorganizer la doc v7 → v8**

---

## 📁 Fichiers

### 🔍 Vragen (instructies)

| Fichier | Beschrijving | Uitvoer |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analyseren, détaillée d&#39;UN folder avec % match | `[folder]-detailed-analysis.md` |

---

## 🚀 Gebruik

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère**:
- 📊 Samenvatting (stats globales)
- 📁 De 21 mappen analyseren
- 🎯 Prioriteit matrijs de
- ✅ Handelingspunten
- ⚠️ Risques
- 📈 Métriques

**Kaart**: ~50-60 pagina&#39;sAfname

---

### 2️⃣ Analyze Détaillée d&#39;un Folder

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère**:
- 📊 Stats du folder
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 Cliquables van Liens (v7 + Experience League)
- 📈 Jusqu&#39;à 3 matchs v8 par fichier avec %
- 📄 Bestand opnieuw toewijzen per bestand
- 🎯 Plan de réorganisation
- ✅ Selectievakjes voor tekstspatiëring

**Kaart** : ~30-40 pagina&#39;sAfname

---

## 📊 Voorbeeld d&#39;Output

### Vragen 1 (overzicht)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Vragen 2 (gedetailleerde map)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 Workflowaanbevolen

### Semaine 1: Vue d&#39;ensemble
1. Exécuter **Herinnering 1** → Obtenir `v7-reorganization-overview.md`
2. Prioriteiten voor mappen voor id&#39;s
3. Deelnemers in de omgeving van partners

### Semaine 2-4: Analyze détaillée
1. Pour chaque folder:
   - Exécuter **Vragen 2**
   - Obtenir `[folder]-detailed-analysis.md`
   - Geldigheidsbesluiten
   - Handelingen van Commentaar

### Semaine 5+ : Exécution
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrer le contenu manquant (MOVE)
4. Revisor les cas ambigus (REVIEW)

---

## 💡 Tips

### Vragen om kleuren
- ✅ Copier/coller l&#39;intégralité du prompt
- ✅ Nieuwe bestandsindeling pas modifier le
- ✅ Adapter seulement le chemin du folder (Vraag 2)

### Uitvoer van ronddraaiende blokken
- 📝 Output en Markdown (pas HTML)
- 🔗 Hiermee worden de cliquables automatisch geladen
- ✅ Selectievakjes voor tekstspatiëring
- 📊 Stats et pourcentages
- 🎨 Emojis et icônes

### Pour l&#39;analyze
- 🎯 Commencer par les gros folders (levering, workflow)
- ⚡ Prioriser les quick wins (95-100% overeenkomst)
- 🔍 Reviewer-handleiding les cas ambigus (&lt;70% overeenkomst)
- ✅ Grote onderdrukking voor Valideren van gemiddelde kmo&#39;s

---

## ⚠️ Belangrijk

### Avant de supprimer
1. ✅ Vérifier l&#39;équivalent v8
2. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu v7-specific
3. ✅ Mettre à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers v7-only
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi c&#39;est alleen v7
3. ✅ Levensmiddelen in beperkte mate v8

---

## 🆘 Ondersteuning

**Vragen**?
- Vragen om nieuwe fonctionne pas → Vérifier les chemins des repos
- Uitvoertrop lang → Demander un résumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

---

**Dernière mise à jour** : 2026-01-13

