---
product: campaign
title: Personalisatieblokken
description: Leer hoe u aanpassingsblokken kunt gebruiken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Personalization
role: User
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 1%

---

# Personalisatieblokken{#personalization-blocks}

De blokken van de verpersoonlijking zijn dynamisch, gepersonaliseerd en bevatten een specifiek teruggeven dat u in uw leveringen kunt opnemen. U kunt bijvoorbeeld een logo, een begroetingsbericht of een koppeling naar een spiegelpagina toevoegen. Zie [ verpersoonlijkingsblokken van het Tussenvoegsel ](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png) ontdekt deze eigenschap [ in video ](#personalization-blocks-video)

U hebt toegang tot aanpassingsblokken via het knooppunt **[!UICONTROL Resources > Campaign Management > Personalization blocks]** van de Adobe Campaign-verkenner. Verscheidene blokken zijn beschikbaar door gebrek (zie [ uit-van-de-doos verpersoonlijkingsblokken ](#out-of-the-box-personalization-blocks)).

U hebt de mogelijkheid om nieuwe blokken te definiëren waarmee u de personalisatie van uw leveringen kunt optimaliseren. Voor meer op dit, verwijs naar [ de blokken van de douaneverpersoonlijking ](#defining-custom-personalization-blocks) bepalen.

>[!NOTE]
>
>U kunt ook aanpassingsblokken gebruiken via **[!UICONTROL Digital Content Editor (DCE)]** . Raadpleeg [deze pagina](../../web/using/editing-content.md#inserting-a-personalization-block) voor meer informatie.

## Verpersoonlijkingsblokken invoegen {#inserting-personalization-blocks}

Volg onderstaande stappen om een verpersoonlijkingsblok in te voegen in een bericht:

1. Klik in de inhoudseditor van de bezorgingsassistent op het pictogram van een gepersonaliseerd veld en selecteer het menu **[!UICONTROL Include]** .
1. Selecteer een verpersoonlijkingsblok in de lijst (in de lijst worden de tien laatst gebruikte blokken weergegeven) of klik op het menu **[!UICONTROL Other...]** om de volledige lijst te openen.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Het **[!UICONTROL Other...]** menu geeft toegang tot alle uit-van-de-doos en douane verpersoonlijkingsblokken (zie [ uit-van-de-doos verpersoonlijkingsblokken ](#out-of-the-box-personalization-blocks) en [ bepalen de blokken van de douaneverpersoonlijking ](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Het verpersoonlijkingsblok wordt dan opgenomen als manuscript. Het wordt automatisch aangepast aan het ontvankelijke profiel wanneer de verpersoonlijking wordt geproduceerd.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klik op het tabblad **[!UICONTROL Preview]** en selecteer een ontvanger om de personalisatie weer te geven.

   ![](assets/s_ncs_user_personalized_block04.png)

U kunt de broncode van een verpersoonlijkingsblok in de leveringsinhoud omvatten. Selecteer **[!UICONTROL Include the HTML source code of the block]** wanneer u dit wilt doen.

![](assets/s_ncs_user_personalized_block05.png)

De broncode van de HTML wordt opgenomen in de leveringsinhoud. Het **[!UICONTROL Greetings]** verpersoonlijkingsblok wordt bijvoorbeeld als volgt weergegeven:

![](assets/s_ncs_user_personalized_block06.png)

## Voorbeeld van aanpassingsblokken {#personalization-blocks-example}

In dit voorbeeld maken we een e-mail waarin we personalisatieblokken gebruiken om de ontvanger in staat te stellen de spiegelpagina te bekijken, de nieuwsbrief te delen op sociale netwerken en ons af te melden voor toekomstige leveringen.

Om dit te doen, moeten wij de volgende verpersoonlijkingsblokken opnemen:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Voor meer op de spiegelpaginageneratie, verwijs naar [ produceer de spiegelpagina ](sending-messages.md#generating-the-mirror-page).

1. Maak een nieuwe levering of open een bestaande e-maillevering.
1. Klik in de bezorgingsassistent op **[!UICONTROL Subject]** om het onderwerp van het bericht te bewerken en een onderwerp in te voeren.
1. Neem de verpersoonlijkingsblokken in het berichtlichaam op. Klik hiertoe in de berichtinhoud, klik op het pictogram van het gepersonaliseerde veld en selecteer het menu **[!UICONTROL Include]** .
1. Selecteer het eerste blok dat u wilt invoegen. Vernieuw de procedure om de twee andere blokken op te nemen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klik op het tabblad **[!UICONTROL Preview]** om het resultaat van de aanpassing weer te geven. U moet een ontvanger selecteren om het bericht van die ontvanger te tonen.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Controleer of de inhoud van het blok correct wordt weergegeven.

## Buiten-de-doos verpersoonlijkingsblokken {#out-of-the-box-personalization-blocks}

Een lijst van verpersoonlijkingsblokken is beschikbaar door gebrek om u te helpen de inhoud van uw bericht personaliseren.

>[!NOTE]
>
>De lijst van verpersoonlijkingsblokken hangt van de modules en de opties af die op uw instantie zijn geïnstalleerd.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : voegt begroetingen in met de naam van de ontvanger. Voorbeeld: &quot;Hello John Doe,&quot;.
* **[!UICONTROL Insert logo]** : voegt een out-of-the-box logo in dat is gedefinieerd tijdens het configureren van de instantie.
* **[!UICONTROL Powered by Adobe Campaign]** : voegt het logo &quot;Powered by Adobe Campaign&quot; in.
* **[!UICONTROL Mirror page URL]** : voegt de URL van de spiegelpagina in, zodat de leveringsontwerpers de koppeling kunnen controleren.

  >[!NOTE]
  >
  >Voor meer op de spiegelpaginageneratie, verwijs naar [ produceer de spiegelpagina ](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : voegt een koppeling naar de spiegelpagina in: &quot;Als u dit bericht niet correct kunt weergeven, klikt u hier&quot;.
* **[!UICONTROL Unsubscription link]** : voegt een koppeling in waarmee u zich kunt afmelden bij alle leveringen (lijst van gewezen personen).
* **[!UICONTROL Formatting function for proper nouns]** : genereert de functie **[!UICONTROL toSmartCase]** Javascript, die de eerste letter van elk woord in hoofdletters wijzigt.
* **[!UICONTROL Registration page URL]** : neemt een abonnement URL op (zie [ Ongeveer de diensten en abonnementen ](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : voegt een abonnementkoppeling in. die is gedefinieerd tijdens het configureren van de instantie.
* **[!UICONTROL Registration link (with referrer)]** : voegt een abonnementkoppeling in, waarmee de bezoeker en de levering kunnen worden geïdentificeerd. De koppeling is gedefinieerd tijdens het configureren van de instantie.

  >[!NOTE]
  >
  >Dit blok kan alleen worden gebruikt bij leveringen voor bezoekers.

* **[!UICONTROL Registration confirmation]** : voegt een koppeling in waarmee het abonnement kan worden bevestigd.
* **[!UICONTROL Social network sharing links]** : neemt knopen op die de ontvanger toelaten om een verbinding met de inhoud van de spiegelpagina met de e-mailcliënt, Facebook, X (vroeger genoemd als Twitter), en LinkedIn (zie [ Virale marketing: door:sturen aan een vriend ](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)) te delen.
* **[!UICONTROL Style of content emails]** en **[!UICONTROL Notification style]** : genereer code waarmee een e-mailbericht wordt opgemaakt met vooraf gedefinieerde stijlen voor HTML. Deze blokken moeten in de broncode van de levering, in de **[!UICONTROL ...]** sectie, in **`<style>...</style>`** markeringen worden opgenomen.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : neemt een URL op toelatend om een aanbieding van de Interactie aan **[!UICONTROL Accepted]** (zie [ deze sectie ](../../interaction/using/offer-analysis-report.md)) te plaatsen.

## Aangepaste aanpassingsblokken definiëren {#defining-custom-personalization-blocks}

Via het menu **[!UICONTROL Include...]** kunt u nieuwe aanpassingsvelden definiëren die via het pictogram voor gepersonaliseerde velden moeten worden ingevoegd. Deze gebieden worden bepaald in verpersoonlijkingsblokken.

Ga naar de verkenner en voer de volgende stappen uit om een verpersoonlijkingsblok te maken:

1. Klik op het knooppunt **[!UICONTROL Resources > Campaign Management > Personalization blocks]** .
1. Klik met de rechtermuisknop op de lijst met blokken en selecteer **[!UICONTROL New]** .
1. Vul de instellingen van het verpersoonlijkingsblok in:

   ![](assets/s_ncs_user_personalized_block.png)

   * Voer het label van het blok in. Dit label wordt weergegeven in het invoegvenster van het aanpassingsveld.
   * Selecteer **[!UICONTROL Visible in the customization menus]** om dit blok toegankelijk te maken via het invoegpictogram voor het aanpassingsveld.
   * Selecteer indien nodig **[!UICONTROL The content of the personalization block depends upon the format]** om twee aparte blokken voor e-mailberichten in de indeling HTML en tekstblokken in de indeling te definiëren.

     Er worden dan twee tabbladen weergegeven in de onderste sectie van deze editor (inhoud van HTML en tekst) om de bijbehorende inhoud te definiëren.

     ![](assets/s_ncs_user_personalized_block_b.png)

   * Voer de inhoud in (in HTML, tekst, JavaScript, enz.) van de aanpassingsblokken en klik op **[!UICONTROL Save]** .

## Video over zelfstudie {#personalization-blocks-video}

Leer hoe u dynamische inhoudsblokken maakt en hoe u deze kunt gebruiken om de inhoud van uw e-maillevering aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

De extra Campaign Classic hoe te video&#39;s zijn beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
