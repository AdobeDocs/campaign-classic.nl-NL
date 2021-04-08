---
solution: Campaign Classic
product: campaign
title: MX-servers gebruiken met campagne
description: Leer hoe MX-servers werken met Adobe Campaign Classic.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# MX-servers gebruiken met campagne {#using-mx-servers}

Leer hoe MX-servers werken met Adobe Campaign Classic.

## MX-servers {#mx-servers}

### Wat is een MX-server?

Een mailuitwisselingsverslag (MX verslag) is een type van middelverslag in het Systeem van de Naam van het Domein (DNS) dat een postserver verantwoordelijk voor het goedkeuren van e-mailberichten namens een domein specificeert.

### Hoe werkt een MX-server?

Wanneer u een e-mail verzendt, zal de softwareserver een verbinding met de ontvankelijke domeinserver vestigen. De communicatie tussen de twee servers gebruikt taal SMTP en een domein kan meer dan één server MX hebben. De verbinding met dit domein zal van de hoogste prioriteit (kleinste cijfer) beginnen en andere servers worden genoemd &quot;reserve&quot;servers. Het verbindingsprotocol moet worden gerespecteerd.

### Hoe werkt een MX-server met Adobe Campaign?

In het verbindingsprotocol moeten de regels worden gerespecteerd om spamming en monopolisering van servers te voorkomen. De belangrijkste zijn de volgende:

* **Maximum aantal toegestane** verbindingen: Wanneer dit aantal wordt gerespecteerd, zijn IPs niet op de lijst van gewezen personen en e-mails worden niet geweigerd wegens extra verbindingen.
* **Maximum aantal berichten**: Tijdens de verbinding moet het aantal berichten worden gedefinieerd dat mag worden verzonden. Als dit aantal niet wordt bepaald, zal de server zo veel mogelijk verzenden. Dit resulteert in wordt geïdentificeerd als spammer en wordt toegevoegd aan de lijst van gewezen personen door ISP.
* **Berichten per uur**: Adobe Campaign bepaalt het aantal e-mailberichten dat uw IP&#39;s per uur kunnen verzenden om aan uw e-reputatie te voldoen. Dit systeem beschermt u tegen e-mailweigering of lijst van gewezen personen.

## E-mailberichten tonen

### Wat is een e-mailbericht voor &#39;Stuiteren&#39;?

Dit is het proces dat Adobe Campaign gebruikt om fouten tijdens servercommunicatie te verwerken.

### Hoe werkt een Inbounce-e-mail?

Het foutenadres zal stuitingen verwerken die door ISPs worden teruggestuurd. Het proces zal verschillende SMTP foutencodes analyseren en de juiste actie volgens de norm toepassen RegEx.

Bijvoorbeeld, heeft een e-mailadres terugkoppelen &quot;550 Gebruiker Onbekend&quot;die door ISP wordt verzonden. Deze foutcode wordt verwerkt door het Adobe Campaign-foutadres (Retournpath-adres). Deze fout wordt dan vergeleken met de norm RegEx en de juiste regel zal van toepassing zijn. Het e-mailbericht wordt beschouwd als een *Hard stuiteren* (overeenkomend met het type) en vervolgens *Gebruiker onbekend* (overeenkomend met de reden) en in quarantaine geplaatst na de eerste lus in het systeem.

### Hoe beheert Adobe Campaign het?

Adobe Campaign beheert dit proces met een overeenkomst tussen een fouttype en een reden:

* **[!UICONTROL User Unknown]**: Adres dat syntactisch correct is maar niet bestaat. Deze fout wordt gecategoriseerd als harde stuit en in quarantaine binnen de eerste fout geduwd.
* **[!UICONTROL Mailbox full]**: Brievenbus die de maximumcapaciteit heeft bereikt. Deze fout kan ook erop wijzen dat de gebruiker deze brievenbus niet meer gebruikt. Deze fout wordt gecategoriseerd als een zachte stuit en in quarantaine gezet binnen de derde fout en na een periode van 30 dagen verwijderd uit de quarantaine.
* **[!UICONTROL Inactive User]**: De brievenbus is gedeactiveerd door ISP toe te schrijven aan een inactieve gebruiker in de laatste 6 maanden. Deze fout wordt gecategoriseerd als zachte stuit en in quarantaine binnen de derde fout.
* **[!UICONTROL Invalid domain]**: Het domein in het e-mailadres bestaat niet. Deze fout wordt gecategoriseerd als zachte stuit en in quarantaine binnen de derde fout.
* **[!UICONTROL Refused]**: ISP weigerde om e-mail aan zijn gebruikers te leveren. Deze fout wordt gecategoriseerd als zachte stuit en niet in quarantaine geduwd aangezien de fout niet met het e-mailadres maar IP of/een domeinreputatie verbonden is.

>[!NOTE]
>
>Meer over de types en de redenen van de leveringsmislukking leren, verwijs naar dit [sectie](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Deliberability-instantie

Een dagelijkse update van de MX-regels en -factureringsregels wordt beheerd door een specifieke workflow in de clientinstantie die is verbonden met de eigenaar van de instantie Deliverability van deze regels.

Deze dagelijkse update wordt uitgevoerd voor alle clients die hun exemplaar via een transparantieproces up-to-date willen houden.

De MX-regels hebben zes verschillende productieniveaus, die voornamelijk worden gebruikt tijdens het oploopproces:

![](assets/mx-rules-throughput.png)

De modus Aangepast is voor geavanceerde clients die hun eigen MX-regels willen instellen. Wanneer de modus Aangepast wordt geactiveerd, wordt de client niet bijgewerkt door de instantie van de leveringszekerheid omdat de synchronisatie wordt uitgeschakeld.

## Stuitvoorbeelden

* **Gebruiker onbekend**  (harde stuit): 550 5.1.1 ... Gebruiker is onbekend {mx003}
* **Volledige**  postbus (zachte stuit): 550 5.2.2 Gebruikerquotum overschreden
* **Inactieve postbus**  (soft bounce): 550 5.7.1 : Ontvangen adres: Inactive MailBox, niet langer dan 6 maanden opgevuld
* **Domein ongeldig**  (soft bounce): DNS-query is mislukt voor &#39;ourdan.com&#39;
* **Geweigerd**  (zachte stuit): Binnenkomende e-mailbounce (regel &#39;Feedback_loop_Hotmail&#39; komt overeen met deze stuit)
* **Onbereikbaar**  (zachte stuit): 421 4.16.55  [TS01] Berichten van x.x.x.x tijdelijk uitgesteld wegens bovenmatige klachten van gebruikers

**Verwante onderwerpen:**
* [MX-configuratie](../../installation/using/email-deliverability.md#mx-configuration)
* [Technische e-mailconfiguratie](../../installation/using/email-deliverability.md)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Technische Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)