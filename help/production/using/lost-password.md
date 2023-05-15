---
product: campaign
title: Wachtwoord verloren
description: Wachtwoord verloren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# Wachtwoord verloren{#lost-password}



U kunt een verloren wachtwoord wijzigen of herstellen.
Er zijn twee mogelijke scenario&#39;s:

* [Wachtwoord verloren door een Adobe Campaign-operator](#password-lost-by-campaign-operator)
* [Intern wachtwoord verloren](#internal-password-lost) (alleen on-premise klanten)

## Wachtwoord verloren door een Campagneoperator {#password-lost-by-campaign-operator}

Als een Adobe Campaign-operator zijn wachtwoord verliest, kunt u het wijzigen.
Volg de onderstaande stappen om dit te doen:

1. Verbind via een exploitant met beheerderrechten.
1. Klik met de rechtermuisknop op een operator.
1. Selecteer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Stel het nieuwe wachtwoord van de operator in. Wij adviseren dat de exploitant hun wachtwoord verandert wanneer zij eerst opnieuw verbinden.

## Intern wachtwoord verloren {#internal-password-lost}

>[!NOTE]
>
>Deze sectie is alleen van toepassing op on-premise klanten.

Als het interne wachtwoord verloren gaat, moet u het opnieuw initialiseren.
Hiervoor volgt u de volgende procedure:

1. Bewerk de **/usr/local/neolane/nl6/conf/serverConf.xml** bestand.

1. Ga naar de **internalPassword** lijn.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Verwijder de tekenreeks tussen aanhalingstekens, in dit geval: **myPassword**

   U krijgt dus de volgende regel:

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Sla de wijzigingen op en sluit het bestand.

1. Configureer het nieuwe wachtwoord. Voer hiertoe de volgende opdrachten in:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. U kunt nu uw nieuwe wachtwoord gebruiken om verbinding te maken met **Intern** in.
