---
title: Inbox rendering
seo-title: Inbox rendering
description: Inbox rendering
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aef56860d6e4558a7f4833066ab3d83733591522
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 0%

---


# Inbox rendering{#inbox-rendering}

## Inbox-rendering {#about-inbox-rendering}

Voordat u op de knop **Verzenden** drukt, moet u ervoor zorgen dat uw bericht op optimale wijze aan de ontvangers wordt weergegeven op verschillende webclients, webmails en apparaten.

Adobe Campaign maakt hiervoor gebruik van de [Litmus](https://litmus.com/email-testing) -testoplossing voor e-mailtests via internet om de renderingen vast te leggen en beschikbaar te maken in een speciaal rapport. Hierdoor kunt u een voorvertoning van het verzonden bericht weergeven in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren.

Litmus is een functie-rijke e-mailbevestiging en previewing toepassing. Hiermee kunnen makers van e-mailinhoud hun berichtinhoud voorvertonen in meer dan 70 e-mailrenderers, zoals de Gmail inbox of de Apple Mail-client.

De clients voor mobiele apparaten, berichten en webmail die beschikbaar zijn voor **Inbox-rendering** in Adobe Campaign, worden weergegeven op de [Litmus-website](https://litmus.com/email-testing) (klik op Alle e-mailclients **** weergeven).

>[!NOTE]
>
>Rendering in doos is niet nodig om personalisatie in leveringen te testen. Personalisatie kan worden gecontroleerd met Adobe-campagneprogramma&#39;s zoals **[!UICONTROL Preview]** en [proefdrukken](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Inbox-rendering activeren {#activating-inbox-rendering}

Voor gehoste en hybride clients wordt de InBox-rendering op uw exemplaar geconfigureerd door technische ondersteuning en consultants van Adobe. Neem voor meer informatie contact op met de manager van uw Adobe-account.

Voor on-premise installaties, volg de stappen hieronder om Inbox teruggeven te vormen.

1. Installeer het **[!UICONTROL Inbox rendering (IR)]** pakket via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Zie Klassieke standaardpakketten [voor campagne](../../installation/using/installing-campaign-standard-packages.md)installeren voor meer informatie.
1. Configureer een externe account van het HTTP-type via **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** . Zie [Een externe account](../../platform/using/external-accounts.md#creating-an-external-account)maken voor meer informatie.
1. Stel de parameters voor de externe account als volgt in:
   * **[!UICONTROL Label]**: Informatie over de leveringsserver
   * **[!UICONTROL Internal name]**: DeliabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Geen
   * Schakel de **[!UICONTROL Enabled]** optie in.
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Ga naar **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** knooppunt. Zoek naar de **[!UICONTROL DmRendering_cuid]** optie en contacteer steun om uw levering te krijgen rapporteert herkenningsteken dat aan het **[!UICONTROL Value (text)]** gebied moet worden gekopieerd.
1. Bewerk het bestand **serverConf.xml** om een aanroep naar de Litmus-server toe te staan. Voeg de volgende regel toe aan de `<urlPermission>` sectie:

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

Telkens wanneer u de **[!UICONTROL Inbox rendering]** functie in een levering gebruikt, vermindert elke gegenereerde rendering de beschikbare tokens met één.

>[!IMPORTANT]
>
>Tokens zijn voor elke afzonderlijke rendering en niet voor het hele Inbox-renderrapport, wat betekent dat:
>
>* Telkens als het Inbox teruggevende rapport wordt geproduceerd, wordt één teken per overseinencliënt afgetrokken: één token voor de rendering van Outlook 2000, één token voor de rendering van Outlook 2010, één token voor de rendering van Apple Mail 9, enzovoort.
>* Als u voor dezelfde levering de rendering Inbox opnieuw genereert, wordt het aantal beschikbare tokens opnieuw verminderd met het aantal gegenereerde renderingen.
>



Het aantal resterende beschikbare tokens wordt weergegeven in het **[!UICONTROL General summary]** Inbox- [renderrapport](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

Doorgaans wordt de renderfunctie Inbox gebruikt om het HTML-framework van een nieuw ontworpen e-mail te testen. Voor elke rendering zijn ongeveer 70 tokens nodig (afhankelijk van het aantal omgevingen dat doorgaans wordt getest). In sommige gevallen hebt u echter meerdere renderingrapporten in postvak nodig om de levering volledig te testen. Het zou dus meer tokens kunnen vergen om meerdere controles te voltooien.

## Toegang tot het renderrapport in Postvak IN {#accessing-the-inbox-rendering-report}

Nadat u de e-maillevering hebt gemaakt en de inhoud ervan en de doelgroep hebt gedefinieerd, volgt u de onderstaande stappen.

Raadpleeg [deze sectie](../../delivery/using/about-email-channel.md)voor meer informatie over het maken, ontwerpen en richten van een levering.

1. Klik op de **[!UICONTROL Inbox rendering]** knop op de bovenste balk van de levering.
1. Selecteer deze optie **[!UICONTROL Analyze]** om het vastlegproces te starten.

   ![](assets/s_tn_inbox_rendering_button.png)

   Er wordt een bewijs verzonden. De renderingminiaturen zijn enkele minuten na het verzenden van de e-mails toegankelijk in die proefdruk. For more on sending proofs, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Na verzending wordt de proefdruk weergegeven in de leveringslijst. Dubbelklik erop.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Ga naar het tabblad **Inbox Rendering** van de proefdruk.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Het renderrapport Postvak IN wordt weergegeven.

## Inbox rendering report {#inbox-rendering-report}

In dit rapport worden de inbox-weergaven weergegeven zoals deze aan de ontvanger worden weergegeven. De renderingen kunnen afwijken, afhankelijk van de manier waarop de ontvanger de e-maillevering opent: in een browser, op een mobiel apparaat of via een e-mailtoepassing.

Het **[!UICONTROL General summary]** aantal ontvangen berichten, ongewenste (spam), ontvangen niet, of hangende ontvangst, als lijst en door een grafische kleur-gecodeerde vertegenwoordiging voor.

![](assets/s_tn_inbox_rendering_summary.png)

Houd de cursor boven het diagram om de details van elke kleur weer te geven.

Het verslag bestaat uit drie delen: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** en **[!UICONTROL Webmails]**. Schuif omlaag het rapport om alle renderingen weer te geven die in deze drie categorieën zijn gegroepeerd.

![](assets/s_tn_inbox_rendering_report.png)

Klik op de bijbehorende kaart om de details voor elk rapport op te halen. De rendering wordt weergegeven voor de geselecteerde ontvangstmethode.

![](assets/s_tn_inbox_rendering_example.png)
