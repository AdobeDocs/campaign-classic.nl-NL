---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Connector
description: Meer informatie over Adobe Analytics Connector levering
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 24cd84d37c48613aa035769514a43b6dd7aa3869
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 5%

---

# Adobe Analytics Connector-provisioning {#adobe-analytics-connector-provisioning}

![](../../assets/common.svg)

>[!IMPORTANT]
>
> Deze stappen mogen alleen worden uitgevoerd door Hybride en On-Premise implementaties.
>
>Neem voor gehoste implementaties contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)-team.

De integratie tussen Adobe Campaign Classic en Adobe Analytics-verificatie ondersteunt Adobe Identity Management Service (IMS). U moet Adobe IMS implementeren en verbinding maken met Campagne [via een Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en), voordat u de implementatie van de Analytics Connector start.

Deze integratie werkt alleen als u een Adobe Analytics-productprofiel maakt dat uitsluitend voor de Analytics-connector wordt gebruikt. Vervolgens moet u een Adobe I/O-project maken.

## Een Adobe Analytics-productprofiel maken {#analytics-product-profile}

Het Profiel van het product bepaalt het niveau van toegang een gebruiker op uw verschillende Componenten van Analytics heeft.

Als u al een productprofiel voor Analytics hebt, moet u nog steeds een nieuw Adobe Analytics-productprofiel maken dat uitsluitend wordt gebruikt voor de Analytics-connector. Zo zorgt u ervoor dat uw productprofiel is ingesteld met de juiste machtigingen voor deze integratie.

Raadpleeg de documentatie [Admin-console](https://helpx.adobe.com/mt/enterprise/admin-guide.html) voor meer informatie over productprofielen.

1. Selecteer uw Adobe Analytics **[!UICONTROL Product]** in de [Admin-console](https://adminconsole.adobe.com/).

   ![](assets/do-not-localize/triggers_1.png)

1. Klik op **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Voeg een **[!UICONTROL Product profile name]** toe, adviseren wij gebruikend de volgende syntaxis: `reserved_campaign_classic_<Company Name>`. Klik vervolgens op **[!UICONTROL Next]**.

   Dit **[!UICONTROL Product profile]** zou exclusief voor de Schakelaar van Analytics moeten worden gebruikt om misconfiguratiefouten te verhinderen.

1. Open uw nieuwe **[!UICONTROL Product profile]** en selecteer **[!UICONTROL Permissions]** tabel.

   ![](assets/do-not-localize/triggers_3.png)

1. Configureer de verschillende mogelijkheden door op **[!UICONTROL Edit]** te klikken en de machtigingen voor het toewijzen aan uw **[!UICONTROL Product profile]** te selecteren door op het plusteken (+) te klikken.

   Raadpleeg de documentatie [Admin-console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html) voor meer informatie over het beheren van machtigingen.

1. Voor de **[!UICONTROL Report Suites]** capaciteit, voeg **[!UICONTROL Report Suites]** toe u moet later gebruiken.

   Als u geen rapportsuites hebt, kunt u het na [deze stappen ](../../platform/using/adobe-analytics-connector.md#report-suite-analytics) tot stand brengen.

   ![](assets/do-not-localize/triggers_4.png)

1. Voor het **[!UICONTROL Metrics]** vermogen, voeg **[!UICONTROL Metrics]** toe u later zult moeten vormen.

   Indien nodig, kunt u de auto-omvat optie inschakelen die elk toestemmingenpunt in de inbegrepen lijst zal toevoegen en automatisch nieuwe toestemmingspunten zal toevoegen.

   ![](assets/do-not-localize/triggers_13.png)

1. Voor het **[!UICONTROL Dimensions]** vermogen, voeg **[!UICONTROL Dimensions]** toe u later zult moeten vormen.

1. Voeg de volgende machtigingen toe voor de **[!UICONTROL Report Suite Tools]**-mogelijkheid:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Voeg de volgende machtigingen toe voor de **[!UICONTROL Analytics Tools]**-mogelijkheid:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Uw productprofiel is nu geconfigureerd. Vervolgens moet u het Adobe I/O-project maken.

## Adobe I/O-project maken {#create-adobe-io}

1. Open Adobe I/O en meld u aan als **Systeembeheerder** van de IMS-organisatie.

   Voor meer informatie over Admin rollen, verwijs naar deze [pagina](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klik op **[!UICONTROL Create a new project]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Klik op **[!UICONTROL Add to Project]** en selecteer **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Selecteer [!DNL Adobe Analytics] en klik op **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype en klik op **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Selecteer de optie **[!UICONTROL Option 1: Generate a Key-Pair]** en klik **[!UICONTROL Generate a Key-Pair]**.

   Het bestand config.zip wordt dan automatisch gedownload.

   ![](assets/do-not-localize/triggers_9.png)

1. Klik op **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Selecteer **[!UICONTROL Product profile]** die in de vorige stappen worden gecreeerd die in dit [sectie](#analytics-product-profile) worden gedetailleerd.

1. Klik vervolgens op **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Selecteer [!DNL Adobe Analytics] in uw project en kopieer de volgende informatie onder **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. Plak deze serviceaccountgegevens op de server met de volgende opdracht:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

U kunt nu de Analytics-connector gebruiken en uw klantgedrag volgen.
