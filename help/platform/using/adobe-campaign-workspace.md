---
product: campaign
title: Adobe Campaign-werkruimte
description: Leer de werkruimte Campagne gebruiken en aanpassen
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 4%

---

# Adobe Campaign-werkruimte{#adobe-campaign-workspace}

![](../../assets/common.svg)

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

### Console en webtoegang {#console-and-web-access}

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

Raadpleeg dit voor meer informatie over het maken van een instantie [page](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>De taal kan na het maken van de instantie niet meer worden gewijzigd.

## Basisbeginselen van navigatie {#navigation-basics}

### Bladeren door pagina&#39;s {#browsing-pages}

De verschillende functies van het platform zijn onderverdeeld in kernmogelijkheden: gebruik de verbindingen die u in de hoogste sectie van de interface ziet om tot hen toegang te hebben.

![](assets/overview_home.png)

De lijst met kernmogelijkheden waartoe u toegang hebt, is afhankelijk van de pakketten en invoegtoepassingen die u hebt geïnstalleerd en van uw toegangsrechten.

Elk vermogen omvat een reeks functionaliteiten die op taak betrekking hebbende behoeften en gebruikscontext worden gebaseerd. Bijvoorbeeld de **[!UICONTROL Profiles and targets]** via de koppeling kunt u de lijsten met ontvangers, abonnementsservices, bestaande workflows voor activering en de sneltoetsen voor het maken van deze elementen gebruiken.

De lijsten zijn beschikbaar via de **[!UICONTROL Lists]** in het linkergedeelte van het dialoogvenster **[!UICONTROL Profiles and Targets]** interface.

![](assets/recipient_list_overview.png)

### Tabs gebruiken {#using-tabs}

* Wanneer u op een kernfunctie of een koppeling klikt, wordt de huidige pagina vervangen door de relevante pagina. Als u terug wilt gaan naar de vorige pagina, klikt u op de knop **[!UICONTROL Back]** op de werkbalk. Als u wilt terugkeren naar de startpagina, klikt u op de knop **[!UICONTROL Home]** knop.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* In het geval van een menu of een snelkoppeling naar een scherm (zoals een webtoepassing, programma, levering, rapport, enz.), wordt de bijbehorende pagina weergegeven op een ander tabblad. Op deze manier kunt u van de ene pagina naar de andere bladeren met de tabbladen.

   ![](assets/d_ncs_user_interface_tabs.png)

### Een element maken {#creating-an-element}

In elke sectie met kernmogelijkheden kunt u bladeren door de beschikbare elementen. Hiervoor gebruikt u de sneltoetsen in het dialoogvenster **[!UICONTROL Browsing]** sectie. De **[!UICONTROL Other choices]** Met de koppeling hebt u toegang tot alle andere pagina&#39;s, ongeacht de omgeving.

U kunt een nieuw element maken (levering, webtoepassing, workflow, enz.) met de sneltoetsen in het dialoogvenster **[!UICONTROL Create]** aan de linkerkant van het scherm. Gebruik de **[!UICONTROL Create]** boven de lijst om nieuwe elementen aan de lijst toe te voegen.

Gebruik bijvoorbeeld op de leveringspagina de **[!UICONTROL Create]** om een nieuwe levering te maken.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Indelingen en eenheden {#formats-and-units}

### Datum en tijd {#date-and-time}

De taal van uw Adobe Campaign Classic-exemplaar is van invloed op datum- en tijdnotaties.

Taal wordt geselecteerd tijdens de installatie van Campagne en kan achteraf niet worden gewijzigd. U kunt selecteren: Engels (VS), Engels (EN), Frans, Duits of Japans. Raadpleeg [deze pagina](../../installation/using/creating-an-instance-and-logging-on.md) voor meer informatie.

De belangrijkste verschillen tussen het Engels van de VS en het Engels van het Verenigd Koninkrijk zijn:

<table> 
 <thead> 
  <tr> 
   <th> Indelingen<br /> </th> 
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
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 25-09-2018 10:47:25:00</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 09-25-2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Waarden toevoegen aan een opsomming {#add-values-in-an-enumeration}

Met de invoervelden in een vervolgkeuzelijst kunt u een opsommingswaarde invoeren die u kunt opslaan en vervolgens als optie kunt aanbieden in de vervolgkeuzelijst. In het dialoogvenster **[!UICONTROL City]** van het **[!UICONTROL General]** kunt u naar Londen gaan. Wanneer u op Enter drukt om deze waarde te bevestigen, wordt u gevraagd of u deze waarde wilt opslaan voor de opsomming die aan het veld is gekoppeld.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Als u op **[!UICONTROL Yes]** Deze waarde is beschikbaar in de keuzelijst met invoervak van het desbetreffende veld (in dit geval: **[!UICONTROL London]**).

>[!NOTE]
>
>Opsommingen (ook wel &#39;gespecificeerde lijsten&#39; genoemd) worden beheerd door de beheerder via de **[!UICONTROL Administration > Platform > Enumerations]** sectie. Raadpleeg voor meer informatie hierover [Opsommingen beheren](../../platform/using/managing-enumerations.md).

### Standaardeenheden {#default-units}

Op de gebieden die een duur uitdrukken (bv. geldigheidsperiode van de middelen van een levering, goedkeuringstermijn voor een taak, enz.), kan de waarde in het volgende worden uitgedrukt **eenheden**:

* **[!UICONTROL s]** gedurende seconden,
* **[!UICONTROL mn]** gedurende minuten,
* **[!UICONTROL h]** gedurende uren,
* **[!UICONTROL d]** dagen.

![](assets/enter_unit_sample.png)

## Video over zelfstudie {#video}

In deze video wordt de werkruimte Campaign Classic weergegeven.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Er zijn aanvullende Campaign Classic-hoe-kan-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
