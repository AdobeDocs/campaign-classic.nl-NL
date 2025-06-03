---
product: campaign
title: E-mailinhoud definiëren in Adobe Campaign Classic
description: Leer hoe u de e-mailinhoud definieert wanneer u Adobe Campaign gebruikt
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design
role: User
hide: true
hidefromtoc: true
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 1%

---

# De e-mailcontent opgeven {#defining-the-email-content}

## Afzender {#sender}

Klik op de koppeling **[!UICONTROL From]** om de naam en het adres te definiëren van de afzender die wordt weergegeven in de koptekst van de verzonden berichten.

![](assets/s_ncs_user_wizard_email02.png)

In dit venster kunt u alle gegevens invoeren die nodig zijn om de e-mailberichtkoppen te maken. Deze informatie kan worden gepersonaliseerd. Hiervoor gebruikt u de knoppen rechts van de invoervelden om aanpassingsvelden in te voegen.

Om te weten te komen hoe te om verpersoonlijkingsgebieden op te nemen en te gebruiken, verwijs naar [ Ongeveer verpersoonlijkings ](about-personalization.md) sectie.

>[!NOTE]
>
>* Het adres van de afzender wordt gebruikt voor antwoorden door gebrek.
>* De headerparameters mogen niet leeg zijn. Door gebrek, bevatten zij de waardeninput wanneer het vormen van de plaatsingstovenaar. Lees meer in [deze sectie](../../installation/using/deploying-an-instance.md).
>* Het adres van de afzender is verplicht om een e-mailbericht toe te staan (norm RFC).
>* Adobe Campaign controleert de syntaxis van de ingevoerde e-mailadressen.

>[!CAUTION]
>
>Om leveringsproblemen te voorkomen, moeten de e-mailaccounts die overeenkomen met de adressen die voor leveringen en antwoorden zijn opgegeven, bestaan en worden gecontroleerd. Neem contact op met de systeembeheerder.

## Berichtonderwerp {#message-subject}

Het onderwerp van het bericht wordt gevormd op het overeenkomstige gebied. U kunt het rechtstreeks in het veld invoeren of op de koppeling **[!UICONTROL Subject]** klikken om een script in te voeren. Met de koppeling voor personalisatie kunt u databasevelden in het onderwerp invoegen.

>[!IMPORTANT]
>
>Het onderwerp van het bericht is verplicht.

![](assets/s_ncs_user_wizard_email_object.png)

De inhoud van het veld wordt vervangen door de waarde in het ontvangende profiel wanneer het bericht wordt verzonden.

In het bovenstaande bericht is het onderwerp van het bericht bijvoorbeeld gepersonaliseerd voor elke ontvanger met gegevens uit zijn profiel.

>[!NOTE]
>
>Het gebruik van verpersoonlijkingsgebieden wordt voorgesteld in [ Ongeveer verpersoonlijking ](about-personalization.md).

U kunt ook emoticons invoegen in uw onderwerpregel via het pop-upvenster van **[!UICONTROL Insert emoticon]** .

## Berichtinhoud {#message-content}

>[!IMPORTANT]
>
>Om privacyredenen raden we u aan HTTPS te gebruiken voor alle externe bronnen.

De inhoud van het bericht wordt bepaald in de lagere sectie van het venster van de leveringsconfiguratie.

Berichten worden standaard in HTML of tekstindeling verzonden, afhankelijk van de voorkeur van de ontvanger. We raden u aan inhoud in beide indelingen te maken om ervoor te zorgen dat berichten correct kunnen worden weergegeven in elk e-mailsysteem. Voor meer op dit, verwijs naar [ Selecterend berichtformaten ](email-parameters.md#selecting-message-formats).

* Als u HTML-inhoud wilt importeren, gebruikt u de knop **[!UICONTROL Open]** . U kunt de broncode ook rechtstreeks in de subtab **[!UICONTROL Source]** plakken.

  Als u de [ Digitale Redacteur van de Inhoud ](../../web/using/about-campaign-html-editor.md) (DCE) gebruikt, verwijs naar [ Selecterend een inhoudsmalplaatje ](../../web/using/use-case-creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >De HTML-inhoud moet vooraf worden gemaakt en vervolgens worden geïmporteerd in Adobe Campaign. De HTML-editor is niet ontworpen voor het maken van inhoud.

  Met het subtabblad **[!UICONTROL Preview]** kunt u de rendering van elke inhoud voor een ontvanger weergeven. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel.

  De werkbalkknoppen bieden toegang tot de standaardhandelingen en opmaakparameters voor de HTML-pagina.

  ![](assets/s_ncs_user_wizard_email01_138.png)

  U kunt afbeeldingen invoegen in berichten vanuit een lokaal bestand of vanuit een afbeeldingsbibliotheek in Adobe Campaign. Klik hiertoe op het pictogram **[!UICONTROL Image]** en selecteer de gewenste optie.

  ![](assets/s_ncs_user_wizard_email01_18.png)

  Bibliotheekafbeeldingen zijn toegankelijk via de map **[!UICONTROL Resources>Online>Public resources]** in de mappenstructuur. Ook verwijs naar [ het Toevoegen van beelden ](#adding-images).

  Met de laatste knop op de werkbalk kunt u aanpassingsvelden invoegen.

  >[!NOTE]
  >
  >Het gebruik van verpersoonlijkingsgebieden wordt voorgesteld in [ Ongeveer verpersoonlijking ](about-personalization.md).

  Met de tabbladen onder aan de pagina kunt u de HTML-code weergeven van de pagina die wordt gemaakt en kunt u de weergave van het bericht met de personalisatie bekijken. Klik op **[!UICONTROL Preview]** en selecteer een ontvanger met de knop **[!UICONTROL Test personalization]** op de werkbalk om deze weergave te starten. U kunt een ontvanger selecteren bij de gedefinieerde doelgroep(en) of een andere ontvanger kiezen.

  ![](assets/s_ncs_user_wizard_email01_139.png)

  U kunt het HTML-bericht valideren. U kunt ook de inhoud van de koptekst van de e-mail weergeven.

  ![](assets/s_ncs_user_wizard_email01_140.png)

* Als u tekstinhoud wilt importeren, gebruikt u de knop **[!UICONTROL Open]** of het tabblad **[!UICONTROL Text Content]** om de inhoud van het bericht in te voeren wanneer deze in tekstindeling wordt weergegeven. Gebruik de werkbalkknoppen om toegang te krijgen tot handelingen over de inhoud. Met de laatste knop kunt u aanpassingsvelden invoegen.

  ![](assets/s_ncs_user_wizard_email01_141.png)

  Voor de HTML-indeling klikt u op de tab **[!UICONTROL Preview]** onder aan de pagina om de weergave van het bericht met de personalisatie weer te geven.

  ![](assets/s_ncs_user_wizard_email01_142.png)


## Interactieve content definiëren {#amp-for-email-format}

Adobe Campaign laat u toe om nieuwe interactieve [ AMP voor E-mail ](https://amp.dev/about/email/) formaat te proberen, dat toelaat om dynamische e-mails, onder bepaalde voorwaarden te verzenden.

Zie [deze sectie](defining-interactive-content.md)voor meer informatie.

## Inhoudsbeheer gebruiken {#using-content-management}

U kunt de inhoud van de levering bepalen gebruikend de vormen van het inhoudsbeheer, direct in de leveringsmedewerker. Hiervoor moet u verwijzen naar de publicatiesjabloon van het te gebruiken inhoudsbeheer op het tabblad **[!UICONTROL Advanced]** van de leveringseigenschappen.

![](assets/s_ncs_content_in_delivery.png)

Met een extra tabblad kunt u inhoud invoeren die automatisch wordt geïntegreerd en opgemaakt volgens de regels voor inhoudsbeheer.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Voor verdere informatie over inhoudsbeheer in Adobe Campaign, verwijs naar [ deze sectie ](about-content-management.md).

## emoticons invoegen {#inserting-emoticons}

U kunt emoticons invoegen in uw e-mailinhoud.

1. Klik op het pictogram **[!UICONTROL Insert emoticon]** .
1. Selecteer een emoticon in het pop-upvenster.

   ![](assets/emoticon_4.png)

1. Klik op de knop **[!UICONTROL Close]** als u klaar bent.

Om de emoticonlijst aan te passen, verwijs naar deze [ pagina ](customizing-emoticon-list.md).

## Afbeeldingen toevoegen {#adding-images}

E-mailleveringen in HTML-indeling kunnen afbeeldingen bevatten. Vanuit de bezorgingsassistent kunt u een HTML-pagina met afbeeldingen importeren of afbeeldingen rechtstreeks invoegen via de HTML-editor via het pictogram **[!UICONTROL Image]** .


### Guardrails {#img-guardrails}

Om prestatieproblemen te voorkomen, mogen afbeeldingen in e-mailberichten niet groter zijn dan 100 kB. Deze standaard ingestelde limiet kan worden gewijzigd met de optie `NmsDelivery_MaxDownloadedImageSize` . Adobe raadt echter sterk aan om grote afbeeldingen in uw e-mailleveringen te voorkomen.

Leer meer in [ de lijst van de opties van Campaign Classic ](../../installation/using/configuring-campaign-options.md#delivery).

### Afbeeldingstypen {#img-types}

Afbeeldingen kunnen:

* Een lokale afbeelding of een afbeelding die wordt aangeroepen vanaf een server
* Een afbeelding die is opgeslagen in de openbare-bronnenbibliotheek van Adobe Campaign

  Openbare bronnen zijn toegankelijk via het knooppunt **[!UICONTROL Resources > Online]** van de Adobe Campaign-hiërarchie. Ze zijn gegroepeerd in een bibliotheek en kunnen worden opgenomen in e-mailberichten, maar kunnen ook worden gebruikt voor campagnes of taken, of voor inhoudsbeheer.

* An asset shared with Adobe Experience Cloud. Zie [deze sectie](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

### Afbeeldingen invoegen en beheren {#manage-images}

Met de leveringsassistent kunt u lokale afbeeldingen of afbeeldingen die zijn opgeslagen in de bibliotheek toevoegen aan de inhoud van berichten. Klik hiertoe op de knop **[!UICONTROL Image]** op de werkbalk HTML-inhoud.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>De ontvangers kunnen de afbeeldingen die zijn opgenomen in de berichten die ze ontvangen, alleen weergeven als deze berichten beschikbaar zijn op een server die van buitenaf toegankelijk is.

Afbeeldingen beheren via de leveringsassistent:

1. Klik op het pictogram **[!UICONTROL Tracking & Images]** op de werkbalk.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. Selecteer **[!UICONTROL Upload images]** op het tabblad **[!UICONTROL Images]** .
1. Vervolgens kunt u kiezen of u de afbeeldingen in het e-mailbericht wilt opnemen.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* U kunt afbeeldingen handmatig uploaden zonder te wachten op de fase van de leveringsanalyse. Klik hiertoe op de koppeling **[!UICONTROL Upload the images straightaway...]** .
* U kunt een ander pad opgeven voor toegang tot de afbeeldingen op de trackingserver. U doet dit door het bestand in het veld **[!UICONTROL Images URL]** in te voeren. Deze waarde treedt de waarde met voeten die in de parameters van de installatiemedewerker wordt bepaald.

Wanneer u HTML-inhoud opent met opgenomen afbeeldingen in de leveringsassistent, kunt u de afbeeldingen volgens de leveringsparameters direct uploaden.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
> De afbeeldings-URL&#39;s worden gewijzigd tijdens handmatig uploaden of tijdens het verzenden van berichten.
> 

### Hoofdlettergebruik: een bericht met afbeeldingen verzenden {#uc-images}

Hieronder ziet u een voorbeeld van een levering met vier afbeeldingen:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Deze afbeeldingen zijn afkomstig uit een lokale map of website die u kunt verifiëren via het tabblad **[!UICONTROL Source]** .

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Klik op het pictogram **[!UICONTROL Tracking & Images]** en vervolgens op de tab **[!UICONTROL Images]** om de afbeeldingen in het bericht te detecteren.

Voor elke gedetecteerde afbeelding kunt u de status bekijken:

* Als een afbeelding lokaal is opgeslagen of zich op een andere server bevindt, zelfs als deze server van buitenaf zichtbaar is (bijvoorbeeld op een internetsite), wordt deze gedetecteerd als **[!UICONTROL Not yet online]** .
* De afbeeldingen worden gedetecteerd als **[!UICONTROL Already online]** als ze eerder zijn geüpload terwijl een andere levering wordt gemaakt.
* In de implementatietovenaar kunt u URLs bepalen waarvoor beeldopsporing niet wordt toegelaten: het uploaden van deze beelden zal **[!UICONTROL Skipped]** zijn.

>[!NOTE]
>
>Afbeeldingen worden geïdentificeerd door hun inhoud en niet door hun toegangspaden. Dit betekent dat een afbeelding die eerder onder een andere naam of in een andere map is geüpload, wordt gedetecteerd als **[!UICONTROL Already online]** .

Tijdens de analysefase worden de afbeeldingen automatisch geüpload naar de server, zodat ze van buitenaf toegankelijk zijn, behalve de lokale afbeeldingen die vooraf moeten worden geüpload.

U kunt vooruit werken en afbeeldingen uploaden, zodat deze door andere Adobe Campaign-operatoren kunnen worden weergegeven. Dit is handig als u in samenwerking werkt. Klik hiertoe op **[!UICONTROL Upload the images straightaway...]** om de afbeeldingen naar de server te uploaden.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>De URL&#39;s van de afbeeldingen in de e-mail en met name de namen van de afbeeldingen worden vervolgens gewijzigd.

Als de afbeeldingen eenmaal online zijn, kunt u de wijzigingen in de naam en het pad bekijken via het tabblad **[!UICONTROL Source]** van het bericht.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Als u **[!UICONTROL Include the images in the email]** selecteert, kunt u kiezen welke afbeeldingen u wilt opnemen in de corresponderende kolom.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Als het bericht lokale afbeeldingen bevat, moet u de wijzigingen in de broncode van het bericht bevestigen.

## Een gepersonaliseerde streepjescode invoegen{#insert-a-barcode}

Met de module voor het genereren van streepjescodes kunt u verschillende typen streepjescodes maken die voldoen aan veel gangbare normen, waaronder 2D-streepjescodes.

Het is mogelijk om dynamisch een streepjescode als bitmap te produceren gebruikend een waarde die gebruikend klantencriteria wordt bepaald. U kunt persoonlijke streepjescodes opnemen in e-mailcampagnes. De ontvanger kan het bericht afdrukken en het aan het uitgevende bedrijf tonen voor scannen (bijvoorbeeld bij uitchecken).

Als u een streepjescode in een e-mailbericht wilt invoegen, plaatst u de cursor op de gewenste plaats in de inhoud en klikt u op de knop voor aanpassen. Selecteer **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Dan vorm de volgende elementen om uw behoeften aan te passen:

1. Selecteer het type streepjescode.

   * Voor 1D-indeling zijn de volgende typen beschikbaar in Adobe Campaign: Codabar, Code 128, GS1-128 (voorheen EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET en Royal Mail (RM4SCC).

     Voorbeeld van een 1D-streepjescode:

     ![](assets/barcode_insert_08.png)

   * De typen DataMatrix en PDF417 hebben betrekking op de 2D-indeling.

     Voorbeeld van een 2D-streepjescode:

     ![](assets/barcode_insert_09.png)

   * Als u een QR-code wilt invoegen, selecteert u dit type en voert u de toe te passen foutcorrectiesnelheid in. Dit percentage bepaalt de hoeveelheid gegevens die wordt herhaald en de tolerantie voor kwaliteitsverlies.

     ![](assets/barcode_insert_06.png)

     Voorbeeld van een QR-code:

     ![](assets/barcode_insert_12.png)

1. Voer de grootte in van de streepjescode die u in de e-mail wilt invoegen: als u de schaal configureert, kunt u de streepjescode groter of kleiner maken, van x1 tot x10.
1. In het veld **[!UICONTROL Value]** kunt u de waarde van de streepjescode definiëren. Een waarde kan een speciale aanbieding aanpassen en kan de functie van criteria zijn, het kan de waarde van een gegevensbestandgebied zijn verbonden met de klanten.

   In dit voorbeeld wordt een streepjescode van het type EAN-8 getoond, waaraan het rekeningnummer van een ontvanger is toegevoegd. Als u dit accountnummer wilt toevoegen, klikt u op de aanpassingsknop rechts van het veld **[!UICONTROL Value]** en selecteert u **[!UICONTROL Recipient > Account number]** .

   ![](assets/barcode_insert_15.png)

1. Met het veld **[!UICONTROL Height]** kunt u de hoogte van de streepjescode configureren zonder de breedte te wijzigen door de hoeveelheid ruimte tussen de streepjes te wijzigen.

   Er is geen restrictief besturingselement voor invoer afhankelijk van het type streepjescode. Als een streepjescodewaarde onjuist is, zal het slechts op **** wijze van de Voorproef zichtbaar zijn waar de streepjescode in rood zal worden gekruist.

   >[!NOTE]
   >
   >De waarde die aan een streepjescode wordt toegewezen, is afhankelijk van het type. Een type EAN-8 moet bijvoorbeeld precies 8 cijfers hebben.
   >
   >Met de aanpassingsknop rechts van het veld **[!UICONTROL Value]** kunt u naast de waarde zelf ook gegevens toevoegen. Hiermee wordt de streepjescode verrijkt, op voorwaarde dat de streepjescodestandaard dit accepteert.
   >
   >Als u bijvoorbeeld een streepjescode van het type GS1-128 gebruikt en als u naast de waarde het rekeningnummer van een ontvanger wilt invoeren, klikt u op de knop Verpersoonlijken en selecteert u **[!UICONTROL Recipient > Account number]** . Als het accountnummer van de geselecteerde ontvanger correct is ingevoerd, wordt hiermee rekening gehouden in de streepjescode.

Zodra deze elementen zijn gevormd, kunt u uw e-mail voltooien en het verzenden. Als u fouten wilt voorkomen, moet u ervoor zorgen dat de inhoud correct wordt weergegeven voordat u de levering uitvoert door op het tabblad **[!UICONTROL Preview]** te klikken.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Wanneer de waarde van een streepjescode onjuist is, wordt de bitmap rood weergegeven.

![](assets/barcode_insert_11.png)
