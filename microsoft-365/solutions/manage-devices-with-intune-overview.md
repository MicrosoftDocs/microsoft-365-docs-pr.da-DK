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
description: Tilmeld dine slutpunktsenheder i Microsoft Intune som en del af din Nul tillid sikkerhedsarkitektur, der beskytter mod ransomware, mens du bygger beskyttelse til fjernarbejdere.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: a9872e707bbbb6546d6801ac88ebd28f23fb9806
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651317"
---
# <a name="manage-devices-with-intune-overview"></a>Administrer enheder med Intune Oversigt

En kernekomponent i sikkerhed på virksomhedsniveau omfatter administration og beskyttelse af enheder. Uanset om du bygger en Nul tillid sikkerhedsarkitektur, hærder dit miljø mod ransomware eller bygger beskyttelse for at understøtte fjernarbejdere, er administration af enheder en del af strategien.
Selvom Microsoft 365 indeholder flere værktøjer og metoder til administration og beskyttelse af enheder, gennemgår denne vejledning Microsofts anbefalinger ved hjælp af Microsoft Intune. Dette er den rette vejledning for dig, hvis du:

- Planlæg at tilmelde enheder til Intune via Azure AD Join (herunder Hybrid Azure AD Join).
- Planlæg at tilmelde enheder til Intune manuelt.
- Tillad BYOD-enheder med planer om at implementere beskyttelse af apps og data og/eller tilmelde disse enheder for at Intune.

Hvis dit miljø indeholder planer for medadministration, herunder Microsoft Endpoint Configuration Manager, skal du på den anden side se Dokumentation til [samtidig administration](/mem/configmgr/comanage/) for at udvikle den bedste vej for din organisation. Hvis dit miljø indeholder planer for Windows 365 Cloud-pc, skal du se [Windows 365 Enterprise dokumentation](/windows-365/enterprise/) for at udvikle den bedste sti til din organisation.

## <a name="why-manage-endpoints"></a>Hvorfor administrere slutpunkter?

Den moderne virksomhed har en utrolig mangfoldighed af slutpunkter, der tilgår deres data. Denne konfiguration skaber en massiv angrebsoverflade, og slutpunkter kan derfor nemt blive det svageste led i din Nul tillid sikkerhedsstrategi.

For det meste drevet af nødvendighed, da verden skiftede til en ekstern eller hybrid arbejdsmodel, arbejder brugerne overalt, fra enhver enhed, mere end når som helst i historien. Personer med ondsindede hensigter justerer hurtigt deres taktik for at drage fordel af denne ændring. Mange organisationer står over for begrænsede ressourcer, når de navigerer i disse nye forretningsudfordringer. Næsten fra den ene dag til den anden har virksomheder accelereret den digitale transformation. Simpelthen sagt, den måde, folk arbejder på, har ændret sig - vi forventer ikke længere at få adgang til det store antal virksomhedsressourcer kun fra kontoret og på virksomhedsejede enheder.

Det første skridt i din Nul tillid enhedsstrategi er at få indblik i de slutpunkter, der får adgang til virksomhedens ressourcer. Virksomheder er typisk proaktive i forhold til at beskytte pc'er mod sårbarheder og angreb, mens mobilenheder ofte ikke overvåges og uden beskyttelse. For at sikre at du ikke eksponerer dine data for risiko, skal vi overvåge hvert slutpunkt for risici og anvende detaljeret adgangskontrol for at levere det relevante adgangsniveau baseret på organisationens politik. Hvis en personlig enhed f.eks. er jailbroken, kan du blokere adgang for at sikre, at virksomhedsprogrammer ikke eksponeres for kendte sikkerhedsrisici.

I denne artikelserie gennemgås en anbefalet proces til administration af enheder, der har adgang til dine ressourcer. Hvis du følger de anbefalede trin, opnår din organisation meget avanceret beskyttelse af dine enheder og de ressourcer, de har adgang til.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Implementering af beskyttelseslag på og for enheder

Beskyttelse af data og apps på enheder og selve enhederne er en proces med flere lag. Der er nogle beskyttelser, du kan få på ikke-administrerede enheder. Når du har tilmeldt enheder til Intune, kan du implementere mere avancerede kontrolelementer. Når trusselsbeskyttelse udrulles på tværs af dine slutpunkter, får du endnu mere indsigt og muligheden for automatisk at afhjælpe nogle angreb. Hvis din organisation har arbejdet med at identificere følsomme data, anvende klassificering og mærkater og konfigurere politikker til forebyggelse af datatab, kan du opnå endnu mere detaljeret beskyttelse af data på dine slutpunkter.

Følgende diagram illustrerer byggestenene til at opnå en Nul tillid sikkerhedsholdning for Microsoft 365 og andre SaaS-apps, som du introducerer til dette miljø. De elementer, der er relateret til enheder, nummereres fra 1 til 7. Dette er lagene af beskyttelse af enhedsadministratorer, der koordinerer med andre administratorer for at opnå dette.

![Microsoft 365 Nul tillid udrulningsstak](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

I denne illustration:

|&nbsp;|Trin|Beskrivelse|Licenskrav|
|---|---|---|---|
|1|Konfigurer startpunkt Nul tillid politikker for identitet og enhedsadgang|Samarbejd med din identitetsadministrator om at [implementere databeskyttelsespolitikker på niveau 2 (APP).](manage-devices-with-intune-app-protection.md) Disse politikker kræver ikke, at du administrerer enheder. Du kan konfigurere APP-politikkerne i Intune. Din identitetsadministrator konfigurerer en politik for betinget adgang til at kræve godkendte apps.|E3, E5, F1, F3, F5|
|2|Tilmeld enheder til Intune|Denne opgave kræver mere planlægning og tid til at implementere. Microsoft anbefaler, at du bruger Intune til at tilmelde enheder, da dette værktøj sikrer optimal integration. Der er flere muligheder for at tilmelde enheder, afhængigt af platformen. Windows enheder kan f.eks. tilmeldes ved hjælp af Azure AD Join eller ved hjælp af Autopilot. Du skal gennemse indstillingerne for hver platform og beslutte, hvilken tilmeldingsmulighed der passer bedst til dit miljø. Se [Trin 3 – Tilmeld enheder for at Intune for at](manage-devices-with-intune-enroll.md) få flere oplysninger.|E3, E5, F1, F3, F5|
|3|Konfigurer politikker for overholdelse af regler og standarder|Du vil være sikker på, at enheder, der tilgår dine apps og data, opfylder minimumskravene, f.eks. at enheder er adgangskode- eller pinkodebeskyttede, og at operativsystemet er opdateret. Politikker for overholdelse af regler og standarder er den måde, hvorpå du kan definere de krav, enhederne skal opfylde. [Trin 3. Konfigurer politikker for overholdelse af angivne standarder](manage-devices-with-intune-compliance-policies.md) hjælper dig med at konfigurere disse politikker.|E3, E5, F3, F5|
|4|Konfigurer Virksomhedspolitikker (anbefales) Nul tillid identitets- og enhedsadgangspolitikker|Nu, hvor dine enheder er tilmeldt, kan du samarbejde med din identitetsadministrator om at [justere politikker for betinget adgang for at kræve sunde og kompatible enheder](manage-devices-with-intune-require-compliance.md).|E3, E5, F3, F5|
|5|Udrul konfigurationsprofiler|I modsætning til politikker for enhedsoverholdelse, der blot markerer en enhed som kompatibel eller ikke er baseret på de kriterier, du konfigurerer, ændrer konfigurationsprofiler faktisk konfigurationen af indstillingerne på en enhed. Du kan bruge konfigurationspolitikker til at hærde enheder mod cyberthreats. Se [trin 5. Udrul konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md).|E3, E5, F3, F5|
|6|Overvåg enhedsrisiko og overholdelse af sikkerhedsbaselinjer|I dette trin opretter du forbindelse Intune til Microsoft Defender for Endpoint. Med denne integration kan du derefter overvåge enhedsrisikoen som en betingelse for adgang. Enheder, der er i risikotilstand, blokeres. Du kan også overvåge overholdelse af grundlæggende sikkerhedsgrundlinjer. Se [trin 6. Overvåg enhedsrisici og overholdelse af angivne standarder i forhold til grundlæggende sikkerhedslinjer](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7|Implementer forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger|Hvis din organisation har arbejdet på at identificere følsomme data og forsyne dokumenter med mærkater, kan du samarbejde med administratoren af beskyttelse af oplysninger for at [beskytte følsomme oplysninger og dokumenter på dine enheder](manage-devices-with-intune-dlp-mip.md).|Tilføjelsesprogrammet E5, F5 til overholdelse af angivne standarder|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Koordinering af administration af slutpunkter med Nul tillid politikker for identitet og enhedsadgang

Denne vejledning er tæt koordineret med de anbefalede [Nul tillid politikker for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Du arbejder sammen med dit identitetsteam om at gennemføre beskyttelse, som du konfigurerer med Intune i politikker for betinget adgang i Azure AD.

Her er en illustration af den anbefalede politik, der er angivet med trinvise billedforklaeringer for det arbejde, du skal udføre i Intune/MEM og de relaterede politikker for betinget adgang, som du kan hjælpe med at koordinere i Azure AD.

[![Nul tillid politikker for identitet og enhedsadgang](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

I denne illustration:

- I trin 1 skal du [implementere niveau 2 App Protection Policies (APP)](manage-devices-with-intune-app-protection.md) for at konfigurere det anbefalede niveau for databeskyttelse med APP-politikker. Derefter arbejder du sammen med dit identitetsteam for at konfigurere den relaterede regel for betinget adgang, så den kræver brug af denne beskyttelse.
- I trin 2, 3 og 4 tilmelder du enheder til administration med Intune, definerer politikker for enhedsoverholdelse og koordinerer derefter med dit identitetsteam for at konfigurere den relaterede regel for betinget adgang, så der kun tillades adgang til enheder, der overholder angivne standarder.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Tilmelding af enheder i forhold til onboarding af enheder

Hvis du følger denne vejledning, skal du tilmelde enheder til administration ved hjælp af Intune, og du vil onboarde enheder til følgende Microsoft 365 funktioner:

- Microsoft Defender for Endpoint
- Microsoft 365 overholdelse af angivne standarder (til forebyggelse af datatab for slutpunkter (DLP)) 

Følgende illustration indeholder oplysninger om, hvordan det fungerer ved hjælp af Intune.

![Proces for tilmelding og onboarding af enheder](../media/devices/devices-enroll-onboard-process.png#lightbox)

I illustrationen:

1. Tilmeld enheder til administration med Intune.
2. Brug Intune til at onboarde enheder for at Microsoft Defender for Endpoint.
3. Enheder, der er onboardet til Defender for Endpoint, er også onboardet til Microsoft 365 funktioner til overholdelse af angivne standarder, herunder slutpunkt DLP.

Bemærk, at kun Intune administrerer enheder. Onboarding refererer til muligheden for, at en enhed kan dele oplysninger med en bestemt tjenesteegenskab. I følgende tabel opsummeres forskellene mellem at tilmelde enheder til administration og onboarding af enheder for en bestemt funktion.

|&nbsp;|Tilmelde|Onboard|
|---|---|---|
|Beskrivelse|Tilmelding gælder for administration af enheder. Enheder er tilmeldt administration med Intune eller Configuration Manager.|Onboarding konfigurerer en enhed til at arbejde med et bestemt sæt funktioner i Microsoft 365. Onboarding gælder i øjeblikket for funktioner til Microsoft Defender for Endpoint og Microsofts overholdelse af angivne standarder. <br/><br/> På Windows enheder involverer onboarding at slå en indstilling til i Windows Defender, der gør det muligt for Defender at oprette forbindelse til onlinetjenesten og acceptere politikker, der gælder for enheden.|
|Omfanget|Disse værktøjer til enhedshåndtering administrerer hele enheden, herunder konfiguration af enheden, så den opfylder bestemte målsætninger, f.eks. sikkerhed.|Onboarding påvirker kun de funktioner, der gælder.|
|Anbefalet metode|Azure Active Directory tilmelde enheder til Intune automatisk.|Intune er den foretrukne metode til onboarding af enheder til Windows Defender for Endpoint og derfor Microsoft 365 funktioner til overholdelse af angivne standarder. <br/><br/> Bemærk, at enheder, der er onboardet til Microsoft 365 funktioner til overholdelse af angivne standarder ved hjælp af andre metoder, ikke automatisk er tilmeldt Defender for Endpoint.|
|Andre metoder|Andre metoder til tilmelding afhænger af enhedens platform, og om det er BYOD eller administreres af din organisation.|Andre metoder til onboarding af enheder omfatter i anbefalet rækkefølge: <ul><li>Konfigurationsstyring</li><li>Andet værktøj til administration af mobilenheder (hvis enheden administreres af et)</li><li>Lokalt script</li><li>VDI-konfigurationspakke til onboarding af ikke-vedvarende VDI-enheder (Virtual Desktop Infrastructure)</li><li>Gruppepolitik</li></ul>|

## <a name="learning-for-administrators"></a>Learning for administratorer

Følgende ressourcer hjælper administratorer med at lære begreber om brug af MEM og Intune.

[Forenkle enhedshåndtering med Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) Beskrivelse: Få mere at vide om moderne administration og Microsoft Endpoint Manager, og hvordan værktøjerne til virksomhedsadministration i Microsoft 365 kan forenkle administrationen af alle dine enheder.

[Konfigurer Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Beskrivelse: Microsoft Intune, som er en del af Microsoft Endpoint Manager, hjælper dig med at beskytte de enheder, apps og data, som personerne i din organisation bruger til at være produktive. Når du har fuldført dette modul, har du konfigureret Microsoft Intune. Konfiguration omfatter gennemgang af understøttede konfigurationer, tilmelding til Intune, tilføjelse af brugere og grupper, tildeling af licenser til brugere, tildeling af administratortilladelser og angivelse af MDM-autoriteten.
