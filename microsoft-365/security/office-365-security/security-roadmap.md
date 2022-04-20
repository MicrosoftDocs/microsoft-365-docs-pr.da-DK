---
title: Microsoft 365 sikkerhedsplan – topprioriteter
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 08/20/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: Topanbefalinger fra Microsofts cybersikkerhedsteam til implementering af sikkerhedsfunktioner for at beskytte dit Microsoft 365 miljø.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b39edc8adbe16d7f085ca9fec9f30d45f484838
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974251"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Oversigt over sikkerhed – topprioriteter for de første 30 dage, 90 dage og derefter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Denne artikel indeholder topanbefalinger fra Microsofts cybersikkerhedsteam til implementering af sikkerhedsfunktioner for at beskytte dit Microsoft 365 miljø. Denne artikel er tilpasset fra en Microsoft Ignite-session – [Secure Microsoft 365 som en cybersikkerhedspro: Topprioriteter for de første 30 dage, 90 dage og mere](https://www.youtube.com/watch?v=luignzNyR-o). Denne session blev udviklet og præsenteret af Mark Simos og Matt Kemelhar, Enterprise Cybersecurity Architects.

I denne artikel:

- [Oversigtsresultater](security-roadmap.md#Roadmap)
- [30 dage – stærke hurtige gevinster](security-roadmap.md#Thirdaydays)
- [90 dage – forbedret beskyttelse](security-roadmap.md#Ninetydays)
- [Uden](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Oversigtsresultater
<a name="Roadmap"> </a>

Disse køreplansanbefalinger er faset på tværs af tre faser i en logisk rækkefølge med følgende mål.

|Tidsramme|Resultater|
|---|---|
|30 dage|Hurtig konfiguration: <ul><li>Grundlæggende administratorbeskyttelse.</li><li>Logføring og analyse.</li><li>Grundlæggende identitetsbeskyttelse.</li></ul> <p> Lejerkonfiguration. <p> Forbered interessenter.|
|90 dage|Avanceret beskyttelse: <ul><li>Administratorkonti.</li><li>Data og brugerkonti.</li></ul> <p> Synlighed i overholdelse af angivne standarder, trusler og brugerbehov. <p> Tilpas og implementer standardpolitikker og -beskyttelser.|
|Uden|Juster og afgræns vigtige politikker og kontrolelementer. <p> Udvid beskyttelsen til afhængigheder i det lokale miljø. <p> Integrer med forretnings- og sikkerhedsprocesser (juridiske, insidertrusler osv.).|

## <a name="30-days--powerful-quick-wins"></a>30 dage – stærke hurtige gevinster
<a name="Thirdaydays"> </a>

Disse opgaver kan udføres hurtigt og have lav indvirkning på brugerne.

|Område|Opgaver|
|---|---|
|Sikkerhedsadministration|<ul><li>Kontrollér Secure Score, og notér din aktuelle score (<https://security.microsoft.com/securescore>).</li><li>Slå logføring af overvågning til for Office 365. Se [Søg i overvågningsloggen](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Konfigurer Microsoft 365 for at øge sikkerheden](tenant-wide-setup-for-increased-security.md).</li><li>Gennemse jævnligt dashboards og rapporter på Microsoft 365 Defender-portalen og Defender for Cloud Apps.</li></ul>|
|Trusselsbeskyttelse|[Forbind Microsoft 365 til at Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) til at begynde at overvåge ved hjælp af standardpolitikker for trusselsregistrering for uregelmæssigheder. Det tager syv dage at oprette en baseline til registrering af uregelmæssigheder. <p>  Implementer beskyttelse for administratorkonti:<ul><li>Brug dedikerede administratorkonti til administratoraktivitet.</li><li>Gennemtving multifaktorgodkendelse for administratorkonti.</li><li>Brug en [yderst sikker Windows enhed](/windows-hardware/design/device-experiences/oem-highly-secure) til administratoraktivitet.</li></ul>|
|Identitets- og adgangsstyring|<ul><li>[Aktivér Azure Active Directory identitetsbeskyttelse](/azure/active-directory/active-directory-identityprotection-enable).</li><li>I forbindelse med identitetsmiljøer i organisationsnetværket skal du gennemtvinge kontosikkerhed (adgangskodelængde, alder, kompleksitet osv.).</li></ul>|
|Beskyttelse af oplysninger|Gennemse eksempler på anbefalinger til beskyttelse af oplysninger. Beskyttelse af oplysninger kræver koordinering på tværs af organisationen. Kom i gang med disse ressourcer:<ul><li>[Office 365 Information Protection for GDPR](/compliance/regulatory/gdpr)</li><li>[Konfigurer Teams med tre beskyttelsesniveauer](../../solutions/configure-teams-three-tiers-protection.md) (omfatter deling, klassificering, forebyggelse af Microsoft Purview-datatab og Azure Information Protection)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 dage – forbedret beskyttelse
<a name="Ninetydays"> </a>

Disse opgaver tager lidt mere tid at planlægge og implementere, men kraftigt øge din sikkerhedsholdning.

|Område|Opgave|
|---|---|
|Sikkerhedsadministration|<ul><li>Kontrollér Secure Score for anbefalede handlinger for dit miljø (<https://security.microsoft.com/securescore>).</li><li>Fortsæt med regelmæssigt at gennemse dashboards og rapporter på Microsoft 365 Defender-portalen, Defender for Cloud Apps og SIEM-værktøjer.</li><li>Søg efter og implementer softwareopdateringer.</li><li>Udfør angrebssimuleringer for spyd-phishing-, adgangskodespray- og brute-force-adgangskodeangreb ved hjælp af [oplæring i simulering af angreb](attack-simulation-training.md) (inkluderet i [Office 365 Threat Intelligence](office-365-ti.md).</li><li>Søg efter delingsrisiko ved at gennemse de indbyggede rapporter i Defender for Cloud Apps (under fanen Undersøg).</li><li>Kontrollér [Overholdelsesstyring](../../compliance/compliance-manager.md) for at gennemse status for de regler, der gælder for din organisation (f.eks. GDPR, NIST 800-171).</li></ul>|
|Trusselsbeskyttelse|Implementer forbedret beskyttelse for administratorkonti: <ul><li>Konfigurer [privilegerede adgangsarbejdsstationer](/security/compass/privileged-access-devices) (PAWs) til administratoraktivitet.</li><li>Konfigurer [Azure AD-Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Konfigurer et SIEM-værktøj (security information and event management) til at indsamle logføringsdata fra Office 365, Defender for Cloud Apps og andre tjenester, herunder AD FS. Overvågningsloggen gemmer kun data i 90 dage. Hvis du registrerer disse data i SIEM-værktøjet, kan du gemme data i en længere periode.</li></ul>|
|Identitets- og adgangsstyring|<ul><li>Aktivér og gennemtving MFA for alle brugere.</li><li>Implementer et sæt [betinget adgang og relaterede politikker](microsoft-365-policies-configurations.md).</li></ul>|
|Beskyttelse af oplysninger| Tilpas og implementer politikker til beskyttelse af oplysninger. Disse ressourcer indeholder eksempler: <ul><li>[Office 365 Information Protection for GDPR](/compliance/regulatory/gdpr)</li><li>[Konfigurer Teams med tre beskyttelsesniveauer](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Brug politikker til forebyggelse af datatab og overvågningsværktøjer i Microsoft Purview til data, der er gemt i Microsoft 365 (i stedet for Defender for Cloud Apps). <p> Brug Defender for Cloud Apps med Microsoft 365 til avancerede beskedfunktioner (bortset fra forebyggelse af datatab).|

## <a name="beyond"></a>Uden
<a name="Beyond"> </a>

Disse er vigtige sikkerhedsforanstaltninger, der bygger på tidligere arbejde.

|Område|Opgave|
|---|---|
|Sikkerhedsadministration|<ul><li>Fortsæt planlægningen af næste handlinger ved hjælp af Secure Score (<https://security.microsoft.com/securescore>).</li><li>Fortsæt med regelmæssigt at gennemse dashboards og rapporter på Microsoft 365 Defender-portalen, Defender for Cloud Apps og SIEM-værktøjer.</li><li>Fortsæt med at søge efter og implementere softwareopdateringer.</li><li>Integrer eDiscovery i dine juridiske processer og trusselssvarprocesser.</li></ul>|
|Trusselsbeskyttelse|<ul><li>Implementer [SPA (Secure Privileged Access](/windows-server/identity/securing-privileged-access/securing-privileged-access) ) for identitetskomponenter i det lokale miljø (AD, AD FS).</li><li>Brug Defender for Cloud Apps til at overvåge insidertrusler.</li><li>Find skygge-IT SaaS-brug ved hjælp af Defender for Cloud Apps.</li></ul>|
|Identitets- og adgangsstyring|<ul><li>Afgræns politikker og driftsprocesser.</li><li>Brug Azure AD Identity Protection til at identificere insidertrusler.</li></ul>|
|Beskyttelse af oplysninger|Afgræns politikker til beskyttelse af oplysninger: <ul><li>Microsoft 365 og Office 365 følsomhedsmærkater og forebyggelse af datatab (DLP) eller Azure Information Protection.</li><li>Defender for Cloud Apps-politikker og -beskeder.</li></ul>|

Se også: [Sådan afhjælper du hurtige cyberangreb som Petya og WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
