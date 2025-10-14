---
product: campaign
title: Een bestand zoeken of versleutelen
description: Leer hoe u een bestand kunt zippen of versleutelen in Campagne voordat u het verwerkt
feature: Data Management, Encryption
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 3%

---

# Een bestand comprimeren of versleutelen {#zipping-or-encrypting-a-file}

Met Adobe Campaign kunt u gecomprimeerde of gecodeerde bestanden exporteren. Wanneer u een exportbewerking definieert aan de hand van een **[!UICONTROL Data extraction (file)]** -activiteit, kunt u een naverwerking definiëren naar ZIP of het bestand versleutelen.

Om dit te kunnen doen:

1. Installeer een zeer belangrijk paar GPG voor uw instantie gebruikend het [&#x200B; Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=nl-NL#encrypting-data).

   >[!NOTE]
   >
   >Het Configuratiescherm is beperkt tot Admin-gebruikers en is alleen beschikbaar voor bepaalde campagneversies. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=nl)
   >

1. Als uw installatie van Adobe Campaign door Adobe wordt ontvangen, contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de noodzakelijke nut te hebben die op de server worden geïnstalleerd.
1. Als de installatie van Adobe Campaign op locatie plaatsvindt, installeert u het hulpprogramma dat u wilt gebruiken (bijvoorbeeld GPG, GZIP) en de benodigde sleutels (coderingssleutel) op de toepassingsserver.

Vervolgens kunt u opdrachten of code gebruiken op het tabblad **[!UICONTROL Script]** van de activiteit of in een **[!UICONTROL JavaScript code]** -activiteit. In het onderstaande gebruiksgeval wordt een voorbeeld gegeven.

**Verwante onderwerpen:**

* [Een bestand uitpakken of ontsleutelen vóór verwerking](../../platform/using/unzip-decrypt.md)
* [&#x200B; de extractie van gegevens (dossier) activiteit &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=nl-NL){target="_blank"}

## Hoofdlettergebruik: gegevens coderen en exporteren met een sleutel die is geïnstalleerd in het Configuratiescherm {#use-case-gpg-encrypt}

In dit geval, zullen wij een werkschema bouwen om gegevens te coderen en uit te voeren gebruikend een sleutel die op Controlebord wordt geïnstalleerd.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#video)

De volgende stappen voor dit gebruik zijn nodig:

1. Genereer een sleutelpaar van GPG (openbaar/privé) gebruikend een nut van GPG, dan installeer de openbare sleutel op Controlebord. De gedetailleerde stappen zijn beschikbaar in [&#x200B; documentatie van het Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=nl-NL#encrypting-data).

1. In Campaign Classic maakt u een workflow om de gegevens te exporteren en te coderen met de persoonlijke sleutel die via het Configuratiescherm is geïnstalleerd. Hiervoor maken we als volgt een workflow:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** activity: In dit voorbeeld willen we een query uitvoeren om de gegevens van de database die we willen exporteren als doel in te stellen.
   * **[!UICONTROL Data extraction (file)]** activiteit: extraheert de gegevens naar een bestand.
   * **[!UICONTROL JavaScript code]** activity: codeert de gegevens die geëxtraheerd moeten worden.
   * **[!UICONTROL File transfer]** activity: verzendt de gegevens naar een externe bron (in dit voorbeeld een SFTP-server).

1. Configureer de **[!UICONTROL Query]** -activiteit om de gewenste gegevens uit de database als doel in te stellen. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=nl-NL){target="_blank"}.

1. Open de **[!UICONTROL Data extraction (file)]** -activiteit en configureer deze op basis van uw behoeften. De globale concepten op hoe te om de activiteit te vormen zijn beschikbaar in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=nl-NL){target="_blank"}.

   ![](assets/gpg-data-extraction.png)

1. Open de **[!UICONTROL JavaScript code]** -activiteit en kopieer en plak de onderstaande opdracht om de gegevens te coderen die u wilt extraheren.

   >[!IMPORTANT]
   >
   >Zorg ervoor u de **vingerafdruk** waarde van het bevel met de vingerafdruk van de openbare sleutel vervangt die op het Controlebord wordt geïnstalleerd.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Open de **[!UICONTROL File transfer]** -activiteit en geef vervolgens de SFTP-server op waarnaar u het bestand wilt verzenden. De globale concepten op hoe te om de activiteit te vormen zijn beschikbaar in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=nl-NL){target="_blank"}.

   ![](assets/gpg-file-transfer.png)

1. U kunt de workflow nu uitvoeren. Zodra het wordt uitgevoerd, zal het gegevensdoel door de vraag naar de server SFTP in een gecodeerd.gpg- dossier worden uitgevoerd.

## Video over zelfstudie {#video}

In deze video wordt getoond hoe u een GPG-sleutel kunt gebruiken om gegevens te coderen. Deze video is ook beschikbaar in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

De extra hoe te video&#39;s van Campaign Classic zijn beschikbaar [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
