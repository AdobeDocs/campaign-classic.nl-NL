---
product: campaign
title: Controleregels
description: Controleregels
feature: Typology Rules
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---

# Controleregels{#control-rules}

![](../../assets/common.svg)

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
* **[!UICONTROL Unsubscription link approval]** (e-mail): controleert of er ten minste één niet-abonnements-URL (opt-out) in elke inhoud (HTML en Tekst) aanwezig is.

## Een besturingsregel maken {#creating-a-control-rule}

Het is mogelijk om nieuwe controleregels tot stand te brengen om uw behoeften aan te passen. Hiertoe maakt u een **[!UICONTROL Control]** typologieregel en voer de besturingsformule in SQL in de **[!UICONTROL Code]** tab.

**Voorbeeld:**

In het volgende voorbeeld, gaan wij een regel tot stand brengen om een aanbieding van SMS te verhinderen worden verzonden naar meer dan 100 ontvangers. Deze regel zal worden gekoppeld aan een campagnetypologie en vervolgens aan de sms-leveringen waarvoor het betrokken aanbod beschikbaar is.

Voer de volgende stappen uit:

1. Een **[!UICONTROL Control]** typologieregel. Selecteer een **[!UICONTROL Warning]** alarmniveau.

   ![](assets/campaign_opt_create_control_01.png)

1. In de **[!UICONTROL Code]** voert u het script in om de gewenste drempelwaarde toe te passen, zoals hieronder wordt weergegeven:

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

   Aan het einde van de analyse **[!UICONTROL Confirm delivery]** is niet beschikbaar.

   ![](assets/campaign_opt_create_control_06.png)
