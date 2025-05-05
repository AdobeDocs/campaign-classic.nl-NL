---
product: campaign
title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}



Pas het volgende proces toe om een nieuwe instantie en een Adobe Campaign-database te maken:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. Maak en configureer de database.

>[!NOTE]
>
>Alleen de **interne** id kan deze bewerkingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

Wanneer de Adobe Campaign-console wordt gestart, gaat u naar een aanmeldingspagina.

Als u een nieuwe instantie wilt maken, voert u de onderstaande stappen uit:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsgegevens om het venster voor het configureren van de verbinding te openen. Deze koppeling kan **[!UICONTROL New...]** of een bestaande instantienaam zijn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld het type URL `https://<machine>.<domain>.com` gebruiken.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]`, `[A-Z]` `[0-9]` en streepjes (-) of volledige stops.

1. Klik **[!UICONTROL Ok]** om de instellingen te bevestigen: u kunt nu beginnen met het proces voor het maken van instanties.
1. Voer in het **[!UICONTROL Connection settings]** venster de interne **aanmeldingsnaam en het** bijbehorende wachtwoord in om verbinding te maken met de toepassingsserver van Adobe Campaign. Nadat de verbinding is gemaakt, opent u de assistent voor het maken van instanties om een nieuwe instantie aan te geven
1. Voer in het **[!UICONTROL Name]** veld de **instantienaam** in. Aangezien deze naam wordt gebruikt om een configuratiebestand **`<instance>`te genereren .xml** en in de opdrachtregelparameters wordt gebruikt om de instantie te identificeren, moet u een korte naam zonder speciale tekens kiezen. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet langer zijn dan 40 tekens. Hiermee voorkomt u dat berichten als spam worden beschouwd, vooral door hulpmiddelen als SpamAssassin.

1. Voer in de **[!UICONTROL DNS masks]** velden de **lijst in met DNS-maskers** waaraan de instantie moet worden gekoppeld. De Adobe Campaign-server gebruikt de hostnaam die in de HTTP-aanvragen wordt weergegeven om te bepalen welke instantie moet worden bereikt.

   Hostname is bevat tussen het koord **https://** en het eerste schuine streep karakter **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De ? en &#42; tekens kunnen als jokertekens worden gebruikt om één of meerdere tekens (DNS, poort, enz.) te vervangen. De demowaarde &#42;**werkt bijvoorbeeld** met &quot;https://demo&quot; en zelfs met &quot;https://demo:8080&quot; en zelfs met &quot;https://demo2&quot;.

   De gebruikte namen moeten zijn gedefinieerd in uw DNS. U kunt ook de correspondentie tussen een DNS-naam en een IP-adres doorgeven in het **c:/windows/system32/drivers/etc/hosts-bestand** in Windows en in het **/etc/hosts-bestand** in Linux. U moet daarom de verbindingsinstellingen wijzigen, zodat deze DNS-naam wordt gebruikt om verbinding te kunnen maken met de door u gekozen instantie.

   De server moet deze naam hebben, in het bijzonder voor het uploaden van afbeeldingen in e-mails.

   Bovendien moet de server verbinding kunnen maken met zichzelf via deze naam, en indien mogelijk met een loopback-adres (127.0.0.1 -), in het bijzonder om het exporteren van rapporten in PDF-indeling mogelijk te maken.

1. Selecteer in de **[!UICONTROL Language]** vervolgkeuzelijst de **instantietaal**: Engels (VS), Engels (UK), Frans of Japans.

   De verschillen tussen het Engels van de V.S. en het Engels van het VK worden beschreven in [ deze sectie ](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Adobe Campaign-instanties zijn niet meertalig: u kunt de interface niet van taal naar taal schakelen.

1. Klik op **[!UICONTROL Ok]** om de instantiedeclaratie te bevestigen. Log uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan vanaf de opdrachtregel worden gemaakt. Zie Opdrachtregels[&#128279;](../../installation/using/command-lines.md) voor meer informatie hierover.
