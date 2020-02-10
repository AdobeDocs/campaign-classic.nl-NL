---
title: Wachtwoord verloren
seo-title: Wachtwoord verloren
description: Wachtwoord verloren
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# Wachtwoord verloren{#lost-password}

U kunt een verloren wachtwoord wijzigen of herstellen.

Er zijn twee mogelijke scenario&#39;s:

* Wachtwoord verloren door een Adobe Campaign-operator.

   In dat geval kunt u het wachtwoord van de betreffende operator wijzigen. U doet dit door verbinding te maken via een operator met beheerdersrechten, met de rechtermuisknop op een operator te klikken, **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** te selecteren en het nieuwe wachtwoord van de operator in te stellen. We raden operatoren aan hun wachtwoord te wijzigen wanneer ze opnieuw verbinden.

   ![](assets/operator-passwd.png)

* **Verlies van intern** wachtwoord (alleen on-premise klanten).

   Als het **interne** wachtwoord verloren gaat, moet u het opnieuw initialiseren. Hiervoor volgt u de volgende procedure:

   1. Bewerk het bestand **/usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Ga naar de regel **internalPassword** .

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

   1. U kunt nu uw nieuwe wachtwoord gebruiken om verbinding te maken in de **interne** modus.

