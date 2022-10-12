---
product: campaign
title: Inbox rendering in campagne
description: Leer hoe u e-mailweergaven vastlegt en beschikbaar maakt in een speciaal rapport
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: 048189f49623cf00f4c3f1f34ff4b795d80391ef
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 8%

---

# Inboxrendering{#inbox-rendering}

![](../../assets/common.svg)

## Inbox-rendering {#about-inbox-rendering}

Voordat u de **Verzenden** , zorgt u ervoor dat uw bericht op optimale wijze aan de ontvangers wordt weergegeven op verschillende webclients, webmails en apparaten.

Om dit mogelijk te maken, gebruikt Adobe Campaign de [Litmus](https://litmus.com/email-testing) testoplossing voor e-mail via internet om de renderingen vast te leggen en beschikbaar te maken in een speciaal rapport. Hierdoor kunt u een voorvertoning van het verzonden bericht weergeven in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren.

>[!CAUTION]
>Inbox-rendering is niet compatibel met [terugkerende leveringen](communication-channels.md#recurring-delivery).

Litmus is een functie-rijke e-mailbevestiging en previewing toepassing. Hiermee kunnen makers van e-mailinhoud hun berichtinhoud voorvertonen in meer dan 70 e-mailrenderers, zoals de Gmail inbox of de Apple Mail client.

De mobiele clients, berichten en webmail zijn beschikbaar voor **Inbox rendering** in Adobe Campaign worden vermeld op de [Litmus-website](https://litmus.com/email-testing) (klik op **Alle e-mailclients weergeven**).

>[!NOTE]
>
>Rendering in doos is niet nodig om personalisatie in leveringen te testen. Personalisatie kan worden gecontroleerd met Adobe Campaign-programma&#39;s zoals **[!UICONTROL Preview]** en [Proefdrukken](steps-validating-the-delivery.md#sending-a-proof).

## Inbox-rendering activeren {#activating-inbox-rendering}

Voor gehoste en hybride clients wordt de InBox-rendering op uw exemplaar geconfigureerd door technische ondersteuning van Adobe en consultants. Neem voor meer informatie contact op met de manager van uw Adobe-account.

Voor on-premise installaties, volg de stappen hieronder om Inbox teruggeven te vormen.

1. Installeer de **[!UICONTROL Inbox rendering (IR)]** pakket via de **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** -menu. Zie voor meer informatie [Campaign Classic-standaardpakketten installeren](../../installation/using/installing-campaign-standard-packages.md).
1. Een externe account voor het HTTP-type configureren via de **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** knooppunt. Zie voor meer informatie [Een externe account maken](../../installation/using/external-accounts.md#creating-an-external-account).
1. Stel de parameters voor de externe account als volgt in:
   * **[!UICONTROL Label]**: Informatie over de leveringsserver
   * **[!UICONTROL Internal name]**: DeliabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Geen
   * Schakel de optie **[!UICONTROL Enabled]** in.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Ga naar de **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** knooppunt. Zoeken naar **[!UICONTROL DmRendering_cuid]** en neem contact op met de ondersteuning om de id van uw leveringsrapporten te verkrijgen die naar de **[!UICONTROL Value (text)]** veld.
1. Bewerk de **serverConf.xml** dossier om een vraag aan de server toe te staan Litmus. Voeg de volgende regel toe aan de `<urlPermission>` sectie:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Laad de configuratie opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Mogelijk moet u zich afmelden bij de console en u opnieuw aanmelden om de rendering Inbox te kunnen gebruiken.

## Informatie over Litmus tokens {#about-litmus-tokens}

Aangezien Litmus een derdedienst is, werkt het op een krediet-per-gebruiksmodel. Telkens wanneer een gebruiker op de functionaliteit van de Leiding roept, wordt het krediet afgetrokken.

In Adobe Campaign komt het krediet overeen met het aantal beschikbare renderingen (tokens genoemd).

>[!NOTE]
>
>Het aantal beschikbare Litmus tokens hangt af van de campagnelicentie die u hebt aangeschaft. Controleer uw licentieovereenkomst.

Elke keer dat u de **[!UICONTROL Inbox rendering]** Bij elke gegenereerde rendering worden de beschikbare tokens met één verminderd.

>[!IMPORTANT]
>
>Tokens zijn voor elke afzonderlijke rendering en niet voor het hele Inbox-renderrapport, wat betekent dat:
>
>* Telkens als het Inbox teruggevende rapport wordt geproduceerd, wordt één teken per overseinencliënt afgetrokken: één token voor de rendering van Outlook 2000, één token voor de rendering van Outlook 2010, één token voor de rendering van Apple Mail 9, enzovoort.
>* Als u voor dezelfde levering de rendering Inbox opnieuw genereert, wordt het aantal beschikbare tokens opnieuw verminderd met het aantal gegenereerde renderingen.
>


Het aantal resterende beschikbare tokens wordt weergegeven in het dialoogvenster **[!UICONTROL General summary]** van de [Inbox rendering report](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

Doorgaans wordt de renderfunctie Inbox gebruikt om het HTML-framework van een nieuw ontworpen e-mail te testen. Voor elke rendering zijn ongeveer 70 tokens nodig (afhankelijk van het aantal omgevingen dat doorgaans wordt getest). In sommige gevallen hebt u echter meerdere renderingrapporten in postvak nodig om de levering volledig te testen. Het zou dus meer tokens kunnen vergen om meerdere controles te voltooien.

## Toegang tot het renderrapport in Postvak IN {#accessing-the-inbox-rendering-report}

Voer onderstaande stappen uit als u de e-maillevering hebt gemaakt en de content en de doelpopulatie ervan hebt bepaald.

Raadpleeg voor meer informatie over het maken, ontwerpen en richten van een levering [deze sectie](about-email-channel.md).

1. Klik op de bovenste balk van de levering op de knop **[!UICONTROL Inbox rendering]** knop.
1. Selecteren **[!UICONTROL Analyze]** om het vastlegproces te starten.

   ![](assets/s_tn_inbox_rendering_button.png)

   Er wordt een bewijs verzonden. De renderingminiaturen zijn enkele minuten na het verzenden van de e-mails toegankelijk in die proefdruk. Raadpleeg voor meer informatie over het verzenden van proefdrukken [deze sectie](steps-validating-the-delivery.md#sending-a-proof).

1. Na verzending wordt de proefdruk weergegeven in de leveringslijst. Dubbelklik erop.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Ga naar de **Inbox Rendering** tabblad van de proefdruk.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Het renderrapport Inbox wordt weergegeven.

## Inbox rendering report {#inbox-rendering-report}

In dit rapport worden de inbox-weergaven weergegeven zoals deze aan de ontvanger worden weergegeven. De renderingen kunnen afwijken, afhankelijk van de manier waarop de ontvanger de e-maillevering opent: in een browser, op een mobiel apparaat of via een e-mailtoepassing.

De **[!UICONTROL General summary]** presenteert het aantal ontvangen, ongewenste (spam), niet ontvangen, of hangende ontvangst, als lijst en door een grafische kleur-gecodeerde vertegenwoordiging.

![](assets/s_tn_inbox_rendering_summary.png)

Houd de cursor boven het diagram om de details van elke kleur weer te geven.

Het verslag bestaat uit drie delen: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]**, en **[!UICONTROL Webmails]**. Blader omlaag door het rapport om alle weergaven gegroepeerd in deze drie categorieën te bekijken.

![](assets/s_tn_inbox_rendering_report.png)

Klik op de bijbehorende kaart om de informatie voor elk rapport op te halen. De weergave wordt getoond voor de geselecteerde ontvangstmethode.

![](assets/s_tn_inbox_rendering_example.png)
