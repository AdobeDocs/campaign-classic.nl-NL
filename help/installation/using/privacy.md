---
product: campaign
title: Privacy
description: Klik hier als je meer wilt weten over de beste praktijken op het gebied van privacy.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 5%

---

# Privacy {#privacy}

## Privacyverzoeken

Adobe Campaign biedt een reeks tools om u te helpen de privacyvereisten voor AVG en CCPA na te leven.

Raadpleeg [deze pagina](../../platform/using/privacy-management.md) voor algemene informatie over wat het Privacybeheer is en de implementatiestappen in Adobe Campaign. U zult ook beste praktijken en een overzicht van het gebruikersproces en persona&#39;s vinden.

## URL-aanpassing {#url-personalization}

Wanneer u persoonlijke koppelingen toevoegt aan uw inhoud, moet u altijd geen persoonlijke instellingen opgeven in het gedeelte hostnaam van de URL om mogelijke hiaten in de beveiliging te voorkomen. De volgende voorbeelden mogen nooit worden gebruikt in alle URL-kenmerken &lt;`a href="">` of `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Aanbeveling

Om te bevestigen en ervoor te zorgen dat u hierboven niet gebruikt, stel een vraag bij het volgen van Url- lijst via [de Algemene Redacteur van de Vraag van de Campagne](../../platform/using/steps-to-create-a-query.md) in werking of creeer een werkschema met filtercriteria in [vraagactiviteit](../../workflow/using/query.md).

Voorbeeld:

1. Maak een workflow en voeg een query-activiteit toe. Meer informatie.

1. Open de activiteit van de Vraag en creeer een filter op de lijst nmsTrackingUrl als volgt: bron-URL begint met http://&lt;% of bron-URL begint met https://&lt;%.

1. Voer de workflow uit en controleer of er resultaten zijn.

1. Als dat het geval is, opent u de uitvoerovergang om de lijst met URL&#39;s weer te geven.

<img src="assets/privacy-query-dynamic-url.png">

### Handtekeningmechanisme

Om de veiligheid te verbeteren, is een nieuw handtekeningmechanisme voor het volgen van verbindingen in e-mails geïntroduceerd in Versie 19.1.4 (9032@3a9dc9c), en is beschikbaar in Bouwstijl 19.1.4 (9032@3a9dc9c) en Campagne 20.2. Deze optie is standaard ingeschakeld voor alle klanten.

>[!NOTE]
>
>Wanneer op een onjuist ondertekende URL wordt geklikt, wordt de volgende fout geretourneerd: &quot;Aangevraagde URL &#39;...&#39; is niet gevonden.&quot;

Bovendien kunnen gehoste en hybride klanten met de startversie van Campagne 20.2 en [!DNL Gold Standard] een verbetering gebruiken om URL&#39;s uit eerdere builds uit te schakelen. Deze optie is standaard uitgeschakeld. U kunt [Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) bereiken om deze functie in te schakelen.

Om dit nieuwe mechanisme te activeren, moeten on-premise klanten deze stappen op alle servers van de Campagne volgen:

1. Wijzig **blockRedirectForUnsignedTrackingLink** in **true** in het serverconfiguratiebestand (serverConf.xml).
1. Start de **nlserver**-service opnieuw.
1. Start de webserver op de trackingserver opnieuw (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows).

Klanten die op [!DNL Gold Standard] 19.1.4 worden uitgevoerd, kunnen problemen ondervinden met de levering van pushberichten via een koppeling voor bijhouden of leveringen met behulp van ankerlabels. In dat geval raadt Adobe aan het nieuwe handtekeningmechanisme voor het bijhouden van koppelingen uit te schakelen:

**Gehoste en hybride** klanten moeten contact opnemen met  [Customer ](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) Cares om dit mechanisme uit te schakelen.

**Op locatie kunnen** klanten de onderstaande stap volgen:

1. Wijzig **signEmailLinks** in **false** in het serverconfiguratiebestand (serverConf.xml).
1. Start de **nlserver**-service opnieuw.
1. Start de webserver op de trackingserver opnieuw (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows).

## Gegevensbeperking

U moet ervoor zorgen dat de gecodeerde wachtwoorden niet toegankelijk zijn voor gebruikers met lage bevoegdheden. Hiervoor zijn er twee hoofdlijnen: toegang tot wachtwoordvelden alleen of tot de gehele entiteit beperken (moet u een build >= 8770 hebben).

Met deze beperking kunt u wachtwoordvelden verwijderen, maar de externe account is wel toegankelijk via de interface voor alle gebruikers. Zie [deze pagina](../../configuration/using/restricting-pii-view.md).

1. Ga in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Maak een nieuwe **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Kies **[!UICONTROL External Account]** (extAccount).

1. In het laatste tovenaar scherm, kunt u uw nieuw srcSchema uitgeven om toegang tot alle wachtwoordgebieden te beperken:

   U kunt het hoofdelement (`<element name="extAccount" ... >`) vervangen door:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Zo kan uw uitgebreide srcSchema als kijken:

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >U kunt `$(loginId) = 0 or $(login) = 'admin'` door `hasNamedRight('admin')` vervangen om alle gebruikers met het juiste admin deze wachtwoorden te laten zien.

## Pagina&#39;s met PII beveiligen

Wij raden klanten op locatie ten zeerste aan de pagina&#39;s te beschermen die persoonlijke gegevens kunnen bevatten, zoals spiegel- en webtoepassingen.

Het doel van deze procedure is te voorkomen dat deze pagina&#39;s worden geïndexeerd, waardoor een mogelijk beveiligingsrisico wordt vermeden. Hier volgen enkele handige artikelen:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Voer de volgende stappen uit om uw pagina&#39;s te beveiligen:

1. Voeg een bestand robots.txt toe aan de hoofdmap van uw webserver (Apache of IIS). Hier volgt de inhoud van het bestand:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Voor IIS, verwijs naar [deze pagina](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Voor Apache kunt u het bestand plaatsen in **/var/www/robots.txt** (Debian).

1. Soms is het toevoegen van een **robots.txt** dossier niet voldoende in termen van veiligheid. Als een andere website bijvoorbeeld een koppeling naar uw pagina bevat, wordt deze mogelijk weergegeven in een zoekresultaat.

Naast het bestand **robots.txt** wordt aangeraden een **X-Robots-Tag**-header toe te voegen. U kunt het in Apache of IIS en in het **serverConf.xml** configuratiedossier doen.

Raadpleeg [dit artikel](https://developers.google.com/search/reference/robots_meta_tag) voor meer informatie.
