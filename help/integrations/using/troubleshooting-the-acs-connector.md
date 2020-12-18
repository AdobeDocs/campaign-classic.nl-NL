---
solution: Campaign Classic
product: campaign
title: Het oplossen van problemen de Schakelaar ACS
description: Het oplossen van problemen de Schakelaar ACS
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---


# Het oplossen van problemen de Schakelaar ACS{#troubleshooting-the-acs-connector}

Afhankelijk van uw implementatie kunt u met meerdere veelvoorkomende problemen worden geconfronteerd.

* **Wat zijn de UI verschillen tussen Campaign Standard en Campaign v7?**

   Campaign Standard en Campagne v7 werken op een vergelijkbare manier. De meeste concepten zijn hetzelfde, maar in sommige gevallen kan de aanpak enigszins afwijken. Hier een aantal van de concepten die in de context van de Schakelaar ACS zouden kunnen verschillen:

<table> 
 <thead> 
  <tr> 
   <th> Campagne v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> ontvangers (of een andere profieldimensie)<br /> </td> 
   <td> profielen<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> publiek<br /> </td> 
  </tr> 
  <tr> 
   <td> campagneworkflows, gericht op workflows<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> bewerkingen<br /> </td> 
   <td> campagnes<br /> </td> 
  </tr> 
  <tr> 
   <td> webtoepassingen<br /> </td> 
   <td> openingspagina's<br /> </td> 
  </tr> 
  <tr> 
   <td> aangepaste tabel- en schema-extensie<br /> </td> 
   <td> aangepaste bron- en bronextensie<br /> </td> 
  </tr> 
  <tr> 
   <td> zaadleden<br /> </td> 
   <td> testprofielen<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **De ontvangers van mijn instantie Campagne v7 zijn niet gesynchroniseerd of zichtbaar aan Campaign Standard.**

   Dit geval kan om verschillende redenen gebeuren:

   * Ontvangers zijn zojuist gemaakt of bijgewerkt in Campaign v7. De synchronisatie wordt elke 15 minuten gestart. Betekenis dat bijgewerkte of pas gecreëerde ontvangers in Campaign Standard na de volgende synchronisatie zichtbaar zullen zijn.
   * Uw implementatie kan zo zijn ingesteld dat alleen ontvangers uit specifieke mappen worden gesynchroniseerd. Ontvangers uit andere mappen worden niet gesynchroniseerd.
   * De ontvanger kan worden gesynchroniseerd maar niet zichtbaar in Campaign Standard. Controleer de toewijzing van maprechten.

* **Ik vind niet de profielgebieden ik mijn vraag op in Campaign Standard moet baseren.**

   Standaard worden 20 velden van de nms:tabel ontvanger gesynchroniseerd met Campaign Standard. Raadpleeg de gedetailleerde lijst met gesynchroniseerde velden. Alle extra velden die u in Campaign Standard wilt ophalen, moeten door uw consultant worden toegewezen en geconfigureerd.

   Om ervoor te zorgen dat het gebied u wilt gebruiken beschikbaar is, kunt u de definitie van het profielmiddel van **[!UICONTROL Administration > Development > Diagnosis > Data schemas]** controleren.

   Bovendien worden alle gegevens die aan ontvangers zijn gekoppeld en zijn opgeslagen in tabellen met betrekking tot nms:ontvangers niet standaard gesynchroniseerd met Campaign Standard.

   Om verwante gegevens nog te kunnen gebruiken, kunt u uw richten in Campagne v7 uitvoeren en extra gegevens toevoegen zoals die in [het synchroniseren van publiek ](../../integrations/using/synchronizing-audiences.md) sectie worden verklaard, of u kunt naar uw consultant verwijzen om aanpassingsmogelijkheden te onderzoeken.

* **Ik gebruik een andere profieldimensie dan de standaardnms:ontvanger in Campagne v7, hoe kan ik hen met Campaign Standard synchroniseren?**

   Campaign Standard gebruikt een unieke doelbron met de naam **profiles**. De basisimplementatie van de functie Campaign Standard Connect biedt een standaardtoewijzing tussen de ontvangers van Campagne v7 en de profielen Campaign Standard.

   Als u een andere profieldimensie gebruikt in Campagne v7, of als u verscheidene degenen gebruikt, moeten zij allen met Campaign Standard profielen in kaart worden gebracht. Raadpleeg uw consultant om aan deze specifieke behoefte tegemoet te komen.

* **Ik wil een lijst van profielen met Campaign Standard door een werkschema delen maar kan mijn publiek niet in Campaign Standard** vinden.

   Soorten publiek vindt u in het menu **[!UICONTROL Audiences]** in Campaign Standard. Zij hebben het etiket dat in **[!UICONTROL List update]** activiteit in uw werkschema van de Campagne v7 wordt gespecificeerd. Ze zijn onderworpen aan de maptoewijzing die tijdens de implementatie is gedefinieerd.

   Het eerste wat u moet controleren is of de workflow zonder fouten is voltooid. Als u een fout op **[!UICONTROL List update]** activiteit opmerkt, betekent het dat de synchronisatie met Campaign Standard kan ontbroken hebben. Als u meer details wilt zien over wat er fout is gegaan, gaat u naar **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Deze map bevat synchronisatieworkflows die worden geactiveerd door de uitvoering van de **[!UICONTROL List update]**-activiteit.

   Zorg er ook voor dat de optie **[!UICONTROL Share with ACS]** is ingeschakeld in de **[!UICONTROL List update]**-activiteit en dat de workflow correct is uitgevoerd.

   Ontvangersprofielen in de lijst moeten vóór de uitvoering van de workflow met Campaign Standard zijn gesynchroniseerd. Wanneer de lijst is gedeeld met Campaign Standard, worden de ontvangers van de lijst verbonden met de profielen Campaign Standard, wat betekent dat ze daar moeten bestaan. Ontvangers in de lijst die niet kunnen worden gecombineerd met profielen in Campaign Standard, worden genegeerd.

   Als u een lijst deelt die van profielen wordt gemaakt en geen met Campaign Standard wordt gesynchroniseerd, leidt het tot een leeg publiek van de Vraag in Campaign Standard dat niet kan worden gebruikt.

* **Ik heb een bericht ontvangen dat me vertelt dat een synchronisatiewerkschema in foutenstaat is. Wat moet ik doen?**

   Controleer de configuratie van de externe account in zowel Campaign Standard als Campagne v7 door de verbinding te testen:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Ik heb geen veiligheidsgroep beschikbaar wanneer het in kaart brengen van omslagen tussen Campagne v7 en Campaign Standard.**

   U moet uw veiligheidsgroepen van **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]** eerst synchroniseren. Deze actie controleert de veiligheidsgroepen beschikbaar in Campaign Standard. Nadat de map is gesynchroniseerd, kunt u de beveiligingsgroepen vinden wanneer u de maptoewijzing configureert.

* **Ik kan een profiel, een publiek of een openingspagina niet bewerken in Campaign Standard. Wat betekent het?**

   De middelen die van Campagne v7 worden gesynchroniseerd zijn op read-only wijze in Campaign Standard, om gegevensconsistentie te verzekeren. Als u één van deze elementen moet uitgeven, kunt u het in Campagne v7 doen en dan de verandering in Campaign Standard herhalen.

