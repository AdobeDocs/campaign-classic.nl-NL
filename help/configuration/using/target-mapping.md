---
product: campaign
title: Targettoewijzing
description: Leer hoe u een doeltoewijzing maakt
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 2%

---

# Targettoewijzing{#target-mapping}

![](../../assets/v7-only.svg)

In twee gevallen is het noodzakelijk om doeltoewijzingen te maken:

* als u een andere ontvangertabel gebruikt dan die van Adobe Campaign,
* als u een het filtreren afmeting vormt die van de standaard gericht afmeting op het scherm van de doelafbeelding verschillend is.

De tovenaar van de verwezenlijking van de doelafbeelding zal u helpen alle schema&#39;s tot stand brengen die worden vereist om uw douanetabel te gebruiken.

## Schema&#39;s maken en configureren die zijn gekoppeld aan de aangepaste tabel {#creating-and-configuring-schemas-linked-to-the-custom-table}

Alvorens u een doelafbeelding creeert, zijn verscheidene configuraties noodzakelijk opdat Adobe Campaign met een nieuw ontvankelijk gegevensschema werkt.

Hiervoor voert u de volgende stappen uit:

1. Maak een nieuw gegevensschema waarin de velden van de aangepaste tabel die u wilt gebruiken, zijn geïntegreerd.

   Zie [Schemaverwijzing (xtk:srcSchema)](../../configuration/using/about-schema-reference.md) voor meer informatie.

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

1. Declareer uw schema als externe mening gebruikend het = &quot;ware&quot;attribuut. Zie [Het weergavekenmerk](../../configuration/using/schema-characteristics.md#the-view-attribute).

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

1. Klik op het knooppunt **[!UICONTROL Administration > Campaign management > Target mappings]**.
1. Klik op de knop **Nieuw** om de wizard Doeltoewijzing maken te openen.
1. Voer het veld **Label** in en selecteer het schema dat u zojuist hebt gemaakt in het veld **Doeldimensie**.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Selecteer in het venster **Adresformulieren bewerken** de velden van het schema die overeenkomen met de verschillende leveringsadressen. Hier, kunnen wij **@email** en **@mobile** gebieden in kaart brengen.

   ![](assets/mapping_diffusion_wizard_2.png)

1. In het volgende **Storage** venster, ga **Achtervoegsel van de uitbreidingsschema&#39;s** gebied in om de nieuwe schema&#39;s van de uit-van-de-doosschema&#39;s te onderscheiden die door Adobe Campaign worden verstrekt.

   Klik **[!UICONTROL Define new additional fields]** om de dimensie te selecteren u in uw levering wilt richten.

   Standaard wordt uitsluitingsbeheer opgeslagen in dezelfde tabellen als berichten. Controleer **Genereer een opslagschema voor het volgen** doos als u opslag voor het volgen verbonden aan uw doelafbeelding wilt vormen.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign steunt geen veelvoudige ontvankelijke schema&#39;s, weet als het richten van schema&#39;s, verbonden aan de zelfde brede en/of trackinglogschema&#39;s. Dit kan anders leiden tot anomalieën in de afstemming van gegevens achteraf. Raadpleeg de pagina [Aanbeveling en beperkingen](../../configuration/using/about-custom-recipient-table.md) voor meer informatie hierover.

1. Selecteer in het venster **Extensies** de optionele schema&#39;s die u wilt genereren (de lijst met beschikbare schema&#39;s is afhankelijk van de modules die op het Adobe Campaign-platform zijn geïnstalleerd).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Klik op de knop **Opslaan** om de wizard te sluiten.

   De tovenaar gebruikt het beginschema om alle andere schema&#39;s tot stand te brengen die worden vereist om de nieuwe doelafbeelding te maken werk.

   ![](assets/mapping_schema_list.png)

## Doeltoewijzing gebruiken {#using-target-mapping}

Er zijn twee manieren om het nieuwe schema als doel van een levering te gebruiken:

* Een of meer leveringssjablonen maken op basis van toewijzing
* Selecteer direct toewijzingen tijdens doelselectie wanneer het creëren van een levering, zoals hieronder getoond:

![](assets/mapping_selection_ciblage.png)

**Verwant onderwerp**

* [Snel reageren op verzoeken van klanten om toegang te krijgen tot hun gegevens](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)
