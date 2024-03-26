---
product: campaign
title: Werkstroomgegevens gebruiken
description: Leer hoe u workflowgegevens gebruikt
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Werkstroomgegevens gebruiken{#how-to-use-workflow-data}



## De database bijwerken {#updating-the-database}

Alle verzamelde gegevens kunnen worden gebruikt om de database bij te werken, of in leveringen. U kunt bijvoorbeeld de personalisatiemogelijkheden voor berichtinhoud verrijken (het aantal contracten in het bericht opnemen, het gemiddelde winkelwagentje van het afgelopen jaar opgeven, enzovoort) of een gedetailleerde bevolkingsgerichtheid (verzend een bericht aan contractmedehouders, richt de 1.000 beste abonnees aan online diensten, enz.). Deze gegevens kunnen ook worden geëxporteerd of gearchiveerd in een lijst.

### Lijsten en directe updates {#lists-and-direct-updates}

De gegevens van de Adobe Campaign-databank en de bestaande lijsten kunnen worden bijgewerkt met behulp van twee specifieke activiteiten:

* De **[!UICONTROL List update]** Met activiteit kunt u werktabellen opslaan in een database.

  U kunt een bestaande lijst selecteren of maken. In dit geval worden de naam en mogelijk de recordmap berekend.

  ![](assets/s_user_create_list.png)

  Zie [Lijstupdate](list-update.md).

* De **[!UICONTROL Update data]** de activiteit voert een massa update van de gebieden in het gegevensbestand uit.

  Raadpleeg voor meer informatie hierover [Gegevens bijwerken](update-data.md).

### Abonnementsbeheer/Abonnementsbeheer {#subscription-unsubscription-management}

Als u via een workflow wilt weten hoe ontvangers zich moeten abonneren op een informatieservice of het abonnement moeten opzeggen, raadpleegt u [Abonnementsservices](subscription-services.md).

## Verzenden via een workflow {#sending-via-a-workflow}

### Leveringsactiviteit {#delivery-activity}

De leveringsactiviteit wordt in detail beschreven in [Aflevering](delivery.md).

### Verrijking en gerichtheid van leveringen {#enriching-and-targeting-deliveries}

Leveringen kunnen gegevens uit workflows verwerken om de inhoud aan te passen of binnen het kader van de selectie van doelgroepen.

Zo kunt u in het kader van een directe postbezorging de aanvullende gegevens, die zijn ontleend aan gegevensmanipulatie die in de workflow is uitgevoerd, opnemen in het extractiebestand:

![](assets/s_advuser_add_data_postal_mail.png)

Naast de gebruikelijke verpersoonlijkingsgebieden, kunt u verpersoonlijkingsgebieden van werkschemafasen aan de leveringsinhoud toevoegen. De extra gegevens die in de werkschemaactiviteiten worden bepaald kunnen in de leveringstovenaar, zoals aangetoond in het hieronder voorbeeld worden gehouden en worden toegankelijk gemaakt, voor het bepalen van de naam van het outputdossier binnen het kader van direct postlevering:

![](assets/s_advuser_using_additional_data.png)

De gegevens in de tabel met workflows worden aangeduid met de naam ervan: deze bestaat altijd uit de **targetData** koppeling. Raadpleeg voor meer informatie hierover [Doelgegevens](data-life-cycle.md#target-data).

In het kader van de e-maillevering kunnen personaliseringsgebieden ook gegevens gebruiken van doeluitbreiding die in de het richten werkschemasfases wordt uitgevoerd, zoals aangetoond in het hieronder voorbeeld:

![](assets/s_advuser_add_data_email.png)

Als een segmentcode in een het richten activiteit wordt gespecificeerd, wordt het toegevoegd aan een specifieke kolom van de werkschemalijst en zal samen met de verpersoonlijkingsgebieden worden aangeboden. Als u alle verpersoonlijkingsvelden wilt weergeven, klikt u op de knop **[!UICONTROL Target extension > Other...]** verbinding toegankelijk via de verpersoonlijkingsknoop.

![](assets/s_advuser_segment_code_select.png)
