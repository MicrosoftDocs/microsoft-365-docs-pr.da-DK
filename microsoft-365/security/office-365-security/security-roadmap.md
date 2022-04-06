---
title: Microsoft 365 oversigt over sikkerhed – Topprioriteter
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
description: De bedste anbefalinger fra Microsofts cybersecurity-team til implementering af sikkerhedsfunktioner for at beskytte dit Microsoft 365 miljø.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7ffdcb8e6f1a3cb167ec3ce8d7ac5a9225b05356
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683225"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Sikkerhedsoversigt – Topprioriteter for de første 30 dage, 90 dage og derefter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Denne artikel indeholder de bedste anbefalinger fra Microsofts cybersecurity-team til implementering af sikkerhedsfunktioner for at beskytte dit Microsoft 365 miljø. Denne artikel er tilpasset fra en Microsoft Ignite-session – [Secure Microsoft 365 som en cybersecurity-pro: Topprioriteter for de første 30 dage, 90 dage og derefter](https://www.youtube.com/watch?v=luignzNyR-o). Denne session blev udviklet og præsenteret af Mark Simos og Matt Kemelhar, Enterprise Cybersecurity Architects.

I denne artikel:

- [Roadmap-resultater](security-roadmap.md#Roadmap)
- [30 dage – effektive hurtige gevinster](security-roadmap.md#Thirdaydays)
- [90 dage – udvidet beskyttelse](security-roadmap.md#Ninetydays)
- [Mere end](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Roadmap-resultater
<a name="Roadmap"> </a>

Disse anbefalinger til roadmap er faselagt på tværs af tre faser i en logisk rækkefølge med følgende mål.

|Tidsramme|Resultater|
|---|---|
|30 dage|Hurtig konfiguration: <ul><li>Grundlæggende administratorbeskyttelse.</li><li>Logføring og analyse.</li><li>Grundlæggende identitetsbeskyttelse.</li></ul> <p> Lejerkonfiguration. <p> Forberede interessenter.|
|90 dage|Avanceret beskyttelse: <ul><li>Administratorkonti.</li><li>Data og brugerkonti.</li></ul> <p> Indsigt i overholdelse, trusler og brugerbehov. <p> Tilpas og implementer standardpolitikker og beskyttelser.|
|Mere end|Justere og justere vigtige politikker og kontrolelementer. <p> Udvid beskyttelse til lokale afhængigheder. <p> Integrer med forretnings- og sikkerhedsprocesser (juridiske, insidertrusler osv.).|

## <a name="30-days--powerful-quick-wins"></a>30 dage – effektive hurtige gevinster
<a name="Thirdaydays"> </a>

Disse opgaver kan udføres hurtigt og har lav indvirkning for brugerne.

|Område|Opgaver|
|---|---|
|Sikkerhedsadministration|<ul><li>Kontrollér Secure Score, og noter dig dit aktuelle resultat (<https://security.microsoft.com/securescore>).</li><li>Slå overvågningslogføring til for Office 365. Se [Søg i overvågningsloggen](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Konfigurer Microsoft 365 for øget sikkerhed](tenant-wide-setup-for-increased-security.md).</li><li>Gennemgå regelmæssigt dashboards og rapporter i Microsoft 365 Defender-portalen og Defender til skyapps.</li></ul>|
|Trusselsbeskyttelse|[Forbind Microsoft 365 Microsoft Defender til skyapps for at](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) begynde overvågning ved hjælp af standardpolitikker til registrering af trusler med henblik på unormal adfærd. Det tager syv dage at oprette en oprindelig plan til registrering af anomali. <p>  Implementer beskyttelse af administratorkonti:<ul><li>Brug dedikerede administratorkonti til administratoraktivitet.</li><li>Gennemtving multifaktorgodkendelse (MFA) for administratorkonti.</li><li>Brug en [meget sikker Windows til](/windows-hardware/design/device-experiences/oem-highly-secure) administratoraktivitet.</li></ul>|
|Administration af identitet og adgang|<ul><li>[Aktivér Azure Active Directory-identitetsbeskyttelse](/azure/active-directory/active-directory-identityprotection-enable).</li><li>For identitetsmiljøer i organisationsnetværket skal du gennemtvinge kontosikkerhed (adgangskodelængde, alder, kompleksitet osv.).</li></ul>|
|Beskyttelse af oplysninger|Gennemse eksempler på anbefalinger til beskyttelse af oplysninger. Beskyttelse af oplysninger kræver koordinering på tværs af organisationen. Introduktion til disse ressourcer:<ul><li>[Office 365 databeskyttelse til GDPR](/compliance/regulatory/gdpr)</li><li>[Konfigurere Teams med tre niveauer af beskyttelse](../../solutions/configure-teams-three-tiers-protection.md) (herunder deling, klassificering, forebyggelse af datatab og Azure Information Protection)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 dage – udvidet beskyttelse
<a name="Ninetydays"> </a>

Disse opgaver tager lidt mere tid at planlægge og implementere, men markant øge din sikkerhed.

|Område|Opgave|
|---|---|
|Sikkerhedsadministration|<ul><li>Kontrollér Secure Score for anbefalede handlinger for dit miljø (<https://security.microsoft.com/securescore>).</li><li>Fortsæt med jævnligt at gennemgå dashboards og rapporter i Microsoft 365 Defender, Defender til skyapps og SIEM-værktøjer.</li><li>Se efter og implementer softwareopdateringer.</li><li>Udfør angrebssimulering for phishing, password-phishing og brute-force-adgangskodeangreb ved hjælp af simulering af [angreb (](attack-simulation-training.md)inkluderet [Office 365 Threat Intelligence](office-365-ti.md).</li><li>Se efter risikodeling ved at gennemse de indbyggede rapporter i Defender til skyapps (på fanen Undersøg).</li><li>Kontrollér [Overholdelsesstyring](../../compliance/compliance-manager.md) for at se status for bestemmelser, der gælder for din organisation (f.eks. GDPR, NIST 800-171).</li></ul>|
|Trusselsbeskyttelse|Implementer forbedret beskyttelse af administratorkonti: <ul><li>Konfigurer [privileged access-arbejdsstationer](/security/compass/privileged-access-devices) (PAWs) for administratoraktivitet.</li><li>Konfigurer [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Konfigurer et værktøj til sikkerhedsoplysninger og begivenhedsstyring (SIEM) til indsamling af logføringsdata fra Office 365, Defender til skyapps og andre tjenester, herunder AD FS. Overvågningsloggen gemmer kun data i 90 dage. Registrering af disse data i SIEM-værktøjet giver dig mulighed for at gemme data i en længere periode.</li></ul>|
|Administration af identitet og adgang|<ul><li>Aktivér og gennemtving MFA for alle brugere.</li><li>Implementer et sæt [betinget adgang og relaterede politikker](microsoft-365-policies-configurations.md).</li></ul>|
|Beskyttelse af oplysninger| Tilpas og implementer politikker for beskyttelse af oplysninger. Disse ressourcer indeholder eksempler: <ul><li>[Office 365 databeskyttelse til GDPR](/compliance/regulatory/gdpr)</li><li>[Konfigurere Teams med tre niveauer af beskyttelse](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Brug politikker til forebyggelse af datatab og overvågningsværktøjer i Microsoft 365 for data, der er gemt i Microsoft 365 (i stedet for Defender til skyapps). <p> Brug Defender til skyapps med Microsoft 365 til avancerede beskedfunktioner (bortset fra forebyggelse af datatab).|

## <a name="beyond"></a>Mere end
<a name="Beyond"> </a>

Disse er vigtige sikkerhedsforanstaltninger, der bygger på tidligere arbejde.

|Område|Opgave|
|---|---|
|Sikkerhedsadministration|<ul><li>Fortsæt med at planlægge næste handlinger ved hjælp af Secure Score (<https://security.microsoft.com/securescore>).</li><li>Fortsæt med jævnligt at gennemgå dashboards og rapporter i Microsoft 365 Defender, Defender til skyapps og SIEM-værktøjer.</li><li>Fortsæt med at søge efter og implementere softwareopdateringer.</li><li>Integrer eDiscovery i dine juridiske processer og trusselsresponsprocesser.</li></ul>|
|Trusselsbeskyttelse|<ul><li>[Implementer SECURE Privileged Access](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) for identitetskomponenter lokalt (AD, AD FS).</li><li>Brug Defender til skyapps til at overvåge for Insider-trusler.</li><li>Opdag skyggen i it SaaS-brugen ved hjælp af Defender til skyapps.</li></ul>|
|Administration af identitet og adgang|<ul><li>Finjustere politikker og driftsprocesser.</li><li>Brug Azure AD Identity Protection til at identificere Insider-trusler.</li></ul>|
|Beskyttelse af oplysninger|Finjustere politikker for beskyttelse af oplysninger: <ul><li>Microsoft 365 og Office 365 følsomhedsmærkater og forebyggelse af datatab (DLP) eller Azure Information Protection.</li><li>Defender til skyapps, politikker og beskeder.</li></ul>|

Læs også: [Sådan kan du afhjælpe hurtige cyberangreb som f.eks. Petya og WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
