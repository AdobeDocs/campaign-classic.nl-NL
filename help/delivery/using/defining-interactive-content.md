---
solution: Campaign Classic
product: campaign
title: Interactieve inhoud definiëren in Adobe Campaign Classic
description: Leer hoe u interactieve en dynamische e-mailinhoud kunt definiëren met AMP in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 3%

---


# Interactieve content definiëren{#defining-interactive-content}

Met Adobe Campaign kunt u de nieuwe interactieve [AMP voor e-mail](https://amp.dev/about/email/)-indeling gebruiken. Hiermee kunt u onder bepaalde omstandigheden dynamische e-mails verzenden.

Met AMP voor e-mail kunt u:
* Test het leveren van AMP-e-mails naar specifieke adressen die correct zijn geconfigureerd.
* E-mails met AMP naar Gmail-, Outlook- of Mail.ru-adressen verzenden nadat u zich hebt geregistreerd bij de betreffende providers.

Zie [Een AMP-e-mail richten voor meer informatie over het testen en verzenden van AMP-e-mails.](#targeting-amp-email)

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet geïnstalleerd zijn om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.

>[!NOTE]
>
> Voor hybride en gehoste architecturen moet het pakket op alle servers worden geïnstalleerd, inclusief de [mid-sourcing server](../../installation/using/mid-sourcing-server.md) en de [uitvoeringsinstantie](../../message-center/using/creating-a-shared-connection.md#execution-instance). Neem contact op met uw accountmanager.

## Informatie over AMP voor e-mail {#about-amp-for-email}

Met de nieuwe indeling **AMP for Email** kunt u AMP-componenten opnemen in berichten om de e-mailervaring te verbeteren met rijke en activeerbare inhoud. Met de moderne applicatiefunctionaliteit die direct beschikbaar is in e-mails, kunnen ontvangers dynamisch communiceren met de content van het bericht zelf.

Bijvoorbeeld:
* E-mails die met AMP zijn geschreven, kunnen interactieve elementen bevatten, zoals afbeeldingscarrousels.
* De inhoud wordt bijgewerkt in het bericht.
* Ontvangers kunnen actie ondernemen zoals op een formulier reageren zonder hun Postvak IN te verlaten.

AMP for Email is compatibel met bestaande e-mails. De AMP-versie van het bericht is in de e-mail ingesloten als een nieuw MIME-onderdeel, naast de HTML en/of onbewerkte tekst, en zorgt voor compatibiliteit tussen alle e-mailclients.

Raadpleeg de [documentatie voor AMP-ontwikkelaars](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email) voor meer informatie over de AMP voor e-mailindeling, specificatie en vereisten.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#amp-email-video)

## Belangrijke stappen voor het gebruik van AMP voor e-mail met Adobe Campaign {#key-steps-to-use-amp}

Volg onderstaande stappen om een AMP-e-mail met Adobe Campaign te testen en te verzenden:
1. Installeer het **[!UICONTROL AMP support]**-pakket. Zie [Standaardpakketten voor campagne installeren](../../installation/using/installing-campaign-standard-packages.md).
1. Maak een e-mail en maak uw AMP-inhoud in Adobe Campaign. Zie [AMP-e-mailinhoud samenstellen met Adobe Campaign](#build-amp-email-content).
1. Zorg ervoor dat u voldoet aan alle leveringsvereisten van de e-mailproviders die de AMP-indeling ondersteunen. Zie [AMP voor vereisten voor e-maillevering](#amp-for-email-delivery-requirements).
1. Wanneer u uw doel definieert, moet u ontvangers selecteren die de AMP-indeling kunnen weergeven. Zie [Een AMP-e-mail richten](#targeting-amp-email).

   >[!NOTE]
   >
   >Momenteel kunt u AMP-e-mails alleen verzenden naar [specifieke e-mailadressen](#testing-amp-delivery-for-selected-addresses) (voor testdoeleinden) of na [registratie](#delivering-amp-emails-by-registering) bij de ondersteunde e-mailclients.

1. Verzend uw e-mail zoals u gewoonlijk zou doen. Zie [Een AMP-e-mail verzenden](#sending-amp-email).

## AMP-e-mailinhoud maken in Adobe Campaign {#build-amp-email-content}

Voer de onderstaande stappen uit om een e-mailbericht te maken in de AMP-indeling.

>[!IMPORTANT]
>
>Zorg ervoor dat u de AMP volgt voor e-mailvereisten en specificaties die worden beschreven in de [documentatie voor AMP-ontwikkelaars](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). U kunt ook de [AMP raadplegen voor best practices voor e-mail](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. Selecteer een sjabloon wanneer u uw e-maillevering maakt.

   >[!NOTE]
   >
   >Een specifieke AMP-sjabloon bevat een voorbeeld van de belangrijkste capaciteiten die u kunt gebruiken: productaanbieding, carrousel, dubbele opt-in, enquête en geavanceerde serveraanvraag.

1. Klik op het tabblad **[!UICONTROL AMP content]**.

   ![](assets/amp_tab.png)

1. Bewerk de AMP-inhoud naar wens.

   >[!NOTE]
   >
   >Raadpleeg de [documentatie voor AMP-ontwikkelaars](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email) voor meer informatie over het maken van uw eerste AMP-e-mail.

   U kunt bijvoorbeeld de component met de productlijst van de AMP-sjabloon gebruiken en een lijst bijhouden met producten van een systeem van derden of zelfs binnen Adobe Campaign. Wanneer u een prijs of een ander element aanpast, zal het automatisch weerspiegeld worden wanneer de ontvanger opnieuw e-mail van hun brievenbus opent.

1. Pas uw AMP-inhoud naar wens aan, zoals u gewoonlijk doet met de HTML-indeling in Adobe Campaign, met personalisatievelden en aanpassingsblokken.

   ![](assets/amp_tab_perso.png)

1. Als u klaar bent met bewerken, selecteert u de volledige AMP-inhoud en kopieert en plakt u deze in de [AMP-webvalidator](https://validator.ampproject.org) of een vergelijkbare website.

   >[!NOTE]
   >
   >Selecteer **AMP4 EMAIL** in de vervolgkeuzelijst boven op het scherm.

   ![](assets/amp_validator.png)

   Eventuele fouten worden inline gemarkeerd.

   >[!NOTE]
   >
   >De AMP-editor van Adobe Campaign is niet ontworpen voor validatie van inhoud. Gebruik een externe website zoals [AMP web-based validator](https://validator.ampproject.org) om te controleren of uw inhoud correct is.

1. Breng zo nodig wijzigingen aan totdat de AMP-inhoud de validatie doorgeeft.

   ![](assets/amp_validator_pass.png)

1. Kopieer de gevalideerde inhoud naar [AMP Playground](https://playground.amp.dev) of een vergelijkbare website om een voorvertoning van de inhoud weer te geven.

   >[!NOTE]
   >
   >Selecteer **AMP voor e-mail** in de vervolgkeuzelijst boven aan het scherm.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >U kunt uw AMP-inhoud niet rechtstreeks in Adobe Campaign voorvertonen. Gebruik een externe website, zoals [AMP Playground](https://playground.amp.dev).

1. Ga terug naar Adobe Campaign en kopieer en plak uw gevalideerde inhoud naar het tabblad **[!UICONTROL AMP content]**.

1. Schakel over naar het tabblad **[!UICONTROL HTML content]** of **[!UICONTROL Text content]** en definieer inhoud voor ten minste een van deze twee indelingen.

   >[!IMPORTANT]
   >
   >Als uw e-mail niet naast de AMP-inhoud ook een HTML- of onbewerkte tekstversie bevat, kan deze niet worden verzonden.

## AMP voor vereisten voor e-maillevering {#amp-for-email-delivery-requirements}

Wanneer u AMP-inhoud maakt in Adobe Campaign, moet u voldoen aan de voorwaarden voor het verzenden van een dynamische e-mail, die specifiek zijn voor de e-mailproviders van uw ontvangers.

Momenteel ondersteunen drie e-mailproviders het testen van deze indeling: Gmail, Outlook en Mail.ru.

Alle stappen en specificaties die vereist zijn om levering met AMP-indeling te testen op Gmail-accounts worden beschreven in de corresponderende documentatie voor [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) en [Mail.ru](https://postmaster.mail.ru/amp)-ontwikkelaars.

Met name moet aan de volgende eisen worden voldaan:
* Volg de specifieke AMP-beveiligingsvereisten voor [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) en [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* Het AMP MIME-onderdeel moet een [geldig AMP-document](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email) bevatten.
* Het AMP MIME-onderdeel moet kleiner zijn dan 100 kB.

U kunt ook de [Tips en bekende beperkingen voor Gmail](https://developers.google.com/gmail/ampemail/tips) en de [AMP beste praktijken voor Vooruitzichten](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices) raadplegen.

## Een AMP-e-mail {#targeting-amp-email} voorbereiden

U kunt momenteel in twee stappen experimenteren met het verzenden van een AMP-e-mail:

1. Met Adobe Campaign kunt u testen of een dynamische e-mail met AMP-functionaliteit wordt geleverd aan geselecteerde e-mailadressen die correct zijn geconfigureerd, om de inhoud en het gedrag ervan te controleren. Zie [AMP-e-maillevering testen voor geselecteerde adressen](#testing-amp-delivery-for-selected-addresses).

1. Nadat u de test hebt uitgevoerd, kunt u een levering of een campagne verzenden als onderdeel van het AMP for Email-programma door u te registreren bij de desbetreffende e-mailprovider(s) om uw senderdomein toe te voegen aan de lijst van gewenste personen. Zie [AMP-e-mails leveren door u te registreren bij een e-mailprovider](#delivering-amp-emails-by-registering).

### Het testen van AMP e-maillevering voor geselecteerde adressen {#testing-amp-delivery-for-selected-addresses}

U kunt testen hoe dynamische berichten van Adobe Campaign naar geselecteerde e-mailadressen worden verzonden.

>[!NOTE]
>
>Momenteel ondersteunen alleen Gmail, Outlook en Mail.ru het testen van de AMP-indeling.

Voor Gmail en Vooruitzichten, moet u eerst de afzenderadres(sen) toevoegen u aan de lijst van gewenste personen gebruikt om van Adobe Campaign voor de rekeningen van Gmail en van Vooruitzichten te leveren u richt.

Dit doet u als volgt:
1. Controleer of de optie voor het inschakelen van dynamische e-mail is ingeschakeld bij de desbetreffende e-mailprovider(s).
1. Kopieer het adres van de afzender dat in het **[!UICONTROL From]** gebied van de levering wordt getoond en kleef het in de aangewezen sectie van de de rekeningsmontages van uw e-mailprovider.

Raadpleeg de documentatie voor [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) en [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) voor meer informatie.

![](assets/amp_from_field.png)

Als u het verzenden van een AMP-e-mail naar een Mail.ru-adres wilt testen, voert u de stappen uit van de [Mail.ru-ontwikkelaarsdocumentatie](https://postmaster.mail.ru/amp/?lang=en#howto) (**Als u een gebruiker**-sectie bent).

### E-mails met AMP leveren door zich te registreren bij een e-mailprovider {#delivering-amp-emails-by-registering}

U kunt experimenteren met het leveren van dynamische e-mailberichten door u te registreren bij de ondersteunde e-mailproviders, zodat uw senderdomein aan de lijst van gewenste personen wordt toegevoegd.

>[!NOTE]
>
>Momenteel ondersteunen alleen Gmail, Outlook en Mail.ru de AMP-indeling.

Als u eenmaal met een paar adressen bent getest, kunt u AMP-e-mails naar elk Gmail- of Outlook-adres sturen. Om dit te doen, moet u respectvol registreren bij Google of Microsoft, en hun antwoord wachten. Volg de stappen in [Gmail](https://developers.google.com/gmail/ampemail/register) en [de documenten van de ontwikkelaar van Vooruitzichten](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) worden voorgesteld. Nadat je bent ingeschreven, word je een geautoriseerde afzender.

Als u AMP-e-mails naar Mail.ru-adressen wilt verzenden, volgt u de vereisten en stappen in de [Mail.ru-ontwikkelaarsdocumentatie](https://postmaster.mail.ru/amp/?lang=en#howto) (**Als u een E-mailafzender**-sectie bent).

## Een AMP-e-mail {#sending-amp-email} verzenden

Zodra uw AMP-inhoud en -fallback klaar zijn en u een compatibel doel hebt gedefinieerd, kunt u de e-mail verzenden zoals u dat gewoonlijk doet.

Momenteel ondersteunen alleen Gmail, Outlook en Mail.ru de AMP-indeling onder bepaalde omstandigheden. U kunt adressen van andere e-mailleveranciers richten, maar zij zullen de HTML of de gewone tekstversie van uw e-mail ontvangen.

>[!IMPORTANT]
>
>Als uw e-mail niet naast de AMP-inhoud ook een HTML- of onbewerkte tekstversie bevat, kan deze niet worden verzonden.

De overeenkomende ontvangers hebben de AMP-versie van de e-mail die in hun postvak wordt weergegeven.

Bijvoorbeeld, als u een productlijst in uw e-mail opnam, wanneer het uitgeven van de prijzen in een derdesysteem, zullen de prijzen automatisch worden aangepast telkens als uw ontvangers de e-mail opnieuw in hun brievenbus openen.

>[!NOTE]
>
>U kunt een regel voor e-mailverwerking maken om te voorkomen dat bepaalde domeinen AMP-e-mails ontvangen. Zie [E-mailindelingen beheren](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Standaard is de optie **[!UICONTROL AMP inclusion]** ingesteld op **[!UICONTROL No]**.

## Video over zelfstudie {#amp-email-video}

In de onderstaande video wordt uitgelegd hoe u AMP kunt activeren in Adobe Campaign Classic en wordt u het gebruik ervan voorgesteld.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
