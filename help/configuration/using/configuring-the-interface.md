---
product: campaign
title: De interface configureren
description: De interface configureren
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# De interface configureren{#configuring-the-interface}

![](../../assets/common.svg)

Voer de volgende stappen uit om de nieuwe tabel met ontvangers in de Adobe Campaign-interface weer te geven en deze te openen:

* Maak een nieuw formulier om de inhoud van de nieuwe tabel met ontvangers te bewerken.
* Voer een nieuw type in in de map van de verkenner-structuur.
* Maak een nieuwe webtoepassing voor toegang tot de aangepaste tabel via de Adobe Campaign-startpagina.

Adobe Campaign gebruikt een globale variabele &quot;Nms_DefaultRcpSchema&quot;aan dialoog met het standaard ontvankelijke gegevensbestand (nms:ontvanger). Deze variabele moet daarom worden gewijzigd.

1. Ga naar de **[!UICONTROL Administration>Platform>Options]** knooppunt van de verkenner.
1. De waarde van de optie **Nms_DefaultRcpSchema** variabele met de naam van het schema dat overeenkomt met de tabel voor externe ontvangers (in dit geval: focus:individu).
1. Wijzigingen opslaan.

## Een nieuw formulier maken {#creating-a-new-form-}

Als u een nieuw formulier maakt, kunt u de gegevens van de externe tabel met ontvangers weergeven en bewerken.

>[!IMPORTANT]
>
>De naam van het formulier moet gelijk zijn aan de naam van het schema waarop het betrekking heeft.

1. Ga naar de **Beheer > Configuratie > Invoerformulieren** knooppunt van de verkenner.
1. Een nieuwe **xtk:form** type **formulier** bestand.
1. Beschrijf alle controle en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Meer informatie over **formulier** tekstbestanden, verwijzing naar [deze pagina](../../configuration/using/identifying-a-form.md).

   In ons huidige voorbeeld wordt **formulier** bestand moet zijn gebaseerd op de **focus:individueel** en hebben daarom de volgende indeling:

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

1. Ga naar de **[!UICONTROL Administration>Configuration>Navigation hierarchies]** knooppunt.
1. Een nieuwe **xtk:navtree** type **navtree** document.
1. Beschrijf alle controle en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Voor meer informatie **navtree** tekstbestanden, verwijzing naar [deze pagina](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   In het huidige voorbeeld wordt **navtree** bestand moet zijn gebaseerd op de **focus:individueel** schema en hebben daarom de volgende vorm:

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
