---
title: zaadadressen maken
seo-title: zaadadressen maken
description: zaadadressen maken
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# zaadadressen maken{#creating-seed-addresses}

De zaadadressen worden niet beheerd via standaardprofielen en doelstellingen, maar in een specifiek knooppunt van de hiërarchie van de Campagne van Adobe **[!UICONTROL Resources > Campaign management > Seed addresses]**.

U kunt submappen maken om de zaadadressen te ordenen. Klik hiertoe met de rechtermuisknop op het **[!UICONTROL Seed addresses]** knooppunt en selecteer **[!UICONTROL Create a new 'Seed addresses' folder]**. Geef de submap een naam en druk op **[!UICONTROL Enter]** om te valideren. U kunt nu zaadadressen maken of kopiëren naar deze submap. Voor meer op dit, verwijs naar het [bepalen van adressen](#defining-addresses).

Met Adobe Campaign kunt u ook zaadadressjablonen maken die worden geïmporteerd in leveringen of campagnes en die worden aangepast op basis van de specifieke behoeften van de desbetreffende leveringen en campagnes. Raadpleeg Sjablonen voor [zaadadressen](#creating-seed-address-templates)maken.

## Adressen definiëren {#defining-addresses}

Voer de volgende stappen uit om zaadadressen te maken:

1. Klik op de **[!UICONTROL New]** knop boven de lijst met zaadadressen.
1. Voer in de overeenkomstige velden op het **[!UICONTROL Recipient]** tabblad de gegevens in die zijn gekoppeld aan het adres. De beschikbare velden komen overeen met de standaardvelden in de profielen van de ontvangers van de levering (nms:tabel van de ontvanger): naam, voornaam, e-mail, enz.

   >[!NOTE]
   >
   >Het label van het adres wordt automatisch ingevuld met de achternaam en voornaam die u hebt gedefinieerd.
   >
   >Het is niet nodig om alle gebieden van elk lusje in te gaan wanneer het creëren van een zaadadres. Ontbrekende personalisatie-elementen worden willekeurig ingevoerd tijdens de levering.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Op het **[!UICONTROL Seed fields]** lusje, ga de waarden in die in de leveringslogboeken tijdens de analysefase (in de **[!UICONTROL nms:broadLog]** lijst) zullen worden opgenomen.
1. Op het **[!UICONTROL Additional data]** lusje, ga de verpersoonlijkingsgegevens in die voor de leveringen worden gebruikt die in de werkschema&#39;s worden gecreeerd Datamanagement en die u een specifieke waarde aan wilt toewijzen.

## Sjablonen voor zaadadressen maken {#creating-seed-address-templates}

Om adresmalplaatjes tot stand te brengen die zullen worden ingevoerd en voor elke levering kunnen worden gewijzigd, is het proces het zelfde als wanneer het bepalen van een nieuw zaadadres. Het enige verschil is dat de adressen van zaadadresmalplaatjes in een &quot;Malplaatje&quot;typemap moeten worden opgeslagen.

Als u een sjabloonmap wilt definiëren, past u het volgende proces toe:

1. Maak een nieuwe **[!UICONTROL Seed addresses]** tekstmap, klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Klik op het **[!UICONTROL Restriction]** tabblad en voeg de volgende filtervoorwaarde toe: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Adressen die in deze map zijn opgeslagen, kunnen nu worden gebruikt als adressjablonen. U kunt ze importeren in leveringen of campagnes en ze aanpassen op basis van de specifieke behoeften van de betrokken leveringen en campagnes (zie [Adding Adding Address](../../delivery/using/adding-seed-addresses.md)).
