---
product: campaign
title: Netwerk, database en SSL/TLS
description: Meer informatie over best practices voor netwerken, databases en SSL/TLS-configuraties
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 9%

---

# Netwerk, database en SSL/TLS {#network-database}



## Netwerkconfiguratie

Een zeer belangrijk ding om te controleren wanneer het opstellen van een on-premisse type van architectuur is [netwerkconfiguratie](../../installation/using/network-configuration.md). Zorg ervoor dat de Tomcat-server NIET rechtstreeks toegankelijk is buiten de server:

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

U kunt ook een [slyze](https://github.com/nabla-c0d3/sslyze/releases) pythonscript dat beide doet.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
