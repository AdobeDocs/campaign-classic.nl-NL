---
product: campaign
title: Netwerk, database en SSL/TLS
description: Meer informatie over best practices voor netwerken, databases en SSL/TLS-configuraties
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

---

# Netwerk, database en SSL/TLS {#network-database}

## Netwerkconfiguratie

Een zeer belangrijk ding om te controleren wanneer het opstellen van een on-premise type van architectuur is de [ voorzien van een netwerkconfiguratie ](../../installation/using/network-configuration.md). Zorg ervoor dat de Tomcat-server NIET rechtstreeks toegankelijk is buiten de server:

* Sluit de Tomcat-poort (8080) op externe IP&#39;s (moet werken op localhost)
* Wijs de standaard HTTP-poort (80) niet toe aan Tomcat (8080)

Gebruik indien mogelijk een beveiligd kanaal: POP3S in plaats van POP3 (of POP3 via TLS).

## Database

U moet de best practices voor de beveiliging van uw database-engine toepassen.

## SSL/TLS-configuratie

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

U kunt ook een [ schuine ](https://github.com/nabla-c0d3/sslyze/releases) pythonmanuscript gebruiken dat allebei doet.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
