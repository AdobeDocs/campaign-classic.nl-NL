---
solution: Campaign Classic
product: campaign
title: Discussieforums
description: Discussieforums
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Discussieforums{#discussion-forums}

Adobe Campaign-operatoren kunnen discussieforums gebruiken om informatie te delen. De volgende elementen hebben elk hun eigen forum: plannen, programma&#39;s, campagnes, middelen, simulaties, bestanden. Elke exploitant heeft ook een persoonlijk forum. Alle discussies zijn openbaar, zelfs op persoonlijke forums.

Operatoren kunnen zich op een forum abonneren om elke keer dat een bericht wordt gepost, een e-mailbericht te ontvangen.

## Een forum openen {#accessing-a-forum}

Als u het forum van een campagne wilt bezoeken, gaat een operator, enz. naar het dashboard en klikt u op de koppeling **[!UICONTROL Forum]** in de rechterbovenhoek. Deze verbinding geeft u ook het totale aantal berichten in het forum.

![](assets/mrm_forum_access_link.png)

## Een forum {#using-a-forum} gebruiken

Berichten en de reacties worden in chronologische volgorde weergegeven (van Nieuwst naar Oudst).

Als u de inhoud van een bericht wilt weergeven, klikt u op de koptekst van het bericht.

![](assets/mrm_forum_expand_msg.png)

**Een nieuwe discussie starten**

Als u een nieuwe discussie wilt starten, klikt u op de knop **[!UICONTROL Add a discussion]** in de rechterbovenhoek. De doos **[!UICONTROL Discussion forum]** komt omhoog (zie hieronder).

![](assets/mrm_forum_new_thread.png)

**Een bericht sturen naar een bestaande discussie**

Als u een bericht wilt plaatsen naar een bestaande discussie, opent u het bericht dat u wilt beantwoorden en klikt u op de koppeling **[!UICONTROL Reply]** in de linkerbovenhoek. De doos **[!UICONTROL Discussion forum]** komt omhoog (zie hieronder).

![](assets/mrm_forum_answer_msg.png)

Wanneer u op een bericht antwoordt, zal de persoon die het originele bericht plaatste een bericht ontvangen.

**Een bericht schrijven**

In het tekstvak **[!UICONTROL Discussion forum]**:

1. Typ uw tekst in het veld **[!UICONTROL Message]** en een titel voor de beschrijving in het veld **[!UICONTROL Subject]**.

   ![](assets/mrm_forum_edit_msg.png)

1. Indien nodig:

   * Als u wilt dat iemand aan de bespreking deelneemt die niet aan het forum wordt geabonneerd, gebruik **[!UICONTROL Operator to notify]** gebied. De exploitant zal een kennisgevingsmail voor dit specifieke bericht ontvangen (zij zullen niet op het forum worden geabonneerd). Selecteer een groep operatoren als u meerdere operatoren wilt melden.
   * Als u een bijlage aan het bericht wilt toevoegen, klikt u op **[!UICONTROL Browse]**. De bijlage wordt ook opgenomen in de e-mail met het bericht. Bijlagen mogen alleen afzonderlijk worden verzonden: als u meerdere bestanden wilt verzenden, moet u deze zip geven.

1. Klik **[!UICONTROL Create the message]** om het aan het forum te posten.

>[!NOTE]
>
>Zodra een bericht aan het forum is gepost, kan het niet meer worden veranderd of worden geschrapt.

## Plaatsen op het persoonlijke forum van een operator {#posting-to-the-personal-forum-of-an-operator}

U kunt een bericht aan het forum van een exploitant posten als, bijvoorbeeld, uw bericht geen specifieke campagne aangaat maar u wilt het gesprek in Adobe Campaign nog volgen. Persoonlijke forums zijn openbaar en alle operatoren zien uw bericht. De exploitant ontvangt telkens een bericht wanneer iemand aan zijn persoonlijk forum post.

Toegang tot het forum van een exploitant:

* Als u de vereiste rechten hebt om toegang te krijgen tot de **[!UICONTROL Administration > Access management > Operators]**-node van de verkenner, opent u het dashboard van de gewenste operator en klikt u op de koppeling **[!UICONTROL Forum]** in de rechterbovenhoek.
* Zo niet, zoek dan de naam van de exploitant in Adobe Campaign (via een bericht dat door deze operator aan het forum is gepost, een taak die hem wordt toegewezen) en klik erop om het dashboard te openen. U kunt de beheerder ook vragen om een weergave van de map met operatoren te maken.

## Abonneren op een forum {#subscribing-to-a-forum}

Als u zich abonneert op een forum, kunt u discussies volgen. Elke keer dat een bericht naar het forum wordt gepost, ontvangt u een e-mailbericht. Deze e-mail bevat de berichttekst en eventuele bijlagen. Als u een bericht wilt beantwoorden, klikt u in de hoofdtekst van de e-mail en meldt u zich vervolgens aan bij de Adobe Campaign-webinterface. Wanneer u zich abonneert op een forum, is deze informatie zichtbaar voor iedereen.

* Als u zich wilt abonneren op een forum, klikt u op de knop **[!UICONTROL Follow discussions]** in de rechterbovensectie boven de lijst met berichten.

   ![](assets/mrm_forum_subscribe.png)

   De sectie gaat blauw en toont aan dat u aan het forum wordt geabonneerd.

* Als u het abonnement op een forum wilt opzeggen, klikt u op de knop **[!UICONTROL Unsubscribe]**.

   ![](assets/mrm_forum_unsubscribe.png)

* Het persoonlijke dashboard bevat de forums waarop u zich hebt geabonneerd. Klik op de koppeling **[!UICONTROL Subscription to discussion forums]** om de lijst weer te geven en klik vervolgens op het item dat u interesseert om het forum te openen.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Raadpleeg [deze sectie](../../platform/using/access-management.md#operators) voor meer informatie over persoonlijke dashboards.

* Om te zien wie aan een forum wordt geabonneerd, klik de **[!UICONTROL List of subscribers to this discussion forum]** verbinding boven de lijst van berichten.

   ![](assets/mrm_forum_subscribers.png)

## Melding verzenden {#checking-notification-delivery} controleren

Als operatoren die zijn geabonneerd op een forum geen meldingen ontvangen zoals u had verwacht:

* Controleer of de e-mailadressen zijn ingevoerd in de profielen van de operator.
* Ga naar **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** knoop en controleer dat **[!UICONTROL Jobs in discussion forums]** werkschema en vrij van fouten begonnen is.
* De leveringslogboeken weergeven:

   * Ga op de startpagina van Adobe Campaign naar **[!UICONTROL Campaigns > Navigation > Deliveries]** en open vervolgens de levering **[!UICONTROL Discussion forum notification]**.
   * Ga in de verkenner naar **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** en klik vervolgens op **[!UICONTROL Discussion forum notifications]**.

   In de **[!UICONTROL Discussion forum notifications]** doos, worden de leveringslogboeken gevonden in **[!UICONTROL Edit > Delivery]** tabel. U kunt ook de tabbladen **[!UICONTROL Tracking > Log]** en **[!UICONTROL Exclusion causes]** weergeven.

