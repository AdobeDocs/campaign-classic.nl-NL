---
product: campaign
title: Een instantie maken en aanmelden
description: Een instantie maken en aanmelden
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 1%

---

# Een instantie maken en aanmelden{#creating-an-instance-and-logging-on}



Pas het volgende proces toe om een nieuwe instantie en een Adobe Campaign-database te maken:

1. Maak de verbinding.
1. Meld u aan om de verwante instantie te maken.
1. Maak en configureer de database.

>[!NOTE]
>
>Slechts kan het **interne** herkenningsteken deze verrichtingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

Wanneer de Adobe Campaign-console wordt gestart, opent u een aanmeldingspagina.

Ga als volgt te werk om een nieuwe instantie te maken:

1. Klik op de koppeling in de rechterbovenhoek van de aanmeldingsvelden om het venster voor de verbindingsconfiguratie te openen. Deze koppeling kan **[!UICONTROL New...]** of een bestaande instantienaam zijn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klik op **[!UICONTROL Add > Connection]** en voer het label en de URL van de Adobe Campaign-toepassingsserver in.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geef een verbinding met uw Adobe Campaign-toepassingsserver op via een URL. Gebruik of DNS of een alias van de machine, of uw IP adres.

   U kunt bijvoorbeeld het type URL `https://<machine>.<domain>.com` gebruiken.

   >[!CAUTION]
   >
   >Gebruik voor de verbindings-URL alleen de volgende tekens: `[a-z]` , `[A-Z]` , `[0-9]` en streepjes (-) of volledige stops.

1. Klik op **[!UICONTROL Ok]** om de instellingen te bevestigen: u kunt nu beginnen met het maken van de instantie.
1. In het **[!UICONTROL Connection settings]** venster, ga **interne** login en zijn wachtwoord in om met de de toepassingsserver van Adobe Campaign te verbinden. Zodra verbonden, hebt u toegang tot de medewerker van de instantiescreatie om een nieuwe instantie te verklaren
1. Op het **[!UICONTROL Name]** gebied, ga de **instantienaam** in. Aangezien deze naam wordt gebruikt om een configuratiedossier **config- `<instance>` .xml** te produceren en in de parameters van de bevellijn wordt gebruikt om de instantie te identificeren, zorg ervoor u een korte naam zonder speciale karakters kiest. Bijvoorbeeld: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   De naam van de instantie die aan de domeinnaam wordt toegevoegd, mag niet meer dan 40 tekens bevatten. Dit laat u de grootte van &quot;bericht-identiteitskaart&quot;kopballen beperken en verhindert berichten als spam, in het bijzonder door hulpmiddelen zoals SpamAssassin worden beschouwd.

1. Op de **[!UICONTROL DNS masks]** gebieden, ga de **lijst van DNS maskers** in waaraan de instantie zou moeten worden vastgemaakt. De Adobe Campaign-server gebruikt de hostnaam die in de HTTP-aanvragen wordt weergegeven om te bepalen welke instantie moet worden bereikt.

   Hostname is bevat tussen het koord **https://** en het eerste schuine streep karakter **/** van het serveradres.

   U kunt een lijst met waarden definiëren, gescheiden door komma&#39;s.

   De ? en &#42; -tekens kunnen worden gebruikt als jokertekens ter vervanging van een of meer tekens (DNS, poort, enz.). Bijvoorbeeld, zal de **demo&#42;** waarde met &quot;https://demo&quot;werken aangezien het met &quot;https://demo :8080&quot;en zelfs &quot;https://demo2&quot;zal.

   De gebruikte namen moeten in uw DNS worden bepaald. U kunt de correspondentie tussen een DNS naam en een IP adres in **c:/windows/system32/drivers/etc/hosts** dossier in Vensters en in het **/etc/hosts** dossier in Linux ook meedelen. Daarom moet u de verbindingsmontages wijzigen om deze DNS naam te gebruiken om met uw gekozen instantie te verbinden.

   De server moet met deze naam worden geïdentificeerd, met name voor het uploaden van afbeeldingen in e-mails.

   Daarnaast moet de server verbinding met zichzelf kunnen maken met deze naam en, indien mogelijk, met een loopbackadres - 127.0.0.1 , vooral om rapporten te kunnen exporteren in PDF-indeling.

1. In de **[!UICONTROL Language]** drop-down lijst, selecteer de **instantietaal**: Engels (V.S.), Engels (VK), Frans, of Japans.

   De verschillen tussen het Engels van de V.S. en het Engels van het VK worden beschreven in [ Campagne v8 (console) documentatie ] (.https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/new/campaign-ui).

   >[!CAUTION]
   >
   >De instantietaal kan na deze stap niet meer worden gewijzigd. Adobe Campaign-instanties zijn niet meertalig: u kunt de interface niet van taal naar taal schakelen.

1. Klik op **[!UICONTROL Ok]** om de instantiedeclaratie te bevestigen. Log uit en weer aan om de database te declareren.

   >[!NOTE]
   >
   >De instantie kan vanaf de opdrachtregel worden gemaakt. Voor meer op dit, verwijs naar [&#x200B; lijnen van het Bevel &#x200B;](../../installation/using/command-lines.md).
