---
title: Doeltoewijzing
seo-title: Doeltoewijzing
description: Doeltoewijzing
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8b3ab02d1fd90c3f14314508a8fa7d99df82436c

---


# Doeltoewijzing{#target-mapping}

In twee gevallen is het noodzakelijk om doeltoewijzingen te maken:

* als u een andere ontvankelijke lijst dan gebruikt die door de Campagne van Adobe wordt verstrekt,
* als u een het filtreren afmeting vormt die van de standaard gericht afmeting op het scherm van de doelafbeelding verschillend is.

De tovenaar van de verwezenlijking van de doelafbeelding zal u helpen alle schema&#39;s tot stand brengen die worden vereist om uw douanetabel te gebruiken.

## Schema&#39;s maken en configureren die zijn gekoppeld aan de aangepaste tabel {#creating-and-configuring-schemas-linked-to-the-custom-table}

Voordat u een doeltoewijzing maakt, zijn verschillende configuraties nodig om Adobe Campagne te laten werken met een nieuw gegevensschema voor ontvangers.

Hiervoor voert u de volgende stappen uit:

1. Maak een nieuw gegevensschema waarin de velden van de aangepaste tabel die u wilt gebruiken, zijn geïntegreerd.

   Zie [Schema reference (xtk:srcSchema)](../../configuration/using/about-schema-reference.md)voor meer informatie.

   In ons voorbeeld, zullen wij een klantenschema, een zeer eenvoudige lijst tot stand brengen die de volgende gebieden bevat: ID, voornaam, achternaam, e-mailadres, mobiele-telefoonnummer. Het doel is om e-mail- of SMS-berichten te kunnen verzenden naar de personen die in deze tabel zijn opgeslagen.

   Voorbeeldschema (cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Declareer uw schema als externe mening gebruikend het = &quot;ware&quot;attribuut. Raadpleeg [het weergavekenmerk](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Gebruik de volgende structuur als u een direct-mailadres wilt toevoegen:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Klik op het **[!UICONTROL Administration > Campaign management > Target mappings]** knooppunt.
1. Klik op de knop **Nieuw** om de wizard Doeltoewijzing maken te openen.
1. Voer het veld **Label** in en selecteer het schema dat u zojuist hebt gemaakt in het veld **Doeldimensie** .

   ![](assets/mapping_diffusion_wizard_1.png)

1. Selecteer in het venster Adresformulieren **** bewerken de velden van het schema die overeenkomen met de verschillende bezorgadressen. Hier kunnen we de velden **@email** en **@mobile** in kaart brengen.

   ![](assets/mapping_diffusion_wizard_2.png)

1. In het volgende venster van de **Opslag** , ga het **Achtervoegsel van het gebied van uitbreidingsschema** in om de nieuwe schema&#39;s van de uit-van-de-doosschema&#39;s te onderscheiden die door de Campagne van Adobe worden verstrekt.

   Klik **[!UICONTROL Define new additional fields]** om de dimensie te selecteren u in uw levering wilt richten.

   Standaard wordt uitsluitingsbeheer opgeslagen in dezelfde tabellen als berichten. Schakel het selectievakje **Een opslagschema genereren voor bijhouden** in als u opslag wilt configureren voor het bijhouden van de koppeling naar de doeltoewijzing.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!CAUTION]
   >
   >De Campagne van Adobe steunt veelvoudige ontvankelijke schema&#39;s, die als richtingsschema&#39;s worden bekend, verbonden aan de zelfde brede en/of trackinglogschema&#39;s. Dit kan anders leiden tot anomalieën in de afstemming van gegevens achteraf. Raadpleeg de pagina [Aanbeveling en beperkingen](../../configuration/using/about-custom-recipient-table.md) voor meer informatie hierover.

1. Selecteer in het venster **Extensies** de optionele schema&#39;s die u wilt genereren (de lijst met beschikbare schema&#39;s is afhankelijk van de modules die op het Adobe Campagneplatform zijn geïnstalleerd).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Klik op de knop **Opslaan** om de wizard te sluiten.

   De tovenaar gebruikt het beginschema om alle andere schema&#39;s tot stand te brengen die worden vereist om de nieuwe doelafbeelding te maken werk.

   ![](assets/mapping_schema_list.png)

## Doeltoewijzing gebruiken {#using-target-mapping}

Er zijn twee manieren om het nieuwe schema als doel van een levering te gebruiken:

* Een of meer leveringssjablonen maken op basis van toewijzing
* Selecteer direct toewijzingen tijdens doelselectie wanneer het creëren van een levering, zoals hieronder getoond:

![](assets/mapping_selection_ciblage.png)

**Verwante onderwerpen**

* [Snel reageren op verzoeken van klanten om toegang te krijgen tot hun gegevens](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)