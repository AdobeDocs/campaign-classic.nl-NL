---
title: Campagne-interface bijwerken na IMS-migratie
description: Meer informatie over het activeren van de Adobe Identity Management System Migration Interface-effecten
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# Campagne-interface bijwerken na IMS-migratie {#impact-ims-migration}

Als u eenmaal [Uw technische operatoren voor campagne zijn gemigreerd naar de Developer Console](ims-migration.md) en [overgang naar IMS voor verificatie van eindgebruikers](migrate-users-to-ims.md), de laatste stap bestaat uit het inschakelen van de gebruikersinterface- en API-beperkingen om opties en mogelijkheden te verwijderen die specifiek zijn voor native verificatie. Deze update is beschikbaar vanaf Campagne v7.4.1.

## IMS-beperkingen inschakelen {#ims-restrictions}

Als u de migratie naar IMS (Adobe Identify Management System) wilt voltooien, moet u het maken van nieuwe native gebruikers, de native gebruikersaanmelding en de API-toegang voor native operatoren blokkeren. Uw omgeving wordt dan beveiligd en gestandaardiseerd.

Als Beheerde Cloud Service/Gehoste gebruiker, contacteer Adobe om deze beperking, en bijbehorende updates in het productgebruikersinterface toe te laten.

Voer als gebruiker op locatie/hybride de de volgende stappen uit:

1. Bladeren naar de `<imsConfig>` sectie van uw dossier van de instantieconfiguratie.
1. Als u de gebruikersinterface-beperkingen wilt inschakelen, werkt u de `nonIMSOperatorMgmtInClientConsoleRestricted` optie, binnen de `nonIMSOperatorMgmtInClientConsole` element, naar `true`, zoals hieronder:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Als u de API-beperkingen wilt inschakelen, werkt u de `disableAPI` optie, binnen de `nonIMSAuthnAPI` element, naar `true`, zoals hieronder:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Houd er rekening mee dat sommige operatoren verbinding mogen maken met Adobe Campaign via een native verificatie. Deze technische operatoren zijn standaard ingeschakeld en mogen niet worden gewijzigd. Om deze uitzondering toe te staan, worden deze technische operatoren standaard toegevoegd aan de allow-list. U kunt deze lijst vinden in het dialoogvenster `<imsConfig>` sectie van uw dossier van de instantieconfiguratie, in `allowOperator` in het dialoogvenster `nonIMSAuthnAPI` element.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Als u een exploitant aan de lijst van gewenste personen moet toevoegen, voeg een nieuwe toe `allowOperator` -element met de naam van de operator. Als u bijvoorbeeld een nieuwe operator met de naam wilt toevoegen `test`Deze sectie als volgt bijwerken:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## De gevolgen in het gebruikersinterface {#ims-impacts}

Nadat de migratie is voltooid en de beperkingen zijn toegepast zoals hieronder wordt beschreven, worden de volgende wijzigingen toegepast op het product en de gebruikersinterface.

### Exploitatiebeheer {#manage-admin}

U kunt vanaf de clientconsole geen operatoren met native verificatie meer maken, bewerken, bijwerken of verwijderen.

Als gevolg hiervan zijn deze handelingen uitgeschakeld in de clientconsole.

Het beheer van operatoren is gecentraliseerd in de Adobe Admin Console en de volgende taken worden nu uitsluitend via deze console beheerd. Leer hoe u gebruikers kunt maken en machtigingen kunt toewijzen in [Campagne v8-documentatie](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Niet-beschikbare opties {#unavailable-migration}

Na de migratie zijn de volgende taken niet meer beschikbaar in de clientconsole:

* Gebruik de [Geselecteerde lijnen samenvoegen, optie](../../platform/using/updating-data.md#merge-data) om operatoren samen te voegen.

* Werk de volgende velden voor uw operatoren bij:
   * Naam
   * Wachtwoord
   * Label
   * Email

* [Wachtwoord voor campagne opnieuw instellen](../../production/using/lost-password.md)

* De XML-bron van de operatoren bewerken

* Dubbele operatoren.


>[!MORELIKETHIS]
>
>* [Migratie van eindgebruikers naar IMS](migrate-users-to-ims.md)
>* [Migratie van technische operatoren naar Adobe Developer-console](ims-migration.md)
>* [Opmerkingen bij de nieuwste release van Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Wat is Adobe Identity Management System (IMS)](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"}

