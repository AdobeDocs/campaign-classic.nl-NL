---
solution: Campaign Classic
product: campaign
title: Integratie in een webserver voor Windows
description: Integratie in een webserver voor Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 2%

---


# Integratie in een webserver voor Windows{#integration-into-a-web-server-for-windows}

Adobe Campaign bevat Apache Tomcat die via HTTP (en SOAP) fungeert als ingangspunt in de toepassingsserver.

U kunt deze geïntegreerde Tomcat-server gebruiken om HTTP-aanvragen te bedienen.

In dit geval:

* de standaard luisterpoort is 8080. Om het te veranderen, verwijs naar [het Vormen Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* De clientconsoles maken vervolgens verbinding met een URL zoals [https:// `<computer>`:8080](https://myserver.adobe.com:8080).

Nochtans, voor veiligheid en beleidsredenen, adviseren wij gebruikend een specifieke server van het Web als belangrijkste ingangspunt voor het verkeer van HTTP wanneer de computer die Adobe Campaign in werking stelt op Internet wordt blootgesteld en u wenst om toegang tot de console buiten uw netwerk te openen.

Een server van het Web laat u ook gegevensvertrouwelijkheid met het protocol van HTTPs waarborgen.

Eveneens, moet u een server van het Web gebruiken wanneer u wenst om de volgende functionaliteit te gebruiken, die slechts als de module van de de serveruitbreiding van het Web beschikbaar is.

>[!NOTE]
>
>Als u de trackingfunctionaliteit niet gebruikt, kunt u een standaardinstallatie van Apache of IIS uitvoeren met een omleiding naar Campagne. De volgende de serveruitbreidingsmodule van het Web wordt niet vereist.

## Het vormen van de server van het Web IIS {#configuring-the-iis-web-server}

De configuratieprocedure voor een server van het Web IIS is meestal grafisch. Het impliceert het gebruiken van een Website (reeds gecreeerd of in afwachting van verwezenlijking) om tot de middelen van de server van Adobe Campaign toegang te hebben: Java-bestanden (.jsp), opmaakmodellen (.css, .xsl), afbeeldingen (.png), de ISAPI DLL voor omleiding, enz.

De volgende secties detailconfiguratie in IIS 7. De configuratie voor IIS8 is fundamenteel het zelfde.

Als de Web IIS-server nog niet op uw computer is geïnstalleerd, kunt u deze installeren via het menu **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]**.

In IIS 7, naast de standaarddiensten, moet u de Extensies ISAPI en filters installeren ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Configuratiestappen {#configuration-steps}

Pas de volgende configuratiestappen toe:

1. Open IIS via het **[!UICONTROL Control panel > Administrative tools > Services]** menu.
1. Maak en configureer de site (bijvoorbeeld Adobe Campaign) afhankelijk van de parameters van uw netwerk (TCP-verbindingshaven, DNS-host, IP-adres).

   ![](assets/s_ncs_install_iis7_add_site.png)

   U moet ten minste de naam van de site en het toegangspad naar de virtuele map opgeven. Aangezien het pad voor toegang tot de map Website niet wordt gebruikt, kunt u de volgende map gebruiken.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Met een **VBS**-script kunt u de bronnen die door de Adobe Campaign-server worden gebruikt, automatisch configureren in de virtuele directory die we zojuist hebben gemaakt. Als u het bestand wilt starten, dubbelklikt u op het bestand **is_neolane_setup.vbs** in de map `[INSTALL]\conf`, waarbij `[INSTALL]` het pad is voor toegang tot de installatiemap van Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >In het geval van een server 2008/IIS7 van Vensters installatie, moet u als beheerder worden aangemeld om het manuscript in werking te stellen VBS of het manuscript uit te voeren als beheerder.

   Klik **[!UICONTROL OK]** als de server van het Web als het volgen omleidingsserver wordt gebruikt, anders klik **[!UICONTROL Cancel]**.

   Wanneer de veelvoudige plaatsen reeds op de server van het Web worden gevormd, wordt een middenpagina getoond om te specificeren op welke Website de installatie van toepassing is: Voer het nummer in dat aan de site is gekoppeld en klik op **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Er moet een bevestigingsbericht worden weergegeven:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. Controleer op het tabblad **[!UICONTROL Content View]** of de website correct is geconfigureerd met de Adobe Campaign-bronnen:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Als de boom niet wordt getoond, begin IIS opnieuw.

### Rechten beheren {#managing-rights}

Vervolgens moet u de beveiligingsinstellingen configureren voor de ISAPI DLL en voor de bronnen in de installatiemap van Adobe Campaign.

Hiervoor voert u de volgende stappen uit:

1. Selecteer de tab **[!UICONTROL Features View]** en dubbelklik op de koppeling **Authentication**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. In **de Veiligheid van de Folder** lusje van de Website, zorg ervoor dat de anonieme toegang wordt toegelaten. Klik zo nodig op de koppeling **[!UICONTROL Edit]** om de instellingen te wijzigen.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### De webserver starten en de configuratie testen {#launching-the-web-server-and-testing-the-configuration}

U moet nu testen of de configuratie correct is.

Hiervoor volgt u de volgende procedure:

1. Start de IIS-server opnieuw met de opdrachtregel **isreset**.
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
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

U kunt ook ervoor zorgen ISAPI DLL correct wordt geladen.

Hiervoor voert u de volgende stappen uit:

1. Bewerk de ISAPI-filters voor de Adobe Campaign-site door op het pictogram **[!UICONTROL Driver mapping]** te klikken.
1. Controleer de inhoud van het ISAPI-filter:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Aanvullende configuraties {#additional-configurations}

### De maximale grootte van het uploadbestand wijzigen {#changing-the-upload-file-size-limit}

Wanneer het vormen van de server van het Web IIS, is een grens van ongeveer 28 MB automatisch voor vastgestelde dossiers die aan de server worden geupload.

Dit kan van invloed zijn op Adobe Campaign, vooral als u bestanden wilt uploaden die groter zijn dan deze limiet.

Als u bijvoorbeeld een activiteit van het type **Gegevens laden (bestand)** in een werkstroom gebruikt om een bestand van 50 MB te importeren, zal een fout ervoor zorgen dat de werkstroom niet correct wordt uitgevoerd.

In dit geval moet u deze limiet verhogen:

1. Open IIS via het **[!UICONTROL Start > (Control panel) > Administration tools]** menu.
1. Selecteer in het deelvenster **Verbindingen** de site die u voor de Adobe-installatie hebt gemaakt en dubbelklik vervolgens op **Filteren aanvragen** in het hoofdvenster.
1. Selecteer **Functie-instellingen bewerken** in het deelvenster **Handelingen** om de waarde te kunnen bewerken in het veld **Maximale toegestane inhoudsgrootte (bytes)**.

   Als u bijvoorbeeld toestemming wilt geven voor het uploaden van bestanden van 50 MB, moet u een waarde opgeven van meer dan &quot;52428800&quot; bytes.

>[!NOTE]
>
>Voor meer informatie over deze optie IIS, verwijs naar de &quot;hoe te&quot;sectie van [officiële documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### De weergave van http-foutberichten configureren {#configuring-http-error-message-display}

Als u een 6.1 versie IIS server gebruikt, kunnen de geproduceerde foutenmeldingen moeilijk zijn te lezen toe te schrijven aan ongewenste HTML code die in het bericht wordt getoond.

Pas de volgende configuratie toe om dit te verhelpen en de fout correct weer te geven:

1. Open IIS via het **[!UICONTROL Start > Control Panel > Administrative tools]** menu.
1. Selecteer in het deelvenster **Verbindingen** de site die voor uw Adobe Campaign-installatie is gemaakt en dubbelklik vervolgens op **Configuration editor** in het hoofdvenster.
1. Selecteer **system.webServer** > **httpErrors** in de vervolgkeuzelijst **Sectie**.
1. Selecteer de waarde **PassThrough** op de regel **existingResponse**.

![](assets/ins_iis_httperrors.png)

