---
product: campaign
title: Tomcat-versie zoeken in Adobe Campaign
description: Leer hoe u de huidige versie van de ingesloten Tomcat-webservlet kunt achterhalen die in een instantie van Adobe Campaign wordt gebruikt
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Tomcat-versie zoeken{#locate-tomcat-version}

Adobe Campaign gebruikt een **ingesloten webservlet genaamd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, SOAP vraag, en anderen) te verwerken. Er is vaak een externe webserver (meestal IIS of Apache) voor deze server voor naar buiten gerichte Adobe Campaign-instanties.

Volg de onderstaande procedure om de exacte versie van Tomcat te achterhalen die in een **Campaign Classic on-premise instantie** om problemen op te lossen.

## Tomcat gebruikt in Adobe Campaign

Tomcat wordt uitgevoerd op Java en vereist dat JDK wordt geïnstalleerd. Zie voor meer informatie Java Development Kit (JDK) in het dialoogvenster [Matrix voor cameracompatibiliteit](../../rn/using/compatibility-matrix.md) sectie.

De Tomcat die in Adobe Campaign wordt gebruikt, is een aangepaste ingesloten versie die niet alle functies van de volledige algemeen beschikbare versie van Tomcat gebruikt en die mogelijk niet alle kwetsbaarheden van de volledige versie ondervindt. De Tomcat mag ook niet worden blootgesteld aan het externe internet, en Adobe Campaign-instanties die worden weergegeven, moeten een externe webserver hebben (IIS, Apache, enz.) voor de Tomcat om hem te beschermen.

Nieuwe of bijgewerkte versies van de ingesloten versies van Tomcat worden alleen vrijgegeven met nieuwe builds van Adobe Campaign zelf en niet als afzonderlijke patches buiten de Adobe Campaign-builds.

>[!AVAILABILITY]
>
>
> Vanaf Campagne v7.4.1 is Tomcat 10.1 de standaardversie.
>

## Hoe te om van de versie van ingebedde Tomcat de plaats te bepalen

Voer de onderstaande stappen uit om de versie van ingesloten Tomcat in een exemplaar van Adobe Campaign te zoeken.

>[!NOTE]
>
>U moet toegang hebben tot de bestanden op de Adobe Campaign-server die u moet controleren. De hieronder beschreven procedure is alleen van toepassing op **hostingmodellen op locatie**.

1. Ga naar de *\tomcat-11\lib* submap in de installatiemap van Adobe Campaign (bijvoorbeeld *C:\Program Bestanden\ [Installatiemap]* in Windows, of */usr/local/neolane/nl6* in Linux).

1. Het bestand kopiëren *catalina.jar* naar een externe tijdelijke map (bijvoorbeeld uw bureaublad) en wijzig de naam van de extensie van .jar in .zip.

1. Pak het gekopieerde bestand uit. Dit resulteert in veel submappen en bestanden.

1. Open of lees in de uitgegane bestanden/mappen het volgende ingesloten bestand met een teksteditor: *org/apache/catalina/util/ServerInfo.properties*. Mogelijk moet u de extensie .txt toevoegen om het openen met een teksteditor te vergemakkelijken.

1. Als het bestand zich op een servercomputer bevindt, verwijdert u de tijdelijke bestanden die u hebt gemaakt.

Als voorbeeld *ServerInfo.properties* Het bestand voor Adobe Campaign bevat de volgende informatie die Tomcat v11.X aangeeft:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Zodra u de nauwkeurige versie van Tomcat kunt bepalen die in een bepaald geval wordt gebruikt, kan het u in het oplossen van problemen met betrekking tot Tomcat helpen.

>[!NOTE]
>
>De belangrijkste versie van het ingesloten Tomcat-bestand wordt alleen bijgewerkt wanneer de belangrijkste versie van Adobe Campaign wordt gewijzigd (hoewel oudere versies mogelijk niet meer officieel worden ondersteund, kan de informatie nuttig zijn omdat sommige klanten deze versies mogelijk nog steeds uitvoeren).
>

