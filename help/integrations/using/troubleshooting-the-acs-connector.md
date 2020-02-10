---
title: Het oplossen van problemen de Schakelaar ACS
seo-title: Het oplossen van problemen de Schakelaar ACS
description: Het oplossen van problemen de Schakelaar ACS
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Het oplossen van problemen de Schakelaar ACS{#troubleshooting-the-acs-connector}

Afhankelijk van uw implementatie kunt u met meerdere veelvoorkomende problemen worden geconfronteerd.

* **Wat zijn de verschillen UI tussen de Norm van de Campagne en Campagne v7?**

   Campagnestandaard en Campagne v7 werken op een vergelijkbare manier. De meeste concepten zijn hetzelfde, maar in sommige gevallen kan de aanpak enigszins afwijken. Hier een aantal van de concepten die in de context van de Schakelaar ACS zouden kunnen verschillen:

<table> 
 <thead> 
  <tr> 
   <th> Campagne v7<br /> </th> 
   <th> Campagnestandaard<br /> </th> 
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
   <td> campagneworkflows, doelgericht werken<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> bewerkingen<br /> </td> 
   <td> campagnes<br /> </td> 
  </tr> 
  <tr> 
   <td> webtoepassingen<br /> </td> 
   <td> landingspagina's<br /> </td> 
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

* **De ontvangers van mijn instantie Campagne v7 zijn niet gesynchroniseerd of zichtbaar aan de Norm van de Campagne.**

   Dit geval kan om verschillende redenen gebeuren:

   * Ontvangers zijn zojuist gemaakt of bijgewerkt in Campaign v7. De synchronisatie wordt elke 15 minuten gestart. Betekenis dat bijgewerkte of pas gecreëerde ontvangers in de Norm van de Campagne na de volgende synchronisatie zichtbaar zullen zijn.
   * Uw implementatie kan zo zijn ingesteld dat alleen ontvangers uit specifieke mappen worden gesynchroniseerd. Ontvangers uit andere mappen worden niet gesynchroniseerd.
   * De ontvanger kan worden gesynchroniseerd maar niet zichtbaar in de Norm van de Campagne. Controleer de toewijzing van maprechten.

* **Ik vind niet de profielgebieden ik mijn vraag op in de Norm van de Campagne moet baseren.**

   Standaard worden 20 velden uit de nms:tabel ontvanger gesynchroniseerd met Campagnestandaard. Raadpleeg de gedetailleerde lijst met gesynchroniseerde velden. Alle extra velden die u in de campagnestandaard moet ophalen, moeten door uw consultant worden toegewezen en geconfigureerd.

   Om ervoor te zorgen dat het veld dat u wilt gebruiken beschikbaar is, kunt u de definitie van de profielbron controleren **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Bovendien worden alle gegevens in bijlage aan ontvangers en opgeslagen in lijsten met betrekking tot nms:ontvangers niet gesynchroniseerd door gebrek aan de Norm van de Campagne.

   Om verwante gegevens nog te kunnen gebruiken, kunt u uw richten in Campagne v7 uitvoeren en extra gegevens toevoegen zoals die in de het [Synchroniseren sectie van publiek](../../integrations/using/synchronizing-audiences.md) worden verklaard, of u kunt naar uw consultant verwijzen om aanpassingsmogelijkheden te onderzoeken.

* **Ik gebruik een andere profieldimensie dan de standaardnms:ontvanger in Campagne v7, hoe kan ik hen met de Norm van de Campagne synchroniseren?**

   De Standaard van de campagne gebruikt een uniek gericht middel dat **profielen** genoemd wordt. De basisimplementatie van de functie Campagnestandaard verbinden biedt een standaardtoewijzing tussen de ontvangers van Campagne v7 en de standaardprofielen van de Campagne.

   Als u een andere profieldimensie gebruikt in Campagne v7, of als u verscheidene degenen gebruikt, moeten zij allen met de Standaardprofielen van de Campagne worden in kaart gebracht. Raadpleeg uw consultant om aan deze specifieke behoefte tegemoet te komen.

* **Ik wil een lijst met profielen delen met de Standaard van de Campagne door een werkschema maar kan mijn publiek in de Norm** van de Campagne niet vinden.

   Het publiek vindt u in het **[!UICONTROL Audiences]** menu Campagnestandaard. Zij hebben het etiket dat in de activiteit in uw werkschema van de Campagne v7 wordt gespecificeerd. **[!UICONTROL List update]** Ze zijn onderworpen aan de maptoewijzing die tijdens de implementatie is gedefinieerd.

   Het eerste wat u moet controleren is of de workflow zonder fouten is voltooid. Als u een fout op de **[!UICONTROL List update]** activiteit opmerkt, betekent het dat de synchronisatie met de Norm van de Campagne kan ontbroken hebben. Ga naar **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Deze map bevat synchronisatieworkflows die worden geactiveerd door het uitvoeren van de **[!UICONTROL List update]** activiteit.

   Controleer ook of de **[!UICONTROL Share with ACS]** optie is ingecheckt in de **[!UICONTROL List update]** activiteit en of de workflow correct is uitgevoerd.

   Ontvangersprofielen in de lijst moeten voorafgaand aan de workflowuitvoering zijn gesynchroniseerd met Campagnestandaard. Als de lijst eenmaal is gedeeld met de campagnestandaard, worden de ontvangers van de lijst verbonden met de standaardprofielen voor campagnes. Dit houdt in dat ze daar moeten bestaan. Ontvangers in de lijst die niet kunnen worden gecombineerd met profielen in Campagnestandaard, worden genegeerd.

   Als u een lijst deelt die van profielen wordt gemaakt en geen die met de Norm van de Campagne worden gesynchroniseerd, leidt het tot een leeg publiek van de Vraag in de Norm van de Campagne die niet kan worden gebruikt.

* **Ik heb een bericht ontvangen dat me vertelt dat een synchronisatiewerkschema in foutenstaat is. Wat moet ik doen?**

   Controleer de configuratie van de externe account in zowel Campagnestandaard als Campagne v7 door de verbinding te testen:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campagnestandaard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Ik heb geen veiligheidsgroep beschikbaar wanneer het in kaart brengen van omslagen tussen Campagne v7 en de Norm van de Campagne.**

   U moet eerst uw beveiligingsgroepen synchroniseren vanuit **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Deze actie controleert de veiligheidsgroepen beschikbaar in de Norm van de Campagne. Nadat de map is gesynchroniseerd, kunt u de beveiligingsgroepen vinden wanneer u de maptoewijzing configureert.

* **Ik kan een profiel, een publiek of een landingspagina niet bewerken in Campagnestandaard. Wat betekent het?**

   De middelen die van Campagne v7 worden gesynchroniseerd zijn op read-only wijze in de Norm van de Campagne, om gegevensconsistentie te verzekeren. Als u één van deze elementen moet uitgeven, kunt u het in Campagne v7 doen en dan de verandering in de Norm van de Campagne herhalen.

