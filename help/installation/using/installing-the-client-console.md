---
title: De clientconsole installeren
seo-title: De clientconsole installeren
description: De clientconsole installeren
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 7%

---


# Campagne-clientconsole installeren{#installing-the-client-console}

De console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden.

Voordat u begint, moet u de [compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)voor Campagne controleren en de URL en gebruikersgegevens van de Campagneserver ophalen.

>[!CAUTION]
>
>De console van de Cliënt van de campagne en de toepassingsserver van de Campagne moeten op de zelfde productversie lopen. Adobe raadt ook aan om dezelfde productbuild te gebruiken.

## Download de console{#download-the-client-console}

Volg onderstaande stappen om de Adobe Campaign-clientconsole te downloaden en installeren:

1. Open een webbrowser en download de console vanaf het volgende adres:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Voer in het venster Identificatie uw aanmeldingsgegevens en wachtwoord in.

   ![](assets/s_ncs_install_setup_download01.png)

   Indien nodig, gebruik de geloofsbrieven van de interne rekening die tijdens instantie verwezenlijking wordt bepaald.

1. Klik op de **[!UICONTROL Download]** koppeling op de installatiepagina.
1. Download en sla het instellingenbestand van de client op.
1. Het gedownloade bestand uitvoeren op een computer in Windows: De installatie wordt gestart. Het standaardinstallatiepad van de clientconsole is **$PROGRAFinnLES$/Adobe/Adobe Campaign Classic vX Client**, waarbij &#39;X&#39; &#39;6&#39; of &#39;7&#39; is, volgens uw Adobe Campaign-versie.

>[!NOTE]
>
>In Windows kunt u het bestand **nlclient.exe** rechtstreeks starten vanuit de `[INSTALL]/bin` map op een Windows-server, waar `[INSTALL]` het toegangspad voor de installatiemap van Adobe Campaign ligt.

## Verbinding maken{#create-the-connection}

Nadat de clientconsole is geïnstalleerd, voert u de onderstaande stappen uit om de verbinding met de toepassingsserver tot stand te brengen:

1. Start de console vanuit het Windows- **[!UICONTROL Start]** menu in de **Adobe Campaign** -programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld het [`https://<machine>.<domain>.com`](https://machine) type URL gebruiken.

1. Als Adobe IMS voor uw organisatie wordt gevormd, controleer de optie **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

U kunt zo veel verbindingen toevoegen als u nodig hebt om bijvoorbeeld verbinding te maken met uw test-, stage- en productieomgeving.

>[!NOTE]
>
>Met de **[!UICONTROL Add]** knop kunt u al uw verbindingen ordenen **[!UICONTROL folders]** . U hoeft alleen elke verbinding naar een map te slepen.


## Aanmelden bij campagne

Volg onderstaande stappen om u aan te melden bij een bestaande instantie:

1. Start de console vanuit het Windows- **[!UICONTROL Start]** menu in de **Adobe Campaign** -programmagroep.

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen.

1. Selecteer de instantie Campagne waaraan u zich moet aanmelden.

1. Klik op **[!UICONTROL Ok]**

1. Voer uw aanmeldingsgegevens voor de gebruiker in en klik op **[!UICONTROL Log in]**

**Verwante onderwerpen**

* [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)
* [De Adobe Campaign-client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) installeren en instellen (video)
