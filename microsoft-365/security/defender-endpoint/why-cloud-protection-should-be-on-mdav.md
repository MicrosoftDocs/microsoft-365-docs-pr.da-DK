---
title: Derfor skal skybeskyttelse være aktiveret for Microsoft Defender Antivirus
description: Se, hvorfor skybeskyttelse skal være slået til for Microsoft Defender Antivirus. Det hjælper mange sikkerhedsfunktioner i Microsoft Defender for Endpoint arbejde
keywords: Microsoft Defender Antivirus, skybeskyttelse, sikkerhedsfunktioner, eksempelindsendelse
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/22/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 65bd7dd0a494cd5b68216265015e80f1f003a5cb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467065"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Derfor skal skybeskyttelse være aktiveret for Microsoft Defender Antivirus

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Microsoft Defender Antivirus skybeskyttelse beskytter mod malware på dine slutpunkter og på tværs af dit netværk. Vi anbefaler, at du holder skybeskyttelse slået til, fordi visse sikkerhedsfunktioner og funktioner i Microsoft Defender for Endpoint kun fungerer, når skybeskyttelse er aktiveret. 

[![alt-text="Diagram, der viser ting, der afhænger af skybeskyttelse](images/mde-cloud-protection.png#lightbox)](enable-cloud-protection-microsoft-defender-antivirus.md)

Følgende tabel opsummerer de funktioner og funktioner, der afhænger af skybeskyttelse: <br/><br/>

| Funktion/funktion  | Abonnementskrav |  Beskrivelse  |
|---------|---------|--------|
| Kontrollerer mod metadata i skyen  | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Den Microsoft Defender Antivirus skytjeneste bruger maskinlæringsmodeller som et ekstra lag af forsvar. Disse modeller til maskinel indlæring omfatter metadata, så når der registreres en mistænkelig eller skadelig fil, kontrolleres dens metadata. <br/><br/>Du kan få mere [at vide på Blog: Lær de avancerede teknologier at kende som kernen Microsoft Defender for Endpoint næste generations beskyttelse](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Skybeskyttelse og indsendelse af eksempler | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Filer og eksekverbare filer kan sendes Microsoft Defender Antivirus skytjenesten til detonation og analyse. <br/><br/>Du kan få mere at vide [under Beskyttelse i skyen og indsendelse af eksempler Microsoft Defender Antivirus](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**BEMÆRK**: Automatisk indsendelse af eksempler er afhængig af skybeskyttelse, men det kan også konfigureres som en separat indstilling.         |
| Beskyttelse mod tæmmer | Microsoft Defender for Endpoint plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E5) | Tamper protection hjælper med at beskytte dig mod uønskede ændringer i organisationens sikkerhedsindstillinger. Hvis du vil gennemtvinge beskyttelse mod tæmme i Microsoft 365 Defender-portalen, skal skybeskyttelse være aktiveret. <br/><br/>Du kan få mere at vide [under Beskyt sikkerhedsindstillinger med tæmmebeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| Bloker ved første synsvidens | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Bloker ved første syn registrerer ny malware og blokerer den inden for få sekunder. Når der registreres en mistænkelig eller skadelig fil, kan du blokere ved første synsegenskaber forespørge cloudbeskyttelses-backend og anvender heuristics, maskinlæring og automatiseret analyse af filen for at afgøre, om det er en trussel.<br/><br/>Du kan få mere at vide [under Hvad er "blok ved første syn"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Opdateringer af nødsignaturer | Microsoft Defender for Endpoint plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E5) | Når skadeligt indhold registreres, installeres der signatureopdateringer og løsninger ved nødstilfælde. I stedet for at vente på den næste almindelige opdatering kan du modtage disse rettelser og opdateringer inden for få minutter.   |
| Slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand | Microsoft Defender for Endpoint plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E5) | Slutpunktsregistrering og -svar bloktilstand giver ekstra beskyttelse, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt på en enhed. Slutpunktsregistrering og -svar blokeringstilstand afhjælper artefakter, der blev fundet under Slutpunktsregistrering og -svar-genererede scanninger, som den primære antivirusløsning, der ikke er Microsoft, kan være gået glip af. Når det er aktiveret for enheder med Microsoft Defender Antivirus som den primære antivirusløsning, giver Slutpunktsregistrering og -svar i bloktilstand den ekstra fordel ved automatisk afhjælpning af artefakter, der er identificeret under Slutpunktsregistrering og -svar-genererede scanninger. <br/><br/>Du kan få mere at vide [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md).|
| Regler for reduktion af angrebsoverflade | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Reduktion af angrebsoverfladen handler om at reducere antallet af steder, og hvordan din organisations slutpunkter er sårbar over for cyberangreb. Regler for reduktion af angrebsoverfladen er intelligente regler, som du kan konfigurere for at stoppe malware. Visse regler kræver, at skybeskyttelse er slået til for at fungere fuldt ud. Disse regler omfatter: <br/>- Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders- eller pålidelige listekriterier <br/>- Brug avanceret beskyttelse mod ransomware <br/>- Bloker upålidelige programmer fra at køre fra flytbare drev <br/><br/>Du kan få mere at vide [under Brug regler for reduktion af angrebsoverfladen til at forhindre malware inficeret](attack-surface-reduction.md).  |
| Indikatorer for forlig (IoCs) | Microsoft Defender for Endpoint plan 2 (Enkeltstående eller inkluderet i en plan som Microsoft 365 E5) | IoCs i Defender til slutpunkt kan konfigureres til at definere registrering, forebyggelse og udelukkelse af enheder. Eksempelvis kan "tillad"-indikatorer bruges til at definere undtagelser til Microsoft Defender Antivirus til scanninger og afhjælpningshandlinger i Defender til Slutpunkt. Som et andet eksempel kan indikatorer for "påmindelser og blokering" bruges til at forhindre filer eller processer i at blive udført, og til at spore disse aktiviteter med beskeder, der kan ses i Microsoft 365 Defender-portalen. <br/><br/>Du kan få mere at vide [under Opret indikatorer](manage-indicators.md).    |

> [!TIP]
> Du kan få mere at vide om Defender for [Endpoint-planer Microsoft Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Næste trin

Nu hvor du har et overblik over skybeskyttelse og dens rolle i Microsoft Defender Antivirus, er her nogle næste trin:

1. **[Aktivér skybeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)**. Du kan aktivere skybeskyttelse med Microsoft Endpoint Manager (som nu omfatter Microsoft Endpoint Configuration Manager og Microsoft Intune), Gruppepolitik eller PowerShell-cmdlet'er.

2. **[Angiv skybeskyttelsesniveauet](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Du kan angive det beskyttelsesniveau, skyen skal tilbyde, ved hjælp Microsoft Endpoint Manager eller Gruppepolitik. Beskyttelsesniveauet påvirker mængden af oplysninger, der deles med skyen, og hvor aggressive nye filer blokeres.

3. **[Konfigurer og valider netværksforbindelser for Microsoft Defender Antivirus](configure-network-connections-microsoft-defender-antivirus.md)**. Der er visse Microsoft-URL-adresser, som dit netværk og slutpunkter skal kunne oprette forbindelse til for at skybeskyttelse kan fungere effektivt. I denne artikel vises de URL-adresser, der skal være tilladt via firewall eller regler for netværksfiltrering, og instruktioner til at bekræfte, at dit netværk er tilmeldt skybeskyttelse korrekt.

4. **[Konfigurer funktionen "Blok ved første syn"](configure-block-at-first-sight-microsoft-defender-antivirus.md)**. Funktionen "Bloker ved første syn" kan blokere ny malware inden for få sekunder uden at skulle vente timer på traditionel sikkerhedsintelligens. Du kan aktivere og konfigurere den ved hjælp af Microsoft Endpoint Manager eller Gruppepolitik.

5. **[Konfigurere timeoutperiode for skyblokering](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. Microsoft Defender Antivirus kan blokere mistænkelige filer fra at køre, mens den forespørger på vores skybeskyttelsestjeneste. Du kan konfigurere, hvor lang tid filen skal være forhindret i at køre ved hjælp Microsoft Endpoint Manager eller Gruppepolitik.
