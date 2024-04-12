---
product: campaign
title: Upgraden naar een nieuwe build
description: Leer technische stappen om aan een nieuwe bouwstijl te bevorderen
feature: Monitoring, Upgrade
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 1%

---

# Upgraden naar een nieuwe build (op locatie){#upgrading}



Voordat u het upgradeproces start, bepaalt en bevestigt u welke versie van Adobe Campaign moet worden bijgewerkt naar en raadpleegt u de [Opmerkingen bij de release](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe raadt u ten zeerste aan een databaseback-up te maken voordat u de database bijwerkt. Raadpleeg [deze sectie](../../production/using/backup.md) voor meer informatie.
>* Om een verbetering uit te voeren, zorg ervoor u de capaciteit en de toestemmingen hebt om tot instanties en logboeken toegang te hebben.
>* Uitlezen [deze sectie](../../installation/using/general-architecture.md) en de [upgrade voor build](https://helpx.adobe.com/nl/campaign/kb/acc-build-upgrade.html) hoofdstuk voordat u begint.
>

## Windows {#in-windows}

Voor een Windows-omgeving voert u de onderstaande stappen uit om Adobe Campaign bij te werken naar een nieuwe build:

* [Afsluiten van services](#shut-down-services),
* [De toepassingsserver upgraden](#upgrade-the-adobe-campaign-server-application),
* [Bronnen synchroniseren](#synchronize-resources),
* [Herstartservices](#restart-services).

Raadpleeg voor informatie over het bijwerken van de clientconsole [deze sectie](../../installation/using/client-console-availability-for-windows.md).

### Afsluiten van services {#shut-down-services}

Als u alle bestanden wilt vervangen door de nieuwe versie, moet u alle instanties van de NLSereservice afsluiten.

1. Sluit de volgende services af:

   * Webservices (IIS):

     **iisreset /stop**

   * Adobe Campaign-service: **netstop nlserver6**

   >[!IMPORTANT]
   >
   >U moet er ook voor zorgen dat de omleidingsserver (webmdl) wordt gestopt, zodat **nlsrvmod.dll** bestand dat door IIS wordt gebruikt, kan worden vervangen door de nieuwe versie.

1. Controleer of er geen taken actief zijn door het dialoogvenster **nlserver pdump** gebruiken. Het volgende moet naar voren komen:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   U kunt Windows Taakbeheer gebruiken om ervoor te zorgen dat alle processen worden gestopt.

### De Adobe Campaign-servertoepassing upgraden {#upgrade-the-adobe-campaign-server-application}

Voer de volgende stappen uit om het upgradebestand uit te voeren:

1. Uitvoeren **setup.exe**.

   Maak verbinding met de [Software-distributieportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) met uw gebruikersgegevens. Meer informatie over softwaredistributie in [deze pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

1. Selecteer de installatiemodus: kies **[!UICONTROL Update or repair]**
1. Klikken **[!UICONTROL Next]** .
1. Klikken **[!UICONTROL Finish]** .

   Het installatieprogramma kopieert vervolgens de nieuwe bestanden.

1. Klik op **[!UICONTROL Finish]** .

### Bronnen synchroniseren {#synchronize-resources}

Gebruik de volgende opdrachtregel:

**nlserver config -postupgrade -allinstances**

Op deze manier kunt u de volgende bewerkingen uitvoeren:

* Bronnen synchroniseren
* Schema&#39;s bijwerken
* de database bijwerken

>[!NOTE]
>
>Deze bewerking mag maar één keer worden uitgevoerd, en alleen op een (**nlserver-web**) toepassingsserver.

Controleer vervolgens of de synchronisatie fouten of waarschuwingen heeft gegenereerd. Raadpleeg voor meer informatie hierover [Oplossen van upgradeconflicten](#resolving-upgrade-conflicts).

### Herstartservices {#restart-services}

De diensten die opnieuw moeten worden opgestart zijn:

* Webservices (IIS):

  **iisreset /start**

* Adobe Campaign-service: **netwerkbeginserver6**

## Linux {#in-linux}

Voor een Linux-omgeving voert u de onderstaande stappen uit om Adobe Campaign bij te werken naar een nieuwe build:

* [De bijgewerkte pakketten downloaden](#obtain-updated-packages),
* [De update uitvoeren](#perform-an-update),
* [De webserver opnieuw opstarten](#reboot-the-web-server).

[Meer informatie over beschikbaarheid van clientconsole](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>Vanaf build 8757 is de bibliotheek van derden niet meer nodig.

### Bijgewerkte pakketten ophalen {#obtain-updated-packages}

Begin door beide bijgewerkte pakketten van Adobe Campaign te herstellen: maak verbinding met de [Software-distributieportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) met uw gebruikersgegevens. Meer informatie over softwaredistributie in [deze pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

Het bestand is **nlserver6-v7-XXX.rpm**

### Een update uitvoeren {#perform-an-update}

* RPM-gebaseerde distributie (RedHat, SuSe)

  Als u deze wilt installeren, voert u uit als hoofdmap:

  ```
  $rpm -Uvh nlserver6-v7-XXXX.rpm
  ```

  Hierbij is XXX de versie van het bestand.

  Het rpm-bestand is afhankelijk van pakketten die u kunt vinden op CentOS/Red Hat-distributies. Als u sommige van deze gebiedsdelen niet wilt gebruiken, kunt u de &quot;nodeps&quot;optie van rpm moeten gebruiken:

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

* DEB-distributie (Debian)

  Als u deze wilt installeren, voert u uit als hoofdmap:

  ```
  dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>De volledige installatieprocedures worden nader beschreven in [deze sectie](../../installation/using/installing-campaign-standard-packages.md). De middelen worden automatisch gesynchroniseerd, nochtans moet u ervoor zorgen geen fouten voorkwamen. Raadpleeg voor meer informatie hierover [Verbeteringsconflicten oplossen](#resolving-upgrade-conflicts).

### De webserver opnieuw opstarten {#reboot-the-web-server}

U moet Apache afsluiten voordat de nieuwe bibliotheek van toepassing wordt.

Hiervoor voert u de volgende opdracht uit:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Uw script wordt mogelijk aangeroepen **httpd** in plaats van **pijn**.
>* U MOET dit bevel uitvoeren tot u het volgende antwoord verkrijgt:
>
>   Deze bewerking is vereist om Apache de nieuwe bibliotheek te laten toepassen.

Start vervolgens Apache opnieuw:

```
/etc/init.d/apache start
```

## Verbeteringsconflicten oplossen {#resolving-upgrade-conflicts}

Tijdens resourcesynchronisatie **postupgrade** kunt u nagaan of synchronisatie fouten of waarschuwingen heeft gegenereerd.

### Het synchronisatieresultaat weergeven {#view-the-synchronization-result}

Er zijn twee manieren om het synchronisatieresultaat weer te geven:

* In de bevel-lijn interface, worden de fouten geconcretiseerd door een drievoudig chevron **>>>** en synchronisatie wordt automatisch gestopt. Waarschuwingen worden geconcretiseerd door een dubbele chevron **>>** en moet worden opgelost zodra de synchronisatie is voltooid. Aan het eind van postupgrade, wordt een samenvatting getoond in de bevelherinnering. Het kan er als volgt uitzien:

  ```
  2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
  2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Als de waarschuwing een conflict van middelen betreft, wordt de aandacht van de gebruiker vereist om het op te lossen.

* De **postupgrade_`<server version number>_<time of postupgrade>`.log** het logboekdossier bevat het synchronisatieresultaat. Deze is standaard beschikbaar in de volgende map: **`<installation directory>/var/<instance/postupgrade`**. Fouten en waarschuwingen worden aangegeven door de fout- en waarschuwingskenmerken.

### Conflicten oplossen {#resolving-conflicts}

Pas het volgende proces toe om conflicten op te lossen:

1. Ga in de Adobe Campaign-boom naar **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selecteer het conflict dat u wilt oplossen in de lijst.

Er zijn drie manieren om een conflict op te lossen:

* **[!UICONTROL Declare as resolved]** : vereist vooraf tussenkomst van de gebruiker.
* **[!UICONTROL Accept the new version]** : aanbevolen als de bronnen die bij Adobe Campaign worden geleverd, niet door de gebruiker zijn gewijzigd.
* **[!UICONTROL Keep the current version]** : betekent dat de bijwerking wordt afgewezen.

  >[!IMPORTANT]
  >
  >Als u deze resolutiemodus selecteert, kunt u geen baat hebben bij correcties in de nieuwe versie.

Ga als volgt te werk als u het conflict handmatig wilt oplossen:

1. Zoek in de onderste sectie van het venster naar de **_conflict_** tekenreeks om de entiteiten met conflicten te zoeken. De entiteit die met de nieuwe versie is geïnstalleerd, bevat de **new** argument, de entiteit die overeenkomt met de vorige versie bevat de **cus** argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Verwijder de versie die u niet wilt behouden. Verwijder de **_conflict_argument_** tekenreeks van de entiteit die u bewaart.

   ![](assets/s_ncs_production_conflict003.png)

1. Ga naar het conflict dat u hebt opgelost. Klik op de knop **[!UICONTROL Actions]** pictogram en selecteer **[!UICONTROL Declare as resolved]** .
1. Sla uw wijzigingen op: het conflict is nu opgelost.

### Best practices {#best-practices}

Er kan een updatefout worden gekoppeld aan de databaseconfiguratie. Zorg ervoor de configuraties die door de technische beheerder en de gegevensbestandbeheerder worden uitgevoerd compatibel zijn.

Een unicode-database mag bijvoorbeeld niet alleen de opslag van LATIN1-gegevens, enzovoort, toestaan.

## Waarschuwen als de clientconsoles van de beschikbare update {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Op de computer waarop de Adobe Campaign-toepassingsserver is geïnstalleerd (**nlserver-web**), het bestand downloaden en kopiëren  **setup-client-6.XXXX.exe** i n **[pad van de toepassing]/datakit/nl/eng/jsp**.

De volgende keer dat clientconsoles worden aangesloten, wordt gebruikers in een venster geïnformeerd over de beschikbaarheid van een update en kunnen ze deze downloaden en installeren.

>[!NOTE]
>
>Zorg ervoor de gebruiker IIS_XPG de aangewezen leesrechten voor dit installatiedossier heeft en verwijs naar [installatiegids](../../installation/using/general-architecture.md) voor meer informatie .

### Linux {#in-linux-1}

Op de computer waarop de Adobe Campaign-toepassingsserver (**nlserver-web**) is geïnstalleerd, haalt u de  **setup-client-6.XXXX.exe** verpakken en kopiëren, opslaan als **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

De volgende keer dat clientconsoles worden aangesloten, wordt gebruikers in een venster geïnformeerd over de beschikbaarheid van een update en kunnen ze deze downloaden en installeren.

>[!NOTE]
>
>Zorg ervoor dat de Apache-gebruiker de juiste leesrechten heeft voor dit installatiebestand en raadpleeg de [installatiegids](../../installation/using/general-architecture.md) voor meer informatie .
