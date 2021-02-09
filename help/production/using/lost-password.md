---
solution: Campaign Classic
product: campaign
title: Wachtwoord verloren
description: Wachtwoord verloren
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---


# Wachtwoord verloren{#lost-password}

U kunt een verloren wachtwoord wijzigen of herstellen.
Er zijn twee mogelijke scenario&#39;s:

* [Wachtwoord verloren door een Adobe Campaign-operator](#password-lost-by-campaign-operator)
* [Intern wachtwoord verloren](#internal-password-lost)  (alleen on-premise klanten)

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

1. Bewerk het bestand **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Ga naar **internalPassword** lijn.

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

1. U kunt uw nieuw wachtwoord nu gebruiken om op **Interne** wijze te verbinden.
