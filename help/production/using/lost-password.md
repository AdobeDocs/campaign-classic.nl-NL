---
solution: Campaign Classic
product: campaign
title: Wachtwoord verloren
description: Wachtwoord verloren
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Wachtwoord verloren{#lost-password}

U kunt een verloren wachtwoord wijzigen of herstellen.

Er zijn twee mogelijke scenario&#39;s:

* Wachtwoord verloren door een Adobe Campaign-operator.

   In dat geval kunt u het wachtwoord van de betreffende operator wijzigen. Om dit te doen, verbind via een exploitant met beheerderrechten, klik op een exploitant met de rechtermuisknop aan, selecteer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** en plaats het nieuwe wachtwoord van de exploitant. We raden operatoren aan hun wachtwoord te wijzigen wanneer ze opnieuw verbinden.

   ![](assets/operator-passwd.png)

* **Verlies van** intern wachtwoord (alleen on-premise klanten).

   Als het **internal** wachtwoord verloren gaat, moet u het opnieuw initialiseren. Hiervoor volgt u de volgende procedure:

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

