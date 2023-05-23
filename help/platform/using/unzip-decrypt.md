---
product: campaign
title: Een bestand ontsleutelen of ontsleutelen
description: Leer hoe u een bestand in Campagne decodeert of decodeert voordat u het verwerkt
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 10%

---

# Een bestand decoderen of decoderen {#unzipping-or-decrypting-a-file-before-processing}



Met Adobe Campaign kunt u gecomprimeerde of gecodeerde bestanden importeren. Voordat ze in een [Gegevens laden (bestand)](../../workflow/using/data-loading--file-.md) -activiteit, kunt u een voorbewerking definiëren voor decoderen of decoderen.

Om dit te kunnen doen:

1. Gebruik de [Deelvenster Beheer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) om een openbare/privé zeer belangrijke paar te produceren.

   >[!NOTE]
   >
   >Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om toegang met beheerdersrechten aan een gebruiker te verlenen worden gedetailleerd beschreven op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
   >
   >Merk op dat uw exemplaar op AWS moet worden gehost en geüpgraded met de [nieuwste GA-build](../../rn/using/rn-overview.md). Leer hoe u uw versie kunt controleren in [dit gedeelte](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Controleer of uw versie wordt gehost op AWS door de volgende stappen te volgen op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

1. Als uw installatie van Adobe Campaign wordt gehost door Adobe, neemt u contact op met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de benodigde hulpprogramma&#39;s op de server te installeren.
1. Als de installatie van Adobe Campaign op locatie plaatsvindt, installeert u het hulpprogramma dat u wilt gebruiken (bijvoorbeeld: GPG, GZIP) en de benodigde sleutels (coderingssleutel) op de toepassingsserver.

Vervolgens kunt u de gewenste voorverwerkingsopdrachten in uw workflows gebruiken:

1. Een **[!UICONTROL File transfer]** activiteit in uw werkstroom.
1. Voeg een **[!UICONTROL Data loading (file)]** en definieert u de bestandsindeling.
1. Schakel de optie **[!UICONTROL Pre-process the file]** in.
1. Geef de voorverwerkingsopdracht op die u wilt toepassen.
1. Voeg andere activiteiten toe om gegevens die uit het bestand komen te beheren.
1. Sla de workflow op en voer deze uit.

In het onderstaande gebruiksgeval wordt een voorbeeld gegeven.

**Verwante onderwerpen:**

* [Activiteit bij laden van gegevens (bestand)](../../workflow/using/data-loading--file-.md).
* [Een bestand comprimeren of versleutelen](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Hoofdlettergebruik: Gegevens importeren die zijn versleuteld met een sleutel die is gegenereerd door het Configuratiescherm {#use-case-gpg-decrypt}

In dit geval, zullen wij een werkschema bouwen om gegevens in te voeren die in een extern systeem zijn gecodeerd, gebruikend een sleutel die in het Controlebord wordt geproduceerd.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#video)

De volgende stappen worden uitgevoerd:

1. Gebruik het Configuratiescherm om een sleutelpaar (openbaar/privé) te genereren. Gedetailleerde stappen zijn beschikbaar in [Documentatie van het regelpaneel](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * De openbare sleutel zal met het externe systeem worden gedeeld, dat het zal gebruiken om de gegevens te coderen om naar Campagne te verzenden.
   * De persoonlijke sleutel wordt door Campaign Classic gebruikt om de inkomende gecodeerde gegevens te decoderen.

   ![](assets/gpg_generate.png)

1. In het externe systeem gebruikt u de openbare sleutel die u van het Configuratiescherm hebt gedownload om de gegevens te coderen die u naar Campaign Classic wilt importeren.

1. In Campaign Classic, bouwt een werkschema om de gecodeerde gegevens in te voeren en het te decrypteren gebruikend de privé sleutel die via het Controlebord is geïnstalleerd. Hiervoor maken we als volgt een workflow:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** activiteit: Hiermee wordt het bestand van een externe bron naar Campaign Classic overgedragen. In dit voorbeeld willen we het bestand overbrengen van een SFTP-server.
   * **[!UICONTROL Data loading (file)]** activiteit: Laadt de gegevens van het dossier in het gegevensbestand en decrypteert het gebruikend de privé sleutel die in het Controlebord wordt geproduceerd.

1. Open de **[!UICONTROL File transfer]** Geef vervolgens de externe account op waaruit u het gecodeerde .gpg-bestand wilt importeren.

   ![](assets/gpg_key_transfer.png)

   Globale concepten over hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/file-transfer.md).

1. Open de **[!UICONTROL Data loading (file)]** activiteit, dan vorm het op uw behoeften. Globale concepten over hoe te om de activiteit te vormen zijn beschikbaar in [deze sectie](../../workflow/using/data-loading--file-.md).

   Voeg een voorbewerkingsstadium aan de activiteit toe, om de inkomende gegevens te decrypteren. Selecteer hiervoor de optie **[!UICONTROL Pre-process the file]** en kopieert en plakt u deze decoderingsopdracht in het dialoogvenster **[!UICONTROL Command]** field:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >In dit voorbeeld, gebruiken wij passphrase die door gebrek door Controlebord wordt gebruikt, dat &quot;passphrase&quot;is.
   >
   >Als u in het verleden al GPG-sleutels op uw exemplaar hebt geïnstalleerd via een verzoek van de klantenservice, is de passphrase mogelijk gewijzigd en is deze standaard anders.

1. Klikken **[!UICONTROL OK]** om de activiteitenconfiguratie te bevestigen.

1. U kunt de workflow nu uitvoeren. Nadat de decodering is uitgevoerd, kunt u in de werkstroomlogboeken controleren of de decodering is uitgevoerd en of de gegevens uit het bestand zijn geïmporteerd.

   ![](assets/gpg_run.png)

## Video over zelfstudie {#video}

In deze video wordt getoond hoe u een GPG-sleutel kunt gebruiken voor het decoderen van gegevens.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Er zijn aanvullende Campaign Classic-hoe-kan-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
