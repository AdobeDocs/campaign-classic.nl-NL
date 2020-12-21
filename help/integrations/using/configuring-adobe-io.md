---
solution: Campaign Classic
product: campaign
title: Adobe I/O configureren voor Adobe Experience Cloud Triggers
description: Leer hoe u Adobe I/O for Adobe Experience Cloud Triggers configureert
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 4%

---


# Adobe I/O configureren voor Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Als u een oudere versie van de integratie van Triggers door Authentificatie Auth gebruikt, **moet u naar Adobe I/O bewegen zoals hieronder beschreven**. De oude Auth-verificatiemodus wordt op 30 april 2021 afgesloten. [Meer informatie](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Vereisten {#adobe-io-prerequisites}

Deze integratie geldt alleen voor de eerste **Campaign Classic 20.3- en Gold Standard 11-releases**.

Controleer voordat u met deze implementatie begint of:

* een geldige IMSOrgID: de identificatiecode van de Identity Management System (IMS)-organisatie is de unieke identificatie binnen de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de VisitorID-service en de IMS Single-Sign On (SSO);
* een ontwikkelaar toegang tot de IMS-organisatie.

>[!NOTE]
>
>Als u om de voorrechten van de Beheerder van het Systeem van IMS Org moet verzoeken, volg de procedure [op deze pagina](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) om deze toegang voor alle Profielen van het Product te verlenen.


## Stap 1: Adobe I/O-project {#creating-adobe-io-project} maken/bijwerken

1. Open Adobe I/O en meld u aan met de System Administrator-rechten voor IMSorg.

   >[!NOTE]
   >
   > Controleer of u bent aangemeld bij de juiste IMSorg-portal.

1. Extraheer de bestaande ID van de integratieclient uit het dossier van de instantieconfiguratie ims/authIMSTAClientId. Niet bestaand of leeg kenmerk geeft aan dat de client-id niet is geconfigureerd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u direct **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identificeer het bestaande project gebruikend gehaalde cliënt ID. Zoek bestaande projecten met dezelfde client-id als de projecten die u in de vorige stap hebt uitgepakt.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecteer **[!UICONTROL + Add to Project]** en kies **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Selecteer **[!UICONTROL Adobe Analytics]** in het venster **[!UICONTROL Add an API]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een openbaar en privé sleutelpaar te maken.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Upload uw openbare sleutel en klik **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Kies het productprofiel **Analytics-&lt; Org Name >** en klik **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Van uw project, selecteer **[!UICONTROL Service Account (JWT)]** en kopieer de volgende informatie:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Stap 2: Voeg de projectgeloofsbrieven in Adobe Campaign {#add-credentials-campaign} toe

Om de projectgeloofsbrieven in Adobe Campaign toe te voegen, stel het volgende bevel als &quot;neolane&quot;gebruiker op alle containers van de instantie van Adobe Campaign in werking om **[!UICONTROL Technical Account]** geloofsbrieven in het dossier van de instantieconfiguratie op te nemen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Codeer de persoonlijke sleutel in base64 UTF-8-indeling. Vergeet niet de nieuwe regel uit de sleutel te verwijderen voordat u deze codeert, behalve voor de persoonlijke sleutel. De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

## Stap 3: Door buizen uitgelijnde tag {#update-pipelined-tag} bijwerken

Als u de tag [!DNL pipelined] wilt bijwerken, moet u het verificatietype bijwerken naar het Adobe I/O-project in het configuratiebestand **config-&lt; instance-name >.xml** als volgt:

```
<pipelined ... authType="imsJwtToken"  ... />
```
