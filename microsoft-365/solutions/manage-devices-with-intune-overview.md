---
title: Administrer enheder med Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into Intune
- manage device endpoints
- zero trust deployment stack
- device management with zero trust
manager: dougeby
audience: ITPro
ms.topic: article
description: Tilmeld dine slutpunktsenheder i Microsoft Intune som en del af din nultillidssikkerhedsarkitektur, der beskytter mod ransomware, mens du skaber beskyttelse mod fjernmedarbejdere.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 9b1f3fbf48b58c477c1ae4c49870af6d58341bc4
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63594088"
---
# <a name="manage-devices-with-intune-overview"></a>Administrer enheder med Oversigt over Intune

En vigtig komponent i sikkerhed på virksomhedsniveau omfatter administration og beskyttelse af enheder. Uanset om du opbygger en nultillidssikkerhedsarkitektur, chikaner dit miljø mod ransomware eller opbygger beskyttelser for at understøtte eksterne medarbejdere, er administration af enheder en del af strategi. Mens Microsoft 365 indeholder flere værktøjer og metoder til administration og beskyttelse af enheder, gennemgår denne vejledning Microsofts anbefalinger med Microsoft Intune. Dette er den rette vejledning for dig, hvis du:

- Planlæg at tilmelde enheder til Intune via Azure AD Join (herunder Hybrid Azure AD Join).
- Planlæg manuelt at tilmelde enheder til Intune.
- Tillad BYOD-enheder med planer for at implementere beskyttelse af apps og data og/eller tilmelde disse enheder til administration.

Hvis dit miljø derimod indeholder planer for samtidig administration, herunder Microsoft Endpoint Configuration Manager, skal du se Dokumentation til samtidig administration for [](/mem/configmgr/comanage/) at udvikle den bedste vej for organisationen. Hvis dit miljø indeholder planer for Windows 365 Cloud PC, skal du Windows [365 Enterprise-dokumentation](/windows-365/enterprise/) for at udvikle den bedste sti til din organisation. 

## <a name="why-manage-endpoints"></a>Hvorfor administrere slutpunkter?
Den moderne virksomhed har en utrolig forskellighed af slutpunkter, der tilgår deres data. Denne konfiguration skaber en massiv angrebsoverflade, og derfor kan slutpunkter nemt blive det svage link i nultillidssikkerhedsstrategi. 

Som oftest drevet af nødvendighed, når verden er flyttet til en fjern- eller hybrid arbejdsmodel, arbejder brugerne hvor som helst fra en hvilken som helst enhed, mere end når som helst i historikken. Hackere justerer hurtigt deres taktikker, så de kan udnytte denne ændring. Mange organisationer står over for begrænsede ressourcer, når de navigerer i disse nye forretningsmæssige udfordringer. Næsten natten over har virksomheder accelereret digital transformation. Den måde, folk arbejder på, har ganske enkelt ændret sig – vi forventer ikke længere, at vi kun vil have adgang til et væld af virksomhedsressourcer fra kontoret og på virksomhedsejede enheder.

At få indsigt i slutpunkterne, der tilgår virksomhedens ressourcer, er det første trin i din Zero Trust-enhedsstrategi. Typisk beskytter virksomheder proaktivt pc'er mod sårbarheder og angreb, mens mobilenheder ofte bliver overvåget og uden beskyttelse. For at sikre, at du ikke eksponerer dine data for risici, er vi nødt til at overvåge alle slutpunkter for risici og anvende granularadgangskontrolelementer for at levere det relevante adgangsniveau baseret på organisationens politik. Hvis en personlig enhed f.eks. er jailbroken, kan du blokere adgangen for at sikre, at virksomhedsprogrammer ikke eksponeres for kendte sårbarheder.

Denne serie af artikler gennemgår en anbefalet proces til administration af enheder, der har adgang til dine ressourcer. Hvis du følger de anbefalede trin, opnår organisationen meget avanceret beskyttelse for dine enheder og de ressourcer, de får adgang til.


## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Implementering af lag af beskyttelse på og for enheder

Beskyttelse af data og apps på enheder og selve enhederne er en proces i flere lag. Der er nogle beskyttelser, du kan opnå på enheder, der ikke er administrerede. Når du har tilmeldt enheder til administration, kan du implementere mere avancerede kontrolelementer. Når trusselsbeskyttelse implementeres på tværs af dine slutpunkter, får du endnu mere viden og muligheden for automatisk at afhjælpe nogle angreb. Hvis din organisation har sat arbejdet ind i at identificere følsomme data, anvende klassificering og etiketter og konfigurere politikker til forebyggelse af datatab, kan du opnå endnu mere detaljeret beskyttelse af data på dine slutpunkter.

Følgende diagram illustrerer dokumentkomponenter for at opnå en nultillidssikkerhedsudseelse for Microsoft 365 og andre SaaS-apps, som du introducerer for dette miljø. De elementer, der er relateret til enheder, nummereret 1 til 7. Dette er lagene for beskyttelse af enheder, som administratorer vil koordinere med andre administratorer for at opnå. 

![Microsoft 365 zero trust-installationsstabling](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

I denne illustration: 


|&nbsp;|Trin |Beskrivelse  |Licenskrav  |
|---------|---------|---------|---------|
|1     | Konfigurere nultillidsidentitet og politikker for enhedsadgang fra start       | Arbejd med din identitetsadministrator for [at implementere niveau 2-politikker for appbeskyttelse (APP) til databeskyttelse](manage-devices-with-intune-app-protection.md). Disse politikker kræver ikke, at du administrerer enheder. Du kan konfigurere APP-politikkerne i Intune. Din identitetsadministrator konfigurerer en politik for Betinget adgang til at kræve godkendte apps.          |E3, E5, F1, F3, F5    |
|2     | Tilmeld enheder til administration       | Denne opgave kræver mere planlægning og mere tid at implementere. Microsoft anbefaler, at du bruger Intune til at tilmelde enheder, da dette værktøj sikrer optimal integration. Der er flere muligheder for tilmelding af enheder, afhængigt af platformen. Eksempelvis kan Windows tilmeldes ved hjælp af Azure AD Join eller ved hjælp af AutoPilot. Du skal gennemgå indstillingerne for hver platform og beslutte, hvilken registreringsindstilling der egner sig bedst til dit miljø. Se [Trin 3 – Tilmeld enheder til administration for at](manage-devices-with-intune-enroll.md) få flere oplysninger.      | E3, E5, F1, F3, F5        |
|3     | Konfigurere politikker for overholdelse af regler og standarder        |  Du skal være sikker på, at enheder, der har adgang til dine apps og data, opfylder minimumskravene. Enhederne er f.eks. adgangskodebeskyttede eller fastgjorte, og operativsystemet er opdateret. Politikker for overholdelse af regler og standarder er den måde, hvorpå du kan definere de krav, som enhederne skal opfylde. [Trin 3. Konfiguration af politikker for overholdelse af regler](manage-devices-with-intune-compliance-policies.md) og standarder hjælper dig med at konfigurere disse politikker.        |   E3, E5, F3, F5      |
|4     | Konfigurere Enterprise (anbefales) nultillidsidentitet og politikker for enhedsadgang        |Nu, hvor dine enheder er tilmeldt, kan du arbejde sammen med din identitetsadministrator om at finjustere politikker for [Betinget adgang, så der kræves sunde og kompatible enheder](manage-devices-with-intune-require-compliance.md).          | E3, E5, F3, F5        |
|5     |Installér konfigurationsprofiler      | I modsætning til politikker for enhedsoverholdelse, som blot markerer en enhed som kompatibel eller ikke er baseret på kriterier, du konfigurerer, ændrer konfigurationsprofiler faktisk konfigurationen af indstillingerne på en enhed. Du kan bruge konfigurationspolitikker til at gøre enheder mod cybertrusler mod cybertrusler. Se [Trin 5. Installér konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md).        | E3, E5, F3, F5        |
|6     |Overvåg risiko og overholdelse af enheder med grundlinjer for sikkerhed         | I dette trin opretter du forbindelse mellem Intune og Microsoft Defender for Endpoint. Med denne integration kan du overvåge enhedsrisici som en betingelse for adgang. Enheder, der findes at være i en risikabel tilstand, blokeres. Du kan også overvåge overholdelse af sikkerheds oprindelige planer. Se [Trin 6. Overvåg enhedsrisici og overholdelse af sikkerheds oprindelige planer](manage-devices-with-intune-monitor-risk.md).       | E5, F5        |
|7     |Implementere forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger   | Hvis din organisation har sat arbejdet i at identificere følsomme data og mærkningsdokumenter, kan du samarbejde med din administrator til beskyttelse af oplysninger for at beskytte følsomme oplysninger og dokumenter [på dine enheder](manage-devices-with-intune-dlp-mip.md).         | Tilføjelsesprogrammet E5, overholdelse af F5        |
| | | | |

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Koordinering af slutpunktsadministration med nultillidsidentitet og politikker for enhedsadgang

Denne vejledning er tæt koordineret med de anbefalede politikker for [Nul tillid til identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Du skal arbejde med dit identitetsteam for at udføre den beskyttelse, du konfigurerer med Intune i Politikker for betinget adgang i Azure AD. 

Her er en illustration af de anbefalede politiksæt med trinforklaringer til det arbejde, du skal udføre i Intune/MEM, og de relaterede politikker for Betinget adgang, som du kan koordinere i Azure AD. 

[![Politikker for nultillidshed og enhedsadgang](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)


I denne illustration:
- I trin 1, [Implementer niveau 2-politikker for appbeskyttelse (APP),](manage-devices-with-intune-app-protection.md) konfigurerer du det anbefalede niveau af databeskyttelse med APP-politikker. Derefter arbejder du med dit identitetsteam for at konfigurere den relaterede regel betinget adgang til at kræve brug af denne beskyttelse.
- I trin 2, 3 og 4 tilmelder du enheder til administration med Intune/MEM, definerer politikker for enhedsoverholdelse og koordinerer derefter med dit identitetsteam for at konfigurere den relaterede regel betinget adgang til kun at tillade adgang til kompatible enheder. 

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Tilmelding af enheder kontra onboardingenheder
Hvis du følger denne vejledning, skal du tilmelde enheder til administration ved hjælp af Intune (eller et andet værktøj), og du vil onboarde enheder til to tjenester:
- Defender til Slutpunkt
- Slutpunkt DLP


Følgende illustration viser, hvordan det fungerer ved hjælp af Intune.
<br>

![Proces for tilmelding og onboardingenheder](../media/devices/devices-enroll-onboard-process.png#lightbox)

I illustrationen:
1. Tilmeld enheder til administration med Intune.
2. Brug Intune til at onboarde enheder til Defender for Endpoint.
3. Enheder, der er onboardet til Defender til Slutpunkt, er også onboardet til Microsoft 365 overholdelsesfunktioner, herunder Endpoint DLP.
 
Bemærk, at det kun er Intune, der administrerer enheder. Onboarding henviser til en enheds mulighed for at dele oplysninger med en bestemt tjeneste. Følgende tabel opsummerer forskellene mellem registrering af enheder i administrations- og onboardingenheder for en bestemt tjeneste.


|         |Tilmeld dig     |Onboard  |
|---------|---------|---------|
|Beskrivelse     |  Tilmelding gælder for administration af enheder. Enheder er tilmeldt administration med Intune eller Konfigurationsstyring.        | Onboarding konfigurerer en enhed til at fungere med et bestemt sæt af funktioner i Microsoft 365. I øjeblikket gælder onboarding for Microsoft Defender for Endpoint og Microsofts egenskaber for overholdelse af regler og standarder. <br><br>På Windows-enheder indebærer onboarding at slå en indstilling i Windows Defender til, så Defender kan oprette forbindelse til onlinetjenesten og acceptere politikker, der gælder for enheden.        |
|Omfang     | Disse værktøjer til administration af enheder administrerer hele enheden, herunder konfiguration af enheden for at opfylde specifikke målsætninger, f.eks. sikkerhed.        |Onboarding påvirker kun de tjenester, der gælder.     |
|Anbefalet metode     | Azure Active Directory tilmelder sig automatisk enheder i Intune.        | Intune er den foretrukne metode til onboardingenheder til Windows Defender til slutpunkt og derfor også Microsoft 365 funktioner til overholdelse af regler og standarder.<br><br>Bemærk, at enheder, der er onboardet til Microsoft 365 overholdelsesegenskaber ved hjælp af andre metoder, ikke automatisk tilmeldes Defender til Slutpunkt.        |
|Andre metoder     |   Andre tilmeldingsmetoder afhænger af enhedens platform, og om den er BYOD eller administreres af din organisation.      | Andre metoder for onboardingenheder omfatter i anbefalet rækkefølge:<br><li>Konfigurationsstyring<li>Andet værktøj til administration af mobilenheder (hvis enheden administreres af en)<li>Lokalt script<li>VDI-konfigurationspakke til onboarding af ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)<li>Gruppepolitik|
| | |     |



## <a name="learning-for-administrators"></a>Learning til administratorer
Følgende ressourcer hjælper administratorer med at lære begreber om brug af MEM og Intune.

[Gør administration af enheder mere enkelt med Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) Beskrivelse: Få mere at vide om moderne administration og Microsoft Endpoint Manager, og hvordan værktøjer til virksomhedsadministration i Microsoft 365 kan forenkle administrationen af alle dine enheder.

[Konfigurer Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Beskrivelse: Microsoft Intune, som er en del af Microsoft Endpoint Manager, hjælper dig med at beskytte de enheder, apps og data, som personerne i organisationen bruger til at være produktive. Når du har fuldført modulet, skal du konfigurere Microsoft Intune. Konfiguration omfatter gennemgang af de understøttede konfigurationer, tilmelding til Intune, tilføjelse af brugere og grupper, tildeling af licenser til brugere, tildeling af administratortilladelser og indstilling af MDM-myndighed.
