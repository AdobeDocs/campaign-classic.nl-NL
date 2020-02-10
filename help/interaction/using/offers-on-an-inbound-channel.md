---
title: Aanbiedingen op een binnenkomend kanaal
seo-title: Aanbiedingen op een binnenkomend kanaal
description: Aanbiedingen op een binnenkomend kanaal
seo-description: null
page-status-flag: never-activated
uuid: 45cfc990-da38-451b-b65e-e9703e443a4d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 63245348-0402-4929-9c4f-71f01f97758e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Aanbiedingen op een binnenkomend kanaal{#offers-on-an-inbound-channel}

## Een voorstel aan een anonieme bezoeker presenteren {#presenting-an-offer-to-an-anonymous-visitor}

De Neobank-site wil op zijn website een aanbieding weergeven die gericht is op onbekende bezoekers die door de pagina bladeren.

Om deze interactie op te zetten, gaan we:

1. [Maak een anonieme omgeving](#creating-an-anonymous-environment).
1. [Maak anonieme aanbiedingsruimten](#creating-anonymous-offer-spaces).
1. [Maak een aanbiedingscategorie en een thema.](#creating-an-offer-category-and-a-theme).
1. [Anonieme aanbiedingen maken.](#creating-anonymous-offers).
1. [Configureer de webaanbiedingsruimten op de website](#configure-the-web-offer-space-on-the-website).

### Een anonieme omgeving maken {#creating-an-anonymous-environment}

Volg de procedure die in het [Creëren van een aanbiedingsmilieu](../../interaction/using/live-design-environments.md#creating-an-offer-environment) wordt beschreven om uw anonieme milieu tot stand te brengen die op de afmetingen van de **Bezoekers** wordt gebaseerd.

U krijgt een boomstructuur met uw nieuwe omgeving:

![](assets/offer_env_anonymous_003.png)

### Anonieme aanbiedingsruimten maken {#creating-anonymous-offer-spaces}

1. Ga in uw anonieme omgeving (**Bezoekers**) naar het **[!UICONTROL Administration]** >- **[!UICONTROL Spaces]** knooppunt.
1. Klik **[!UICONTROL New]** om vraagkanalen tot stand te brengen.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >De ruimte wordt automatisch gekoppeld aan de anonieme omgeving.

1. Wijzig het label en selecteer het **[!UICONTROL Inbound Web]** kanaal. U moet ook het **[!UICONTROL Enable unitary mode]** selectievakje inschakelen.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. Selecteer de velden voor aanbiedingsinhoud die voor de ruimte worden gebruikt en geef deze desgewenst op door het desbetreffende vak in te schakelen.

   Op die manier komen alle aanbiedingen die een van de volgende elementen missen, niet in aanmerking voor deze ruimte:

   * Titel
   * HTML-inhoud
   * URL afbeelding
   * Doel-URL.
   ![](assets/offer_inbound_anonymous_example_030.png)

1. Bewerk de HTML-renderfunctie, bijvoorbeeld als volgt:

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!CAUTION]
   >
   >De renderfunctie moet de velden die voor de ruimte worden gebruikt een naam geven in de volgorde waarin deze eerder zijn geselecteerd, zodat de aanbiedingen correct worden weergegeven.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. Bespaar de ruimte voor het voorstel.

### Een aanbiedingscategorie en een thema maken {#creating-an-offer-category-and-a-theme}

1. Ga naar het **[!UICONTROL Offer catalog]** knooppunt in de omgeving die u zojuist hebt gemaakt.
1. Klik met de rechtermuisknop op het **[!UICONTROL Offer catalog]** knooppunt en selecteer **[!UICONTROL Create a new 'Offer category' folder]**.

   Geef de nieuwe categorie bijvoorbeeld de naam **Financiële producten** .

1. Ga naar het **[!UICONTROL Eligibility]** tabblad van de categorie en voer **financiering** in als thema en sla de wijzigingen op.

   ![](assets/offer_inbound_anonymous_example_023.png)

### Anonieme aanbiedingen maken {#creating-anonymous-offers}

1. Ga naar de rubriek die je zojuist hebt gemaakt.
1. Klik **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. Selecteer het anonieme aanbiedingstemplate uit de doos of een eerder gemaakte sjabloon.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. Wijzig het label en sla je voorstel op.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en geef het gewicht van de aanbiedingen op volgens de toepassingscontext.

   In dit voorbeeld, wordt de aanbieding gevormd om op de homepage van de plaats als prioriteit tot het eind van het jaar worden getoond.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. Ga naar het **[!UICONTROL Content]** tabblad en definieer de inhoud van de aanbieding.

   >[!NOTE]
   >
   >U kunt selecteren **[!UICONTROL Content definitions]** om de lijst van elementen te tonen die voor de Webruimte worden vereist.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. Maak een tweede voorstel.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en pas hetzelfde gewicht toe als voor de eerste aanbieding.
1. Voer de goedkeuringscyclus voor elke aanbieding uit om deze, evenals de goedgekeurde aanbiedingsruimten, beschikbaar te maken in de online omgeving.

### Webaanbiedingsruimte op de website configureren {#configure-the-web-offer-space-on-the-website}

Als u de aanbiedingen die u net hebt geconfigureerd zichtbaar wilt maken op de website, voegt u een JavaScript-code in op de HTML-pagina van uw site om de Interactie-engine op te roepen (zie voor meer informatie [over binnenkomende kanalen](../../interaction/using/about-inbound-channels.md)).

1. Ga naar de HTML-pagina en voeg een @id-kenmerk in met een waarde die overeenkomt met de interne naam van de anonieme aanbiedingsruimte die eerder is gemaakt (zie [Anonieme aanbiedingsruimten](#creating-anonymous-offer-spaces)maken), voorafgegaan door **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. Voeg de URL van de aanroep in.

   ![](assets/offer_inbound_anonymous_example_020.png)

   De blauwe URL-vakken hierboven komen overeen met de instantienaam, de interne naam van de omgeving (zie [Een anonieme omgeving](#creating-an-anonymous-environment)maken) en het thema dat aan de categorie is gekoppeld (een aanbiedingencategorie en een thema[](#creating-an-offer-category-and-a-theme)maken). De laatste optie is facultatief.

Wanneer een bezoeker de homepage van de website opent, worden de aanbiedingen met het **financieringsthema** getoond zoals gevormd op de HTML- pagina.

![](assets/offer_inbound_anonymous_example_022.png)

Een gebruiker die de pagina meerdere keren bezoekt, ziet een van beide aanbiedingen in de categorie omdat aan beide hetzelfde gewicht is toegewezen.

## Overschakelen op een anonieme omgeving in het geval van niet-geïdentificeerde contacten {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Het Neobank-bedrijf wil marketingaanbiedingen voor twee verschillende doelen maken. Het wil algemene aanbiedingen voor zijn anonieme websitebrowsers tonen. Als één van deze gebruikers een klant met herkenningstekens blijkt te zijn die door Neobank worden verstrekt, zou het bedrijf hen willen om gepersonaliseerde aanbiedingen te ontvangen zodra zij login.

Deze casestudy is gebaseerd op het volgende scenario:

1. Een bezoeker bladert door de Neobank-website zonder u aan te melden.

   ![](assets/offer_inbound_fallback_example_050.png)

   Er worden drie anonieme voorstellen weergegeven op de pagina: twee **beste aanbiedingen** voor Neobank producten en één aanbieding van een Neobank partner.

   ![](assets/offer_inbound_fallback_example_051.png)

1. De gebruiker, een Neobank klant, logt met zijn geloofsbrieven aan.

   ![](assets/offer_inbound_fallback_example_052.png)

   Er worden drie persoonlijke aanbiedingen weergegeven.

   ![](assets/offer_inbound_fallback_example_053.png)

Voor de implementatie van deze casestudy hebt u twee omgevingen nodig die u kunt bieden: één voor anonieme interactie en één met aanbiedingen die vooral voor geïdentificeerde contacten worden gevormd. Het geïdentificeerde aanbiedingsmilieu zal worden gevormd om aan het anonieme aanbiedingsmilieu automatisch over te schakelen als het contact niet wordt het programma geopend en daarom niet wordt geïdentificeerd.

Voer de volgende stappen uit:

* Maak een catalogus met aanbiedingen die specifiek zijn voor anonieme binnenkomende interacties door de volgende stappen uit te voeren:

   1. [Een omgeving voor anonieme contactpersonen maken](#creating-an-environment-for-anonymous-contacts)
   1. [Het vormen aanbiedingsruimten voor het anonieme milieu](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [Aanbiedingscategorieën maken in een anonieme omgeving](#creating-offer-categories-in-an-anonymous-environment)
   1. [Aanbiedingen maken voor anonieme bezoekers](#creating-offers-for-anonymous-visitors)

* Maak een catalogus met aanbiedingen die specifiek zijn voor geïdentificeerde binnenkomende interacties met behulp van de volgende stappen:

   1. [Vorm de aanbiedingsruimten in het geïdentificeerde milieu](#configure-the-offer-spaces-in-the-identified-environment)
   1. [Aanbiedingscategorieën maken in een geïdentificeerde omgeving](#creating-offer-categories-in-an-identified-environment)
   1. [Aangepaste aanbiedingen maken](#creating-personalized-offers)

* Vorm de vraag aan de aanbiedingsmotor:

   1. [Aanbiedingsruimten op de webpagina configureren](#configuring-offer-spaces-on-the-web-page)
   1. [De geavanceerde instellingen van de opgegeven aanbiedingsruimten opgeven](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### Een omgeving voor anonieme contactpersonen maken {#creating-an-environment-for-anonymous-contacts}

1. Creeer een aanbiedingsmilieu voor anonieme binnenkomende interacties via de tovenaar van de leveringstoewijzing (**afbeelding van de Bezoeker** ). Raadpleeg [Een aanbiedingsomgeving](../../interaction/using/live-design-environments.md#creating-an-offer-environment)maken voor meer informatie hierover.

   ![](assets/offer_env_anonymous_003.png)

### Het vormen aanbiedingsruimten voor het anonieme milieu {#configuring-offer-spaces-for-the-anonymous-environment}

De aanbiedingen die op de website moeten worden gepresenteerd, behoren tot twee verschillende categorieën: **Beste voorstel** en **Partner**. In dit voorbeeld maken we een specifieke aanbiedingsruimte voor elke categorie.

Pas het volgende proces toe om de aanbiedingsruimte aan te passen aan de **rubriek Beste voorstel** :

1. Ga in de Adobe Campagne-structuur naar de anonieme omgeving die u zojuist hebt gemaakt en voeg een aanbiedingsruimte toe.

   ![](assets/offer_inbound_fallback_example_023.png)

1. Maak een nieuwe **[!UICONTROL Inbound web]** tekstruimte.

   ![](assets/offer_inbound_fallback_example_024.png)

1. Voer een label in voor dit item: Beste anonieme **webaanbieding** bijvoorbeeld.
1. Voeg de velden met aanbiedingsinhoud die voor deze aanbiedingsruimte worden gebruikt toe en configureer de renderfuncties.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!CAUTION]
   >
   >De renderfunctie moet de velden die voor de ruimte worden gebruikt een naam geven in de volgorde waarin deze eerder zijn geselecteerd, zodat de aanbiedingen correct worden weergegeven.

1. Gebruik het zelfde proces om een binnenkomend Webkanaalaanbiedingsruimte tot stand te brengen om de categorie van de **Partner** aan te passen.

   ![](assets/offer_inbound_fallback_example_026.png)

### Aanbiedingscategorieën maken in een anonieme omgeving {#creating-offer-categories-in-an-anonymous-environment}

Begin met het maken van twee categorieën voorstellen: de categorie **Beste voorstel** en de categorie **Partner** . Elke categorie zal twee aanbiedingen voor anonieme contacten bevatten.

1. Ga naar de **[!UICONTROL Offer catalog]** anonieme omgeving die je net hebt gemaakt.
1. Voeg een **[!UICONTROL Offer category]** map met **Beste voorstel** als label toe.

   ![](assets/offer_inbound_fallback_example_027.png)

1. Creeer een tweede categorie met **Partner** als etiket.

   ![](assets/offer_inbound_fallback_example_028.png)

### Aanbiedingen maken voor anonieme bezoekers {#creating-offers-for-anonymous-visitors}

We gaan nu twee aanbiedingen maken voor elk van de hierboven geschetste rubrieken.

1. Ga naar de rubriek **Beste voorstel** en maak een anoniem voorstel.

   ![](assets/offer_inbound_fallback_example_029.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en geef het gewicht van de aanbiedingen op volgens de toepassingscontext.

   ![](assets/offer_inbound_fallback_example_030.png)

1. Ga naar het **[!UICONTROL Content]** tabblad en definieer de inhoud van de aanbieding.

   ![](assets/offer_inbound_fallback_example_032.png)

1. Maak een tweede voorstel in de rubriek **Beste voorstel** .

   ![](assets/offer_inbound_fallback_example_031.png)

1. Ga naar de categorie **Partner** en creeer een anonieme aanbieding.
1. Ga naar het **[!UICONTROL Content]** tabblad en definieer de inhoud van de aanbieding.

   ![](assets/offer_inbound_fallback_example_033.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en geef het gewicht van de aanbiedingen op volgens de toepassingscontext.

   ![](assets/offer_inbound_fallback_example_034.png)

1. Creeer een tweede aanbieding voor de categorie van de **Partner** .

   ![](assets/offer_inbound_fallback_example_035.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en pas het gewicht toe dat u op de eerste aanbieding in deze categorie hebt toegepast, zodat de aanbiedingen achtereenvolgens op de website worden weergegeven.

   ![](assets/offer_inbound_fallback_example_036.png)

1. Voer de goedkeuringscyclus voor elke aanbieding uit om ze live te laten gaan. Wanneer het goedkeuren van inhoud, activeer de **Partner** of de **Beste aanbieding** van de Aanbieding, volgens de aanbieding.

### Vorm de aanbiedingsruimten in het geïdentificeerde milieu {#configure-the-offer-spaces-in-the-identified-environment}

De voorstellen die u op de website gaat presenteren, zijn afkomstig uit twee verschillende categorieën: **Beste voorstel** en **Partner**. In dit voorbeeld willen we een specifieke spatie maken voor elke categorie.

Om de twee aanbiedingsruimten tot stand te brengen, pas de zelfde procedure toe zoals voor anonieme aanbiedingsruimten. Verwijs naar het [Vormen aanbiedingsruimten voor het anonieme milieu](#configuring-offer-spaces-for-the-anonymous-environment).

1. Ga in de Adobe Campaign-structuur naar de omgeving die u net hebt gemaakt en voeg **Beste voorstel** en **Partner** -aanbiedingsruimten toe.
1. Pas het proces toe dat in het [Vormen aanbiedingsruimten voor het anonieme milieu](#configuring-offer-spaces-for-the-anonymous-environment)wordt gedetailleerd.

   ![](assets/offer_inbound_fallback_example_005.png)

1. Selecteer de **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** optie.

   ![](assets/offer_inbound_fallback_example_006.png)

1. Gebruikend de drop-down lijst, selecteer de anonieme eerder gecreeerd ruimte van de Webaanbieding (verwijs naar het [Vormen aanbiedingsruimten voor het anonieme milieu](#configuring-offer-spaces-for-the-anonymous-environment)).

   ![](assets/offer_inbound_fallback_example_007.png)

### De geavanceerde instellingen van de opgegeven aanbiedingsruimten opgeven {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

In dit voorbeeld vindt de identificatie van de contactpersoon plaats via het e-mailadres in de Adobe Campaign-database. Pas het volgende proces toe om de e-mail voor ontvangers aan de ruimte toe te voegen:

1. Ga in de geïdentificeerde omgeving naar de map met aanbiedingsruimte.
1. Selecteer de ruimte voor **beste voorstel** en klik op **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. Klik op het **[!UICONTROL Target identification]** tabblad op **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. Klik, ga **[!UICONTROL Edit expression]** naar de lijst van ontvangers en selecteer het **[!UICONTROL Email]** gebied.

   ![](assets/offer_inbound_fallback_example_047.png)

1. Klik **[!UICONTROL OK]** om het **[!UICONTROL Advanced parameters]** venster te sluiten en klaar te zijn met het configureren van de ruimte voor **beste voorstel** .
1. Pas het zelfde proces voor de **Partner** aan aanbiedingsruimte toe.

   ![](assets/offer_inbound_fallback_example_048.png)

### Aanbiedingscategorieën maken in een geïdentificeerde omgeving {#creating-offer-categories-in-an-identified-environment}

We gaan twee aparte categorieën maken: de categorie **Beste voorstel** en de categorie **Partner** , elk met twee gepersonaliseerde aanbiedingen.

1. Ga naar het **[!UICONTROL Offer catalogs]** knooppunt in de geïdentificeerde omgeving.
1. Zoals in het anonieme milieu, voeg twee **[!UICONTROL Offer category]** omslagen met **Beste Aanbieding** en **Partner** als etiketten toe.

   ![](assets/offer_inbound_fallback_example_009.png)

### Aangepaste aanbiedingen maken {#creating-personalized-offers}

We willen voor elke categorie twee persoonlijke aanbiedingen maken, dat wil zeggen vier aanbiedingen.

1. Ga naar de rubriek **Beste voorstel** en maak een eerste persoonlijke aanbieding.

   ![](assets/offer_inbound_fallback_example_011.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en geef het gewicht van de aanbiedingen op volgens de toepassingscontext.

   ![](assets/offer_inbound_fallback_example_012.png)

1. Ga naar het **[!UICONTROL Content]** tabblad en definieer de inhoud van de aanbieding.

   ![](assets/offer_inbound_fallback_example_013.png)

1. Maak een tweede voorstel in de rubriek **Beste voorstel** .

   ![](assets/offer_inbound_fallback_example_014.png)

1. Ga naar de categorie **Partner** en creeer een gepersonaliseerde aanbieding.

   ![](assets/offer_inbound_fallback_example_015.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en geef het gewicht van de aanbiedingen op volgens de toepassingscontext.

   ![](assets/offer_inbound_fallback_example_016.png)

1. Creeer een tweede aanbieding voor de categorie van de **Partner** .

   ![](assets/offer_inbound_fallback_example_017.png)

1. Ga naar het **[!UICONTROL Eligibility]** tabblad en pas het gewicht toe dat u op de eerste aanbieding in deze categorie hebt toegepast, zodat de aanbiedingen achtereenvolgens op de website worden weergegeven.
1. Voer de goedkeuringscyclus voor elke aanbieding uit om deze bij te werken. Tijdens inhoudsgoedkeuring, activeer de **Partner** of de **Beste aanbieding** ruimten.

### Aanbiedingsruimten op de webpagina configureren {#configuring-offer-spaces-on-the-web-page}

Op de website van Neobank vindt u drie mogelijkheden: twee voor aan banken gerelateerde aanbiedingen uit de categorie **Beste voorstel** en één voor aanbiedingen uit de categorie **Partner** .

![](assets/offer_inbound_fallback_example_038.png)

Pas het volgende proces toe om deze aanbiedingsruimten op de HTML-pagina van de website te configureren:

1. Voeg in de inhoud van de HTML-pagina drie in

   elementen met een kenmerk @id waarvan de waarde ons in staat stelt de aanbiedingen op te roepen in de verschillende aanbiedingsruimten van de website.

   ![](assets/offer_inbound_fallback_example_039.png)

1. Voeg vervolgens het script in voor het definiëren van kenmerkwaarden.

   ![](assets/offer_inbound_fallback_example_040.png)

   In dit voorbeeld ontvangen **ContBO1** en **ContBO2** de waarde **OsWebBestOfferIdentified**, d.w.z. de interne naam van de **Beste aanbieding** ruimte die eerder in het geïdentificeerde milieu wordt gecreeerd. De waarden **CatBestOffer** en **CatBestOfferAnoniem** komen overeen met de interne naam van de categorieën **Beste voorstel** voor anonieme en geïdentificeerde omgevingen.

   ![](assets/offer_inbound_fallback_example_041.png)

   Eveneens, ontvangt **ContPtn** de **waarde OSWebPartnerIdentified** , die de interne naam van de **Partner** aanbiedt ruimte die in het geïdentificeerde milieu wordt gecreeerd. **CatPartner** en **CatPartnerAnonym** passen de interne naam van de categorieën van de **Partner** voor anonieme en geïdentificeerde milieu&#39;s aan.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Wijs de informatie toe die u de persoon zal identificeren die aan de Neobank plaats aan de **interactionTarget** variabele het programma opent.

   ![](assets/offer_inbound_fallback_example_043.png)

   De identificatie van de persoon kan op een browser koekje, een lezingsparameter in URL, e-mail, of herkenningsteken van de persoon worden gebaseerd. Als een gebied van de ontvankelijke lijst buiten de primaire sleutel wordt gebruikt, moet het in de geavanceerde parameters van de ruimte worden bepaald (verwijs naar het [Specificeren van de geavanceerde montages van de geïdentificeerde aanbiedingsruimten](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. Voeg de URL van de aanroep in.

   ![](assets/offer_inbound_fallback_example_049.png)

   De URL bevat **EnvNeobankRecip**, de interne naam van de geïdentificeerde omgeving.

Wanneer u de webpagina opent; Met het script kunt u de Interactie-engine opvragen om de inhoud van aanbiedingen in de relevante ruimten van de webpagina weer te geven. Bij één aanroep naar de Adobe Campagneserver bepaalt de engine de omgeving, de aanbiedingsruimte en de categorieën die moeten worden geselecteerd.

In dit voorbeeld herkent de engine de geïdentificeerde omgeving (**EnvNeobankIdnRecip**). Het identificeert de aanbiedingsruimte (**OSWebBestOfferIdentified**) en de categorie **Beste aanbieding** (**CatBestOffer**) voor de eerste en tweede aanbiedingsruimten op de Web-pagina, evenals (**OSWebPartnerIdentified**) aanbieden ruimte en de **Partner****** categorie (het bevestigen van de PartnerPartner) de derde aanbiedingsruimte op de site.

Als de motor niet de ontvanger kan identificeren, schakelt het aan de anonieme aanbiedingsruimten van verwijzingen voorzien in de geïdentificeerde aanbiedingsruimten en naar de anonieme categorieën (**CatPartner** en **CatPartnerAnoniem**) zoals die in het manuscript worden gespecificeerd.
