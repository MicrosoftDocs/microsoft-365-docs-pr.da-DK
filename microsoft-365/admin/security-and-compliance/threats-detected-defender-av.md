---
title: Trusler, der registreres af Microsoft Defender Antivirus
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
description: Få mere Microsoft Defender Antivirus, hvordan du beskytter Windows enheder mod softwaretrusler, f.eks. virus, malware og spyware.
ms.openlocfilehash: c11ce9a2f38f1ecb7f47cd5b74e710d92c8ffbe0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592332"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>Trusler, der registreres af Microsoft Defender Antivirus

Microsoft Defender Antivirus beskytter dine Windows mod softwaretrusler, f.eks. virus, malware og spyware.

- Virus spredes typisk ved at vedhæfte deres kode til andre filer på din enhed eller dit netværk og kan medføre, at inficeret programmer fungerer forkert.
- Malware omfatter skadelige filer, programmer og kode, der kan forårsage skade og afbryde normal brug af enheder. Malware kan også tillade uautoriseret adgang, bruge systemressourcer, stjæle adgangskoder og kontooplysninger, låse dig ude af computeren og bede om hjælp og meget mere.
- Spyware indsamler data, f.eks. aktiviteter i forbindelse med webbrowsing, og sender dataene til fjernservere.
 
For at yde trusselsbeskyttelse Microsoft Defender Antivirus bruge flere forskellige metoder. Disse metoder omfatter skybaseret beskyttelse, beskyttelse i realtid og dedikerede opdateringer til beskyttelse.

- Beskyttelse, der leveres i skyen, giver øjeblikkelig registrering og blokering af nye og fremspirende trusler.
- Ved altid-on-scanning bruges fil- og procesfunktionsmådeovervågning og andre teknikker (også kaldet *beskyttelse i realtid*).
- Dedikerede opdateringer til beskyttelse er baseret på maskinlæring, menneskelig og automatiseret big data-analyse og dybdegående forskning om trusselsbeskyttelse. 

Hvis du vil have mere at vide om malware Microsoft Defender Antivirus, skal du se følgende artikler: 

- [Forstå malware & andre trusler](/windows/security/threat-protection/intelligence/understanding-malware)
- [Sådan identificerer Microsoft malware og potentielt uønskede programmer](/windows/security/threat-protection/intelligence/criteria)
- [Næste generations beskyttelse i Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Hvad sker der, når der bruges en antivirusløsning, som ikke er Microsoft? 

Microsoft Defender Antivirus er en del af operativsystemet og er aktiveret på enheder, der kører Windows 10. Men hvis du bruger en antivirusløsning, som ikke er Microsoft, og du ikke bruger [Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), Microsoft Defender Antivirus automatisk i deaktiveret tilstand.  

Når deaktiveret tilstand er deaktiveret, kan brugere og kunder stadig bruge Microsoft Defender Antivirus til planlagte scanninger eller scanninger efter behov til at identificere trusler, men Microsoft Defender Antivirus vil ikke længere:

- bruges som standardprogram til antivirus.
- scan aktivt filer for trusler.
- afhjælpe eller løse trusler.

Hvis du fjerner den ikke-Microsoft-antivirusløsning, Microsoft Defender Antivirus automatisk i aktiv tilstand for at beskytte Windows enheder mod trusler.

> [!TIP]
> - Hvis du bruger en Microsoft 365, bør du overveje Microsoft Defender Antivirus som din primære antivirusløsning. Integration kan give bedre beskyttelse. Se [bedre sammen: Microsoft Defender Antivirus og Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Sørg for at Microsoft Defender Antivirus opdateret, også selvom du bruger en antivirusløsning, der ikke er Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>Hvad du kan forvente, når der registreres trusler

Når trusler opdages af Microsoft Defender Antivirus, sker følgende:

- Brugerne modtager [meddelelser i Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Registreringer er angivet i [Windows Sikkerhed på](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) siden **Beskyttelsesoversigt**.  
- Hvis du har sikret dig dine [Windows 10-enheder](../setup/secure-win-10-pcs.md) og tilmeldt dem [i Intune](/mem/intune/enrollment/windows-enrollment-methods), og din organisation har 800 eller færre enheder tilmeldt sig, får du vist **trusselsregistreringer** og indsigt i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> på siden Trusler og antivirus, **som du kan få adgang til fra Microsoft Defender Antivirus** på **startsiden** (eller fra **navigationsruden ved at vælge HealthThreats** >  & antivirus).

    Hvis din organisation har mere end 800 enheder tilmeldt Intune, bliver du bedt om at få vist **trusselsregistreringer** og indsigt fra [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) i stedet for fra siden Trusler og antivirus.
 
    > [!NOTE]
    > Siden **Microsoft Defender Antivirus** og **trusler og antivirus** bliver rullet ud i faser, så du har muligvis ikke øjeblikkelig adgang til dem.

I de fleste tilfælde behøver brugerne ikke at gøre mere. Så snart der registreres en skadelig fil eller et program på en enhed, Microsoft Defender Antivirus den og forhindrer den i at køre. Desuden føjes nyligt registrerede trusler til antivirus- og antimalwareprogrammet, så andre enheder og brugere også er beskyttet.  

Hvis der er en handling, en bruger skal gøre, f.eks. godkendelse af fjernelse af en skadelig fil, vil brugeren kunne se det i den meddelelse, brugeren modtager. Du kan få mere at vide om Microsoft Defender Antivirus, der sker på en brugers vegne, eller handlinger, som brugere muligvis skal udføre, i [Beskyttelsesoversigt](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Du kan få mere at vide om, hvordan du administrerer trusselsregistreringer som it-fagperson/administrator under [Gennemgå registrerede trusler, og reaktion](review-threats-take-action.md).

Hvis du vil have mere at vide om forskellige trusler, <a href="https://www.microsoft.com/wdsi/threats" target="_blank">skal Microsoft Sikkerhedsviden webstedet Threats</a>, hvor du kan udføre følgende handlinger: 

- Få vist aktuelle oplysninger om de vigtigste trusler.
- Se de seneste trusler for et bestemt område.
- Søg i trusselscykelopedia for at få mere at vide om en bestemt trussel.

## <a name="related-content"></a>Relateret indhold

[Gør Windows-enheder](/misc/m365bp-secure-windows-devices) sikre (artikel)\
[Evaluer Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (artikel)\
[Sådan aktiverer du antivirusbeskyttelse i realtid og skybaseret (](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) artikel)\
[Sådan aktiverer og bruger du Microsoft Defender Antivirus fra Windows Sikkerhed (](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus)artikel)\
[Sådan slår du en Microsoft Defender Antivirus til ved hjælp Gruppepolitik](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (artikel)\
[Sådan opdaterer du dine antivirusdefinitioner](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (artikel)\
[Sådan sender du malware og ikke-malware til Microsoft til analyse](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (artikel)