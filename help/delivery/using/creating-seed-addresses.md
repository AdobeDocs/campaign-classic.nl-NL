---
product: campaign
title: Seed-adressen maken
description: Leer hoe u zaadadressen maakt en gebruikt
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Seedadressen maken{#creating-seed-addresses}

![](../../assets/common.svg)

Zaadadressen worden niet beheerd via standaardprofielen en -doelen, maar in een speciaal knooppunt van de Adobe Campaign-hiërarchie **[!UICONTROL Resources > Campaign management > Seed addresses]**.

U kunt submappen maken om de zaadadressen te ordenen. Klik hiertoe met de rechtermuisknop op de knop **[!UICONTROL Seed addresses]** knooppunt en selecteer **[!UICONTROL Create a new 'Seed addresses' folder]**. Geef de submap een naam en druk op **[!UICONTROL Enter]** om te valideren. U kunt nu zaadadressen maken of kopiëren naar deze submap. Raadpleeg voor meer informatie hierover [Adressen definiëren](#defining-addresses).

Met Adobe Campaign kunt u ook zaadadressjablonen maken die worden geïmporteerd in leveringen of campagnes en die worden aangepast aan de specifieke behoeften van de desbetreffende leveringen en campagnes. Zie [Sjablonen voor zaadadressen maken](#creating-seed-address-templates).

## Adressen definiëren {#defining-addresses}

Voer de volgende stappen uit om zaadadressen te maken:

1. Klik op de knop **[!UICONTROL New]** knop boven de lijst met adressen.
1. Voer in de overeenkomende velden de gegevens die zijn gekoppeld aan het adres in de **[!UICONTROL Recipient]** tab. De beschikbare velden komen overeen met de standaardvelden in de profielen van de ontvangers van de levering (nms:tabel van de ontvanger): naam, voornaam, e-mail, enz.

   >[!NOTE]
   >
   >Het label van het adres wordt automatisch ingevuld met de achternaam en voornaam die u hebt gedefinieerd.
   >
   >Het is niet nodig om alle gebieden van elk lusje in te gaan wanneer het creëren van een zaadadres. Ontbrekende personalisatie-elementen worden willekeurig ingevoerd tijdens de levering.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In de **[!UICONTROL Seed fields]** voert u de waarden in die tijdens de analysefase in de leveringslogboeken worden ingevoegd (in de **[!UICONTROL nms:broadLog]** tabel).

1. In de **[!UICONTROL Additional data]** voert u de aanpassingsgegevens in die worden gebruikt voor de leveringen die worden gemaakt in de workflows voor gegevensbeheer en waaraan u een specifieke waarde wilt toewijzen.

   >[!NOTE]
   >
   >Zorg ervoor dat aanvullende doelgegevens zijn gedefinieerd met een alias die begint met &#39;@&#39; in het dialoogvenster **[!UICONTROL Enrichment]** activiteit. Anders, zult u hen niet behoorlijk met uw zaadadressen in uw leveringsactiviteit kunnen gebruiken.

## Sjablonen voor zaadadressen maken {#creating-seed-address-templates}

Om adresmalplaatjes tot stand te brengen die zullen worden ingevoerd en voor elke levering kunnen worden gewijzigd, is het proces het zelfde als wanneer het bepalen van een nieuw zaadadres. Het enige verschil is dat de adressen van zaadadresmalplaatjes in een &quot;Malplaatje&quot;typemap moeten worden opgeslagen.

Als u een sjabloonmap wilt definiëren, past u het volgende proces toe:

1. Een nieuwe **[!UICONTROL Seed addresses]** tekstmap, klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Klik op de knop **[!UICONTROL Restriction]** en voeg de volgende filtervoorwaarde toe: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Adressen die in deze map zijn opgeslagen, kunnen nu worden gebruikt als adressjablonen. U kunt ze importeren in leveringen of campagnes en ze aanpassen op basis van de specifieke behoeften van de betrokken leveringen en campagnes (zie [zaadadressen toevoegen](adding-seed-addresses.md)).
