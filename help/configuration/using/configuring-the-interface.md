---
product: campaign
title: De interface configureren
description: Leer hoe u de interface Campagne configureert
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# De interface configureren{#configuring-the-interface}

Voer de volgende stappen uit om de nieuwe tabel met ontvangers in de Adobe Campaign-interface weer te geven en deze te openen:

* Maak een nieuw formulier om de inhoud van de nieuwe tabel met ontvangers te bewerken.
* Voer een nieuw type in in de map van de verkenner-structuur.
* Maak een nieuwe webtoepassing voor toegang tot de aangepaste tabel via de Adobe Campaign-startpagina.

Adobe Campaign gebruikt een globale variabele &quot;Nms_DefaultRcpSchema&quot;aan dialoog met het standaard ontvankelijke gegevensbestand (nms :recipient). Deze variabele moet daarom worden gewijzigd.

1. Ga naar de **[!UICONTROL Administration>Platform>Options]** -node van de verkenner.
1. Verander de waarde van **Nms_DefaultRcpSchema** variabele met de naam van het schema dat de externe ontvankelijke lijst (in dit geval: cus :individual) aanpast.
1. Wijzigingen opslaan.

## Een nieuw formulier maken {#creating-a-new-form-}

Als u een nieuw formulier maakt, kunt u de gegevens van de externe tabel met ontvangers weergeven en bewerken.

>[!IMPORTANT]
>
>De naam van het formulier moet gelijk zijn aan de naam van het schema waarop het betrekking heeft.

1. Ga naar het **Beleid > Configuratie > de vormen van de Input** knoop van de ontdekkingsreiziger.
1. Creeer een nieuw **xtk:form** type **vorm** dossier.
1. Beschrijf alle controle en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   >[!NOTE]
   >
   >Om meer over **vorm** typedossiers te weten te komen, verwijs naar [&#x200B; deze pagina &#x200B;](../../configuration/using/identifying-a-form.md).

   In ons huidige voorbeeld, moet het **vorm** dossier op het **focus:individual** schema worden gebaseerd en daarom de volgende lay-out hebben:

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

1. Ga naar het knooppunt **[!UICONTROL Administration>Configuration>Navigation hierarchies]** .
1. Creeer een nieuw **xtk:navtree** type **navtree** document.
1. Beschrijf alle controle en gebieden die u afhankelijk van uw lijstmalplaatje nodig hebt.

   In het huidige voorbeeld, moet het **navtree** dossier op het **focus:individual** schema worden gebaseerd en daarom de volgende vorm hebben:

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
