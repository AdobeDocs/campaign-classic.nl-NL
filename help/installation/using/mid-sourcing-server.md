---
title: Een server voor midsourcing installeren in Adobe Campaign Classic
description: In deze sectie worden de installatie en configuratie van een server voor midsourcing in Adobe Campaign Classic beschreven.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Server voor midsourcing{#mid-sourcing-server}

In deze sectie worden de installatie en configuratie van een server voor midsourcing beschreven, evenals de implementatie van een instantie die derden in staat stelt berichten te verzenden in de modus **mid-sourcing** .

De &quot;mid-sourcing&quot;-architectuur wordt gepresenteerd in [mid-sourcing-implementatie](../../installation/using/mid-sourcing-deployment.md).

Voor de installatie van een server voor midsourcing wordt hetzelfde proces gevolgd als voor de installatie van een server op de normale manier (zie de standaardconfiguratie). Het is een onafhankelijke instantie met zijn eigen gegevensbestand dat kan worden gebruikt om leveringen in werking te stellen. Eenvoudig gezet, bevat het een extra configuratie om verre instanties toe te staan leveringen door het in midsourcingswijze uitvoeren.

## Stappen voor het installeren en configureren van een instantie {#steps-for-installing-and-configuring-an-instance}

### Vereisten voor het installeren en configureren van een instantie {#prerequisites-for-installing-and-configuring-an-instance}

* JDK op de toepassingsserver.
* Toegang tot een databaseserver op de toepassingsserver.
* Firewall geconfigureerd voor het openen van HTTP- (80) of HTTPS-poorten (443) naar de server voor midsourcing.

In de volgende procedure wordt een configuratie beschreven met één server voor midsourcing. Het is ook mogelijk meerdere servers te gebruiken. Het is ook mogelijk om bepaalde berichten (zoals workflowmeldingen) vanuit een interne configuratie te verzenden.

### De toepassingsserver installeren en configureren voor implementatie van midsourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

De installatieprocedure is identiek aan die van standalone instantie. Zie [Installeren en configureren (enkele computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

U moet echter het volgende toepassen:

* In stap **5**, moet u de **mta** (levering) en **inMail** (stuiterende berichten) modules onbruikbaar maken. De **wfserver** -module (workflow) moet echter geactiveerd blijven.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Raadpleeg [Processen](../../installation/using/campaign-server-configuration.md#enabling-processes)inschakelen voor meer informatie.

* Stappen **6**, **9** en **10** zijn niet nodig.
* Tijdens stappen **12** en **13**, moet u op de haven 8080 in verbindings URL wijzen (aangezien de console direct met Tomcat, niet via de server van het Web communiceert). De URL wordt [http://console.campaign.net:8080](http://console.campaign.net). Tijdens stap **13** selecteert u zowel het **[!UICONTROL Issue towards Mid-sourcing]** pakket als de pakketten die u wilt installeren.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Het standaardverpletteren van technische leveringen wordt automatisch vervangen met e-mailverpletteren via Midden-sourcing.

### De server voor midsourcing installeren en configureren {#installing-and-configuring-the-mid-sourcing-server}

Zoek vanuit de clientconsole de **e-mailroutering met gebruik van de mid-sourcing** -account (in de map **/Administration/External accounts/** ). Vul de **URL van de server**-, **account**-, **wachtwoord** - en URL **-instellingen van de pagina** Mirror met de informatie die is verstrekt door de serverprovider die als host fungeert voor de server voor midsourcing. Test de verbinding.

>[!NOTE]
>
>De optie **mid-sourcingEmitter** creëert twee **mid-sourcing** workflows. Het is een proces dat door gebrek om de 1 uur en 20 minuten loopt en leveringsinformatie over de midsourcingserver verzamelt.

## Een server voor midsourcing implementeren {#deploying-a-mid-sourcing-server}

1. De toepassingsserver installeren:

   >[!CAUTION]
   >
   >Als u de server voor midsourcing installeert en extra Adobe Campagne-modules wilt installeren, raden we u aan de module Aflevering te gebruiken en niet de module Campagne.

   Volg dezelfde procedure als voor de standaardplaatsing, die slechts de **[!UICONTROL Mid-sourcing platform]** optie selecteert.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuratie voor ontvangst in de modus Midden-sourcing

   Stel het wachtwoord voor de verzendaccount in: In de map **/Mid-sourcing/Access Management/Operators/** wordt de operator **mid** door de externe instantie gebruikt voor opmerkingen in de modus Midden-sourcing. U moet een wachtwoord instellen voor deze operator en dit aan de beheerder van het verzendingsexemplaar geven.

   Met de optie **Middelsourcingsplatform** worden de standaardmappen gemaakt voor het opslaan van de verzonden leveringen en de standaardoperator die de verzonden gegevens uitvoert.

## Multiplexing van de server voor midsourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wordt alleen ondersteund voor omgevingen op locatie.

Het is mogelijk dat een mid-sourcing-instantie wordt gedeeld door meerdere verzendende instanties. Elk van deze instanties moet met een exploitant in het midsourcingsgegevensbestand worden geassocieerd. Een tweede account maken op de server voor midsourcing:

1. Maak een map in het **[!UICONTROL Mid-sourcing > Deliveries]** knooppunt die wordt gekoppeld aan de standaardaccount voor midsourcing (bijvoorbeeld: prod).
1. Maak een map in het **[!UICONTROL Mid-sourcing > Deliveries]** knooppunt met dezelfde naam als het account (bijvoorbeeld: accept_test).

   ![](assets/mid_recette_account.png)

1. Maak in **[!UICONTROL Mid-sourcing > Access Management > Operators]** een nieuwe account.

   ![](assets/mid_recette_user_create.png)

1. Geef deze operator op het **[!UICONTROL Access rights]** tabblad de rechten van de **verzendgroep** Midden-sourcing. Dit toegangsrecht is beschikbaar in **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selecteer de **[!UICONTROL Restrict to data in the sub-folders of]** optie en selecteer de leveringsmap om deze operator te beperken tot de map voor leveringen via de midsourcing.

   ![](assets/mid_recette_user_restrictions.png)

1. Start de module Web opnieuw met de volgende opdracht: Start **het web** opnieuw op de server.

U moet de instelling voor de server voor midsourcing wijzigen in het bestand serverConf.xml. De volgende lijn moet aan de &quot;Beheer van affiniteiten met IP adressen&quot;sectie, onder de bestaande lijn worden toegevoegd:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Het kenmerk &#39;@name&#39; moet de volgende regels in acht nemen:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affiniteit_groep&#39;**

&#39;marketing_account_operator_name&#39; heeft betrekking op de interne naam van de mid-sourcingrekening die in het mid-sourcingexemplaar is gedeclareerd.

&#39;affinity_name&#39; heeft betrekking op de willekeurige naam die aan de affiniteit is gegeven. Deze naam moet uniek zijn. Geautoriseerde tekens zijn `[a-z]``[A-Z]``[0-9]`. Het doel is een groep openbare IP adressen te verklaren.

&#39;affinity_group&#39; heeft betrekking op de subaffiniteit die is opgegeven in de doeltoewijzing die in elk van de leveringen wordt gebruikt. Het laatste deel, inclusief de &#39;.&#39; wordt genegeerd als er geen subaffiniteit is. Geautoriseerde tekens zijn `[a-z]``[A-Z]``[0-9]`.

U moet de server stoppen en dan opnieuw beginnen om met de wijziging rekening te houden.

## Tracking configureren op een server voor midsourcing {#configuring-tracking-on-a-mid-sourcing-server}

**De server voor midsourcing configureren**

1. Ga naar &#39;operatoren&#39; en selecteer de operator **[!UICONTROL mid]**.
1. Voer op het **[!UICONTROL Frontal servers]** tabblad de parameters voor de trackingserververbinding in.

   Als u een instantie tracking wilt maken, voert u de URL van de tracingserver, het wachtwoord voor de interne account van de tracingserver en de naam van de instantie, het wachtwoord en de bijbehorende DNS-maskers in.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Klik op de verbindingsparameters **[!UICONTROL Confirm the configuration]**.
1. Geef zo nodig de locatie op waar de afbeeldingen in de leveringen moeten worden opgeslagen. Selecteer hiertoe een van de publicatiemodi in de vervolgkeuzelijst.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Als u de **[!UICONTROL Tracking server(s)]** optie kiest, worden de afbeeldingen gekopieerd op de server voor midsourcing.

**Het klantplatform configureren**

1. Ga naar de externe mid-sourcing verpletterende rekening.
1. Geef op het **[!UICONTROL Mid-Sourcing]** tabblad de parameters voor de serververbinding voor de midsourcing op.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bevestig uw configuratie door te klikken **[!UICONTROL Test the connection]**.
1. Declareer de volgende instantie waarnaar wordt verwezen op de mid-sourcing server:

   Klik op de koppeling **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   Geef de naam van de instantie tracking op en bevestig vervolgens de verbinding met de tracingserver.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Als de levering van berichten door verscheidene midsourcingservers moet worden beheerd, selecteer de optie **[!UICONTROL Routing with alternating mid-sourcing accounts]** en specificeer de verschillende servers.

![](assets/s_ncs_install_midsourcing_tracking04.png)

