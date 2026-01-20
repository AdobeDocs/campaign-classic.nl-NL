---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 18%

---
# 📊 v7 Documentatiereorganisatie - Overzicht

**Gegenereerd**: 2026-01-13\
**Totale Omslagen**: 21\
**Totale Dossiers**: ~1.500

---

## 📈 Samenvatting

| Metrisch | Aantal | Percentage |
|--------|-------|------------|
| 📄 **Totale Dossiers** | 1.500 | 100% |
| ✅ **KEEP (v7-specifiek)** | 400 | 27% |
| 🗑️ **DELETE (in v8)** | 800 | 53% |
| ➡️ **VERPLAATSEN (aan v8)** | 200 | 13% |
| 🔍 **HERZIENING (onduidelijk)** | 100 | 7% |

**🎯Geschatte reductie**: 60-75% (1.500 → 400-600 bestanden)

---

## 📁 Mapanalyse op prioriteit

### 🟢 Prioriteit 1: 100% BEHOUD - Alleen v7-functies

| Map | Bestanden | Reden | v8-status | Actie |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Installatie op locatie/hybride | Alleen cloud in v8 | ✅ ALLE + badge BEHOUDEN |
| 📂 `/mrm/` | 5 | Marketing Resource Management | NOT in FFDA | ✅ ALLE + badge BEHOUDEN |
| 📂 `/surveys/` | 8 | Online enquêtes | NOT in FFDA | ✅ ALLE + badge BEHOUDEN |
| 📂 `/distributed/` | 7 | Gedistribueerde marketing | NOT in FFDA | ✅ ALLE + badge BEHOUDEN |
| 📂 `/response/` | 5 | Responsbeheer | Status onduidelijk | 🔍 VERIFIËREN EN HOUDEN |
| 📂 `/migration/` | 8 | v6.1 → v7 migratie | v7-specifiek | ✅ ALLES BEHOUDEN |
| **TOTAL** | **108** | **7%** | - | **Badge als v7-slechts** |

---

### 🔴 Prioriteit 2: 60-70% DELETE - hoge duplicatie

| Map | Totaal | HOUDEN | DELETE | VERPLAATSEN | REVISIE | Notities |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (%) | 67 (60%) | 8 (7%) | 18 (17%) | E-mail/SMS/Push in v8 |
| 📂 `/workflow/` | 121 | (20%) | 60 (50%) | 12 (%) | (20%) | Gemeenschappelijke activiteiten in v8 |
| 📂 `/reporting/` | 32 | 3 (10%) | (70%) | 2 (6%) | 5 (14%) | Rapporten opnieuw ontworpen in v8 |
| 📂 `/platform/` | 61 | 12 (20%) | 34 (55%) | 5 (8%) | 10 (17%) | Algemene functies in v8 |
| 📂 `/campaign/` | 11 | 2 (18%) | 7 (64%) | 1 (9%) | 1 (9%) | Campagnebeheer in v8 |
| **TOTAL** | **336** | **59** | **190** | **28** | **59** | **Hoog verminderingspotentieel** |

---

### 🟡 Prioriteit 3: 30-50% GEMENGD - Gedetailleerde analyse vereist

| Map | Totaal | % BEHOUDEN | DELETE % | Notities |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65% | 22% | Schema/DB-configuraties (meestal v7) |
| 📂 `/production/` | 43 | 65% | 23% | Serverbeheer (meestal v7) |
| 📂 `/integrations/` | 37 | 40% | 40% | Beschikbaarheid van connector controleren |
| 📂 `/interaction/` | 39 | 51% | 31% | Aanbiedingsengine (v8 controleren) |
| 📂 `/web/` | 26 | 92% | 8% | Web apps > Landing pages v8 |
| 📂 `/message-center/` | 16 | 60% | 30% | Transactieberichten |
| **TOTAL** | **230** | **~55%** | **~25%** | **vereist omslag-door-omslag overzicht** |

---

## 🎯 Snel winnen - Week 1

### Verwijdering met hoog vertrouwen (95-100% v8 overeenkomst)

| Map | Te verwijderen bestanden | Gevolgen | Inspanningen |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 bestanden | 🔥🔥🔥 Hoog | 2 dagen |
| 📂 `/workflow/` | 60 bestanden | 🔥🔥🔥 Hoog | 2 dagen |
| 📂 `/reporting/` | 22 bestanden | 🔥🔥 Medium | 1 dag |
| 📂 `/platform/` | 34 bestanden | 🔥🔥 Medium | 1 dag |
| 📂 `/campaign/` | 7 bestanden | 🔥 Laag | 0,5 dag |
| **TOTAL** | **190 dossiers** | **53% vermindering** | **6.5 dagen** |

**Voorbeelden**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (workflow) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

---

## 📋 Gedetailleerde mapindeling

### 📂 Aflevering (`/help/delivery/using/`) - 111 bestanden

| Categorie | Bestanden | HOUDEN | DELETE | VERPLAATSEN | REVISIE | Notities |
|----------|-------|------|--------|------|--------|-------|
| Aan de slag | 8 | 0 | 7 | 0 | 1 | Basisbeginselen in v8 |
| Email | 18 | 0 | 16 | 0 | 2 | Volledig in v8 |
| Sms | 7 | 1 | 5 | 0 | 1 | Midden-sourcing = BEHOUD |
| Push | 9 | 0 | 8 | 0 | 1 | Volledig in v8 |
| Direct mail | 4 | 0 | 4 | 0 | 0 | In v8 |
| Personalization | 8 | 1 | 6 | 0 | 1 | Coupons = KEEP |
| Sjablonen | 6 | 0 | 6 | 0 | 0 | In v8 |
| A/B-test | 11 | 0 | 10 | 0 | 1 | In v8 |
| Controle | 14 | 0 | 12 | 1 | 1 | Meestal in v8 |
| Problemen oplossen | 9 | 2 | 4 | 2 | 1 | Tips op de prem houden |
| Afleverbaarheid | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Geavanceerd | 9 | 11 | 5 | 5 | 8 | Gemengd |
| **TOTAL** | **111** | **18** | **67** | **8** | **18** | **60% kan worden geschrapt** |

**moet** houden:
- ✅ `personalized-coupons.md` - NIET in FFDA v8
- ✅ `sms-set-up-mid.md` - Midden-sourcing (on-prem)
- ✅ `spamassassin.md` - Spamfiltering op prem

**Snelle Voorbeelden van de Schrapping**:
- 🗑️ `about-email-channel.md` → 95% in `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95% in `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90% in `campaign-web/v8/msg/send-sms`

---

### 📂 Workflow (`/help/workflow/using/`) - 121 bestanden

| Categorie | Bestanden | HOUDEN | DELETE | VERPLAATSEN | REVISIE | Notities |
|----------|-------|------|--------|------|--------|-------|
| Aan de slag | 12 | 2 | 9 | 0 | 1 | Basisbeginselen in v8 |
| Targeting | 18 | 3 | 12 | 1 | 2 | Query/Splitsen in v8 |
| Stroom besturen | 15 | 2 | 10 | 1 | 2 | Algemeen in v8 |
| Activiteiten | 24 | 4 | 16 | 2 | 2 | Meest in v8 |
| Gebeurtenisactiviteiten | 8 | 1 | 6 | 0 | 1 | In v8 |
| MRM-activiteiten | 5 | 5 | 0 | 0 | 0 | NOT in FFDA |
| Technisch | 16 | 4 | 8 | 2 | 2 | Gemengd |
| Geavanceerd | 12 | 3 | 4 | 3 | 2 | Nuttige patronen |
| Gevallen gebruiken | 11 | 0 | 5 | 3 | 3 | Goede voorbeelden |
| **TOTAL** | **121** | **24** | **60** | **12** | **25** | **50% kan worden geschrapt** |

**moet** houden:
- ✅ Alle MRM-activiteiten (5 bestanden) - NIET in FFDA versie 8
- ✅ Configuraties op locatie
- ✅ Geavanceerde technische workflows

**Snelle Voorbeelden van de Schrapping**:
- 🗑️ `query.md` → 95% in `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95% in `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95% in `campaign/v8/automation/workflow/enrichment`

---

### 📂 Installatie (`/help/installation/using/`) - 75 bestanden

| Categorie | Bestanden | Actie | Notities |
|----------|-------|--------|-------|
| Serverinstallatie | 18 | ✅ HOUDEN | Alleen op locatie |
| Database instellen | 12 | ✅ HOUDEN | Alleen op locatie |
| Configuratie | 15 | ✅ HOUDEN | nlserver, enz. |
| Netwerk | 8 | ✅ HOUDEN | Beveiligingszones |
| Integratie | 10 | ✅ HOUDEN | LDAP, enz. |
| Problemen oplossen | 8 | ✅ HOUDEN | Problemen tijdens de prem |
| Algemene documenten | 4 | 🗑️ DELETE | In v8-startgids |
| **TOTAL** | **75** | **71 KEEP/4 DELETE** | **95% v7-specifiek** |

**Reden**: v8 is wolk-slechts, zijn alle on-premise opstellingsdocumenten v7-specifiek.

---

### 📂 Web (`/help/web/using/`) - 26 bestanden

| Categorie | Bestanden | HOUDEN | DELETE | Notities |
|----------|-------|------|--------|-------|
| Webtoepassingen | 14 | 14 | 0 | Geavanceerde functies niet in v8 |
| Webformulieren | 8 | 8 | 0 | Meer dan v8-bestemmingspagina&#39;s |
| Landingspagina&#39;s | 2 | 0 | 2 | Basispagina&#39;s in v8 |
| HTML Editor | 2 | 2 | 0 | Verschil ten opzichte van v8 |
| **TOTAL** | **26** | **24** | **2** | **92% v7-specifiek** |

**Reden**: v7 heeft het volledige kader van de Toepassingen van het Web, v8 heeft het Aanlanden van Pagina&#39;s vereenvoudigd.

---

## ✅ Actieplan

### Week 1: Verwijdering met grote impact
- [ ] `/delivery/`: Verwijder 67 bestanden (e-mail, SMS, push-basics)
- [ ] `/workflow/`: Verwijder 60 bestanden (algemene activiteiten)
- [ ] `/reporting/`: 22 bestanden verwijderen (standaardrapporten)
- [ ] `/platform/`: 34 bestanden verwijderen (algemene functies)
- [ ] `/campaign/`: 7 bestanden verwijderen (campagnebeheer)
- **Totaal**: 190 schrapte dossiers (13% vermindering)

### Week 2: v7-specifieke Badging
- [ ] `/installation/`: 71-bestanden indelen als &quot;alleen on-premise versie 7&quot;
- [ ] `/mrm/`: Badge 5-bestanden als &quot;Niet beschikbaar in FFDA v8&quot;
- [ ] `/surveys/`: Badge 8 bestanden als &quot;Niet beschikbaar in FFDA v8&quot;
- [ ] `/distributed/`: Badge 7-bestanden als &quot;Niet beschikbaar in FFDA v8&quot;
- [ ] `/web/`: 24 bestanden indelen als &quot;v7-webtoepassingen&quot;
- **Totaal**: 115 dossiers badged

### Week 3: Inhoud migreren
- [ ] Tips voor het oplossen van problemen migreren van `/delivery/` naar v8
- [ ] Best practices voor workflow migreren naar v8
- [ ] Geavanceerde patronen migreren van `/platform/` naar v8
- **Totaal**: 40 dossiers gemigreerd toen geschrapt

### Week 4: Handmatige revisie
- [ ] Gemengde inhoud controleren `/configuration/`
- [ ] Beschikbaarheid van de connector controleren `/integrations/`
- [ ] Bekijken `/interaction/` biedt motordekking
- [ ] Status van revisie `/response/` -functie
- **Totaal**: 50 gereviseerde dossiers en beslist

---

## 📊 Verwachte resultaten

| Fase | Betrokken bestanden | Cumulatief % |
|-------|----------------|--------------|
| Week 1: Verwijderingen | 190 | 13% |
| Week 2: Badging | 115 | 20% |
| Week 3: Migratie | 40 | 23% |
| Week 4: Revisie | 50 | 26% |
| **TOTAL** | **395** | **26% verwerkte** |

**Resterend**: ~1.100 dossiers om in verdere fasen te verwerken

**Definitief Doel**: 1.500 → 400-600 dossiers (60-73% vermindering)

---

## 🎯 Succeswaarden

| Metrisch | Target | Status |
|--------|--------|--------|
| Verwijderde bestanden | 800+ (53%) | ⏳ In behandeling |
| Bestanden geblokkeerd | 200+ (13%) | ⏳ In behandeling |
| Bestanden gemigreerd | 200+ (13%) | ⏳ In behandeling |
| Verbroken koppelingen | 0 | ⏳ In behandeling |
| Toelating van belanghebbenden | ✅ | ⏳ In behandeling |

---

**Laatste bijgewerkte**: 2026-01-13\
**Volgende Overzicht**: Na Week 1 uitvoering

