---
title: Beschikbaarheid van clientconsole voor Windows
seo-title: Beschikbaarheid van clientconsole voor Windows
description: Beschikbaarheid van clientconsole voor Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Beschikbaarheid van clientconsole voor Windows{#client-console-availability-for-windows}

Gebruikers van Adobe Campagne kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd als ze de clientconsole gebruiken.

Wanneer de computer die wordt gebruikt om een Adobe Campagne-toepassingsserver (**nlserver web**) te starten gebruikersverbindingen ontvangt van de clientconsole, kunt u deze configureren om het installatieprogramma voor de rijke client van Adobe Campaign beschikbaar te maken via een HTML-interface.

Hiervoor moet u:

1. Herstel het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt aangeroepen `setup-client-7.X.XXXX.exe` voor v7 of `setup-client-6.X.XXXX.exe` voor v6.1. `X` Dit is de subversie van Adobe Campagne en `XXXX` is het buildnummer.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campagne, onder **/datakit/nl/eng/jsp**.
1. Start de Adobe Campagneserver.

De uiteindelijke gebruikers kunnen het installatieprogramma van de console dan downloaden via een webbrowser via de volgende URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Voor deze pagina is een aanmeldingsnaam en wachtwoord vereist die in de toepassing zijn gedefinieerd.

Als u de console wilt downloaden en installeren, raadpleegt u [De clientconsole](../../installation/using/installing-the-client-console.md)installeren.

Wanneer er een nieuwe versie van de clientconsole beschikbaar is, wordt u gevraagd deze te downloaden.

>[!NOTE]
>
>In de prompt die wordt weergegeven, raadt Adobe aan de optie **[!UICONTROL No longer ask this question]** uitgeschakeld te laten om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.\
>Als u deze optie selecteert en ervoor kiest de nieuwste versie niet te downloaden, wordt geen andere gebruiker op de hoogte gesteld van nieuwe beschikbare versies.

Om deze herinnering terug te stellen, volg de stappen hieronder (slechts zouden de systeembeheerders comfortabel met het uitgeven van het Registratie deze veranderingen moeten aanbrengen):

1. Open de Register-editor met de **opdracht regedit** in het **[!UICONTROL Start > Run]** menu.
1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Verwijder het **confAdvisedUpgrade** -item en sluit de Register-editor.

