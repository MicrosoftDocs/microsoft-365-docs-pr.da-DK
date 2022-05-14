---
title: Hvorfor skal cloudbeskyttelse aktiveres for Microsoft Defender Antivirus
description: Se, hvorfor skybeskyttelse skal være aktiveret for Microsoft Defender Antivirus. Det hjælper mange sikkerhedsfunktioner i Microsoft Defender for Endpoint arbejde
keywords: Microsoft Defender Antivirus, cloudbeskyttelse, sikkerhedsfunktioner, indsendelse af eksempel
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
ms.openlocfilehash: 195e929c0de1be9ab05f2685ba60e56c13dd3629
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415222"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Hvorfor skal cloudbeskyttelse aktiveres for Microsoft Defender Antivirus

**Gælder for:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platforme**
- Windows

Microsoft Defender Antivirus cloudbeskyttelse hjælper med at beskytte mod malware på dine slutpunkter og på tværs af dit netværk. Vi anbefaler, at skybeskyttelse er aktiveret, fordi visse sikkerhedsfunktioner og -funktioner i Microsoft Defender for Endpoint kun fungerer, når skybeskyttelse er aktiveret. 

[![alt-text="Diagram, der viser ting, der afhænger af skybeskyttelse](images/mde-cloud-protection.png#lightbox)](enable-cloud-protection-microsoft-defender-antivirus.md)

I følgende tabel opsummeres de funktioner og egenskaber, der afhænger af skybeskyttelse: <br/><br/>

| Funktion/funktionalitet  | Abonnementskrav |  Beskrivelse  |
|---------|---------|--------|
| Kontrol mod metadata i cloudmiljøet  | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Den Microsoft Defender Antivirus cloudtjeneste bruger modeller til maskinel indlæring som et ekstra forsvarslag. Disse modeller til maskinel indlæring indeholder metadata, så når der registreres en mistænkelig eller skadelig fil, kontrolleres dens metadata. <br/><br/>Du kan få mere at vide under [Blog: Lær de avancerede teknologier at kende i kernen af Microsoft Defender for Endpoint næste generations beskyttelse](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Skybeskyttelse og indsendelse af eksempler | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Filer og eksekverbare filer kan sendes til Microsoft Defender Antivirus cloudtjenesten med henblik på detonation og analyse. <br/><br/>Du kan få mere at vide under [Cloud protection og indsendelse af eksempler i Microsoft Defender Antivirus](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**BEMÆRK**! Automatisk indsendelse af eksempler afhænger af cloudbeskyttelse, selvom den også kan konfigureres som en separat indstilling.         |
| Ændringsbeskyttelse | Microsoft Defender for Endpoint Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E5) | Ændringsbeskyttelse hjælper med at beskytte mod uønskede ændringer af organisationens sikkerhedsindstillinger. Cloudbeskyttelse skal være aktiveret for at gennemtvinge manipulationsbeskyttelse på Microsoft 365 Defender portalen. <br/><br/>Du kan få mere at vide under [Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| Blok ved første øjekast | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Blok ved første øjekast registrerer ny malware og blokerer den inden for få sekunder. Når der registreres en mistænkelig eller skadelig fil, kan du ved første øjekast forespørge cloudbeskyttelses-backend og anvende heuristik, maskinel indlæring og automatiseret analyse af filen for at afgøre, om det er en trussel.<br/><br/>Du kan få mere at vide under [Hvad er "blok ved første øjekast"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Signaturopdateringer i nødstilfælde | Microsoft Defender for Endpoint Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E5) | Når der registreres skadeligt indhold, installeres der opdateringer og rettelser til nødsignaturen. I stedet for at vente på den næste almindelige opdatering kan du modtage disse rettelser og opdateringer på få minutter.   |
| Registrering af slutpunkt og svar (Slutpunktsregistrering og -svar) i bloktilstand | Microsoft Defender for Endpoint Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E5) | Slutpunktsregistrering og -svar i bloktilstand giver ekstra beskyttelse, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt på en enhed. Slutpunktsregistrering og -svar i bloktilstand afhjælper artefakter, der blev fundet under Slutpunktsregistrering og -svar genererede scanninger, som den primære antivirusløsning, der ikke er Microsoft, måske gik glip af. Når den er aktiveret for enheder med Microsoft Defender Antivirus som den primære antivirusløsning, giver Slutpunktsregistrering og -svar i bloktilstand den ekstra fordel, at artefakter, der identificeres under Slutpunktsregistrering og -svar genererede scanninger, afhjælpes automatisk. <br/><br/>Du kan få mere at vide under [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md).|
| Regler for reduktion af angrebsoverflade | Microsoft Defender for Endpoint Plan 1 eller Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E3 eller E5) | Reduktion af angrebsoverfladen handler om at reducere de steder og måder, din organisations slutpunkter er sårbare over for et cyberangreb på. Regler for reduktion af angrebsoverfladen er intelligente regler, som du kan konfigurere for at stoppe malware. Visse regler kræver, at cloudbeskyttelse er slået til for at fungere fuldt ud. Disse regler omfatter: <br/>- Bloker eksekverbare filer fra at køre, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til <br/>- Brug avanceret beskyttelse mod ransomware <br/>- Bloker programmer, der ikke er tillid til, fra at køre fra flytbare drev <br/><br/>Du kan få mere at vide under [Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion](attack-surface-reduction.md).  |
| Indikatorer for kompromis (IoCs) | Microsoft Defender for Endpoint Plan 2 (separat eller inkluderet i en plan som Microsoft 365 E5) | IoCs i Defender for Endpoint kan konfigureres til at definere registrering, forebyggelse og udeladelse af enheder. "Tillad"-indikatorer kan f.eks. bruges til at definere undtagelser for Microsoft Defender Antivirus scanninger og afhjælpningshandlinger i Defender for Endpoint. Som et andet eksempel kan indikatorer for "besked og blokering" bruges til at forhindre, at filer eller processer udføres, og til at spore disse aktiviteter med beskeder, der kan ses på Microsoft 365 Defender portalen. <br/><br/>Du kan få mere at vide under [Opret indikatorer](manage-indicators.md).    |

> [!TIP]
> Hvis du vil vide mere om Defender for Endpoint-planer, [skal du se Microsoft Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Næste trin

Nu, hvor du har et overblik over skybeskyttelse og dens rolle i Microsoft Defender Antivirus, er her nogle næste trin:

1. **[Aktivér beskyttelse i skyen](enable-cloud-protection-microsoft-defender-antivirus.md)**. Du kan aktivere skybeskyttelse med Microsoft Endpoint Manager (som nu omfatter Microsoft Endpoint Configuration Manager og Microsoft Intune), Gruppepolitik eller PowerShell-cmdlet'er.

2. **[Angiv niveauet for skybeskyttelse](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Du kan angive det beskyttelsesniveau, skyen tilbyder, ved hjælp af Microsoft Endpoint Manager eller Gruppepolitik. Beskyttelsesniveauet påvirker mængden af oplysninger, der deles med cloudmiljøet, og hvor aggressivt nye filer blokeres.

3. **[Konfigurer og valider netværksforbindelser for Microsoft Defender Antivirus](configure-network-connections-microsoft-defender-antivirus.md)**. Der er visse Microsoft URL-adresser, som dit netværk og dine slutpunkter skal kunne oprette forbindelse til, for at cloudbeskyttelsen kan fungere effektivt. Denne artikel indeholder en liste over de URL-adresser, der skal tillades via firewall- eller netværksfiltreringsregler, og instruktioner til bekræftelse af dit netværk er korrekt tilmeldt cloudbeskyttelse.

4. **[Konfigurer funktionen "blok ved første øjekast"](configure-block-at-first-sight-microsoft-defender-antivirus.md)**. Funktionen "blok ved første øjekast" kan blokere ny malware inden for få sekunder uden at skulle vente timer på traditionel sikkerhedsintelligens. Du kan aktivere og konfigurere den ved hjælp af Microsoft Endpoint Manager eller Gruppepolitik.

5. **[Konfigurer timeoutperioden for skyblokering](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. Microsoft Defender Antivirus kan blokere for kørsel af mistænkelige filer, mens den sender forespørgsler til vores cloudbeskyttelsestjeneste. Du kan konfigurere, hvor lang tid filen skal forhindres i at køre, ved hjælp af Microsoft Endpoint Manager eller Gruppepolitik.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)