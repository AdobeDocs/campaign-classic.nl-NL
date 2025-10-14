---
product: campaign
title: De clientconsole installeren
description: Leer hoe u de clientconsole installeert
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# De clientconsole van de campagne installeren en bijwerken{#installing-the-client-console}

De Console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden.

Voordat u de clientconsole gaat installeren, moet u:

* Controleer uw systeem en hulpmiddelverenigbaarheid met Adobe Campaign in de [&#x200B; matrijs van de Verenigbaarheid &#x200B;](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* URL van campagneserver ophalen
* Je gebruikersgegevens ophalen
* Microsoft Edge Webview2-runtime op uw systeem laten installeren (vanaf versie 7.3 voor build van Campaign Classic). [Meer informatie](#webview)

Het proces voor het installeren of bijwerken van de clientconsole is afhankelijk van uw implementatie van Adobe Campaign Classic.
Controleer de onderstaande details om te begrijpen wat nodig is voor uw implementatie.

![](assets/do-not-localize/how-to-video.png) ontdekt hoe te om de Cliënt van Adobe Campaign in [&#x200B; video te installeren en te plaatsen &#x200B;](#video)

>[!CAUTION]
>
>* De console van de Cliënt van de campagne en de toepassingsserver van de Campagne moeten **op de zelfde productversie** in werking stellen. De Adobe adviseert ook hoogst om **zelfde product te gebruiken bouwt**. Leer hoe te om uw Cliënt van de Campagne en versies van de Server in [&#x200B; deze sectie &#x200B;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) te controleren.
>
>* De toegang tot de installatiemap waarin de console wordt geïnstalleerd zou tot de voorgenomen gebruiker moeten worden beperkt slechts, die ervoor zorgt dat de schrijftoestemmingen dienovereenkomstig worden beperkt.



## Installatie van Microsoft Edge Webview2-runtime {#webview}

Vanuit Campaign Classic 7.3 is de build-versie van Microsoft Edge Webview 2 vereist voor elke consoleinstallatie.

De webweergave wordt standaard geïnstalleerd als onderdeel van het besturingssysteem Windows 11. Als het niet reeds op uw systeem aanwezig is, zal de Installateur van de Console van het Campaign Classic u ertoe aanzetten om het van [&#x200B; de website van de Ontwikkelaar van Microsoft &#x200B;](https://www.adobe.com/go/acc-ms-webview2-runtime-download) te downloaden. De downloadkoppeling werkt niet in Internet Explorer 11, omdat Microsoft de ondersteuning heeft vervangen. Zorg ervoor dat u een andere browser gebruikt om de koppeling te openen.

## Op Adobe gehoste implementaties {#hosted-customers}

Als gehoste klant hebt u twee opties om uw clientconsole(s) te installeren of bij te werken:

1. Adobe kan direct worden geïmplementeerd. Zodra de console wordt bijgewerkt, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

1. U kunt aan uw cliëntconsole(s) van [&#x200B; Distributie van de Software downloaden &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)

   **de Gebruikers zullen toegang Admin vereisen om de update te voltooien. Als de gebruikers geen admin rechten hebben, zal een systeembeheerder aan alle cliëntconsoles moeten opstellen**

## Hybride en implementaties op locatie {#hybrid-onprem-customers}

Adobe Campaign-gebruikers kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd, als ze de clientconsole gebruiken.

### De console beschikbaar maken voor gebruikers {#make-console-available}

Wanneer de computer die wordt gebruikt om een Adobe Campaign-toepassingsserver (nlserver-web) te starten, gebruikersverbindingen ontvangt via de clientconsole, kunt u deze configureren om het installatieprogramma voor de Adobe Campaign-client met uitgebreide functionaliteit beschikbaar te maken via een HTML-interface. Wanneer een nieuwe versie van de clientconsole beschikbaar is, worden gebruikers uitgenodigd deze te downloaden wanneer ze hun clientconsole starten.

Hiervoor moet u:

1. Selecteer het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt setup-client-7.X.XXXX.exe genoemd, waarbij X de subversie van Adobe Campaign is en XXXX het buildnummer.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campaign (op de marketingserver voor hybride installaties) onder /datakit/nl/eng/jsp.

1. Start Adobe Campaign-server.


### Deze vraagoptie niet langer instellen

Adobe raadt aan de optie **[!UICONTROL No longer ask this question]** niet in te schakelen om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.  Als deze optie is geselecteerd, wordt de gebruiker niet op de hoogte gesteld van nieuwe beschikbare versies.

Als **[!UICONTROL No longer ask this question]** is geselecteerd, kunt u deze aanwijzing opnieuw instellen. Alleen systeembeheerders die vertrouwd zijn met het bewerken van het Windows-register, moeten deze wijzigingen aanbrengen:

1. Open de Redacteur van de Registratie gebruikend het **regedit** bevel van het **[!UICONTROL Start > Run]** menu.

1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Schrap de **ingang confAdvisedUpgrade** en sluit de Redacteur van de Registratie.

>[!NOTE]
>
>Als u een bijgewerkte console op een bestaande implementatie toepast, zullen de gebruikers automatisch een herinnering ontvangen om hun cliëntconsole bij te werken. Als u Campagne voor het eerst uitvoert, zullen de gebruikers de console moeten downloaden. Zie hieronder voor meer informatie over beide opties

### De console bijwerken voor een bestaande implementatie{#update-the-client-console}

Zodra de console in de de serveromslag van de Campagne beschikbaar is, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

**de Gebruikers zullen beheerdertoegang vereisen om de update te voltooien. Als de gebruikers geen admin rechten hebben, zal een systeembeheerder aan alle cliëntconsoles moeten opstellen**


### Download de console voor nieuwe implementatie{#download-the-client-console}

Gebruikers moeten de console nu downloaden en installeren door de onderstaande stappen uit te voeren:

1. Open een webbrowser en download de console vanaf het volgende adres:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Voer in het venster Identificatie uw aanmeldingsgegevens en wachtwoord in.

   ![](assets/s_ncs_install_setup_download01.png)

   Indien nodig, gebruik de geloofsbrieven van de interne rekening die tijdens instantie verwezenlijking wordt bepaald.

1. Klik op de koppeling **[!UICONTROL Download]** op de installatiepagina.
1. Download en sla het instellingenbestand van de client op.
1. Het gedownloade bestand uitvoeren op een computer in Windows: de installatie wordt gestart. Het standaardinstallatiepad van de clientconsole is **$PROGRAFinnLES$/Adobe/Adobe Campaign Classic vX Client**, waarbij &#39;X&#39; &#39;6&#39; of &#39;7&#39; is, volgens uw versie van Adobe Campaign.

### Verbinding maken - alleen eerste gebruikers{#create-the-connection}

Nadat de clientconsole is geïnstalleerd, voert u de onderstaande stappen uit om de verbinding met de toepassingsserver tot stand te brengen:

1. Begin de console van het menu van Vensters **[!UICONTROL Start]**, in de **Adobe Campaign** programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld het type URL `https://<machine>.<domain>.com` gebruiken.

1. Als Adobe IMS is geconfigureerd voor uw organisatie, schakelt u deze optie in **[!UICONTROL Connect with an Adobe ID]**

1. Klik op **[!UICONTROL Ok]** om uw instellingen op te slaan.

U kunt zo veel verbindingen toevoegen als u nodig hebt om bijvoorbeeld verbinding te maken met uw test-, stage- en productieomgeving.

>[!NOTE]
>
>Met de knop **[!UICONTROL Add]** kunt u **[!UICONTROL folders]** maken om al uw verbindingen te organiseren. U hoeft alleen elke verbinding naar een map te slepen.

### Aanmelden bij Adobe Campaign

Volg onderstaande stappen om u aan te melden bij een bestaande instantie:

1. Begin de console van het menu van Vensters **[!UICONTROL Start]**, in de **Adobe Campaign** programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

1. Selecteer de instantie Campagne waaraan u zich moet aanmelden.

1. Klikken **[!UICONTROL Ok]**

1. Voer uw aanmeldingsgegevens voor de gebruiker in en klik op **[!UICONTROL Log in]**

>[!NOTE]
>
>Voor campagne klassieke 7.3 bouwt versies, kan de cliëntconsole van Adobe Campaign om volmachtsgeloofsbrieven twee keer tijdens volmachtsauthentificatie vragen. Dit komt door het feit dat Microsoft Edge Webview2 in tegenstelling tot Internet Explorer geen volmachtsgeloofsbrieven in het geheime voorgeheugen/wachtwoordopslag bewaart.

**Verwante onderwerpen**

* [&#x200B; Creërend een instantie en het programma openen &#x200B;](../../installation/using/creating-an-instance-and-logging-on.md).
* [Compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)

## Video over zelfstudie

In deze video ziet u hoe u de Adobe Campaign-client installeert en instelt.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

De extra Campaign Classic hoe te video&#39;s zijn beschikbaar [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
