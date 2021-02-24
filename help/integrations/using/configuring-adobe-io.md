---
solution: Campaign Classic
product: campaign
title: Adobe I/O configureren voor Adobe Experience Cloud Triggers
description: Leer hoe u Adobe I/O voor Adobe Experience Cloud Triggers configureert
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 333d2221d4f86fe18232473385653ed8409adf54
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 6%

---


# Adobe I/O configureren voor Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Als u een oudere versie van de integratie van Trekkers door authentificatie Auth gebruikt, **moet u naar Adobe I/O bewegen zoals hieronder beschreven**. De oude oAuth-verificatiemodus wordt op 30 april 2021 buiten gebruik gesteld. [Meer informatie](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Houd er rekening mee dat tijdens deze overgang naar Adobe I/O enkele inkomende triggers verloren kunnen gaan.

## Vereisten {#adobe-io-prerequisites}

Deze integratie is alleen van toepassing vanaf **Campaign Classic 20.3, 20.2.4, 19.1.8 en Gold Standard 11-releases**.

Controleer voordat u met deze implementatie begint of:

* een geldige **Organisatie-id**: de identificatiecode van de Identity Management System (IMS)-organisatie is de unieke identificatie binnen de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de VisitorID-service en de IMS Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Toegang voor ontwikkelaars** tot uw organisatie.  Als u om de voorrechten van de Beheerder van het Systeem van IMS Org moet verzoeken, volg de procedure [op deze pagina](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) om deze toegang voor alle Profielen van het Product te verlenen.

## Stap 1: Adobe I/O-project maken/bijwerken {#creating-adobe-io-project}

1. Open Adobe I/O en meld u aan met de System Administrator-rechten voor de IMS-organisatie.

   >[!NOTE]
   >
   > Zorg ervoor u in het correcte portaal van de Organisatie wordt geregistreerd.

1. Extraheer de bestaande id van de integratieclient (client-id) uit het Instance Configuration-bestand ims/authIMSTAClientId. Niet bestaand of leeg kenmerk geeft aan dat de client-id niet is geconfigureerd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u direct **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identificeer het bestaande project gebruikend het gehaalde cliëntherkenningsteken. Zoek naar bestaande projecten met het zelfde cliëntherkenningsteken zoals die in vorige stap wordt gehaald.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecteer **[!UICONTROL + Add to Project]** en kies **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Selecteer **[!UICONTROL Adobe Analytics]** in het venster **[!UICONTROL Add an API]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een combinatie van openbare en persoonlijke sleutels te maken.

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

>[!CAUTION]
>
>Adobe I/O certificaat verloopt na twaalf maanden. Je moet elk jaar een nieuw sleutelpaar genereren.

## Stap 2: Voeg de projectgeloofsbrieven in Adobe Campaign {#add-credentials-campaign} toe

Om de projectgeloofsbrieven in Adobe Campaign toe te voegen, stel het volgende bevel als &quot;neolane&quot;gebruiker op alle containers van de instantie van Adobe Campaign in werking om **[!UICONTROL Technical Account]** geloofsbrieven in het dossier van de instantieconfiguratie op te nemen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

De persoonlijke sleutel moet in base64 UTF-8-indeling worden gecodeerd. Dit doet u als volgt:

1. Gebruik de persoonlijke sleutel die in [Stap 1 wordt geproduceerd: Sectie Adobe I/O-project maken/bijwerken](#creating-adobe-io-project). De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

1. Met deze [website](https://www.base64encode.org/) kopieert u uw persoonlijke sleutel naar het corresponderende veld.

   >[!NOTE]
   >
   >Soms wordt automatisch een extra regel toegevoegd wanneer u de persoonlijke sleutel kopieert/plakt. Vergeet niet deze te verwijderen voordat u uw persoonlijke sleutel gaat coderen.

1. Klik op **[!UICONTROL Encode]**.

1. Gebruik de zojuist gegenereerde persoonlijke sleutel die is gecodeerd in de indeling base64 UTF-8 om de bovenstaande opdracht uit te voeren.

## Stap 3: Door buizen uitgelijnde tag {#update-pipelined-tag} bijwerken

Als u [!DNL pipelined]-tag wilt bijwerken, moet u het verificatietype bijwerken naar een Adobe I/O-project in het configuratiebestand **config-&lt; instance-name >.xml** als volgt:

```
<pipelined ... authType="imsJwtToken"  ... />
```
