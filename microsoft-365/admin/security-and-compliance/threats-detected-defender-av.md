---
title: Trusler registreret af Microsoft Defender Antivirus
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Få mere at vide om, hvordan Microsoft Defender Antivirus beskytter dine Windows enheder mod softwaretrusler, f.eks. virus, malware og spyware.
ms.openlocfilehash: 47f6af2b91eed8096a685f8d3281f16fdc677331
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466300"
---
# <a name="overview-of-threat-protection-by-microsoft-defender-antivirus"></a>Oversigt over trusselsbeskyttelse fra Microsoft Defender Antivirus

Microsoft Defender Antivirus beskytter dine Windows enheder mod softwaretrusler, f.eks. virus, malware og spyware.

- Virus spredes typisk ved at vedhæfte deres kode til andre filer på din enhed eller dit netværk, og det kan medføre, at inficerede programmer fungerer forkert.
- Malware omfatter skadelige filer, programmer og kode, der kan forårsage skade og forstyrre normal brug af enheder. Malware kan også tillade uautoriseret adgang, bruge systemressourcer, stjæle adgangskoder og kontooplysninger, låse dig ud af din computer og bede om løsepenge og meget mere.
- Spyware indsamler data, f.eks. webbrowsingaktivitet, og sender dataene til fjernservere.
 
For at yde trusselsbeskyttelse bruger Microsoft Defender Antivirus flere metoder. Disse metoder omfatter skybaseret beskyttelse, beskyttelse i realtid og dedikerede beskyttelsesopdateringer.

- Cloudbaseret beskyttelse hjælper med at registrere og blokere nye og nye trusler næsten øjeblikkeligt.
- Ved altid at scanne bruges overvågning af fil- og procesadfærd og andre teknikker (også kendt som *beskyttelse i realtid*).
- Dedikerede beskyttelsesopdateringer er baseret på maskinel indlæring, analyse af mennesker og automatiseret analyse af big data og dybdegående forskning i trusselsresistens. 

Du kan få mere at vide om malware og Microsoft Defender Antivirus i følgende artikler: 

- [Om malware & andre trusler](/windows/security/threat-protection/intelligence/understanding-malware)
- [Sådan identificerer Microsoft malware og potentielt uønskede programmer](/windows/security/threat-protection/intelligence/criteria)
- [Næste generations beskyttelse i Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Hvad sker der, når der bruges en antivirusløsning, der ikke er fra Microsoft? 

Microsoft Defender Antivirus er en del af operativsystemet og er aktiveret på enheder, der kører Windows 10. Men hvis du bruger en antivirusløsning, der ikke er fra Microsoft, og du ikke bruger [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), går Microsoft Defender Antivirus automatisk i deaktiveret tilstand.  

I deaktiveret tilstand kan brugere og kunder stadig bruge Microsoft Defender Antivirus til planlagte scanninger eller on-demand-scanninger til at identificere trusler, men Microsoft Defender Antivirus vil ikke længere:

- bruges som standardprogram til antivirus.
- aktivt scanne filer for trusler.
- afhjælpe eller løse trusler.

Hvis du fjerner den antivirusløsning, der ikke er Microsoft, skifter Microsoft Defender Antivirus automatisk til aktiv tilstand for at beskytte dine Windows enheder mod trusler.

> [!TIP]
> - Hvis du bruger Microsoft 365, kan du overveje at bruge Microsoft Defender Antivirus som din primære antivirusløsning. Integration kan give bedre beskyttelse. Se [Bedre sammen: Microsoft Defender Antivirus og Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Sørg for at holde Microsoft Defender Antivirus opdateret, selvom du bruger en antivirusløsning, der ikke er fra Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>Hvad kan man forvente, når der registreres trusler?

Når der registreres trusler af Microsoft Defender Antivirus, sker følgende ting:

- Brugerne modtager [meddelelser i Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Registreringer er angivet i [appen Windows Sikkerhed](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) på siden **Beskyttelsesoversigt**.  
- Hvis du har [sikret dine Windows 10 enheder](../setup/secure-win-10-pcs.md) og [tilmeldt dem i Intune](/mem/intune/enrollment/windows-enrollment-methods), og din organisation har 800 eller færre enheder tilmeldt, kan du se trusselsregistreringer og indsigt i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> på siden **Trusler og antivirus**, som du kan få adgang til fra **siden Microsoft Defender Antivirus** kort **på startsiden** (eller i navigationsruden ved at vælge **TilstandThreats** >  & antivirus).

    Hvis din organisation har mere end 800 enheder tilmeldt Intune, bliver du bedt om at få vist trusselsregistreringer og indsigt fra [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) i stedet for fra siden **Trusler og antivirus**.
 
    > [!NOTE]
    > Siden **Microsoft Defender Antivirus** kort og **trusler og antivirus** udrulles i faser, så du har muligvis ikke umiddelbar adgang til dem.

I de fleste tilfælde behøver brugerne ikke at foretage sig yderligere. Så snart der registreres en skadelig fil eller et program på en enhed, blokerer Microsoft Defender Antivirus den og forhindrer den i at køre. Desuden føjes nyligt registrerede trusler til antivirus- og antimalwareprogrammet, så andre enheder og brugere også er beskyttet.  

Hvis der er en handling, som en bruger skal udføre, f.eks. godkendelse af fjernelsen af en skadelig fil, kan vedkommende se det i den meddelelse, vedkommende modtager. Hvis du vil vide mere om de handlinger, Microsoft Defender Antivirus udfører på en brugers vegne, eller hvilke handlinger brugerne skal udføre, skal du se [Beskyttelsesoversigt](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Hvis du vil vide mere om, hvordan du administrerer trusselsregistreringer som it-professionel/administrator, skal du se [Gennemse registrerede trusler og udføre handlinger](review-threats-take-action.md).

Hvis du vil vide mere om forskellige trusler, skal du besøge <a href="https://www.microsoft.com/wdsi/threats" target="_blank">webstedet Microsoft Sikkerhedsviden Trusler</a>, hvor du kan udføre følgende handlinger: 

- Vis aktuelle oplysninger om de vigtigste trusler.
- Få vist de seneste trusler for et bestemt område.
- Søg i trusselsleksikonet for at få oplysninger om en bestemt trussel.

## <a name="related-content"></a>Relateret indhold

[Sikker Windows enheder](/misc/m365bp-secure-windows-devices) (artikel)\
[Evaluer Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (artikel)\
[Sådan aktiverer du antivirusbeskyttelse i realtid og cloudbaseret antivirusbeskyttelse](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (artikel)\
[Sådan aktiverer og bruger du Microsoft Defender Antivirus fra appen Windows Sikkerhed](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (artikel)\
[Sådan slår du Microsoft Defender Antivirus til ved hjælp af Gruppepolitik](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (artikel)\
[Sådan opdaterer du dine antivirusdefinitioner](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (artikel)\
[Sådan indsender du malware og ikke-malware til Microsoft til analyse](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (artikel)