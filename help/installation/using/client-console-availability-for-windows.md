---
product: campaign
title: Beschikbaarheid van clientconsole voor Windows
description: Beschikbaarheid van clientconsole voor Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Beschikbaarheid van clientconsole voor Windows{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

Adobe Campaign-gebruikers kunnen zich alleen aanmelden bij de instantie die u hebt gemaakt en geconfigureerd, als ze de clientconsole gebruiken.

## Maak de cliëntconsole beschikbaar

Wanneer de computer wordt gebruikt om een Adobe Campaign-toepassingsserver te starten (**nlserver-web**) ontvangt gebruikersverbindingen van de clientconsole, kunt u deze configureren om het installatieprogramma voor de Adobe Campaign Rich Client beschikbaar te maken via een HTML-interface. Wanneer een nieuwe versie van de clientconsole beschikbaar is, worden gebruikers uitgenodigd deze te downloaden wanneer ze hun clientconsole starten.

Hiervoor moet u:

1. Selecteer het pakket dat het consoleinstallatieprogramma bevat.

   Dit bestand wordt aangeroepen `setup-client-7.X.XXXX.exe` voor v7 of `setup-client-6.X.XXXX.exe` voor v6.1, waarbij `X` is de subversie van Adobe Campaign en `XXXX` is het bouwstijlaantal.

1. Kopieer en plak dit pakket naar de installatiemap van Adobe Campaign (op de marketingserver voor hybride installaties), onder **/datakit/nl/eng/jsp**.
1. Start Adobe Campaign-server.

Campagnegebruikers kunnen het installatieprogramma van de console vervolgens via een webbrowser downloaden via de volgende URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Voor deze pagina is een aanmeldingsnaam en wachtwoord vereist die in de toepassing zijn gedefinieerd.

Leer hoe u de console installeert [in deze sectie](../../installation/using/installing-the-client-console.md).

## Voorstellen eindgebruikers om hun clientconsole bij te werken

Zodra de console in de serveromslag van de Campagne beschikbaar is, worden de gebruikers uitgenodigd om de recentste versie van de cliëntconsole in specifiek het vraagvenster te downloaden. Adobe raadt u aan deze optie te laten **[!UICONTROL No longer ask this question]** niet geselecteerd om ervoor te zorgen dat alle gebruikers worden gewaarschuwd wanneer een nieuwe versie van de console beschikbaar is.

Als u deze optie selecteert en ervoor kiest de nieuwste versie niet te downloaden, wordt geen andere gebruiker op de hoogte gesteld van nieuwe beschikbare versies.

Als de optie is geselecteerd, kunt u deze aanwijzing opnieuw instellen. Alleen systeembeheerders die vertrouwd zijn met het bewerken van het Windows-register, moeten deze wijzigingen aanbrengen:

1. Registereditor openen met de **regedit** van de **[!UICONTROL Start > Run]** -menu.
1. Zoek het knooppunt en vouw het uit.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Verwijder de **confAdvisedUpgrade** item en sluit de Register-editor.
