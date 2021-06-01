---
product: campaign
title: Instanties configureren
description: Leer hoe te om de Transactionele controle en uitvoeringsinstanties van het overseinen in Adobe Campaign Classic te vormen.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 1%

---


# Instanties {#creating-a-shared-connection} configureren

Om de mogelijkheden van het transactionele overseinen te gebruiken, moet u de controle en uitvoeringsinstanties vormen. U kunt beide gebruiken:
* [Één controle ](#control-instance) instantie verbonden aan één of verscheidene uitvoeringsinstanties
* [Verschillende besturingsinstanties ](#using-several-control-instances) die zijn gekoppeld aan verschillende uitvoeringsinstanties

>[!IMPORTANT]
>
>De uitbreidingen van het schema beïnvloedden de middelen die door [technische werkschema&#39;s van het Centrum van het Bericht ](../../message-center/using/additional-configurations.md#technical-workflows) op of controle of uitvoeringsinstanties worden gebruikt moeten op de andere instanties worden gedupliceerd die door de Transactionele overseinenmodule worden gebruikt.

U moet ook de uitvoeringsinstantie(s) opgeven en verbinden met de besturingsinstantie(s).

Alle stappen nodig om de controle en uitvoeringsinstanties te vormen en aan te sluiten worden beschreven in deze sectie.

>[!IMPORTANT]
>
>De bedieningsinstantie en de uitvoeringsinstantie(s) moeten op verschillende computers zijn geïnstalleerd. Ze kunnen niet dezelfde Campagne-instantie delen.

## De besturingsinstantie {#control-instance} configureren

Om de controleinstantie en de uitvoeringsinstanties te verbinden, moet u eerst een **[!UICONTROL Execution instance]** type externe rekening **op de controleinstantie** creëren en vormen. Daarom kunnen zodra [published](../../message-center/using/publishing-message-templates.md#template-publication), transactionele berichtmalplaatjes aan de uitvoeringsinstanties worden opgesteld.

Als u meerdere uitvoeringsinstanties gebruikt, moet u net zoveel externe accounts maken als er uitvoeringen zijn.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar [Gebruikend verscheidene controleinstanties](#using-several-control-instances).

### Een externe account maken

>[!NOTE]
>
>De onderstaande stappen moeten worden uitgevoerd **op de besturingsinstantie**.

Als u een externe account van het type **[!UICONTROL Execution instance]** wilt maken, past u het volgende toe:

1. Ga naar de **[!UICONTROL Administration > Platform > External accounts]** omslag.
1. Selecteer een van de uitvoerinstantietypen voor externe accounts die bij Adobe Campaign buiten de box worden geleverd, klik met de rechtermuisknop en kies **[!UICONTROL Duplicate]**.

   ![](assets/messagecenter_create_extaccount_001.png)

1. Wijzig het label naar wens.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Selecteer de optie **[!UICONTROL Enabled]** om de externe account operationeel te maken.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Geef het adres op van de server waarop de uitvoeringsinstantie is geïnstalleerd.

   ![](assets/messagecenter_create_extaccount_004.png)

1. De rekening moet de Agent van het Centrum van het Bericht zoals die in de exploitantomslag wordt bepaald aanpassen. De door Adobe Campaign verschafte out-of-box-account is standaard **[!UICONTROL mc]**.

   ![](assets/messagecenter_create_extaccount_005.png)

1. Voer het wachtwoord van de account in zoals gedefinieerd in de map met operatoren.

   >[!NOTE]
   >
   >Om te vermijden ingaand een wachtwoord telkens als u aan de instantie het programma opent, kunt u het IP adres van de controleinstantie in de uitvoeringsinstantie specificeren. Voor meer op dit, verwijs naar [vorm de uitvoeringsinstantie(s)](#execution-instance).

1. Geef de herstelmethode op die door de uitvoeringsinstantie moet worden gebruikt. De gegevens die moeten terugkrijgen worden door:sturen aan de controleinstantie door de uitvoeringsinstantie, om aan transactiebericht en gebeurtenisarchieven toe te voegen.

   ![](assets/messagecenter_create_extaccount_007.png)

   De inzameling van gegevens komt of via de dienst van het Web voor die HTTP/HTTPS toegang, of via de Federated Module van de Toegang van Gegevens (FDA) gebruikt.

   >[!NOTE]
   >
   >Houd er rekening mee dat als u FDA via HTTP gebruikt, alleen uitvoeringsinstanties met een PostSQL-database worden ondersteund. MSSQL- of Oracle-databases worden niet ondersteund.

   De tweede methode (FDA) wordt geadviseerd als de controleinstantie directe toegang tot het gegevensbestand van de uitvoeringsinstanties heeft. Als niet, kies de de diensttoegang van het Web. De FDA rekening om te specificeren valt met de verbinding aan de gegevensbestanden van de diverse uitvoeringsinstanties die op de controleinstantie worden gecreeerd.

   ![](assets/messagecenter_create_extaccount_008.png)

   Raadpleeg [Toegang tot een externe database](../../installation/using/about-fda.md) voor meer informatie over FDA (Federated Data Access).

1. Klik **[!UICONTROL Test the connection]** om ervoor te zorgen de controleinstantie en de uitvoeringsinstantie omhoog worden verbonden.

   ![](assets/messagecenter_create_extaccount_006.png)

Herhaal deze stappen om zoveel externe accounts te maken als er uitvoeringsinstanties zijn.

### Uitvoeringsinstanties identificeren {#identifying-execution-instances}

Elke uitvoeringsinstantie moet met een unieke herkenningsteken worden geassocieerd om de geschiedenis van elke uitvoeringsinstantie te onderscheiden wanneer het bekijken van hen op de controleinstantie.

Deze id kan worden toegewezen aan elke uitvoeringsinstantie **handmatig**. In dit geval moet deze stap worden uitgevoerd **op elke uitvoeringsinstantie**. Hiervoor gebruikt u de implementatiewizard zoals hieronder beschreven:

1. Open de implementatiewizard op een uitvoeringsinstantie.
1. Ga naar het **[!UICONTROL Message Center]** venster.
1. Wijs de gekozen id toe aan de instantie.

   ![](assets/messagecenter_id_execinstance_001.png)

1. Herhaal bovenstaande stappen voor elke uitvoeringsinstantie.

De id kan ook **automatisch** worden toegewezen. Om dit te doen, ga naar **controleinstantie**, en klik **[!UICONTROL Initialize connection]** knoop.

![](assets/messagecenter_create_extaccount_006bis.png)

## De uitvoerinstantie(s) {#execution-instance} configureren

>[!NOTE]
>
>De onderstaande stappen moeten worden uitgevoerd **op de uitvoeringsinstantie(s)**.

Voer de onderstaande stappen uit om de uitvoeringsinstantie(s) aan te sluiten op de besturingsinstantie.

Opdat de controleinstantie met de uitvoeringsinstantie kan verbinden zonder het moeten een wachtwoord geven, ga eenvoudig het IP adres van de controleinstantie in het **Centrum van het Bericht** de sectie van toegangsrechten in. Lege wachtwoorden zijn echter standaard niet toegestaan.

Als u een leeg wachtwoord wilt gebruiken, gaat u naar de uitvoeringsinstanties en definieert u een beveiligingszone die is beperkt tot het IP-adres van het informatiesysteem dat de gebeurtenissen levert. Deze veiligheidszone moet lege wachtwoorden toestaan en `<identifier> / <password>` typeverbindingen goedkeuren. Raadpleeg [deze sectie](../../installation/using/security-zones.md) voor meer informatie.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar [Gebruikend verscheidene controleinstanties](#using-several-control-instances).

1. Ga bij een uitvoeringsinstantie naar de operatormap ( **[!UICONTROL Administration > Access management > Operators]**).
1. Selecteer **Message Center** agent.

   ![](assets/messagecenter_operator_001.png)

1. Selecteer de tab **[!UICONTROL Edit]**, klik op **[!UICONTROL Access rights]** en klik vervolgens op de koppeling **[!UICONTROL Edit the access parameters...]**.

   ![](assets/messagecenter_operator_002.png)

1. Klik in het venster **[!UICONTROL Access settings]** op de koppeling **[!UICONTROL Add a trusted IP mask]** en voeg het IP-adres van de besturingsinstantie toe.

   ![](assets/messagecenter_operator_003.png)

Herhaal deze stappen voor elke uitvoeringsinstantie wanneer u meerdere uitvoeringsinstanties gebruikt.

## Verschillende besturingsinstanties gebruiken {#using-several-control-instances}

U kunt een uitvoeringscluster met diverse controleinstanties delen. Voor dit type architectuur is de volgende configuratie vereist.

Stel dat uw bedrijf bijvoorbeeld twee merken beheert, elk met een eigen bedieningsinstantie: **Control 1** en **Control 2**. Er worden ook twee uitvoeringsinstanties gebruikt. U moet een verschillende exploitant van het Centrum van het Bericht voor elke controleinstantie ingaan: een **mc1** operator voor de **Control 1** instantie en een **mc2** operator voor de **Control 2** instantie.

Maak in de boomstructuur van alle uitvoeringsinstanties één map per operator (**Folder 1** en **Folder 2**) en beperk de gegevenstoegang van elke operator tot de bijbehorende map.

### Controleinstanties {#configuring-control-instances} configureren

>[!NOTE]
>
>De onderstaande stappen moeten worden uitgevoerd **op de besturingsinstanties**.

1. In **Control 1** controleinstantie, creeer één externe rekening per uitvoeringsinstantie, en ga **mc1** exploitant in elke externe rekening in. De **mc1** exploitant zal dan op alle uitvoeringsinstanties worden gecreeerd (verwijs naar [uitvoeringsinstanties vormen](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. In **Control 2** controleinstantie, creeer één externe rekening per uitvoeringsinstantie, en ga **mc2** exploitant in elke externe rekening in. De **mc2** exploitant zal daarna op alle uitvoeringsinstanties worden gecreeerd (verwijs naar [uitvoeringsinstanties vormen](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Voor meer bij het vormen van een controleinstantie, verwijs naar [deze sectie](#control-instance).

### Uitvoeringsinstanties {#configuring-execution-instances} configureren

>[!NOTE]
>
>De onderstaande stappen moeten worden uitgevoerd **op uitvoeringsinstanties**.

Om verscheidene controleinstanties te gebruiken, moet deze configuratie op ALLE uitvoeringsinstanties worden uitgevoerd.

1. Maak één map per operator in het knooppunt **[!UICONTROL Administration > Production > Message Center]**: **Map 1** en **Map 2**. Raadpleeg [deze pagina](../../platform/using/access-management-folders.md) voor meer informatie over het maken van mappen en weergaven.

   ![](assets/messagecenter_multi_control_3.png)

1. Maak de **mc1** en **mc2** exploitanten door de exploitant van het Centrum van het Bericht te dupliceren die door gebrek (**mc**) wordt verstrekt. Raadpleeg [deze sectie](../../platform/using/access-management-operators.md) voor meer informatie over het maken van operatoren.

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** en  **mc2** operatoren moeten  **[!UICONTROL Message Center execution]** rechten hebben en hebben geen toegang tot de Adobe Campaign-clientconsole. Een exploitant moet altijd met een veiligheidsstreek verbonden zijn. Raadpleeg [deze sectie](../../installation/using/security-zones.md) voor meer informatie.

1. Voor elke exploitant, controleer **[!UICONTROL Restrict to information found in sub-folders of]** doos, en selecteer de relevante omslag (**Omslag 1** voor de **mc1** exploitant en **Omslag 2** voor **mc2** exploitant).

   ![](assets/messagecenter_multi_control_5.png)

1. Geef elke exploitant lees en schrijf toestemmingen voor hun omslag. Klik hiertoe met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties]**. Selecteer vervolgens de tab **[!UICONTROL Security]** en voeg de relevante operator (**mc1** voor **Map 1** en **mc2** voor **Map 2**) toe. Controleer of de selectievakjes **[!UICONTROL Read/Write data]** zijn ingeschakeld.

   ![](assets/messagecenter_multi_control_6.png)
