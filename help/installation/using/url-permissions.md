---
solution: Campaign Classic
product: campaign
title: URL-machtigingen configureren
description: Leer hoe u URL-machtigingen configureert
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 23%

---


# URL-machtigingen configureren (op locatie){#url-permissions}

De standaardlijst met URL’s die via JavaScript-codes kunnen worden aangeroepen (workflows, enz.) door uw Campaign Classic-instanties, is beperkt. Dit zijn URL’s waardoor uw instanties correct kunnen werken.

Instanties mogen standaard geen verbinding maken met externe URL’s. Het is echter mogelijk om sommige externe URL&#39;s toe te voegen aan de lijst met geoorloofde URL&#39;s, zodat uw instantie hiermee verbinding kan maken. Hierdoor kunt u uw Campaign-instanties verbinden met externe systemen zoals SFTP-servers of websites, om de overdracht van bestanden en/of data mogelijk te maken.

>[!NOTE]
>
>Deze procedure is beperkt tot **on-premise** plaatsingen.
>
>Als **gehoste** klant, als u tot [Controlebord van de Campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) kunt toegang hebben, kunt u de de toestemmingen gebruiken zelfinstellings interface van URL. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>Andere **hybride/gehoste** klanten moeten zich tot het ondersteuningsteam van Adobe richten om IP aan de lijst van gewenste personen toe te voegen.


Voor **Hybride** en **On-premise** plaatsingen, moet de beheerder een nieuwe **urlPermission** in **serverConf.xml** dossier van verwijzingen voorzien.


Er zijn drie modi voor verbindingsbeveiliging beschikbaar:

* **Blokkeren**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, worden geblokkeerd, met een foutbericht. Dit is de standaardwijze na een postupgrade.
* **Toestemming**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, zijn toegestaan.
* **Waarschuwing**: alle URL&#39;s die niet tot de lijst van gewenste personen behoren, zijn toegestaan, maar de JS-interpreter geeft een waarschuwing weer, zodat de beheerder deze kan verzamelen. In deze modus worden JST-310027-waarschuwingsberichten toegevoegd.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Nieuwe implementaties gebruiken standaard de modus **Blokkeren**.
>
>Als bestaande klant die afkomstig is uit een migratie, kunt u tijdelijk de **waarschuwingsmodus** gebruiken. Analyseer het uitgaande verkeer alvorens URLs toe te staan. Als de lijst met toegestane URL&#39;s is gedefinieerd, kunt u de URL&#39;s toevoegen aan de lijst van gewenste personen en de modus **Blokkeren** activeren.

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Hostmodellen](hosting-models.md)
* [Configuratie van de Campaign-server](configuring-campaign-server.md)
* [Parameters van het configuratiebestand van de Campagneserver](the-server-configuration-file.md)
* [Controlelijst voor beveiliging en privacy](get-started-security-privacy.md)