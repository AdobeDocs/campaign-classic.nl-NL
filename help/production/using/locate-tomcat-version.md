---
product: campaign
title: Tomcat-versie zoeken in Adobe Campaign
description: Leer hoe u de huidige versie van de ingesloten Tomcat-webservlet kunt achterhalen die in een exemplaar van Adobe Campaign wordt gebruikt.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Tomcat-versie zoeken{#locate-tomcat-version}

![](../../assets/v7-only.svg)

Adobe Campaign gebruikt een **ingesloten webservlet genaamd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, de vraag van de ZEEP, en anderen) te verwerken. Voor alle naar buiten gerichte Adobe Campaign-instanties is er vaak een externe webserver (gewoonlijk IIS of Apache) aanwezig.

Volg de onderstaande procedure om de exacte versie van Tomcat te achterhalen die in een **Campaign Classic-instantie op locatie** om problemen op te lossen.

## Tomcat gebruikt in Adobe Campaign

Tomcat wordt uitgevoerd op Java en vereist dat JDK wordt geïnstalleerd. Voor meer informatie, zie de Uitrusting van de Ontwikkeling van Java (JDK) in [Matrix voor cameracompatibiliteit](../../rn/using/compatibility-matrix.md) sectie.

De Tomcat die in Adobe Campaign wordt gebruikt, is een aangepaste ingesloten versie die niet alle functies van de volledige algemeen beschikbare versie van Tomcat gebruikt en die mogelijk niet alle kwetsbaarheden van de volledige versie ondervindt. De Tomcat mag ook niet worden blootgesteld aan het externe internet, en Adobe Campaign-instanties die worden weergegeven, moeten een externe webserver hebben (IIS, Apache, enz.) voor de Tomcat om hem te beschermen.

Nieuwe of bijgewerkte versies van de ingesloten versies van Tomcat worden alleen vrijgegeven met nieuwe builds van Adobe Campaign zelf en niet als afzonderlijke patches buiten de Adobe Campaign-builds.

## Hoe te om van de versie van ingebedde Tomcat de plaats te bepalen

Voer de onderstaande stappen uit om de versie van ingesloten Tomcat in een exemplaar van Adobe Campaign te zoeken.

>[!NOTE]
>
>U moet toegang hebben tot de bestanden op de Adobe Campaign-server die u moet controleren. De hieronder beschreven procedure is alleen van toepassing op: **hostingmodellen op locatie**.

1. Ga naar de *\tomcat-7\lib* submap in de installatiemap van Adobe Campaign (bijvoorbeeld *C:\Program Files\ [Installatiemap]* in Windows, of */usr/local/neolane/nl6* in Linux).

   Als u met Tomcat v6 een oudere versie van Adobe Campaign gebruikt, kunt u *\tomcat-6\lib*.

1. Het bestand kopiëren *catalina.jar* naar een externe tijdelijke map (bijvoorbeeld uw bureaublad) en wijzig de naam van de extensie van .jar in .zip.

1. Pak het gekopieerde bestand uit. Dit resulteert in veel submappen en bestanden.

1. Open of lees in de uitgegane bestanden/mappen het volgende ingesloten bestand met een teksteditor: *org/apache/catalina/util/ServerInfo.properties*. Mogelijk moet u de extensie .txt toevoegen om het openen met een teksteditor te vergemakkelijken.

1. Als het bestand zich op een servercomputer bevindt, verwijdert u de tijdelijke bestanden die u hebt gemaakt.

Als voorbeeld *ServerInfo.properties* Het bestand voor Adobe Campaign bevat de volgende informatie, met vermelding van Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

Zodra u de nauwkeurige versie van Tomcat kunt bepalen die in een bepaald geval wordt gebruikt, kan het u in het oplossen van problemen met betrekking tot Tomcat helpen.

>[!NOTE]
>
>De belangrijkste versie van het ingesloten Tomcat-bestand wordt alleen bijgewerkt wanneer de belangrijkste versie van Adobe Campaign wordt gewijzigd (hoewel oudere versies mogelijk niet meer officieel worden ondersteund, kan de informatie nuttig zijn omdat sommige klanten deze versies mogelijk nog steeds uitvoeren).
>
>Adobe Campaign v6.02 gebruikt bijvoorbeeld altijd Tomcat v6.x.
