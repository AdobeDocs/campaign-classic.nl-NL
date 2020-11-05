---
title: Adobe I/O configureren voor Adobe Experience Cloud-triggers
description: Leer hoe u Adobe I/O voor Adobe Experience Cloud-triggers configureert
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Adobe I/O configureren voor Adobe Experience Cloud-triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Als u een oudere versie van de integratie van Triggers door tokens JWT of authentificatie Auth gebruikt, moet **u naar Adobe I/O bewegen zoals hieronder** beschreven. JWT- en Auth-verificatiemodi zijn nu afgekeurd. [Meer informatie](https://github.com/AdobeDocs/analytics-1.4-apis)

## Vereisten {#adobe-io-prerequisites}

Controleer voordat u met deze implementatie begint of:

* een recente versie van Adobe Campaign: 19.1.8 of 20.2.1 gebouwen en hoger,
* een geldige IMSOrgID: de identificatiecode van de Identity Management System (IMS)-organisatie is de unieke identificatie binnen de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de VisitorID-service en de IMS Single-Sign On (SSO);
* een ontwikkelaar toegang tot de IMS-organisatie.

>[!NOTE]
>
>Als u de bevoegdheden van de systeembeheerder van de IMS-organisatie moet aanvragen, volgt u de procedure die [in deze pagina](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) wordt beschreven om deze toegang te bieden aan alle productprofielen.


## Stap 1: Adobe I/O-project maken/bijwerken {#creating-adobe-io-project}

1. Open Adobe I/O en meld u aan met de System Administrator-rechten voor IMSorg.

   >[!NOTE]
   >
   > Controleer of u bent aangemeld bij de juiste IMSorg-portal.

1. Extraheer de bestaande ID van de integratieclient uit het dossier van de instantieconfiguratie ims/authIMSTAClientId. Niet bestaand of leeg kenmerk geeft aan dat de client-id niet is geconfigureerd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u deze rechtstreeks **[!UICONTROL Create a New project]** in Adobe I/O gebruiken.

1. Identificeer het bestaande project gebruikend gehaalde cliënt ID. Zoek bestaande projecten met dezelfde client-id als de projecten die u in de vorige stap hebt uitgepakt.

   ![](assets/adobe_io_8.png)

1. Selecteer **[!UICONTROL + Add to Project]** en kies **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. In the **[!UICONTROL Add an API]** window, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype.

   ![](assets/adobe_io_3.png)

1. Als uw identiteitskaart van de Cliënt leeg was, selecteer **[!UICONTROL Generate a key pair]** om een Openbaar en Privé sleutelpaar tot stand te brengen.

   ![](assets/adobe_io_4.png)

1. Upload uw openbare sleutel en klik **[!UICONTROL Next]**.

   ![](assets/adobe_io_5.png)

1. Kies het productprofiel **Analytics-&lt; Org Name >** en klik **[!UICONTROL Save configured API]**.

   ![](assets/adobe_io_6.png)

1. Selecteer in uw project de volgende gegevens **[!UICONTROL Service Account (JWT)]** en kopieer deze:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## Stap 2: De referenties van het project toevoegen in Adobe Campaign {#add-credentials-campaign}

Om de projectgeloofsbrieven in Adobe Campaign toe te voegen, stel het volgende bevel als &quot;neolane&quot;gebruiker op alle containers van de instantie van Adobe Campaign in werking om de **[!UICONTROL Technical Account]** geloofsbrieven in het dossier van de instantieconfiguratie op te nemen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Codeer de persoonlijke sleutel in base64 UTF-8-indeling. Vergeet niet de nieuwe regel uit de sleutel te verwijderen voordat u deze codeert, behalve voor de persoonlijke sleutel. De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

## Stap 3: Label voor pijplijnen bijwerken {#update-pipelined-tag}

Om [!DNL pipelined] markering bij te werken, moet u het authentificatietype aan Adobe I/O project in het configuratiedossier **config-&lt; instance-name >.xml** als volgt bijwerken:

```
<pipelined ... authType="imsJwtToken"  ... />
```
