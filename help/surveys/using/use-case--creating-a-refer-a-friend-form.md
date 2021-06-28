---
product: campaign
title: Een enquête voor een vriend maken
description: Meer informatie over het maken van een formulier voor een vriend
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Gebruiksscenario: een referralformulier maken{#use-case-creating-a-refer-a-friend-form}

In dit voorbeeld willen we een wedstrijd aanbieden aan de ontvangers in de database. Het webformulier bevat een sectie waarin u antwoorden kunt invoeren en een andere sectie waarin u een vriend kunt verwijzen door zijn e-mailadres in te voeren.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

De identificatie- en mededingingsblokken worden gecreëerd met behulp van de eerder beschreven processen.

Om het verwijzingsblok te vormen en tot stand te brengen, pas de volgende stappen toe:

1. Maak een vergelijkings-webformulier met vragen en een veld voor het invoeren van contactgegevens van een vriend, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Met het veld **Uw bericht** kunt u een bericht voor de referentie invoeren. De referentie moet ook zijn **Achternaam**, **Voornaam** en **E-mail** invoeren.

   De informatie die in de velden wordt ingevoerd, wordt opgeslagen in een specifieke tabel die de bezoekerstabel wordt genoemd.

   >[!NOTE]
   >
   >Zolang de ontvanger zijn toestemming niet heeft gegeven, kunt u hen niet met de ontvangers in het gegevensbestand opslaan. Ze worden tijdelijk opgeslagen in de tabel **bezoeker** (**nms:bezoeker**) die is ontworpen voor virale marketingcampagnes. Deze tabel wordt regelmatig gewist dankzij **reinigingsbewerkingen**.
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

1. Dan creeer het leveringsmalplaatje verbonden aan de informatiedienst die tijdens stap 1 wordt gecreeerd. Deze wordt geselecteerd in het veld **[!UICONTROL Choose scenario]** van de informatieservice.

   De leveringstemplate die wordt gebruikt om het verwijzingsaanbiedingsbericht te maken, bevat de volgende informatie:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Deze sjabloon heeft de volgende kenmerken:

   * Selecteer de bezoekerslijst als doelafbeelding.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * De contactgegevens van de scheidsrechter en de informatie over de verwijzende persoon worden uit de bezoekerslijst gehaald. Het wordt opgenomen gebruikend de verpersoonlijkingsknoop.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Deze sjabloon bevat een koppeling naar het concurrentieformulier en de abonnementskoppeling waarmee de scheidsrechter zich op de nieuwsbrief kan abonneren.

      De abonnementskoppeling wordt ingevoegd via een aanpassingsblok. Door gebrek, laat het u profielen aan de **nieuwsbrief** dienst intekenen. Dit verpersoonlijkingsblok kan worden veranderd om uw behoefte aan te passen, bijvoorbeeld om de ontvanger aan een verschillende dienst in te tekenen.

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

1. Publiceer het concurrentieformulier en verzend een uitnodiging aan de ontvangers van het oorspronkelijke doel. Wanneer één van hen een vriend uitnodigt, wordt een levering gebaseerd op **Referral aanbieding** malplaatje gecreeerd.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   De referentie wordt toegevoegd aan de bezoekersmap in **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Hun profiel bevat de informatie die door hun referentie is ingevoerd. Deze wordt opgeslagen op basis van de configuraties die zijn ingevoerd in het formulierscript. Als ze besluiten zich te abonneren op de nieuwsbrief, worden ze opgeslagen in de tabel voor ontvangers.
