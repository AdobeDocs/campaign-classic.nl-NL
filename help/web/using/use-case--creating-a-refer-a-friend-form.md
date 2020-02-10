---
title: '"Hoofdlettergebruik: een formulier voor verfijnen als vriend maken"'
seo-title: '"Hoofdlettergebruik: een formulier voor verfijnen als vriend maken"'
description: '"Hoofdlettergebruik: een formulier voor verfijnen als vriend maken"'
seo-description: null
page-status-flag: never-activated
uuid: ad8b9076-c551-420d-bb23-0b3c645ee943
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: bbb1154f-2818-489c-9860-0e860596cbf7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Hoofdlettergebruik: een formulier voor een vriend maken{#use-case-creating-a-refer-a-friend-form}

In dit voorbeeld willen we een wedstrijd aanbieden aan de ontvangers in de database. Het webformulier bevat een sectie waarin u antwoorden kunt invoeren en een andere sectie waarin u een vriend kunt verwijzen door zijn e-mailadres in te voeren.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

De identificatie- en mededingingsblokken worden gecreëerd met behulp van de eerder beschreven processen.

Om het verwijzingsblok te vormen en tot stand te brengen, pas de volgende stappen toe:

1. Maak een vergelijkings-webformulier met vragen en een veld voor het invoeren van contactgegevens van een vriend, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   In het veld **Uw bericht** kunt u een bericht voor de referentie invoeren. De referentie moet ook zijn **achternaam**, **voornaam** en **e-mail** invoeren.

   De informatie die in de velden wordt ingevoerd, wordt opgeslagen in een specifieke tabel die de bezoekerstabel wordt genoemd.

   >[!NOTE]
   >
   >Zolang de ontvanger zijn toestemming niet heeft gegeven, kunt u hen niet met de ontvangers in het gegevensbestand opslaan. Ze worden tijdelijk opgeslagen in de **bezoekerstabel** (**nms:bezoeker**) die is ontworpen voor virale marketingcampagnes. Deze tabel wordt regelmatig gezuiverd door **reinigingswerkzaamheden** .
   >
   >In dit voorbeeld willen we ontvangers aansporen om mee te doen aan de concurrentie die door hun referentie wordt aanbevolen. In dit bericht willen we ze echter ook een abonnement op een van onze informatiediensten aanbieden. Als zij zich abonneren, kunnen zij in het gegevensbestand worden opgeslagen.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   De inhoud van de velden die betrekking hebben op de referentie, wordt gebruikt in het script voor het maken van profielen en in het bericht dat naar hen wordt verzonden.

1. Begin door een manuscript te creëren om de verwijzer aan de refereer te verbinden.

   Het bevat de volgende instructies:

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   De achternaam, voornaam en e-mailadres die u in het paginatekenblok hebt ingevoerd, worden geïdentificeerd als achternaam, voornaam en e-mailadres van de verwijzende persoon. Deze velden worden opnieuw geïnjecteerd in de hoofdtekst van het bericht dat aan de scheidsrechter is gezonden.

   De APP5-waarde komt overeen met de interne naam van het webformulier: met deze informatie kunt u de oorsprong van de scheidsrechter achterhalen, d.w.z. de bezoeker koppelen aan het webformulier waarop ze zijn gemaakt.

1. In het opslagvak kunt u informatie verzamelen en opslaan in de database.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Dan creeer het leveringsmalplaatje verbonden aan de informatiedienst die tijdens stap 1 wordt gecreeerd. Deze wordt geselecteerd op het **[!UICONTROL Choose scenario]** gebied van de informatiedienst.

   De leveringstemplate die wordt gebruikt om het verwijzingsaanbiedingsbericht te maken, bevat de volgende informatie:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Deze sjabloon heeft de volgende kenmerken:

   * Selecteer de bezoekerslijst als doelafbeelding.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * De contactgegevens van de scheidsrechter en de informatie over de verwijzende persoon worden uit de bezoekerslijst gehaald. Het wordt opgenomen gebruikend de verpersoonlijkingsknoop.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Deze sjabloon bevat een koppeling naar het concurrentieformulier en de abonnementskoppeling waarmee de scheidsrechter zich op de nieuwsbrief kan abonneren.

      De abonnementskoppeling wordt ingevoegd via een aanpassingsblok. Standaard kunt u hiermee profielen abonneren op de **nieuwsbrief** . Dit verpersoonlijkingsblok kan worden veranderd om uw behoefte aan te passen, bijvoorbeeld om de ontvanger aan een verschillende dienst in te tekenen.

   * De interne naam (&#39;referrer&#39; hier) zal in het manuscript van de berichtlevering worden gebruikt zoals hieronder getoond.
   >[!NOTE]
   >
   >Raadpleeg [deze pagina](../../delivery/using/about-templates.md) voor meer informatie over leveringssjablonen.

1. Maak het tweede script voor het verzenden van abonnementsberichten.

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. Publiceer het concurrentieformulier en verzend een uitnodiging aan de ontvangers van het oorspronkelijke doel. Wanneer één van hen een vriend uitnodigt, wordt een levering die op het malplaatje van de **Verwijzing wordt gebaseerd** gecreeerd.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   De referentie wordt toegevoegd aan de bezoekersmap in de **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Hun profiel bevat de informatie die door hun referentie is ingevoerd. Deze wordt opgeslagen op basis van de configuraties die zijn ingevoerd in het formulierscript. Als ze besluiten zich te abonneren op de nieuwsbrief, worden ze opgeslagen in de tabel voor ontvangers.

