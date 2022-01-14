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
source-git-commit: 966da123b30278817ca465ac5dfe1f733c4d6c5c
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 3%

---

# Adobe I/O configureren voor Adobe Experience Cloud Triggers {#configuring-adobe-io}

![](../../assets/v7-only.svg)

>[!CAUTION]
>
>Als u een oudere versie van de integratie van Triggers door authentificatie Auth gebruikt, **u moet naar Adobe I/O gaan zoals hieronder beschreven**.
>Let op: tijdens deze overgang naar [!DNL Adobe I/O]bepaalde inkomende triggers kunnen verloren gaan.
>
>De oude verificatiemodus Auth met Campagne is uitgeschakeld op **20 oktober 2021**. Gehoste omgevingen profiteren van een verlenging tot **25 mei 2022**. Als klant op locatie of hybride klant neemt u contact op met de klantenservice van Adobe om de ondersteuning uit te breiden tot **mei 2022**. U moet [Geef de appID van de OAuth-toepassing op](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) naar Adobe.

## Vereisten {#adobe-io-prerequisites}

Deze integratie geldt alleen voor het starten **Campaign Classic 20.2.4 en hoger, 19.1.8 en Gold Standard 11-releases**.

Controleer voordat u met deze implementatie begint of:

* geldig **Organisatie-id**: de identificatiecode van de Identity Management System (IMS)-organisatie is de unieke identificatie binnen de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de VisitorID-service en de IMS Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Toegang voor ontwikkelaars** aan uw organisatie. De systeembeheerder van de IMS-organisatie moet de **Ontwikkelaars toevoegen aan één productprofiel** procedure [op deze pagina](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) om ontwikkelaarstoegang voor `Analytics - {tenantID}` Productprofiel van het Adobe Analytics-product dat is gekoppeld aan Triggers.

## Stap 1: Adobe I/O-project maken/bijwerken {#creating-adobe-io-project}

1. Toegang [!DNL Adobe I/O] en meld u aan bij de Developer Access van de IMS-organisatie.

   >[!NOTE]
   >
   > Zorg ervoor u in het correcte portaal van de Organisatie wordt geregistreerd.

1. Extraheer de bestaande id van de integratieclient (Cliënt ID) van het dossier van de instantieconfiguratie ims/authIMSTAClientId. Niet-bestaand of leeg kenmerk geeft aan dat de id van de client niet is geconfigureerd.

   >[!NOTE]
   >
   >Als uw client-id leeg is, kunt u rechtstreeks **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identificeer het bestaande project gebruikend het gehaalde cliëntherkenningsteken. Zoek naar bestaande projecten met het zelfde herkenningsteken van de Cliënt zoals die in vorige stap wordt gehaald.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecteren **[!UICONTROL + Add to Project]** en kiest u **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. In de **[!UICONTROL Add an API]** venster, selecteert u **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Kies **[!UICONTROL Service Account (JWT)]** als het verificatietype.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een openbare en privé zeer belangrijke paar tot stand te brengen.

   De sleutels zullen dan automatisch met een standaardvervaldatum van 365 dagen worden gedownload. Zodra verlopen, zult u een nieuw zeer belangrijk paar moeten creëren en de integratie in het configuratiedossier bijwerken. Met de optie 2 kunt u handmatig uw **[!UICONTROL Public key]** met een langere vervaldatum.

   >[!CAUTION]
   >
   >Sla het bestand config.zip op wanneer de downloadprompt verschijnt, omdat u deze niet opnieuw kunt downloaden.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Klik op **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Bestaande kiezen **[!UICONTROL Product profile]** of maak indien nodig een nieuwe versie. Hiervoor is geen toestemming vereist **[!UICONTROL Product profile]**. Voor meer informatie over [!DNL Analytics] **[!UICONTROL Product Profiles]**, zie [Adobe Analytics-documentatie](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   Klik vervolgens op **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Van uw project, selecteer **[!UICONTROL Adobe Analytics]** en kopieert u de volgende informatie onder **[!UICONTROL Service Account (JWT)]**:

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

1. Gebruik de persoonlijke sleutel die is gegenereerd in het dialoogvenster [Stap 1: Sectie Adobe I/O-project maken/bijwerken](#creating-adobe-io-project). De persoonlijke sleutel moet dezelfde zijn als die waarmee de integratie is gemaakt.

1. Codeer de persoonlijke sleutel met behulp van de volgende opdracht: `base64 ./private.key > private.key.base64`. Hierdoor wordt de base64-inhoud opgeslagen in een nieuw bestand `private.key.base64`.

   >[!NOTE]
   >
   >Soms kunnen extra regels automatisch worden toegevoegd wanneer u de persoonlijke sleutel kopieert/plakt. Vergeet niet deze te verwijderen voordat u uw persoonlijke sleutel gaat coderen.

1. De inhoud van het bestand kopiëren `private.key.base64`.

1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd en voeg de projectgegevens toe in Adobe Campaign door de volgende opdracht uit te voeren als `neolane` gebruiker. Hiermee voegt u de **[!UICONTROL Technical Account]** referenties in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Stap 3: Label voor pijplijnen bijwerken {#update-pipelined-tag}

>[!NOTE]
>
>Deze stap is niet vereist als uw client-id niet leeg was in [Stap 1: Adobe I/O-project maken/bijwerken](#creating-adobe-io-project).

Bijwerken [!DNL pipelined] -tag, moet u het verificatietype bijwerken naar een Adobe I/O-project in het configuratiebestand **config-&lt; instance-name >.xml** als volgt:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Voer vervolgens een `config -reload` en het opnieuw opstarten van de [!DNL pipelined] voor de in aanmerking te nemen wijzigingen.
