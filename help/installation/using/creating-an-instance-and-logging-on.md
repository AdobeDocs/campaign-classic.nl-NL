---
product: campaign
title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 5%

---

# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}



Pas het volgende proces toe om een nieuwe instantie en een Adobe Campaign-database te maken:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. De database maken en configureren.

>[!NOTE]
>
>Alleen de **internal** identificator kan deze bewerkingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

Wanneer de Adobe Campaign-console wordt gestart, opent u een aanmeldingspagina.

Ga als volgt te werk om een nieuwe instantie te maken:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen. Deze koppeling kan **[!UICONTROL New...]** of een bestaande instantienaam.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klikken **[!UICONTROL Add > Connection]** en voert u het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld de opdracht `https://<machine>.<domain>.com` type URL.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]`, `[A-Z]`, `[0-9]` en streepjes (-) of volledige stops.

1. Klikken **[!UICONTROL Ok]** om de instellingen te bevestigen: U kunt nu beginnen met het maken van de instantie.
1. In de **[!UICONTROL Connection settings]** venster, voert u de **internal** en het bijbehorende wachtwoord om verbinding te maken met de Adobe Campaign-toepassingsserver. Nadat u verbinding hebt gemaakt, kunt u de wizard voor het maken van instanties gebruiken om een nieuwe instantie te declareren
1. In de **[!UICONTROL Name]** veld, voert u de **instantienaam**. Aangezien deze naam wordt gebruikt om een configuratiedossier te produceren **config-`<instance>`.xml** en wordt gebruikt in de opdrachtregelparameters om de instantie te identificeren, controleert u of u een korte naam zonder speciale tekens kiest. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet meer dan 40 tekens bevatten. Dit laat u de grootte van &quot;bericht-identiteitskaart&quot;kopballen beperken en verhindert berichten als spam, in het bijzonder door hulpmiddelen zoals SpamAssassin worden beschouwd.

1. In de **[!UICONTROL DNS masks]** velden, voert u de **lijst met DNS-maskers** waaraan de instantie moet worden toegevoegd. De Adobe Campaign-server gebruikt de hostnaam die in de HTTP-aanvragen wordt weergegeven om te bepalen welke instantie moet worden bereikt.

   De hostnaam staat tussen de tekenreeks **https://** en de eerste schuine streep **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De ? en &#42; tekens kunnen worden gebruikt als jokertekens om een of meer tekens (DNS, poort, enz.) te vervangen. Bijvoorbeeld de **demo&#42;** value werkt met &quot;https://demo&quot; zoals met &quot;https://demo:8080&quot; en zelfs met &quot;https://demo2&quot;.

   De gebruikte namen moeten in uw DNS worden bepaald. U kunt ook de correspondentie tussen een DNS-naam en een IP-adres in het dialoogvenster **c:/windows/system32/drivers/etc/hosts** in Windows en in het **/etc/hosts** in Linux. Daarom moet u de verbindingsmontages wijzigen om deze DNS naam te gebruiken om met uw gekozen instantie te verbinden.

   De server moet met deze naam worden geïdentificeerd, met name voor het uploaden van afbeeldingen in e-mails.

   Bovendien moet de server met zich door deze naam, en indien mogelijk door een loopbackadres - 127.0.0.1 - kunnen verbinden, vooral om rapporten toe te staan om in formaat van PDF worden uitgevoerd.

1. In de **[!UICONTROL Language]** vervolgkeuzelijst selecteert u de **instantietaal**: Engels (VS), Engels (VK), Frans of Japans.

   Verschillen tussen Engels in de VS en Engels in het VK worden beschreven in [deze sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Adobe Campaign-instanties zijn niet meertalig: u kunt niet de interface van een taal aan een andere schakelen.

1. Klikken **[!UICONTROL Ok]** ter bevestiging van de instantieverklaring. Log uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan vanaf de opdrachtregel worden gemaakt. Raadpleeg voor meer informatie hierover [Opdrachtlijnen](../../installation/using/command-lines.md).
