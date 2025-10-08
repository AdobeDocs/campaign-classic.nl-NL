---
product: campaign
title: Configuratie van de instellingen voor de levering van campagnes
description: Leer hoe u instellingen voor de levering van campagnes configureert
feature: Installation, Channel Configuration
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 4%

---

# Leveringsinstellingen configureren {#delivery-settings}



De leveringsparameters moeten in de {**omslag worden gevormd 0} serverConf.xml.**

* **DNS configuratie**: specificeer het leveringsdomein en de IP adressen (of gastheer) van de DNS servers die worden gebruikt om aan MX-type DNS vragen te antwoorden die door de module MTA van **`<dnsconfig>`** worden gemaakt.

  >[!NOTE]
  >
  >De **nameServers** parameter is essentieel voor een installatie in Vensters. Voor een installatie in Linux, moet het leeg worden verlaten.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

U kunt de volgende configuraties afhankelijk van uw behoeften en montages ook uitvoeren: vorm het relais van a [&#x200B; SMTP &#x200B;](#smtp-relay), pas het aantal [&#x200B; MTA kindprocessen &#x200B;](#mta-child-processes) aan, [&#x200B; beheer uitgaand verkeer SMTP &#x200B;](#managing-outbound-smtp-traffic-with-affinities).

## SMTP-relay {#smtp-relay}

De module MTA doet dienst als inheemse agent van de postoverdracht voor uitzending SMTP (haven 25).

Het is echter mogelijk deze te vervangen door een relaisserver als dit voor uw beveiligingsbeleid is vereist. In dat geval, zal de globale productie relais zijn één (op voorwaarde dat de productie van de relaisserver aan Adobe Campaign minder is).

In dit geval worden deze parameters ingesteld door de SMTP-server in de sectie **`<relay>`** te configureren. U moet het IP adres (of de gastheer) van de server specificeren SMTP die wordt gebruikt om post en zijn bijbehorende haven (25 door gebrek) over te brengen.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Deze werkende wijze impliceert ernstige beperkingen op leveringen, aangezien het de productie wegens de intrinsieke prestaties van de relaisserver (latentie, bandbreedte...) kan zeer verminderen. Bovendien zal de capaciteit om synchrone leveringsfouten (die door het analyseren van verkeer SMTP worden ontdekt) te kwalificeren beperkt zijn, en het verzenden zal niet mogelijk zijn als de relaisserver niet beschikbaar is.

## MTA onderliggende processen {#mta-child-processes}

Het is mogelijk om het aantal onderliggende processen (maxSpareServers door gebrek 2) te controleren om uitzendprestaties volgens de macht van CPU van de servers en de beschikbare netwerkmiddelen te optimaliseren. Deze configuratie moet in de **`<master>`** sectie van configuratie MTA op elke individuele computer worden gemaakt.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Verwijs ook naar [&#x200B; E-mail die optimalisering verzenden &#x200B;](../../installation/using/email-deliverability.md#email-sending-optimization).

## Beheer uitgaand verkeer SMTP met affiniteiten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>De affiniteitsconfiguratie moet consistent zijn van de ene server naar de andere. Wij adviseren dat u Adobe voor affiniteitsconfiguratie contacteert, aangezien de configuratieveranderingen op alle toepassingsservers zouden moeten worden herhaald die MTA in werking stellen.

U kunt uitgaand verkeer SMTP door affiniteiten met IP adressen verbeteren.

Hiervoor voert u de volgende stappen uit:

1. Ga de affiniteiten in de **`<ipaffinity>`** sectie van het **serverConf.xml** dossier in.

   Een affiniteit kan verschillende namen hebben: als u ze wilt scheiden, gebruikt u het teken **;** .

   Voorbeeld:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Om de relevante parameters te bekijken, verwijs naar het {**dossier 0} serverConf.xml.**

1. Om affiniteitselectie in de drop-down lijsten toe te laten, moet u de affiniteitsnaam (s) in de **IPAffinity** opsomming toevoegen.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Leer meer hoe te **met opsommingen** in [&#x200B; Adobe Campaign v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank} werken.


   Vervolgens kunt u de affiniteit selecteren die u wilt gebruiken, zoals hieronder voor typologieën wordt getoond:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >U kunt ook naar [&#x200B; de serverconfiguratie van de Levering &#x200B;](../../installation/using/email-deliverability.md#delivery-server-configuration) verwijzen.

**Verwante onderwerpen**
* [Technische e-mailconfiguraties](email-deliverability.md)
* [MX-servers gebruiken met Campaign](using-mx-servers.md)
* [Bcc van e-mail configureren](email-archiving.md)
