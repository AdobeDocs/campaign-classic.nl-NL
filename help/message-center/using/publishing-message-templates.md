---
product: campaign
title: Berichtensjablonen publiceren
description: Meer informatie over de publicatie en publicatie van een berichtsjabloon in Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Berichtensjablonen publiceren {#publishing-template-messages}



## Sjabloonpublicatie {#template-publication}

Wanneer het [ berichtmalplaatje ](../../message-center/using/creating-the-message-template.md) op de controleinstantie wordt gecreeerd volledig is en zodra u [ ](../../message-center/using/testing-message-templates.md) het hebt getest, kunt u het publiceren. Dit proces zal het op alle uitvoeringsinstanties ook publiceren.

De publicatie laat u automatisch **twee berichtmalplaatjes** op de uitvoeringsinstanties creëren, die u zullen toestaan om berichten te verzenden verbonden aan **gebeurtenissen in real time** en **partijgebeurtenissen**.

>[!NOTE]
>
>Wanneer het publiceren van transactiemalplaatjes van het berichtbericht, worden de typologische regels ook automatisch gepubliceerd op de uitvoeringsinstanties.

>[!IMPORTANT]
>
>Wanneer u om het even welke veranderingen in een malplaatje aanbrengt, zorg ervoor u het voor deze veranderingen opnieuw publiceert om tijdens de levering van het transactiemelding van berichten effectief te zijn.

1. Ga in de besturingsinstantie naar de map **[!UICONTROL Message Center > Transactional message templates]** van de boomstructuur.
1. Selecteer de sjabloon die u op de uitvoeringsinstanties wilt publiceren.
1. Klik op **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Wanneer de publicatie is voltooid, worden zowel berichtsjablonen die moeten worden toegepast op batchgebeurtenissen als realtime-typegebeurtenissen gemaakt in de structuur van de productieinstantie in de map **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** .

![](assets/messagecenter_deployed_model_001.png)

Zodra een malplaatje wordt gepubliceerd, als de overeenkomstige gebeurtenis wordt teweeggebracht, zal de uitvoeringsinstantie de gebeurtenis ontvangen, zal het verbinden met het transactiesjabloon en het overeenkomstige transactiemelding naar elke ontvanger verzenden. Voor meer op dit, zie [ verwerking van de Gebeurtenis ](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Als u een bestaand veld van de transactiemplate voor berichten, zoals het adres van de afzender, vervangt door een lege waarde, wordt het corresponderende veld op de uitvoeringsinstantie(s) niet bijgewerkt wanneer het transactiemelding opnieuw wordt gepubliceerd. De vorige waarde blijft in de selectie staan.
>
>Als u echter een niet-lege waarde toevoegt, wordt het desbetreffende veld op de gebruikelijke wijze na de volgende publicatie bijgewerkt.

## Publicatie van sjabloon ongedaan maken {#template-unpublication}

Zodra een berichtmalplaatje op de uitvoeringsinstanties wordt gepubliceerd, kan het unpublished. Voor meer op het proces van de malplaatjepublicatie, zie [ deze sectie ](#template-publication).

* Een gepubliceerde sjabloon kan zelfs nog steeds worden aangeroepen als de bijbehorende gebeurtenis wordt geactiveerd: als u geen berichtsjabloon meer gebruikt, wordt aangeraden de publicatie ongedaan te maken. Dit om te voorkomen dat er per ongeluk een ongewenste transactiemelding wordt verzonden.

  U hebt bijvoorbeeld een berichtsjabloon gepubliceerd die u alleen gebruikt voor kerstcampagnes. Misschien wilt u de publicatie ongedaan maken nadat de kerstperiode is afgelopen en deze volgend jaar opnieuw publiceren.

* U kunt ook geen transactiemalplaatje verwijderen dat de **[!UICONTROL Published]** status heeft. U moet eerst de publicatie ongedaan maken.

>[!NOTE]
>
>Deze mogelijkheid is beschikbaar vanaf de release van Campagne 20.2.

Volg onderstaande stappen om de publicatie van een transactiemalplaatje ongedaan te maken.

1. Ga in de besturingsinstantie naar de map **[!UICONTROL Message Center > Transactional message templates]** van de boomstructuur.
1. Selecteer de sjabloon die u wilt verwijderen.
1. Klik op **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klik op **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

De status van de transactiemeldsjabloon verandert weer van **[!UICONTROL Published]** in **[!UICONTROL Being edited]** .

Zodra de publicatie is voltooid:

* Beide berichtmalplaatjes (die op partij en real-time typegebeurtenissen worden toegepast) worden geschrapt van elke uitvoeringsinstantie.

  Zij verschijnen niet meer in de **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** omslag (zie [ deze sectie ](#template-publication)).

* Zodra een malplaatje unpublished is, kunt u het van de controleinstantie schrappen.

  U doet dit door het in de lijst te selecteren en op de knop **[!UICONTROL Delete]** rechtsboven in het scherm te klikken.
