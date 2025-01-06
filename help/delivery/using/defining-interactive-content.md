---
product: campaign
title: Interactieve inhoud definiëren in Adobe Campaign Classic
description: Leer hoe u interactieve en dynamische e-mailinhoud kunt definiëren met AMP in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design
role: User
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 3%

---

# Interactieve content definiëren{#defining-interactive-content}

Adobe Campaign laat u toe om interactieve [ AMP voor E-mail ](https://amp.dev/about/email/) formaat te gebruiken, dat toelaat om dynamische e-mail, onder bepaalde voorwaarden te verzenden.

Met AMP voor e-mail kunt u:
* Test het leveren van AMP-e-mails naar specifieke adressen die correct zijn geconfigureerd.
* Verzend AMP-e-mails naar Gmail- of Mail.ru-adressen nadat u zich hebt geregistreerd bij de betreffende providers.

Voor meer bij het testen van en het verzenden van e-mails van AMP, zie [ deze sectie ](#targeting-amp-email).

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Afhankelijk van uw machtigingen en uw implementatiemodel kunt u dit pakket installeren of de Adobe bereiken om het voor u te installeren.

>[!NOTE]
>
> Voor hybride en ontvangen architecturen, moet het pakket op alle servers, met inbegrip van de [ midsourcing server ](../../installation/using/mid-sourcing-server.md) en de [ uitvoeringsinstantie ](../../message-center/using/configuring-instances.md#execution-instance) worden geïnstalleerd.


## Informatie over AMP voor e-mail {#about-amp-for-email}

Gebruik **AMP voor E-mail** nieuw formaat om de componenten van AMP in uw berichten te omvatten en de e-mailervaring met een rijke en actionable inhoud te verbeteren. Met moderne appfunctionaliteit die direct beschikbaar is in e-mails, kunnen ontvangers dynamisch communiceren met de content van het bericht zelf.

Bijvoorbeeld:
* E-mails die met AMP zijn geschreven, kunnen interactieve elementen bevatten, zoals afbeeldingscarrousels.
* De inhoud wordt bijgewerkt in het bericht.
* Ontvangers kunnen reageren op een formulier zonder hun postvak IN te vullen.

AMP for Email is compatibel met bestaande e-mails. De AMP-versie van het bericht is in de e-mail ingesloten als een nieuw MIME-onderdeel, naast de HTML en/of onbewerkte tekst, waardoor compatibiliteit tussen alle e-mailclients wordt gegarandeerd.

Voor meer op AMP voor E-mail formaat, specificatie en vereisten, zie de [ documentatie van de ontwikkelaar van AMP ](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#amp-email-video)

## Belangrijke stappen voor het gebruik van AMP voor e-mail met Adobe Campaign {#key-steps-to-use-amp}

Volg onderstaande stappen om een AMP-e-mail met Adobe Campaign te testen en te verzenden:
1. Installeer het pakket **[!UICONTROL AMP support]** . Zie [ het Installeren ingebouwde pakketten van de Campagne ](../../installation/using/installing-campaign-standard-packages.md).
1. Maak een e-mail en maak uw AMP-inhoud in Adobe Campaign. Zie [ AMP e-mailinhoud met Adobe Campaign ](#build-amp-email-content) bouwen.
1. Zorg ervoor dat u voldoet aan alle leveringsvereisten van de e-mailproviders die de AMP-indeling ondersteunen. Zie [ AMP voor E-mail leveringsvereisten ](#amp-for-email-delivery-requirements).
1. Wanneer u uw doel definieert, moet u ontvangers selecteren die de AMP-indeling kunnen weergeven. Zie [ richtend een e-mail van AMP ](#targeting-amp-email).

   >[!NOTE]
   >
   >Momenteel kunt u AMP e-mails aan [ specifieke e-mailadressen ](#testing-amp-delivery-for-selected-addresses) (voor het testen doel) of na [ registratie ](#delivering-amp-emails-by-registering) met de gesteunde e-mailcliënten slechts leveren.

1. Verzend uw e-mail zoals u gewoonlijk zou doen. Zie [ verzenden een e-mail van AMP ](#sending-amp-email).

## AMP-e-mailinhoud maken in Adobe Campaign {#build-amp-email-content}

Voer de onderstaande stappen uit om een e-mailbericht te maken in de AMP-indeling.

>[!IMPORTANT]
>
>Zorg ervoor u AMP voor E-mailvereisten en specificaties volgt die in de [ documentatie van de ontwikkelaar van AMP ](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email) worden gedetailleerd. U kunt [ AMP voor E-mail beste praktijken ](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email) ook raadplegen.

1. Selecteer een sjabloon wanneer u uw e-maillevering maakt.

   >[!NOTE]
   >
   >Een specifieke AMP-sjabloon bevat een voorbeeld van de belangrijkste mogelijkheden die u kunt gebruiken: productvermelding, carrousel, dubbele aanmelding, enquête en geavanceerde serveraanvraag.

1. Klik op de tab **[!UICONTROL AMP content]** .

   ![](assets/amp_tab.png)

1. Bewerk de AMP-inhoud naar wens.

   >[!NOTE]
   >
   >Voor meer bij de bouw van uw eerste e-mail van AMP, zie de [ documentatie van de ontwikkelaar van AMP ](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   U kunt bijvoorbeeld de component met de productlijst van de AMP-sjabloon gebruiken en een lijst bijhouden met producten van een systeem van derden of zelfs binnen Adobe Campaign. Wanneer u een prijs of een ander element aanpast, wordt het automatisch weerspiegeld wanneer de ontvangers e-mail van hun brievenbus openen.

1. Pas uw AMP-inhoud naar wens aan, zoals u gewoonlijk doet met de HTML-indeling in Adobe Campaign, met personalisatievelden en aanpassingsblokken.

   ![](assets/amp_tab_perso.png)

1. Zodra gedaan met het uitgeven, selecteer uw volledige inhoud AMP en kopieer-kleef het in [ AMP web-based validator ](https://validator.ampproject.org) of een gelijkaardige website.

   >[!NOTE]
   >
   >Zorg ervoor u **AMP4 EMAIL** van de drop-down lijst bovenop het scherm selecteert.

   ![](assets/amp_validator.png)

   Fouten worden inline gemarkeerd.

   >[!NOTE]
   >
   >De AMP-editor van Adobe Campaign is niet ontworpen voor validatie van inhoud. Gebruik een externe website zoals [ AMP web-based validator ](https://validator.ampproject.org) om te controleren dat uw inhoud correct is.

1. Breng zo nodig wijzigingen aan totdat de AMP-inhoud de validatie doorgeeft.

   ![](assets/amp_validator_pass.png)

1. Om uw inhoud voor te vertonen, kopieer-kleef uw bevestigde inhoud in [ de Playground van AMP ](https://playground.amp.dev) of een gelijkaardige website.

   >[!NOTE]
   >
   >Zorg ervoor u **AMP voor E-mail** van de drop-down lijst bovenop het scherm selecteert.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >U kunt uw AMP-inhoud niet rechtstreeks in Adobe Campaign voorvertonen. Gebruik een externe website zoals [ de Playground van AMP ](https://playground.amp.dev).

1. Ga terug naar Adobe Campaign en kopieer en plak uw gevalideerde inhoud naar het tabblad **[!UICONTROL AMP content]** .

1. Schakel over naar het tabblad **[!UICONTROL HTML content]** of **[!UICONTROL Text content]** en definieer inhoud voor ten minste een van deze twee indelingen.

   >[!IMPORTANT]
   >
   >Als uw e-mail niet naast de AMP-inhoud een HTML- of onbewerkte tekstversie bevat, kan deze niet worden verzonden.

## AMP voor vereisten voor e-maillevering {#amp-for-email-delivery-requirements}

Wanneer u AMP-inhoud maakt in Adobe Campaign, moet u voldoen aan de voorwaarden voor het verzenden van een dynamische e-mail, die specifiek zijn voor de e-mailproviders van uw ontvangers.

Momenteel ondersteunen twee e-mailproviders het testen van deze indeling: Gmail en Mail.ru.

Alle stappen en specificaties die worden vereist om levering met formaat te testen AMP op de rekeningen van Gmail worden gedetailleerd in de overeenkomstige [ Gmail ](https://developers.google.com/gmail/ampemail?), en [ Mail.ru ](https://postmaster.mail.ru/amp) ontwikkelaarsdocumenten.

Met name moet aan de volgende eisen worden voldaan:
* Volg de de veiligheidsvereisten van AMP specifiek voor [ Gmail ](https://developers.google.com/gmail/ampemail/security-requirements), en [ Mail.ru ](https://postmaster.mail.ru/amp/#howto).
* Het AMP MIME deel moet a [ geldig document van AMP ](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email) bevatten.
* Het AMP MIME-onderdeel moet kleiner zijn dan 100 kB.

U kunt ook de [ Uiteinden en bekende beperkingen voor Gmail ](https://developers.google.com/gmail/ampemail/tips) documentatie raadplegen.

## Een AMP-e-mail sturen {#targeting-amp-email}

U kunt momenteel in twee stappen experimenteren met het verzenden van een AMP-e-mail:

1. Met Adobe Campaign kunt u testen of een dynamische e-mail met AMP-functionaliteit wordt geleverd aan geselecteerde e-mailadressen die correct zijn geconfigureerd, om de inhoud en het gedrag ervan te controleren. Zie [ het Testen AMP e-maillevering voor geselecteerde adressen ](#testing-amp-delivery-for-selected-addresses).

1. Nadat u de test hebt uitgevoerd, kunt u een levering of een campagne verzenden als onderdeel van het AMP for Email-programma door u te registreren bij de desbetreffende e-mailprovider(s) om uw senderdomein toe te voegen aan de lijst van gewenste personen. Zie [ Leverend de e-mails van AMP door met een e-mailleverancier ](#delivering-amp-emails-by-registering) te registreren.

### AMP-e-maillevering testen voor geselecteerde adressen {#testing-amp-delivery-for-selected-addresses}

U kunt testen hoe dynamische berichten van Adobe Campaign naar geselecteerde e-mailadressen worden verzonden.

>[!NOTE]
>
>Alleen Gmail en Mail.ru ondersteunen het testen van de AMP-indeling.

Voor Gmail, moet u eerst de afzenderadres(sen) toevoegen u aan de lijst van gewenste personen gebruikt om van Adobe Campaign voor de rekeningen te leveren Gmail u richt.

Dit doet u als volgt:
1. Controleer of de optie voor het inschakelen van dynamische e-mail is ingeschakeld bij de desbetreffende e-mailprovider(s).
1. Kopieer het adres van de afzender dat in het gebied van de levering **[!UICONTROL From]** wordt getoond en kleef het in de aangewezen sectie van de de rekeningsmontages van uw e-mailprovider.

Voor verdere details, raadpleeg de ](https://developers.google.com/gmail/ampemail/testing-dynamic-email) ontwikkelaarsdocumentatie 0} Gmail {.[

![](assets/amp_from_field.png)

Om het verzenden van een e-mail van AMP naar een adres Mail.ru te testen, volg de stappen van de [ Mail.ru ontwikkelaarsdocumentatie ](https://postmaster.mail.ru/amp/#howto) (**als u een gebruiker** sectie bent).

### E-mails met AMP leveren door zich te registreren bij een e-mailprovider {#delivering-amp-emails-by-registering}

U kunt experimenteren met het leveren van dynamische e-mailberichten door u te registreren bij de ondersteunde e-mailproviders, zodat uw senderdomein wordt toegevoegd aan de lijst van gewenste personen.

>[!NOTE]
>
>Alleen Gmail en Mail.ru ondersteunen de AMP-indeling.

Als u eenmaal met een paar adressen bent getest, kunt u AMP-e-mails naar elk Gmail-adres sturen. Hiervoor moet u zich registreren bij Google en wachten op het antwoord. Volg de stappen die in de [ worden voorgesteld Gmail ](https://developers.google.com/gmail/ampemail/register) ontwikkelaarsdocumentatie. Nadat je bent ingeschreven, word je een geautoriseerde afzender.

Om AMP e-mails naar Mail.ru adressen te verzenden, volg de vereisten en de stappen die in de [ worden vermeld Mail.ru ontwikkelaarsdocumentatie ](https://postmaster.mail.ru/amp/#howto) (**als u een E-mail afzender** sectie bent).

## Een AMP-e-mail verzenden {#sending-amp-email}

Zodra uw AMP-inhoud en -fallback klaar zijn en u een compatibel doel hebt gedefinieerd, kunt u de e-mail verzenden zoals u dat gewoonlijk doet.

Momenteel ondersteunen alleen Gmail en Mail.ru de AMP-indeling onder bepaalde omstandigheden. U kunt adressen van andere e-mailleveranciers richten, maar zij zullen de HTML of gewone tekstversie van uw e-mail ontvangen.

>[!IMPORTANT]
>
>Als uw e-mail niet naast de AMP-inhoud een HTML- of onbewerkte tekstversie bevat, kan deze niet worden verzonden.

De overeenkomende ontvangers hebben de AMP-versie van de e-mail die in hun postvak wordt weergegeven.

Bijvoorbeeld, als u een productlijst in uw e-mail opnam, wanneer het uitgeven van de prijzen in een derdesysteem, zullen de prijzen automatisch worden aangepast telkens als uw ontvangers de e-mail opnieuw in hun brievenbus openen.

>[!NOTE]
>
>U kunt een regel voor e-mailverwerking maken om te voorkomen dat bepaalde domeinen AMP-e-mails ontvangen. Zie [ het Leiden e-mailformaten ](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Standaard is de optie **[!UICONTROL AMP inclusion]** ingesteld op **[!UICONTROL No]** .

## Video over zelfstudie {#amp-email-video}

In de onderstaande video wordt uitgelegd hoe u AMP in Adobe Campaign kunt activeren en krijgt u een voorbeeld van het gebruik.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

De extra campagne hoe-aan video&#39;s is beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
