---
product: campaign
title: Een server voor midsourcing installeren in Campagne
description: In deze sectie worden de installatie en configuratie van een medio-sourcingserver in Campagne beschreven
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# Midsourcingserver{#mid-sourcing-server}



Deze sectie detailleert de installatie en de configuratie van een midsourcingserver, evenals de plaatsing van een instantie die derden toelaat om berichten in te sturen **midsourcing** in.

De &quot;mid-sourcing&quot;-architectuur wordt gepresenteerd in [Implementatie van midsourcing](../../installation/using/mid-sourcing-deployment.md).

Voor de installatie van een server voor midsourcing wordt hetzelfde proces gevolgd als voor de installatie van een server op de normale manier (zie de standaardconfiguratie). Het is een onafhankelijke instantie met zijn eigen gegevensbestand dat kan worden gebruikt om leveringen in werking te stellen. Eenvoudig gezet, bevat het een extra configuratie om verre instanties toe te staan leveringen door het in midsourcingswijze uitvoeren.

>[!CAUTION]
>
>Zodra de medio-sourcingserver is ingesteld en de [synchronisatieworkflows](../../workflow/using/about-technical-workflows.md) die voor het eerst zijn gestart, moet u de interne naam van de externe accounts van de midsourcing niet bijwerken.

## Stappen voor het installeren en configureren van een instantie {#steps-for-installing-and-configuring-an-instance}

### Vereisten voor het installeren en configureren van een instantie {#prerequisites-for-installing-and-configuring-an-instance}

* JDK op de toepassingsserver.
* Toegang tot een databaseserver op de toepassingsserver.
* Firewall geconfigureerd voor het openen van HTTP- (80) of HTTPS-poorten (443) naar de server voor midsourcing.

In de volgende procedure wordt een configuratie beschreven met één server voor midsourcing. Het is ook mogelijk meerdere servers te gebruiken. Het is ook mogelijk om bepaalde berichten (zoals workflowmeldingen) vanuit een interne configuratie te verzenden.

### De toepassingsserver installeren en configureren voor implementatie van midsourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

De installatieprocedure is identiek aan die van standalone instantie. Zie [Installeren en configureren (één computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

U moet echter het volgende toepassen:

* In stap **5**, moet u de **mta** (levering) en **inMail** (stuiterende berichten) modules. De **wfserver** (workflow) moet echter geactiveerd blijven.

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

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#enabling-processes) voor meer informatie.

* Stappen **6**, **9** en **10** zijn niet nodig.
* Tijdens stappen **12** en **13**, moet u op de haven 8080 in verbindings URL wijzen (aangezien de console direct met Tomcat, niet via de server van het Web communiceert). De URL wordt `http://console.campaign.net:8080`. Tijdens stap **13**, selecteert u de **[!UICONTROL Issue towards Mid-sourcing]** te installeren.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Het standaardverpletteren van technische leveringen wordt automatisch vervangen met e-mailverpletteren via Midden-sourcing.

### De server voor midsourcing installeren en configureren {#installing-and-configuring-the-mid-sourcing-server}

Van de cliëntconsole, bepaal de plaats van **E-mailroutering via midsourcing** mid-sourcingrekening (in de **/Administratie/externe rekeningen/** map). Vul de **URL van server**, **account**, **password** en **URL van pagina spiegelen** instellingen met de informatie die wordt verschaft door de serverprovider die als host fungeert voor de server voor midsourcing. Test de verbinding.

>[!NOTE]
>
>De **mid-sourcingEmitter** optie maakt twee **Midden-sourcing** workflows. Het is een proces dat door gebrek om de 1 uur en 20 minuten loopt en leveringsinformatie over de midsourcingserver verzamelt.

## Een server voor midsourcing implementeren {#deploying-a-mid-sourcing-server}

1. De toepassingsserver installeren:

   >[!CAUTION]
   >
   >Als u de server voor midsourcing installeert en extra Adobe Campaign-modules wilt installeren, raden wij u aan de module Aflevering te gebruiken en niet de module Campagne.

   Volg dezelfde procedure als voor de standaardplaatsing, die slechts selecteert **[!UICONTROL Mid-sourcing platform]** optie.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuratie voor ontvangst in de modus Midden-sourcing

   Stel het wachtwoord voor de verzendaccount in: In de **/Mid-sourcing/Access Management/Operators/** map, de **midden** operator wordt door de externe instantie gebruikt voor inzendingen in de midsourcingmodus. U moet een wachtwoord instellen voor deze operator en dit aan de beheerder van het verzendingsexemplaar geven.

   De **Middelsourcingsplatform** worden de standaardmappen gemaakt voor het opslaan van de verzonden items en de standaardoperator die de verzonden items uitvoert.

## Multiplexing van de server voor midsourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wordt alleen ondersteund voor omgevingen op locatie.

Het is mogelijk dat een mid-sourcing-instantie wordt gedeeld door meerdere verzendende instanties. Elk van deze instanties moet met een exploitant in het midsourcingsgegevensbestand worden geassocieerd. Een tweede account maken op de server voor midsourcing:

1. Een map maken in het dialoogvenster **[!UICONTROL Mid-sourcing > Deliveries]** knooppunt dat wordt gekoppeld aan de standaardaccount voor midsourcing (bijvoorbeeld: prod).
1. Een map maken in het dialoogvenster **[!UICONTROL Mid-sourcing > Deliveries]** knooppunt met dezelfde naam als de account (bijvoorbeeld: accept_test).

   ![](assets/mid_recette_account.png)

1. In **[!UICONTROL Mid-sourcing > Access Management > Operators]**, maak een nieuwe account.

   ![](assets/mid_recette_user_create.png)

1. In de **[!UICONTROL Access rights]** -tab, geeft deze operator de rechten van de **Tussentijdse inzendingen** groep. Dit toegangsrecht is beschikbaar in **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selecteer **[!UICONTROL Restrict to data in the sub-folders of]** en selecteert u de map met leveringen om deze operator te beperken tot de map met leveringen via de tussenliggende bron.

   ![](assets/mid_recette_user_restrictions.png)

1. Start de module Web opnieuw met de volgende opdracht: **nlserver start web opnieuw**.

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
1. In de **[!UICONTROL Frontal servers]** voert u de parameters van de trackingserververbinding in.

   Als u een instantie tracking wilt maken, voert u de URL van de tracingserver, het wachtwoord voor de interne account van de tracingserver en de naam van de instantie, het wachtwoord en de bijbehorende DNS-maskers in.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Wanneer u de verbindingsparameters hebt ingevoerd, klikt u op **[!UICONTROL Confirm the configuration]**.
1. Geef zo nodig de locatie op waar de afbeeldingen in de leveringen moeten worden opgeslagen. Selecteer hiertoe een van de publicatiemodi in de vervolgkeuzelijst.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Als u **[!UICONTROL Tracking server(s)]** worden de afbeeldingen gekopieerd op de server voor midsourcing.

**Het klantplatform configureren**

1. Ga naar de externe mid-sourcing verpletterende rekening.
1. In de **[!UICONTROL Mid-Sourcing]** , geeft u de parameters voor de serververbinding voor midsourcing op.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bevestig uw configuratie door te klikken **[!UICONTROL Test the connection]**.
1. Declareer de volgende instantie waarnaar wordt verwezen op de mid-sourcing server:

   Klik op de koppeling **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Geef de naam van de instantie tracking op en bevestig vervolgens de verbinding met de tracingserver.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Als de levering van berichten door verscheidene midsourcingservers moet worden beheerd, selecteer de optie **[!UICONTROL Routing with alternating mid-sourcing accounts]** en geeft u de verschillende servers op.

![](assets/s_ncs_install_midsourcing_tracking04.png)
