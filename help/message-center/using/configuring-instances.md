---
product: campaign
title: Instanties configureren
description: Leer hoe te om de Transactieoverseinencontrole en uitvoeringsinstanties in Adobe Campaign Classic te vormen
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 221e2ccdaadf793212fcacdf5e13823f1505f4dc
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 1%

---


# Instanties configureren {#creating-a-shared-connection}



Om de mogelijkheden van het transactionele overseinen te gebruiken, moet u de controle en uitvoeringsinstanties vormen. U kunt beide gebruiken:
* [&#x200B; Één controleinstantie &#x200B;](#control-instance) verbonden aan één of verscheidene uitvoeringsinstanties
* [&#x200B; Verscheidene controleinstanties &#x200B;](#using-several-control-instances) verbonden aan verscheidene uitvoeringsinstanties

>[!IMPORTANT]
>
>De uitbreidingen van het schema beïnvloedden de middelen die door [&#x200B; technische werkschema&#39;s van het Centrum van het Bericht &#x200B;](../../message-center/using/additional-configurations.md#technical-workflows) op of controle of uitvoeringsinstanties worden gebruikt moeten op de andere instanties worden gedupliceerd die door de Transactionele overseinenmodule worden gebruikt.

U moet ook de uitvoeringsinstantie(s) opgeven en verbinden met de besturingsinstantie(s).

Alle stappen nodig om de controle en uitvoeringsinstanties te vormen en aan te sluiten worden beschreven in deze sectie.

>[!IMPORTANT]
>
>De bedieningsinstantie en de uitvoeringsinstantie(s) moeten op verschillende computers zijn geïnstalleerd. Ze kunnen niet dezelfde Campagne-instantie delen.

## Vorm de controleinstantie {#control-instance}

Om de controleinstantie en de uitvoeringsinstanties te verbinden, moet u eerst een **[!UICONTROL Execution instance]** type externe rekening **op de controleinstantie** creëren en vormen. Daarom zodra [&#x200B; gepubliceerd &#x200B;](../../message-center/using/publishing-message-templates.md#template-publication), transactionele berichtmalplaatjes aan de uitvoeringsinstanties kunnen worden opgesteld.

Als u meerdere uitvoeringsinstanties gebruikt, moet u net zoveel externe accounts maken als er uitvoeringen zijn.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, zie [&#x200B; Gebruik verscheidene controleinstanties &#x200B;](#using-several-control-instances).

### Een externe account maken

>[!NOTE]
>
>De stappen hieronder moeten **op de controleinstantie** worden uitgevoerd.

Pas het volgende toe om een **[!UICONTROL Execution instance]** type extern account te maken:

1. Ga naar de map **[!UICONTROL Administration > Platform > External accounts]** .
1. Selecteer een van de uitvoerinstantietypen voor externe accounts die in Adobe Campaign buiten het vak zijn geplaatst, klik met de rechtermuisknop en kies **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Wijzig het label naar wens.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Selecteer de optie **[!UICONTROL Enabled]** om de externe account operationeel te maken.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Geef het adres op van de server waarop de uitvoeringsinstantie is geïnstalleerd.

   ![](assets/messagecenter_create_extaccount_004.png)

1. De rekening moet de Agent van het Centrum van het Bericht zoals die in de exploitantomslag wordt bepaald aanpassen. De door Adobe Campaign verschafte out-of-box-account is standaard ingesteld op **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Voer het wachtwoord van de account in zoals gedefinieerd in de map met operatoren.

   >[!NOTE]
   >
   >Om te vermijden ingaand een wachtwoord telkens als u aan de instantie het programma opent, kunt u het IP adres van de controleinstantie in de uitvoeringsinstantie specificeren. Voor meer op dit, zie [&#x200B; de uitvoeringsinstantie(s) &#x200B;](#execution-instance) vormen.

1. Geef de herstelmethode op die door de uitvoeringsinstantie moet worden gebruikt. De gegevens die moeten terugkrijgen worden door:sturen aan de controleinstantie door de uitvoeringsinstantie, om aan transactiebericht en gebeurtenisarchieven toe te voegen.

   ![](assets/messagecenter_create_extaccount_007.png)

   De inzameling van gegevens komt of via de dienst van het Web voor die HTTP/HTTPS toegang, of via de Federated Module van de Toegang van Gegevens (FDA) gebruikt.

   >[!NOTE]
   >
   >Houd er rekening mee dat als u FDA via HTTP gebruikt, alleen uitvoeringsinstanties met een PostSQL-database worden ondersteund. MSSQL of Oracle databases worden niet ondersteund.

   De tweede methode (FDA) wordt geadviseerd als de controleinstantie directe toegang tot het gegevensbestand van de uitvoeringsinstanties heeft. Als niet, kies de de diensttoegang van het Web. De FDA rekening om te specificeren valt met de verbinding aan de gegevensbestanden van de diverse uitvoeringsinstanties die op de controleinstantie worden gecreeerd.

   ![](assets/messagecenter_create_extaccount_008.png)

   Voor meer informatie over Federated Data Access (FDA), verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/about-fda.md).

1. Klik op **[!UICONTROL Test the connection]** om ervoor te zorgen dat de besturingsinstantie en de uitvoeringsinstantie zijn gekoppeld.

   ![](assets/messagecenter_create_extaccount_006.png)

Herhaal deze stappen om zoveel externe accounts te maken als er uitvoeringsinstanties zijn.

### Uitvoeringsinstanties identificeren {#identifying-execution-instances}

Elke uitvoeringsinstantie moet met een unieke herkenningsteken worden geassocieerd om de geschiedenis van elke uitvoeringsinstantie te onderscheiden wanneer het bekijken van hen op de controleinstantie.

Dit herkenningsteken kan op elke uitvoeringsinstantie **manueel** worden toegeschreven. In dit geval, moet deze stap **op elke uitvoeringsinstantie** worden uitgevoerd. Hiervoor gebruikt u de implementatiewizard zoals hieronder beschreven:

1. Open de implementatiewizard op een uitvoeringsinstantie.
1. Ga naar het **[!UICONTROL Message Center]** -venster.
1. Wijs de gekozen id toe aan de instantie.

   ![](assets/messagecenter_id_execinstance_001.png)

1. Herhaal bovenstaande stappen voor elke uitvoeringsinstantie.

Het herkenningsteken kan ook **automatisch** worden toegeschreven. Om dit te doen, ga naar de **controleinstantie**, en klik de **[!UICONTROL Initialize connection]** knoop.

![](assets/messagecenter_create_extaccount_006bis.png)

## De uitvoeringsinstantie(s) configureren {#execution-instance}

>[!NOTE]
>
>De stappen hieronder moeten **op de uitvoeringsinstantie(s)** worden uitgevoerd.

Voer de onderstaande stappen uit om de uitvoeringsinstantie(s) aan te sluiten op de besturingsinstantie.

Opdat de controleinstantie met de uitvoeringsinstantie kan verbinden zonder het moeten een wachtwoord geven, ga eenvoudig het IP adres van de controleinstantie in de **sectie van de toegangsrechten van het Centrum van het Bericht** in. Lege wachtwoorden zijn echter standaard niet toegestaan.

Als u een leeg wachtwoord wilt gebruiken, gaat u naar de uitvoeringsinstanties en definieert u een beveiligingszone die is beperkt tot het IP-adres van het informatiesysteem dat de gebeurtenissen levert. Deze beveiligingszone moet lege wachtwoorden toestaan en `<identifier> / <password>` -typeverbindingen accepteren. Raadpleeg [deze sectie](../../installation/using/security-zones.md) voor meer informatie.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, zie [&#x200B; Gebruik verscheidene controleinstanties &#x200B;](#using-several-control-instances).

1. Ga bij een uitvoeringsinstantie naar de operatormap ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Selecteer de **agent van het Centrum van het Bericht**.

   ![](assets/messagecenter_operator_001.png)

1. Selecteer de tab **[!UICONTROL Edit]** , klik op **[!UICONTROL Access rights]** en klik vervolgens op de koppeling **[!UICONTROL Edit the access parameters...]** .

   ![](assets/messagecenter_operator_002.png)

1. Klik in het venster **[!UICONTROL Access settings]** op de koppeling **[!UICONTROL Add a trusted IP mask]** en voeg het IP-adres van de besturingsinstantie toe.

   ![](assets/messagecenter_operator_003.png)

Herhaal deze stappen voor elke uitvoeringsinstantie wanneer u meerdere uitvoeringsinstanties gebruikt.

## Verschillende besturingsinstanties gebruiken {#using-several-control-instances}

U kunt een uitvoeringscluster met diverse controleinstanties delen. Voor dit type architectuur is de volgende configuratie vereist.

Bijvoorbeeld, veronderstel uw bedrijf twee merken beheert, elk met zijn eigen controleinstantie: **Controle 1** en **Controle 2**. Er worden ook twee uitvoeringsinstanties gebruikt. U moet een verschillende exploitant van het Centrum van het Bericht voor elke controleinstantie ingaan: een **mc1** exploitant voor de **Controle 1** instantie en een **mc2** exploitant voor de **Controle 2** instantie.

In de boom van alle uitvoeringsinstanties, creeer één omslag per exploitant (**Omslag 1** en **Omslag 2**), en beperkt de gegevenstoegang van elke exploitant tot hun omslag.

### Controleinstanties configureren {#configuring-control-instances}

>[!NOTE]
>
>De stappen hieronder moeten **op de controleinstanties** worden uitgevoerd.

1. Op **Controle 1** controlegeval, creeer één externe rekening per uitvoeringsinstantie, en ga de **mc1** exploitant in elke externe rekening in. De {**exploitant 0} mc1 zal daarna op alle uitvoeringsinstanties (zie** uitvoeringsinstanties [&#x200B; vormen) worden gecreeerd.](#configuring-execution-instances)

   ![](assets/messagecenter_multi_control_1.png)

1. Op **Controle 2** controlegeval, creeer één externe rekening per uitvoeringsinstantie, en ga de **mc2** exploitant in elke externe rekening in. De **mc2** exploitant zal daarna op alle uitvoeringsinstanties (zie [&#x200B; uitvoeringsinstanties &#x200B;](#configuring-execution-instances) vormen) worden gecreeerd.

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Voor meer bij het vormen van een controleinstantie, zie [&#x200B; deze sectie &#x200B;](#control-instance).

### Uitvoeringsinstanties configureren {#configuring-execution-instances}

>[!NOTE]
>
>De stappen hieronder moeten **op de uitvoeringsinstanties** worden uitgevoerd.

Om verscheidene controleinstanties te gebruiken, moet deze configuratie op ALLE uitvoeringsinstanties worden uitgevoerd.

1. Creeer één omslag per exploitant in de **[!UICONTROL Administration > Production > Message Center]** knoop: **Omslag 1** en **Omslag 2**. Leer meer over omslagen en meningen in [&#x200B; Campagne v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.

   ![](assets/messagecenter_multi_control_3.png)

1. Creeer **mc1** en **mc2** exploitanten door de exploitant van het Centrum van het Bericht te dupliceren die door gebrek wordt verstrekt (**mc**). Voor meer bij het creëren van exploitanten, verwijs naar [&#x200B; deze sectie &#x200B;](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** en **mc2** exploitanten moeten **[!UICONTROL Message Center execution]** rechten hebben en zij kunnen geen toegang tot de de cliëntconsole van Adobe Campaign hebben. Een exploitant moet altijd met een veiligheidsstreek verbonden zijn. Raadpleeg [deze sectie](../../installation/using/security-zones.md) voor meer informatie.

1. Voor elke exploitant, controleer de **[!UICONTROL Restrict to information found in sub-folders of]** doos, en selecteer de relevante omslag (**Omslag 1** voor de **mc1** exploitant en **Omslag 2** voor de **mc2** exploitant).

   ![](assets/messagecenter_multi_control_5.png)

1. Geef elke exploitant lees en schrijf toestemmingen voor hun omslag. Klik hiertoe met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties]** . Dan selecteer het **[!UICONTROL Security]** lusje en voeg de relevante exploitant (**mc1** voor **Omslag 1** en **mc2** voor **Omslag 2**) toe. Controleer of de vakken **[!UICONTROL Read/Write data]** zijn ingeschakeld.

   ![](assets/messagecenter_multi_control_6.png)
