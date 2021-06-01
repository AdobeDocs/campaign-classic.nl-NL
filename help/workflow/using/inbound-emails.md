---
product: campaign
title: Binnenkomende e-mails
description: Meer informatie over de workflowactiviteiten voor inkomende e-mails
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# Binnenkomende e-mails{#inbound-emails}

Met de activiteit **Binnenkomende e-mails** kunt u e-mailberichten downloaden en verwerken vanaf een POP3-mailserver.

![](assets/email_rec_edit_1.png)

Het eerste lusje van **Binnenkomende E-mail** activiteit laat u de parameters van de POP3 server ingaan en het manuscript ingaan dat op ontvangstbewijs van elk bericht moet worden uitgevoerd. Het tweede lusje laat u een programma aan de activiteit toewijzen, en het derde lusje bepaalt de voorwaarden van de activiteitenvervaldatum.

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

         POP3-poortnummer van verbinding. De standaardpoort is 110.
   * **[!UICONTROL Stop as soon as email is processed]**

      Met deze optie kunt u e-mailberichten een voor een verwerken. De activiteit activeert zijn overgang slechts eenmaal en voltooit dan verwerking, verlatend onverwerkte berichten op de server.


1. **[!UICONTROL Script]**

   Met het script kunt u het bericht verwerken en verschillende bewerkingen uitvoeren die afhankelijk zijn van de inhoud van het bericht. Het script wordt uitgevoerd voor elk bericht en kan bepalen welke bewerking op berichten moet worden uitgevoerd (het bericht verlaat of verwijdert) en hoe de uitgaande overgang moet worden geactiveerd.

   De retourcode moet een van de volgende waarden zijn:

   * 1 - Verwijdert het bericht van de server en activeert de uitgaande overgang.
   * 2 - Laat het bericht op de server achter en activeert de uitgaande overgang.
   * 3 - Hiermee verwijdert u het bericht van de server.
   * 4 - Laat het bericht op de server achter.

   De inhoud van het bericht is toegankelijk vanuit de algemene variabele **[!UICONTROL mailMessage]**.

1. **[!UICONTROL Schedule]**

   Als u een schema voor de activiteit wilt definiëren, klikt u op het tabblad **[!UICONTROL Scheduling]** en schakelt u **[!UICONTROL Plan execution]** in. Klik **[!UICONTROL Change]** knoop om het programma te vormen.

   De configuratie van het programma is het zelfde als voor de het plannen activiteit. Zie [Planner](../../workflow/using/scheduler.md).

1. **[!UICONTROL Expiration]**

   U kunt vertragingen bij verlopen definiëren via het tabblad **[!UICONTROL Expiration]**.

   ![](assets/email_rec_edit_3.png)

   De configuratie is het zelfde als voor de het plannen activiteit. Zie [Verlopen](../../workflow/using/defining-approvals.md).
