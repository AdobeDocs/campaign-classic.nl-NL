---
product: campaign
title: MX-servers gebruiken met Campaign
description: Meer informatie over hoe MX-servers werken met Adobe Campaign Classic
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 1%

---

# MX-servers gebruiken met Campaign {#using-mx-servers}



Leer hoe MX-servers werken met Adobe Campaign Classic.

## MX-servers {#mx-servers}

### Wat is een MX-server?

Een mailuitwisselingsverslag (MX verslag) is een type van middelverslag in het Systeem van de Naam van het Domein (DNS) dat een postserver verantwoordelijk voor het goedkeuren van e-mailberichten namens een domein specificeert.

### Hoe werkt een MX-server?

Wanneer u een e-mail verzendt, zal de softwareserver een verbinding met de ontvankelijke domeinserver vestigen. De communicatie tussen de twee servers gebruikt taal SMTP en een domein kan meer dan één server MX hebben. De verbinding met dit domein zal van de hoogste prioriteit (kleinste cijfer) beginnen en andere servers worden genoemd &quot;reserve&quot;servers. Het verbindingsprotocol moet worden gerespecteerd.

### Hoe werkt een MX-server met Adobe Campaign?

In het verbindingsprotocol moeten de regels worden gerespecteerd om spamming en monopolisering van servers te voorkomen. De belangrijkste zijn de volgende:

* **Maximum aantal toegestane verbindingen**: Wanneer dit aantal wordt gerespecteerd, zijn IPs niet op de lijst van gewezen personen en e-mails worden niet geweigerd toe te schrijven aan extra verbindingen.
* **Maximum aantal berichten**: Tijdens de verbinding, moet het aantal berichten die worden toegestaan worden verzonden worden bepaald. Als dit aantal niet wordt bepaald, zal de server zo veel mogelijk verzenden. Dit resulteert in wordt geïdentificeerd als spammer en wordt toegevoegd aan de lijst van gewezen personen door ISP.
* **Berichten per uur**: Om met uw e-reputatie aan te passen, zal Adobe Campaign het aantal e-mails controleren uw IPs per uur kunnen verzenden. Dit systeem beschermt u tegen e-mailweigering of lijst van gewezen personen.

## E-mailberichten opsturen

### Wat is een e-mailbericht voor &#39;Stuiteren&#39;?

Dit is het proces dat Adobe Campaign gebruikt om fouten tijdens servercommunicatie te verwerken.

### Hoe werkt een Inbounce-e-mail?

Het foutenadres zal stuitingen verwerken die door ISPs worden teruggestuurd. Het proces zal verschillende SMTP foutencodes analyseren en de juiste actie volgens de norm toepassen RegEx.

Bijvoorbeeld, heeft een e-mailadres terugkoppelen &quot;550 Gebruiker Onbekend&quot;die door ISP wordt verzonden. Deze foutcode wordt verwerkt door het Adobe Campaign-foutadres (Retournpath-adres). Deze fout wordt dan vergeleken met de norm RegEx en de juiste regel zal van toepassing zijn. E-mail wordt beschouwd als a *Vaste stuit* (aanpassend het type) en dan *Onbekende Gebruiker* (aanpassend de reden) en in quarantaine na de eerste lijn in het systeem geduwd.

### Hoe beheert Adobe Campaign het?

Adobe Campaign beheert dit proces met een overeenkomst tussen een fouttype en een reden:

* **[!UICONTROL User Unknown]**: adres dat syntactisch correct is maar niet bestaat. Deze fout wordt gecategoriseerd als harde stuit en in quarantaine binnen de eerste fout geduwd.
* **[!UICONTROL Mailbox full]**: postbus die de maximale capaciteit heeft bereikt. Deze fout kan ook erop wijzen dat de gebruiker deze brievenbus niet meer gebruikt. Deze fout wordt gecategoriseerd als een zachte stuit en in quarantaine gezet binnen de derde fout en na een periode van 30 dagen verwijderd uit de quarantaine.
* **[!UICONTROL Inactive User]**: De brievenbus is gedeactiveerd door ISP toe te schrijven aan een inactieve gebruiker in de laatste 6 maanden. Deze fout wordt gecategoriseerd als zachte stuit en in quarantaine binnen de derde fout.
* **[!UICONTROL Invalid domain]**: Het domein in het e-mailadres bestaat niet. Deze fout wordt gecategoriseerd als zachte stuit en in quarantaine binnen de derde fout.
* **[!UICONTROL Refused]**: ISP weigerde om e-mail aan zijn gebruikers te leveren. Deze fout wordt gecategoriseerd als zachte stuit en niet in quarantaine geduwd aangezien de fout niet met het e-mailadres maar IP of/een domeinreputatie verbonden is.

>[!NOTE]
>
>Meer over de types en de redenen van de leveringsmislukking leren, verwijs naar deze [&#x200B; sectie &#x200B;](../../delivery/using/delivery-failures-quarantine.md#delivery-failure-types-and-reasons).

## Leverbaarheid-instantie {#deliveratbility-env}

Een dagelijkse update van de MX-regels en -factureringsregels wordt beheerd door een specifieke workflow in de clientinstantie die is verbonden met de eigenaar van de instantie Deliverability van deze regels.

Deze dagelijkse update wordt uitgevoerd voor alle clients die hun exemplaar via een transparantieproces up-to-date willen houden.

De MX-regels hebben zes verschillende productieniveaus, die voornamelijk worden gebruikt tijdens het oploopproces:

![](assets/mx-rules-throughput.png)

De modus Aangepast is voor geavanceerde clients die hun eigen MX-regels willen instellen. Wanneer de modus Aangepast wordt geactiveerd, wordt de client niet bijgewerkt door de instantie van de leveringszekerheid omdat de synchronisatie wordt uitgeschakeld.

## Voorbeelden van stuit

* **Onbekende Gebruiker** (harde stuit): 550 5.1.1.. Gebruiker is onbekend {mx003}
* **Volledige Brievenbus** (zachte stuit): Het quotum van de Gebruiker van 5.2.2 van 550 overschreden
* **Inactieve Brievenbus** (zachte stuit): 550 5.7.1: Ontworpen Ontvangen Ontvangeradres: Inactieve MailBox, niet voor meer dan 6 maanden
* **ongeldig Domein** (zachte stuit): DNS vraag ontbrak voor &quot;ourdan.com&quot;
* **Geweigerd** (zachte stuiter): Binnenkomende e-mailstuit (de regel &quot;Feedback_loop_Hotmail&quot;heeft deze stuit aangepast)
* **Onbereikbaar** (zachte stuit): 421 4.16.55 [ TS01 ] Berichten van x.x.x.x tijdelijk uitgesteld wegens bovenmatige gebruikersklachten

**Verwante onderwerpen:**
* [MX-configuratie](../../installation/using/email-deliverability.md#mx-configuration)
* [Technische e-mailconfiguratie](../../installation/using/email-deliverability.md)
* [Leveringsfouten begrijpen](../../delivery/using/delivery-failures-quarantine.md)
* [&#x200B; Campaign Classic - Technische Aanbevelingen &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
