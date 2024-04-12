---
product: campaign
title: Lidmaatschappen beheren
description: Meer informatie over het beheren van abonnementen in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Subscriptions
role: User
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 2%

---

# Lidmaatschappen beheren{#managing-subscriptions}

## Informatie over informatiediensten {#about-information-services}

Een informatiedienst omvat:

* registratie en abonnement (opt-in),
* Deregistratie, vrijwillig afzien van abonnement (opt-out) of automatisch afzien van abonnement (beperkte-tijdservice, bijvoorbeeld als proefaanbieding);
* bevestigingsmechanismen voor abonnementen en abonnementen (eenvoudige mechanismen met bevestiging, dubbele aanmelding, enz.);
* Het volgen van abonneegeschiedenis.

Deze services omvatten standaard specifieke statistische rapporten: volgen van abonnees, niveau van loyaliteit, trends voor abonnementen, enz.

Voor e-mails worden de verplichte abonnementskoppelingen automatisch gegenereerd. De volledige procedure voor het in- en uitschakelen van e-mail verloopt volledig geautomatiseerd, waarbij de historie wordt bijgehouden om volledige naleving van de geldende regels te garanderen.

Er zijn drie modi voor abonnementen/abonnementen op services:

1. handmatig
1. door importeren (alleen abonnement),
1. via een webformulier

>[!NOTE]
>
>Een voorbeeld voor het maken van een abonnementsformulier met dubbele aanmelding vindt u in [deze sectie](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

## Een informatiedienst maken {#creating-an-information-service}

U kunt abonnementen op informatieservices maken en beheren met de bijbehorende bevestigingsberichten of automatische leveringen aan abonnees.

Als u toegang wilt krijgen tot de kaart met informatieservices, opent u de **[!UICONTROL Profiles and Targets]** en klik op de knop **[!UICONTROL Services and Subscriptions]** koppeling.

![](assets/s_ncs_user_services_new.png)

Als u een bestaande service wilt bewerken, klikt u op de naam van de service. Om de dienst tot stand te brengen, klik **[!UICONTROL Create]** boven de lijst.

![](assets/s_ncs_user_services_add.png)

* Voer de naam van de service in het dialoogvenster **[!UICONTROL Label]** en selecteer het leveringskanaal: e-mail, mobiel, Facebook, X (voorheen bekend als Twitter) of mobiele toepassingen.

  >[!NOTE]
  >
  >Facebook- en X-abonnementen worden beschreven in [deze sectie](../../social/using/about-social-marketing.md). Mobiele toepassingsabonnementen worden beschreven in [Mobiel toepassingskanaal](about-mobile-app-channel.md).

* Selecteer voor een E-mailtypeservice de optie **Leveringsmodus**. De mogelijke modi zijn: **[!UICONTROL Newsletter]** of **[!UICONTROL Viral]**.
* U kunt **bevestigingsberichten** voor een abonnement of een abonnement. Hiervoor selecteert u de leveringssjablonen die u wilt gebruiken om de corresponderende leveringen te maken via de **[!UICONTROL Subscription]** en **[!UICONTROL Unsubscription]** velden. Deze sjablonen moeten worden geconfigureerd met een **[!UICONTROL Subscription]** type target mapping, zonder een gedefinieerd doel. Zie sectie [E-mailkanaal](about-email-channel.md).
* Abonnementen zijn standaard onbeperkt. U kunt de selectie van **[!UICONTROL Unlimited]** optie om een geldigheidstermijn voor de dienst te bepalen. De duur kan worden opgegeven in dagen (**[!UICONTROL d]** ) of maanden (**[!UICONTROL m]** ).

Nadat de service is opgeslagen, wordt deze toegevoegd aan de lijst Services en abonnementen. Klik op de naam van de service om deze te bewerken. Er zijn verschillende tabbladen beschikbaar. De **[!UICONTROL Subscriptions]** kunt u de lijst met abonnees van de informatiedienst bekijken (**[!UICONTROL Active subscriptions]** tab) of de abonnementsgeschiedenis (**[!UICONTROL History]** ). U kunt ook abonnees toevoegen en verwijderen van dit tabblad. Zie [Abonnees toevoegen en verwijderen](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

De **[!UICONTROL Detail...]** de knoop laat u de abonnementseigenschappen voor de geselecteerde ontvanger bekijken.

U kunt de abonnementseigenschappen voor een ontvanger wijzigen.

![](assets/s_ncs_user_services_modify.png)

Klik op het dashboard op de knop **[!UICONTROL Reports]** tab om abonnementen bij te houden: wijzigingen in abonnementsniveaus, totaal aantal abonnees, enz. U kunt rapporten archiveren en historie bekijken van dit lusje.

## Abonnees toevoegen en verwijderen {#adding-and-deleting-subscribers}

Van de **[!UICONTROL Subscriptions]** tabblad van een informatiedienst **[!UICONTROL Add]** om abonnees toe te voegen. U kunt ook met de rechtermuisknop op de lijst met abonnees klikken en **[!UICONTROL Add]**. Selecteer de map waarin de profielen zijn opgeslagen die u wilt abonneren, selecteer vervolgens de profielen die u wilt abonneren en klik op **[!UICONTROL OK]** om te valideren.

Als u abonnees wilt verwijderen, selecteert u deze en klikt u op **[!UICONTROL Delete]**. U kunt ook met de rechtermuisknop op de abonnementenlijst klikken en **[!UICONTROL Delete]**.

In beide gevallen kunt u een bevestigingsbericht naar de betrokken gebruikers sturen als er een leveringssjabloon voor abonnementen aan de service is gekoppeld (zie [Een informatiedienst maken](#creating-an-information-service)). Met een waarschuwing kunt u deze levering valideren of niet valideren:

![](assets/s_ncs_user_services_update.png)

Zie [Abonnementsmechanismen en regelingen voor niet-inschrijving](#subscription-and-unsubscription-mechanisms).

## Het leveren aan de abonnees van een dienst {#delivering-to-the-subscribers-of-a-service}

Om aan de abonnees van een informatiedienst te leveren, kunt u de abonnees aan de betrokken informatiedienst richten, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>De doeltoewijzing moet **[!UICONTROL Subscriptions]**.

Selecteer **[!UICONTROL Subscribers of an information service]** en klik op **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Selecteer de beoogde informatiedienst en klik op **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

De **[!UICONTROL Preview]** kunt u de lijst met abonnees van de geselecteerde informatiedienst weergeven.

## Abonnementsmechanismen en regelingen voor niet-inschrijving {#subscription-and-unsubscription-mechanisms}

U kunt abonnements- en uitstapmechanismen instellen om de processen en het abonneebeheer te automatiseren.

>[!NOTE]
>
>Je kunt een bevestigingsbericht naar nieuwe abonnees sturen.\
>De inhoud van dit bericht wordt bepaald in de configuratie van de informatiedienst via **[!UICONTROL Subscription]** of **[!UICONTROL Unsubscription]** velden.
>
>De bevestigingsberichten worden gecreeerd via de leveringsmalplaatjes die in deze gebieden worden gespecificeerd. Deze doeltoewijzingen moeten **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Een ontvanger aan de dienst abonneren {#subscribing-a-recipient-to-a-service}

Als u ontvangers wilt registreren voor een informatieservice, kunt u:

* Voeg handmatig de service toe: hiervoor gebruikt u de opdracht **[!UICONTROL Subscriptions]** tabblad van hun profiel, klikt u op **[!UICONTROL Add]** en selecteert u de betrokken inlichtingendienst.

  Raadpleeg voor meer informatie de sectie over het bewerken van profielen in [deze sectie](../../platform/using/editing-a-profile.md).

* Schrijf automatisch een reeks ontvangers in op deze service. De lijst met ontvangers kan afkomstig zijn van een filterbewerking, een groep, een map, een import of een directe selectie met de muis. Als u zich op deze ontvangers wilt abonneren, selecteert u de profielen en klikt u met de rechtermuisknop. Selecteren **[!UICONTROL Actions > Subscribe selection to a service...]**, selecteert u de desbetreffende service en start de bewerking.
* Importeer ontvangers en meld ze automatisch aan bij een informatieservice. Selecteer hiertoe de desbetreffende service in de laatste stap van de wizard Importeren.

  Raadpleeg [deze sectie](../../platform/using/executing-import-jobs.md) voor meer informatie.

* Gebruik een webformulier zodat ontvangers zich op een service kunnen abonneren.

  Raadpleeg [deze sectie](../../web/using/about-web-applications.md) voor meer informatie.

* Een doelworkflow maken en een **[!UICONTROL Subscription service]** doos.

  ![](assets/s_ncs_user_subscribe_from_wf.png)

  Workflows en hoe deze worden gebruikt worden beschreven in [deze sectie](../../workflow/using/about-workflows.md).

### Een ontvanger afmelden bij een service {#unsubscribing-a-recipient-from-a-service}

#### Handmatig afmelden {#manual-unsubscribing}

e-mailleveringen moeten wettelijk gezien een link zonder abonnement bevatten. Ontvangers kunnen op deze koppeling klikken om hun profiel bij te werken en worden uitgesloten van de doelstellingen voor toekomstige leveringen.

De standaardkoppeling voor het opzeggen van abonnementen wordt ingevoegd via de laatste knop op de werkbalk van de inhoudseditor die wordt geleverd in de wizard voor levering (zie [Over personalisatie](about-personalization.md)). Wanneer de ontvanger op deze koppeling klikt, wordt het profiel toegevoegd aan de lijst van gewezen personen (opt-out), wat betekent dat deze ontvanger niet langer het doelwit is van een leveringsactie.

Ontvangers kunnen echter besluiten hun abonnement op een service op te zeggen zonder zich af te melden bij alle services. U kunt dit toestaan door een webformulier te gebruiken (zie [deze sectie](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) of voeg een persoonlijke koppeling voor het opzeggen van een abonnement in (zie [Aanpassingsblokken](personalization-blocks.md)).

U kunt het abonnement op een ontvanger ook handmatig opzeggen vanuit het ontvangende profiel. Om dit te doen, klik **[!UICONTROL Subscriptions]** tabblad van de betrokken ontvanger, selecteer de betrokken informatiedienst(en) en klik op **[!UICONTROL Delete]**.

U kunt de abonnement op een of meer ontvangers opzeggen via de betreffende informatiedienst. Om dit te doen, klik **[!UICONTROL Subscriptions]** Selecteer de betrokken ontvangers en klik op **[!UICONTROL Delete]**.

#### Automatisch uitschakelen {#automatic-unsubscription}

Een informatiedienst kan een beperkte duur hebben. Ontvangers worden automatisch afgemeld wanneer de geldigheidsperiode is verlopen. Deze periode wordt gespecificeerd in de **[!UICONTROL Edit]** tabblad van de service-eigenschappen. Het wordt uitgedrukt in dagen.

![](assets/s_ncs_user_services_delay.png)

U kunt ook een workflow zonder abonnement instellen voor een populatie. Hiervoor volgt u dezelfde procedure als voor een abonnementswerkstroom, maar selecteert u de optie **[!UICONTROL Unsubscription]** -optie. Zie [Een ontvanger aan de dienst abonneren](#subscribing-a-recipient-to-a-service).

### Abonnementen bijhouden {#subscriber-tracking}

U kunt de wijzigingen in abonnementen op de informatieservices bijhouden met de functie **[!UICONTROL Reports]** koppeling op het dashboard.

![](assets/s_ncs_user_services_report.png)
