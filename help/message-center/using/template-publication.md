---
solution: Campaign Classic
product: campaign
title: Sjabloonpublicatie
description: Publicatie van een transactiemalplaatje
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---


# Sjabloonpublicatie{#template-publication}

Wanneer het berichtmalplaatje op de controleinstantie wordt gecreeerd volledig is, kunt u het publiceren. Dit proces zal het op alle uitvoeringsinstanties ook publiceren.

Met Publicatie kunt u automatisch twee berichtsjablonen maken op de uitvoeringsinstanties. Hiermee kunt u berichten verzenden die zijn gekoppeld aan realtime- en batchgebeurtenissen.

>[!NOTE]
>
>Wanneer het publiceren van transactiemalplaatjes van het berichtbericht, worden de typologische regels ook automatisch gepubliceerd op de uitvoeringsinstanties.

>[!IMPORTANT]
>
>Wanneer u om het even welke veranderingen in een malplaatje aanbrengt, zorg ervoor u het voor deze veranderingen opnieuw publiceert om tijdens de levering van het transactiemelding van berichten effectief te zijn.

1. Ga voor de besturingsinstantie naar de map **[!UICONTROL Message Center > Transactional message templates]** van de boomstructuur.
1. Selecteer de sjabloon die u op de uitvoeringsinstanties wilt publiceren.
1. Klik op **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Wanneer de publicatie is voltooid, worden zowel berichtsjablonen die moeten worden toegepast op batchgebeurtenissen als realtime-typegebeurtenissen gemaakt in de structuur van de productieinstantie in de map **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Zodra een malplaatje wordt gepubliceerd, als de overeenkomstige gebeurtenis wordt teweeggebracht, zal de uitvoeringsinstantie de gebeurtenis ontvangen, zal het verbinden met het transactiesjabloon en het overeenkomstige transactiemelding naar elke ontvanger verzenden.

>[!NOTE]
>
>Als u een bestaand veld van de transactiemplate voor berichten, zoals het adres van de afzender, vervangt door een lege waarde, wordt het corresponderende veld op de uitvoeringsinstantie(s) niet bijgewerkt wanneer het transactiemelding opnieuw wordt gepubliceerd. De vorige waarde blijft in de selectie staan.
>
>Als u echter een niet-lege waarde toevoegt, wordt het desbetreffende veld op de gebruikelijke wijze na de volgende publicatie bijgewerkt.
