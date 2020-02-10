---
title: Een gedeelde verbinding maken
seo-title: Een gedeelde verbinding maken
description: Een gedeelde verbinding maken
seo-description: null
page-status-flag: never-activated
uuid: 30d6d23b-72c6-4454-8d6b-a10102f89262
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 7f471ac1-cd6a-4371-977e-52d60ce8d968
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Een gedeelde verbinding maken{#creating-a-shared-connection}

>[!CAUTION]
>
>* De uitbreidingen van het schema die op de schema&#39;s worden gemaakt door de technische werkschema [&#39;s van het Centrum van het](../../message-center/using/technical-workflows.md) Bericht op of controle of uitvoeringsinstanties worden gebruikt moeten op de andere instanties worden gedupliceerd die door de transactionele overseinenmodule van de Campagne van Adobe worden gebruikt.
>* De bedieningsinstantie en de uitvoeringsinstantie(s) moeten op verschillende computers zijn geïnstalleerd. Ze kunnen niet dezelfde Campagne-instantie delen.
>



## Control-instantie {#control-instance}

Als u een opgesplitste architectuur hebt, moet u de uitvoeringsinstanties specificeren verbonden aan de controleinstantie en hen verbinden. Transactionele berichtmalplaatjes worden opgesteld aan de uitvoeringsinstanties. De verbinding tussen de controleinstantie en de uitvoeringsinstanties wordt gecreeerd door het type externe rekeningen te vormen. **[!UICONTROL Execution instance]** U moet zoveel externe accounts maken als er uitvoeringen zijn.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar het [Gebruiken van verscheidene controleinstanties](#using-several-control-instances).

Voer de volgende stappen uit om een uitvoerinstantie van het type externe account te maken:

1. Ga naar de **[!UICONTROL Administration > Platform > External accounts]** map.
1. Selecteer een van de uitvoerinstantietypen voor externe accounts die bij Adobe Campagne buiten het vak zijn geplaatst, klik met de rechtermuisknop en kies **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Wijzig het label naar wens.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Selecteer de **[!UICONTROL Enabled]** optie om de externe account operationeel te maken.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Geef het adres op van de server waarop de uitvoeringsinstantie is geïnstalleerd.

   ![](assets/messagecenter_create_extaccount_004.png)

1. De rekening moet de Agent van het Centrum van het Bericht zoals die in de exploitantomslag wordt bepaald aanpassen. Standaard wordt het account buiten de box van Adobe Campaign geleverd **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Voer het wachtwoord van de account in zoals gedefinieerd in de map met operatoren.

   >[!NOTE]
   >
   >Om te vermijden ingaand een wachtwoord telkens als u aan de instantie het programma opent, kunt u het IP adres van de controleinstantie in de uitvoeringsinstantie specificeren. Raadpleeg de [uitvoeringsinstantie](#execution-instance)voor meer informatie hierover.

1. Geef de herstelmethode op die door de uitvoeringsinstantie moet worden gebruikt.

   De gegevens die moeten terugkrijgen worden door:sturen aan de controleinstantie door de uitvoeringsinstantie, om aan transactiebericht en gebeurtenisarchieven toe te voegen.

   ![](assets/messagecenter_create_extaccount_007.png)

   De inzameling van gegevens komt of via de dienst van het Web voor die HTTP/HTTPS toegang, of via de Federated Module van de Toegang van Gegevens (FDA) gebruikt.

   De tweede methode wordt geadviseerd als de controleinstantie directe toegang tot het gegevensbestand van de uitvoeringsinstanties heeft. Als niet, kies de de diensttoegang van het Web. De FDA rekening om te specificeren valt met de verbinding aan de gegevensbestanden van de diverse uitvoeringsinstanties die op de controleinstantie worden gecreeerd.

   ![](assets/messagecenter_create_extaccount_008.png)

   Raadpleeg [Toegang tot een externe database](../../platform/using/accessing-an-external-database.md)voor meer informatie over FDA (Federated Data Access).

1. Klik **[!UICONTROL Test the connection]** om ervoor te zorgen de controleinstantie en de uitvoeringsinstantie omhoog worden verbonden.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Elke uitvoeringsinstantie moet aan een id worden gekoppeld. Dit herkenningsteken kan op elke uitvoeringsinstantie of manueel, door de plaatsingstovenaar (verwijs naar het [Identificeren van uitvoeringsinstanties](../../message-center/using/identifying-execution-instances.md)) te gebruiken worden toegeschreven, of automatisch, door de **Initialize verbindingsknoop** van de controleinstantie te klikken.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Uitvoeringsinstantie {#execution-instance}

Opdat de controleinstantie met de uitvoeringsinstantie kan verbinden zonder het moeten een wachtwoord geven, ga eenvoudig het IP adres van de controleinstantie in de de toegangsrechtensectie van het Centrum van het **Bericht** in. Lege wachtwoorden zijn echter standaard niet toegestaan.

Als u een leeg wachtwoord wilt gebruiken, gaat u naar de uitvoeringsinstanties en definieert u een beveiligingszone die is beperkt tot het IP-adres van het informatiesysteem dat de gebeurtenissen levert. Deze veiligheidszone moet lege wachtwoorden toestaan en `<identifier> / <password>` typeverbindingen goedkeuren. Zie [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie.

>[!NOTE]
>
>Wanneer uitvoeringsinstanties door verscheidene controleinstanties worden gebruikt, kunnen de gegevens door omslag en door exploitant worden verdeeld. Voor meer op dit, verwijs naar het [Gebruiken van verscheidene controleinstanties](#using-several-control-instances).

1. Ga naar de operatormap in de uitvoeringsinstantie ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Selecteer de **agent van het Centrum** van het Bericht.

   ![](assets/messagecenter_operator_001.png)

1. Selecteer het **[!UICONTROL Edit]** tabblad, klik **[!UICONTROL Access rights]** en klik op de **[!UICONTROL Edit the access parameters...]** koppeling.

   ![](assets/messagecenter_operator_002.png)

1. In het **[!UICONTROL Access settings]** venster, klik de **[!UICONTROL Add a trusted IP mask]** verbinding en voeg het IP adres van de controleinstantie toe.

   ![](assets/messagecenter_operator_003.png)

## Verschillende besturingsinstanties gebruiken {#using-several-control-instances}

U kunt een uitvoeringscluster met diverse controleinstanties delen. Voor dit type architectuur is de volgende configuratie vereist.

Bijvoorbeeld als uw bedrijf twee merken beheert, elk met zijn eigen controleinstantie: **Control 1** en **Control 2**. Er worden ook twee uitvoeringsinstanties gebruikt. U moet een verschillende exploitant van het Centrum van het Bericht voor elke controleinstantie ingaan: een **mc1** operator voor de **Control 1** instantie en een **mc2** operator voor de **Control 2** instantie.

Maak in de boomstructuur van alle uitvoeringsinstanties één map per operator (**Map 1** en **Map 2**) en beperk de gegevenstoegang van elke operator tot de bijbehorende map.

### Configureren van besturingsinstanties {#configuring-control-instances}

1. In **Controle 1** controlegeval, creeer één externe rekening per uitvoeringsinstantie, en ga de **mc1** exploitant in elke externe rekening in. De **mc1** exploitant zal dan op alle uitvoeringsinstanties (verwijs naar het [Vormen uitvoeringsinstanties](#configuring-execution-instances)) worden gecreeerd.

   ![](assets/messagecenter_multi_control_1.png)

1. In **Controle 2** controle instantie, creeer één externe rekening per uitvoeringsinstantie, en ga de **mc2** exploitant in elke externe rekening in. De **mc2** exploitant zal dan op alle uitvoeringsinstanties worden gecreeerd (verwijs naar het [Vormen van uitvoeringsinstanties](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Voor meer bij het vormen van een controleinstantie, verwijs naar de instantie [van de](#control-instance)Controle.

### Uitvoeringsinstanties configureren {#configuring-execution-instances}

Om verscheidene controleinstanties te gebruiken, moet deze configuratie op ALLE uitvoeringsinstanties worden uitgevoerd.

1. Eén map per operator in het **[!UICONTROL Administration > Production > Message Center]** knooppunt maken: **Map 1** en **Map 2**. Raadpleeg [Platform](../../platform/using/access-management.md#folders-and-views)voor meer informatie over het maken van mappen en weergaven.

   ![](assets/messagecenter_multi_control_3.png)

1. Maak de **operatoren mc1** en **mc2** door de standaardoperator **mc**(Message Center) te dupliceren. Raadpleeg [deze sectie](../../platform/using/access-management.md#operators)voor meer informatie over het maken van operatoren.

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** - en **mc2** -operatoren moeten **[!UICONTROL Message Center execution]** rechten hebben en kunnen geen toegang hebben tot de Adobe Campaign-clientconsole. Een exploitant moet altijd met een veiligheidsstreek verbonden zijn. Zie [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie.

1. Voor elke exploitant, controleer het **[!UICONTROL Restrict to information found in sub-folders of]** vakje, en selecteer de relevante omslag (**Omslag 1** voor de exploitant **mc1** en **Omslag 2** voor de exploitant **mc2** ).

   ![](assets/messagecenter_multi_control_5.png)

1. Geef elke exploitant lees en schrijf toestemmingen voor hun omslag. Klik hiertoe met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties]** . Selecteer vervolgens het **[!UICONTROL Security]** tabblad en voeg de relevante operator (**mc1** voor **map 1** en **mc2** voor **map 2**) toe. Controleer of de **[!UICONTROL Read/Write data]** vakken zijn ingeschakeld.

   ![](assets/messagecenter_multi_control_6.png)

