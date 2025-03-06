---
product: campaign
title: Binnenkomende e-mails
description: Meer informatie over de workflowactiviteiten voor inkomende e-mails
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# Binnenkomende e-mails{#inbound-emails}



De **Binnenkomende e-mail** activiteit laat u e-mailberichten van een POP3 postserver downloaden en verwerken.

![](assets/email_rec_edit_1.png)

Het eerste lusje van de **Binnenkomende E-mail** activiteit laat u de parameters van de POP3 server ingaan en het manuscript ingaan dat op ontvangstbewijs van elk bericht moet worden uitgevoerd. Het tweede lusje laat u een programma aan de activiteit toewijzen, en het derde lusje bepaalt de voorwaarden van de activiteitenvervaldatum.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     Wanneer deze optie is geactiveerd, kunt u een externe POP3-account selecteren in plaats van de verbindingsparameters in te voeren. In het veld **[!UICONTROL External account]** wordt de externe POP3-account opgegeven die moet worden gebruikt om verbinding te maken met de e-mailservice. Dit veld is alleen zichtbaar als de optie Een externe account gebruiken is ingeschakeld.

     Als deze optie niet is geselecteerd, moet u de volgende parameters opgeven:

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

        Naam van de POP3-server.

      * **[!UICONTROL POP3 account]**

        Naam van de gebruiker.

      * **[!UICONTROL Password]**

        Wachtwoord voor gebruikersaccount.

      * **[!UICONTROL Port]**

        POP3-poortnummer van verbinding. De standaardpoort is 10.

   * **[!UICONTROL Stop as soon as email is processed]**

     Met deze optie kunt u e-mailberichten een voor een verwerken. De activiteit activeert zijn overgang slechts eenmaal en voltooit dan verwerking, verlatend onverwerkte berichten op de server.

1. **[!UICONTROL Script]**

   Met het script kunt u het bericht verwerken en verschillende bewerkingen uitvoeren die afhankelijk zijn van de inhoud van het bericht. Het script wordt uitgevoerd voor elk bericht en kan bepalen welke bewerking op berichten moet worden uitgevoerd (het bericht verlaat of verwijdert) en hoe de uitgaande overgang moet worden geactiveerd.

   De retourcode moet een van de volgende waarden zijn:

   * 1 - Verwijdert het bericht van de server en activeert de uitgaande overgang.
   * 2 - Laat het bericht op de server achter en activeert de uitgaande overgang.
   * 3 - Hiermee verwijdert u het bericht van de server.
   * 4 - Laat het bericht op de server achter.

   De inhoud van het bericht is toegankelijk via de algemene variabele **[!UICONTROL mailMessage]** .

1. **[!UICONTROL Schedule]**

   Als u een schema voor de activiteit wilt definiëren, klikt u op de tab **[!UICONTROL Scheduling]** en schakelt u **[!UICONTROL Plan execution]** in. Klik op de knop **[!UICONTROL Change]** om het schema te configureren.

   De configuratie van het programma is het zelfde als voor de het plannen activiteit. Verwijs naar [ Planner ](scheduler.md).

1. **[!UICONTROL Expiration]**

   U kunt verloopvertragingen definiëren via het tabblad **[!UICONTROL Expiration]** .

   ![](assets/email_rec_edit_3.png)

   De configuratie is het zelfde als voor de het plannen activiteit. Verwijs naar [ Verlopen ](defining-approvals.md).
