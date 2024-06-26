---
product: campaign
title: "Hoofdlettergebruik: inhoudsbeheer maken"
description: "Hoofdlettergebruik: inhoudsbeheer maken"
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# Hoofdlettergebruik: inhoudsbeheer maken{#use-case-creating-content-management}



Voor het maken van contentbeheer in Adobe Campaign zijn de volgende stappen nodig:

* [Stap 1 - Analyseer de inhoud die moet worden geproduceerd](#step-1---analyzing-the-content-to-be-produced),
* [Stap 2 - creeer het gegevensschema](#step-2---creating-the-data-schema),
* [Stap 3 - Maak het invoerformulier](#step-3---creating-the-input-form),
* [Stap 4 - Een constructiesjabloon maken](#step-4---creating-the-construction-template),
* [Stap 5 - De publicatiesjabloon maken](#step-5---creating-the-publication-template),
* [Stap 6 - Inhoud maken](#step-6---creating-contents).

## Stap 1 - Analyseer de inhoud die moet worden geproduceerd {#step-1---analyzing-the-content-to-be-produced}

Voordat u begint, moet u een nauwkeurige analyse uitvoeren van de inhoud die moet worden geproduceerd: de elementen identificeren die moeten worden weergegeven, de beperkingen bestuderen die eraan zijn gekoppeld, een type definiëren voor elk element, enz. U moet ook onderscheid maken tussen statische elementen en variabele elementen.

Als u bijvoorbeeld een nieuwsbrief wilt maken in HTML met het volgende type inhoud:

![](assets/s_ncs_content_newsletter.png)

Deze nieuwsbrief bevat drie soorten elementen:

1. Variabele elementen waarvan de inhoud door de gebruiker via een invoerformulier wordt ingevoerd of geselecteerd tijdens het maken van de levering.

   ![](assets/s_ncs_content_define_element_types.png)

1. Personaliseringsgebieden die dynamisch op de informatie worden ingegaan die in het gegevensbestand (de voornaam en achternaam van de ontvanger in dit geval) wordt opgeslagen.

   ![](assets/s_ncs_content_define_dynamics.png)

1. Statische elementen, die voor alle nieuwsbrieven hetzelfde zijn.

   ![](assets/s_ncs_content_define_statics.png)

De verschillende elementen van deze nieuwsbrief worden samengesteld op basis van de regels die zijn gedefinieerd in een JavaScript-sjabloon waarin wordt verwezen naar alle elementen die moeten worden ingevoegd en waarin de lay-out ervan wordt beschreven.

Deze elementen worden gemaakt via een speciaal schema dat de volgende elementen voor elke inhoud opgeeft: naam, label, type, grootte en alle andere informatie die relevant is voor de verwerking ervan in Adobe Campaign.

## Stap 2 - creeer het gegevensschema {#step-2---creating-the-data-schema}

Een gegevensschema is een XML-document dat is gekoppeld aan inhoud. Hierin wordt de XML-structuur van de gegevens in deze inhoud beschreven.

>[!NOTE]
>
>Voor meer informatie over het maken en configureren van gegevensschema&#39;s in Adobe Campaign raadpleegt u [deze sectie](../../configuration/using/about-schema-edition.md).
>
>De configuratieelementen die specifiek zijn voor inhoudsbeheer worden nader beschreven in [Gegevensschema&#39;s](data-schemas.md).

Voer de volgende stappen uit om een gegevensschema te maken:

1. Open de Adobe Campaign Explorer en selecteer de **[!UICONTROL Administration > Configuration > Data schemas]** knooppunt.

   Klik op de knop **[!UICONTROL New]** pictogram boven de lijst met gegevensschema&#39;s.

1. Selecteer de **[!UICONTROL Create a schema]** optie voor inhoudsbeheer en klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/s_ncs_content_create_schema.png)

1. Voer de naam en het label van het schema in de desbetreffende velden in. U kunt desgewenst een beschrijving toevoegen en een bepaalde afbeelding koppelen.

   ![](assets/s_ncs_content_param_schema.png)

   Klikken **[!UICONTROL Next]** om te valideren.

1. Voer de inhoud van het schema in het dialoogvenster **[!UICONTROL Edit schema]** venster.

   Gebruik de **[!UICONTROL Insert]** om de schemainhoud te creëren.

   ![](assets/s_ncs_content_param_schema_step2.png)

   Raadpleeg voor meer informatie hierover [Schema&#39;s bewerken](data-schemas.md#editing-schemas).

   Voor elk element waarnaar in de inhoud wordt verwezen, moet u een overeenkomend type selecteren.

   In dit voorbeeld zijn de geïdentificeerde inhoud, de opmaak en het type als volgt:

<table> 
 <thead> 
  <tr> 
   <th> <strong>Inhoud</strong> <br /> </th> 
   <th> <strong>Indeling</strong> <br /> </th> 
   <th> <strong>Type</strong> <br /> </th> 
   <th> <strong>Label</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Titel<br /> </td> 
   <td> Kenmerk<br /> </td> 
   <td> String<br /> </td> 
   <td> Titel<br /> </td> 
  </tr> 
  <tr> 
   <td> Ondertitel<br /> </td> 
   <td> Kenmerk<br /> </td> 
   <td> String<br /> </td> 
   <td> Naam<br /> </td> 
  </tr> 
  <tr> 
   <td> Gebeurtenisdatum<br /> </td> 
   <td> Kenmerk<br /> </td> 
   <td> Datum<br /> </td> 
   <td> Datum<br /> </td> 
  </tr> 
  <tr> 
   <td> Inleiding<br /> </td> 
   <td> Element<br /> </td> 
   <td> HTML<br /> </td> 
   <td> Overzicht<br /> </td> 
  </tr> 
  <tr> 
   <td> Foto van de auteur<br /> </td> 
   <td> Kenmerk<br /> </td> 
   <td> String<br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> Auteur<br /> </td> 
   <td> Element<br /> </td> 
   <td> Memo<br /> </td> 
   <td> Auteur<br /> </td> 
  </tr> 
  <tr> 
   <td> Koptekstlogo (opgeslagen in publieke middelen van Adobe Campaign)<br /> </td> 
   <td> Kenmerk<br /> </td> 
   <td> Koppeling<br /> </td> 
   <td> Afbeelding<br /> </td> 
  </tr> 
 </tbody> 
</table>

Het schema bevat de volgende informatie:

```
<element label="Invitation" name="invitation" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    <attribute label="Title" length="40" name="title" type="string"/>
    <element label="Presentation" name="presentation" type="html"/>
    <attribute label="Date" name="date" type="date"/>
    <attribute label="Name" length="10" name="name" type="string"/>
    <attribute label="URL" name="url" type="string"/>
    <element label="Author" name="author" type="memo"/>
    <element label="Image" name="image" target="xtk:fileRes" type="link"/>
  </element>
```

1. Klikken **[!UICONTROL Save]** om het gegevensschema te maken.

## Stap 3 - Maak het invoerformulier {#step-3---creating-the-input-form}

Met het invoerformulier kunt u een inhoudsinstantie bewerken via een invoerinterface vanuit de Adobe Campaign-clientconsole.

De beschrijving van een formulier is een gestructureerd XML-document waarin de grammatica van het formulierschema &quot;xtk:form&quot; wordt gevolgd.

>[!NOTE]
>
>Raadpleeg voor meer informatie over het maken en configureren van formulieren in Adobe Campaign [deze sectie](../../configuration/using/identifying-a-form.md).
>
>De configuratieelementen die specifiek zijn voor inhoudsbeheer worden nader beschreven in [Invoerformulieren](input-forms.md).

Voer de volgende stappen uit om een invoerformulier te maken voor inhoudsbeheer:

1. Open de Adobe Campaign Explorer en selecteer de **[!UICONTROL Administration > Configuration > Input forms]** knooppunt.

   Klik op de knop **[!UICONTROL New]** pictogram boven de lijst met formulieren.

1. Voer de naam in van het formulier en het label dat aan het formulier is gekoppeld, en selecteer vervolgens de optie **[!UICONTROL Content management]** type.

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >Als u wilt dat beide elementen automatisch overeenkomen, kunt u het beste dezelfde naam gebruiken als voor het gekoppelde gegevensschema. Gebruik de **[!UICONTROL Insert]** boven de invoerzone om velden toe te voegen van het schema dat is gekoppeld aan het formulier.

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. Geef in het middelste gedeelte van de editor de velden op die u in het invoerformulier wilt weergeven.

   In dit voorbeeld hebben we het volgende type informatie:

   ```
    <input xpath="@title"/>
     <input xpath="@date"/>
     <input xpath="presentation"/>
     <input xpath="@name"/>
     <input xpath="@url"/>
     <input xpath="author"/>
     <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
       <sysFilter>
         <condition expr="@isImage = true"/>
       </sysFilter>
     </input>
   ```

   De **[!UICONTROL Preview]** kunt u de weergave van het formulier controleren terwijl u het bewerkt:

   ![](assets/s_ncs_content_param_form_preview.png)

1. Klikken **[!UICONTROL Save]** om het invoerformulier te maken.

## Stap 4 - Een constructiesjabloon maken {#step-4---creating-the-construction-template}

Met de XSLT-taal kunt u een XML-document transformeren in een ander uitvoerdocument. Deze transformatie wordt beschreven in XML in een document genoemd een stijlblad.

In dit voorbeeld willen we een JavaScript-sjabloon gebruiken om de gegevensconstructie en de lay-outmodus in het gegenereerde document te definiëren.

>[!NOTE]
>
>Restricties die zijn gekoppeld aan het maken van documenten (JavaScript- of XSL-sjabloon) worden beschreven in [Opmaak](formatting.md).

Als u een JavaScript-sjabloon wilt gebruiken in Adobe Campaign, voert u de volgende stappen uit:

1. Open de Adobe Campaign Explorer en selecteer de **[!UICONTROL Administration > Configuration > JavaScript Templates]** knooppunt.

   Klik op de knop **[!UICONTROL New]** boven de lijst met sjablonen.

1. Voer een sjabloonnaam in en selecteer het schema dat u voor inhoudsbeheer hebt gemaakt.
1. Importeer de setinhoud die u in het bericht wilt weergeven.

   Voeg de elementen van de variabele toe met inachtneming van de syntaxis die in [JavaScript-sjablonen](formatting.md#javascript-templates).

   Als u de inhoud wilt weergeven die in ons voorbeeld wordt weergegeven, moet de JavaScript-sjabloon de volgende elementen bevatten:

   ```
   <html>
   <% eval(xtk.javascript.load("xac:perso").data); %>
   <head>
     <title>Invitation to an exceptional dedication session</title>
   </head>
   <body link="#0E59AE" vlink="#0E59AE" alink="#0E59AE" style="background-color:white;">
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-top: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td colspan="3">
             <%= generateImgTag(content.@["image-id"]) %>
           </td>
         </tr>
       </table>
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td>
             <table border="0" cellspacing="0" cellpadding="5">
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:2em; padding-bottom:2em;" width="730" align="middle">
                   <b>
                     <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:14px; color:#800080;">
                       <span style="FONT-VARIANT: small-caps"><%= content.@title %> - <%= content.@name %></span>
                     </font>
                   </b>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     Hello <%= perso('recipient.firstName') %> <%= perso('recipient.lastName') %>,
                     <p>
                       <%= content.presentation %>
                     </p>               
                     <center>
                       <b><%= formatDate(content.@date, "%2D %Bl %4Y") %></b> come to our Book Fair and meet our favorite authors and illustrators.<br>
                       <br>
                       <a href="https://www.site.web.com/registration" target="_blank"><b>REGISTER</b></a>
                     </center>
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                    <img style="float:left;margin-right:10px" border="0" src="<%= content.@url %>" width="70" height="70">
                     <b><%= content.author %></b>, will be signing their book between 2
   and 5:30PM.
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>            
                   <tr>
                 <td width="10"> </td>
                 <td width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">                  
                 </td>
                 <td width="10"> </td>
               </tr>           
               <tr>
                 <td width="10"> </td>
                 <td>
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     <center>
                       <p>
                         <a href="https://www.site.web.com/program" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Program</b></span></a>
                          | 
                         <a href="https://www.site.web.com/information" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Useful information</b></span></a>
                          | 
                       <a href="https://www.site.web.com/registration" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Register</b></span></a></p>
                       </center>
                     </font>
                   </td>
                   <td width="10"> </td>
                 </tr>
               </table>
               <br>
             </td>
           </tr>
         </table>
   </body>
   </html>
   ```

   Het roepen van omhoog een functie bij het begin van een malplaatje laat u opstelling een vraag aan verpersoonlijkingsgegevens die uit het gegevensbestand van Adobe Campaign (in dit geval worden genomen: receiving.firstName en receiving.lastName), zodat het kan worden geïnterpreteerd wanneer gebruikt in een levering. Raadpleeg voor meer informatie hierover [Een JavaScript-sjabloon opnemen](formatting.md#including-a-javascript-template).

   In dit voorbeeld bevat de functie de volgende code:

   ```
   function perso(strPerso)
   {
     var strStart = '<' + '%' + '=';
     var strEnd = '%' + '>';
     return strStart + strPerso + strEnd;
   }
     function bloc(strPerso)
   {
     var strStart = '<' + '%' + '@ include view="';
     var strEnd = '" %' + '>';
     return strStart + strPerso + strEnd;
   }
   ```

   De JavaScript-sjabloon is alleen geldig als deze functie vooraf is gemaakt op basis van het **[!UICONTROL JavaScript codes]** knooppunt in de boomstructuur, zoals hieronder:

   ![](assets/contentmgt_jscode_perso_sample.png)

## Stap 5 - De publicatiesjabloon maken {#step-5---creating-the-publication-template}

De volgende stap bestaat uit het maken van een publicatiesjabloon voor inhoud om het schema, het formulier en de constructiesjabloon voor inhoud te koppelen. Deze publicatiesjabloon kan verschillende uitvoerindelingen hebben.

>[!NOTE]
>
>Raadpleeg voor meer informatie over publicatiesjablonen voor inhoud [Publicatiesjablonen](publication-templates.md).

In dit voorbeeld zijn de stappen als volgt:

1. Een nieuwe publicatiesjabloon maken via het dialoogvenster **[!UICONTROL Administration > Configuration > Publication templates]** knooppunt.
1. Voer een naam en een label in en selecteer het schema en het formulier dat u wilt gebruiken.
1. Voer vervolgens de naam van de sjabloon in en kies de renderingmodus die u wilt toepassen. Hier hebben we een **[!UICONTROL JavaScript]** type rendering op basis van de hierboven gemaakte sjabloon.

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >De **[!UICONTROL DOM interface]** Deze optie is standaard ingeschakeld. Dit betekent dat dit document niet toegankelijk is als u de syntaxis E4X gebruikt. De DOM-interface moet worden gebruikt wanneer deze optie is ingeschakeld. Dit is de aanbevolen syntaxis.
   >
   >U kunt nog steeds de syntaxis E4X gebruiken. Als dat het geval is, schakelt u deze optie uit.

   Gebruik de **[!UICONTROL Add]** om andere transformatiesjablonen te maken.

1. Klikken **[!UICONTROL Save]** om de publicatiesjabloon te maken.

## Stap 6 - Inhoud maken {#step-6---creating-contents}

U kunt nu inhoud maken op basis van deze publicatiesjabloon.

>[!NOTE]
>
>Raadpleeg voor meer informatie over het maken van inhoud [Een inhoudssjabloon gebruiken](using-a-content-template.md).

### Inhoud maken in de wizard voor levering {#creating-content-in-the-delivery-wizard}

Voer de volgende stappen uit om inhoud rechtstreeks in de leveringen te maken:

1. Begin door de publicatiesjabloon via **[!UICONTROL Advanced]** tabblad van de leveringseigenschappen.

   ![](assets/s_ncs_content_in_delivery.png)

   Er wordt een extra tabblad toegevoegd aan de wizard voor levering om de inhoud te definiëren via het inhoudsbeheerformulier.

1. Voer de variabele gegevens van uw nieuwsbrief in.

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. Klik op de knop **[!UICONTROL HTML preview]** om de rendering weer te geven. U moet een ontvanger selecteren om verpersoonlijking te testen.

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
