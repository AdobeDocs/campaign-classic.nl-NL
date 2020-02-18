---
title: De interface configureren
seo-title: De interface configureren
description: De interface configureren
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# De interface configureren{#configuring-the-interface}

Voer de volgende stappen uit om de nieuwe tabel met ontvangers in de Adobe Campagne weer te geven en een dialoogvenster te openen:

* Maak een nieuw formulier om de inhoud van de nieuwe tabel met ontvangers te bewerken.
* Voer een nieuw type in in de map van de verkenner-structuur.
* Maak een nieuwe webtoepassing voor toegang tot de aangepaste tabel via de startpagina van Adobe Campagne.

Adobe Campagne gebruikt een globale variabele &quot;Nms_DefaultRcpSchema&quot;aan dialoog met het gebrek ontvankelijke gegevensbestand (nms:ontvanger). Deze variabele moet daarom worden gewijzigd.

1. Ga naar het **[!UICONTROL Administration>Platform>Options]** knooppunt van de verkenner.
1. Wijzig de waarde van de **variabele Nms_DefaultRcpSchema** met de naam van het schema dat overeenkomt met de externe tabel voor ontvangers (in dit geval: focus:individu).
1. Wijzigingen opslaan.

## Een nieuw formulier maken {#creating-a-new-form-}

Als u een nieuw formulier maakt, kunt u de gegevens van de externe tabel met ontvangers weergeven en bewerken.

>[!IMPORTANT]
>
>De naam van het formulier moet gelijk zijn aan de naam van het schema waarop het betrekking heeft.

1. Ga naar het knooppunt **Beheer > Configuratie > Invoerformulieren** van de verkenner.
1. Maak een nieuw **xtk:formuliertype** - **formulierbestand** .
1. Beschrijf alle controles en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Meer informatie over **formuliertypebestanden** vindt u op [deze pagina](../../configuration/using/identifying-a-form.md).

   In ons huidige voorbeeld moet het **formulierbestand** zijn gebaseerd op het **schema focus:individual** en daarom de volgende indeling hebben:

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

1. Ga naar het **[!UICONTROL Administration>Configuration>Navigation hierarchies]** knooppunt.
1. Maak een nieuw **xtk:navtree** - **document van het type navtree** .
1. Beschrijf alle controles en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Raadpleeg **deze pagina** voor meer informatie over bestanden van het type navtree [](../../configuration/using/about-navigation-hierarchy.md).

   In het huidige voorbeeld moet het **navigatiestructuurbestand** zijn gebaseerd op het schema **focus:individual** en moet het daarom de volgende vorm hebben:

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

