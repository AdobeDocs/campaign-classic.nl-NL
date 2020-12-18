---
solution: Campaign Classic
product: campaign
title: Seed-adressen maken
description: Leer hoe u zaadadressen maakt en gebruikt
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---


# Seed-adressen maken{#creating-seed-addresses}

Zaadadressen worden niet beheerd via standaardprofielen en -doelen, maar in een speciaal knooppunt van de Adobe Campaign-hiërarchie **[!UICONTROL Resources > Campaign management > Seed addresses]**.

U kunt submappen maken om de zaadadressen te ordenen. Klik hiertoe met de rechtermuisknop op het knooppunt **[!UICONTROL Seed addresses]** en selecteer **[!UICONTROL Create a new 'Seed addresses' folder]**. Geef de submap een naam en druk op **[!UICONTROL Enter]** om te valideren. U kunt nu zaadadressen maken of kopiëren naar deze submap. Voor meer op dit, verwijs naar [Het bepalen van adressen](#defining-addresses).

Met Adobe Campaign kunt u ook zaadadressjablonen maken die worden geïmporteerd in leveringen of campagnes en die worden aangepast aan de specifieke behoeften van de desbetreffende leveringen en campagnes. Zie [Sloopadadesjablonen maken](#creating-seed-address-templates).

## Adressen {#defining-addresses} definiëren

Voer de volgende stappen uit om zaadadressen te maken:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met adressen.
1. Voer in de overeenkomstige velden op het tabblad **[!UICONTROL Recipient]** de gegevens in die zijn gekoppeld aan het adres. De beschikbare velden komen overeen met de standaardvelden in de profielen van de ontvangers van de levering (nms:tabel van de ontvanger): naam, voornaam, e-mail, enz.

   >[!NOTE]
   >
   >Het label van het adres wordt automatisch ingevuld met de achternaam en voornaam die u hebt gedefinieerd.
   >
   >Het is niet nodig om alle gebieden van elk lusje in te gaan wanneer het creëren van een zaadadres. Ontbrekende personalisatie-elementen worden willekeurig ingevoerd tijdens de levering.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Op **[!UICONTROL Seed fields]** lusje, ga de waarden in die in de leveringslogboeken tijdens de analysefase (in **[!UICONTROL nms:broadLog]** lijst) zullen worden opgenomen.

1. Voer op het tabblad **[!UICONTROL Additional data]** de aanpassingsgegevens in die worden gebruikt voor de leveringen die in de workflows voor gegevensbeheer zijn gemaakt en waaraan u een specifieke waarde wilt toewijzen.

   >[!NOTE]
   >
   >Controleer of er aanvullende doelgegevens zijn gedefinieerd met een alias die begint met &#39;@&#39; in de activiteit **[!UICONTROL Enrichment]**. Anders, zult u hen niet behoorlijk met uw zaadadressen in uw leveringsactiviteit kunnen gebruiken.

## Sjablonen voor zaadadressen maken {#creating-seed-address-templates}

Om adresmalplaatjes tot stand te brengen die zullen worden ingevoerd en voor elke levering kunnen worden gewijzigd, is het proces het zelfde als wanneer het bepalen van een nieuw zaadadres. Het enige verschil is dat de adressen van zaadadresmalplaatjes in een &quot;Malplaatje&quot;typemap moeten worden opgeslagen.

Als u een sjabloonmap wilt definiëren, past u het volgende proces toe:

1. Maak een nieuwe **[!UICONTROL Seed addresses]** typemap, klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Klik op het tabblad **[!UICONTROL Restriction]** en voeg de volgende filtervoorwaarde toe: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Adressen die in deze map zijn opgeslagen, kunnen nu worden gebruikt als adressjablonen. U kunt ze importeren in leveringen of campagnes en ze aanpassen op basis van de specifieke behoeften van de betrokken leveringen en campagnes (zie [Adding zaadadressen toevoegen](../../delivery/using/adding-seed-addresses.md)).
