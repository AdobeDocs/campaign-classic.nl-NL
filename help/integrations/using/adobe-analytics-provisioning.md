---
product: campaign
title: Adobe Analytics-connector
description: Meer informatie over Adobe Analytics-connectorprovisioning
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Is alleen van toepassing op v7 on-premise en hybride implementaties"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 1%

---

# Adobe Analytics-connector-provisioning {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Deze stappen mogen alleen worden uitgevoerd door Hybride en On-premise implementaties.
>
>Neem voor de gehoste en Campagne Managed Services-implementaties contact op met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team.

De integratie tussen Adobe Campaign Classic en Adobe Analytics-verificatie ondersteunt Adobe Identity Management Service (IMS):

* Als u een gemigreerde externe account beheert, moet u Adobe IMS implementeren en verbinding maken met Adobe Campaign via een Adobe ID.

  Houd er rekening mee dat de gebruiker die via Adobe ID IMS is aangemeld, eigenaar moet zijn van de **Gegevensconnector** -account in Adobe Analytics en beschikken over de juiste machtigingen voor de **Productprofiel** genoemd [onder](#analytics-product-profile).

Het probleem was dat de eigenaar van de gegevensconnector een andere gebruiker was dan de gebruiker die was aangemeld bij Campagne en die de integratie met Analytics probeerde uit te voeren.

* Als u een nieuwe aansluiting implementeert, is de implementatie van Adobe IMS optioneel. Zonder Adobe ID-gebruiker gebruikt Adobe Campaign een technische gebruiker voor synchronisatie met Adobe Analytics.

Deze integratie werkt alleen als u een Adobe Analytics-productprofiel maakt dat uitsluitend voor de Analytics-connector wordt gebruikt. Dan, zult u een de consoleproject van de Ontwikkelaar moeten creëren.

>[!AVAILABILITY]
>
> De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe, de integratie van de Campagne met de oplossingen van de Adobe en apps moet nu op server-aan-server referentie van OAuth vertrouwen. </br>
>
> * Als u ingebouwde integratie met Campagne hebt uitgevoerd, moet u uw Technische Rekening migreren zoals die in [deze documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). De bestaande geloofsbrieven van de Rekening van de Dienst (JWT) zullen tot 27 Januari, 2025 blijven werken.</br>
>
> * Als u uitgaande integratie hebt geïmplementeerd, zoals integratie met Campaign-Analytics of Experience Cloud Triggers, blijven ze tot 27 januari 2025 werken. Nochtans, vóór die datum, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan OAuth.

## Een Adobe Analytics-productprofiel maken {#analytics-product-profile}

Het Profiel van het product bepaalt het niveau van toegang een gebruiker op uw verschillende Componenten van Analytics heeft.

Als u al een productprofiel voor Analytics hebt, moet u nog steeds een nieuw Adobe Analytics-productprofiel maken dat uitsluitend wordt gebruikt voor de Analytics-connector. Zo zorgt u ervoor dat uw productprofiel is ingesteld met de juiste machtigingen voor deze integratie.

Raadpleeg voor meer informatie over productprofielen de [Documentatie voor beheerconsole](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Van de [Admin Console](https://adminconsole.adobe.com/), selecteer je Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Klik op **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Voeg een **[!UICONTROL Product profile name]** We raden u aan de volgende syntaxis te gebruiken: `reserved_campaign_classic_<Company Name>`. Klik vervolgens op **[!UICONTROL Next]**.

   Dit **[!UICONTROL Product profile]** uitsluitend gebruiken voor de Analytics Connector om fouten in de configuratie te voorkomen.

1. Open uw nieuw gemaakte **[!UICONTROL Product profile]** en selecteert u de **[!UICONTROL Permissions]** tab.

   ![](assets/do-not-localize/triggers_3.png)

1. De verschillende mogelijkheden configureren door te klikken **[!UICONTROL Edit]** en selecteer de machtigingen die aan uw **[!UICONTROL Product profile]** door op de plusknop (+) te klikken.

   Raadpleeg voor meer informatie over het beheren van machtigingen de [Documentatie voor beheerconsole](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Voor de **[!UICONTROL Report Suites]** mogelijkheden, voegt de **[!UICONTROL Report Suites]** moet u later gebruiken.

   Als u geen rapportsuites hebt, kunt u het volgende creëren [deze stappen](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Voor de **[!UICONTROL Metrics]** mogelijkheden, voegt de **[!UICONTROL Metrics]** u zult later moeten vormen.

   Indien nodig, kunt u de auto-omvat optie inschakelen die elk toestemmingenpunt in de inbegrepen lijst zal toevoegen en automatisch nieuwe toestemmingspunten zal toevoegen.

   ![](assets/do-not-localize/triggers_13.png)

1. Voor de **[!UICONTROL Dimensions]** mogelijkheden, voegt de **[!UICONTROL Dimensions]** nodig voor toekomstige configuratie.

   Zorg ervoor dat de gekozen Dimensionen overeenkomen met de instellingen die in de externe account moeten worden geconfigureerd en lijn deze uit met het corresponderende eVars-nummer van Adobe Analytics.

1. Voor de **[!UICONTROL Report Suite Tools]** kunt u de volgende machtigingen toevoegen:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Voor de **[!UICONTROL Analytics Tools]** kunt u de volgende machtigingen toevoegen:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Uw productprofiel is nu geconfigureerd. Vervolgens moet u het OAuth-project maken.

## OAuth-project maken {#create-adobe-io}

Als u verder wilt gaan met het configureren van uw Adobe Analytics-connector, opent u de Adobe Developer-console en maakt u uw OAuth Server-to-Server-project.

Zie [deze pagina](oauth-technical-account.md#oauth-service) voor de gedetailleerde documentatie.

## Configuratie en gebruik {#adobe-analytics-connector-usage}

Leer hoe u met Adobe Campaign en Adobe Analytics werkt in [Adobe Campaign v8-documentatie](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.