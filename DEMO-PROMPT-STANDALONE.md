---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 DEMO PROMPT - Documentatieanalyse v7 tot v8

**kopiëren-kleef deze volledige herinnering in Cursor/ChatGPT om het even welke omslag te analyseren v7**

---

## 📋 DE PROMPT (KOPIËREN VAN HIER) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

---

## 🎯 DEMO-INSTRUCTIES

### Stap 1: De prompt weergeven
1. Dit bestand openen (`DEMO-PROMPT-STANDALONE.md`)
2. Naar de sectie &quot;PROMPT&quot; schuiven
3. Zeg: *&quot;Dit is onze geautomatiseerde analyseherinnering&quot;*

### Stap 2: De prompt kopiëren
1. Selecteer alles van &quot;# de Analyse van de Documentatie van de Campagne v7 aan het eind&quot;
2. Kopiëren naar klembord
3. Zeg: *&quot;Ik kopieer enkel de volledige herinnering...&quot;*

### Stap 3: Plakken en uitvoeren
1. Cursor openen
2. De prompt plakken
3. Zeg: *&quot;...en kleef het in Cursor&quot;*
4. Druk op Enter

### Stap 4: Resultaten tonen
1. Wachten op genereren (~30-60 seconden)
2. Door het gegenereerde rapport bladeren
3. Belangrijke gedeelten markeren:
   - 📊 Samenvattingsstaten
   - 📋 Bestand-voor-bestand tabel
   - ✅ Sectie behouden
   - 🗑️ Snel wint
   - 🎯 Uitvoeringsplan

### Stap 5: Wow Moment
1. De markeringsvoorvertoning weergeven
2. Punt uit:
   - *&quot;111 dossiers automatisch geanalyseerd&quot;*
   - *&quot;67 veilig te schrappen dossiers (60% vermindering)&quot;*
   - *&quot;18 v7-specifieke geïdentificeerde dossiers&quot;*
   - *&quot;Volledig uitvoeringsplan met chronologie&quot;*

---

## 💡 DEMO-TIPS

### Interactief maken
**vraag het publiek**: *&quot;Welke omslag zouden wij moeten analyseren?&quot;*
- levering ✅ (111 bestanden - indrukwekkend)
- workflow ✅ (121 bestanden - nog groter)
- web ✅ (26 bestanden - snelle demo)
- melden ✅ (32 bestanden, snel)

### Aanpassen op de vlucht
**toon flexibiliteit**: Verander de omslagweg in de herinnering:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Belangrijkste kenmerken markeren
1. **Automatisering**: *&quot;Geen nodig handwerk&quot;*
2. **Nauwkeurigheid**: *&quot;gebruikt v8 documentatie voor vergelijking&quot;*
3. **Handelbaar**: *&quot;Klaar-om plan met checkboxes uit te voeren&quot;*
4. **Slim**: *&quot;identificeert v7-specifieke eigenschappen automatisch&quot;*

### Tijdvergelijking
**vóór**: *&quot;Handmatige analyse = 2-3 dagen per omslag&quot;*\
**na**: *&quot;Geautomatiseerde analyse = 30 seconden per omslag&quot;*

**ROI**: *&quot;21 omslagen × 2 dagen = 42 dagen → 15 minuten&quot;*

---

## 📊 VERWACHTE VOORVERTONING UITVOER

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

---

## 🎬 DEMO-SCRIPT

**Openend**:
> &quot;Vandaag zal ik u tonen hoe wij v7 documentreorganisatie gebruikend AI automatiseren. Dit kostte vroeger weken, nu duurt het minuten.&quot;

**Probleem**:
> &quot;We hebben 1.500+ v7 documentatiebestanden. Veel hiervan worden gedupliceerd in versie 8. We moeten identificeren wat we moeten behouden, verwijderen of migreren.&quot;

**Oplossing**:
> &quot;We hebben een slimme prompt gemaakt die elke map analyseert en aanbevelingen voor handelingen genereert.&quot;

**Demo**:
> &quot;Laat me je tonen. Ik zal de map &#39;delivery&#39; analyseren met 111 bestanden...&quot;
> 
> [ herinnering van het Exemplaar, deeg, voer uit ]
> 
> &quot;...en over 30 seconden krijgen we een volledige analyse.&quot;

**Resultaten**:
> &quot;Kijk naar dit:
> - 67 te verwijderen bestanden (60% reductie)
> - 18 v7-specifieke bestanden geïdentificeerd
> - 8 te migreren bestanden
> - Volledig uitvoeringsplan van 3 weken
> 
> Alles geautomatiseerd. Alles nauwkeurig.&quot;

**dicht**:
> &quot;Hetzelfde proces werkt voor alle 21 mappen. Wat vroeger 6 weken duurde, duurt nu 15 minuten.&quot;

---

## 🚀 READY TO DEMO!

**enkel**:
1. Dit bestand openen
2. De prompt kopiëren
3. Plakken in cursor
4. De magie tonen ✨

**Totale manifestatietijd**: 3-5 notulen\
**Wow factor**: 🔥🔥🔥

