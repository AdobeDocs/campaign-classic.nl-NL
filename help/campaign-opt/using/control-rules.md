---
product: campaign
title: Controleregels
description: Leer hoe u met besturingsregels werkt in Adobe Campaign
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Controleregels{#control-rules}

## Regels inzake analyse en arbitrage {#analysis-and-arbitration-control-rules}

Met besturingsregels kunt u de geldigheid en kwaliteit van berichten vóór levering garanderen: weergave van tekens, grootte van SMS, adresindeling, enzovoort.

Met een set regels voor verduistering kunt u gebruikelijke controles uitvoeren. Deze controles (die in vette letters in de interface worden getoond) zijn:

* **[!UICONTROL Object approval]** (e-mail): hiermee wordt gecontroleerd of het verzendingsobject en -adres geen speciale tekens bevatten die problemen kunnen veroorzaken bij bepaalde e-mailagents.
* **[!UICONTROL URL label approval]** (e-mail): hiermee wordt gecontroleerd of elke URL die de gegevens bijhoudt een label heeft.
* **[!UICONTROL URL approval]** (e-mail): hiermee controleert u de URL&#39;s die worden gevolgd (aanwezigheid van het teken &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (mobiel): hiermee wordt de grootte van SMS-berichten gecontroleerd.
* **[!UICONTROL Validity period check]** (e-mail): controleert of de geldigheidsperiode van de levering lang genoeg is om alle berichten te verzenden.
* **[!UICONTROL Proof size check]** (alle kanalen): genereert een foutbericht als de proefdoelpopulatie groter is dan 100 ontvangers.
* **[!UICONTROL Wave scheduling check]** (e-mail): hiermee wordt gecontroleerd of de laatste leveringsgolf moet beginnen vóór het einde van de geldigheidsperiode als de levering in verschillende golven is opgesplitst.
* **[!UICONTROL Unsubscription link approval]** (e-mail): controleert of er ten minste één niet-abonnements-URL (opt-out) aanwezig is in elke inhoud (HTML en Tekst).

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

1. Tijdens leveringsanalyse, wordt de regel toegepast en een waarschuwing gecreeerd indien van toepassing.

   ![](assets/campaign_opt_create_control_04.png)

   De levering is echter nog steeds klaar voor verzending.

   Als u het waarschuwingsniveau verhoogt, wordt de levering niet gestart.

   ![](assets/campaign_opt_create_control_05.png)

   Aan het einde van de analyse **[!UICONTROL Confirm delivery]** is niet beschikbaar.

   ![](assets/campaign_opt_create_control_06.png)
