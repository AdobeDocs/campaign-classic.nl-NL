---
product: campaign
title: Integratie in een webserver voor Windows
description: Integratie in een webserver voor Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 4%

---

# Integratie in een webserver voor Windows{#integration-into-a-web-server-for-windows}



Adobe Campaign bevat Apache Tomcat die via HTTP (en SOAP) fungeert als ingangspunt in de toepassingsserver.

U kunt deze geïntegreerde Tomcat-server gebruiken om HTTP-aanvragen te bedienen.

In dit geval:

* de standaard luisterpoort is 8080. Als u deze wilt wijzigen, raadpleegt u [deze sectie](../../installation/using/configure-tomcat.md).
* De clientconsoles maken vervolgens verbinding met een URL, zoals ```https:// `<computer>`:8080```.

Nochtans, voor veiligheid en beleidsredenen, adviseren wij gebruikend een specifieke server van het Web als belangrijkste ingangspunt voor het verkeer van HTTP wanneer de computer die Adobe Campaign in werking stelt op Internet wordt blootgesteld en u wenst om toegang tot de console buiten uw netwerk te openen.

Een server van het Web laat u ook gegevensvertrouwelijkheid met het protocol van HTTPs waarborgen.

Eveneens, moet u een server van het Web gebruiken wanneer u wenst om de volgende functionaliteit te gebruiken, die slechts als de module van de de serveruitbreiding van het Web beschikbaar is.

>[!NOTE]
>
>Als u de trackingfunctionaliteit niet gebruikt, kunt u een standaardinstallatie van Apache of IIS uitvoeren met een omleiding naar Campagne. De volgende de serveruitbreidingsmodule van het Web wordt niet vereist.

## Het vormen van de server van het Web IIS {#configuring-the-iis-web-server}

De configuratieprocedure voor een server van het Web IIS is meestal grafisch. Het impliceert het gebruiken van een Website (reeds gecreeerd of in afwachting van verwezenlijking) om tot de middelen van de server van Adobe Campaign toegang te hebben: Java-bestanden (.jsp), opmaakmodellen (.css, .xsl), afbeeldingen (.png), de ISAPI DLL voor omleiding, enz.

De volgende secties detailconfiguratie in IIS 7. De configuratie voor IIS8 is fundamenteel het zelfde.

Als de Web IIS-server nog niet op uw computer is geïnstalleerd, kunt u deze installeren via de **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** -menu.

In IIS 7, naast de standaarddiensten, moet u de Extensies ISAPI en filters installeren ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Configuratiestappen {#configuration-steps}

Pas de volgende configuratiestappen toe:

1. Open IIS via **[!UICONTROL Control panel > Administrative tools > Services]** -menu.
1. Maak en configureer de site (bijvoorbeeld Adobe Campaign) afhankelijk van de parameters van uw netwerk (TCP-verbindingshaven, DNS-host, IP-adres).

   ![](assets/s_ncs_install_iis7_add_site.png)

   U moet ten minste de naam van de site en het toegangspad naar de virtuele map opgeven. Aangezien het pad voor toegang tot de map Website niet wordt gebruikt, kunt u de volgende map gebruiken.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** Met script kunt u automatisch de bronnen configureren die door de Adobe Campaign-server worden gebruikt in de virtuele directory die we zojuist hebben gemaakt. Dubbelklik op de knop **is_neolane_setup.vbs** bestand in het dialoogvenster `[INSTALL]\conf` map, waar `[INSTALL]` is het pad voor toegang tot de installatiemap van Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >In het geval van een server 2008/IIS7 van Vensters installatie, moet u als beheerder worden aangemeld om het manuscript in werking te stellen VBS of het manuscript uit te voeren als beheerder.

   Klikken **[!UICONTROL OK]** als de server van het Web als het volgen omleidingsserver wordt gebruikt, anders klik **[!UICONTROL Cancel]**.

   Wanneer de veelvoudige plaatsen reeds op de server van het Web worden gevormd, wordt een middenpagina getoond om te specificeren op welke Website de installatie van toepassing is: Voer het nummer in dat aan de site is gekoppeld en klik op **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Er moet een bevestigingsbericht worden weergegeven:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. In de **[!UICONTROL Content View]** tabblad, zorgt u ervoor dat de website correct is geconfigureerd met de Adobe Campaign-bronnen:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Als de boom niet wordt getoond, begin IIS opnieuw.

### Rechten beheren {#managing-rights}

Vervolgens moet u de beveiligingsinstellingen configureren voor de ISAPI DLL en voor de bronnen in de installatiemap van Adobe Campaign.

Hiervoor voert u de volgende stappen uit:

1. Selecteer **[!UICONTROL Features View]** en dubbelklikt u op de knop **Verificatie** koppeling.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. In de **Directorybeveiliging** van de Website, zorg ervoor dat de anonieme toegang wordt toegelaten. Klik indien nodig op de knop **[!UICONTROL Edit]** koppelen om de instellingen te wijzigen.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### De server van het Web lanceren en de configuratie testen {#launching-the-web-server-and-testing-the-configuration}

U moet nu testen of de configuratie correct is.

Hiervoor volgt u de volgende procedure:

1. Start de IIS-server opnieuw met de **iisreset** opdrachtregel.

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
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

U kunt ook ervoor zorgen ISAPI DLL correct wordt geladen.

Hiervoor voert u de volgende stappen uit:

1. Bewerk de ISAPI-filters voor de Adobe Campaign-site door op de knop **[!UICONTROL Driver mapping]** pictogram.
1. Controleer de inhoud van het ISAPI-filter:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Aanvullende configuraties {#additional-configurations}

### De maximale bestandsgrootte voor uploaden wijzigen {#changing-the-upload-file-size-limit}

Wanneer het vormen van de server van het Web IIS, is een grens van ongeveer 28 MB automatisch voor vastgestelde dossiers die aan de server worden geupload.

Dit kan van invloed zijn op Adobe Campaign, vooral als u bestanden wilt uploaden die groter zijn dan deze limiet.

Als u bijvoorbeeld een **Gegevens laden (bestand)** Typ activiteit in een werkstroom om een 50 MB dossier in te voeren, zal een fout de werkschema tegenhouden correct te presteren.

In dit geval moet u deze limiet verhogen:

1. Open IIS via **[!UICONTROL Start > (Control panel) > Administration tools]** -menu.
1. In de **Verbindingen** selecteert u de site die u voor uw Adobe-installatie hebt gemaakt en dubbelklikt u op **Verzoek filteren** in het hoofdvenster.
1. In de **Handelingen** deelvenster, selecteert u **Functie-instellingen bewerken** om de waarde in het dialoogvenster **Maximale toegestane inhoudsgrootte (bytes)** veld.

   Als u bijvoorbeeld toestemming wilt geven voor het uploaden van bestanden van 50 MB, moet u een waarde opgeven van meer dan &quot;52428800&quot; bytes.

>[!NOTE]
>
>Voor meer informatie over deze optie IIS, verwijs naar de &quot;hoe te&quot;sectie van [officiële documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

