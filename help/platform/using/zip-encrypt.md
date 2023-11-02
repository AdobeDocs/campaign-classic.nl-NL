---
product: campaign
title: Een bestand zoeken of versleutelen
description: Leer hoe u een bestand kunt zippen of versleutelen in Campagne voordat u het verwerkt
feature: Data Management, Encryption
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 7%

---

# Een bestand comprimeren of versleutelen {#zipping-or-encrypting-a-file}



Met Adobe Campaign kunt u gecomprimeerde of gecodeerde bestanden exporteren. Wanneer u een exportbewerking definieert via een **[!UICONTROL Data extraction (file)]** kunt u een nabewerking definiëren om het bestand te zip of te coderen.

Om dit te kunnen doen:

1. Installeer een sleutelpaar GPG voor uw instantie gebruikend [Deelvenster Beheer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Het Configuratiescherm is beperkt tot Admin-gebruikers en is alleen beschikbaar voor bepaalde campagneversies. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html)
   >

1. Als uw installatie van Adobe Campaign wordt gehost op Adobe, neemt u contact op met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de benodigde hulpprogramma&#39;s op de server te installeren.
1. Als de installatie van Adobe Campaign op locatie plaatsvindt, installeert u het hulpprogramma dat u wilt gebruiken (bijvoorbeeld GPG, GZIP) en de benodigde sleutels (coderingssleutel) op de toepassingsserver.

U kunt dan bevelen of code in gebruiken **[!UICONTROL Script]** tabblad van de activiteit of in een **[!UICONTROL JavaScript code]** activiteit. In het onderstaande gebruiksgeval wordt een voorbeeld gegeven.

**Verwante onderwerpen:**

* [Een bestand uitpakken of ontsleutelen vóór verwerking](../../platform/using/unzip-decrypt.md)
* [Activiteit voor gegevensextractie (bestand)](../../workflow/using/extraction--file-.md).

## Hoofdlettergebruik: gegevens coderen en exporteren met een sleutel die is geïnstalleerd in het Configuratiescherm {#use-case-gpg-encrypt}

In dit geval, zullen wij een werkschema bouwen om gegevens te coderen en uit te voeren gebruikend een sleutel die op Controlebord wordt geïnstalleerd.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#video)

De volgende stappen voor dit gebruik zijn nodig:

1. Genereer een sleutelpaar van GPG (openbaar/privé) gebruikend een nut van GPG, dan installeer de openbare sleutel op Controlebord. Gedetailleerde stappen zijn beschikbaar in [Documentatie van het regelpaneel](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. In Campaign Classic, bouwt een werkschema om de gegevens uit te voeren en het te coderen gebruikend de privé sleutel die via het Controlebord is geïnstalleerd. Hiervoor maken we als volgt een workflow:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** activiteit: In dit voorbeeld, willen wij een vraag uitvoeren om de gegevens van het gegevensbestand te richten dat wij willen uitvoeren.
   * **[!UICONTROL Data extraction (file)]** activiteit: extraheert de gegevens naar een bestand.
   * **[!UICONTROL JavaScript code]** activiteit: versleutelt de gegevens die geëxtraheerd moeten worden.
   * **[!UICONTROL File transfer]** activiteit: verzendt de gegevens naar een externe bron (in dit voorbeeld, een server SFTP).

1. Vorm **[!UICONTROL Query]** activiteit om de gewenste gegevens van het gegevensbestand te richten. Raadpleeg [deze sectie](../../workflow/using/query.md) voor meer informatie.

1. Open de **[!UICONTROL Data extraction (file)]** activiteit vormt dan het op uw behoeften. Globale concepten over hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Open de **[!UICONTROL JavaScript code]** activiteit, dan kopieer-kleef het bevel hieronder om de gegevens te coderen om uit te halen.

   >[!IMPORTANT]
   >
   >Zorg ervoor dat u de **vingerafdruk** waarde van het bevel met de vingerafdruk van de openbare sleutel die op het Controlebord wordt geïnstalleerd.

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

1. Open de **[!UICONTROL File transfer]** en geeft u vervolgens de SFTP-server op waarnaar u het bestand wilt verzenden. Globale concepten over hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. U kunt de workflow nu uitvoeren. Zodra het wordt uitgevoerd, zal het gegevensdoel door de vraag naar de server SFTP in een gecodeerd.gpg- dossier worden uitgevoerd.

## Video over zelfstudie {#video}

In deze video wordt getoond hoe u een GPG-sleutel kunt gebruiken om gegevens te coderen. Deze video is ook beschikbaar in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Er zijn aanvullende Campaign Classic-to-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
