---
product: campaign
title: Gegevens bijwerken
description: Gegevens bijwerken
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# Gegevens bijwerken{#updating-data}

>[!NOTE]
>
>Deze pagina is alleen van toepassing op operatoren die verbinding maken met Campagne met native verificatie.

De gegevens die aan het profiel van een ontvanger zijn gekoppeld, kunnen handmatig of automatisch worden bijgewerkt.

## Een automatische update instellen {#setting-up-an-automatic-update}

Een automatische update kan worden geconfigureerd via een workflow. Raadpleeg [deze sectie](../../workflow/using/update-data.md) voor meer informatie.

## Een massaupdate uitvoeren {#performing-a-mass-update}

Als u handmatige updates wilt uitvoeren, klikt u met de rechtermuisknop op de geselecteerde ontvanger(s) om het snelmenu **[!UICONTROL Actions]** te gebruiken of gebruikt u het pictogram **[!UICONTROL Actions]** .

![](assets/s_ncs_user_action_icon.png)

Er zijn twee soorten updates: massa-update voor een reeks ontvangers, en gegevens die tussen twee profielen samenvoegen. Voor elke actie, laat een medewerker u de update vormen.

### Massa-update {#mass-update}

Gebruik **[!UICONTROL Action > Mass update of selected lines...]** voor updates op grote schaal. De hulphulp u vormt en stelt de update in werking.

De eerste stap van de assistent bestaat uit het opgeven van het (de) veld(en) dat/die moeten worden bijgewerkt.

In het linkergedeelte van de assistent wordt de lijst met beschikbare velden weergegeven. Gebruik het veld **[!UICONTROL Find]** om een zoekopdracht van deze velden uit te voeren. Druk **ga** sleutel in om de lijst te doorbladeren. De veldnamen die overeenkomen met uw invoer worden vet weergegeven, zoals hieronder wordt weergegeven.

Dubbelklik op de velden die u wilt bijwerken om deze weer te geven in het rechtergedeelte van de assistent.

![](assets/s_ncs_user_update_wizard01_1.png)

Als er een fout optreedt, gebruikt u de knop **[!UICONTROL Delete]** om een veld te verwijderen uit de lijst met velden die moeten worden bijgewerkt.

Selecteer of voer de waarden in die u wilt toepassen op de profielen die moeten worden bijgewerkt.

![](assets/s_ncs_user_update_wizard01_12.png)

U kunt op **[!UICONTROL Distribution of values]** klikken om de verdeling weer te geven van de waarden van het geselecteerde veld voor de ontvangers in de huidige map (niet alleen de ontvangers die door de update worden beïnvloed).

![](assets/s_ncs_user_update_wizard01_2.png)

U kunt filters definiëren om de verdeling van waarden in dit venster weer te geven of de huidige map wijzigen om de verdeling van waarden in een andere map weer te geven. Dit zijn alleen-lezen handelingen; deze zijn niet van invloed op de configuratie van de update die wordt gedefinieerd.

![](assets/s_ncs_user_update_wizard01_3.png)

Sluit dit venster en klik op **[!UICONTROL Next]** om de tweede update-hulpstap weer te geven. In deze stap kunt u de update starten door op **[!UICONTROL Start]** te klikken.

![](assets/s_ncs_user_update_wizard01_4.png)

De informatie betreffende updateuitvoering wordt getoond in de hogere sectie van de medewerker.

Met **[!UICONTROL Stop]** kunt u de update annuleren, maar bepaalde records zijn mogelijk bijgewerkt. Als u het proces stopt, worden deze updates niet geannuleerd. Op de voortgangsbalk ziet u hoe ver de bewerking is gevorderd.

### Gegevens samenvoegen {#merge-data}

Selecteer **[!UICONTROL Merge selected lines...]** om het samenvoegen van twee profielen voor ontvangers te starten. De profielen die moeten worden samengevoegd, moeten worden geselecteerd voordat u de optie selecteert. De fusie wordt gevormd en gelanceerd gebruikend een medewerker.

De assistent geeft de waarden weer die moeten worden opgehaald voor elk veld dat wordt ingevuld in een van de bronprofielen. Als een of meer velden in de profielen die moeten worden samengevoegd andere waarden hebben, worden deze weergegeven in de sectie **[!UICONTROL List of conflicts]** . Vervolgens kunt u het standaardprofiel selecteren met de keuzerondjes in de lijst, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_merge_wizard01_1.png)

Klik op **[!UICONTROL Compute]** om het resultaat van uw keuze weer te geven.

![](assets/s_ncs_user_merge_wizard01_2.png)

Controleer de **[!UICONTROL Result]** -kolommen van beide secties van het venster en klik op **[!UICONTROL Finish]** om het samenvoegen uit te voeren.

## Gegevens exporteren {#exporting-data}

U kunt de inhoud van een lijst exporteren. Het exporteren configureren en uitvoeren:

1. Selecteer de records die u wilt exporteren.
1. Klik met de rechtermuisknop en selecteer **[!UICONTROL Export...]** .

   ![](assets/s_ncs_user_export_list.png)

1. Selecteer vervolgens de gegevens die u wilt extraheren. Standaard worden alle weergegeven kolommen toegevoegd aan de uitvoerkolommen.

   ![](assets/s_ncs_user_export_list_start.png)

   Voor meer op hoe te om de uitvoermedewerker te vormen, verwijs naar [ deze sectie ](../../platform/using/executing-export-jobs.md).

## Abonneren op een service {#subscribing-to-a-service}

In de meeste gevallen, tekenen de ontvangers aan een nieuwsbrief door een specifieke het landen pagina in, zoals die in [ wordt verklaard deze sectie ](../../delivery/using/managing-subscriptions.md). De profielen van gefilterde ontvangers kunnen echter handmatig worden geabonneerd op een service (nieuwsbrief of virtuele service). Dit doet u als volgt:

1. Selecteer de ontvangers u zich wilt intekenen en met de rechtermuisknop klikken.
1. Selecteer **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Selecteer de gewenste service en klik op **[!UICONTROL Next]** :

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Met deze editor kunt u een nieuwe service maken: klik op de knop **[!UICONTROL Create]** .

1. U kunt **[!UICONTROL Send a confirmation message]** aan ontvangers. De inhoud van dit bericht kan in het abonnementsscenario worden gevormd verbonden aan de geselecteerde dienst.
1. Klik op **[!UICONTROL Start]** om het abonnementsproces uit te voeren.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

In de bovenste sectie van het venster kunt u het uitvoeringsproces volgen. Met de knop **[!UICONTROL Stop]** kunt u het proces stoppen. Ontvangers die al zijn verwerkt, worden echter geabonneerd.

Als u de optie **[!UICONTROL Do not keep a trace of this job in the database]** uitschakelt, kunt u de uitvoeringsmap selecteren (of maken) waarin de informatie over dit proces wordt opgeslagen.

Als u het proces wilt controleren, gaat u naar het tabblad **[!UICONTROL Subscriptions]** in de profielen van de ontvangers die bij deze bewerking betrokken zijn, of naar het tabblad **[!UICONTROL Subscriptions]** dat via het knooppunt **[!UICONTROL Profiles and Targets > Services and Subscriptions]** wordt geopend.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Voor meer bij het creëren van en het vormen van de informatiediensten, verwijs naar [ deze pagina ](../../delivery/using/managing-subscriptions.md).
