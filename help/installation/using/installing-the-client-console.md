---
product: campaign
title: De clientconsole installeren
description: Leer hoe u de clientconsole installeert
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 403227736e2e8c606204e9324d0afb5b71be62a5
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 3%

---

# De clientconsole van de campagne installeren en bijwerken{#installing-the-client-console}



De Console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden.

Voordat u de clientconsole gaat installeren, moet u:

* Controleer de compatibiliteit van uw systeem en gereedschappen met Adobe Campaign in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* URL van campagneserver ophalen
* Je gebruikersgegevens ophalen
* Microsoft Edge Webview2-runtime op uw systeem laten installeren (vanaf versie Campaign Classic 7.3). [Meer informatie](#webview)

Het proces voor het installeren of bijwerken van de clientconsole is afhankelijk van uw implementatie van Adobe Campaign Classic.
Controleer de onderstaande details om te begrijpen wat nodig is voor uw implementatie.

![](assets/do-not-localize/how-to-video.png) Ontdek hoe u de Adobe Campaign-client kunt installeren en installeren in [video](#video)

>[!CAUTION]
>
>Campagne Client Console en Campagne application server moeten in werking stellen **op dezelfde productversie**. Adobe beveelt ook ten zeerste aan de **zelfde product bouwen**. Leer hoe u de versies van uw Campagne Client en Server kunt controleren in [deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Installatie van de Microsoft Edge Webview2-runtime {#webview}

Vanuit de Campaign Classic 7.3-build-versie is de installatie van de Microsoft Edge Webview 2-runtime vereist voor elke consoleinstallatie.

De webweergave wordt standaard geïnstalleerd als onderdeel van het besturingssysteem Windows 11. Als dit nog niet het geval is op uw systeem, wordt u gevraagd het te downloaden via het Campaign Classic Console-installatieprogramma [Microsoft Developer-website](https://www.adobe.com/go/acc-ms-webview2-runtime-download). De downloadkoppeling werkt niet in Internet Explorer 11, omdat Microsoft de ondersteuning heeft vervangen. Zorg ervoor dat u een andere browser gebruikt om de koppeling te openen.

## Adobe Gehoste implementaties {#hosted-customers}

Als gehoste klant hebt u twee opties om uw clientconsole(s) te installeren of bij te werken:

1. Adobe kan direct implementeren. Zodra de console wordt bijgewerkt, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

1. U kunt downloaden naar uw clientconsole(s) van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)

   **Gebruikers hebben beheerdersrechten nodig om de update te voltooien. Als de gebruikers geen beheerrechten hebben, moet een systeembeheerder op alle clientconsoles implementeren**

## Hybride en op locatie uitgevoerde implementaties {#hybrid-onprem-customers}

Adobe Campaign-gebruikers kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd, als ze de clientconsole gebruiken.

### De console beschikbaar maken voor gebruikers {#make-console-available}

Wanneer de computer die wordt gebruikt om een Adobe Campaign-toepassingsserver (nlserver-web) te starten, gebruikersverbindingen ontvangt via de clientconsole, kunt u deze configureren om het installatieprogramma voor de Adobe Campaign-client met uitgebreide functionaliteit beschikbaar te maken via een HTML-interface. Wanneer een nieuwe versie van de clientconsole beschikbaar is, worden gebruikers uitgenodigd deze te downloaden wanneer ze hun clientconsole starten.

Hiervoor moet u:

1. Selecteer het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt setup-client-7.X.XXXX.exe genoemd, waarbij X de subversie van Adobe Campaign is en XXXX het buildnummer.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campaign (op de marketingserver voor hybride installaties) onder /datakit/nl/eng/jsp.

1. Start Adobe Campaign-server.


### Deze vraagoptie niet langer instellen

Adobe raadt u aan deze optie te laten **[!UICONTROL No longer ask this question]** niet geselecteerd om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.  Als deze optie is geselecteerd, wordt de gebruiker niet op de hoogte gesteld van nieuwe beschikbare versies.

Indien **[!UICONTROL No longer ask this question]**  is geselecteerd, kunt u deze herinnering opnieuw instellen. Alleen systeembeheerders die vertrouwd zijn met het bewerken van het Windows-register, moeten deze wijzigingen aanbrengen:

1. Registereditor openen met de **regedit** van de **[!UICONTROL Start > Run]** -menu.

1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Verwijder de **confAdvisedUpgrade** item en sluit de Register-editor.

>[!NOTE]
>
>Als u een bijgewerkte console op een bestaande implementatie toepast, zullen de gebruikers automatisch een herinnering ontvangen om hun cliëntconsole bij te werken. Als u Campagne voor het eerst uitvoert, zullen de gebruikers de console moeten downloaden. Zie hieronder voor meer informatie over beide opties

### De console bijwerken voor een bestaande implementatie{#update-the-client-console}

Zodra de console in de de serveromslag van de Campagne beschikbaar is, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

**Gebruikers hebben beheerderstoegang nodig om de update te voltooien. Als de gebruikers geen beheerrechten hebben, moet een systeembeheerder op alle clientconsoles implementeren**


### Download de console voor nieuwe implementatie{#download-the-client-console}

Gebruikers moeten de console nu downloaden en installeren door de onderstaande stappen uit te voeren:

1. Open een webbrowser en download de console vanaf het volgende adres:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Voer in het venster Identificatie uw aanmeldingsgegevens en wachtwoord in.

   ![](assets/s_ncs_install_setup_download01.png)

   Indien nodig, gebruik de geloofsbrieven van de interne rekening die tijdens instantie verwezenlijking wordt bepaald.

1. Klik op de knop **[!UICONTROL Download]** koppeling op de installatiepagina.
1. Download en sla het instellingenbestand van de client op.
1. Het gedownloade bestand uitvoeren op een computer in Windows: De installatie wordt gestart. Het standaardinstallatiepad van de clientconsole is **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, waarbij &#39;X&#39; &#39;6&#39; of &#39;7&#39; is, volgens uw Adobe Campaign-versie.

### Verbinding maken - alleen eerste gebruikers{#create-the-connection}

Nadat de clientconsole is geïnstalleerd, voert u de onderstaande stappen uit om de verbinding met de toepassingsserver tot stand te brengen:

1. De console starten vanuit Windows **[!UICONTROL Start]** in het menu **Adobe Campaign** programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klikken **[!UICONTROL Add > Connection]** en voert u het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld de opdracht `https://<machine>.<domain>.com` type URL.

1. Als Adobe IMS voor uw organisatie is geconfigureerd, controleert u de optie **[!UICONTROL Connect with an Adobe ID]**

1. Klikken **[!UICONTROL Ok]** om uw instellingen op te slaan.

U kunt zo veel verbindingen toevoegen als u nodig hebt om bijvoorbeeld verbinding te maken met uw test-, stage- en productieomgeving.

>[!NOTE]
>
>De **[!UICONTROL Add]** knop laat u maken **[!UICONTROL folders]** om al uw verbindingen te organiseren. U hoeft alleen elke verbinding naar een map te slepen.

### Aanmelden bij Adobe Campaign

Volg onderstaande stappen om u aan te melden bij een bestaande instantie:

1. De console starten vanuit Windows **[!UICONTROL Start]** in het menu **Adobe Campaign** programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

1. Selecteer de instantie Campagne waaraan u zich moet aanmelden.

1. Klik op **[!UICONTROL Ok]**

1. Voer uw aanmeldingsgegevens voor de gebruiker in en klik op **[!UICONTROL Log in]**

>[!NOTE]
>
>Voor campagne klassieke 7.3 bouwt versies, kan de cliëntconsole van Adobe Campaign om volmachtsgeloofsbrieven twee keer tijdens volmachtsauthentificatie vragen. Dit komt doordat Microsoft Edge Webview2 in tegenstelling tot Internet Explorer geen proxygegevens in de cache-/wachtwoordwinkel opslaat.

**Verwante onderwerpen**

* [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)

## Video over zelfstudie

In deze video ziet u hoe u de Adobe Campaign-client installeert en instelt.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Er zijn aanvullende Campaign Classic-hoe-kan-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
