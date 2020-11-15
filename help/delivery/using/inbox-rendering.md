---
title: Inbox rendering in campagne
description: Leer hoe u e-mailweergaven vastlegt en beschikbaar maakt in een speciaal rapport
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
translation-type: tm+mt
source-git-commit: 3d6515ca291715e5e02f9b5404803e9087555284
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---


# Inboxrendering{#inbox-rendering}

## Inbox-rendering {#about-inbox-rendering}

Before hitting the **Send** button, make sure that your message will be displayed to the recipients in an optimal way on a variety of web clients, web mails and devices.

Om dit mogelijk te maken, gebruikt Adobe Campaign de [Litmus](https://litmus.com/email-testing) webgebaseerde e-mailtestoplossing om de renderingen vast te leggen en deze beschikbaar te maken in een speciaal rapport. Hierdoor kunt u een voorvertoning van het verzonden bericht weergeven in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren.

Litmus is een functie-rijke e-mailbevestiging en previewing toepassing. Hiermee kunnen makers van e-mailinhoud hun berichtinhoud voorvertonen in meer dan 70 e-mailrenderers, zoals de Gmail inbox of de Apple Mail-client.

The mobile, messaging and webmail clients available for **Inbox rendering** in Adobe Campaign are listed on the [Litmus website](https://litmus.com/email-testing) (click **View all email clients**).

>[!NOTE]
>
>Rendering in doos is niet nodig om personalisatie in leveringen te testen. Personalisatie kan worden gecontroleerd met Adobe Campaign-gereedschappen zoals **[!UICONTROL Preview]** en [proefdrukken](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Inbox-rendering activeren {#activating-inbox-rendering}

Voor gehoste en hybride clients wordt de InBox-rendering op uw exemplaar geconfigureerd door technische ondersteuning van Adobe en consultants. Neem voor meer informatie contact op met de manager van uw Adobe-account.

Voor on-premise installaties, volg de stappen hieronder om Inbox teruggeven te vormen.

1. Installeer het **[!UICONTROL Inbox rendering (IR)]** pakket via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Zie [Standaardpakketten](../../installation/using/installing-campaign-standard-packages.md)voor Campaign Classic installeren voor meer informatie.
1. Configureer een externe account van het HTTP-type via **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** . Zie [Een externe account](../../installation/using/external-accounts.md#creating-an-external-account)maken voor meer informatie.
1. Stel de parameters voor de externe account als volgt in:
   * **[!UICONTROL Label]**: Informatie over de leveringsserver
   * **[!UICONTROL Internal name]**: DeliabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Geen
   * Schakel de optie **[!UICONTROL Enabled]** in.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Go to the **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** node. Zoek naar de **[!UICONTROL DmRendering_cuid]** optie en contacteer steun om uw levering te krijgen rapporteert herkenningsteken dat aan het **[!UICONTROL Value (text)]** gebied moet worden gekopieerd.
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

Voer onderstaande stappen uit als u de e-maillevering hebt gemaakt en de content en de doelpopulatie ervan hebt bepaald.

Raadpleeg [deze sectie](../../delivery/using/about-email-channel.md)voor meer informatie over het maken, ontwerpen en richten van een levering.

1. Klik op de **[!UICONTROL Inbox rendering]** knop op de bovenste balk van de levering.
1. Selecteer deze optie **[!UICONTROL Analyze]** om het vastlegproces te starten.

   ![](assets/s_tn_inbox_rendering_button.png)

   Er wordt een bewijs verzonden. De renderingminiaturen zijn enkele minuten na het verzenden van de e-mails toegankelijk in die proefdruk. For more on sending proofs, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Na verzending wordt de proefdruk weergegeven in de leveringslijst. Dubbelklik erop.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Ga naar het tabblad **Inbox Rendering** van de proefdruk.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Het renderrapport Inbox wordt weergegeven.

## Inbox rendering report {#inbox-rendering-report}

In dit rapport worden de inbox-weergaven weergegeven zoals deze aan de ontvanger worden weergegeven. De renderingen kunnen afwijken, afhankelijk van de manier waarop de ontvanger de e-maillevering opent: in een browser, op een mobiel apparaat of via een e-mailtoepassing.

Het **[!UICONTROL General summary]** aantal ontvangen berichten, ongewenste (spam), ontvangen niet, of hangende ontvangst, als lijst en door een grafische kleur-gecodeerde vertegenwoordiging voor.

![](assets/s_tn_inbox_rendering_summary.png)

Houd de cursor boven het diagram om de details van elke kleur weer te geven.

Het verslag bestaat uit drie delen: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** en **[!UICONTROL Webmails]**. Blader omlaag door het rapport om alle weergaven gegroepeerd in deze drie categorieën te bekijken.

![](assets/s_tn_inbox_rendering_report.png)

Klik op de bijbehorende kaart om de informatie voor elk rapport op te halen. De weergave wordt getoond voor de geselecteerde ontvangstmethode.

![](assets/s_tn_inbox_rendering_example.png)
