---
title: Deaktivering af TLS 1.0 og 1.1 for Microsoft 365
description: Beskriver TLS 1.0 og 1.1-udfasning og deaktivering for Microsoft 365.
author: workshay
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: fasqiu
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 519b2c025236be49f2f1c96e098c841f789c079b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759661"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Deaktivering af TLS 1.0 og 1.1 for Microsoft 365

> [!IMPORTANT]
> Vi har midlertidigt stoppet deaktivering af TLS 1.0 og 1.1 for erhvervskunder på grund af COVID-19. Da forsyningskæderne er blevet justeret og visse lande åbner op igen, genstartede vi TLS 1.2 håndhævelsesudrulningen den 15. oktober 2020. Udrulningen fortsætter i løbet af de følgende uger og måneder.

Fra og med den 31. oktober 2018 frarådes protokollerne TLS (Transport Layer Security) 1.0 og 1.1 for Microsoft 365-tjenesten. Effekten for slutbrugere er minimal. Denne ændring er blevet offentliggjort i over to år, med den første offentlige meddelelse fra december 2017. Denne artikel er kun beregnet til at dække den Office 365 lokale klient i forbindelse med Office 365-tjenesten, men kan også anvendes på TLS-problemer i det lokale miljø med Office og Office Online Server/Office Web Apps.

Hvis du vil have SharePoint og OneDrive, skal du opdatere og konfigurere .NET til at understøtte TLS 1.2. Du kan få flere oplysninger under [Sådan aktiverer du TLS 1.2 på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>oversigt over Office 365 og TLS

Den Office klient er afhængig af WINHTTP (Windows webtjeneste) til at sende og modtage trafik via TLS-protokoller. Den Office klient kan bruge TLS 1.2, hvis webtjenesten på den lokale computer kan bruge TLS 1.2. Alle Office klienter kan bruge TLS-protokoller, da TLS- og SSL-protokoller er en del af operativsystemet og ikke specifikke for den Office klient.

### <a name="on-windows-8-and-later-versions"></a>På Windows 8 og nyere versioner

Protokollerne TLS 1.2 og 1.1 er som standard tilgængelige, hvis ingen netværksenheder er konfigureret til at afvise TLS 1.2-trafik.

### <a name="on-windows-7"></a>Den Windows 7

TLS 1.1- og 1.2-protokoller er ikke tilgængelige uden [kb-3140245-opdateringen](https://support.microsoft.com/help/3140245) . Opdateringen løser dette problem og tilføjer følgende undernøgle i registreringsdatabasen:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 brugere, der ikke har denne opdatering, påvirkes fra den 31. oktober 2018. [KB 3140245](https://support.microsoft.com/help/3140245) indeholder oplysninger om, hvordan du ændrer WINHTTP-indstillinger for at aktivere TLS-protokoller.

#### <a name="more-information"></a>Flere oplysninger

Værdien af registreringsdatabasenøglen **DefaultSecureProtocols, som beskrives** i KB-artiklen, bestemmer, hvilke netværksprotokoller der kan bruges:

|Standardværdi forSecureProtocols|Protokollen er aktiveret|
|---|---|
|0x00000008|Aktivér SSL 2.0 som standard|
|0x00000020|Aktivér SSL 3.0 som standard|
|0x00000080|Aktivér TLS 1.0 som standard|
|0x00000200|Aktivér TLS 1.1 som standard|
|0x00000800|Aktivér TLS 1.2 som standard|

## <a name="office-clients-and-tls-registry-keys"></a>Office klienter og TLS-registreringsdatabasenøgler

Du kan se [KB 4057306 Forberedelse til obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306). Dette er en generel artikel for it-administratorer, og det er den officielle dokumentation om TLS 1.2-ændringen.

I følgende tabel vises de relevante registreringsdatabasenøgleværdier i Office 365 klienter efter den 31. oktober 2018.

|Aktiverede protokoller for Office 365 efter 31. oktober 2018|Hexadecimal værdi|
|---|---|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> Brug ikke protokollerne SSL 2.0 og 3.0, som også kan angives ved hjælp af nøglen **DefaultSecureProtocols** . SSL 2.0 og 3.0 betragtes som forældede og usikre protokoller. Bedste praksis er at afslutte brugen af SSL 2.0 og SSL 3.0, selvom beslutningen om at gøre dette i sidste ende afhænger af, hvad der bedst opfylder dine produktbehov. Du kan finde flere oplysninger om sikkerhedsrisici i SSL 3.0 [i KB 3009008](https://support.microsoft.com/help/3009008).

Du kan bruge standard-Windows Calculator i programmer-tilstand til at konfigurere de samme referencenøgleværdier i registreringsdatabasen. Du kan få flere oplysninger under [KB 3140245-opdatering, der aktiverer TLS 1.1 og TLS 1.2 som standard sikre protokoller i WinHTTP i Windows](https://support.microsoft.com/help/3140245).

Uanset om Windows 7-opdateringen ([KB 3140245](https://support.microsoft.com/help/3140245)) er installeret eller ej, er undernøglen DefaultSecureProtocols i registreringsdatabasen ikke til stede og skal tilføjes manuelt eller via et gruppepolitikobjekt. Medmindre du skal tilpasse, hvilke sikre protokoller der er aktiveret eller begrænset, er denne nøgle ikke påkrævet. Du skal kun bruge opdateringen Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>Opdater og konfigurer .NET Framework til at understøtte TLS 1.2

Du skal opdatere programmer, der kalder Microsoft 365 API'er over TLS 1.0 eller TLS 1.1, for at bruge TLS 1.2. .NET 4.5 er som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se [Sådan aktiverer du TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Flere oplysninger

Du kan finde flere oplysninger under [Forberedelse til obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>Referencer

Følgende ressourcer indeholder en vejledning til at sikre, at dine klienter bruger TLS 1.2 eller en nyere version og til at deaktivere TLS 1.0 og 1.1:

- For Windows 7 klienter, der opretter forbindelse til Office 365, skal du sørge for, at TLS 1.2 er standardsikker protokol i WinHTTP i Windows. Du kan få flere oplysninger under [KB 3140245 – Opdatering til aktivering af TLS 1.1 og TLS 1.2 som standardsikre protokoller i WinHTTP i Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- Hvis du vil håndtere svag brug af TLS ved at fjerne TLS 1.0- og 1.1-afhængigheder, skal [du se TLS 1.2-support hos Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Ny IIS-funktionalitet](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) gør det nemmere at finde klienter på [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) og [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), der opretter forbindelse til tjenesten ved hjælp af svage sikkerhedsprotokoller.
- Få flere oplysninger om, hvordan du [løser TLS 1.0-problemet](https://www.microsoft.com/download/details.aspx?id=55266).
- Du kan få generelle oplysninger om vores tilgang til sikkerhed ved at gå til [Office 365 Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Forberedelse til TLS 1.0/1.1 Udfasning – Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS-vejledning, del 1: Klar til TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS-vejledning, del 2: Aktivering af TLS 1.2 og identificering af klienter, der ikke bruger den](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS-vejledning, del 3: Deaktiver TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 i Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
