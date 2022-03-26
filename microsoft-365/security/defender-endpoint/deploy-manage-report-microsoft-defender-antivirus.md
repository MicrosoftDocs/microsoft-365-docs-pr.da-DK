---
title: Installér, administrer og rapportér om Microsoft Defender Antivirus
description: Du kan installere og administrere Microsoft Defender Antivirus med Intune, Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell eller WMI
keywords: installere, administrere, opdatere, beskytte, Microsoft Defender Antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1ce212bf01b8c464760192a4bbd6355498d19c3c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63595888"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Installér, administrer og rapportér om Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan installere, administrere og rapportere om Microsoft Defender Antivirus på flere forskellige måder.

Da Microsoft Defender Antivirus-klienten er installeret som en central del af Windows 10 og Windows 11, gælder traditionel installation af en klient til dine slutpunkter ikke.

Men i de fleste tilfælde skal du stadig aktivere beskyttelsestjenesten på dine slutpunkter med Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender til skyen eller Gruppepolitik-objekter, som er beskrevet i følgende tabel.

Du får også vist flere links til:

- Administration Microsoft Defender Antivirus beskyttelse, herunder administration af produkt- og beskyttelsesopdateringer
- Rapportering om Microsoft Defender Antivirus beskyttelse

> [!IMPORTANT]
> I de fleste tilfælde deaktiverer Windows 10 eller Windows 11 Microsoft Defender Antivirus, hvis der findes et andet antivirusprodukt, der kører og er opdateret. Du skal deaktivere eller fjerne antivirusprodukter fra tredjepart, før Microsoft Defender Antivirus fungerer. Hvis du genaktiverer eller installerer antivirusprodukter fra tredjepart, deaktiverer Windows 10 eller Windows 11 automatisk Microsoft Defender Antivirus.

Værktøj|Installationsindstillinger (<a href="#fn2" id="ref2">2</a>)|Administrationsindstillinger (konfiguration og politik for hele netværket eller installation af grundlinje) ([3](#fn3))|Rapporteringsmuligheder
---|---|---|---
Microsoft Intune|[Tilføj indstillinger for slutpunktsbeskyttelse i Intune](/intune/endpoint-protection-configure)|[Konfigurer indstillinger for enhedsbegrænsning i Intune](/intune/device-restrictions-configure)| [Brug Intune-konsollen til at administrere enheder](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Brug [Endpoint Protection på webstedets systemrolle][] og [Endpoint Protection med brugerdefinerede klientindstillinger][]|Med [standard og tilpassede antimalwarepolitikker][] og [klientadministration][]|Med standardindstillingen [Konfigurationsstyring Overvågning arbejdsområde][] og [mailbeskeder][]
Gruppepolitik og Active Directory (domæne forbundet)|Brug et Gruppepolitik-objekt til at implementere konfigurationsændringer og sikre, Microsoft Defender Antivirus er aktiveret.|Brug Gruppepolitik-objekter (GPOs) til [Konfigurer opdateringsindstillinger for Microsoft Defender Antivirus][] og [Konfigurer Windows Defender funktioner][]|Slutpunktsrapportering er ikke tilgængelig med Gruppepolitik. Du kan oprette en liste over [Gruppepolitikker for at afgøre, om nogen indstillinger eller politikker ikke anvendes][]
PowerShell|Installer med Gruppepolitik, Microsoft Endpoint Configuration Manager eller manuelt på individuelle slutpunkter.|Brug de [Set-MpPreference] og [Update-MpSignature]-cmdlet'er, der er tilgængelige i Defender-modulet.|Brug de relevante [Get- cmdlets, der er tilgængelige i Defender-modulet][]
Windows administrationsmiddel|Installer med Gruppepolitik, Microsoft Endpoint Configuration Manager eller manuelt på individuelle slutpunkter.|Brug [Angiv metoden for MSFT_MpPreference klasse][] og [Metoden Opdater for MSFT_MpSignature klasse][]|Brug klassen [MSFT_MpComputerStatus][] og hent metoden for tilknyttede klasser i [Windows Defender WMIv2 Provider][]
Microsoft Azure|Installér Microsoft Antimalware til Azure i Azure-portalen ved hjælp Visual Studio konfiguration af virtuel maskine eller ved [hjælp Azure PowerShell cmdlet'er](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Du kan også [installere Endpoint-beskyttelse i Microsoft Defender for Cloud*](/azure/security-center/security-center-install-endpoint-protection)|Konfigurer [Microsoft Antimalware til virtuelle maskiner og skytjenester med Azure PowerShell cmdlet'er,](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) eller [brug kodeeksempler](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Brug [Microsoft Antimalware til virtuelle maskiner og skytjenester med Azure PowerShell cmdlet'er for](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) at aktivere overvågning. Du kan også gennemse brugsrapporter i Azure Active Directory for at bestemme mistænkelig aktivitet, herunder rapporten [Muligvis inficeret enheder][] og konfigurere et SIEM-værktøj til at rapportere om [Microsoft Defender Antivirus-begivenheder][] og tilføje dette værktøj som en app i AAD.

1. <span id="fn1" />Tilgængeligheden af nogle funktioner og funktioner, især relateret til skybaseret beskyttelse, varierer mellem Microsoft Endpoint Manager (Current Branch) og System Center 2012 Konfigurationsstyring. I dette bibliotek har vi fokuseret på Windows 10, Windows 11, Windows Server 2016 og Microsoft Endpoint Manager (Current Branch). Se [Brug Microsoft cloud-provided protection i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md) for en tabel, der beskriver de største forskelle. [(Gå tilbage til tabel)](#ref2)

2. <span id="fn2" />I Windows 10 og Windows 11 er Microsoft Defender Antivirus en komponent tilgængelig uden installation eller installation af en ekstra klient eller tjeneste. Det bliver automatisk aktiveret, når antivirusprodukter fra tredjeparter enten er fjernet eller forældede (undtagen Windows Server 2016). Traditionel installation er derfor ikke påkrævet. Installation her henviser til at sikre, Microsoft Defender Antivirus-komponenten er tilgængelig og aktiveret på slutpunkter eller servere. [(Gå tilbage til tabel)](#ref2)

3. <span id="fn3" />Konfiguration af funktioner og beskyttelse, herunder konfiguration af produkt- og beskyttelsesopdateringer, er yderligere beskrevet i afsnittet [Konfigurer Microsoft Defender Antivirus-funktioner](configure-notifications-microsoft-defender-antivirus.md) i dette bibliotek. [(Gå tilbage til tabel)](#ref2)

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
---|---
[Installér og aktivér Microsoft Defender Antivirus beskyttelse](deploy-microsoft-defender-antivirus.md) | Selvom klienten er installeret som en central del af Windows 10 eller Windows 11, og traditionel installation ikke gælder, skal du stadig aktivere klienten på dine slutpunkter med Microsoft Endpoint Configuration Manager, Microsoft Intune eller Gruppepolitik-objekter.
[Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md) | Der er to dele til opdatering Microsoft Defender Antivirus: opdatering af klienten på slutpunkter (produktopdateringer) og opdatering af Sikkerhedsintelligens (sikkerhedsopdateringer). Du kan opdatere sikkerhedsintelligens på flere forskellige måder ved hjælp Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell og WMI.
[Overvåg og rapportér om Microsoft Defender Antivirus beskyttelse](report-monitor-microsoft-defender-antivirus.md) | Du kan bruge Microsoft Intune, Microsoft Endpoint Configuration Manager, tilføjelsesprogrammet Overholdelse af opdatering til Microsoft Operations Management-pakken eller et SIEM-tredjepartsprodukt (ved at bruge Windows-hændelseslogfiler) til at overvåge beskyttelsesstatus og oprette rapporter om slutpunktsbeskyttelse.
