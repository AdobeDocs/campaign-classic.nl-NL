---
solution: Campaign Classic
product: campaign
title: Netwerk, database en SSL/TLS
description: Leer meer over netwerk, gegevensbestand, en SSL/TLS configuratie beste praktijken.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 2%

---


# Netwerk, database en SSL/TLS {#network-database}

## Netwerkconfiguratie

Een zeer belangrijk ding om te controleren wanneer het opstellen van een on-premise type van architectuur is de [voorzien van een netwerkconfiguratie](../../installation/using/network-configuration.md). Zorg ervoor dat de Tomcat-server NIET rechtstreeks toegankelijk is buiten de server:

* Sluit de Tomcat-poort (8080) op externe IP&#39;s (moet werken op localhost)
* Wijs de standaard HTTP-poort (80) niet toe aan de Tomcat-poort (8080)

Gebruik, indien mogelijk, een beveiligd kanaal: POP3S in plaats van POP3 (of POP3 via TLS).

## Database

Het is absoluut noodzakelijk dat u de beveiliging van de database-engine volgt.

### SSL/TLS-configuratie*

U kunt openssl gebruiken om het certificaat te controleren. Om actieve ciphers te controleren, kunt u nmap gebruiken:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

U kunt ook een [slyze](https://github.com/nabla-c0d3/sslyze/releases) pythonscript gebruiken dat beide doet.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
