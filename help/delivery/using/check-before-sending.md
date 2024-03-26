---
product: campaign
title: Controleren vóór verzending
description: Zodra uw bericht klaar is, voer alle controles uit alvorens te verzenden
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 2%

---

# Alle controles uitvoeren voordat ze worden verzonden {#perform-all-checks}

Zodra uw bericht klaar is, zorg ervoor zijn inhoud correct, op alle apparaten wordt getoond, en bevat geen fouten zoals verkeerde verpersoonlijking of gebroken verbindingen.

Alvorens uw bericht te verzenden, zorg ook dat de parameters en de configuratie met de levering verenigbaar zijn.

## Waarom validatie de sleutel is {#validation-is-key}

Alvorens een levering te verzenden, moet u ervoor zorgen dat uw ontvangers het bericht zullen ontvangen dat u echt hen wilt verzenden. Hiervoor moet u de inhoud en de leveringsparameters van het bericht valideren.

Met deze stap kunt u mogelijke fouten detecteren en corrigeren voordat u deze aan uw hoofddoel kunt leveren.

De stappen voor het valideren van een levering worden weergegeven [in deze sectie](steps-validating-the-delivery.md).

## Inboxrendering {#inbox-and-email-rendering}

Met Postvak-rendering kunt u uw berichten voorvertonen bij belangrijke e-mailclients, inhoud en reputatie scannen en ontdekken hoe ontvangers berichten lezen.

**Tips**:

* U kunt het verzonden bericht weergeven in de verschillende contexten waarin het kan worden ontvangen: webmail, berichtservice, mobiel enzovoort.

* Rendermogelijkheden in postvakken zijn van cruciaal belang om te bepalen of uw e-mailcampagnes erin slagen het voorbij de filters van belangrijke ISP&#39;s (Internet Service Providers) en webmailservices te maken. Dergelijke hulpmiddelen verzenden een pre-vlucht exemplaar van een e-mail naar een netwerk van testinboxes, zodat kunt u zien hoe het bericht, over deze diensten zal tonen of teruggeven. Ze kunnen ook rapporten en opties voor codecorrectie bevatten die u helpen snel oplossingen te vinden en te maken die de leesbaarheid verbeteren.

Meer informatie [in deze sectie](inbox-rendering.md).

## Proefberichten {#proof-messages}

Door proefdrukken te verzenden, kunt u de koppeling om te weigeren controleren, de pagina spiegelen en andere koppelingen controleren, het bericht valideren, controleren of afbeeldingen worden weergegeven, mogelijke fouten opsporen, enz. Mogelijk wilt u ook uw ontwerp en rendering op verschillende apparaten controleren.

Meer informatie [in deze sectie](steps-validating-the-delivery.md#sending-a-proof).

## A/B-testleveringen instellen {#a-b-testing-deliveries}

Als u meerdere inhoud voor een e-maillevering hebt, kunt u A/B-tests gebruiken om na te gaan welke versie de grootste invloed heeft op de doelpopulatie.

**Tips**:

* Verschillende versies naar sommige ontvangers verzenden

* Selecteer het bestand met de hoogste successnelheid en stuur het naar de rest van het doel

Meer informatie [in deze sectie](get-started-a-b-testing.md).

## Controleer of je bericht is bezorgd {#make-sure-your-message-is-delivered}

Als laatste stap maximaliseert u uw kansen en gebruikt u de kracht van Adobe Campaign Classic om ervoor te zorgen dat uw bericht ook daadwerkelijk aan de relevante ontvangers wordt bezorgd.

### Een validatieproces doorlopen

U kunt een volledig validatieproces definiëren, waarbij Adobe Campaign-operatoren en -groepen betrokken zijn, om zowel de inhoud van het doel als het bericht te valideren. Dit zal zorgen voor volledig toezicht en controle op de verschillende processen van de campagne: gericht op, inhoud, begroting, extractie en het verzenden van bewijzen. Afhankelijk van hun machtigingen zullen gebruikers op de hoogte worden gesteld, proefdrukken ontvangen en het bericht kunnen valideren of afwijzen. Meer informatie [in deze sectie](../../campaign/using/marketing-campaign-approval.md).

### Golven gebruiken

U kunt het verzonden volume progressief verhogen gebruikend golven. Zo voorkomt u dat uw berichten als spam worden gemarkeerd of dat u het aantal berichten per dag wilt beperken. Met golven kunt u leveringen in verschillende batches verdelen in plaats van tegelijkertijd grote volumes berichten te verzenden. Meer informatie [in deze sectie](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Prioriteitsberichten

U kunt de verzendende orde voor uw leveringen plaatsen door het prioritaire niveau te verklaren. Dit doet u als volgt:

1. Bewerk de leveringseigenschappen en selecteer de **[!UICONTROL Delivery]** tab.

1. Het prioriteitsniveau voor levering op schaal bepalen van **[!UICONTROL Very low]** tot **[!UICONTROL Very high]**.

>[!NOTE]
>
>Het is niet mogelijk om de volgorde te bepalen waarin berichten worden verzonden vanuit een levering.

### IP-affiniteiten instellen

Om het uitgaande verkeer beter te controleren SMTP, kunt u affiniteiten beheren door te bepalen welke specifieke IP adressen voor elke affiniteit kunnen worden gebruikt. Hiermee kunt u het aantal e-mails voor specifieke leveringen beperken tot computers of uitvoeradressen. U kunt bijvoorbeeld één affiniteit per land of subdomein gebruiken. Vervolgens kunt u één typologie per land maken en elke affiniteit koppelen aan de overeenkomstige typologie.

U kunt:

* Definieer de IP-affiniteiten in het configuratiebestand serverConf.xml. [Meer informatie](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Voor elk element IPAffinity, verklaar de IP adressen die kunnen worden gebruikt. [Meer informatie](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In de [typologie](../../campaign-opt/using/about-campaign-typologies.md) van uw keuze gebruikt u de **[!UICONTROL Managing affinities with IP addresses]** veld voor het koppelen van leveringen aan de bezorgserver (MTA) die de opgegeven affiniteit beheert. [Meer informatie](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Zodra e-mail wordt verzonden, controleer de kopbal om te verifiëren welk IP adres de levering van werd verzonden. De e-mailbeheerder moet u helpen de koptekstgegevens op te halen.

* Voor SMS-leveringen moet u ervoor zorgen dat het SMS-kanaal een specifieke affiniteit heeft die beperkt is tot **één** toepassingsservercontainer. [Meer informatie](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>De meeste van deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

### Typologieën gebruiken

U kunt typologische regels gebruiken om een deel van het doel uit te sluiten op basis van specifieke criteria. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie. U kunt bijvoorbeeld de ontvangers die jonger zijn, filteren van het doel van de nieuwsbrief. Meer informatie [in dit voorbeeld](../../campaign-opt/using/filtering-rules.md).

### Bijlagen voorkomen

Bijlagen blijven een van de meest voorkomende vectoren voor de proliferatie van malware, vooral wanneer ze bulksgewijs worden verzonden. Neem een beveiligde koppeling naar het document op in plaats van deze te koppelen. Dit verzekert een extra laag van veiligheid om onbedoelde herdistributie te verhinderen, en vermindert enorm de kansen dat het bericht bij binnenkomende e-mailgateways voor berichtgrootte of veiligheidsredenen zal worden verworpen.
