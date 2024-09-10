---
product: campaign
title: "Hoofdlettergebruik: inhoudsbeheer maken"
description: "Hoofdlettergebruik: inhoudsbeheer maken"
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# Hoofdlettergebruik: inhoudsbeheer maken{#use-case-creating-content-management}



Voor het maken van contentbeheer in Adobe Campaign zijn de volgende stappen nodig:

* [ Stap 1 - analyseer de te produceren inhoud ](#step-1---analyzing-the-content-to-be-produced),
* [ Stap 2 - creeer het gegevensschema ](#step-2---creating-the-data-schema),
* [ Stap 3 - creeer de inputvorm ](#step-3---creating-the-input-form),
* [ Stap 4 - creeer het bouwmalplaatje ](#step-4---creating-the-construction-template),
* [ Stap 5 - creeer het publicatiemalplaatje ](#step-5---creating-the-publication-template),
* [ Stap 6 - creeer inhoud ](#step-6---creating-contents).

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

De verschillende elementen van deze nieuwsbrief worden samengesteld op basis van de regels die zijn gedefinieerd in een JavaScript-sjabloon, waarin alle elementen worden vermeld die moeten worden ingevoegd en waarin de lay-out ervan wordt beschreven.

Deze elementen worden gemaakt via een speciaal schema dat de volgende elementen voor elke inhoud opgeeft: naam, label, type, grootte en alle andere informatie die relevant is voor de verwerking ervan in Adobe Campaign.

## Stap 2 - creeer het gegevensschema {#step-2---creating-the-data-schema}

Een gegevensschema is een XML-document dat is gekoppeld aan inhoud. Hierin wordt de XML-structuur van de gegevens in deze inhoud beschreven.

>[!NOTE]
>
>Voor meer bij het creëren van en het vormen van gegevensschema&#39;s in Adobe Campaign, gelieve te verwijzen naar [ deze sectie ](../../configuration/using/about-schema-edition.md).
>
>De elementen van de configuratie specifiek voor inhoudsbeheer zijn gedetailleerd in [ schema&#39;s van Gegevens ](data-schemas.md).

Voer de volgende stappen uit om een gegevensschema te maken:

1. Open Adobe Campaign Explorer en selecteer het knooppunt **[!UICONTROL Administration > Configuration > Data schemas]** .

   Klik op het pictogram **[!UICONTROL New]** boven de lijst met gegevensschema&#39;s.

1. Selecteer de optie **[!UICONTROL Create a schema]** voor inhoudsbeheer en klik op **[!UICONTROL Next]** .

   ![](assets/s_ncs_content_create_schema.png)

1. Voer de naam en het label van het schema in de desbetreffende velden in. U kunt desgewenst een beschrijving toevoegen en een bepaalde afbeelding koppelen.

   ![](assets/s_ncs_content_param_schema.png)

   Klik op **[!UICONTROL Next]** om te valideren.

1. Voer de inhoud van het schema in het **[!UICONTROL Edit schema]** -venster in.

   Gebruik de knop **[!UICONTROL Insert]** om de schemainhoud te maken.

   ![](assets/s_ncs_content_param_schema_step2.png)

   Voor meer op dit, verwijs naar [ het Uitgeven schema&#39;s ](data-schemas.md#editing-schemas).

   Voor elk element waarnaar in de inhoud wordt verwezen, moet u een overeenkomend type selecteren.

   In dit voorbeeld zijn de geïdentificeerde inhoud, de opmaak en het type als volgt:

<table> 
 <thead> 
  <tr> 
   <th> <strong> Inhoud </strong> <br /> </th> 
   <th> <strong> Formaat </strong> <br /> </th> 
   <th> <strong> Type </strong> <br /> </th> 
   <th> <strong> Etiket </strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Titel <br /> </td> 
   <td> Kenmerk <br /> </td> 
   <td> String <br /> </td> 
   <td> Titel <br /> </td> 
  </tr> 
  <tr> 
   <td> Subtitel <br /> </td> 
   <td> Kenmerk <br /> </td> 
   <td> String <br /> </td> 
   <td> Naam <br /> </td> 
  </tr> 
  <tr> 
   <td> Gebeurtenisdatum <br /> </td> 
   <td> Kenmerk <br /> </td> 
   <td> Datum <br /> </td> 
   <td> Datum <br /> </td> 
  </tr> 
  <tr> 
   <td> Inleiding alinea <br /> </td> 
   <td> Element <br /> </td> 
   <td> HTML<br /> </td> 
   <td> Overzicht <br /> </td> 
  </tr> 
  <tr> 
   <td> Foto van de auteur <br /> </td> 
   <td> Kenmerk <br /> </td> 
   <td> String <br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> Auteur <br /> </td> 
   <td> Element <br /> </td> 
   <td> Memo <br /> </td> 
   <td> Auteur <br /> </td> 
  </tr> 
  <tr> 
   <td> Het embleem van de kopbal (dat in de openbare middelen van Adobe Campaign wordt opgeslagen) <br /> </td> 
   <td> Kenmerk <br /> </td> 
   <td> Koppeling<br /> </td> 
   <td> Afbeelding <br /> </td> 
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

1. Klik op **[!UICONTROL Save]** om het gegevensschema te maken.

## Stap 3 - Maak het invoerformulier {#step-3---creating-the-input-form}

Met het invoerformulier kunt u een inhoudsinstantie bewerken via een invoerinterface vanuit de Adobe Campaign-clientconsole.

De beschrijving van een formulier is een gestructureerd XML-document waarin de grammatica van het formulierschema &quot;xtk:form&quot; wordt gevolgd.

>[!NOTE]
>
>Voor meer bij het creëren van en het vormen van vormen in Adobe Campaign, verwijs naar [ deze sectie ](../../configuration/using/identifying-a-form.md).
>
>De elementen van de configuratie specifiek voor inhoudsbeheer zijn gedetailleerd in [ vormen van de Input ](input-forms.md).

Voer de volgende stappen uit om een invoerformulier te maken voor inhoudsbeheer:

1. Open Adobe Campaign Explorer en selecteer het knooppunt **[!UICONTROL Administration > Configuration > Input forms]** .

   Klik op het pictogram **[!UICONTROL New]** boven de lijst met formulieren.

1. Voer de naam in van het formulier en het label dat aan het formulier is gekoppeld en selecteer vervolgens het type **[!UICONTROL Content management]** .

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >Als u wilt dat beide elementen automatisch overeenkomen, kunt u het beste dezelfde naam gebruiken als voor het gekoppelde gegevensschema. Gebruik de knop **[!UICONTROL Insert]** boven de invoerzone om velden toe te voegen vanuit het schema dat is gekoppeld aan het formulier.

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

   Op het tabblad **[!UICONTROL Preview]** kunt u de weergave van het formulier controleren terwijl u het bewerkt:

   ![](assets/s_ncs_content_param_form_preview.png)

1. Klik op **[!UICONTROL Save]** om het invoerformulier te maken.

## Stap 4 - Een constructiesjabloon maken {#step-4---creating-the-construction-template}

Met de XSLT-taal kunt u een XML-document transformeren in een ander uitvoerdocument. Deze transformatie wordt beschreven in XML in een document genoemd een stijlblad.

In dit voorbeeld willen we een JavaScript-sjabloon gebruiken om de gegevensconstructie en de lay-outmodus in het gegenereerde document te definiëren.

>[!NOTE]
>
>De beperkingen verbonden aan documentbouw (het malplaatje van JavaScript of van XSL) zijn gedetailleerd in [ Formatterend ](formatting.md).

Voer de volgende stappen uit om een JavaScript-sjabloon te gebruiken in Adobe Campaign:

1. Open Adobe Campaign Explorer en selecteer het knooppunt **[!UICONTROL Administration > Configuration > JavaScript Templates]** .

   Klik op het pictogram **[!UICONTROL New]** boven de lijst met sjablonen.

1. Voer een sjabloonnaam in en selecteer het schema dat u voor inhoudsbeheer hebt gemaakt.
1. Importeer de setinhoud die u in het bericht wilt weergeven.

   Voeg de veranderlijke elementen toe terwijl het respecteren van de syntaxis die in [ wordt gedetailleerd de malplaatjes van JavaScript ](formatting.md#javascript-templates).

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

   Het roepen van omhoog een functie bij het begin van een malplaatje laat u opstelling een vraag aan verpersoonlijkingsgegevens die uit het gegevensbestand van Adobe Campaign (in dit geval worden genomen: receiving.firstName en receiving.lastName), zodat het kan worden geïnterpreteerd wanneer gebruikt in een levering. Voor meer op dit, verwijs naar [ omvat een malplaatje van JavaScript ](formatting.md#including-a-javascript-template).

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

   De JavaScript-sjabloon is alleen geldig als deze functie vooraf wordt gemaakt vanaf het knooppunt **[!UICONTROL JavaScript codes]** in de boomstructuur, zoals hieronder:

   ![](assets/contentmgt_jscode_perso_sample.png)

## Stap 5 - De publicatiesjabloon maken {#step-5---creating-the-publication-template}

De volgende stap bestaat uit het maken van een publicatiesjabloon voor inhoud om het schema, het formulier en de constructiesjabloon voor inhoud te koppelen. Deze publicatiesjabloon kan verschillende uitvoerindelingen hebben.

>[!NOTE]
>
>Voor meer op de malplaatjes van de inhoudspublicatie, verwijs naar [ de malplaatjes van de Publicatie ](publication-templates.md).

In dit voorbeeld zijn de stappen als volgt:

1. Maak een nieuwe publicatiesjabloon via het knooppunt **[!UICONTROL Administration > Configuration > Publication templates]** .
1. Voer een naam en een label in en selecteer het schema en het formulier dat u wilt gebruiken.
1. Voer vervolgens de naam van de sjabloon in en kies de renderingmodus die u wilt toepassen. Hier hebben we een rendering van het type **[!UICONTROL JavaScript]** op basis van de hierboven gemaakte sjabloon.

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >De optie **[!UICONTROL DOM interface]** is standaard ingeschakeld. Dit betekent dat dit document niet toegankelijk is als u de syntaxis E4X gebruikt. De DOM-interface moet worden gebruikt wanneer deze optie is ingeschakeld. Dit is de aanbevolen syntaxis.
   >
   >U kunt nog steeds de syntaxis E4X gebruiken. Als dat het geval is, schakelt u deze optie uit.

   Gebruik de knop **[!UICONTROL Add]** om andere transformatiesjablonen te maken.

1. Klik op **[!UICONTROL Save]** om de publicatiesjabloon te maken.

## Stap 6 - Inhoud maken {#step-6---creating-contents}

U kunt nu inhoud maken op basis van deze publicatiesjabloon.

>[!NOTE]
>
>Voor meer bij het creëren van inhoud, verwijs naar [ Gebruik een inhoudsmalplaatje ](using-a-content-template.md).

### Inhoud maken in de leveringsassistent {#creating-content-in-the-delivery-assistant}

Voer de volgende stappen uit om inhoud rechtstreeks in de leveringen te maken:

1. Begin door via het tabblad **[!UICONTROL Advanced]** van de leveringseigenschappen naar de publicatiesjabloon te verwijzen.

   ![](assets/s_ncs_content_in_delivery.png)

   Een extra lusje wordt toegevoegd aan de leveringsmedewerker om de inhoud via de vorm van het inhoudsbeheer te bepalen.

1. Voer de variabele gegevens van uw nieuwsbrief in.

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. Klik op de tab **[!UICONTROL HTML preview]** om de rendering weer te geven. U moet een ontvanger selecteren om verpersoonlijking te testen.

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
