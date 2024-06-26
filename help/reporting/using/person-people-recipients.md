---
product: campaign
title: Personen, personen en ontvangers
description: Personen, personen en ontvangers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 5%

---

# Persoon/personen en ontvangers {#person-people-and-recipients}



Dit voorbeeld helpt u het verschil te begrijpen tussen een persoon/persoon en een ontvanger in Adobe Campaign. Wij zullen een levering naar verscheidene mensen verzenden om het verschil tussen mensen en ontvangers te benadrukken terwijl het detailleren van de berekeningsmethode voor de volgende indicatoren:

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>Deze indicatoren worden gebruikt in de **[!UICONTROL Tracking indicators]** verslag. Raadpleeg voor meer informatie hierover [Traceringsindicatoren](../../reporting/using/delivery-reports.md#tracking-indicators).

Er worden drie koppelingen toegevoegd aan een levering. Het wordt verzonden naar 4 ontvangers:

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : deze ontvanger opent het e-mailbericht niet (en klikt daarom niet op koppelingen).
* **[!UICONTROL Marie Stuart]** : opent de e-mail maar klikt niet op koppelingen.
* **[!UICONTROL Florian David]** : opent de e-mail en klikt 9 keer op de koppelingen. Hij stuurt het e-mailbericht ook door naar iemand die het opent en tweemaal klikt.
* **[!UICONTROL Henry Macdonald]** : deze ontvanger heeft zijn internetbrowser geconfigureerd om cookies af te wijzen. Hij opent de e-mail en klikt vier keer op de koppelingen.

De volgende trackinglogboeken worden geretourneerd:

![](assets/s_ncs_user_indicators_example_2.png)

Om een duidelijker beeld te krijgen van hoe mensen en ontvangers worden geteld, gaan we de logboeken van elk profiel analyseren.

## Stap 1: John {#step-1--john}

**[!UICONTROL John Davis]** Hiermee opent u het e-mailbericht niet (en klikt u daarom niet op koppelingen).

![](assets/s_ncs_user_indicators_example_8.png)

Omdat John niet opende en niet klikte in de e-mail, verschijnt hij niet in de logboeken.

**Tussentijdse berekening:**

|   | Ontvangers waarop is geklikt | Personen die hebben geklikt | Ontvangers die geopend zijn |
|---|---|---|---|
| John | - | - | - |
| Tussentotaal | 0 | 0 | 0 |

## Stap 2: {#step-2--marie}

**[!UICONTROL Marie Stuart]** Hiermee opent u het e-mailbericht, maar klikt u niet op koppelingen.

![](assets/s_ncs_user_indicators_example_7.png)

Marie&#39;s open wordt getoond in het volgende logboek:

![](assets/s_ncs_user_indicators_example_4bis.png)

De open lijst wordt toegewezen aan een ontvanger: Marie. Adobe Campaign voegt daarom een nieuwe begunstigde aan de telling toe.

**Tussentijdse berekening:**

|   | Ontvangers waarop is geklikt | Personen die hebben geklikt | Ontvangers die geopend zijn |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Tussentotaal | 0 | 0 | 1 |

## Stap 3: Florian {#step-3--florian}

**[!UICONTROL Florian David]** Hiermee opent u het e-mailbericht en klikt u 9 keer op de koppelingen. Hij stuurt het e-mailbericht ook door naar iemand die het opent en tweemaal klikt.

![](assets/s_ncs_user_indicators_example_9.png)

De acties van Florian (open en 9 klikken) verschijnen in de volgende logboeken:

![](assets/s_ncs_user_indicators_example_3bis.png)

**Ontvangers**: open en klikken worden toegewezen aan dezelfde ontvanger (Florian). Aangezien deze ontvanger verschilt van de vorige (Marie), voegt Adobe Campaign een nieuwe ontvanger aan de telling toe.

Personen: Omdat de browser van deze ontvanger cookies accepteert, kunnen we zien dat dezelfde id (UUID) is toegewezen aan alle kliklogboeken: **`fe37a503 [...]`**. Adobe Campaign identificeert deze klikken correct als behorend tot dezelfde persoon. Er wordt een nieuwe persoon toegevoegd aan de telling.

**Tussentijdse berekening:**

|   | Ontvangers waarop is geklikt | Personen die hebben geklikt | Ontvangers die geopend zijn |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Tussentotaal | 1 | 1 | 2 |

De volgende logboeken vallen samen met de open en twee klikken die worden uitgevoerd door de persoon die Florian de e-mail heeft doorgestuurd naar:

![](assets/s_ncs_user_indicators_example_6bis.png)

**Ontvangers**: de open en kliks worden toegewezen aan de ontvanger die de e-mail (Florian) heeft doorgestuurd. Aangezien deze ontvanger reeds is geteld, blijft het aantal ontvangers gelijk.

![](assets/s_ncs_user_indicators_example_12.png)

**Mensen**: met betrekking tot kliks, kunnen wij zien dat het zelfde herkenningsteken (UUID) aan alle logboeken wordt toegewezen: **`9ab648f9 [...]`**. Deze id is nog niet meegeteld. Er wordt dus een nieuwe persoon aan het tellen toegevoegd.

![](assets/s_ncs_user_indicators_example_13.png)

**Tussentijdse berekening:**

|   | Ontvangers waarop is geklikt | Personen die hebben geklikt | Ontvangers die geopend zijn |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Onbekende persoon | - | +1 | - |
| Tussentotaal | 1 | 2 | 2 |

## Stap 4: Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** heeft zijn internetbrowser geconfigureerd om cookies af te wijzen. Hij opent de e-mail en klikt vier keer op de koppelingen.

![](assets/s_ncs_user_indicators_example_10.png)

De open en 4 klikken die door Henry worden uitgevoerd verschijnen in de volgende logboeken:

![](assets/s_ncs_user_indicators_example_5bis.png)

**Ontvangers**: open en kliks worden toegewezen aan de zelfde ontvanger (Henry). Aangezien deze ontvanger nog niet is meegeteld, voegt Adobe Campaign een ontvanger aan de telling toe.

**Mensen**: Aangezien Henry&#39;s browser geen cookies accepteert, wordt voor elke klik een nieuwe id (UUID) gegenereerd. Elk van de vier klikken wordt geïnterpreteerd als afkomstig van een andere persoon. Aangezien deze id&#39;s nog niet zijn geteld, worden ze aan de telling toegevoegd.

**Tussentijdse berekening:**

|   | Ontvangers waarop is geklikt | Personen die hebben geklikt | Ontvangers die geopend zijn |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Onbekende persoon | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Tussentotaal | 2 | 6 | 3 |

## Samenvatting {#summary}

Op het niveau van levering, hebben wij de volgende resultaten:

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (ontvangers die hebben geklikt): 2
* **[!UICONTROL Distinct clicks for the population reached]** (personen die hebben geklikt): 6
* **[!UICONTROL Distinct opens for the population reached]** (Ontvangers die de behandeling hebben geopend): 3

De ruwe reactiviteit en de raming van de forwards worden als volgt berekend:

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (dus 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A / C** (dus 2 / 3 = 66,67%)

>[!NOTE]
>
>In de volgende formules:
>
>* A staat voor de **[!UICONTROL Clicks]** indicator (ontvangers die klikten).
>* B staat voor de **[!UICONTROL Distinct clicks for the population reached]** indicator (mensen die klikte).
>* C staat voor de **[!UICONTROL Distinct opens for the population reached]** indicator (ontvangers die opende).
