---
product: campaign
title: Valideren
description: Valideren
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 1%

---

# Valideren{#validating}



De globale concepten wanneer het bevestigen van een levering worden voorgesteld in [ deze sectie ](steps-validating-the-delivery.md).

Het outputdossier van een directe postlevering wordt geproduceerd tijdens de leveringsanalyse. De inhoud van het dossier hangt van de geselecteerde outputkolommen (verwijs naar [ dossier van de Uitwinning ](defining-the-direct-mail-content.md#extraction-file)) af.

>[!NOTE]
>
>De analysefase wordt gedetailleerd in [ Analyserend de levering ](steps-validating-the-delivery.md#analyzing-the-delivery).

Tijdens de analysefase wordt het bestand gegenereerd, maar wordt informatie over ontvangers (d.w.z. leveringslogboeken) niet bijgewerkt. U kunt deze taak dus annuleren zonder risico&#39;s te lopen.

Controleer het resultaat van de analyse en de inhoud van het uitvoerbestand voordat u op **[!UICONTROL Confirm delivery]** klikt. Met een bevestigingsbericht kunt u de levering starten.

Met de verzendbevestiging wordt de gegevensextractie in het opgegeven bestand gestart.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

U kunt de assistent vervolgens sluiten en de leveringslogboeken bekijken via het tabblad **[!UICONTROL Delivery]** , dat toegankelijk is via de leveringsdetails.

U kunt de terugwinningswijze van de leveringslogboeken van het **[!UICONTROL Analysis]** lusje van de leveringseigenschappen vormen.

Er zijn twee modi:

* **[!UICONTROL Messages are considered sent after validation]** (standaardmodus): in deze functiemodus worden alle uitzendingen bijgewerkt wanneer de operator de send bevestigt (de status gaat van &#39;In behandeling&#39; naar &#39;Verzonden&#39;) en wordt de levering automatisch ingesteld op **[!UICONTROL Finished]** .
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : in deze modus kunt u de uitzendingen bijwerken via een extern bestand dat door het servicebureau is verzonden. In dit geval moet een workflow voor het verwerken van deze informatie worden gebruikt om de status van de broadlog bij te werken.

  >[!NOTE]
  >
  >In dit geval moet de gebruiker ook de status van de levering wijzigen in **[!UICONTROL Finished]** zodra de weblogs zijn bijgewerkt.
