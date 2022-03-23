---
title: Nyheder i Microsoft Secure Score
description: Beskriver, hvilke nye ændringer der er sket med Microsoft Secure Score på Microsoft 365 Defender-portalen.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 72bd56905392ff89fbcd3209212029d3b33b9a98
ms.sourcegitcommit: cfcdb11cc5d39c6c71a34e09c03e8859cd6708d3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63592890"
---
# <a name="whats-new-in-microsoft-secure-score"></a>Nyheder i Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

For at gøre Microsoft Secure Score til en bedre repræsentant for din sikkerhedspost har vi foretaget nogle ændringer. Du kan få mere at vide om planlagte [ændringer under Hvad kommer der med Microsoft Secure Score?](microsoft-secure-score-whats-coming.md)

Microsoft Secure Score kan findes på https://security.microsoft.com/securescore [Microsoft 365 Defender-portalen](microsoft-365-defender.md#the-microsoft-365-defender-portal).

## <a name="july-2021"></a>Juli 2021

### <a name="added-improvement-action-related-to-microsoft-teams"></a>Der er blevet tilføjet en forbedringshandling i forbindelse med Microsoft Teams

- Begræns opkaldsbrugeres adgang til at springe en mødelobbyen over
- Begræns eksterne deltagere fra at have kontrol i Teams møde
- Begræns anonyme brugere fra Teams møder
- Kræv, at der skal konfigureres lobbymøder Teams møder
- Konfigurere, hvilke brugere der har tilladelse til at være til stede Teams møder

### <a name="added-improvement-action-related-to-microsoft-defender-for-endpoint"></a>Der er blevet tilføjet en forbedringshandling relateret til Microsoft Defender til slutpunkt

- Ret data om Sensor i Microsoft Defender til Endpoint til macOS
- Ret problemer med Microsoft Defender til slutpunktshæmmet kommunikation til macOS
- Angiv minimum adgangskodelængde til 15 eller flere tegn i macOS
- Angiv "Gennemtving adgangskodehistorik" til "24 eller flere adgangskoder)" i macOS
- Angiv "Maksimal adgangskodealder" til "90 dage eller færre, men ikke 0" i macOS
- Angiv grænseværdien for spærring af konto til 5 eller lavere i macOS
- Slå firewallen til på macOS
- Aktivér Gatekeeper
- Aktivér beskyttelse af systemintegritet (SIP)
- Aktivér diskkryptering i FileVault
- Indstil skærm til låsning, når screensaver starter i macOS
- Sørg for, at pauseskærm er indstillet til at starte på 20 minutter eller mindre i macOS
- Sikre private mapper
- Slå beskyttelse Microsoft Defender Antivirus til i realtid til macOS
- Aktivér Microsoft Defender Antivirus PUA-beskyttelse i bloktilstand for macOS
- Aktivér Microsoft Defender Antivirus cloud-leveret beskyttelse til macOS
- Opdater Microsoft Defender Antivirus definitioner for macOS
- Løs problemer med indsamling af sensordata for Microsoft Defender til Endpoint til Linux
- Ret problemer med Microsoft Defender til slutpunktshæmmet kommunikation til Linux
- Ikke-tilgås-konti
- Aktivere Microsoft Defender Antivirus beskyttelse i realtid til Linux
- Aktivér Microsoft Defender Antivirus PUA-beskyttelse i bloktilstand til Linux
- Aktivér Microsoft Defender Antivirus cloud-leveret beskyttelse til Linux
- Opdater Microsoft Defender Antivirus definitioner til Linux

## <a name="june-2021"></a>Juni 2021

### <a name="removed-improvement-action-related-to-microsoft-cloud-app-security"></a>Forbedringshandling, der er relateret til Microsoft Cloud App Security

- Brug Cloud App Security til at registrere unormal funktionsmåde.

## <a name="february-2021"></a>I februar 2021

### <a name="compatibility-with-graph-api"></a>Kompatibilitet med Graph API

Microsoft Secure Score-anbefalinger leveret via Graph API ser ud og bliver vægtet på samme måde som de anbefalinger, du aktuelt ser på Microsoft 365 Defender portal.

## <a name="january-2021"></a>Januar 2021

### <a name="added-our-first-security-recommendation-for-microsoft-teams"></a>Vores første sikkerhedsanbefaling for Microsoft Teams

Microsoft Teams vil se "Begræns anonyme brugere i at deltage i møder" som en ny forbedringshandling i Secure Score.

## <a name="december-2020"></a>december 2020

### <a name="added-six-accounts-related-improvement-actions-for-microsoft-defender-for-endpoint"></a>Seks kontorelaterede forbedringshandlinger for Microsoft Defender til Slutpunkt er blevet tilføjet:

- Angiv "Minimum adgangskodelængde" til "14 eller flere tegn"
- Angiv "Gennemtving adgangskodehistorik" til "24 eller flere adgangskoder)"
- Angiv "Maksimal adgangskodealder" til "60 dage eller færre, men ikke 0"
- Angiv "Minimumsalder for adgangskode" til "1 eller flere dage)"
- Deaktiver den indbyggede administratorkonto
- Deaktiver den indbyggede gæstekonto

## <a name="november-2020"></a>november 2020

### <a name="removed-the-ability-to-create-servicenow-tickets-through-secure-score"></a>Muligheden for at oprette ServiceNow-billetter blev fjernet via Secure Score 

Muligheden for at oprette ServiceNow-billetter via Secure Score ved at **gå til Del > ServiceNow** er ikke længere tilgængelig. Tak for din feedback og fortsatte support, mens vi fastlægger de næste trin.

### <a name="added-three-services-related-improvement-actions-for-microsoft-defender-for-endpoint"></a>Tre tjenesterelaterede forbedringshandlinger er blevet tilføjet for Microsoft Defender til Slutpunkt:

- Ret ikke-angivet tjenestesti for Windows tjenester
- Ændre eksekverbar sti for tjenesten til en fælles beskyttet placering
- Skift tjenestekonto for at undgå cachelagret adgangskode i Windows-registreringsdatabasen

## <a name="october-2020"></a>Oktober 2020

### <a name="removed-improvement-action-related-to-microsoft-defender-for-endpoint"></a>Forbedringshandling, der er relateret til Microsoft Defender til Slutpunkt, er blevet fjernet

- Indstil Microsoft Defender SmartScreen Windows Store app-webindholdskontrol for at advare

## <a name="august-2020"></a>August 2020

### <a name="updated-improvement-action-for-azure-active-directory"></a>Opdateret forbedringshandling for Azure Active Directory

- Aktivér politik for at blokere ældre godkendelse

## <a name="incompatibility-with-identity-secure-score"></a>Manglendekompatibilitet med Identity Secure Score

I den seneste version af Microsoft Secure Score blev der udgivet en forbedret pointmodel. Disse ændringer giver mulighed for en mere fleksibel og nøjagtig visning af din sikkerhedsstilling. Disse opdateringer har dog gjort Microsoft Secure Score midlertidigt inkompatibel med Identity Secure Score.

Med tiden vil Identity Secure Score indføre den nye pointmodel. Indtil da vil kunderne se forskelle i de resultater, der rapporteres af Microsoft Secure Score og Identity Secure Score. Vi beklager ulejligheden af dette og arbejder på at sikre, at disse oplevelser bliver mere kompatible i fremtiden.

## <a name="updated-improvement-actions"></a>Opdaterede forbedringshandlinger

- Tilføjede Azure Active Directory forbedringshandlinger
- Tilføjede forbedringshandlinger for Microsoft Defender for Identity
- Understøttelse af Microsoft Defender til Endpoint [Threat & anbefalinger til sikkerhedsanbefalinger](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) i forbindelse med sikkerhedsrisiko
    - Alle udgivne sikkerhedsanbefalinger leveret af TVM er nu tilgængelige

## <a name="updated-interface-and-functionality"></a>Opdateret brugergrænseflade og funktionalitet

* Alle nye metrikværdier og tendensvisninger for CISO og diskussioner på kundeemneniveau
* Nye måder at spore og benchmarke dine resultater på
* Bedre sporing og forståelse for regressioner af point
* Filtrere, mærke, søge og gruppere dine forbedringshandlinger
* Administrer mod dine fremtidige mål ved hjælp af scoreprojektioner og planlagte handlinger
* Og meget mere!

## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Hvis du har problemer, kan du fortælle os om det ved at slå et indlæg op i [community'et Sikkerhed, & Privacy Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Vi overvåger communityet og yder hjælp.

## <a name="related-resources"></a>Relaterede ressourcer

- [Vurder din sikkerhedsstilling](microsoft-secure-score-improvement-actions.md)
- [Spor din Microsoft Secure Score-historik, og opfylder mål](microsoft-secure-score-history-metrics-trends.md)
- [Hvad der kommer](microsoft-secure-score-whats-coming.md)
