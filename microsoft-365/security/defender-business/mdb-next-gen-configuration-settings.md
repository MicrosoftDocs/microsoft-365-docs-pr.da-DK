---
title: Forstå konfigurationsindstillinger for næste generations beskyttelse i Microsoft Defender for Business
description: Forstå konfigurationsindstillinger for næste generations beskyttelse i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 263d6457c8e913bdd3d8224af71f201156e24b5a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63598571"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Forstå næste generations konfigurationsindstillinger i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Næste generations beskyttelse i Defender for Business omfatter robust antivirus- og antimalwarebeskyttelse. Dine standardpolitikker er designet til at beskytte dine enheder og brugere uden at forhindre produktivitet. Du kan dog også tilpasse dine politikker, så de passer til virksomhedens behov. Og hvis du bruger en Microsoft Endpoint Manager, kan du bruge den til at administrere dine sikkerhedspolitikker.

**I denne artikel beskrives følgende**:

- [Næste generations beskyttelsesindstillinger og -indstillinger](#next-generation-protection-settings-and-options)

- [Andre forudkonfigurerede indstillinger i Defender for Business](#other-preconfigured-settings-in-defender-for-business) 

- [Standardindstillinger og -indstillinger for Defender for Business Microsoft Endpoint Manager](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Næste generations beskyttelsesindstillinger og -indstillinger

I følgende tabel vises dine indstillinger og indstillinger:<br/><br/>

| Indstilling | Beskrivelse |
|:---|:---|
| **Beskyttelse i realtid**  |  |
| **Slå beskyttelse i realtid til** | Beskyttelse i realtid er aktiveret som standard og finder og stopper malware fra at køre på enheder. *Vi anbefaler, at beskyttelse i realtid er slået til.*<br/><br/>Når beskyttelse i realtid er slået til, konfigureres følgende indstillinger:<br/>- Overvågning af adfærd er slået til ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- Alle downloadede filer og vedhæftede filer scannes ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Scripts, der bruges i Microsoft-browsere, scannes ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Bloker ved første synsvidens** | Aktiveret som standard blokerer ved første syn mod malware i løbet af få sekunder efter registrering, øger tiden (i sekunder), der får tilladelse til at sende eksempelfiler til analyse, og indstiller registreringsniveauet til Høj. *Vi anbefaler, at blok ved første syn er slået til.*<br/><br/>Når blok ved første syn er slået til, konfigureres følgende indstillinger for Microsoft Defender Antivirus: <br/>- Blokering og scanning af mistænkelige filer er indstillet til niveauet Høj blokering ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>- Antallet af sekunder, som en fil skal blokeres og kontrolleres i, er angivet til 50 sekunder ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**VIGTIGT**: Hvis blok ved første syn er slået fra, påvirker det og `CloudBlockLevel` `CloudExtendedTimeout` for Microsoft Defender Antivirus.  |
| **Slå netværksbeskyttelse til** | Når den er slået til, hjælper netværksbeskyttelse med at beskytte dig mod forsøg på phishing, udnyttelseshosting af websteder og skadeligt indhold på internettet. Det forhindrer også brugere i at slå netværksbeskyttelse fra.<br/><br/>Netværksbeskyttelse kan indstilles til en af følgende tilstande:<br/>- **Bloker** tilstand (denne indstilling er standard), som forhindrer brugere i at besøge websteder, der betragtes som usikre. *Vi anbefaler, at du holder netværksbeskyttelsen indstillet til bloktilstand.*<br/>- **Overvågningstilstand**, som giver brugerne mulighed for at besøge websteder, der kan være usikre, og registrere netværksaktivitet til/fra sådanne websteder <br/>- **Deaktiveret tilstand**, som blokerer brugere fra at besøge websteder, der kan være usikre, eller som sporer netværksaktivitet til/fra sådanne websteder |
| **Afhjælpning**  |  |
| **Handling, der kan forårsage uønskede apps (PUA)** | PUA kan omfatte reklamesoftware, bundtningssoftware, der tilbyder at installere anden, usigneret software og software, der er til at efterse, og som forsøger at undgå sikkerhedsfunktioner. Selvom PUA ikke nødvendigvis er en virus, malware eller andre typer trusler, kan PUA påvirke enhedens ydeevne.<br/><br/>PUA-beskyttelse blokerer elementer, der registreres som PUA. Du kan angive PUA-beskyttelse til en af følgende indstillinger: <br/>- **Aktiveret** (denne indstilling er standard), som blokerer elementer, der er registreret som PUA på enheder. *Vi anbefaler, at du holder PUA-beskyttelse aktiveret.*<br/>- **Overvågningstilstand**, som ikke kræver en handling på elementer, der er registreret som PUA <br/>- **Deaktiveret**, som ikke registrerer eller handler på elementer, der kan være PUA |
| **Scan**   |  |
| **Planlagt scanningstype** | Overvej at køre en ugentlig antivirusscanning på dine enheder. Du kan vælge mellem følgende indstillinger for scanningstype: <br/>- **Quickscan kontrollerer** placeringer, f.eks. registreringsdatabasenøgler og startmapper, hvor der kunne registreres malware for at starte med en enhed. *Vi anbefaler, at du bruger indstillingen Hurtig kant.* <br/>- **Fullscan** kontrollerer alle filer og mapper på en enhed <br/>- **Deaktiveret** betyder, at der ikke sker planlagte scanninger. Brugere kan stadig køre scanninger på deres egne enheder. (Generelt anbefaler vi ikke, at du deaktiverer dine planlagte scanninger).) <br/><br/> [Få mere at vide om scanningstyper](../defender-endpoint/schedule-antivirus-scans.md). |
| **Ugedag til at køre en planlagt scanning** | Vælg en dag, hvor dine almindelige ugentlige antivirusscanninger skal køre. |
| **Tidspunkt på dagen for at køre en planlagt scanning** | Vælg et tidspunkt, hvor du vil køre dine regelmæssigt planlagte antivirusscanninger. |
| **Brug lav ydeevne** | Denne indstilling er som standard slået fra. *Vi anbefaler, at du holder denne indstilling slået fra.* Du kan dog slå denne indstilling til for at begrænse enhedens hukommelse og ressourcer, der bruges under planlagte scanninger. <br/><br/>**VIGTIGT** Hvis du slår **Brug lav ydeevne** til, konfigureres følgende indstillinger for Microsoft Defender Antivirus: <br/>- Arkivfiler scannes ikke ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- Scanninger tildeles en lav CPU-prioritet ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Hvis en fuld antivirusscanning mistes, køres der ingen opfristningsscan ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Hvis en hurtig antivirusscanning mistes, vil der ikke blive kørt en opfrisket scanning ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Reducerer den gennemsnitlige CPU-indlæsningsfaktor under en antivirusscanning fra 50 % til 20 % ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Brugeroplevelse**   |  |
| **Give brugere adgang til Windows Sikkerhed appen** | Slå denne indstilling til for at give brugerne mulighed for at Windows Sikkerhed appen på deres enheder. Brugere kan ikke tilsidesætte indstillinger, som du konfigurerer i Microsoft Defender for Business, men de vil kunne køre en hurtig scanning, hvis det er nødvendigt, eller se registrerede trusler. |
| **Udeladelse af antivirus** | Udeladelse er processer, filer eller mapper, der ignoreres ved Microsoft Defender Antivirus scanninger. *Generelt set behøver du ikke at definere udeladelse.* Microsoft Defender Antivirus omfatter mange automatiske udeladelsesfiler, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler.<br/><br/>[Få mere at vide om udeladelse](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Procesudetagelser** | Procesudetagelser forhindrer filer, der åbnes af bestemte processer, i at blive scannet af Microsoft Defender Antivirus. <br/><br/>[Få mere at vide om procesude udeladelse](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Udeladelse af filtypenavn** | Udeladelse af filtypenavne forhindrer filer med bestemte filtyper i at blive scannet af Microsoft Defender Antivirus.<br/><br/>[Få mere at vide om udeladelse af filtypenavn](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Udeladelse af filer og mapper** | Udeladelse af filer og mapper forhindrer filer, der findes i bestemte mapper, i at blive scannet af Microsoft Defender Antivirus. <br/><br/>[Få mere at vide om udeladelse af filer og mapper](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Andre forudkonfigurerede indstillinger i Defender for Business

Følgende sikkerhedsindstillinger er forudkonfigureret i Defender for Business:

- Scanning af flytbare drev er slået til ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))

- Daglige hurtige scanninger har ikke et foruddefineret tidspunkt ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))

- Sikkerhedsintelligensopdateringer kontrolleres, før en antivirusscan kører ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))

- Sikkerhedsvidenskontroller udføres hver fjerde time ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>Standardindstillinger og -indstillinger for Defender for Business Microsoft Endpoint Manager

I følgende tabel beskrives de indstillinger, der er forudkonfigureret til Defender for Business, og hvordan disse indstillinger svarer til det, du muligvis ser i Microsoft Endpoint Manager (eller Microsoft Intune). Hvis du bruger den [forenklede konfigurationsproces i Defender for Business (prøveversion](mdb-simplified-configuration.md) ), behøver du ikke at redigere disse indstillinger.
<br/><br/>

| Indstilling  | Beskrivelse  |
|---------|---------|
| [Skybeskyttelse](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Nogle gange kaldet cloud-leveret beskyttelse eller Microsoft Advanced Protection Service (MAPS), fungerer skybeskyttelse med Microsoft Defender Antivirus og Microsoft Cloud til at identificere nye trusler, nogle gange før en enkelt enhed påvirkes. Som standard er [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) slået til. <br/><br/>[Få mere at vide om skybeskyttelse](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Overvågning af indgående og udgående filer](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | For at overvåge indgående og udgående [filer er RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) indstillet til at overvåge alle filer.         |
| [Scan netværksfiler](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Som standard er [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) ikke aktiveret, og netværksfiler scannes ikke. |
| [Scan mails](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Som standard [er AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) ikke aktiveret, og mails scannes ikke. |
| [Antal dage (0-90) til at beholde malware i karantæne](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Som standard er [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) indstillet til nul (0) dage. Artefakter, der er i karantæne, fjernes ikke automatisk.  |
| [Indsend samtykke til eksempler](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | [SubmitSamplesConsent bruges som standard](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) til automatisk at sende sikre eksempler. Eksempler på sikre eksempler omfatter `.bat`, `.scr`, `.dll`og filer `.exe` , der ikke indeholder personidentificerbare oplysninger (PII). Hvis en fil indeholder pii, modtager brugeren en anmodning om at tillade, at eksempelindsendelsen fortsætter.<br/><br/>[Få mere at vide om skybeskyttelse og indsendelse af eksempler](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Scan flytbare drev](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) er som standard konfigureret til at scanne flytbare drev, f.eks. USB-miniaturedrev på enheder.<br/><br/>[Få mere at vide om indstillinger for antimalwarepolitik](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Kør den daglige hurtig scanningstid](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Som standard [er ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) indstillet til 02:00.<br/><br/>[Få mere at vide om indstillinger for scanning](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Søg efter signaturopdateringer, før scanningen køres](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Som standard er [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) konfigureret til at søge efter sikkerhedsintelligensopdateringer, før du kører antivirus-/antimalwarescanninger.<br/><br/>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [og sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Hvor ofte (0-24 timer) der skal søges efter sikkerhedsintelligensopdateringer](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | [SignatureUpdateInterval er som standard](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) konfigureret til at søge efter sikkerhedsintelligensopdateringer hver fjerde time.<br/><br/>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [og sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Se også

- [Gå til Microsoft 365 Defender portalen](mdb-get-started.md)

- [Administrer indstillinger for firewall i Microsoft Defender for Business](mdb-custom-rules-firewall.md)

- [CSP for politik – Defender](/windows/client-management/mdm/policy-csp-defender)