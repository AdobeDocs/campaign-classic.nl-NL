---
title: Adobe-IO configureren voor Adobe Experience Cloud-triggers
seo-title: Adobe-IO configureren voor Adobe Experience Cloud-triggers
description: Adobe-IO configureren voor Adobe Experience Cloud-triggers
seo-description: null
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
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Adobe-IO configureren voor Adobe Experience Cloud-triggers {#configuring-adobe-io}

Voorwaardelijke configuraties zijn:

* Adobe Campaign Classic build ACC-19.1.9 of ACC-20.2.1 en hoger.
* een geldige IMSOrgID.
* een ontwikkelaar toegang tot de IMS-organisatie. U moet de bevoegdheden van de systeembeheerder van IMS Org aanvragen om de procedure te volgen die in deze [pagina](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) wordt beschreven om deze toegang te bieden aan alle productprofielen.

## Stap 1: Adobe-IO-project maken/bijwerken {#creating-adobe-io-project}

1. Open Adobe IO en meld u aan met de System Administrator-rechten voor IMSorg.

   >[!NOTE]
   >
   > Controleer of u bent aangemeld bij de juiste IMSorg-portal.

1. Extraheer de bestaande ID van de integratieclient uit het dossier van de instantieconfiguratie ims/authIMSTAClientId. Niet bestaand of leeg attribuut wijst op cliëntIdentiteitskaart niet wordt gevormd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u deze rechtstreeks **[!UICONTROL Create a New project]** in Adobe IO gebruiken.

1. U moet nu het bestaande project identificeren gebruikend gehaalde cliëntidentiteitskaart Zoek bestaande projecten met dezelfde client-id als de projecten die u in de vorige stap hebt uitgepakt.

   ![](assets/adobe_io_8.png)

1. Selecteer **[!UICONTROL + Add to Project]** en kies **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. Selecteer in het venster **[!UICONTROL Add an API]** de optie **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype.

   ![](assets/adobe_io_3.png)

1. Als u identiteitskaart van de Cliënt leeg bent, selecteer **[!UICONTROL Generate a key pair]** om openbaar en Privé keypair tot stand te brengen.

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

Om de projectgeloofsbrieven in Adobe Campaign toe te voegen, stel het volgende bevel als neolane gebruiker op alle containers van de instantie van Adobe Campaign in werking om de **[!UICONTROL Technical Account]** geloofsbrieven in het dossier van de instantieconfiguratie op te nemen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Codeer de persoonlijke sleutel in base64 UTF-8-indeling. Vergeet niet de nieuwe regel uit de sleutel te verwijderen voordat u deze codeert, behalve voor de persoonlijke sleutel. De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

## Stap 3: Label voor pijplijnen bijwerken {#update-pipelined-tag}

Om [!DNL pipelined] markering bij te werken, moet u het authentificatietype aan Adobe IO project in het configuratiedossier **config-&lt; instance-name >.xml** als volgt bijwerken:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Als u de oudere versie van de Integratie van Triggers gebruikend de Verouderde tokens van JWT gebruikt, zou u ook Adobe IO API voor [!DNL Adobe Analytics] gedetailleerde in de eerste stap moeten toevoegen om automatisch aan de nieuwe Authentificatie van Triggers te migreren.
