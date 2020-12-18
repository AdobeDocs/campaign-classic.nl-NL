---
solution: Campaign Classic
product: campaign
title: De interface configureren
description: De interface configureren
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# De interface configureren{#configuring-the-interface}

Voer de volgende stappen uit om de nieuwe tabel met ontvangers in de Adobe Campaign-interface weer te geven en deze te openen:

* Maak een nieuw formulier om de inhoud van de nieuwe tabel met ontvangers te bewerken.
* Voer een nieuw type in in de map van de verkenner-structuur.
* Maak een nieuwe webtoepassing voor toegang tot de aangepaste tabel via de Adobe Campaign-startpagina.

Adobe Campaign gebruikt een globale variabele &quot;Nms_DefaultRcpSchema&quot;aan dialoog met het standaard ontvankelijke gegevensbestand (nms:ontvanger). Deze variabele moet daarom worden gewijzigd.

1. Ga naar de **[!UICONTROL Administration>Platform>Options]** knoop van de ontdekkingsreiziger.
1. Wijzig de waarde van de variabele **Nms_DefaultRcpSchema** met de naam van het schema dat overeenkomt met de externe ontvangende tabel (in dit geval: focus:individu).
1. Wijzigingen opslaan.

## Een nieuw formulier maken {#creating-a-new-form-}

Als u een nieuw formulier maakt, kunt u de gegevens van de externe tabel met ontvangers weergeven en bewerken.

>[!IMPORTANT]
>
>De naam van het formulier moet gelijk zijn aan de naam van het schema waarop het betrekking heeft.

1. Ga naar **Beheer > Configuratie > Invoerformulieren** van de verkenner.
1. Maak een nieuw **xtk:form** type **form** bestand.
1. Beschrijf alle controles en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Als u meer wilt weten over **form**-tekstbestanden, raadpleegt u [deze pagina](../../configuration/using/identifying-a-form.md).

   In ons huidige voorbeeld moet het **form** bestand zijn gebaseerd op het schema **cus:individual** en daarom de volgende indeling hebben:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Sla het ontwerp op.

## Een nieuw type map maken in de navigatiehiërarchie {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Ga naar de **[!UICONTROL Administration>Configuration>Navigation hierarchies]** knoop.
1. Maak een nieuw **xtk:navtree** type **navtree** document.
1. Beschrijf alle controles en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Raadpleeg [deze pagina](../../configuration/using/about-navigation-hierarchy.md) voor meer informatie over **navtree**-tekstbestanden.

   In het huidige voorbeeld moet het **navtree** bestand zijn gebaseerd op het schema **cus:individual** en daarom de volgende vorm hebben:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Sla het ontwerp op.

