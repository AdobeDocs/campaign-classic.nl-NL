---
product: campaign
title: E-mailinhoud definiëren in Adobe Campaign Classic
description: Leer hoe u de e-mailinhoud definieert wanneer u Adobe Campaign Classic gebruikt.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 1%

---

# De e-mailcontent definiëren {#defining-the-email-content}

![](../../assets/common.svg)

## Afzender {#sender}

Klik op de koppeling **[!UICONTROL From]** om de naam en het adres van de afzender te definiëren die worden weergegeven in de koptekst van de verzonden berichten.

![](assets/s_ncs_user_wizard_email02.png)

In dit venster kunt u alle gegevens invoeren die nodig zijn om de e-mailberichtkoppen te maken. Deze informatie kan worden aangepast. Hiervoor gebruikt u de knoppen rechts van de invoervelden om aanpassingsvelden in te voegen.

Om te weten te komen hoe te om verpersoonlijkingsgebieden op te nemen en te gebruiken, verwijs naar [Ongeveer verpersoonlijking](about-personalization.md) sectie.

>[!NOTE]
>
>* Het adres van de afzender zal voor antwoorden door gebrek worden gebruikt.
>* De headerparameters mogen niet leeg zijn. Door gebrek, bevatten zij de waardeninput wanneer het vormen van de plaatsingstovenaar. Raadpleeg de [Installatiegids](../../installation/using/deploying-an-instance.md) voor meer informatie.
>* Het adres van de afzender is verplicht om een e-mailbericht toe te staan (norm RFC).
>* Adobe Campaign controleert de syntaxis van de ingevoerde e-mailadressen.


>[!IMPORTANT]
>
>In het kader van de controles die door de Leveranciers van de Toegang van Internet (ISPs) worden uitgevoerd om ongevraagde e-mail (spam) te bestrijden, adviseert Adobe het creëren van e-mailrekeningen die aan de adressen beantwoorden die voor leveringen en antwoorden worden gespecificeerd. Vraag de beheerder van het berichtensysteem om advies.

## Berichtonderwerp {#message-subject}

Het onderwerp van het bericht wordt gevormd op het overeenkomstige gebied. U kunt het in het gebied direct ingaan of **[!UICONTROL Subject]** klikken om een manuscript in te gaan. Met de koppeling voor personalisatie kunt u databasevelden in het onderwerp invoegen.

>[!IMPORTANT]
>
>Het onderwerp van het bericht is verplicht.

![](assets/s_ncs_user_wizard_email_object.png)

De inhoud van het veld wordt vervangen door de waarde in het ontvangende profiel wanneer het bericht wordt verzonden.

In het bovenstaande bericht is het onderwerp van het bericht bijvoorbeeld gepersonaliseerd voor elke ontvanger met gegevens uit zijn profiel.

>[!NOTE]
>
>Het gebruik van verpersoonlijkingsgebieden wordt voorgesteld in [Info verpersoonlijking](about-personalization.md).

U kunt ook emoticons invoegen in uw onderwerpregel met het pop-upvenster **[!UICONTROL Insert emoticon]**.

## Berichtinhoud {#message-content}

>[!IMPORTANT]
>
>Om privacyredenen raden we u aan HTTPS te gebruiken voor alle externe bronnen.

De inhoud van het bericht wordt bepaald in de lagere sectie van het venster van de leveringsconfiguratie.

Berichten worden standaard in HTML- of tekstindeling verzonden, afhankelijk van de voorkeur van de ontvanger. We raden u aan inhoud in beide indelingen te maken om ervoor te zorgen dat berichten correct kunnen worden weergegeven in elk e-mailsysteem. Voor meer op dit, verwijs naar [Selecting berichtformaten](#selecting-message-formats).

* Als u HTML-inhoud wilt importeren, gebruikt u de knop **[!UICONTROL Open]**. U kunt de broncode ook rechtstreeks in **[!UICONTROL Source]** subtab kleven.

   Als u [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE) gebruikt, raadpleegt u [Een inhoudssjabloon selecteren](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >De HTML-inhoud moet vooraf worden gemaakt en vervolgens worden geïmporteerd in Adobe Campaign. De HTML-editor is niet ontworpen voor het maken van inhoud.

   Met het subtabblad **[!UICONTROL Preview]** kunt u de rendering van elke inhoud voor een ontvanger bekijken. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel.

   Met de werkbalkknoppen hebt u toegang tot de standaardhandelingen en opmaakparameters voor de HTML-pagina.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   U kunt afbeeldingen invoegen in berichten vanuit een lokaal bestand of vanuit een afbeeldingsbibliotheek in Adobe Campaign. Klik hiertoe op het pictogram **[!UICONTROL Image]** en selecteer de gewenste optie.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   Bibliotheekafbeeldingen zijn toegankelijk via de map **[!UICONTROL Resources>Online>Public resources]** in de mappenstructuur. Zie ook [Afbeeldingen toevoegen](#adding-images).

   Met de laatste knop op de werkbalk kunt u aanpassingsvelden invoegen.

   >[!NOTE]
   >
   >Het gebruik van verpersoonlijkingsgebieden wordt voorgesteld in [Info verpersoonlijking](about-personalization.md).

   Met de tabbladen onder aan de pagina kunt u de HTML-code weergeven van de pagina die wordt gemaakt en kunt u de weergave van het bericht met de personalisatie bekijken. Als u deze weergave wilt starten, klikt u op **[!UICONTROL Preview]** en selecteert u een ontvanger met de knop **[!UICONTROL Test personalization]** op de werkbalk. U kunt een ontvanger selecteren bij de gedefinieerde doelgroep(en) of een andere ontvanger kiezen.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   U kunt het HTML-bericht valideren. U kunt ook de inhoud van de koptekst van de e-mail weergeven.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* Als u tekstinhoud wilt importeren, gebruikt u de knop **[!UICONTROL Open]** of het tabblad **[!UICONTROL Text Content]** om de inhoud van het bericht in te voeren wanneer deze wordt weergegeven in tekstopmaak. Gebruik de werkbalkknoppen om toegang te krijgen tot handelingen over de inhoud. Met de laatste knop kunt u aanpassingsvelden invoegen.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   Als voor het formaat van HTML klikt het **[!UICONTROL Preview]** lusje bij de bodem van de pagina om het teruggeven van het bericht met zijn verpersoonlijking te bekijken.

   ![](assets/s_ncs_user_wizard_email01_142.png)


## Interactieve content definiëren {#amp-for-email-format}

Met Adobe Campaign kunt u de nieuwe interactieve [AMP voor e-mail](https://amp.dev/about/email/)-indeling uitproberen, waarmee u onder bepaalde omstandigheden dynamische e-mailberichten kunt verzenden.

Zie [deze sectie](defining-interactive-content.md)voor meer informatie.

## Inhoudsbeheer gebruiken {#using-content-management}

U kunt de inhoud van de levering bepalen gebruikend de vormen van het inhoudsbeheer, direct in de leveringstovenaar. Hiervoor moet u verwijzen naar de publicatiesjabloon van het inhoudsbeheer dat moet worden gebruikt, op het tabblad **[!UICONTROL Advanced]** van de leveringseigenschappen.

![](assets/s_ncs_content_in_delivery.png)

Met een extra tabblad kunt u inhoud invoeren die automatisch wordt geïntegreerd en opgemaakt volgens de regels voor inhoudsbeheer.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Zie [deze sectie](about-content-management.md) voor meer informatie over contentbeheer in Adobe Campaign.

## emoticons invoegen {#inserting-emoticons}

U kunt emoticons invoegen in uw e-mailinhoud.

1. Klik op het pictogram **[!UICONTROL Insert emoticon]**.
1. Selecteer een emoticon in het pop-upvenster.

   ![](assets/emoticon_4.png)

1. Klik op de knop **[!UICONTROL Close]** als u klaar bent.

Als u de lijst met emoticonen wilt aanpassen, raadpleegt u deze [pagina](customizing-emoticon-list.md).

## Afbeeldingen toevoegen {#adding-images}

E-mailleveringen in HTML-indeling kunnen afbeeldingen bevatten. Vanuit de wizard voor levering kunt u een HTML-pagina met afbeeldingen importeren of afbeeldingen rechtstreeks invoegen met de HTML-editor via het pictogram **[!UICONTROL Image]**.

Afbeeldingen kunnen:

* Een lokale afbeelding of een afbeelding die wordt aangeroepen vanaf een server
* Een afbeelding die is opgeslagen in de openbare-bronnenbibliotheek van Adobe Campaign

   De openbare middelen zijn toegankelijk via de **[!UICONTROL Resources > Online]** knoop van de hiërarchie van Adobe Campaign. Ze zijn gegroepeerd in een bibliotheek en kunnen worden opgenomen in e-mailberichten, maar kunnen ook worden gebruikt voor campagnes of taken, of voor inhoudsbeheer.

* An asset shared with Adobe Experience Cloud. Zie [deze sectie](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!IMPORTANT]
>
>Als u afbeeldingen in de e-mailberichten wilt opnemen met de wizard voor levering, moet de Adobe Campaign-instantie zo zijn geconfigureerd dat het beheer van openbare bronnen is ingeschakeld. Deze procedure kan van de plaatsingstovenaar worden uitgevoerd. Raadpleeg [deze sectie](../../installation/using/deploying-an-instance.md) voor meer informatie over de configuratie.

Met de wizard voor levering kunt u lokale afbeeldingen of afbeeldingen die zijn opgeslagen in de bibliotheek toevoegen aan de inhoud van berichten. Klik hiertoe op de knop **[!UICONTROL Image]** op de werkbalk HTML-inhoud.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>De ontvangers kunnen de afbeeldingen die zijn opgenomen in de berichten die ze ontvangen, alleen weergeven als deze berichten beschikbaar zijn op een server die van buitenaf toegankelijk is.

Afbeeldingen beheren via de wizard voor levering:

1. Klik op het pictogram **[!UICONTROL Tracking & Images]** op de werkbalk.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. Selecteer **[!UICONTROL Upload images]** op **[!UICONTROL Images]** tabel.
1. Vervolgens kunt u kiezen of u de afbeeldingen in het e-mailbericht wilt opnemen.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* U kunt afbeeldingen handmatig uploaden zonder te wachten op de fase van de leveringsanalyse. Klik op de koppeling **[!UICONTROL Upload the images straightaway...]** om dit te doen.
* U kunt een ander pad opgeven voor toegang tot de afbeeldingen op de trackingserver. Om dit te doen, ga het op het **[!UICONTROL Images URL]** gebied in. Deze waarde negeert de waarde die is gedefinieerd in de parameters van de installatiewizard.

Wanneer u HTML-inhoud met opgenomen afbeeldingen opent in de wizard voor levering, kunt u de afbeeldingen volgens de leveringsparameters direct uploaden.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>* De toegangspaden voor afbeeldingen worden gewijzigd tijdens het handmatig uploaden of tijdens het verzenden van berichten.
> 
>* Om prestatieproblemen te voorkomen, moet elke afbeeldingsgrootte standaard niet groter zijn dan 100.000 bytes als u direct gedownloade afbeeldingen opneemt van een gepersonaliseerde URL als [bijlage](attaching-files.md). Deze geadviseerde drempel kan van [de lijst van Campaign Classic opties](../../installation/using/configuring-campaign-options.md#delivery) worden gevormd.


**Hoofdlettergebruik: een bericht met afbeeldingen verzenden**

Hier volgt een voorbeeld van een levering met vier afbeeldingen:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Deze afbeeldingen komen uit een lokale map of website zoals u kunt controleren op het tabblad **[!UICONTROL Source]**.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Klik op het pictogram **[!UICONTROL Tracking & Images]** en vervolgens op het tabblad **[!UICONTROL Images]** om de afbeeldingen in het bericht te detecteren.

Voor elke gedetecteerde afbeelding kunt u de status bekijken:

* Als een afbeelding lokaal is opgeslagen of zich op een andere server bevindt, zelfs als deze server van buitenaf zichtbaar is (bijvoorbeeld op een internetsite), wordt de afbeelding gedetecteerd als **[!UICONTROL Not yet online]**.
* De afbeeldingen worden gedetecteerd als **[!UICONTROL Already online]** als ze eerder zijn geüpload terwijl een andere levering wordt gemaakt.
* In de plaatsingstovenaar, kunt u URLs bepalen waarvoor beeldopsporing niet wordt toegelaten: Het uploaden van deze afbeeldingen wordt **[!UICONTROL Skipped]**.

>[!NOTE]
>
>Afbeeldingen worden geïdentificeerd door hun inhoud en niet door hun toegangspaden. Dit betekent dat een afbeelding die eerder onder een andere naam of in een andere map is geüpload, wordt gedetecteerd als **[!UICONTROL Already online]**.

Tijdens de analysefase worden de afbeeldingen automatisch geüpload naar de server, zodat ze van buitenaf toegankelijk zijn, behalve de lokale afbeeldingen die vooraf moeten worden geüpload.

U kunt vooruit werken en afbeeldingen uploaden, zodat deze door andere Adobe Campaign-operatoren kunnen worden weergegeven. Dit is handig als u in samenwerking werkt. Om dit te doen, klik **[!UICONTROL Upload the images straightaway...]** om de beelden op de server te uploaden.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>De URL&#39;s van de afbeeldingen in de e-mail en met name de namen van de afbeeldingen worden vervolgens gewijzigd.

Als de afbeeldingen eenmaal online zijn, kunt u de wijzigingen in de naam en het pad bekijken op het tabblad **[!UICONTROL Source]** van het bericht.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Als u **[!UICONTROL Include the images in the email]** selecteert, kunt u kiezen welke afbeeldingen u in de corresponderende kolom wilt opnemen.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Als het bericht lokale afbeeldingen bevat, moet u de wijzigingen in de broncode van het bericht bevestigen.

## Een streepjescode invoegen in een e-mail{#inserting-a-barcode-in-an-email}

Met de module voor het genereren van streepjescodes kunt u verschillende typen streepjescodes maken die voldoen aan veel gangbare normen, waaronder 2D-streepjescodes.

Het is mogelijk om dynamisch een streepjescode als bitmap te produceren gebruikend een waarde die gebruikend klantencriteria wordt bepaald. U kunt persoonlijke streepjescodes opnemen in e-mailcampagnes. De ontvanger kan het bericht afdrukken en het aan het uitgevende bedrijf tonen voor scannen (bijvoorbeeld bij uitchecken).

Als u een streepjescode in een e-mailbericht wilt invoegen, plaatst u de cursor op de gewenste plaats in de inhoud en klikt u op de knop voor aanpassen. Selecteer **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Dan vorm de volgende elementen om uw behoeften aan te passen:

1. Selecteer het type streepjescode.

   * Voor de 1D-indeling zijn de volgende typen beschikbaar in Adobe Campaign: Codabar, Code 128, GS1-128 (voorheen EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET and Royal Mail (RM4SCC).

      Voorbeeld van een 1D-streepjescode:

      ![](assets/barcode_insert_08.png)

   * De typen DataMatrix en PDF417 hebben betrekking op de 2D-indeling.

      Voorbeeld van een 2D-streepjescode:

      ![](assets/barcode_insert_09.png)

   * Als u een QR-code wilt invoegen, selecteert u dit type en voert u de toe te passen foutcorrectiesnelheid in. Dit percentage bepaalt de hoeveelheid gegevens die wordt herhaald en de tolerantie voor kwaliteitsverlies.

      ![](assets/barcode_insert_06.png)

      Voorbeeld van een QR-code:

      ![](assets/barcode_insert_12.png)

1. Voer de grootte in van de streepjescode die u in de e-mail wilt invoegen: Door de schaal te configureren kunt u de grootte van de streepjescode verhogen of verlagen, van x1 tot x10.
1. In het veld **[!UICONTROL Value]** kunt u de waarde van de streepjescode definiëren. Een waarde kan een speciale aanbieding aanpassen en kan de functie van criteria zijn, het kan de waarde van een gegevensbestandgebied zijn verbonden met de klanten.

   In dit voorbeeld wordt een streepjescode van het type EAN-8 getoond, waaraan het rekeningnummer van een ontvanger is toegevoegd. Als u dit accountnummer wilt toevoegen, klikt u op de aanpassingsknop rechts van het veld **[!UICONTROL Value]** en selecteert u **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. Met het veld **[!UICONTROL Height]** kunt u de hoogte van de streepjescode configureren zonder de breedte te wijzigen door de hoeveelheid ruimte tussen de streepjes te wijzigen.

   Er is geen restrictief besturingselement voor invoer afhankelijk van het type streepjescode. Als een streepjescodewaarde onjuist is, is deze alleen zichtbaar in de modus **Voorvertoning** waarin de streepjescode rood wordt doorgestreept.

   >[!NOTE]
   >
   >De waarde die aan een streepjescode wordt toegewezen, is afhankelijk van het type. Een type EAN-8 moet bijvoorbeeld precies 8 cijfers hebben.
   >
   >Met de aanpassingsknop rechts van het veld **[!UICONTROL Value]** kunt u naast de waarde zelf ook gegevens toevoegen. Hiermee wordt de streepjescode verrijkt, op voorwaarde dat de streepjescodestandaard dit accepteert.
   >
   >Als u bijvoorbeeld een streepjescode van het type GS1-128 gebruikt en als u naast de waarde het rekeningnummer van een ontvanger wilt invoeren, klikt u op de knop Verpersoonlijken en selecteert u **[!UICONTROL Recipient > Account number]**. Als het accountnummer van de geselecteerde ontvanger correct is ingevoerd, wordt hiermee rekening gehouden in de streepjescode.

Zodra deze elementen zijn gevormd, kunt u uw e-mail voltooien en het verzenden. Als u fouten wilt voorkomen, moet u ervoor zorgen dat de inhoud correct wordt weergegeven voordat u de levering uitvoert door op het tabblad **[!UICONTROL Preview]** te klikken.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Wanneer de waarde van een streepjescode onjuist is, wordt de bitmap rood weergegeven.

![](assets/barcode_insert_11.png)
