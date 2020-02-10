---
title: Een instantie maken en aanmelden
seo-title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}

Als u een nieuwe instantie en een Adobe Campagne-database wilt maken, past u het volgende proces toe:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. Maak en configureer de database.

>[!NOTE]
>
>Alleen de **interne** id kan deze bewerkingen uitvoeren. Raadpleeg de [interne id](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie hierover.

Wanneer de Adobe Campaign-console wordt gestart, hebt u toegang tot een aanmeldingspagina.

Ga als volgt te werk om een nieuwe instantie te maken:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen. Deze koppeling kan een van beide **[!UICONTROL New...]** of een bestaande instantienaam zijn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de toepassingsserver van Adobe Campagne in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campagne-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld het [`https://<machine>.<domain>.com`](https://machine) type URL gebruiken.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]`, `[A-Z]`, `[0-9]` en streepjes (-) of volledige stops.

1. Klik **[!UICONTROL Ok]** om de instellingen te bevestigen: U kunt nu beginnen met het maken van de instantie.
1. Voer in het **[!UICONTROL Connection settings]** venster de **interne** aanmelding en het bijbehorende wachtwoord in om verbinding te maken met de Adobe Campaign-toepassingsserver. Nadat u verbinding hebt gemaakt, kunt u de wizard voor het maken van instanties gebruiken om een nieuwe instantie te declareren
1. Voer in het **[!UICONTROL Name]** veld de **instantienaam** in. Aangezien deze naam wordt gebruikt om een configuratiedossier **config-`<instance>`.xml** te produceren en in de parameters van de bevellijn wordt gebruikt om de instantie te identificeren, zorg ervoor u een korte naam zonder speciale karakters kiest. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet meer dan 40 tekens bevatten. Dit laat u de grootte van &quot;bericht-identiteitskaart&quot;kopballen beperken en verhindert berichten als spam, in het bijzonder door hulpmiddelen zoals SpamAssassin worden beschouwd.

1. Voer in de **[!UICONTROL DNS masks]** velden de **lijst in met DNS-maskers** waaraan de instantie moet worden gekoppeld. De Adobe Campagneserver gebruikt hostname die in de HTTP- verzoeken verschijnt om te bepalen welke instantie te bereiken.

   De hostname is bevat tussen het koord **https://** en het eerste schuine streep karakter **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De ? en * tekens kunnen worden gebruikt als jokertekens om een of meer tekens (DNS, poort, enz.) te vervangen. De waarde **demo*** werkt bijvoorbeeld met &quot;https://demo&quot;, net als met &quot;https://demo:8080&quot; en zelfs met &quot;https://demo2&quot;.

   De gebruikte namen moeten in uw DNS worden bepaald. U kunt de correspondentie tussen een DNS naam en een IP adres in **c:/windows/system32/drivers/etc/hosts** dossier in Vensters en in het **/etc/hosts** dossier in Linux ook meedelen. Daarom moet u de verbindingsmontages wijzigen om deze DNS naam te gebruiken om met uw gekozen instantie te verbinden.

   De server moet met deze naam worden geïdentificeerd, met name voor het uploaden van afbeeldingen in e-mails.

   Daarnaast moet de server verbinding met zichzelf kunnen maken met deze naam en, indien mogelijk, met een loopbackadres - 127.0.0.1 -, vooral om rapporten te kunnen exporteren in PDF-indeling.

1. Selecteer in de **[!UICONTROL Language]** vervolgkeuzelijst de **instantietaal**: Engels (VS), Engels (VK), Frans of Japans.

   Verschillen tussen Engels in de VS en Engels in het VK worden in [dit gedeelte](../../platform/using/adobe-campaign-workspace.md#date-and-time)beschreven.

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Instanties van Adobe Campagne zijn niet meertalig: u kunt niet de interface van een taal aan een andere schakelen.

1. Klik **[!UICONTROL Ok]** om de instantiedeclaratie te bevestigen. Log uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan vanaf de opdrachtregel worden gemaakt. Raadpleeg de [opdrachtregels](../../installation/using/command-lines.md)voor meer informatie.

