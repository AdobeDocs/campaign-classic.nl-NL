---
product: campaign
title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}

![](../../assets/v7-only.svg)

Pas het volgende proces toe om een nieuwe instantie en een Adobe Campaign-database te maken:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. De database maken en configureren.

>[!NOTE]
>
>Alleen de **internal**-id kan deze bewerkingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

Wanneer de Adobe Campaign-console wordt gestart, opent u een aanmeldingspagina.

Ga als volgt te werk om een nieuwe instantie te maken:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen. Deze koppeling kan **[!UICONTROL New...]** of een bestaande instantienaam zijn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld de URL van het type [`https://<machine>.<domain>.com`](https://myserver.adobe.com) gebruiken.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]`, `[A-Z]`, `[0-9]` en streepjes (-) of volledige stops.

1. Klik **[!UICONTROL Ok]** om de instellingen te bevestigen: U kunt nu beginnen met het maken van de instantie.
1. Voer in het venster **[!UICONTROL Connection settings]** de **internal**-aanmelding en het bijbehorende wachtwoord in om verbinding te maken met de Adobe Campaign-toepassingsserver. Nadat u verbinding hebt gemaakt, kunt u de wizard voor het maken van instanties gebruiken om een nieuwe instantie te declareren
1. Voer in het veld **[!UICONTROL Name]** de instantienaam **a2/> in.** Aangezien deze naam wordt gebruikt om een configuratiedossier **config-`<instance>`.xml** te produceren en in de parameters van de bevellijn wordt gebruikt om de instantie te identificeren, zorg ervoor u een korte naam zonder speciale karakters kiest. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet meer dan 40 tekens bevatten. Dit laat u de grootte van &quot;bericht-identiteitskaart&quot;kopballen beperken en verhindert berichten als spam, in het bijzonder door hulpmiddelen zoals SpamAssassin worden beschouwd.

1. Op **[!UICONTROL DNS masks]** gebieden, ga **lijst van DNS maskers** in waaraan de instantie zou moeten worden vastgemaakt. De Adobe Campaign-server gebruikt de hostnaam die in de HTTP-aanvragen wordt weergegeven om te bepalen welke instantie moet worden bereikt.

   De hostnaam bevindt zich tussen de tekenreeks **https://** en de eerste schuine streep **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De ? en * tekens kunnen worden gebruikt als jokertekens om een of meer tekens (DNS, poort, enz.) te vervangen. De waarde **demo*** werkt bijvoorbeeld met &quot;https://demo&quot;, net als met &quot;https://demo:8080&quot; en zelfs met &quot;https://demo2&quot;.

   De gebruikte namen moeten in uw DNS worden bepaald. U kunt de correspondentie tussen een DNS naam en een IP adres in **c:/windows/system32/drivers/etc/hosts** dossier in Vensters en in **/etc/hosts** dossier in Linux ook meedelen. Daarom moet u de verbindingsmontages wijzigen om deze DNS naam te gebruiken om met uw gekozen instantie te verbinden.

   De server moet met deze naam worden geïdentificeerd, met name voor het uploaden van afbeeldingen in e-mails.

   Daarnaast moet de server verbinding met zichzelf kunnen maken met deze naam en, indien mogelijk, met een loopbackadres - 127.0.0.1 -, vooral om rapporten te kunnen exporteren in PDF-indeling.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Language]** de instantietaal **instance language**: Engels (VS), Engels (VK), Frans of Japans.

   Verschillen tussen Engels in de VS en Engels in het VK worden beschreven in [deze sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Adobe Campaign-instanties zijn niet meertalig: u kunt niet de interface van een taal aan een andere schakelen.

1. Klik **[!UICONTROL Ok]** om instantiedeclaratie te bevestigen. Log uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan vanaf de opdrachtregel worden gemaakt. Voor meer op dit, verwijs naar [De lijnen van het Bevel](../../installation/using/command-lines.md).
