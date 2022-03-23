---
title: Forbered Microsoft Defender til installation på slutpunkt
description: Forbered interessenternes godkendelse, tidslinjer, miljøovervejelser og anvendelsesrækkefølge for udrulning af Microsoft Defender til Slutpunkt
keywords: Deploy, prepare, stakeholder, timeline, environment, endpoint, server, management, adoption
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 29f9aabf2c0345e46123ba76869718c15d8d1885
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63592900"
---
# <a name="prepare-microsoft-defender-for-endpoint-deployment"></a>Forbered Microsoft Defender til installation på slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Implementering af Defender til slutpunkt er en trefaset proces:

|![implementeringsfase – klargøring.](images/phase-diagrams/prepare.png)<br>Fase 1: Forbered|[![Installationsfase – konfiguration](images/phase-diagrams/setup.png)](production-deployment.md)<br>[Fase 2: Konfiguration](production-deployment.md)|[![Implementeringsfase – onboard](images/phase-diagrams/onboard.png)](onboarding.md)<br>[Fase 3: Onboard](onboarding.md)|
|---|---|---|
|*Du er her!*|||

Du er i øjeblikket i forberedelsesfasen.

Forberedelse er nøglen til en vellykket installation. I denne artikel bliver du vejledt om de punkter, du skal overveje, når du forbereder dig på at udrulle Defender til Slutpunkt.

## <a name="stakeholders-and-approval"></a>Interessenter og godkendelse

Det følgende afsnit bruges til at identificere alle interessenter, der er involveret i projektet, og skal godkende, gennemgå eller holde sig orienteret.

Føj interessenter til tabellen nedenfor efter behov for din organisation.

- SO = Godkend projekt
- R = Gennemse dette projekt, og angiv input
- I = Informeret om dette projekt

<br>

****

|Navn|Rolle|Handling|
|---|---|---|
|Angiv navn og mail|**Chief Information Security Officer (CISO) En** *lederrepræsentant, der fungerer som sponsor i organisationen for udrulningen af den nye teknologi.*|SO|
|Angiv navn og mail|**Head of Cyber Defense Operations Center (CDOC) En** repræsentant fra CDOC-teamet, der har ansvaret for at definere, hvordan denne ændring er justeret med processerne i *kundens sikkerhedsteam.*|SO|
|Angiv navn og mail|**Sikkerhedsarkitekt** En repræsentant fra sikkerhedsteamet, der har ansvaret for at definere, hvordan denne ændring er *justeret med den grundlæggende sikkerhedsarkitektur i organisationen.*|R|
|Angiv navn og mail|**Workplace Architect** *En repræsentant fra it-teamet, der har* ansvaret for at definere, hvordan denne ændring er justeret med den centrale arkitektur på arbejdspladsen i organisationen.|R|
|Angiv navn og mail|**Sikkerhedsanalytiker** *En repræsentant fra CDOC-teamet*, der kan give input om registreringsfunktioner, brugeroplevelse og den overordnede anvendelighed af denne ændring set fra et sikkerhedsperspektiv.|I|
||||

## <a name="environment"></a>Miljø

Dette afsnit bruges til at sikre, at dit miljø forstås fuldt ud af interessenterne, hvilket kan hjælpe med at identificere potentielle afhængigheder og/eller ændringer, der kræves i teknologier eller processer.

<br>

****

|Hvad|Beskrivelse|
|---|---|
|Antal slutpunkter|Samlet antal slutpunkter efter operativsystem.|
|Serverantal|Samlet antal servere efter operativsystemversion.|
|Management engine|Navn og version på administrationsmaskine (f.eks. System Center Configuration Manager Aktuel forgrening 1803).|
|CDOC-fordeling|CDOC-struktur på højt niveau (f.eks. niveau 1, der er distribueret til Contoso, niveau 2 og niveau 3 internt fordelt over Europa og Asien).|
|Sikkerhedsoplysninger og begivenhed (SIEM)|SIEM-teknologi i brug.|
|||

## <a name="role-based-access-control"></a>Rollebaseret adgangskontrol

Microsoft anbefaler, at du bruger begrebet de mindste rettigheder. Defender til slutpunkt udnytter indbyggede roller i Azure Active Directory. Microsoft anbefaler, [at du gennemgår de](/azure/active-directory/roles/permissions-reference) forskellige roller, der er tilgængelige, og vælger den rette rolle til at løse dine behov for hver persona til dette program. Nogle roller skal muligvis anvendes midlertidigt og fjernes, når installationen er fuldført.

<br>

****

|Personaer|Roller|Azure AD-rolle (hvis det er nødvendigt)|Tildel til|
|---|---|---|---|
|Sikkerhedsadministrator||||
|Sikkerhedsanalytiker||||
|Slutpunktsadministrator||||
|Infrastrukturadministrator||||
|Virksomhedsejer/interessent||||
|

Microsoft anbefaler at bruge [Privileged Identity Management til](/azure/active-directory/active-directory-privileged-identity-management-configure) at administrere dine roller for at give yderligere overvågning, kontrol og adgangsgennemsyn for brugere med katalogtilladelser.

Defender til Slutpunkt understøtter to måder at administrere tilladelser på:

- **Grundlæggende administration af tilladelser**: Angiv tilladelser til enten fuld adgang eller skrivebeskyttet. Brugere med globale administrator- eller sikkerhedsadministratorroller i Azure Active Directory har fuld adgang. Sikkerhedslæserrollen har skrivebeskyttet adgang og giver ikke adgang til visning af maskiner/lager af enheder.

- **Rollebaseret adgangskontrol :** Angiv detaljerede tilladelser ved at definere roller, tildele Azure AD-brugergrupper til rollerne og give brugergrupperne adgang til enhedsgrupper. Få mere at vide. Se [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

Microsoft anbefaler, at du udnytter RBAC for at sikre, at kun brugere, der har en forretningsberettigelse, kan få adgang til Defender til slutpunktet.

Du kan finde oplysninger om retningslinjer for tilladelser [her: Opret roller, og tildel rollen til Azure Active Directory gruppe](/microsoft-365/security/defender-endpoint/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group).

Følgende eksempeltabel bruges til at identificere strukturen for Cyber Defense Operations Center i dit miljø, som kan hjælpe dig med at bestemme den RBAC-struktur, der kræves til dit miljø.

<br>

****

|Niveau|Beskrivelse|Tilladelse påkrævet|
|---|---|---|
|Niveau 1|**Lokalt sikkerhedsteam/it-team** <p> Dette team undersøger og undersøger sædvanligvis beskeder, der er indeholdt i deres geoplacering, og eskalerer til niveau 2 i tilfælde, hvor en aktiv afhjælpning er påkrævet.||
|Niveau 2|**Regionalt sikkerhedsteam** <p> Dette team kan se alle enheder i deres område og udføre afhjælpningshandlinger.|Vis data|
|Niveau 3|**Global sikkerhedsteam** <p> Dette team består af sikkerhedseksperter og er autoriseret til at se og udføre alle handlinger fra portalen.|Vis data <p> Undersøgelse af beskeder Aktive afhjælpningshandlinger <p> Undersøgelse af beskeder Aktive afhjælpningshandlinger <p> Administrere indstillinger for portalsystem <p> Administrer sikkerhedsindstillinger|
||||

## <a name="adoption-order"></a>Indføringsordre

I mange tilfælde har organisationer eksisterende sikkerhedsprodukter til slutpunkter på plads. Det eneste minimum, hver organisation bør have været en antivirusløsning. Men i nogle tilfælde har en organisation muligvis også allerede Slutpunktsregistrering og -svar en løsning.

Historisk set erstatter en sikkerhedsløsning, der plejede at være tidsintensiv og svær at opnå på grund af de tæt kroge i programlaget og infrastrukturafhængighederne. Men da Defender til slutpunkt er indbygget i operativsystemet, er det nu nemt at erstatte tredjepartsløsninger.

Vælg den komponent af Defender, som slutpunktet skal bruges til, og fjern dem, der ikke er gældende. Tabellen nedenfor angiver den rækkefølge, som Microsoft anbefaler til, hvordan sikkerhedspakken til slutpunkter skal være aktiveret.

<br>

****

|Komponent|Beskrivelse|Rækkefølge af indføringsrækkefølge|
|---|---|---|
|Slutpunktsregistrering & svar (Slutpunktsregistrering og -svar)|Defender for Endpoint slutpunktsregistrering og -svar funktioner giver avancerede registreringer af angreb, der er næsten i realtid og kan handles på. Sikkerhedsanalytikere kan prioritere beskeder effektivt, få overblik over det fulde omfang af en overtrædelse og reagere på handlinger for at løse trusler. <p> [Lær mere.](/windows/security/threat-protection/windows-defender-atp/overview-endpoint-detection-response)|1|
|Administration & af trusselssikkerhedsrisiko (TVM)|Threat & Vulnerability Management er en komponent i Microsoft Defender til slutpunkt og giver både sikkerhedsadministratorer og sikkerhedsteams unik værdi, herunder: <ul><li>Indsigter i realtid slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) korreleret med slutpunktsrisici</li><li>Uvurderlig enhedssikkerhedsrisiko under hændelsesundersøgelse</li><li>Indbyggede afhjælpningsprocesser via Microsoft Intune og Microsoft System Center Configuration Manager</li></ul> <p> [Få mere at vide](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Introducing-a-risk-based-approach-to-threat-and-vulnerability/ba-p/377845).|2|
|Næste generations beskyttelse (NGP)|Microsoft Defender Antivirus er en indbygget antimalwareløsning, der giver næste generations beskyttelse til stationære computere, bærbare computere og servere. Microsoft Defender Antivirus indeholder: <ul><li>Cloud-leveret beskyttelse til øjeblikkelig registrering og blokering af nye og nye trusler. Ud over maskinlæring og intelligent sikkerheds Graph er cloud-leveret beskyttelse en del af den næste generation af teknologier, der Microsoft Defender Antivirus.</li><li>Scanner altid ved hjælp af avanceret overvågning af fil- og procesfunktionsmåder og andre heuristiske funktioner (også kaldet "beskyttelse i realtid").</li><li>Dedikerede opdateringer til beskyttelse, der er baseret på maskinlæring, mennesker og automatiseret analyse af big-data og dybdegående forskning om trusselsmodstand.</li></ul> <p> [Få mere at vide](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10).|3|
|Reduktion af angrebsoverfladen (ASR)|Funktioner til reduktion af angrebsoverfladen i Microsoft Defender til Slutpunkt hjælper med at beskytte enheder og programmer i organisationen mod nye og fremspirende trusler. <br> [Lær mere.](/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction)|4|
|Automatisk afhjælpning & undersøgelse (AIR)|Microsoft Defender til Slutpunkt bruger automatiserede undersøgelser til at reducere mængden af beskeder, der skal undersøges individuelt. Funktionen Automatiseret undersøgelse udnytter forskellige inspektionsalgoritmer og processer, der bruges af analytikere (f.eks. playbooks), til at undersøge vigtige beskeder og omgående afhjælpe eventuelle overtrædelser. Dette reducerer mængden af beskeder betydeligt, så sikkerhedseksperter kan fokusere på mere avancerede trusler og andre initiativer med høj værdi. <p> [Lær mere.](/windows/security/threat-protection/windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection)|Ikke relevant|
|Microsoft-trusselseksperter (MTE)|Microsoft-trusselseksperter er en administreret jagttjeneste, der leverer SECURITY Operation Centers (SOCs) med ekspertniveauovervågning og -analyse for at hjælpe dem med at sikre, at kritiske trusler i deres unikke miljøer ikke overser. <p> [Lær mere.](/windows/security/threat-protection/windows-defender-atp/microsoft-threat-experts)|Ikke relevant|

## <a name="next-step"></a>Næste trin

![Fase 2: Konfiguration.](images/setup.png) <br> [Fase 2: Konfiguration](production-deployment.md)

Konfigurer Microsoft Defender til udrulning af Slutpunkt.
