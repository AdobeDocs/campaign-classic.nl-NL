---
solution: Campaign Classic
product: campaign
title: Beschikbaarheid van clientconsole voor Windows
description: Beschikbaarheid van clientconsole voor Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# Beschikbaarheid van clientconsole voor Windows{#client-console-availability-for-windows}

Adobe Campaign-gebruikers kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd, als ze de clientconsole gebruiken.

Wanneer de computer die wordt gebruikt om een Adobe Campaign-toepassingsserver (**nlserver-web**) te starten gebruikersverbindingen ontvangt van de clientconsole, kunt u deze configureren om het installatieprogramma voor de Adobe Campaign-client beschikbaar te maken via een HTML-interface.

Hiervoor moet u:

1. Herstel het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt aangeroepen `setup-client-7.X.XXXX.exe` voor v7 of `setup-client-6.X.XXXX.exe` voor v6.1, waarbij `X` de subversie van Adobe Campaign en het buildnummer `XXXX` zijn.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campaign, onder **/datakit/nl/eng/jsp**.
1. Start de Adobe Campaign-server.

De uiteindelijke gebruikers kunnen het installatieprogramma van de console dan downloaden via een webbrowser via de volgende URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Voor deze pagina is een aanmeldingsnaam en wachtwoord vereist die in de toepassing zijn gedefinieerd.

Als u de console wilt downloaden en installeren, raadpleegt u [De clientconsole](../../installation/using/installing-the-client-console.md)installeren.

Wanneer er een nieuwe versie van de clientconsole beschikbaar is, wordt u gevraagd deze te downloaden.

>[!NOTE]
>
>In de herinnering die wordt getoond, adviseert Adobe het verlaten van de optie **[!UICONTROL No longer ask this question]** om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.\
>Als u deze optie selecteert en ervoor kiest de nieuwste versie niet te downloaden, wordt geen andere gebruiker op de hoogte gesteld van nieuwe beschikbare versies.

Om deze herinnering terug te stellen, volg de stappen hieronder (slechts zouden de systeembeheerders comfortabel met het uitgeven van het Registratie deze veranderingen moeten aanbrengen):

1. Open de Register-editor met de **opdracht regedit** in het **[!UICONTROL Start > Run]** menu.
1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Verwijder het **confAdvisedUpgrade** -item en sluit de Register-editor.

