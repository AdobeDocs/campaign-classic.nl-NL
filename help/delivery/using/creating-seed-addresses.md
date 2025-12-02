---
product: campaign
title: Seedadressen maken
description: Leer hoe u zaadadressen maakt en gebruikt
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
role: User, Developer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 1%

---

# Seedadressen maken{#creating-seed-addresses}

Zaadadressen worden niet beheerd via standaardprofielen en -doelen, maar in een speciaal knooppunt van de Adobe Campaign-hiërarchie **[!UICONTROL Resources > Campaign management > Seed addresses]** .

U kunt submappen maken om de zaadadressen te ordenen. Klik hiertoe met de rechtermuisknop op het knooppunt **[!UICONTROL Seed addresses]** en selecteer **[!UICONTROL Create a new 'Seed addresses' folder]** . Geef de submap een naam en druk op **[!UICONTROL Enter]** om te valideren. U kunt nu zaadadressen maken of kopiëren naar deze submap. Voor meer op dit, verwijs naar [&#x200B; bepalen adressen &#x200B;](#defining-addresses).

Met Adobe Campaign kunt u ook zaadadressjablonen maken die worden geïmporteerd in leveringen of campagnes en die worden aangepast aan de specifieke behoeften van de desbetreffende leveringen en campagnes. Verwijs naar [&#x200B; zaadadresmalplaatjes &#x200B;](#creating-seed-address-templates) creëren.

## Adressen definiëren {#defining-addresses}

Voer de volgende stappen uit om zaadadressen te maken:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met adressen.
1. Voer in de overeenkomende velden op het tabblad **[!UICONTROL Recipient]** de gegevens in die zijn gekoppeld aan het adres. De beschikbare velden komen overeen met de standaardvelden in de profielen van de ontvangers van de levering (nms :recipient tabel): naam, voornaam, e-mail, enz.

   >[!NOTE]
   >
   >Het label van het adres wordt automatisch ingevuld met de achternaam en voornaam die u hebt gedefinieerd.
   >
   >U hoeft niet alle velden van elk tabblad in te voeren wanneer u een zaadadres maakt. Ontbrekende personalisatie-elementen worden willekeurig ingevoerd tijdens de leveringsanalyse.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Voer op het tabblad **[!UICONTROL Address fields]** de waarden in die tijdens de analysefase (in de **[!UICONTROL nms:broadLog]** -tabel) in de leveringslogboeken worden ingevoegd.

1. Voer op het tabblad **[!UICONTROL Additional data]** de aanpassingsgegevens in die worden gebruikt voor de leveringen die in de workflows voor gegevensbeheer zijn gemaakt en waaraan u een specifieke waarde wilt toewijzen.

   >[!NOTE]
   >
   >Controleer of er aanvullende doelgegevens zijn gedefinieerd met een alias die begint met &#39;@&#39; in de **[!UICONTROL Enrichment]** -activiteit. Anders, zult u hen niet behoorlijk met uw zaadadressen in uw leveringsactiviteit kunnen gebruiken.

## Sjablonen voor zaadadressen maken {#creating-seed-address-templates}

Om adresmalplaatjes tot stand te brengen die zullen worden ingevoerd en voor elke levering kunnen worden gewijzigd, is het proces het zelfde als wanneer het bepalen van een nieuw zaadadres. Het enige verschil is dat de adressen van zaadadresmalplaatjes in een &quot;Malplaatje&quot;typemap moeten worden opgeslagen.

Als u een sjabloonmap wilt definiëren, past u het volgende proces toe:

1. Maak een nieuwe **[!UICONTROL Seed addresses]** typemap, klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]** .

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Klik op het tabblad **[!UICONTROL Restriction]** en voeg de volgende filtervoorwaarde toe: **@isModel = true** .

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   In deze map opgeslagen adressen kunnen nu worden gebruikt als adressjablonen. U kunt hen invoeren in leveringen of campagnes en hen aanpassen die op de specifieke behoeften van de betrokken leveringen en de campagnes worden gebaseerd (zie [&#x200B; zaadadressen &#x200B;](adding-seed-addresses.md) toevoegen).
