---
product: campaign
title: Adobe Analytics-connector
description: Meer informatie over Adobe Analytics-connectorprovisioning
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Is alleen van toepassing op v7 on-premise en hybride implementaties"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Analytics-connector-provisioning {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Deze stappen mogen alleen worden uitgevoerd door Hybride en On-premise implementaties.
>
>Voor Gehoste en de implementaties van Managed Services van de Campagne, gelieve te contacteren ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team van de Zorg van de Klant van 0} Adobe.[

De integratie tussen Adobe Campaign Classic en Adobe Analytics-verificatie ondersteunt Adobe Identity Management Service (IMS):

* Als u een gemigreerde externe account beheert, moet u Adobe IMS implementeren en verbinding maken met Adobe Campaign via een Adobe ID.

  Gelieve te merken op dat de gebruiker die via Adobe ID IMS het programma wordt geopend de eigenaar van de **schakelaar van Gegevens** rekening in Adobe Analytics moet zijn en toestemmingen voor het **genoemde profiel van het Product** [ hieronder ](#analytics-product-profile) heeft.

Het probleem was dat de eigenaar van de gegevensconnector een andere gebruiker was dan de gebruiker die was aangemeld bij Campagne en die de integratie met Analytics probeerde uit te voeren.

* Als u een nieuwe aansluiting implementeert, is de implementatie van Adobe IMS optioneel. Zonder Adobe ID-gebruiker gebruikt Adobe Campaign een technische gebruiker voor synchronisatie met Adobe Analytics.

Deze integratie werkt alleen als u een Adobe Analytics-productprofiel maakt dat uitsluitend voor de Analytics-connector wordt gebruikt. Dan, zult u een de consoleproject van de Ontwikkelaar moeten creëren.

>[!AVAILABILITY]
>
> De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe, de integratie van de Campagne met de oplossingen van de Adobe en apps moet nu op server-aan-server referentie van OAuth vertrouwen. </br>
>
> * Als u binnenkomende integratie met Campagne hebt uitgevoerd, moet u uw Technische Rekening zoals die in [ wordt gedetailleerd deze documentatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank) migreren. De bestaande [ geloofsbrieven van de Rekening van de Dienst (JWT) ](oauth-technical-account.md) zullen tot 27 Januari, 2025 blijven werken.</br>
>
> * Als u uitgaande integratie hebt geïmplementeerd, zoals integratie met Campaign-Analytics of Experience Cloud Triggers, blijven ze tot 27 januari 2025 werken. Nochtans, vóór die datum, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan OAuth.

## Een Adobe Analytics-productprofiel maken {#analytics-product-profile}

Het Profiel van het product bepaalt het niveau van toegang een gebruiker op uw verschillende Componenten van Analytics heeft.

Als u al een productprofiel voor Analytics hebt, moet u nog steeds een nieuw Adobe Analytics-productprofiel maken dat uitsluitend wordt gebruikt voor de Analytics-connector. Zo zorgt u ervoor dat uw productprofiel is ingesteld met de juiste machtigingen voor deze integratie.

Voor meer informatie over de profielen van het Product, verwijs naar de [ documentatie van de Admin console ](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Van de [ console Admin ](https://adminconsole.adobe.com/), selecteer uw Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Klik op **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Voeg een **[!UICONTROL Product profile name]** toe en raden we u aan de volgende syntaxis te gebruiken: `reserved_campaign_classic_<Company Name>` . Klik vervolgens op **[!UICONTROL Next]** .

   Dit **[!UICONTROL Product profile]** zou exclusief voor de Schakelaar van Analytics moeten worden gebruikt om misconfiguratiefouten te verhinderen.

1. Open de nieuwe versie van **[!UICONTROL Product profile]** en selecteer de tab **[!UICONTROL Permissions]** .

   ![](assets/do-not-localize/triggers_3.png)

1. Configureer de verschillende mogelijkheden door op **[!UICONTROL Edit]** te klikken en de machtigingen die aan de **[!UICONTROL Product profile]** -functie moeten worden toegewezen te selecteren door op de plusknop (+) te klikken.

   Voor meer informatie over hoe te om toestemmingen te beheren, verwijs naar de [ documentatie van de Admin console ](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Voor de **[!UICONTROL Report Suites]** mogelijkheid voegt u **[!UICONTROL Report Suites]** toe die u later moet gebruiken.

   Als u geen rapportsuites hebt, kunt u het na [ tot stand brengen deze stappen ](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Voor de **[!UICONTROL Metrics]** mogelijkheid voegt u de **[!UICONTROL Metrics]** toe die u later moet configureren.

   Indien nodig, kunt u de auto-omvat optie inschakelen die elk toestemmingenpunt in de inbegrepen lijst zal toevoegen en automatisch nieuwe toestemmingspunten zal toevoegen.

   ![](assets/do-not-localize/triggers_13.png)

1. Voor de **[!UICONTROL Dimensions]** mogelijkheid voegt u de **[!UICONTROL Dimensions]** toe die nodig is voor toekomstige configuratie.

   Zorg ervoor dat de gekozen Dimensionen overeenkomen met de instellingen die in de externe account moeten worden geconfigureerd en lijn deze uit met het corresponderende eVars-nummer van Adobe Analytics.

1. Voeg voor de functie **[!UICONTROL Report Suite Tools]** de volgende machtigingen toe:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Voeg voor de functie **[!UICONTROL Analytics Tools]** de volgende machtigingen toe:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Uw productprofiel is nu geconfigureerd. Vervolgens moet u het OAuth-project maken.

## OAuth-project maken {#create-adobe-io}

Als u verder wilt gaan met het configureren van uw Adobe Analytics-connector, opent u de Adobe Developer-console en maakt u uw OAuth Server-to-Server-project.

Verwijs naar [ deze pagina ](oauth-technical-account.md#oauth-service) voor de gedetailleerde documentatie.

## Configuratie en gebruik {#adobe-analytics-connector-usage}

Leer hoe te met Adobe Campaign en Adobe Analytics in [ Adobe Campaign v8 documentatie ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa) {target="_blank"} te werken.