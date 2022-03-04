---
product: campaign
title: Valideren
description: Valideren
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Valideren{#validating}

![](../../assets/common.svg)

Algemene concepten bij het valideren van een levering worden weergegeven in [deze sectie](steps-validating-the-delivery.md).

Het outputdossier van een directe postlevering wordt geproduceerd tijdens de leveringsanalyse. De inhoud van het bestand is afhankelijk van de geselecteerde uitvoerkolommen (zie [Extractiebestand](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>De analysefase wordt in detail beschreven in [De levering analyseren](steps-validating-the-delivery.md#analyzing-the-delivery).

Tijdens de analysefase wordt het bestand gegenereerd, maar wordt informatie over ontvangers (d.w.z. leveringslogboeken) niet bijgewerkt. U kunt deze taak dus annuleren zonder risico&#39;s te lopen.

Controleer het resultaat van de analyse en de inhoud van het uitvoerbestand voordat u op **[!UICONTROL Confirm delivery]**. Met een bevestigingsbericht kunt u de levering starten.

Met de verzendbevestiging wordt de gegevensextractie in het opgegeven bestand gestart.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

U kunt de wizard vervolgens sluiten en de leveringslogboeken bekijken via de **[!UICONTROL Delivery]** , toegankelijk via de leveringsgegevens.

U kunt de terugwinningswijze van leveringslogboeken van vormen **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen.

Er zijn twee modi:

* **[!UICONTROL Messages are considered sent after validation]** (standaardmodus): in deze functiemodus, worden alle uitzendingen bijgewerkt wanneer de exploitant verzendt bevestigt (hun status gaat van &quot;Hangende levering&quot;aan &quot;Verzonden&quot; over) en de levering wordt automatisch geplaatst aan **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : in deze modus kunt u de uitzendingen bijwerken via een extern bestand dat door het prepress-bureau wordt verzonden. In dit geval moet een workflow voor het verwerken van deze informatie worden gebruikt om de status van de broadlog bij te werken.

   >[!NOTE]
   >
   >In dit geval moet ook de status van de levering worden gewijzigd in **[!UICONTROL Finished]** door de gebruiker zodra de uitzendingen worden bijgewerkt.
