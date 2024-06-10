---
product: campaign
title: Integratie in een webserver voor Windows
description: Integratie in een webserver voor Windows
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 0e88ac270423ad419237264e562a03ab0c42efb5
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 2%

---

# Integratie in een webserver voor Windows {#integration-into-a-web-server-for-windows}

Adobe Campaign bevat Apache Tomcat die via HTTP (en SOAP) fungeert als ingangspunt in de toepassingsserver.

U kunt deze geïntegreerde Tomcat-server gebruiken om HTTP-aanvragen te bedienen.

In dit geval:

* de standaard luisterpoort is 8080. Als u deze wilt wijzigen, raadpleegt u [deze sectie](../../installation/using/configure-tomcat.md).
* De clientconsoles maken vervolgens verbinding met een URL, zoals ```https:// `<computer>`:8080```.

Nochtans, voor veiligheid en beleidsredenen, adviseren wij gebruikend een specifieke server van het Web als belangrijkste ingangspunt voor het verkeer van HTTP wanneer de computer die Adobe Campaign in werking stelt op Internet wordt blootgesteld en u wenst om toegang tot de console buiten uw netwerk te openen.

Een server van het Web laat u ook gegevensvertrouwelijkheid met het protocol van HTTPs waarborgen.

Eveneens, moet u een server van het Web gebruiken wanneer u wenst om de volgende functionaliteit te gebruiken, die slechts als de module van de de serveruitbreiding van het Web beschikbaar is.

## Het vormen van de server van het Web IIS {#configuring-the-iis-web-server}

De configuratieprocedure voor een server van het Web van Microsoft IIS is meestal grafisch. Het impliceert het gebruiken van een Website om tot de middelen van de server van Adobe Campaign toegang te hebben: dossiers Java (.jsp), stylesheets (.css, .xsl), beelden (.png), ISAPI DLL voor redirection, enz.


### Configuratiestappen {#configuration-steps}

Ga als volgt te werk om Adobe Campaign te integreren met de Microsoft IIS-webserver:

1. Open Microsoft IIS.
1. Maak en configureer de site (bijvoorbeeld Adobe Campaign) afhankelijk van de parameters van uw netwerk (TCP-verbindingshaven, DNS-host, IP-adres).

   U moet ten minste de naam van de site en het toegangspad naar de virtuele map opgeven. Aangezien het pad voor toegang tot de map Website niet wordt gebruikt, kunt u de volgende map gebruiken.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** Met script kunt u automatisch de bronnen configureren die door de Adobe Campaign-server worden gebruikt in de virtuele directory die we zojuist hebben gemaakt. Dubbelklik op de knop **iis_neolane_setup.vbs** bestand in het dialoogvenster `[INSTALL]\conf` map, waar `[INSTALL]` is het pad voor toegang tot de installatiemap van Adobe Campaign.

   >[!NOTE]
   >
   >U moet als beheerder worden aangemeld om het manuscript in werking te stellen VBS of het manuscript uit te voeren als beheerder.

   Klikken **[!UICONTROL OK]** als de server van het Web als het volgen omleidingsserver wordt gebruikt, anders klik **[!UICONTROL Cancel]**.

   Wanneer de veelvoudige plaatsen reeds op de server van het Web worden gevormd, wordt een middenpagina getoond om te specificeren op welke Website de installatie van toepassing is: ga het aantal verbonden aan de plaats in en klik **[!UICONTROL OK]**.

1. In de **[!UICONTROL Content View]** tabblad, zorgt u ervoor dat de website correct is geconfigureerd met de Adobe Campaign-bronnen:

   Start Microsoft IIS opnieuw als de structuur niet wordt weergegeven.

### Rechten beheren {#managing-rights}

Vervolgens moet u de beveiligingsinstellingen configureren voor de ISAPI DLL en voor de bronnen in de installatiemap van Adobe Campaign.

Hiervoor voert u de volgende stappen uit:

1. Selecteer de **[!UICONTROL Features View]** en dubbelklikt u op de knop **Verificatie** koppeling.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. In de **Directorybeveiliging** van de Website, zorg ervoor dat de anonieme toegang wordt toegelaten. Klik indien nodig op de knop **[!UICONTROL Edit]** koppelen om de instellingen te wijzigen.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### De server van het Web lanceren en de configuratie testen {#launching-the-web-server-and-testing-the-configuration}

U moet nu testen of de configuratie correct is.

Hiervoor volgt u de volgende procedure:

1. Start de Microsoft IIS-server opnieuw met de **iisreset** opdrachtregel.

1. Start de Adobe Campaign-service en controleer of deze actief is.

1. Test de volgende module door volgende URL in browser van het Web op te nemen:

   ```
   https://<computer>/r/test
   ```

   De browser moet de volgende reactie weergeven:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Voer de volgende opdrachtregel uit om te testen of de omleidingsmodule aanwezig is:

```
nlserver pdump
```

Zij moet de volgende informatie teruggeven:

```
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

U kunt ook ervoor zorgen ISAPI DLL correct wordt geladen.

Hiervoor voert u de volgende stappen uit:

1. Bewerk de ISAPI-filters voor de Adobe Campaign-site door op de knop **[!UICONTROL Driver mapping]** pictogram.
1. Controleer de inhoud van het ISAPI-filter.


## De maximale bestandsgrootte voor uploaden wijzigen {#changing-the-upload-file-size-limit}

Wanneer het vormen van de server van het Web IIS, is een grens van ongeveer 28 MB automatisch voor vastgestelde dossiers die aan de server worden geupload.

Dit kan van invloed zijn op Adobe Campaign, vooral als u bestanden wilt uploaden die groter zijn dan deze limiet.

Als u bijvoorbeeld een **Gegevens laden (bestand)** Typ activiteit in een werkstroom om een 50 MB dossier in te voeren, zal een fout de werkschema tegenhouden correct te presteren.

In dit geval moet u deze limiet verhogen.

Voor meer informatie over deze optie van Microsoft IIS, verwijs naar de &quot;Hoe kan&quot;sectie van [Microsoft-documentatie](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.

