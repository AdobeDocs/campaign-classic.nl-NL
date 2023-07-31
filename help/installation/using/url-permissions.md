---
product: campaign
title: URL-machtigingen configureren
description: Leer hoe u URL-machtigingen configureert
feature: Installation, Instance Settings, Permissions
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 29%

---

# URL-machtigingen configureren (op locatie){#url-permissions}



De standaardlijst met URL’s die via JavaScript-codes kunnen worden aangeroepen (workflows, enz.) door uw Campaign Classic-instanties, is beperkt. Dit zijn URL’s waardoor uw instanties correct kunnen werken.

Instanties mogen standaard geen verbinding maken met externe URL’s. Het is echter mogelijk om sommige externe URL&#39;s toe te voegen aan de lijst met geoorloofde URL&#39;s, zodat uw instantie hiermee verbinding kan maken. Hierdoor kunt u uw Campaign-instanties verbinden met externe systemen zoals SFTP-servers of websites, om de overdracht van bestanden en/of data mogelijk te maken.

>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.
>
>Als **gehost** klant, als u toegang hebt tot [Campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl), kunt u de interface van de URL toestemmingen zelf gebruiken. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=nl)
>
>Overige **hybride/gehost** de klanten moeten uit bereiken aan het ondersteuningsteam van Adobe om IP aan de lijst van gewenste personen toe te voegen.
>

Voor **Hybride** en **Op locatie** implementaties, moet de beheerder naar een nieuwe **urlPermission** in de **serverConf.xml** bestand.


Er zijn drie modi voor verbindingsbeveiliging beschikbaar:

* **Blokkeren**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, worden geblokkeerd, met een foutbericht. Dit is de standaardwijze na een postupgrade.
* **Permissief**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, zijn toegestaan.
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
>Nieuwe implementaties gebruiken standaard de opdracht **Blokkeren** -modus.
>
>Als bestaande klant die uit een migratie komt, kunt u tijdelijk gebruikmaken van de **Waarschuwing** -modus. Analyseer het uitgaande verkeer alvorens URLs toe te staan. Als de lijst met toegestane URL&#39;s is gedefinieerd, kunt u de URL&#39;s toevoegen aan de lijst van gewenste personen en de URL activeren **Blokkeren** -modus.

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl)
* [Hostmodellen](hosting-models.md)
* [Configuratie van de Campaign-server](configuring-campaign-server.md)
* [Parameters van het configuratiebestand van de Campagneserver](the-server-configuration-file.md)
* [Controlelijst voor beveiliging en privacy](get-started-security-privacy.md)
