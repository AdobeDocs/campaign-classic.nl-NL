---
product: campaign
title: Werkstroomgegevens gebruiken
description: Leer hoe u workflowgegevens gebruikt
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Werkstroomgegevens gebruiken{#how-to-use-workflow-data}



## De database bijwerken {#updating-the-database}

Alle verzamelde gegevens kunnen worden gebruikt om de database bij te werken, of in leveringen. U kunt bijvoorbeeld de personalisatiemogelijkheden voor berichtinhoud verrijken (het aantal contracten in het bericht opnemen, het gemiddelde winkelwagentje van het afgelopen jaar opgeven, enzovoort) of een gedetailleerde bevolkingsgerichtheid (verzend een bericht aan contractmedehouders, richt de 1.000 beste abonnees aan online diensten, enz.). Deze gegevens kunnen ook worden geëxporteerd of gearchiveerd in een lijst.

### Lijsten en directe updates {#lists-and-direct-updates}

De gegevens van de Adobe Campaign-databank en de bestaande lijsten kunnen worden bijgewerkt met behulp van twee specifieke activiteiten:

* Met de activiteit **[!UICONTROL List update]** kunt u werktabellen opslaan in een datalist.

  U kunt een bestaande lijst selecteren of maken. In dit geval worden de naam en mogelijk de recordmap berekend.

  ![](assets/s_user_create_list.png)

  Verwijs naar [ update van de Lijst ](list-update.md).

* De **[!UICONTROL Update data]** -activiteit voert een massa-update uit van de velden in de database.

  Voor meer op dit, verwijs naar [ gegevens van de Update ](update-data.md).

### Abonnementsbeheer/Abonnementsbeheer {#subscription-unsubscription-management}

Om te weten te komen over het intekenen van en het opzeggen van ontvangers aan de informatiedienst via een werkschema, verwijs naar [ Diensten van het Abonnement ](subscription-services.md).

## Verzenden via een workflow {#sending-via-a-workflow}

### Leveringsactiviteit {#delivery-activity}

De leveringsactiviteit is gedetailleerd in [ Levering ](delivery.md).

### Verrijking en gerichtheid van leveringen {#enriching-and-targeting-deliveries}

Leveringen kunnen gegevens uit workflows verwerken om de inhoud aan te passen of binnen het kader van de selectie van doelgroepen.

Zo kunt u in het kader van een directe postbezorging de aanvullende gegevens, die zijn ontleend aan gegevensmanipulatie die in de workflow is uitgevoerd, opnemen in het extractiebestand:

![](assets/s_advuser_add_data_postal_mail.png)

Naast de gebruikelijke verpersoonlijkingsgebieden, kunt u verpersoonlijkingsgebieden van werkschemafasen aan de leveringsinhoud toevoegen. De extra gegevens die in de werkschemaactiviteiten worden bepaald kunnen in de leveringsmedewerker worden gehouden en worden toegankelijk gemaakt, zoals aangetoond in het voorbeeld hieronder, voor het bepalen van de naam van het outputdossier binnen het kader van direct postlevering:

![](assets/s_advuser_using_additional_data.png)

De gegevens in de werkschemalijst worden geïdentificeerd door zijn naam: het wordt altijd samengesteld uit de **targetData** verbinding. Voor meer op dit, verwijs naar [ gegevens van het Doel ](data-life-cycle.md#target-data).

In het kader van de e-maillevering kunnen personaliseringsgebieden ook gegevens gebruiken van doeluitbreiding die in de het richten werkschemasfases wordt uitgevoerd, zoals aangetoond in het hieronder voorbeeld:

![](assets/s_advuser_add_data_email.png)

Als een segmentcode in een het richten activiteit wordt gespecificeerd, wordt het toegevoegd aan een specifieke kolom van de werkschemalijst en zal samen met de verpersoonlijkingsgebieden worden aangeboden. Als u alle aanpassingsvelden wilt weergeven, klikt u op de koppeling **[!UICONTROL Target extension > Other...]** die toegankelijk is via de aanpassingsknop.

![](assets/s_advuser_segment_code_select.png)
