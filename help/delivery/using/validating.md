---
title: Valideren
seo-title: Valideren
description: Valideren
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Valideren{#validating}

Algemene concepten bij het valideren van een levering worden in [deze sectie](../../delivery/using/steps-validating-the-delivery.md)weergegeven.

Het outputdossier van een directe postlevering wordt geproduceerd tijdens de leveringsanalyse. De inhoud van het bestand is afhankelijk van de geselecteerde uitvoerkolommen (zie [Extractiebestand](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>De analysefase wordt gedetailleerd beschreven in [Analyseren van de levering](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Tijdens de analysefase wordt het bestand gegenereerd, maar wordt informatie over ontvangers (d.w.z. leveringslogboeken) niet bijgewerkt. U kunt deze taak dus annuleren zonder risico&#39;s te lopen.

Controleer het resultaat van de analyse en de inhoud van het uitvoerbestand voordat u op **[!UICONTROL Confirm delivery]** klikt. Met een bevestigingsbericht kunt u de levering starten.

Met de verzendbevestiging wordt de gegevensextractie in het opgegeven bestand gestart.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

U kunt de wizard vervolgens sluiten en de leveringslogboeken bekijken via het **[!UICONTROL Delivery]** tabblad, dat toegankelijk is via de leveringsdetails.

U kunt de terugwinningswijze van leveringslogboeken van het **[!UICONTROL Analysis]** lusje van de leveringseigenschappen vormen.

Er zijn twee modi:

* **[!UICONTROL Messages are considered sent after validation]** (standaardmodus): in deze functiemodus, worden alle uitzendingen bijgewerkt wanneer de exploitant verzendt bevestigt (hun status gaat van &quot;Hangende levering&quot;aan &quot;Verzonden&quot;over) en de levering wordt automatisch geplaatst aan **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : in deze modus kunt u de uitzendingen bijwerken via een extern bestand dat door het prepress-bureau wordt verzonden. In dit geval moet een workflow voor het verwerken van deze informatie worden gebruikt om de status van de broadlog bij te werken.

   >[!NOTE]
   >
   >In dit geval moet de status van de levering ook door de gebruiker worden veranderd **[!UICONTROL Finished]** zodra de uitzendingen worden bijgewerkt.
