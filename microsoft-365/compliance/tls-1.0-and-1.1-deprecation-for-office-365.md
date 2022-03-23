---
title: Deaktivering af TLS 1.0 og 1.1 for Microsoft 365
description: Beskrivelse af udrådning og deaktivering af TLS 1.0 og 1.1 for Microsoft 365.
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
ms.openlocfilehash: 3084232f267a1180425d2daa3fcd2ba2fbcbd063
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588654"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Deaktivering af TLS 1.0 og 1.1 for Microsoft 365

> [!IMPORTANT]
> Vi har midlertidigt standset deaktivering af TLS 1.0 og 1.1 for kommercielle kunder på grund af COVID-19. Efterhånden som forsyningskæder er blevet justeret, og visse lande åbner op igen, genstartede vi udrulningen af TLS 1.2 d. 15. oktober 2020. Udrulningen fortsætter i løbet af de følgende uger og måneder.

Pr. 31. oktober 2018 frarådes protokollerne Transport Layer Security (TLS) 1.0 og 1.1 for Microsoft 365-tjenesten. Effekten for slutbrugere er minimal. Denne ændring er blevet offentliggjort i over to år med den første offentlige bekendtgørelse, der blev offentliggjort i december 2017. Denne artikel er kun beregnet til at dække den lokale Office 365-klient i forhold til Office 365-tjenesten, men kan også gælde for lokale TLS-problemer med Office og Office Online Server/Office Web Apps.

For SharePoint og OneDrive skal du opdatere og konfigurere .NET til at understøtte TLS 1.2. Du kan få mere at [vide under Sådan aktiverer du TLS 1.2 på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Office 365 og TLS

Klientklienten Office af Windows (WINHTTP) til at sende og modtage trafik via TLS-protokoller. Den Office klient kan bruge TLS 1.2, hvis webtjenesten på den lokale computer kan bruge TLS 1.2. Alle Office klienter kan bruge TLS-protokoller, da TLS og SSL-protokoller er en del af operativsystemet og ikke er specifikke for Office klient.

### <a name="on-windows-8-and-later-versions"></a>I Windows 8 og nyere versioner

Som standard er protokollerne TLS 1.2 og 1.1 tilgængelige, hvis ingen netværksenheder er konfigureret til at afvise TLS 1.2-trafik.

### <a name="on-windows-7"></a>Den Windows 7

Protokollerne TLS 1.1 og 1.2 er ikke tilgængelige uden [kb 3140245](https://support.microsoft.com/help/3140245) opdateringen. Opdateringen løser dette problem og tilføjer følgende undernøgle i registreringsdatabasen:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 brugere, der ikke har denne opdatering, påvirkes pr. 31. oktober 2018. [KB 3140245 indeholder](https://support.microsoft.com/help/3140245) oplysninger om, hvordan du ændrer WINHTTP-indstillinger for at aktivere TLS-protokoller.

#### <a name="more-information"></a>Flere oplysninger

Værdien af **registreringsdatabasenøglen DefaultSecureProto hele registreringsdatabase** , som kb-artiklen beskriver, bestemmer, hvilke netværksprotokoller der kan bruges:

|DefaultSecureProtoskildpaddes Value|Protokol aktiveret|
|-|-|
|0x00000008|Aktivér SSL 2.0 som standard|
|0x00000020|Aktivér SSL 3.0 som standard|
|0x00000080|Aktivér TLS 1.0 som standard|
|0x00000200|Aktivér TLS 1.1 som standard|
|0x00000800|Aktivér TLS 1.2 som standard|

## <a name="office-clients-and-tls-registry-keys"></a>Office klienter og TLS-registreringsdatabasenøgler

Du kan se [KB 4057306 forberedelse til obligatorisk brug af TLS 1,2 i Office 365](https://support.microsoft.com/help/4057306). Dette er en generel artikel til it-administratorer, og det er officiel dokumentation om TLS 1.2-ændringen.

Følgende tabel viser de relevante registreringsdatabasenøgleværdier i Office 365 efter 31. oktober 2018.

|Aktiverede protokoller for Office 365 efter d. 31. oktober 2018|Hexadecimal værdi|
|-|-|
|TLS 1.0 + 1.1 + 1,2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> Brug ikke protokollerne SSL 2.0 og 3.0, som også kan angives ved hjælp af **defaultSecureProtoskildpaddes-nøglen** . SSL 2.0 og 3.0 betragtes som forældede og usikre protokoller. Den bedste fremgangsmåde er at afslutte brugen af SSL 2.0 og SSL 3.0, selvom beslutningen om at gøre dette i sidste ende afhænger af, hvad der bedst opfylder dine produktbehov. Du kan finde flere oplysninger om ssl 3.0-sårbarheder i [KB 3009008](https://support.microsoft.com/help/3009008).

Du kan bruge standarddataberegneren Windows Programmer-tilstand til at konfigurere de samme referenceværdier for registreringsdatabasenøgler. Du kan finde flere oplysninger i [KB 3140245 Update for at aktivere TLS 1.1 og TLS 1.2](https://support.microsoft.com/help/3140245) som en sikker standardprotokoller i WinHTTP Windows.

Uanset om Windows 7-opdateringen ([KB 3140245](https://support.microsoft.com/help/3140245)) er installeret eller ej, er DefaultSecureProtoinstalls-undernøglen i registreringsdatabasen ikke til stede og skal tilføjes manuelt eller via et gruppepolitikobjekt. Det vil sige, medmindre du er nødt til at tilpasse, hvilke sikre protokoller der er aktiveret eller begrænset, er denne nøgle ikke påkrævet. Du skal kun bruge Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)) opdatering.

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>Opdatere og konfigurere .NET Framework til at understøtte TLS 1.2

Du skal opdatere programmer, der kalder Microsoft 365 API'er over TLS 1.0 eller TLS 1.1 for at bruge TLS 1.2. .NET 4.5 bruger som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se Sådan aktiveres [TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Flere oplysninger

Få mere at vide under [Forberedelse til obligatorisk brug af TLS 1.2 Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>Referencer

Følgende ressourcer indeholder en vejledning til at sikre, at dine kunder bruger TLS 1.2 eller en nyere version og til at deaktivere TLS 1.0 og 1.1:

- For Windows 7 klienter, der opretter forbindelse til Office 365, skal du sørge for, at TLS 1.2 er den sikre standardprotokol i Winhttp Windows. Få mere at vide under KB 3140245 – Opdater for at aktivere [TLS 1.1 og TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) som standard sikre protokoller i WinHTTP Windows.
- Hvis du vil håndtere svag TLS-brug ved at fjerne afhængighederne TLS 1.0 og 1.1, skal du se [understøttelse af TLS 1.2 hos Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Den nye IIS-funktionalitet](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) gør det nemmere at finde klienter på [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) og [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), der opretter forbindelse til tjenesten ved hjælp af svage sikkerhedsprotokoller.
- Få mere at vide om, [hvordan du løser problemet TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- Du kan finde generelle oplysninger om vores tilgang til sikkerhed i [Office 365 Center for sikkerhed og sikkerhed](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Forberedelse til udrådning af TLS 1.0/1.1 – Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS-vejledning, del 1: Blive klar til TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS-vejledning Del 2: Aktivering af TLS 1.2 og identificering af klienter, der ikke bruger det](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS-vejledning Del 3: De slår TLS 1.0/1.1 fra](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)

