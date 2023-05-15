---
product: campaign
title: Berichtensjablonen publiceren
description: Meer informatie over de publicatie en publicatie van een berichtsjabloon in Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Berichtensjablonen publiceren {#publishing-template-messages}



## Sjabloonpublicatie {#template-publication}

Wanneer de [berichtsjabloon](../../message-center/using/creating-the-message-template.md) gecreeerd op de controleinstantie is volledig en zodra u hebt [getest](../../message-center/using/testing-message-templates.md) u kunt deze publiceren. Dit proces zal het op alle uitvoeringsinstanties ook publiceren.

Met Publicatie kunt u automatisch **twee berichtsjablonen** over de uitvoeringsinstanties, waarmee u berichten kunt verzenden die zijn gekoppeld aan **realtime gebeurtenissen** en **batch-gebeurtenissen**.

>[!NOTE]
>
>Wanneer het publiceren van transactiemalplaatjes van het berichtbericht, worden de typologische regels ook automatisch gepubliceerd op de uitvoeringsinstanties.

>[!IMPORTANT]
>
>Wanneer u om het even welke veranderingen in een malplaatje aanbrengt, zorg ervoor u het voor deze veranderingen opnieuw publiceert om tijdens de levering van het transactiemelding van berichten effectief te zijn.

1. Ga in de besturingsinstantie naar de knop **[!UICONTROL Message Center > Transactional message templates]** map van de structuur.
1. Selecteer de sjabloon die u op de uitvoeringsinstanties wilt publiceren.
1. Klik op **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Wanneer de publicatie is voltooid, worden zowel berichtsjablonen die moeten worden toegepast op batchgebeurtenissen als realtime-typegebeurtenissen gemaakt in de structuur van de productieinstantie in het dialoogvenster **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** map.

![](assets/messagecenter_deployed_model_001.png)

Zodra een malplaatje wordt gepubliceerd, als de overeenkomstige gebeurtenis wordt teweeggebracht, zal de uitvoeringsinstantie de gebeurtenis ontvangen, zal het verbinden met het transactiesjabloon en het overeenkomstige transactiemelding naar elke ontvanger verzenden. Zie voor meer informatie [Gebeurtenisverwerking](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Als u een bestaand veld van de transactiemplate voor berichten, zoals het adres van de afzender, vervangt door een lege waarde, wordt het corresponderende veld op de uitvoeringsinstantie(s) niet bijgewerkt wanneer het transactiemelding opnieuw wordt gepubliceerd. De vorige waarde blijft in de selectie staan.
>
>Als u echter een niet-lege waarde toevoegt, wordt het desbetreffende veld op de gebruikelijke wijze na de volgende publicatie bijgewerkt.

## Publicatie van sjabloon ongedaan maken {#template-unpublication}

Zodra een berichtmalplaatje op de uitvoeringsinstanties wordt gepubliceerd, kan het unpublished. Voor meer informatie over het publicatieproces van een sjabloon raadpleegt u [deze sectie](#template-publication).

* Een gepubliceerde sjabloon kan zelfs nog steeds worden opgeroepen als de overeenkomstige gebeurtenis wordt geactiveerd: Als u geen berichtmalplaatje meer gebruikt, wordt het geadviseerd om het unpublish. Dit om te voorkomen dat er per ongeluk een ongewenste transactiemelding wordt verzonden.

   U hebt bijvoorbeeld een berichtsjabloon gepubliceerd die u alleen gebruikt voor kerstcampagnes. Misschien wilt u de publicatie ongedaan maken nadat de kerstperiode is afgelopen en deze volgend jaar opnieuw publiceren.

* U kunt ook geen transactiemalplaatje verwijderen dat de **[!UICONTROL Published]** status. U moet eerst de publicatie ongedaan maken.

>[!NOTE]
>
>Deze mogelijkheid is beschikbaar vanaf de release van Campagne 20.2.

Volg onderstaande stappen om de publicatie van een transactiemalplaatje ongedaan te maken.

1. Ga in de besturingsinstantie naar de knop **[!UICONTROL Message Center > Transactional message templates]** map van de structuur.
1. Selecteer de sjabloon die u wilt verwijderen.
1. Klik op **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klik op **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

De status van de transactiemalplaatje verandert terug van **[!UICONTROL Published]** tot **[!UICONTROL Being edited]**.

Zodra de publicatie is voltooid:

* Beide berichtmalplaatjes (die op partij en real-time typegebeurtenissen worden toegepast) worden geschrapt van elke uitvoeringsinstantie.

   Ze verschijnen niet meer in het dialoogvenster **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** map (zie [deze sectie](#template-publication)).

* Zodra een malplaatje unpublished is, kunt u het van de controleinstantie schrappen.

   Selecteer dit in de lijst en klik op de knop **[!UICONTROL Delete]** op de rechterbovenhoek van het scherm.
