---
title: Controlevoorschriften
seo-title: Controlevoorschriften
description: Controlevoorschriften
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Controlevoorschriften{#control-rules}

## Regels inzake analyse en arbitrage {#analysis-and-arbitration-control-rules}

Met de controleregels kunt u de geldigheid en kwaliteit van berichten vóór levering garanderen: tekenweergave, SMS-grootte, adresnotatie, enz.

Met een set regels voor verduistering kunt u gebruikelijke controles uitvoeren. Deze controles (die in vette letters in de interface worden getoond) zijn:

* **[!UICONTROL Object approval]** (e-mail): controleert dat het afzendervoorwerp en het adres geen speciale karakters bevatten die problemen op bepaalde postagenten kunnen veroorzaken.
* **[!UICONTROL URL label approval]** (e-mail): controleert of elke URL die het bijhouden van een URL uitvoert, een label heeft.
* **[!UICONTROL URL approval]** (e-mail): Hiermee controleert u de URL&#39;s die worden gevolgd (aanwezigheid van het teken &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (mobiel): controleert de grootte van SMS-berichten.
* **[!UICONTROL Validity period check]** (e-mail): controleert of de geldigheidsperiode van de levering lang genoeg is om alle berichten te verzenden.
* **[!UICONTROL Proof size check]** (alle kanalen): genereert een foutbericht als de proefdoelpopulatie groter is dan 100 ontvangers.
* **[!UICONTROL Wave scheduling check]** (e-mail): controleert of de laatste leveringsgolf volgens de planning vóór het einde van de geldigheidsperiode zal beginnen, als de levering in verschillende golven is opgesplitst.
* **[!UICONTROL Unsubscription link approval]** (e-mail): controleert op de aanwezigheid van ten minste één niet-abonnements-URL (opt-out) in elke inhoud (HTML en Tekst).

## Een besturingsregel maken {#creating-a-control-rule}

Het is mogelijk om nieuwe controleregels tot stand te brengen om uw behoeften aan te passen. Om dit te doen, creeer een **[!UICONTROL Control]** typologieregel en ga de controleformule in SQL op het **[!UICONTROL Code]** lusje in.

**Voorbeeld:**

In het volgende voorbeeld, gaan wij een regel tot stand brengen om een aanbieding van SMS te verhinderen worden verzonden naar meer dan 100 ontvangers. Deze regel zal worden gekoppeld aan een campagnetypologie en vervolgens aan de sms-leveringen waarvoor het betrokken aanbod beschikbaar is.

Voer de volgende stappen uit:

1. Maak een **[!UICONTROL Control]** typologieregel. Selecteer een **[!UICONTROL Warning]** waarschuwingsniveau.

   ![](assets/campaign_opt_create_control_01.png)

1. Voer op het **[!UICONTROL Code]** tabblad het script in om de gewenste drempelwaarde toe te passen, zoals hieronder wordt weergegeven:

   ![](assets/campaign_opt_create_control_02.png)

   Dit manuscript zal een waarschuwing teweegbrengen als het leveringsdoel 100 contacten overschrijdt:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Koppel deze regel aan een campagnetypologie en verwijs de typologie in de betrokken levering van SMS.

   ![](assets/campaign_opt_create_control_03.png)

1. Tijdens leveringsanalyse, wordt de regel toegepast en een waarschuwing gecreeerd indien toepasselijk.

   ![](assets/campaign_opt_create_control_04.png)

   De levering is echter nog steeds klaar voor verzending.

   Als u het waarschuwingsniveau verhoogt, wordt de levering niet gestart.

   ![](assets/campaign_opt_create_control_05.png)

   Aan het einde van de analyse is de **[!UICONTROL Confirm delivery]** knop niet beschikbaar.

   ![](assets/campaign_opt_create_control_06.png)

