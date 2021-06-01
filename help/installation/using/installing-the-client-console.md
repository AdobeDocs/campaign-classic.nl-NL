---
product: campaign
title: De clientconsole installeren
description: Leer hoe u de clientconsole installeert
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 3%

---

# De clientconsole van de campagne installeren en bijwerken{#installing-the-client-console}

De Console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden.

Voordat u de clientconsole gaat installeren, moet u:

* Controleer de compatibiliteit van uw systeem en gereedschappen met Adobe Campaign in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* URL van campagneserver ophalen
* Je gebruikersgegevens ophalen

Het proces voor het installeren of bijwerken van de clientconsole is afhankelijk van uw implementatie van Adobe Campaign Classic.
Controleer de onderstaande details om te begrijpen wat nodig is voor uw implementatie.

![](assets/do-not-localize/how-to-video.png) Ontdek hoe u de Adobe Campaign Client in  [video kunt installeren en instellen](#video)

>[!CAUTION]
>
>De console van de Cliënt van de campagne en de toepassingsserver van de Campagne moeten **op de zelfde productversie** in werking stellen. Adobe raadt ook ten zeerste aan om de **zelfde productbuild** te gebruiken. Leer hoe te om uw versies van de Cliënt en van de Server van de Campagne in [deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) te controleren.

## Adobe gehoste implementaties {#hosted-customers}

Voor een gehoste klant hebt u twee opties om uw clientconsole(s) te installeren of bij te werken:

1. Adobe kan direct implementeren. Zodra de console wordt bijgewerkt, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

1. U kunt aan uw cliëntconsole(s) van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) downloaden

   **Gebruikers hebben beheerdersrechten nodig om de update te voltooien. Als de gebruikers geen beheerdersrechten hebben, moet een systeembeheerder implementeren op alle clientconsoles**

## Implementaties {#hybrid-onprem-customers} op locatie

Adobe Campaign-gebruikers kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd, als ze de clientconsole gebruiken.

### De console beschikbaar maken voor gebruikers {#make-console-available}

Wanneer de computer die wordt gebruikt om een Adobe Campaign-toepassingsserver (nlserver-web) te starten, gebruikersverbindingen ontvangt via de clientconsole, kunt u deze configureren om het installatieprogramma voor de Adobe Campaign-client beschikbaar te maken via een HTML-interface. Wanneer een nieuwe versie van de clientconsole beschikbaar is, worden gebruikers uitgenodigd deze te downloaden wanneer ze hun clientconsole starten.

Hiervoor moet u:

1. Selecteer het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt setup-client-7.X.XXXX.exe voor v7 of setup-client-6.X.XXXX.exe voor v6.1 genoemd, waarbij X de subversie van Adobe Campaign is en XXXX de build   getal.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campaign (op de marketingserver voor hybride installaties) onder /datakit/nl/eng/jsp.

1. Start Adobe Campaign-server.


### Deze vraagoptie niet langer instellen

Adobe raadt aan de optie **[!UICONTROL No longer ask this question]** niet in te schakelen om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.  Als deze optie is geselecteerd, wordt de gebruiker niet op de hoogte gesteld van nieuwe beschikbare versies.

Als **[!UICONTROL No longer ask this question]** is geselecteerd, kunt u deze herinnering terugstellen. Alleen systeembeheerders die vertrouwd zijn met het bewerken van het Windows-register, moeten deze wijzigingen aanbrengen:

1. Open de Register-editor met de opdracht **regedit** in het menu **[!UICONTROL Start > Run]**.

1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Verwijder het **confAdvisedUpgrade**-item en sluit de Register-editor.

>[!NOTE]
>
>Als u een bijgewerkte console op een bestaande implementatie toepast, zullen de gebruikers automatisch een herinnering ontvangen om hun cliëntconsole bij te werken. Als u Campagne voor het eerst uitvoert, zullen de gebruikers de console moeten downloaden. Zie hieronder voor meer informatie over beide opties

### Werk de console voor bestaande implementatie bij{#update-the-client-console}

Zodra de console in de de serveromslag van de Campagne beschikbaar is, zullen de gebruikers worden ertoe aangezet om de recentste versie van de cliëntconsole in een pop-up venster te downloaden.

**Gebruikers hebben beheerderstoegang nodig om de update te voltooien. Als de gebruikers geen beheerdersrechten hebben, moet een systeembeheerder implementeren op alle clientconsoles**


### Download de console voor nieuwe implementatie{#download-the-client-console}

Gebruikers moeten de console nu downloaden en installeren door de onderstaande stappen uit te voeren:

1. Open een webbrowser en download de console vanaf het volgende adres:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Voer in het venster Identificatie uw aanmeldingsgegevens en wachtwoord in.

   ![](assets/s_ncs_install_setup_download01.png)

   Indien nodig, gebruik de geloofsbrieven van de interne rekening die tijdens instantie verwezenlijking wordt bepaald.

1. Klik op de koppeling **[!UICONTROL Download]** op de installatiepagina.
1. Download en sla het instellingenbestand van de client op.
1. Het gedownloade bestand uitvoeren op een computer in Windows: De installatie wordt gestart. Het standaardinstallatiepad van de clientconsole is **$PROGRAFinnLES$/Adobe/Adobe Campaign Classic vX Client**, waarbij &#39;X&#39; &#39;6&#39; of &#39;7&#39; is, volgens uw Adobe Campaign-versie.

### Maak de verbinding - alleen eerste gebruikers{#create-the-connection}

Nadat de clientconsole is geïnstalleerd, voert u de onderstaande stappen uit om de verbinding met de toepassingsserver tot stand te brengen:

1. Start de console vanuit het menu Windows **[!UICONTROL Start]** in de programmagroep **Adobe Campaign**.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld de URL van het type [`https://<machine>.<domain>.com`](https://myserver.adobe.com) gebruiken.

1. Als Adobe IMS voor uw organisatie wordt gevormd, controleer de optie **[!UICONTROL Connect with an Adobe ID]**

1. Klik **[!UICONTROL Ok]** om uw montages te bewaren.

U kunt zo veel verbindingen toevoegen als u nodig hebt om bijvoorbeeld verbinding te maken met uw test-, stage- en productieomgeving.

>[!NOTE]
>
>Met de knop **[!UICONTROL Add]** kunt u **[!UICONTROL folders]** maken om al uw verbindingen te organiseren. U hoeft alleen elke verbinding naar een map te slepen.

### Aanmelden bij Adobe Campaign

Volg onderstaande stappen om u aan te melden bij een bestaande instantie:

1. Start de console vanuit het menu Windows **[!UICONTROL Start]** in de programmagroep **Adobe Campaign**.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

1. Selecteer de instantie Campagne waaraan u zich moet aanmelden.

1. Klik op **[!UICONTROL Ok]**

1. Voer uw aanmeldingsgegevens voor de gebruiker in en klik op **[!UICONTROL Log in]**


**Verwante onderwerpen**

* [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)

## Video over zelfstudie

In deze video ziet u hoe u de Adobe Campaign-client installeert en instelt.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
