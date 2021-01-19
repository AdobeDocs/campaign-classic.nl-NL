---
solution: Campaign Classic
product: campaign
title: Workflowdata gebruiken
description: Leer hoe u workflowgegevens gebruikt
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 1901db70fde2b7b3c2789154bd93160012cd4c29
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# Workflowdata gebruiken{#how-to-use-workflow-data}

## De database {#updating-the-database} bijwerken

Alle verzamelde gegevens kunnen worden gebruikt om de database bij te werken, of in leveringen. U kunt bijvoorbeeld de personalisatiemogelijkheden voor berichtinhoud verrijken (het aantal contracten in het bericht opnemen, het gemiddelde winkelwagentje van het afgelopen jaar opgeven, enzovoort) of een gedetailleerde bevolkingsgerichtheid (verzend een bericht aan contractmedehouders, richt de 1.000 beste abonnees aan online diensten, enz.). Deze gegevens kunnen ook worden geëxporteerd of gearchiveerd in een lijst.

### Lijsten en directe updates {#lists-and-direct-updates}

De gegevens van de Adobe Campaign-databank en de bestaande lijsten kunnen worden bijgewerkt met behulp van twee specifieke activiteiten:

* Met de activiteit **[!UICONTROL List update]** kunt u werktabellen opslaan in een datalist.

   U kunt een bestaande lijst selecteren of maken. In dit geval worden de naam en mogelijk de recordmap berekend.

   ![](assets/s_user_create_list.png)

   Zie [Lijstupdate](../../workflow/using/list-update.md).

* De **[!UICONTROL Update data]** activiteit voert een massa update van de gebieden in het gegevensbestand uit.

   Raadpleeg [Gegevens bijwerken](../../workflow/using/update-data.md) voor meer informatie hierover.

### Abonnementsbeheer/-beheer {#subscription-unsubscription-management}

Raadpleeg [Abonnementsservices](../../workflow/using/subscription-services.md) voor informatie over het abonneren en het opzeggen van ontvangers voor een informatieservice via een workflow.

## Verzenden via een workflow {#sending-via-a-workflow}

### Leveringsactiviteit {#delivery-activity}

De leveringsactiviteit wordt gedetailleerd in [Levering](../../workflow/using/delivery.md).

### Verrijken en richten van leveringen {#enriching-and-targeting-deliveries}

Leveringen kunnen gegevens uit workflows verwerken om de inhoud aan te passen of binnen het kader van de selectie van doelgroepen.

Zo kunt u in het kader van een directe postbezorging de aanvullende gegevens, die zijn ontleend aan gegevensmanipulatie die in de workflow is uitgevoerd, opnemen in het extractiebestand:

![](assets/s_advuser_add_data_postal_mail.png)

Naast de gebruikelijke verpersoonlijkingsgebieden, kunt u verpersoonlijkingsgebieden van werkschemafasen aan de leveringsinhoud toevoegen. De extra gegevens die in de werkschemaactiviteiten worden bepaald kunnen in de leveringstovenaar, zoals aangetoond in het hieronder voorbeeld worden gehouden en worden toegankelijk gemaakt, voor het bepalen van de naam van het outputdossier binnen het kader van direct postlevering:

![](assets/s_advuser_using_additional_data.png)

De gegevens in de workflowtabel worden aangeduid met de naam: het wordt altijd samengesteld uit **targetData** verbinding. Raadpleeg [Doelgegevens](../../workflow/using/data-life-cycle.md#target-data) voor meer informatie hierover.

In het kader van de e-maillevering kunnen personaliseringsgebieden ook gegevens gebruiken van doeluitbreiding die in de het richten werkschemasfases wordt uitgevoerd, zoals aangetoond in het hieronder voorbeeld:

![](assets/s_advuser_add_data_email.png)

Als een segmentcode in een het richten activiteit wordt gespecificeerd, wordt het toegevoegd aan een specifieke kolom van de werkschemalijst en zal samen met de verpersoonlijkingsgebieden worden aangeboden. Als u alle aanpassingsvelden wilt weergeven, klikt u op de koppeling **[!UICONTROL Target extension > Other...]** die toegankelijk is via de aanpassingsknop.

![](assets/s_advuser_segment_code_select.png)
