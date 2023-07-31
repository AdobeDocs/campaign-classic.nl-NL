---
product: campaign
title: Gedistribueerde architecturen
description: Gedistribueerde architecturen
feature: Interaction, Offers, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 083be073-aad4-4c81-aff2-77f5ef3e80db
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 1%

---

# Gedistribueerde architecturen{#distributed-architectures}



## Beginsel {#principle}

Om scalability te kunnen steunen en de dienst 24/7 op het binnenkomende kanaal te verlenen, kunt u Interactie met een verdeelde architectuur gebruiken. Dit type architectuur wordt reeds gebruikt met het Centrum van het Bericht en uit verscheidene instanties samengesteld:

* één of meerdere controleinstanties gewijd aan het uitgaande kanaal en die de marketing en de basis van het milieuontwerp bevatten
* één of meerdere uitvoeringsinstanties specifiek voor het binnenkomende kanaal

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>Besturingsinstanties worden toegewezen aan het binnenkomende kanaal en bevatten de onlineversie van de catalogus. Elke uitvoeringsinstantie is onafhankelijk en gewijd aan één contactsegment (bijvoorbeeld, één uitvoeringsinstantie per land). Aanroepen van de engine voor aanbieding moeten rechtstreeks op de uitvoering worden uitgevoerd (één specifieke URL per uitvoeringsinstantie). Aangezien synchronisatie tussen instanties niet automatisch is, moeten de interacties van het zelfde contact door de zelfde instantie worden verzonden.

## Propositiesynchronisatie {#proposition-synchronization}

De synchronisatie van aanbiedingen wordt uitgevoerd via pakketten. Bij uitvoeringsinstanties krijgen alle catalogusobjecten de naam van de externe account vooraf. Dit betekent dat verschillende besturingsinstanties (bijvoorbeeld ontwikkelings- en productieinstanties) op dezelfde uitvoeringsinstantie kunnen worden ondersteund.

>[!IMPORTANT]
>
>We raden u aan korte en expliciete interne namen te gebruiken.

Aanbiedingen worden automatisch geïmplementeerd en vervolgens gepubliceerd op uitvoerings- en besturingsinstanties.

Aanbiedingen die zijn verwijderd in de ontwerpomgeving, worden in alle online exemplaren uitgeschakeld. De verouderde voorstellen en de aanbiedingen worden automatisch geschrapt op alle instanties na de purge periode (die in de plaatsingsmedewerker van elke instantie wordt gespecificeerd) en het glijden periode (die in de de typologieregels van inkomende voorstellen wordt gespecificeerd).

![](assets/interaction_powerbooster_schema2.png)

Er wordt een workflow gemaakt voor elke omgeving en externe account voor propositiesynchronisatie. De synchronisatiefrequentie kan worden aangepast voor elke omgeving en externe account.

## Beperkingen {#limitations}

* Als u de valfunctie van een anonieme omgeving aan een geïdentificeerd milieu gebruikt, moeten deze twee milieu&#39;s op de zelfde uitvoeringsinstantie zijn.
* De synchronisatie tussen verschillende uitvoeringsinstanties wordt niet in real-time uitgevoerd. Interacties van dezelfde contactpersoon moeten naar dezelfde instantie worden verzonden. De controleinstantie moet aan het uitgaande kanaal (geen echte tijd) worden gewijd.
* De marketingdatabase wordt niet automatisch gesynchroniseerd. De marketinggegevens die in de wegingsregels en de subsidiabiliteitsregels worden gebruikt, moeten in geval van uitvoering worden gedupliceerd. Dit proces komt niet als standaard, u moet het ontwikkelen tijdens de integratieperiode.
* De synchronisatie van voorstellen wordt uitsluitend uitgevoerd door een FDA-verbinding.
* Als u Interaction en het Centrum van het Bericht op de zelfde instantie gebruikt, zal de synchronisatie via protocol FDA in beide gevallen voorkomen.

## Pakketconfiguratie {#packages-configuration}

Willekeurige schema-extensies die rechtstreeks zijn gekoppeld aan **Interactie** (aanbiedingen, voorstellen, ontvangers, enz.) moeten worden ingezet op de uitvoeringsinstanties.

Het interactiepakket moet in alle gevallen (besturing en uitvoering) zijn geïnstalleerd. Er zijn twee extra pakketten beschikbaar: een pakket dat op de besturingsinstanties moet worden geïnstalleerd en een ander pakket dat op elke uitvoeringsinstantie moet worden geïnstalleerd.

>[!NOTE]
>
>Wanneer u het pakket installeert, **lang** tekstvelden van het dialoogvenster **nms:voorstel** tabel, zoals de propositie-id, wordt **int64** tekstvelden. Dit type gegevens wordt in het dialoogvenster [deze sectie](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

De duur van het gegevensbehoud moet op elke instantie (via **[!UICONTROL Data purge]** in de implementatiewizard). Bij uitvoering moet deze periode overeenstemmen met de historische diepte die nodig is voor de berekening van de typologische regels (verschuivingstermijn) en de subsidiabiliteitsregels.

Op besturingsinstanties:

1. Een externe account maken via een uitvoeringsinstantie:

   ![](assets/interaction_powerbooster1.png)

   * Vul het label in en voeg een korte en expliciete interne naam toe.
   * Selecteer **[!UICONTROL Execution instance]**.
   * Schakel de optie **[!UICONTROL Enabled]** in.
   * Voltooi de verbindingsparameters voor de uitvoeringsinstantie.
   * Elke uitvoeringsinstantie moet aan een identiteitskaart worden verbonden. Deze id wordt toegewezen wanneer u op het tabblad **[!UICONTROL Initialize connection]** knop.
   * Controleer het gebruikte type toepassing: **[!UICONTROL Message Center]**, **[!UICONTROL Interaction]**, of beide.
   * Voer de gebruikte FDA-account in. Een exploitant moet op de uitvoeringsinstanties worden gecreeerd en moet de volgende lees- en schrijfrechten op het gegevensbestand van de betrokken instantie hebben:

     ```
     grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
     grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
     ```

   >[!NOTE]
   >
   >Het IP adres van de controleinstantie moet op de uitvoeringsinstanties worden toegelaten.

1. Configureer de omgeving:

   ![](assets/interaction_powerbooster2.png)

   * Voeg de lijst met uitvoeringsinstanties toe.
   * Geef voor elke synchronisatie de synchronisatieperiode en filtercriteria op (bijvoorbeeld per land).

     >[!NOTE]
     >
     >Als er een fout optreedt, kunt u de synchronisatieworkflows raadplegen en meldingen aanbieden. Deze zijn te vinden in de technische workflows van de toepassing.

Als voor optimalisatie slechts een deel van de marketingdatabase wordt gedupliceerd op de uitvoeringsinstanties, kunt u een beperkt schema opgeven dat is gekoppeld aan de omgeving, zodat gebruikers alleen gegevens kunnen gebruiken die beschikbaar zijn op de uitvoeringsinstanties. U kunt een aanbieding maken met gegevens die niet beschikbaar zijn op uitvoeringsinstanties. Om dit te doen, moet u de regel op de andere kanalen deactiveren door deze regel op het uitgaande kanaal (**[!UICONTROL Taken into account if]** veld).

![](assets/ita_filtering.png)

## Onderhoudsopties {#maintenance-options}

Hier is een lijst van onderhoudsopties beschikbaar op de controle instantie:

>[!IMPORTANT]
>
>Deze opties mogen alleen voor specifieke onderhoudsbeurten worden gebruikt.

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**: laatste datum waarop een omgeving is gesynchroniseerd op een bepaalde instantie.
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**: laatste datum waarop voorstellen uit een bepaald schema zijn gesynchroniseerd van de ene instantie naar de andere.
* **`NmsInteraction_MapWorkflowId`**: een optie die de lijst bevat van alle gegenereerde synchronisatieworkflows.

De volgende optie is beschikbaar bij uitvoeringsinstanties:

**NmsExecutionInstanceId**: optie met de instantie-id.

## Installatie van pakketten {#packages-installation}

Als uw instantie eerder niet over het interactiepakket beschikte, is er geen migratie nodig. Standaard wordt de tabel met voorstellen weergegeven in 64 bits nadat de pakketten zijn geïnstalleerd.

>[!IMPORTANT]
>
>Afhankelijk van het volume van bestaande voorstellingen in uw instantie, kan deze bewerking even duren.

* Als uw instantie weinig of geen voorstellingen heeft, is geen handmatige wijziging van de tabel met voorstellingen nodig. De wijziging wordt uitgevoerd wanneer pakketten worden geïnstalleerd.
* Als uw instantie veel voorstellingen heeft, is het beter om de structuur van de lijst met voorstellingen te wijzigen voordat u de controlepakketten installeert en uitvoert. We raden u aan de query&#39;s uit te voeren tijdens een periode met weinig activiteit.

>[!NOTE]
>
>Als u specifieke configuraties in de voorstellingstabel hebt uitgevoerd, pas dienovereenkomstig de vragen aan.

### PostgreSQL {#postgresql}

Er zijn twee methoden. De eerste (met een werktabel) is iets sneller.

**Werktabel**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**Tabel wijzigen**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

De grootte van een **Getal** type leidt niet tot waarden of de index wordt opnieuw geschreven. Het is dus onmiddellijk.

De uit te voeren query is als volgt:

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

De uit te voeren vragen zijn als volgt:

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```
