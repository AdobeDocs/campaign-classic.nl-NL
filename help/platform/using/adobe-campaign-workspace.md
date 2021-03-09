---
solution: Campaign Classic
product: campaign
title: Adobe Campaign-werkruimte
description: Leer de werkruimte Campagne gebruiken en aanpassen
feature: Overzicht
role: Gegevensengineer
level: Begin
translation-type: tm+mt
source-git-commit: c91d9c39d92779ed0366905a944f065c427b1e5a
workflow-type: tm+mt
source-wordcount: '1260'
ht-degree: 3%

---


# Adobe Campaign-werkruimte{#adobe-campaign-workspace}

## De Adobe Campaign-interface verkennen {#about-adobe-campaign-interface}

Zodra u met het gegevensbestand wordt verbonden, zult u tot de homepage van Adobe Campaign toegang hebben, die een dashboard is: het bestaat uit verbindingen en kortere weg die u tot mogelijkheden, afhankelijk van uw installatie en algemene platformconfiguraties kunnen toegang hebben.

Vanuit het centrale gedeelte van de homepage kunt u koppelingen gebruiken om toegang te krijgen tot het online documentatieportaal, -forum en de ondersteuningswebsite van Campagne.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ Campaign-werkruimte ontdekken in video](#video)

>[!NOTE]
>
>De Adobe Campaign-mogelijkheden die voor uw instantie beschikbaar zijn, zijn afhankelijk van de geïnstalleerde modules en invoegtoepassingen. Sommige zijn mogelijk ook niet beschikbaar, afhankelijk van uw machtigingen en specifieke configuraties.
>
>Voordat u een module of invoegtoepassing kunt installeren, moet u de licentieovereenkomst controleren of contact opnemen met de Adobe-accountmanager.

### Console- en webtoegang {#console-and-web-access}

Het Adobe Campaign-platform is toegankelijk via een console of via een internetbrowser.

De toegang van het Web verstrekt een interface die aan de console maar met een verminderde reeks functionaliteiten gelijkaardig is.

Bijvoorbeeld, voor een bepaalde exploitant, zal een campagne met de volgende opties in de console verschijnen:

![](assets/operation_from_console.png)

Terwijl met de toegang van het Web, de opties hoofdzakelijk het bekijken zullen toelaten:

![](assets/operation_from_web.png)

### Talen {#languages}

De taal wordt geselecteerd wanneer u uw Adobe Campaign Classic-exemplaar installeert.

![](assets/language.png)

U kunt kiezen uit vijf verschillende talen:

* Engels (VK)
* Engels (VS)
* Frans
* Duits
* Japans

De taal die u voor uw Adobe Campaign Classic-exemplaar hebt gekozen, kan van invloed zijn op de datum- en tijdnotatie. Raadpleeg deze [sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time) voor meer informatie.

Raadpleeg deze [pagina](../../installation/using/creating-an-instance-and-logging-on.md) voor meer informatie over het maken van een instantie.

>[!CAUTION]
>
>De taal kan na het maken van de instantie niet meer worden gewijzigd.

## Basisbeginselen van navigatie {#navigation-basics}

### Bladeren door pagina&#39;s {#browsing-pages}

De verschillende functies van het platform zijn onderverdeeld in kernmogelijkheden: gebruik de verbindingen die u in de hoogste sectie van de interface ziet om tot hen toegang te hebben.

![](assets/overview_home.png)

De lijst met kernmogelijkheden waartoe u toegang hebt, is afhankelijk van de pakketten en invoegtoepassingen die u hebt geïnstalleerd en van uw toegangsrechten.

Elk vermogen omvat een reeks functionaliteiten die op taak betrekking hebbende behoeften en gebruikscontext worden gebaseerd. Met de koppeling **[!UICONTROL Profiles and targets]** krijgt u bijvoorbeeld toegang tot de lijsten met ontvangers, abonnementsservices, bestaande workflows voor activering en de sneltoetsen voor het maken van deze elementen.

De lijsten zijn beschikbaar via de **[!UICONTROL Lists]** verbinding in de linkersectie van de **[!UICONTROL Profiles and Targets]** interface.

![](assets/recipient_list_overview.png)

### Tabs {#using-tabs} gebruiken

* Wanneer u op een kernfunctie of een koppeling klikt, wordt de huidige pagina vervangen door de relevante pagina. Als u wilt teruggaan naar de vorige pagina, klikt u op de knop **[!UICONTROL Back]** op de werkbalk. Als u wilt terugkeren naar de startpagina, klikt u op de knop **[!UICONTROL Home]**.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* In het geval van een menu of een snelkoppeling naar een scherm (zoals een webtoepassing, programma, levering, rapport, enz.), wordt de bijbehorende pagina weergegeven op een ander tabblad. Op deze manier kunt u van de ene pagina naar de andere bladeren met de tabbladen.

   ![](assets/d_ncs_user_interface_tabs.png)

### Een element maken {#creating-an-element}

In elke sectie met kernmogelijkheden kunt u bladeren door de beschikbare elementen. Hiervoor gebruikt u de sneltoetsen in de sectie **[!UICONTROL Browsing]**. Met de koppeling **[!UICONTROL Other choices]** hebt u toegang tot alle andere pagina&#39;s, ongeacht de omgeving.

U kunt een nieuw element maken (levering, webtoepassing, workflow, enz.) met de sneltoetsen in de sectie **[!UICONTROL Create]** links van het scherm. Gebruik de knop **[!UICONTROL Create]** boven de lijst om nieuwe elementen aan de lijst toe te voegen.

Gebruik bijvoorbeeld op de leveringspagina de knop **[!UICONTROL Create]** om een nieuwe levering te maken.

![](assets/d_ncs_user_interface_tab_add_del.png)

## Adobe Campaign-verkenner {#using-adobe-campaign-explorer} gebruiken

De Adobe Campaign-verkenner is toegankelijk via het werkbalkpictogram. Hiermee hebt u toegang tot de Adobe Campaign, alle Adobe Campaign-mogelijkheden, configuratieschermen en een gedetailleerdere weergave van enkele platformelementen.

De werkruimte **[!UICONTROL Explorer]** is verdeeld in drie zones:

![](assets/s_ncs_user_navigation.png)

**1 - Boom**: U kunt de inhoud van de structuur aanpassen (knooppunten toevoegen, verplaatsen of verwijderen). Deze procedure is alleen bedoeld voor professionele gebruikers. Raadpleeg [deze sectie](#about-navigation-hierarchy).) voor meer informatie.

**2 - Lijst**: u kunt deze lijst filteren, zoekopdrachten uitvoeren, informatie toevoegen of gegevens sorteren. [Meer informatie](adobe-campaign-ui-lists.md).

**3 - Details**: u kunt de details van het geselecteerde element weergeven. Met het pictogram in de rechterbovensectie kunt u deze informatie op volledig scherm weergeven.

### Mappen en boomstructuur{#about-navigation-hierarchy}

De navigatiestructuur werkt als een bestandsbrowser (bijvoorbeeld Windows Verkenner). Mappen kunnen submappen bevatten. Als u een knooppunt selecteert, wordt de weergave weergegeven die overeenkomt met het knooppunt.

De weergegeven weergave is een lijst die is gekoppeld aan een schema en een invoerformulier voor het bewerken van de geselecteerde regel.

![](assets/d_ncs_integration_navigation.png)

Als u een nieuwe map aan de structuur wilt toevoegen, klikt u met de rechtermuisknop op de map in de vertakking waar u een map wilt invoegen en selecteert u **[!UICONTROL Add new folder]**. Selecteer in het snelmenu het type bestand dat u wilt maken.

![](assets/d_ncs_integration_navigation_create.png)

Leer hoe te om de boomstructuur van de navigatie van de Campagne [in deze sectie ](../../configuration/using/configuration.md) te vormen.

Leer hoe u machtigingen voor mappen [instelt in deze sectie](access-management-folders.md).

### Aanbevolen werkwijzen voor mapconfiguratie

* **Ingebouwde mappen gebruiken**

   Door de ingebouwde mappen te gebruiken, kunt u de toepassing eenvoudiger gebruiken, onderhouden en problemen oplossen voor personen die niet bij het project zijn betrokken. U moet geen aangepaste mapstructuren maken voor ontvangers, lijsten, leveringen, enzovoort, maar u moet wel de standaardmappen gebruiken, zoals Beheer, Profielen en doelen, Campagnebeheer.

* **Submappen maken**

   Plaats technische workflows in de standaardmap: Beheer / Productie / Technische workflows en maak submappen per workflowtype.

* **Een naamgevingsconventie instellen**

   U kunt de werkstromen bijvoorbeeld in alfabetische volgorde benoemen, zodat ze in de volgorde van uitvoering gesorteerd worden weergegeven.

   Bijvoorbeeld:

   * A1 - ontvangers van de invoer, begint om 10:00;
   * A2 - Importopdrachten beginnen om 11.00 uur.

* **Sjablonen maken waarmee gebruikers kunnen beginnen**

   Maak leveringssjablonen, workflowsjablonen, campagnemalplaatjes die specifiek zijn voor gebruikers. Deze structuur kan tijd besparen en ervoor zorgen dat de juiste leveringstoewijzing en typologieën voor elke gebruiker worden gebruikt.

### Schermresolutie {#screen-resolution}

Voor optimale navigatie en bruikbaarheid raadt Adobe u aan een minimale schermresolutie van 1600 x 900 pixels te gebruiken.

>[!CAUTION]
>
>Resoluties van minder dan 1600 x 900 pixels worden door Adobe Campaign ondersteund.

Als in de **[!UICONTROL Explorer]** werkruimte sommige delen van de **[!UICONTROL Details]** streek lijken te zijn afgekapt, breidt u deze uit met de pijl boven de zone of klikt u op de **[!UICONTROL Enlarge]** knop.

![](assets/s_ncs_user_resolution.png)

### Bladeren en lijsten aanpassen {#browsing-lists}

Leer hoe u lijsten [in deze sectie](adobe-campaign-ui-lists.md) doorbladert, beheert en aanpast.

## Opmaak en eenheden {#formats-and-units}

### Datum en tijd {#date-and-time}

De taal van uw Adobe Campaign Classic-exemplaar is van invloed op datum- en tijdnotaties.

Taal wordt geselecteerd tijdens de installatie van Campagne en kan achteraf niet worden gewijzigd. U kunt selecteren: Engels (VS), Engels (EN), Frans, Duits of Japans. Raadpleeg [deze pagina](../../installation/using/creating-an-instance-and-logging-on.md) voor meer informatie.

De belangrijkste verschillen tussen het Engels van de VS en het Engels van het Verenigd Koninkrijk zijn:

<table> 
 <thead> 
  <tr> 
   <th> Formaten<br /> </th> 
   <th> Engels (VS)<br /> </th> 
   <th> Engels (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> Week begint op zondag<br /> </td> 
   <td> Week begint op maandag<br /> </td> 
  </tr> 
  <tr> 
   <td> Korte datum<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>ex: 25-09-2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>ex: 09-25-2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Korte datum met tijd<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 25-09-2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Waarden toevoegen in een opsomming {#add-values-in-an-enumeration}

Met de invoervelden in een vervolgkeuzelijst kunt u een opsommingswaarde invoeren die u kunt opslaan en vervolgens als optie kunt aanbieden in de vervolgkeuzelijst. In het veld **[!UICONTROL City]** van het tabblad **[!UICONTROL General]** van een ontvankelijk profiel kunt u bijvoorbeeld Londen invoeren. Wanneer u op Enter drukt om deze waarde te bevestigen, wordt u gevraagd of u deze waarde wilt opslaan voor de opsomming die aan het veld is gekoppeld.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Als u op **[!UICONTROL Yes]** klikt, is deze waarde beschikbaar in de keuzelijst met invoervak van het desbetreffende veld (in dit geval: **[!UICONTROL London]**).

>[!NOTE]
>
>Opsommingen (ook wel &#39;gespecificeerde lijsten&#39; genoemd) worden beheerd door de beheerder via de sectie **[!UICONTROL Administration > Platform > Enumerations]**. Raadpleeg [Opsommingen beheren](../../platform/using/managing-enumerations.md) voor meer informatie.

### Standaardeenheden {#default-units}

In de velden die een duur uitdrukken (bijvoorbeeld de geldigheidsperiode van de bronnen van een levering, de goedkeuringstermijn voor een taak, enz.), kan de waarde worden uitgedrukt in de volgende **eenheden**:

* **[!UICONTROL s]** gedurende seconden,
* **[!UICONTROL mn]** gedurende minuten,
* **[!UICONTROL h]** gedurende uren,
* **[!UICONTROL d]** dagen.

![](assets/enter_unit_sample.png)

## Video over zelfstudie {#video}

In deze video wordt de werkruimte Campaign Classic weergegeven.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
