---
solution: Campaign Classic
product: campaign
title: Wachtwoord verloren
description: Wachtwoord verloren
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: f24642223a2ec9f3d8e78e2f7e71a55bf14b80c7
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 9%

---


# Wachtwoord verloren{#lost-password}

U kunt een verloren wachtwoord wijzigen of herstellen.
Er zijn twee mogelijke scenario&#39;s:

**Wachtwoord verloren door een Adobe Campaign-operator**

In dat geval kunt u het wachtwoord van de betreffende operator wijzigen.
Volg de onderstaande stappen om dit te doen:

1. Verbind via een exploitant met beheerderrechten.
1. Klik met de rechtermuisknop op een operator.
1. Selecteer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Stel het nieuwe wachtwoord van de operator in. We raden aan dat de operatoren hun wachtwoord wijzigen wanneer ze opnieuw verbinden.

**Verlies van intern wachtwoord (alleen on-premise klanten)**

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
