---
solution: Campaign Classic
product: campaign
title: Workflowdata gebruiken
description: Leer hoe u workflowgegevens gebruikt
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 3%

---


# Workflowdata gebruiken{#how-to-use-workflow-data}

## De database {#updating-the-database} bijwerken

Alle verzamelde gegevens kunnen worden gebruikt om de database bij te werken, of in leveringen. U kunt bijvoorbeeld de personalisatiemogelijkheden voor berichtinhoud verrijken (het aantal contracten in het bericht opnemen, het gemiddelde winkelwagentje van het afgelopen jaar opgeven, enzovoort) of een gedetailleerde bevolkingsgerichtheid (verzend een bericht aan contractmedehouders, richt de 1.000 beste abonnees aan online diensten, enz.). Deze gegevens kunnen ook worden geëxporteerd of gearchiveerd in een lijst.

### Lijsten en directe updates {#lists-and-direct-updates}

De gegevens van de Adobe Campaign-databank en de bestaande lijsten kunnen worden bijgewerkt met behulp van twee specifieke activiteiten:

* Met de activiteit **[!UICONTROL List update]** kunt u werktabellen opslaan in een datalist.

   U kunt een bestaande lijst selecteren of maken. In dit geval worden de naam en mogelijk de recordmap berekend.

   ![](assets/s_user_create_list.png)

   Zie [Lijstupdate](../../workflow/using/list-update.md).

* De **[!UICONTROL Update data]** activiteit voert een massa update van de gebieden in het gegevensbestand uit.

   Raadpleeg [Gegevens bijwerken](../../workflow/using/update-data.md) voor meer informatie hierover.

### Abonnementsbeheer/-beheer {#subscription-unsubscription-management}

Raadpleeg [Abonnementsservices](../../workflow/using/subscription-services.md) voor informatie over het abonneren en het opzeggen van ontvangers voor een informatieservice via een workflow.

## Verzenden via een workflow {#sending-via-a-workflow}

### Leveringsactiviteit {#delivery-activity}

De leveringsactiviteit wordt gedetailleerd in [Levering](../../workflow/using/delivery.md).

### Verrijken en richten van leveringen {#enriching-and-targeting-deliveries}

Leveringen kunnen gegevens uit workflows verwerken om de inhoud aan te passen of binnen het kader van de selectie van doelgroepen.

Zo kunt u in het kader van een directe postbezorging de aanvullende gegevens, die zijn ontleend aan gegevensmanipulatie die in de workflow is uitgevoerd, opnemen in het extractiebestand:

![](assets/s_advuser_add_data_postal_mail.png)

Naast de gebruikelijke verpersoonlijkingsgebieden, kunt u verpersoonlijkingsgebieden van werkschemafasen aan de leveringsinhoud toevoegen. De extra gegevens die in de werkschemaactiviteiten worden bepaald kunnen in de leveringstovenaar, zoals aangetoond in het hieronder voorbeeld worden gehouden en worden toegankelijk gemaakt, voor het bepalen van de naam van het outputdossier binnen het kader van direct postlevering:

![](assets/s_advuser_using_additional_data.png)

De gegevens in de workflowtabel worden aangeduid met de naam: het wordt altijd samengesteld uit **targetData** verbinding. Raadpleeg [Doelgegevens](../../workflow/using/data-life-cycle.md#target-data) voor meer informatie hierover.

In het kader van de e-maillevering kunnen personaliseringsgebieden ook gegevens gebruiken van doeluitbreiding die in de het richten werkschemasfases wordt uitgevoerd, zoals aangetoond in het hieronder voorbeeld:

![](assets/s_advuser_add_data_email.png)

Als een segmentcode in een het richten activiteit wordt gespecificeerd, wordt het toegevoegd aan een specifieke kolom van de werkschemalijst en zal samen met de verpersoonlijkingsgebieden worden aangeboden. Als u alle aanpassingsvelden wilt weergeven, klikt u op de koppeling **[!UICONTROL Target extension > Other...]** die toegankelijk is via de aanpassingsknop.

![](assets/s_advuser_segment_code_select.png)

## Data exporteren {#exporting-data}

### Een bestand {#zipping-or-encrypting-a-file} uitpakken of versleutelen

Met Adobe Campaign kunt u gecomprimeerde of gecodeerde bestanden exporteren. Wanneer u een exportbewerking definieert aan de hand van een **[!UICONTROL Data extraction (file)]**-activiteit, kunt u een nabewerkingsbewerking definiëren als ZIP-bestand of het bestand versleutelen.

Om dit te kunnen doen:

1. Installeer een sleutelpaar GPG voor uw instantie gebruikend [Controlebord](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Het Configuratiescherm is beschikbaar voor alle klanten die op AWS worden gehost (behalve voor klanten die hun marketinginstanties op locatie hosten).

1. Als uw installatie van Adobe Campaign wordt gehost door Adobe, neemt u contact op met de klantenservice van Adobe om de benodigde hulpprogramma&#39;s op de server te installeren.
1. Als de installatie van Adobe Campaign op locatie plaatsvindt, installeert u het hulpprogramma dat u wilt gebruiken (bijvoorbeeld: GPG, GZIP) en de benodigde sleutels (coderingssleutel) op de toepassingsserver.

Vervolgens kunt u opdrachten of code gebruiken op het tabblad **[!UICONTROL Script]** van de activiteit of in een activiteit **[!UICONTROL JavaScript code]**. In het onderstaande gebruiksgeval wordt een voorbeeld gegeven.

**Verwante onderwerpen:**

* [Een bestand decoderen of decoderen voordat het wordt verwerkt](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [Activiteit](../../workflow/using/extraction--file-.md) voor gegevensextractie (bestand).

### Hoofdlettergebruik: Gegevens coderen en exporteren met behulp van een sleutel die is geïnstalleerd in het Configuratiescherm {#use-case-gpg-encrypt}

In dit geval, zullen wij een werkschema bouwen om gegevens te coderen en uit te voeren gebruikend een sleutel die op Controlebord wordt geïnstalleerd.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#video)

De volgende stappen worden uitgevoerd:

1. Genereer een sleutelpaar van GPG (openbaar/privé) gebruikend een nut van GPG, dan installeer de openbare sleutel op Controlebord. Gedetailleerde stappen zijn beschikbaar in [documentatie van het Configuratiescherm](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. In Campaign Classic, bouwt een werkschema om de gegevens uit te voeren en het te coderen gebruikend de privé sleutel die via het Controlebord is geïnstalleerd. Hiervoor maken we als volgt een workflow:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** activiteit: In dit voorbeeld, willen wij een vraag uitvoeren om de gegevens van het gegevensbestand te richten dat wij willen uitvoeren.
   * **[!UICONTROL Data extraction (file)]** activiteit: Extraheert de gegevens naar een bestand.
   * **[!UICONTROL JavaScript code]** activiteit: Codeert de gegevens die u wilt extraheren.
   * **[!UICONTROL File transfer]** activiteit: Hiermee verzendt u de gegevens naar een externe bron (in dit voorbeeld een SFTP-server).

1. Vorm **[!UICONTROL Query]** activiteit om de gewenste gegevens van het gegevensbestand te richten. Raadpleeg [deze sectie](../../workflow/using/query.md) voor meer informatie.

1. Open de **[!UICONTROL Data extraction (file)]** activiteit dan vorm het op uw behoeften. De globale concepten op hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Open de **[!UICONTROL JavaScript code]** activiteit, dan kopieer-kleef het hieronder bevel om de gegevens te coderen om te halen.

   >[!IMPORTANT]
   >
   >Zorg ervoor dat u de **vingerafdruk**-waarde van de opdracht vervangt door de vingerafdruk van de openbare sleutel die in het Configuratiescherm is geïnstalleerd.

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

1. Open de **[!UICONTROL File transfer]** activiteit, dan specificeer de server SFTP waarnaar u het dossier wilt verzenden. De globale concepten op hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. U kunt de workflow nu uitvoeren. Zodra het wordt uitgevoerd, zal het gegevensdoel door de vraag naar de server SFTP in een gecodeerd.gpg- dossier worden uitgevoerd.

### Video over zelfstudie {#video}

In deze video wordt getoond hoe u een GPG-sleutel kunt gebruiken om gegevens te coderen. Deze video is ook beschikbaar in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
