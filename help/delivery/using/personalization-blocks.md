---
product: campaign
title: Personalisatieblokken
description: Personalisatieblokken
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 2%

---

# Personalisatieblokken{#personalization-blocks}

![](../../assets/common.svg)

De blokken van de verpersoonlijking zijn dynamisch, gepersonaliseerd en bevatten een specifiek teruggeven dat u in uw leveringen kunt opnemen. U kunt bijvoorbeeld een logo, een begroetingsbericht of een koppeling naar een spiegelpagina toevoegen. Zie [Aanmaakblokken invoegen](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Ontdek deze functie in video](#personalization-blocks-video)

Personaliseringsblokken zijn toegankelijk via de **[!UICONTROL Resources > Campaign Management > Personalization blocks]** knooppunt van de Adobe Campaign Explorer. Verschillende blokken zijn standaard beschikbaar (zie [Buiten-de-doos verpersoonlijkingsblokken](#out-of-the-box-personalization-blocks)).

U hebt de mogelijkheid om nieuwe blokken te definiëren waarmee u uw leveringen kunt optimaliseren. Raadpleeg voor meer informatie hierover [Aangepaste aanpassingsblokken definiëren](#defining-custom-personalization-blocks).

>[!NOTE]
>
>De blokken van de verpersoonlijking zijn ook beschikbaar bij **[!UICONTROL Digital Content Editor (DCE)]** . Raadpleeg [deze pagina](../../web/using/editing-content.md#inserting-a-personalization-block) voor meer informatie.

## Aanmaakblokken invoegen {#inserting-personalization-blocks}

Volg onderstaande stappen om een verpersoonlijkingsblok in te voegen in een bericht:

1. Klik in de inhoudseditor van de wizard voor levering op het pictogram van een gepersonaliseerd veld en selecteer het pictogram **[!UICONTROL Include]** -menu.
1. Selecteer een verpersoonlijkingsblok in de lijst (in de lijst staan de tien laatst gebruikte blokken) of klik op de knop **[!UICONTROL Other...]** voor toegang tot de volledige lijst.

   ![](assets/s_ncs_user_personalized_block01.png)

1. De **[!UICONTROL Other...]** geeft toegang tot alle uit-van-de-doos en douane verpersoonlijkingsblokken (zie [Buiten-de-doos verpersoonlijkingsblokken](#out-of-the-box-personalization-blocks) en [Aangepaste aanpassingsblokken definiëren](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Het verpersoonlijkingsblok wordt dan opgenomen als manuscript. Het wordt automatisch aangepast aan het ontvankelijke profiel wanneer de verpersoonlijking wordt geproduceerd.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klik op de knop **[!UICONTROL Preview]** en selecteert u een ontvanger om de personalisatie weer te geven.

   ![](assets/s_ncs_user_personalized_block04.png)

U kunt de broncode van een verpersoonlijkingsblok in de leveringsinhoud omvatten. Selecteer **[!UICONTROL Include the HTML source code of the block]** wanneer u het selecteert.

![](assets/s_ncs_user_personalized_block05.png)

De broncode van de HTML wordt opgenomen in de leveringsinhoud. De **[!UICONTROL Greetings]** de vertoningen van het verpersoonlijkingsblok zoals hieronder:

![](assets/s_ncs_user_personalized_block06.png)

## Voorbeeld van aanpassingsblokken {#personalization-blocks-example}

In dit voorbeeld maken we een e-mail waarin we personalisatieblokken gebruiken om de ontvanger in staat te stellen de spiegelpagina te bekijken, de nieuwsbrief te delen op sociale netwerken en ons af te melden voor toekomstige leveringen.

Om dit te doen, moeten wij de volgende verpersoonlijkingsblokken opnemen:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Raadpleeg voor meer informatie over het genereren van spiegelpagina&#39;s [De spiegelpagina genereren](sending-messages.md#generating-the-mirror-page).

1. Maak een nieuwe levering of open een bestaande e-maillevering.
1. Klik in de wizard voor levering op **[!UICONTROL Subject]** om het onderwerp van het bericht te bewerken en een onderwerp in te voeren.
1. Neem de verpersoonlijkingsblokken in het berichtlichaam op. Om dit te doen, klik in de berichtinhoud, klik het gepersonaliseerde gebiedspictogram en selecteer **[!UICONTROL Include]** -menu.
1. Selecteer het eerste blok dat u wilt invoegen. Vernieuw de procedure om de twee andere blokken op te nemen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klik op de knop **[!UICONTROL Preview]** om het verpersoonlijkingsresultaat weer te geven. U moet een ontvanger selecteren om het bericht van die ontvanger te tonen.

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
   >Raadpleeg voor meer informatie over het genereren van spiegelpagina&#39;s [De spiegelpagina genereren](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : voegt een koppeling naar de spiegelpagina in: &quot;Klik hier als je dit bericht niet juist kunt weergeven.&quot;
* **[!UICONTROL Unsubscription link]** : voegt een koppeling in waarmee u zich kunt afmelden bij alle leveringen (lijst van gewezen personen).
* **[!UICONTROL Formatting function for proper nouns]** : genereert de **[!UICONTROL toSmartCase]** De functie Javascript, die de eerste letter van elk woord in hoofdletters verandert.
* **[!UICONTROL Registration page URL]** : voegt een abonnement-URL in (zie [Informatie over services en abonnementen](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : voegt een abonnementkoppeling in. die is gedefinieerd tijdens het configureren van de instantie.
* **[!UICONTROL Registration link (with referrer)]** : voegt een abonnementkoppeling in, waarmee de bezoeker en de levering kunnen worden geïdentificeerd. De koppeling is gedefinieerd tijdens het configureren van de instantie.

   >[!NOTE]
   >
   >Dit blok kan alleen worden gebruikt bij leveringen voor bezoekers.

* **[!UICONTROL Registration confirmation]** : voegt een koppeling in waarmee u het abonnement kunt bevestigen.
* **[!UICONTROL Social network sharing links]** : voegt knoppen in waarmee de ontvanger een koppeling naar de inhoud van de spiegel kan delen met de e-mailclient, Facebook, Twitter en LinkedIn (zie [Virale marketing: doorsturen naar een vriend](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** en **[!UICONTROL Notification style]** : genereren code waarmee een e-mailbericht wordt opgemaakt met vooraf gedefinieerde HTML-stijlen. Deze blokken moeten in de broncode van de levering, in worden opgenomen **[!UICONTROL ...]** sectie, naar **`<style>...</style>`** -tags.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : voegt een URL in waarmee een interactieaanbieding kan worden ingesteld op **[!UICONTROL Accepted]** (zie [deze sectie](../../interaction/using/offer-analysis-report.md)).

## Aangepaste aanpassingsblokken definiëren {#defining-custom-personalization-blocks}

U kunt nieuwe verpersoonlijkingsgebieden bepalen die van het gepersonaliseerde gebiedspictogram via worden opgenomen **[!UICONTROL Include...]** -menu. Deze gebieden worden bepaald in verpersoonlijkingsblokken.

Ga naar de verkenner en voer de volgende stappen uit om een verpersoonlijkingsblok te maken:

1. Klik op de knop **[!UICONTROL Resources > Campaign Management > Personalization blocks]** knooppunt.
1. Klik met de rechtermuisknop op de lijst met blokken en selecteer **[!UICONTROL New]** .
1. Vul de instellingen van het verpersoonlijkingsblok in:

   ![](assets/s_ncs_user_personalized_block.png)

   * Voer het label van het blok in. Dit label wordt weergegeven in het invoegvenster van het aanpassingsveld.
   * Selecteren **[!UICONTROL Visible in the customization menus]** om dit blok toegankelijk te maken vanaf het pictogram voor het invoegen van het aanpassingsveld.
   * Selecteer indien nodig **[!UICONTROL The content of the personalization block depends upon the format]** om twee aparte blokken voor e-mails in de indeling HTML en in de tekstindeling te definiëren.

      Er worden dan twee tabbladen weergegeven in de onderste sectie van deze editor (inhoud van HTML en tekst) om de bijbehorende inhoud te definiëren.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Voer de inhoud in (in HTML, tekst, JavaScript, enz.) van het (de) verpersoonlijkingsblok(ken) en klik op **[!UICONTROL Save]**.

## Video over zelfstudie {#personalization-blocks-video}

Leer hoe u dynamische inhoudsblokken maakt en hoe u deze kunt gebruiken om de inhoud van uw e-maillevering aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Er zijn aanvullende Campaign Classic-hoe-kan-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
