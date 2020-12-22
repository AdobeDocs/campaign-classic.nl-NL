---
solution: Campaign Classic
product: campaign
title: Een gedeelde verbinding maken
description: Een gedeelde verbinding maken
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 2%

---


# Een gedeelde verbinding maken{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* De uitbreidingen van het schema die op de schema&#39;s worden gemaakt door [technische werkschema&#39;s van het Centrum van het Bericht](../../message-center/using/technical-workflows.md) op of controle of uitvoeringsinstanties worden gebruikt moeten op de andere instanties worden gedupliceerd die door de module van het de transactionele overseinen van Adobe Campaign worden gebruikt.
>* De bedieningsinstantie en de uitvoeringsinstantie(s) moeten op verschillende computers zijn geïnstalleerd. Ze kunnen niet dezelfde Campagne-instantie delen.

>



## Control-instantie {#control-instance}

Als u een opgesplitste architectuur hebt, moet u de uitvoeringsinstanties specificeren verbonden aan de controleinstantie en hen verbinden. De transactionele berichtmalplaatjes worden opgesteld aan de uitvoeringsinstanties. De verbinding tussen de controleinstantie en de uitvoeringsinstanties wordt gecreeerd door **[!UICONTROL Execution instance]** type externe rekeningen te vormen. U moet zoveel externe accounts maken als er uitvoeringen zijn.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar [Gebruikend verscheidene controleinstanties](#using-several-control-instances).

Voer de volgende stappen uit om een uitvoerinstantie van het type externe account te maken:

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
   >Om te vermijden ingaand een wachtwoord telkens als u aan de instantie het programma opent, kunt u het IP adres van de controleinstantie in de uitvoeringsinstantie specificeren. Raadpleeg [Uitvoeringsinstantie](#execution-instance) voor meer informatie hierover.

1. Geef de herstelmethode op die door de uitvoeringsinstantie moet worden gebruikt.

   De gegevens die moeten terugkrijgen worden door:sturen aan de controleinstantie door de uitvoeringsinstantie, om aan transactiebericht en gebeurtenisarchieven toe te voegen.

   ![](assets/messagecenter_create_extaccount_007.png)

   De inzameling van gegevens komt of via de dienst van het Web voor die HTTP/HTTPS toegang, of via de Federated Module van de Toegang van Gegevens (FDA) gebruikt.

   >[!NOTE]
   >
   >Houd er rekening mee dat als u FDA via HTTP gebruikt, alleen uitvoeringsinstanties met een PostSQL-database worden ondersteund. MSSQL- of Oracle-databases worden niet ondersteund.

   De tweede methode wordt geadviseerd als de controleinstantie directe toegang tot het gegevensbestand van de uitvoeringsinstanties heeft. Als niet, kies de de diensttoegang van het Web. De FDA rekening om te specificeren valt met de verbinding aan de gegevensbestanden van de diverse uitvoeringsinstanties die op de controleinstantie worden gecreeerd.

   ![](assets/messagecenter_create_extaccount_008.png)

   Raadpleeg [Toegang tot een externe database](../../installation/using/about-fda.md) voor meer informatie over FDA (Federated Data Access).

1. Klik **[!UICONTROL Test the connection]** om ervoor te zorgen de controleinstantie en de uitvoeringsinstantie omhoog worden verbonden.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Elke uitvoeringsinstantie moet aan een id worden gekoppeld. Deze id kan op elke uitvoeringsinstantie of manueel worden toegeschreven, door de plaatsingstovenaar te gebruiken (verwijs naar [Uitvoeringsinstanties identificeren](../../message-center/using/identifying-execution-instances.md)), of automatisch, door **te klikken initialiseert verbinding** knoop van de controleinstantie.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Uitvoeringsinstantie {#execution-instance}

Opdat de controleinstantie met de uitvoeringsinstantie kan verbinden zonder het moeten een wachtwoord geven, ga eenvoudig het IP adres van de controleinstantie in het **Centrum van het Bericht** de sectie van toegangsrechten in. Lege wachtwoorden zijn echter standaard niet toegestaan.

Als u een leeg wachtwoord wilt gebruiken, gaat u naar de uitvoeringsinstanties en definieert u een beveiligingszone die is beperkt tot het IP-adres van het informatiesysteem dat de gebeurtenissen levert. Deze veiligheidszone moet lege wachtwoorden toestaan en `<identifier> / <password>` typeverbindingen goedkeuren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones) voor meer informatie.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar [Gebruikend verscheidene controleinstanties](#using-several-control-instances).

1. Ga naar de exploitantomslag in de uitvoeringsinstantie ( **[!UICONTROL Administration > Access management > Operators]**).
1. Selecteer **Message Center** agent.

   ![](assets/messagecenter_operator_001.png)

1. Selecteer de tab **[!UICONTROL Edit]**, klik op **[!UICONTROL Access rights]** en klik vervolgens op de koppeling **[!UICONTROL Edit the access parameters...]**.

   ![](assets/messagecenter_operator_002.png)

1. Klik in het venster **[!UICONTROL Access settings]** op de koppeling **[!UICONTROL Add a trusted IP mask]** en voeg het IP-adres van de besturingsinstantie toe.

   ![](assets/messagecenter_operator_003.png)

## Verschillende besturingsinstanties gebruiken {#using-several-control-instances}

U kunt een uitvoeringscluster met diverse controleinstanties delen. Voor dit type architectuur is de volgende configuratie vereist.

Bijvoorbeeld als uw bedrijf twee merken beheert, elk met zijn eigen controleinstantie: **Control 1** en **Control 2**. Er worden ook twee uitvoeringsinstanties gebruikt. U moet een verschillende exploitant van het Centrum van het Bericht voor elke controleinstantie ingaan: een **mc1** operator voor de **Control 1** instantie en een **mc2** operator voor de **Control 2** instantie.

Maak in de boomstructuur van alle uitvoeringsinstanties één map per operator (**Folder 1** en **Folder 2**) en beperk de gegevenstoegang van elke operator tot de bijbehorende map.

### Configureren van besturingsinstanties {#configuring-control-instances}

1. In **Control 1** controleinstantie, creeer één externe rekening per uitvoeringsinstantie, en ga **mc1** exploitant in elke externe rekening in. De **mc1** exploitant zal dan op alle uitvoeringsinstanties worden gecreeerd (verwijs naar [Het vormen van uitvoeringsinstanties](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. In **Control 2** controleinstantie, creeer één externe rekening per uitvoeringsinstantie, en ga **mc2** exploitant in elke externe rekening in. De **mc2** exploitant zal daarna op alle uitvoeringsinstanties worden gecreeerd (verwijs naar [Het vormen van uitvoeringsinstanties](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Voor meer bij het vormen van een controleinstantie, verwijs naar [Controleinstantie](#control-instance).

### Uitvoeringsinstanties {#configuring-execution-instances} configureren

Om verscheidene controleinstanties te gebruiken, moet deze configuratie op ALLE uitvoeringsinstanties worden uitgevoerd.

1. Maak één map per operator in het knooppunt **[!UICONTROL Administration > Production > Message Center]**: **Map 1** en **Map 2**. Raadpleeg [Platform](../../platform/using/access-management.md#folders-and-views) voor meer informatie over het maken van mappen en weergaven.

   ![](assets/messagecenter_multi_control_3.png)

1. Maak de **mc1** en **mc2** exploitanten door de exploitant van het Centrum van het Bericht te dupliceren die door gebrek (**mc**) wordt verstrekt. Raadpleeg [deze sectie](../../platform/using/access-management.md#operators) voor meer informatie over het maken van operatoren.

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** en  **mc2** operatoren moeten  **[!UICONTROL Message Center execution]** rechten hebben en hebben geen toegang tot de Adobe Campaign-clientconsole. Een exploitant moet altijd met een veiligheidsstreek verbonden zijn. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones) voor meer informatie.

1. Voor elke exploitant, controleer **[!UICONTROL Restrict to information found in sub-folders of]** doos, en selecteer de relevante omslag (**Omslag 1** voor de **mc1** exploitant en **Omslag 2** voor **mc2** exploitant).

   ![](assets/messagecenter_multi_control_5.png)

1. Geef elke exploitant lees en schrijf toestemmingen voor hun omslag. Klik hiertoe met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties]**. Selecteer vervolgens de tab **[!UICONTROL Security]** en voeg de relevante operator (**mc1** voor **Map 1** en **mc2** voor **Map 2**) toe. Controleer of de selectievakjes **[!UICONTROL Read/Write data]** zijn ingeschakeld.

   ![](assets/messagecenter_multi_control_6.png)

