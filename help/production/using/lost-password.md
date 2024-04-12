---
product: campaign
title: Wachtwoord verloren
description: Wachtwoord verloren
feature: Monitoring, Access Management
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---

# Wachtwoord verloren{#lost-password}



U kunt een verloren wachtwoord wijzigen of herstellen.
Er zijn twee mogelijke scenario&#39;s:

* [Wachtwoord verloren door een Adobe Campaign-operator](#password-lost-by-campaign-operator)
* [Intern wachtwoord verloren](#internal-password-lost) (alleen on-premise klanten)

## Wachtwoord verloren door een Campagneoperator {#password-lost-by-campaign-operator}

Als een Adobe Campaign-operator zijn wachtwoord verliest, kunt u het wijzigen.
Hiervoor voert u de volgende stappen uit:

1. Verbind via een exploitant met beheerderrechten.
1. Klik met de rechtermuisknop op een operator.
1. Selecteren **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

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

1. Vorm het nieuwe wachtwoord. Voer hiertoe de volgende opdrachten in:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. U kunt nu uw nieuwe wachtwoord gebruiken om verbinding te maken met **Intern** -modus.
