---
product: campaign
title: Personalisatieblokken
description: Personalisatieblokken
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 2%

---

# Personalisatieblokken{#personalization-blocks}

De blokken van de verpersoonlijking zijn dynamisch, gepersonaliseerd en bevatten een specifiek teruggeven dat u in uw leveringen kunt opnemen. U kunt bijvoorbeeld een logo, een begroetingsbericht of een koppeling naar een spiegelpagina toevoegen. Zie [Verpersoonlijkingsblokken invoegen](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Ontdek deze functie in video](#personalization-blocks-video)

De blokken van de Personalisering worden betreden via de **[!UICONTROL Resources > Campaign Management > Personalization blocks]** knoop van de ontdekkingsreiziger van Adobe Campaign. Verscheidene blokken zijn beschikbaar door gebrek (zie [Out-of-the-box verpersoonlijkingsblokken](#out-of-the-box-personalization-blocks)).

U hebt de mogelijkheid om nieuwe blokken te definiëren waarmee u uw leveringen kunt optimaliseren. Voor meer op dit, verwijs naar [Bepalend de blokken van de douaneverpersoonlijking](#defining-custom-personalization-blocks).

>[!NOTE]
>
>De blokken van de aanpassing zijn ook beschikbaar bij **[!UICONTROL Digital Content Editor (DCE)]**. Raadpleeg [deze pagina](../../web/using/editing-content.md#inserting-a-personalization-block) voor meer informatie.

## Aanmaakblokken invoegen {#inserting-personalization-blocks}

Volg onderstaande stappen om een verpersoonlijkingsblok in te voegen in een bericht:

1. Klik in de inhoudseditor van de wizard voor levering op het pictogram van het gepersonaliseerde veld en selecteer het menu **[!UICONTROL Include]**.
1. Selecteer een verpersoonlijkingsblok van de lijst (de lijst toont de 10 laatst gebruikte blokken), of klik **[!UICONTROL Other...]** menu om tot de volledige lijst toegang te hebben.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Het **[!UICONTROL Other...]** menu geeft toegang tot alle uit-van-de-doos en douane verpersoonlijkingsblokken (zie [Out-of-the-box verpersoonlijkingsblokken](#out-of-the-box-personalization-blocks) en [Bepalend douaneverpersoonlijkingsblokken](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Het verpersoonlijkingsblok wordt dan opgenomen als manuscript. Het wordt automatisch aangepast aan het ontvankelijke profiel wanneer de verpersoonlijking wordt geproduceerd.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klik op het tabblad **[!UICONTROL Preview]** en selecteer een ontvanger om de personalisatie weer te geven.

   ![](assets/s_ncs_user_personalized_block04.png)

U kunt de broncode van een verpersoonlijkingsblok in de leveringsinhoud omvatten. Selecteer **[!UICONTROL Include the HTML source code of the block]** wanneer u dit wilt doen.

![](assets/s_ncs_user_personalized_block05.png)

De HTML-broncode wordt ingevoegd in de leveringsinhoud. Het **[!UICONTROL Greetings]**-aanpassingsblok wordt bijvoorbeeld als volgt weergegeven:

![](assets/s_ncs_user_personalized_block06.png)

## Voorbeeld van aanpassingsblokken {#personalization-blocks-example}

In dit voorbeeld maken we een e-mail waarin we personalisatieblokken gebruiken om de ontvanger in staat te stellen de spiegelpagina te bekijken, de nieuwsbrief te delen op sociale netwerken en ons af te melden voor toekomstige leveringen.

Om dit te doen, moeten wij de volgende verpersoonlijkingsblokken opnemen:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Raadpleeg [De spiegelpagina genereren](sending-messages.md#generating-the-mirror-page) voor meer informatie over het genereren van de spiegelpagina.

1. Maak een nieuwe levering of open een bestaande e-maillevering.
1. Klik in de wizard voor aflevering op **[!UICONTROL Subject]** om het onderwerp van het bericht te bewerken en een onderwerp in te voeren.
1. Neem de verpersoonlijkingsblokken in het berichtlichaam op. Klik hiertoe in de berichtinhoud, klik op het pictogram van het gepersonaliseerde veld en selecteer het menu **[!UICONTROL Include]**.
1. Selecteer het eerste blok dat u wilt invoegen. Vernieuw de procedure om de twee andere blokken op te nemen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klik op het tabblad **[!UICONTROL Preview]** om het verpersoonlijkingsresultaat weer te geven. U moet een ontvanger selecteren om het bericht van die ontvanger te tonen.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Controleer of de inhoud van het blok correct wordt weergegeven.

## Buiten-de-doos verpersoonlijkingsblokken {#out-of-the-box-personalization-blocks}

Een lijst van verpersoonlijkingsblokken is beschikbaar door gebrek om u te helpen de inhoud van uw bericht personaliseren.

>[!NOTE]
>
>De lijst van verpersoonlijkingsblokken hangt van de modules en de opties af die op uw instantie zijn geïnstalleerd.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : voegt begroetingen met de naam van de ontvanger in. Voorbeeld: &quot;Hallo JanDoe,&quot;.
* **[!UICONTROL Insert logo]** : neemt een uit-van-de-doos embleem op dat wanneer het vormen van de instantie is bepaald.
* **[!UICONTROL Powered by Adobe Campaign]** : voegt het logo &quot;Powered by Adobe Campaign&quot; in.
* **[!UICONTROL Mirror page URL]** : voegt de URL van de spiegelpagina in, waardoor de leveringsontwerpers de koppeling kunnen controleren.

   >[!NOTE]
   >
   >Raadpleeg [De spiegelpagina genereren](sending-messages.md#generating-the-mirror-page) voor meer informatie over het genereren van de spiegelpagina.

* **[!UICONTROL Link to mirror page]** : voegt een koppeling naar de spiegelpagina in: &quot;Klik hier als je dit bericht niet juist kunt weergeven.&quot;
* **[!UICONTROL Unsubscription link]** : voegt een koppeling in waarmee u zich kunt afmelden bij alle leveringen (lijst van gewezen personen).
* **[!UICONTROL Formatting function for proper nouns]** : Hiermee wordt de functie  **[!UICONTROL toSmartCase]** JavaScript gegenereerd. De eerste letter van elk woord wordt in hoofdletters gewijzigd.
* **[!UICONTROL Registration page URL]** : voegt een abonnement-URL in (zie  [Informatie over services en abonnementen](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : voegt een abonnementkoppeling in. die is gedefinieerd tijdens het configureren van de instantie.
* **[!UICONTROL Registration link (with referrer)]** : voegt een abonnementkoppeling in, waarmee de bezoeker en de levering kunnen worden geïdentificeerd. De koppeling is gedefinieerd tijdens het configureren van de instantie.

   >[!NOTE]
   >
   >Dit blok kan alleen worden gebruikt bij leveringen voor bezoekers.

* **[!UICONTROL Registration confirmation]** : voegt een koppeling in waarmee u het abonnement kunt bevestigen.
* **[!UICONTROL Social network sharing links]** : voegt knopen in die de ontvanger toelaten om een verbinding aan de inhoud van de spiegelpagina met de e-mailcliënt, Facebook, Twitter, en LinkedIn te delen (zie  [Viral marketing: door naar een vriend](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** en  **[!UICONTROL Notification style]** : genereren code waarmee een e-mailbericht wordt opgemaakt met vooraf gedefinieerde HTML-stijlen. Deze blokken moeten in de broncode van de levering, in **[!UICONTROL ...]** sectie, in **`<style>...</style>`** markeringen worden opgenomen.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : voegt een URL in waarmee een interactieaanbieding kan worden ingesteld op  **[!UICONTROL Accepted]** (zie  [deze sectie](../../interaction/using/offer-analysis-report.md)).

## Aangepaste aanpassingsblokken definiëren {#defining-custom-personalization-blocks}

U kunt nieuwe verpersoonlijkingsgebieden bepalen die van het gepersonaliseerde gebiedspictogram via het **[!UICONTROL Include...]** menu moeten worden opgenomen. Deze gebieden worden bepaald in verpersoonlijkingsblokken.

Ga naar de verkenner en voer de volgende stappen uit om een verpersoonlijkingsblok te maken:

1. Klik op het knooppunt **[!UICONTROL Resources > Campaign Management > Personalization blocks]**.
1. Klik met de rechtermuisknop op de lijst met blokken en selecteer **[!UICONTROL New]**.
1. Vul de instellingen van het verpersoonlijkingsblok in:

   ![](assets/s_ncs_user_personalized_block.png)

   * Voer het label van het blok in. Dit label wordt weergegeven in het invoegvenster van het aanpassingsveld.
   * Selecteer **[!UICONTROL Visible in the customization menus]** om dit blok toegankelijk van het pictogram van het verpersoonlijkingsgebiedtoevoeging te maken.
   * Selecteer zo nodig **[!UICONTROL The content of the personalization block depends upon the format]** om twee aparte blokken voor e-mails in HTML-indeling en blokken in tekstindeling te definiëren.

      Er worden dan twee tabbladen weergegeven in de onderste sectie van deze editor (HTML-inhoud en tekstinhoud) om de bijbehorende inhoud te definiëren.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Voer de inhoud in (in HTML, tekst, JavaScript, enz.) van het (de) verpersoonlijkingsblok(ken) en klik **[!UICONTROL Save]**.

## Video over zelfstudie {#personalization-blocks-video}

Leer hoe u dynamische inhoudsblokken maakt en hoe u deze kunt gebruiken om de inhoud van uw e-maillevering aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
