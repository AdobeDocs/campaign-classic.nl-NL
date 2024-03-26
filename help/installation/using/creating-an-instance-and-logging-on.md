---
product: campaign
title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}



Als u een nieuwe instantie en een Adobe Campaign-database wilt maken, past u het volgende proces toe:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. Maak en configureer de database.

>[!NOTE]
>
>Alleen de **interne** id kan deze bewerkingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

Wanneer de Adobe Campaign-console wordt gestart, gaat u naar een aanmeldingspagina.

Ga als volgt te werk om een nieuwe instantie te maken:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen. Deze koppeling kan **[!UICONTROL New...]** of een bestaande instantienaam.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klikken **[!UICONTROL Add > Connection]** en voert u het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik een DNS of een alias van de computer of uw IP-adres.

   U kunt bijvoorbeeld het `https://<machine>.<domain>.com` type URL gebruiken.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]`, `[A-Z]``[0-9]` en streepjes (-) of volledige stops.

1. Klik **[!UICONTROL Ok]** om de instellingen te bevestigen: u kunt nu beginnen met het proces voor het maken van instanties.
1. Voer in het **[!UICONTROL Connection settings]** venster de interne **aanmeldingsnaam en het** bijbehorende wachtwoord in om verbinding te maken met de toepassingsserver van Adobe Campaign. Nadat de verbinding is gemaakt, opent u de wizard voor het maken van instanties om een nieuwe instantie aan te geven
1. Voer in het **[!UICONTROL Name]** veld de **instantienaam** in. Aangezien deze naam wordt gebruikt om een configuratiebestand **`<instance>`te genereren .xml** en in de opdrachtregelparameters wordt gebruikt om de instantie te identificeren, moet u een korte naam zonder speciale tekens kiezen. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet meer dan 40 tekens bevatten. Dit laat u de grootte van &quot;bericht-identiteitskaart&quot;kopballen beperken en verhindert berichten als spam, in het bijzonder door hulpmiddelen zoals SpamAssassin worden beschouwd.

1. In de **[!UICONTROL DNS masks]** velden, voert u de **lijst met DNS-maskers** waaraan de instantie moet worden toegevoegd. De Adobe Campaign-server gebruikt de hostnaam die in de HTTP-aanvragen wordt weergegeven om te bepalen welke instantie moet worden bereikt.

   De hostnaam bevindt zich tussen de tekenreeks **https://** en de eerste schuine streep **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De? en &#42; tekens kunnen als jokertekens worden gebruikt om één of meerdere tekens (DNS, poort, enz.) te vervangen. De demowaarde &#42;**werkt bijvoorbeeld** met &quot;https://demo&quot; en zelfs met &quot;https://demo:8080&quot; en zelfs met &quot;https://demo2&quot;.

   De gebruikte namen moeten zijn gedefinieerd in uw DNS. U kunt ook de correspondentie tussen een DNS-naam en een IP-adres doorgeven in het **c:/windows/system32/drivers/etc/hosts-bestand** in Windows en in het **/etc/hosts-bestand** in Linux. U moet daarom de verbindingsinstellingen wijzigen, zodat deze DNS-naam wordt gebruikt om verbinding te kunnen maken met de door u gekozen instantie.

   De server moet met deze naam worden geïdentificeerd, met name voor het uploaden van afbeeldingen in e-mails.

   Bovendien moet de server met zich door deze naam, en indien mogelijk door een loopbackadres - 127.0.0.1 - kunnen verbinden, vooral om rapporten toe te staan om in formaat van PDF worden uitgevoerd.

1. In de **[!UICONTROL Language]** vervolgkeuzelijst selecteert u de **instantietaal**: Engels (VS), Engels (VK), Frans of Japans.

   Verschillen tussen Engels in de VS en Engels in het VK worden beschreven in [deze sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Adobe Campaign-instanties zijn niet meertalig: u kunt de interface niet van taal naar taal schakelen.

1. Klik om **[!UICONTROL Ok]** de declaratie van een instantie te bevestigen. Meld u uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan worden gemaakt vanaf de opdrachtregel. Zie Opdrachtregels](../../installation/using/command-lines.md) voor [meer informatie hierover.
