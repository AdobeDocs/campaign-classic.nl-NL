---
solution: Campaign Classic
product: campaign
title: Configuratie van de instellingen voor de levering van campagnes
description: Leer hoe u instellingen voor de levering van campagnes configureert
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# Leveringsinstellingen configureren {#delivery-settings}

De leveringsparameters moeten worden geconfigureerd in de map **serverConf.xml**.

* **DNS-configuratie**: specificeer het leveringsdomein en de IP adressen (of gastheer) van de DNS servers die worden gebruikt om aan MX-type DNS vragen te antwoorden die door de MTA module van de  **`<dnsconfig>`** vanaf worden gemaakt.

   >[!NOTE]
   >
   >De **nameServers** parameter is essentieel voor een installatie in Vensters. Voor een installatie in Linux, moet het leeg worden verlaten.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Afhankelijk van uw behoeften en instellingen kunt u ook de volgende configuraties uitvoeren: configureer een [SMTP relais](#smtp-relay), pas het aantal [MTA kindprocessen](#mta-child-processes), [Beheer uitgaand verkeer SMTP](#managing-outbound-smtp-traffic-with-affinities) aan.

## SMTP-relais {#smtp-relay}

De module MTA doet dienst als inheemse agent van de postoverdracht voor uitzending SMTP (haven 25).

Het is echter mogelijk deze te vervangen door een relaisserver als dit voor uw beveiligingsbeleid is vereist. In dat geval, zal de globale productie relais zijn één (op voorwaarde dat de productie van de relaisserver aan Adobe Campaign minder is).

In dit geval, worden deze parameters geplaatst door de server SMTP in **`<relay>`** sectie te vormen. U moet het IP adres (of de gastheer) van de server specificeren SMTP die wordt gebruikt om post en zijn bijbehorende haven (25 door gebrek) over te brengen.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Deze werkende wijze impliceert ernstige beperkingen op leveringen, aangezien het de productie wegens de intrinsieke prestaties van de relaisserver (latentie, bandbreedte...) kan zeer verminderen. Bovendien zal de capaciteit om synchrone leveringsfouten (die door het analyseren van verkeer SMTP worden ontdekt) te kwalificeren beperkt zijn, en het verzenden zal niet mogelijk zijn als de relaisserver niet beschikbaar is.

## MTA onderliggende processen {#mta-child-processes}

Het is mogelijk om het aantal kindprocessen (maxSpareServers door gebrek 2) te controleren om uitzendingsprestaties volgens de macht van cpu van de servers en de beschikbare netwerkmiddelen te optimaliseren. Deze configuratie moet in de **`<master>`** sectie van configuratie MTA op elke individuele computer worden gemaakt.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Zie ook [Optimalisatie voor verzenden via e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

## Beheer uitgaand verkeer SMTP met affiniteiten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>De affiniteitsconfiguratie moet consistent zijn van de ene server naar de andere. Wij adviseren dat u Adobe voor affiniteitsconfiguratie contacteert, aangezien de configuratieveranderingen op alle toepassingsservers zouden moeten worden herhaald die MTA in werking stellen.

U kunt uitgaand verkeer SMTP door affiniteiten met IP adressen verbeteren.

Hiervoor voert u de volgende stappen uit:

1. Voer de affiniteiten in de sectie **`<ipaffinity>`** van het bestand **serverConf.xml** in.

   Een affiniteit kan verschillende namen hebben: om hen te scheiden, gebruik **;** karakter.

   Voorbeeld:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Raadpleeg het bestand **serverConf.xml** om de relevante parameters weer te geven.

1. Als u affiniteitselectie wilt inschakelen in de vervolgkeuzelijsten, moet u de affiniteitsnaam of -namen toevoegen in de **IPAffinity**-opsomming.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Opsommingen worden beschreven in [dit document](../../platform/using/managing-enumerations.md).

   Vervolgens kunt u de affiniteit selecteren die u wilt gebruiken, zoals hieronder voor typologieën wordt getoond:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >U kunt ook naar [Configuratie leveringsserver](../../installation/using/email-deliverability.md#delivery-server-configuration) verwijzen.

**Verwante onderwerpen**
* [Technische e-mailconfiguraties](email-deliverability.md)
* [MX-servers gebruiken met campagne](using-mx-servers.md)
* [Bcc van e-mail configureren](email-archiving.md)
