---
product: campaign
title: Aan de slag met personalisatie
description: Leer hoe u berichten kunt personaliseren en voorwaardelijke inhoud kunt gebruiken in Campagne
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 12%

---

# Aan de slag met personalisatie{#about-personalization}

Berichten die door Adobe Campaign worden geleverd, kunnen op verschillende manieren worden gepersonaliseerd, met betrekking tot de content of de weergave van berichten. Deze methoden kunnen worden gecombineerd aan de hand van criteria die met name uit de profielen van de ontvangers zijn afgeleid. Voor e-mailleveringen kunt u de elementen en voorwaarden voor de personalisatie van een levering rechtstreeks in JavaScript definiëren via het tabblad **[!UICONTROL Source]** van het bericht. In het algemeen kunt u met Adobe Campaign:

* Het berichtformaat aanpassen. Zie {de inhoud van het 0} Bericht [.](defining-the-email-content.md#message-content)
* Dynamische personalisatievelden invoegen. Zie {de gebieden van 0} Personalisatie [.](personalization-fields.md)
* Vooraf gedefinieerde aanpassingsblokken invoegen. Zie [&#x200B; blokken van de Personalisatie &#x200B;](personalization-blocks.md).
* Voorwaardelijke content maken. Verwijs naar de [&#x200B; Voorwaardelijke inhoud &#x200B;](conditional-content.md) sectie.

>[!CAUTION]
>
>De volgende variabelen zijn interne variabelen die voor verpersoonlijking kunnen worden gebruikt maar moeten niet worden gewijzigd: **levering**, **bericht**, **dataSource**, **targetData**, **leverancier**, **coupon**, **couponValue**, **5&rbrace;.**


Met Adobe Campaign kunt u uw leveringen personaliseren om berichten te verzenden die overeenkomen met het profiel en de interesses van elke ontvanger.

Personalization helpt je om je berichten relevanter en boeiender te maken. U kunt de gegevens van de ontvanger gebruiken om inhoud aan te passen, dynamische gebieden toe te voegen, of verschillende informatie te tonen die op voorwaarden wordt gebaseerd. Leer hoe te opstelling en gebruiks verpersoonlijkingseigenschappen in uw leveringen in [&#x200B; Adobe Campaign v8 documentatie &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=nl-NL){target=_blank}.

In het kader van het promotieinitiatief Campaign v8 is de documentatie van Campaign Classic gereorganiseerd. Algemene functies zijn nu alleen beschikbaar in de documentatieset van Campagne v8.

>[!BEGINTABS]

>[!TAB  de verpersoonlijkingsdocumentatie van de Inhoud ]

Om meer over inhoudsprijdmaking te leren, verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=nl-NL){target=_blank}.


[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=nl-NL){target=_blank}


>[!TAB  de verwezenlijking van de E-mail levering ]

Leer de belangrijkste stappen met betrekking tot het maken van e-maillevering in de documentatie van Campagne v8:

* [&#x200B; creeer een e-maillevering &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=nl-NL){target="_blank"}: Leer over de verschillende stappen nodig om een e-maillevering tot stand te brengen.
* [&#x200B; bepaal de e-mailinhoud &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=nl-NL){target="_blank"}: Bepaal wat uw e-mail zal omvatten: afzender, onderwerp, inhoud, beelden.
* [&#x200B; bepaal interactieve inhoud &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=nl-NL){target="_blank"}: Gebruik interactieve AMP voor E-mail formaat om dynamische e-mails te verzenden.
* [&#x200B; verzend e-mails op Japanse mobiele toestellen &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=nl-NL){target="_blank"}: Gebruik één van de drie specifieke Japanse formaten voor e-mail op mobiele telefoons.
* [&#x200B; maak dossiers aan e-mail &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=nl-NL){target="_blank"} vast: Leer de verschillende manieren om één of meerdere dossiers aan e-mail vast te maken.


>[!TAB E-mailparameters]

Raadpleeg de volgende pagina&#39;s voor meer informatie over e-mailparameters in de documentatie van Campagne v8:

* [&#x200B; Verbinding aan de spiegelpagina &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=nl-NL){target="_blank"}: Vorm de spiegelpagina om ervoor te zorgen uw cliënten altijd de beste het teruggeven ervaring krijgen.
* [&#x200B; voeg een adres BCC &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=nl-NL){target="_blank"} toe: Vorm Adobe Campaign om een exemplaar van e-mails te houden die van uw platform worden verzonden.
* [&#x200B; bepaalt extra e-mailparameters &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=nl-NL){target="_blank"}: Leer meer over de opties en de parameters beschikbaar bij de leveringseigenschappen.

Ook verwijs naar deze [&#x200B; pagina &#x200B;](sending-with-enhanced-mta.md) om over Verbeterde MTA te leren.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl-NL).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->