---
product: campaign
title: Afleveringsfouten en quarantainebeheer
description: Leer hoe u fouten bij de levering begrijpt en quarantines beheert in Campaign Classic v7
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 1%

---

# Afleveringsfouten en quarantainebeheer {#delivery-failures-quarantine}

>[!NOTE]
>
>Uitgebreide instructies over leveringstekorten en quarantainebeheer worden beschreven in de documentatie van Campagne v8. Deze inhoud is van toepassing op gebruikers van Campaign Classic v7 en Campagne v8:
>
>* [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} - behandelt mislukkingstypes, foutenredenen, synchrone/asynchrone fouten, herprobeert beheer, en het oplossen van problemen
>* [&#x200B; het beheer van de quarantaine &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} - behandelt quarantaine vs lijst van gewezen personen, zachte foutendrempels, quarantainerapporten, en adresverwijdering
>
>Deze pagina documenteert **Campaign Classic v7-specifieke configuratie** voor stuit post en quarantainebeheer in hybride en op-gebouw plaatsingen.

## Leveringsfouten begrijpen

Voor gemeenschappelijke concepten van de leveringsmislukking, foutentypes, en het oplossen van problemenbegeleiding, verwijs naar de [&#x200B; Campagne v8 die de documentatie van de leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} begrijpen.

## Bounce mail-configuratie {#bounce-mail-config}

De volgende configuratieopties zijn beschikbaar voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7** om stuiterende postverwerking te beheren.

### Vorm van postvak stuiteren {#bounce-mailbox-configuration}

Voor installaties op-gebouw, is de configuratie van de stuiterende brievenbus gedetailleerd in [&#x200B; deze sectie &#x200B;](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

De asynchrone foutenmeldingen worden verzameld door het platform van Adobe Campaign door de stuiterende brievenbus en door het inMail proces gekwalificeerd om de lijst van e-mailbeheerregels te verrijken.

>[!NOTE]
>
>Voor Campagne v8 Managed Cloud Services-gebruikers wordt de configuratie van de stuiterende mailbox uitgevoerd en beheerd door Adobe. Er is geen configuratie vereist.

### Bounce-mailkwalificatiebeheer {#bounce-mail-qualification-management}

Voor installaties op locatie en de gehoste/hybride installaties die de oude Campagne MTA gebruiken, wanneer de levering van een e-mail ontbreekt, ontvangt de de leveringsserver van Adobe Campaign een foutenmelding van de overseinenserver of de verre DNS server. De lijst met fouten bestaat uit tekenreeksen in het bericht dat door de externe server wordt geretourneerd. De types en de redenen van mislukkingen worden toegewezen aan elk foutenbericht.

Deze lijst is beschikbaar via het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** . Het bevat alle regels die Adobe Campaign gebruikt om leveringsfouten te kwalificeren. Het is niet-limitatief en wordt regelmatig door Adobe Campaign bijgewerkt en kan ook door de gebruiker worden beheerd.

![](assets/tech_quarant_rules_qualif.png)

Het bericht dat door de externe server wordt geretourneerd bij de eerste instantie van dit fouttype, wordt weergegeven in de kolom **[!UICONTROL First text]** van de tabel **[!UICONTROL Delivery log qualification]** . Als deze kolom niet wordt weergegeven, klikt u op de knop **[!UICONTROL Configure list]** rechts onder aan de lijst om deze te selecteren.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert dit bericht om de inhoud van de variabele (zoals id&#39;s, datums, e-mailadressen, telefoonnummers, enz.) te verwijderen en geeft het gefilterde resultaat weer in de kolom **[!UICONTROL Text]** . De variabelen worden vervangen door **`#xxx#`** , behalve adressen die worden vervangen door **`*`** .

Dit proces staat toe om alle mislukkingen van het zelfde type samen te brengen en veelvoudige ingangen voor gelijkaardige fouten in de de kwalificatielijst van het Logboek van de Levering te vermijden.

>[!NOTE]
>
>In het veld **[!UICONTROL Number of occurrences]** wordt het aantal exemplaren van het bericht in de lijst weergegeven. Het is beperkt tot 100 000 voorvallen. U kunt het veld bewerken als u het bijvoorbeeld opnieuw wilt instellen.

Stuitberichten kunnen de volgende kwalificatiestatus hebben:

* **[!UICONTROL To qualify]** : de stuiterende post kan niet worden gekwalificeerd. De kwalificatie moet aan het leveringsteam worden toegewezen om efficiënte platformleverantie te waarborgen. Zolang het niet gekwalificeerd is, wordt de stuiterende post niet gebruikt om de lijst van e-mailbeheerregels te verrijken.
* **[!UICONTROL Keep]**: de stuiterende post werd gekwalificeerd en zal door **worden gebruikt verfrissen zich voor leverability** werkschema om aan bestaande e-mailbeheerregels worden vergeleken en de lijst verrijken.
* **[!UICONTROL Ignore]**: de stuiterende post wordt genegeerd door de Campagne MTA, betekenend dat deze stuit nooit het adres van de ontvanger zal veroorzaken om in quarantined te zijn. Het zal niet door **worden gebruikt verfrissen zich voor leverability** werkschema en het zal niet naar cliëntinstanties worden verzonden.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In het geval van een stroomonderbreking van ISP, zullen de e-mails die door Campaign worden verzonden verkeerd als stegels worden gemerkt. U moet de stuiterkwalificatie bijwerken om dit te corrigeren. Ga voor meer informatie naar [deze pagina](update-bounce-qualification.md).

### Configuratie van regels voor e-mailbeheer {#email-management-rules}

E-mailregels zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** . De regels voor e-mailbeheer worden weergegeven in het onderste gedeelte van het venster.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>De standaardparameters van het platform worden gevormd in de plaatsingstovenaar. Voor verdere informatie, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/deploying-an-instance.md).

De standaardregels zijn als volgt:

>[!IMPORTANT]
>
>* De leveringsserver (MTA) moet opnieuw worden begonnen als de parameters zijn veranderd.
>* De wijziging of invoering van beheerregels is alleen voor professionele gebruikers.

#### Binnenkomende e-mail {#inbound-email}

Deze regels bevatten de koorden die door verre servers kunnen zijn teruggekeerd en die u toelaten om de fout (**Vaste**, **Zacht** of **Genegeerde**) te kwalificeren.

Wanneer een e-mail mislukt, retourneert de externe server een stuiterend bericht naar het adres dat is opgegeven in de platformparameters. Adobe Campaign vergelijkt de inhoud van elk stuiterend bericht met de koorden in de regellijst, en wijst het dan één van de drie foutentypes toe.

>[!NOTE]
>
>De gebruiker kan zijn eigen regels tot stand brengen. Wanneer het invoeren van een pakket en wanneer het bijwerken van gegevens via **verfrissen zich voor leverability** werkschema, worden de user-created regels beschreven.

Voor meer op de kwalificatie van de stuiterende post, verwijs naar [&#x200B; deze sectie &#x200B;](#bounce-mail-qualification-management).

#### Domeinbeheer {#domain-management}

Voor op-gebouw installaties, past MTA één enkele **het beheersregel van het Domein** op alle domeinen toe.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* U kunt kiezen al dan niet om bepaalde identificatienormen en encryptiesleutels te activeren om de domeinnaam, zoals **identiteitskaart van de Afzender**, **DomainKeys**, **DKIM**, en **S/MIME** te controleren.
* De **SMTP relais** parameters laten u het IP adres en de haven van een relaisserver voor een bepaald domein vormen. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#smtp-relay) voor meer informatie.

Als uw berichten **[!UICONTROL on behalf of]** in het afzenderadres tonen, zorg ervoor niet om e-mails met **identiteitskaart van de Afzender** te ondertekenen, die de verouderde merkgebonden standaard van de e-mailauthentificatie van Microsoft is. Als de **[!UICONTROL Sender ID]** optie wordt toegelaten, uncheck de overeenkomstige doos en contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). De leverbaarheid wordt niet beïnvloed.

#### MX-beheer {#mx-management}

Voor installaties op locatie worden MX-beheerregels gebruikt om de stroom van uitgaande e-mails voor een bepaald domein te regelen.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

Deze regels zijn beschikbaar in de plaatsingstovenaar en kunnen worden aangepast:

* **[!UICONTROL MX Management]**: deze regel wordt gebruikt om de stroom van uitgaande e-mails voor een domein te controleren. Het steekproeven stuit berichten en blokkeert verzendend waar nodig.

* **[!UICONTROL Period]**: het tijdframe waarin berichten worden vertraagd of geblokkeerd.

* **[!UICONTROL Limit]**: het maximale aantal berichten dat per tijdsperiode is toegestaan.

* **[!UICONTROL Type]**: het fouttype (hard, zacht of genegeerd) dat wordt gebruikt om het verzendgedrag te bepalen. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} voor foutentype definities.

Voor meer op MX beheer, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>Voor Campagne v8 Managed Cloud Services-gebruikers worden MX-regels en e-mailflowbeheer door Adobe beheerd als onderdeel van de beheerde infrastructuur. Neem contact op met de klantenservice van Adobe als u de MX-instellingen voor specifieke gebruiksgevallen moet aanpassen.

## Quarantainebeheer {#quarantine-management}

Voor uitvoerige richtlijnen van het quarantainebeheer, verwijs naar de [&#x200B; het beheersdocumentatie van de Campagne v8 Quarantine &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantaineconfiguratie {#quarantine-config}

De volgende configuratieopties zijn beschikbaar voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7** om quarantainegedrag aan te passen.

### Configuratie van drempelwaarde voor zachte fout {#soft-error-threshold}

Voor installaties op locatie die de oudere Campagne MTA gebruiken, kunt u het aantal fouten en de periode tussen twee fouten wijzigen alvorens een adres quarantined is.

Deze instellingen configureren:

1. Via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]** kunt u de wizard Implementatie openen.
2. Ga naar **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configureren:
   * **Aantal fouten**: Het maximumaantal zachte fouten alvorens een adres wordt quarantined (gebrek: 5)
   * **Periode tussen twee significante fouten**: Het tijdvenster (in seconden) voor fout het tellen (gebrek: 86.400 seconden = 1 dag)

Wanneer de foutenteller de drempel bereikt, is het adres quarantined. Als de laatste significante fout meer dan 10 dagen geleden voorkwam, wordt de foutenteller opnieuw geïnitialiseerd.

Voor meer details, verwijs naar [&#x200B; deze pagina &#x200B;](communication-channels.md) onder **het verzenden van de Levering** > **vormen opnieuw probeert**.

>[!NOTE]
>
>Voor Campagne v8 Managed Cloud Services-gebruikers worden instellingen voor opnieuw proberen en drempelwaarden voor fouten beheerd door Adobe op basis van IP-prestaties en domeinreputatie. Er is geen configuratie vereist.

### Workflow voor het opschonen van databases {#database-cleanup-workflow}

Voor installaties op locatie verwijdert de technische workflow van **[!UICONTROL Database cleanup]** automatisch quarantineadressen die overeenkomen met specifieke voorwaarden.

Open deze workflow via **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]** .

De workflow verwijdert adressen uit quarantaine in de volgende gevallen:

* Hiermee wordt de status **[!UICONTROL With errors]** na een geslaagde levering geactiveerd
* Hiermee wordt de status **[!UICONTROL With errors]** toegevoegd als de laatste zachte stuit meer dan 10 dagen geleden is opgetreden
* Vermeldt de status **[!UICONTROL With errors]** met de fout **[!UICONTROL Mailbox full]** na 30 dagen

Zorg ervoor dat deze workflow regelmatig wordt uitgevoerd (aanbevolen: dagelijks) om de hygiëne van de quarantainelijst te handhaven.

Voor meer op gegevensbestandschoonmaakbeurt, verwijs naar [&#x200B; deze sectie &#x200B;](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services wordt de workflow voor het opschonen van databases gecontroleerd en beheerd door Adobe.

### quarantainespecificaties voor pushmeldingen {#push-quarantine-specifics}

Voor Campaign Classic v7 volgen pushmeldingen het algemene quarantainemechanisme met bepaalde kanaalspecifieke gedragingen.

Voor **iOS** en **Android** dupberichten, gebruikt het quarantainemechanisme apparatentokens eerder dan e-mailadressen. Wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd, wordt het bijbehorende token in quarantaine geplaatst.

Voor gedetailleerde informatie over de scenario&#39;s van de duw- bericht quarantaine (de foutentypes van iOS en van Android, retry gedrag, enz.), verwijs naar de [&#x200B; Begrijpende documentatie van de leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} die uitvoerige het type van de dupmeldingsfout lijsten omvat.

### SMS-quarantainespecificaties {#sms-quarantine-specifics}

Voor Campaign Classic v7, volgen SMS quarantines het algemene quarantainemechanisme met wat kanaal-specifieke gedrag met betrekking tot telefoonaantallen eerder dan e-mailadressen.

Het quarantainemechanisme van SMS varieert afhankelijk van de gebruikte schakelaar:

* **StandaardSMPP schakelaars**: De kwalificatieregels van de fout die in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** worden bepaald zijn op de leveringen van SMS van toepassing.

* **Uitgebreide generische schakelaar SMPP**: Het beheer van de fout wordt behandeld verschillend gebruikend regelmatige uitdrukkingen (regexes) om de berichten van het Rapport van de Status (SR) te ontleden die door de leverancier SMSC zijn teruggekeerd.

Voor gedetailleerde informatie over de quarantainescenario&#39;s van SMS en foutentypes, verwijs naar [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentatie die uitvoerige de foutenentabellen van SMS omvat.

## Verwante onderwerpen

* [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; het beheer van de quarantaine &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; beste praktijken van de Levering &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; leveringsstatussen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; het schoonmaakbeurtenwerkschema van het Gegevensbestand &#x200B;](../../production/using/database-cleanup-workflow.md) (v7 hybride/op-gebouw)
* [&#x200B; vorm levering opnieuw probeert &#x200B;](communication-channels.md) (v7 hybride/op-gebouw)
* [&#x200B; stuitkwalificatie van de update &#x200B;](update-bounce-qualification.md) (v7 hybride/op-gebouw)
* [&#x200B; de configuratie van de E-maillevering &#x200B;](../../installation/using/email-deliverability.md) (v7 hybride/op-gebouw)
* [&#x200B; die een instantie &#x200B;](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 hybride/op-gebouw) opstelt

