---
product: campaign
title: Adobe I/O configureren voor Adobe Experience Cloud Triggers
description: Leer hoe u Adobe I/O voor Adobe Experience Cloud Triggers configureert
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 24030d15ec57fd10fa5c2606e6f8544a8c15f179
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 4%

---

# Adobe I/O configureren voor Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Als u een oudere versie van de integratie van Trekkers door authentificatie Auth gebruikt, **moet u naar Adobe I/O bewegen zoals hieronder beschreven**. De de authentificatiemodus van de Oudere Auth met Campagne met Campagne zal op 30 november 2021 worden gepensioneerd. [Meer informatie](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Tijdens deze overgang naar [!DNL Adobe I/O] kunnen sommige inkomende triggers verloren gaan.

## Vereisten {#adobe-io-prerequisites}

Deze integratie is alleen van toepassing vanaf **Campaign Classic 20.3, 20.2.4, 19.1.8 en [!DNL Gold Standard] 11 releases**.

Controleer voordat u met deze implementatie begint of:

* een geldige **Organisatie-id**: de identificatiecode van de Identity Management System (IMS)-organisatie is de unieke identificatie binnen de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de VisitorID-service en de IMS Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Toegang voor ontwikkelaars** tot uw organisatie. De systeembeheerder van IMS Org moet **ontwikkelaars aan één enkel productprofiel toevoegen** volgen
procedure [op deze pagina](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) wordt beschreven om ontwikkelaars toegang te verlenen tot het `Analytics - {tenantID}` Profiel van het Product van Adobe Analytics verbonden aan Trekkers.

## Stap 1: Adobe I/O-project maken/bijwerken {#creating-adobe-io-project}

1. Open [!DNL Adobe I/O] en meld u aan met de ontwikkelaarstoegang van de IMS-organisatie.

   >[!NOTE]
   >
   > Zorg ervoor u in het correcte portaal van de Organisatie wordt geregistreerd.

1. Extraheer de bestaande id van de integratieclient (Cliënt ID) van het dossier van de instantieconfiguratie ims/authIMSTAClientId. Niet-bestaand of leeg kenmerk geeft aan dat de id van de client niet is geconfigureerd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u direct **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identificeer het bestaande project gebruikend het gehaalde cliëntherkenningsteken. Zoek naar bestaande projecten met het zelfde herkenningsteken van de Cliënt zoals die in vorige stap wordt gehaald.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecteer **[!UICONTROL + Add to Project]** en kies **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Selecteer **[!UICONTROL Adobe Analytics]** in het venster **[!UICONTROL Add an API]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als verificatietype.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een combinatie van openbare en persoonlijke sleutels te maken.

   De sleutels zullen dan automatisch met een standaardvervaldatum van 365 dagen worden gedownload. Zodra verlopen, zult u een nieuw zeer belangrijk paar moeten creëren en de integratie in het configuratiedossier bijwerken. Met Optie 2 kunt u ervoor kiezen om uw **[!UICONTROL Public key]** handmatig te maken en te uploaden met een langere vervaldatum.

   >[!CAUTION]
   >
   >Sla het bestand config.zip op wanneer de downloadprompt verschijnt, omdat u deze niet opnieuw kunt downloaden.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Klik op **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Kies een bestaande **[!UICONTROL Product profile]** of maak indien nodig een nieuwe . Voor deze **[!UICONTROL Product profile]** is geen toestemming vereist. Raadpleeg [Adobe Analytics-documentatie](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console) voor meer informatie over [!DNL Analytics] **[!UICONTROL Product Profiles]**.

   Klik vervolgens op **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Selecteer **[!UICONTROL Adobe Analytics]** in uw project en kopieer de volgende informatie onder **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O certificaat verloopt na twaalf maanden. Je moet elk jaar een nieuw sleutelpaar genereren.

## Stap 2: De referenties van het project toevoegen in Adobe Campaign {#add-credentials-campaign}

>[!NOTE]
>
>Deze stap is niet vereist als uw client-id niet leeg was in [Stap 1: Adobe I/O-project maken/bijwerken](#creating-adobe-io-project).

De persoonlijke sleutel moet in base64 UTF-8-indeling worden gecodeerd. Dit doet u als volgt:

1. Gebruik de persoonlijke sleutel die in [Stap 1 wordt geproduceerd: Sectie Adobe I/O-project maken/bijwerken](#creating-adobe-io-project). De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

1. Codeer de persoonlijke sleutel met behulp van de volgende opdracht: `base64 ./private.key > private.key.base64`. Hierdoor wordt de base64-inhoud opgeslagen in een nieuw bestand `private.key.base64`.

   >[!NOTE]
   >
   >Soms kunnen extra regels automatisch worden toegevoegd wanneer u de persoonlijke sleutel kopieert/plakt. Vergeet niet deze te verwijderen voordat u uw persoonlijke sleutel gaat coderen.

1. Kopieer de inhoud uit het bestand `private.key.base64`.

1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd en voeg de projectgegevens in Adobe Campaign toe door de volgende opdracht als `neolane`-gebruiker uit te voeren. Hiermee worden de **[!UICONTROL Technical Account]**-referenties ingevoegd in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Stap 3: Label voor pijplijnen bijwerken {#update-pipelined-tag}

>[!NOTE]
>
>Deze stap is niet vereist als uw client-id niet leeg was in [Stap 1: Adobe I/O-project maken/bijwerken](#creating-adobe-io-project).

Als u [!DNL pipelined]-tag wilt bijwerken, moet u het verificatietype bijwerken naar een Adobe I/O-project in het configuratiebestand **config-&lt; instance-name >.xml** als volgt:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Voer vervolgens een `config -reload` en een nieuwe start van [!DNL pipelined] uit om de wijzigingen in overweging te nemen.
