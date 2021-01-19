---
solution: Campaign Classic
product: campaign
title: Lidmaatschappen beheren
description: Lidmaatschappen beheren
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 2%

---


# Abonnementen beheren{#managing-subscriptions}

## Informatie over services {#about-information-services}

Een informatiedienst omvat:

* registratie en abonnement (opt-in),
* Deregistratie, vrijwillig afzien van abonnement (opt-out) of automatisch afzien van abonnement (beperkte-tijdservice, bijvoorbeeld als proefaanbieding);
* bevestigingsmechanismen voor abonnementen en abonnementen (eenvoudige mechanismen met bevestiging, dubbele aanmelding, enz.);
* Het volgen van abonneegeschiedenis.

Deze diensten omvatten standaard specifieke statistische rapporten: het volgen van abonnees, loyaliteitsniveau, uitstaptendensen, enz.

Voor e-mails worden de verplichte abonnementskoppelingen automatisch gegenereerd. De volledige procedure voor het in- en uitschakelen van e-mail verloopt volledig geautomatiseerd, waarbij de historie wordt bijgehouden zodat de geldende regels volledig worden nageleefd.

Er zijn drie modi voor abonnementen/abonnementen op services:

1. handmatig
1. door importeren (alleen abonnement),
1. via een webformulier

>[!NOTE]
>
>In [deze sectie](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in) wordt een voorbeeld gegeven voor het maken van een abonnementsformulier met dubbele aanmelding.

## Informatieservice {#creating-an-information-service} maken

U kunt abonnementen op informatiediensten met bijbehorende bevestigingsberichten of automatische leveringen aan abonnees tot stand brengen en beheren.

Ga naar het **[!UICONTROL Profiles and Targets]** universum en klik op de koppeling **[!UICONTROL Services and Subscriptions]** om de kaart met informatieservices te openen.

![](assets/s_ncs_user_services_new.png)

Als u een bestaande service wilt bewerken, klikt u op de naam van de service. Als u een service wilt maken, klikt u op de knop **[!UICONTROL Create]** boven de lijst.

![](assets/s_ncs_user_services_add.png)

* Voer in het veld **[!UICONTROL Label]** de naam van de service in en selecteer het leveringskanaal: e-mail-, mobiele, Facebook-, Twitter- of mobiele toepassingen.

   >[!NOTE]
   >
   >Facebook- en Twitter-abonnementen worden beschreven in [deze sectie](../../social/using/about-social-marketing.md). Abonnementen voor mobiele toepassingen worden beschreven in [Mobiel toepassingskanaal](../../delivery/using/about-mobile-app-channel.md).

* Voor een E-mailtypeservice selecteert u de **leveringsmodus**. De mogelijke modi zijn: **[!UICONTROL Newsletter]** of **[!UICONTROL Viral]**.
* U kunt **bevestigingsberichten** voor een abonnement of een unsubscription verzenden. Hiervoor selecteert u de leveringssjablonen die u wilt gebruiken om de corresponderende leveringen te maken in de velden **[!UICONTROL Subscription]** en **[!UICONTROL Unsubscription]**. Deze malplaatjes moeten met een **[!UICONTROL Subscription]** type doelafbeelding, zonder een bepaald doel worden gevormd. Zie sectie [Informatie over e-mailkanaal](../../delivery/using/about-email-channel.md).
* Abonnementen zijn standaard onbeperkt. U kunt de optie **[!UICONTROL Unlimited]** uitschakelen om een geldigheidsduur voor de service te definiëren. De duur kan worden opgegeven in dagen (**[!UICONTROL d]**) of maanden (**[!UICONTROL m]** ).

Zodra de dienst is opgeslagen, wordt het toegevoegd aan de lijst van de Diensten en van Abonnementen: Klik op de naam van het bestand om het te bewerken. Er zijn verschillende tabbladen beschikbaar. Op het tabblad **[!UICONTROL Subscriptions]** kunt u de lijst met abonnees van de informatieservice (**[!UICONTROL Active subscriptions]** tabblad) of de abonnements-/uitstapgeschiedenis (**[!UICONTROL History]** tabblad) bekijken. U kunt ook abonnees toevoegen en verwijderen van dit tabblad. Zie [Abonnees toevoegen en verwijderen](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Met de knop **[!UICONTROL Detail...]** kunt u de abonnementseigenschappen voor de geselecteerde ontvanger bekijken.

U kunt de abonnementseigenschappen voor een ontvanger wijzigen.

![](assets/s_ncs_user_services_modify.png)

Klik op het dashboard op het tabblad **[!UICONTROL Reports]** om abonnementen bij te houden: wijzigingen in het abonnementsniveau, het totale aantal abonnees, enz. U kunt rapporten archiveren en historie bekijken van dit lusje.

## Abonnees {#adding-and-deleting-subscribers} toevoegen en verwijderen

Klik op het tabblad **[!UICONTROL Subscriptions]** van een informatieservice op **[!UICONTROL Add]** om abonnees toe te voegen. U kunt ook met de rechtermuisknop op de lijst met abonnees klikken en **[!UICONTROL Add]** selecteren. Selecteer de map waarin de profielen zijn opgeslagen die u wilt abonneren, selecteer vervolgens de profielen die u wilt abonneren en klik op **[!UICONTROL OK]** om te valideren.

Als u abonnees wilt verwijderen, selecteert u deze en klikt u op **[!UICONTROL Delete]**. U kunt ook met de rechtermuisknop op de abonnementenlijst klikken en **[!UICONTROL Delete]** selecteren.

In beide gevallen kunt u een bevestigingsbericht naar de betrokken gebruikers sturen als er een leveringssjabloon voor abonnementen aan de service is gekoppeld (zie [Een informatieservice maken](#creating-an-information-service)). Met een waarschuwing kunt u deze levering valideren of niet valideren:

![](assets/s_ncs_user_services_update.png)

Zie [Abonnementsmechanismen](#subscription-and-unsubscription-mechanisms).

## Levering aan de abonnees van een dienst {#delivering-to-the-subscribers-of-a-service}

Om aan de abonnees van een informatiedienst te leveren, kunt u de abonnees aan de betrokken informatiedienst richten, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>De doelafbeelding moet **[!UICONTROL Subscriptions]** zijn.

Selecteer **[!UICONTROL Subscribers of an information service]** en klik op **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Selecteer de beoogde informatieservice en klik op **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

Op het tabblad **[!UICONTROL Preview]** kunt u de lijst met abonnees van de geselecteerde informatieservice weergeven.

## Mechanismen {#subscription-and-unsubscription-mechanisms} voor abonnementen en afschrijving

U kunt abonnements- en uitstapmechanismen instellen om de processen en het abonneebeheer te automatiseren.

>[!NOTE]
>
>Je kunt een bevestigingsbericht naar nieuwe abonnees sturen.\
>De inhoud van dit bericht wordt gedefinieerd in de configuratie van de informatieservice via de velden **[!UICONTROL Subscription]** of **[!UICONTROL Unsubscription]**.
>
>De bevestigingsberichten worden gecreeerd via de leveringsmalplaatjes die in deze gebieden worden gespecificeerd. Deze doeltoewijzingen moeten **[!UICONTROL Subscriptions]** zijn.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Een ontvanger abonneren op een service {#subscribing-a-recipient-to-a-service}

Als u ontvangers wilt registreren voor een informatieservice, kunt u:

* Voeg de service handmatig toe: om dit te doen, van **[!UICONTROL Subscriptions]** lusje van hun profiel, klik **[!UICONTROL Add]** en selecteer de betrokken informatiedienst.

   Raadpleeg voor meer informatie de sectie over het bewerken van profielen in [deze sectie](../../platform/using/editing-a-profile.md).

* Schrijf automatisch een reeks ontvangers in op deze service. De lijst met ontvangers kan afkomstig zijn van een filterbewerking, een groep, een map, een import of een directe selectie met de muis. Als u zich op deze ontvangers wilt abonneren, selecteert u de profielen en klikt u met de rechtermuisknop. Selecteer **[!UICONTROL Actions > Subscribe selection to a service...]**, selecteer de betreffende service en start de bewerking.
* Importeer ontvangers en meld ze automatisch aan bij een informatieservice. Selecteer hiertoe de desbetreffende service in de laatste stap van de wizard Importeren.

   Raadpleeg [deze sectie](../../platform/using/executing-import-jobs.md) voor meer informatie.

* Gebruik een webformulier zodat ontvangers zich op een service kunnen abonneren.

   Raadpleeg [deze sectie](../../web/using/about-web-applications.md) voor meer informatie.

* Het creëren van een het richten werkschema en het gebruiken van een **[!UICONTROL Subscription service]** doos.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Workflows en het gebruik ervan worden beschreven in [deze sectie](../../workflow/using/about-workflows.md).

### Abonnement op een ontvanger opzeggen {#unsubscribing-a-recipient-from-a-service}

#### Handmatig afmelden {#manual-unsubscribing}

e-mailleveringen moeten wettelijk gezien een link zonder abonnement bevatten. Ontvangers kunnen op deze koppeling klikken om hun profiel bij te werken en worden uitgesloten van de doelstellingen voor toekomstige leveringen.

De standaardkoppeling voor het ongedaan maken van abonnementen wordt ingevoegd via de laatste knop op de werkbalk van de inhoudeditor die wordt geleverd in de wizard voor levering (zie [Informatie over personalisatie](../../delivery/using/about-personalization.md)). Wanneer de ontvanger op deze koppeling klikt, wordt het profiel toegevoegd aan de lijst van afgewezen personen (opt-out), wat betekent dat deze ontvanger niet langer het doelwit is van een leveringsactie.

Ontvangers kunnen echter besluiten hun abonnement op een service op te zeggen zonder zich af te melden bij alle services. Om dit toe te staan, kunt u een Webvorm gebruiken (verwijs naar [deze sectie](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) of een gepersonaliseerde unsubscription verbinding (zie [Persoonlijke blokken](../../delivery/using/personalization-blocks.md)) opnemen.

U kunt het abonnement op een ontvanger ook handmatig opzeggen vanuit het ontvangende profiel. Klik hiertoe op het tabblad **[!UICONTROL Subscriptions]** van de betrokken ontvanger, selecteer de desbetreffende informatieservice(s) en klik op **[!UICONTROL Delete]**.

U kunt de abonnement op een of meer ontvangers opzeggen via de betreffende informatiedienst. Klik hiertoe op het tabblad **[!UICONTROL Subscriptions]** van de service, selecteer de betrokken ontvangers en klik op **[!UICONTROL Delete]**.

#### Abonnement automatisch opzeggen {#automatic-unsubscription}

Een informatiedienst kan een beperkte duur hebben. Ontvangers worden automatisch afgemeld wanneer de geldigheidsperiode is verlopen. Deze periode wordt opgegeven op het tabblad **[!UICONTROL Edit]** van de service-eigenschappen. Het wordt uitgedrukt in dagen.

![](assets/s_ncs_user_services_delay.png)

U kunt ook een workflow zonder abonnement instellen voor een populatie. Hiervoor volgt u dezelfde procedure als voor een abonnementsworkflow, maar selecteert u de optie **[!UICONTROL Unsubscription]**. Zie [Een ontvanger abonneren op een service](#subscribing-a-recipient-to-a-service).

### Abonnementstracering {#subscriber-tracking}

U kunt de wijzigingen in abonnementen op de informatieservices bijhouden met de koppeling **[!UICONTROL Reports]** op het dashboard.

![](assets/s_ncs_user_services_report.png)
