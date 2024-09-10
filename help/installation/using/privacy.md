---
product: campaign
title: Personalisatie en privacy
description: Meer informatie over best practices op het gebied van beveiliging voor privacy en personalisatie
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Personalisatie en privacy {#privacy}

## URL PERSONALIZATION {#url-personalization}

Wanneer u persoonlijke koppelingen toevoegt aan uw inhoud, moet u altijd geen persoonlijke instellingen opgeven in het gedeelte hostnaam van de URL om mogelijke beveiligingsproblemen te voorkomen. De volgende voorbeelden mogen nooit in alle URL-kenmerken &lt;`a href="">` of `<img src="">` worden gebruikt:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Aanbeveling

Om te bevestigen en ervoor te zorgen dat u hierboven niet gebruikt, stel een vraag bij het volgen van een lijst URL via [ de Algemene Redacteur van de Vraag van de Campagne ](../../platform/using/steps-to-create-a-query.md) in werking of creeer een werkschema met filtercriteria in de [ vraagactiviteit ](../../workflow/using/query.md).

Voorbeeld:

1. Creeer een werkschema en voeg de activiteit van de a **Vraag** toe. [Meer informatie](../../workflow/using/query.md).

1. Open de **activiteit van de Vraag** en creeer een filter op de `nmsTrackingUrl` lijst als volgt:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Voer de workflow uit en controleer of er resultaten zijn.

1. Als dat het geval is, opent u de uitvoerovergang om de lijst met URL&#39;s weer te geven.

   ![](assets/privacy-query-dynamic-url.png)


### URL-handtekening

Om de veiligheid te verbeteren, is een handtekeningmechanisme geïntroduceerd voor het bijhouden van koppelingen in e-mails. De build is beschikbaar vanaf 19.1.4 (9032@3a9dc9c) en 20.2. Deze functie is standaard ingeschakeld.

>[!NOTE]
>
>Wanneer op een onjuist ondertekende URL wordt geklikt, wordt deze fout geretourneerd: `Requested URL '…' was not found.`

Bovendien kunt u een verbetering gebruiken om URLs onbruikbaar te maken die in vorige bouwstijlen worden geproduceerd. Deze functie is standaard uitgeschakeld. U kunt uit aan [ de Zorg van de Klant ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) bereiken om deze eigenschap toe te laten.

Als u werkt op de build 19.1.4, kan het zijn dat u problemen ondervindt met de levering van pushberichten via koppelingen voor reeksspatiëring of met ankerlabels. Als dat het geval is, raden we u aan de URL-handtekening uit te schakelen.

Als Ontvangen Campagne, Beheerde Cloud Servicen of hybride klant, moet u uit [ de Zorg van de Klant ](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) bereiken om de handtekening te hebben URL gehandicapt.

Als u Campagne in een hybride architectuur in werking stelt, alvorens u URL handtekening toelaat, zorg ervoor dat de ontvangen mid-sourcing instantie als volgt is bevorderd:

* Eerste marketinginstantie op locatie
* Voer vervolgens een upgrade uit naar dezelfde versie als de marketinginstantie op locatie of naar een iets hogere versie

Anders kunnen enkele van deze problemen optreden:

* Voordat de mid-sourcing-instantie wordt bijgewerkt, worden URL&#39;s zonder handtekening verzonden via deze instantie.
* Nadat de mid-sourcing-instantie is bijgewerkt en de URL-handtekening op beide instanties is ingeschakeld, worden de URL&#39;s die eerder zonder handtekening waren verzonden, afgewezen. De reden is dat een handtekening wordt aangevraagd door de volgende bestanden die door het marketingexemplaar zijn opgegeven.

Als u URL&#39;s wilt uitschakelen die zijn gegenereerd in eerdere builds, voert u de volgende stappen uit op alle Campagneservers tegelijk:

1. In het dossier van de serverconfiguratie (`serverConf.xml`), verander **blockRedirectForUnsignedTrackingLink** optie in **waar**.
1. Start de service `nlserver` opnieuw.
1. Start de `web` -server (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows) opnieuw op de `tracking` -server.

Als u URL-ondertekening wilt inschakelen, voert u de volgende stappen uit op alle campagnemeservers tegelijk:

1. In het dossier van de serverconfiguratie (`serverConf.xml`), verandering **signEmailLinks** optie, **waar**.
1. Begin de **nlserver** dienst opnieuw.
1. Start de `web` -server (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows) opnieuw op de `tracking` -server.

## Gegevensbeperking

U moet ervoor zorgen dat de gecodeerde wachtwoorden niet toegankelijk zijn voor gebruikers met lage bevoegdheden. Hiervoor beperkt u alleen de toegang tot wachtwoordvelden of tot de gehele entiteit (u hebt een build >= 8770 nodig).

Met deze beperking kunt u wachtwoordvelden verwijderen, maar de externe account is wel toegankelijk via de interface voor alle gebruikers. [Meer informatie](../../configuration/using/restricting-pii-view.md).

Volg onderstaande stappen om dit te doen:

1. Blader naar de map **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** van de Campagneverkenner.

1. Maak als **[!UICONTROL Extension of a schema]** een gegevensschema.

   ![](assets/privacy-data-restriction.png)

1. Kies **[!UICONTROL External Account]** (extAccount).

1. In het laatste hulpscherm, geef uw nieuw &quot;srcSchema&quot;uit om toegang tot alle wachtwoordgebieden te beperken:

   U kunt het hoofdelement (`<element name="extAccount" ... >`) vervangen door:

   ```sql
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

   ```sql
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
   >U kunt `$(loginId) = 0 or $(login) = 'admin'` vervangen door `hasNamedRight('admin')` zodat alle gebruikers met beheerdersrechten deze wachtwoorden kunnen zien.

## Protect-pagina&#39;s met PI

We raden klanten op locatie ten zeerste aan de pagina&#39;s te beschermen die persoonlijke gegevens (PI) kunnen bevatten, zoals spiegel- en webtoepassingen.

Het doel van deze procedure is te voorkomen dat deze pagina&#39;s worden geïndexeerd, waardoor een mogelijk beveiligingsrisico wordt vermeden. Hier volgen enkele handige artikelen:

* [ https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [ https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Voer de volgende stappen uit om uw pagina&#39;s te beveiligen:

1. Voeg een `robots.txt` -bestand toe aan de hoofdmap van uw webserver (Apache of IIS). Hier volgt de inhoud van het bestand:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Voor IIS, verwijs naar [ deze pagina ](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Voor Apache, kunt u het dossier in **plaatsen /var/www/robots.txt** (Debian).

1. Soms is het toevoegen van a **robots.txt** dossier niet voldoende in termen van veiligheid. Als een andere website bijvoorbeeld een koppeling naar uw pagina bevat, wordt deze mogelijk weergegeven in een zoekresultaat.

   Naast het {**dossier 0} robots.txt, wordt het geadviseerd om a** x-robots-markering **kopbal toe te voegen.** U kunt het in Apache of IIS en in het **serverConf.xml** configuratiedossier doen.

   Voor meer informatie, verwijs naar [ dit artikel ](https://developers.google.com/search/reference/robots_meta_tag).


## Privacyverzoeken

Verwijs naar [ deze pagina ](../../platform/using/privacy-management.md) voor algemene informatie over wat het Beheer van de Privacy en de implementatiestappen in Adobe Campaign is. U zult ook beste praktijken en een overzicht van het gebruikersproces en persona&#39;s vinden.
