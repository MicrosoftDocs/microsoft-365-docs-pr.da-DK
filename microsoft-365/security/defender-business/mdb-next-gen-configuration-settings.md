---
title: Om konfigurationsindstillinger for næste generation af beskyttelse i Microsoft Defender til virksomheder
description: Forstå konfigurationsindstillingerne for næste generations beskyttelse i Microsoft Defender til virksomheder
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
ms.openlocfilehash: a5ffc97c6b2cfd1016da1f218ab2a16c153a5528
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666278"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Om næste generations konfigurationsindstillinger i Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra den 1. marts 2022. Defender for Business som et separat abonnement fås som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Prøveversionen indeholder et [indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

Næste generations beskyttelse i Defender for Business omfatter robust beskyttelse mod antivirus og antimalware. Dine standardpolitikker er udviklet til at beskytte dine enheder og brugere uden at hindre produktiviteten. Du kan dog også tilpasse dine politikker, så de passer til dine forretningsbehov. Og hvis du bruger Microsoft Endpoint Manager, kan du bruge det til at administrere dine sikkerhedspolitikker.

**I denne artikel beskrives**:

- [Næste generations beskyttelsesindstillinger](#next-generation-protection-settings-and-options)

- [Andre forudkonfigurerede indstillinger i Defender for Business](#other-preconfigured-settings-in-defender-for-business) 

- [Standardindstillinger og Microsoft Endpoint Manager for Defender for Business](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Næste generations beskyttelsesindstillinger

I følgende tabel vises dine indstillinger og indstillinger:<br/><br/>

| Indstilling | Beskrivelse |
|:---|:---|
| **Beskyttelse i realtid**  |  |
| **Slå beskyttelse i realtid til** | Aktiveret som standard finder og stopper beskyttelse i realtid malware fra at køre på enheder. *Vi anbefaler, at beskyttelse i realtid er slået til.*<br/><br/>Når beskyttelse i realtid er slået til, konfigurerer den følgende indstillinger:<br/>– Overvågning af funktionsmåde er slået til ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>– Alle downloadede filer og vedhæftede filer scannes ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Scripts, der bruges i Microsoft-browsere, scannes ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Blok ved første øjekast** | Aktiveret som standard blokerer ved første øjekast malware inden for sekunder efter registrering, øger den tid (i sekunder), der tillades til at indsende eksempelfiler til analyse, og indstiller dit registreringsniveau til Høj. *Vi anbefaler, at blok ved første øjekast er slået til.*<br/><br/>Når blok ved første øjekast er slået til, konfigurerer den følgende indstillinger for Microsoft Defender Antivirus: <br/>- Blokering og scanning af mistænkelige filer er indstillet til niveauet Høj blokering ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>– Antallet af sekunder for en fil, der skal blokeres og kontrolleres, er indstillet til 50 sekunder ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**VIGTIGT**! Hvis blok ved første øjekast er slået fra, påvirker `CloudBlockLevel` det og `CloudExtendedTimeout` for Microsoft Defender Antivirus.  |
| **Slå netværksbeskyttelse til** | Når netværksbeskyttelse er slået til, hjælper den med at beskytte mod phishing, websteder, der udnytter websteder, og skadeligt indhold på internettet. Det forhindrer også brugerne i at slå netværksbeskyttelse fra.<br/><br/>Netværksbeskyttelse kan indstilles til en af følgende tilstande:<br/>- **Bloktilstand** (denne indstilling er standard), hvilket forhindrer brugerne i at besøge websteder, der anses for at være usikre. *Vi anbefaler, at netværksbeskyttelse er indstillet til bloktilstand.*<br/>- **Overvågningstilstand**, som giver brugerne mulighed for at besøge websteder, der kan være usikre, og sporer netværksaktivitet til/fra sådanne websteder <br/>- **Deaktiveret tilstand**, som forhindrer brugere i at besøge websteder, der kan være usikre, eller sporer netværksaktivitet til/fra sådanne websteder |
| **Oprydning**  |  |
| **Handling, der skal udføres på potentielt uønskede apps (PUA)** | PUA kan omfatte reklame software, bundling software, der tilbyder at installere andre, usigneret software, og undvige software, der forsøger at undgå sikkerhedsfunktioner. Selvom PUA ikke nødvendigvis er en virus, malware eller andre typer trusler, kan PUA påvirke enhedens ydeevne.<br/><br/>PUA-beskyttelse blokerer elementer, der registreres som PUA. Du kan angive PUA-beskyttelse til en af følgende indstillinger: <br/>- **Aktiveret** (denne indstilling er standard), der blokerer elementer, der er registreret som PUA på enheder. *Vi anbefaler, at PUA-beskyttelse bevares aktiveret.*<br/>- **Overvågningstilstand**, hvor der ikke udføres nogen handling på elementer, der er registreret som PUA <br/>- **Deaktiveret**, som ikke registrerer eller udfører handlinger på elementer, der kan være PUA |
| **Skan**   |  |
| **Planlagt scanningstype** | Overvej at køre en ugentlig antivirusscanning på dine enheder. Du kan vælge mellem følgende indstillinger for scanningstype: <br/>- **Quickscan** kontrollerer placeringer, f.eks. registreringsdatabasenøgler og startmapper, hvor malware kan registreres til at starte med en enhed. *Vi anbefaler, at du bruger quickscan-indstillingen.* <br/>- **Fullscan** kontrollerer alle filer og mapper på en enhed <br/>- **Deaktiveret** betyder, at der ikke foretages nogen planlagte scanninger. Brugerne kan stadig køre scanninger på deres egne enheder. (Generelt anbefaler vi ikke, at du deaktiverer planlagte scanninger). <br/><br/> [Få mere at vide om scanningstyper](../defender-endpoint/schedule-antivirus-scans.md). |
| **Dag i ugen for at køre en planlagt scanning** | Vælg en dag, som dine normale, ugentlige antivirusscanninger skal køre. |
| **Tidspunkt på dagen til kørsel af en planlagt scanning** | Vælg et tidspunkt, hvor du vil køre de regelmæssigt planlagte antivirusscanninger, der skal køres. |
| **Brug lav ydeevne** | Denne indstilling er som standard slået fra. *Vi anbefaler, at du holder denne indstilling slået fra.* Du kan dog slå denne indstilling til for at begrænse enhedens hukommelse og de ressourcer, der bruges under planlagte scanninger. <br/><br/>**VIGTIGT** Hvis du slår **Brug lav ydeevne** til, konfigureres følgende indstillinger for Microsoft Defender Antivirus: <br/>- Arkivfiler scannes ikke ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>– Scanninger tildeles en lav CPU-prioritet ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Hvis en fuld antivirusscanning går tabt, køres der ingen indfangningsscanning ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Hvis en hurtig antivirusscanning går tabt, køres der ingen indfangningsscanning ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>– Reducerer den gennemsnitlige CPU-belastningsfaktor under en antivirusscanning fra 50 % til 20 % ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Brugeroplevelse**   |  |
| **Tillad brugere at få adgang til appen Windows Sikkerhed** | Slå denne indstilling til for at give brugerne mulighed for at åbne appen Windows Sikkerhed på deres enheder. Brugerne kan ikke tilsidesætte indstillinger, som du konfigurerer i Microsoft Defender til virksomheder, men de kan om nødvendigt køre en hurtig scanning eller få vist registrerede trusler. |
| **Antivirusudeladelser** | Udeladelser er processer, filer eller mapper, der springes over af Microsoft Defender Antivirus scanninger. *Generelt skal du ikke definere undtagelser.* Microsoft Defender Antivirus omfatter mange automatiske undtagelser, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler.<br/><br/>[Få mere at vide om undtagelser](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Behandl udeladelser** | Procesudeladelser forhindrer filer, der åbnes af bestemte processer, i at blive scannet af Microsoft Defender Antivirus. <br/><br/>[Få mere at vide om procesudeladelser](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Undtagelser for filtypenavne** | Udeladelser af filtypenavne forhindrer, at filer med bestemte filtypenavne scannes af Microsoft Defender Antivirus.<br/><br/>[Få mere at vide om undtagelser for filtypenavne](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Fil- og mappeudeladelser** | Fil- og mappeudeladelser forhindrer, at filer i bestemte mapper scannes af Microsoft Defender Antivirus. <br/><br/>[Få mere at vide om fil- og mappeudeladelser](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Andre forudkonfigurerede indstillinger i Defender for Business

Følgende sikkerhedsindstillinger forudkonfigureres i Defender for Business:

- Scanning af flytbare drev er slået til ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))

- Daglige hurtige scanninger har ikke et forudindstillet tidspunkt ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))

- Sikkerhedsintelligensopdateringer kontrolleres, før en antivirusscanning kører ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))

- Sikkerhedsintelligenskontroller finder sted hver fjerde time ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>Standardindstillinger og Microsoft Endpoint Manager for Defender for Business

I følgende tabel beskrives indstillinger, der er forudkonfigureret til Defender for Business, og hvordan disse indstillinger svarer til det, du kan se i Microsoft Endpoint Manager (eller Microsoft Intune). Hvis du bruger den [forenklede konfigurationsproces i Defender for Business](mdb-simplified-configuration.md) (prøveversion), behøver du ikke at redigere disse indstillinger.
<br/><br/>

| Indstilling  | Beskrivelse  |
|---------|---------|
| [Skybeskyttelse](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Cloudbeskyttelse kaldes nogle gange cloudbaseret beskyttelse eller Microsoft Maps (Advanced Protection Service), cloudbeskyttelse fungerer sammen med Microsoft Defender Antivirus og Microsoft-cloudmiljøet til at identificere nye trusler, nogle gange endda før en enkelt enhed påvirkes. [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) er som standard slået til. <br/><br/>[Få mere at vide om cloudbeskyttelse](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Overvågning af indgående og udgående filer](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) er indstillet til at overvåge alle filer for at overvåge indgående og udgående filer.         |
| [Scan netværksfiler](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) er som standard ikke aktiveret, og netværksfiler scannes ikke. |
| [Scan mails](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) er som standard ikke aktiveret, og mails scannes ikke. |
| [Antal dage (0-90) til at holde malware i karantæne](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Indstillingen [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) er som standard angivet til nul (0) dage. Artefakter, der er i karantæne, fjernes ikke automatisk.  |
| [Indsend eksempelsamtykke](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) er som standard et for automatisk at sende sikre eksempler. Eksempler på sikre eksempler omfatter `.bat`, `.scr`, `.dll`og `.exe` filer, der ikke indeholder personidentificerbare oplysninger. Hvis en fil indeholder pii, modtager brugeren en anmodning om, at eksempelafsendelsen kan fortsætte.<br/><br/>[Få mere at vide om cloudbeskyttelse og indsendelse af eksempler](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Scan flytbare drev](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) er som standard konfigureret til at scanne flytbare drev, f.eks. USB-tommelfingerdrev på enheder.<br/><br/>[Få mere at vide om politikindstillinger for antimalware](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Kør daglig hurtigsøgningstid](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) er som standard angivet til 02:00.<br/><br/>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Søg efter signaturopdateringer, før du kører scanningen](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) er som standard konfigureret til at søge efter sikkerhedsintelligensopdateringer, før der køres antivirus-/antimalwarescanninger.<br/><br/>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) og [sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Hvor ofte (0-24 timer) der skal søges efter sikkerhedsopdateringer](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) er som standard konfigureret til at søge efter sikkerhedsintelligensopdateringer hver fjerde time.<br/><br/>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) og [sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)

- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Se også

- [Besøg Microsoft 365 Defender-portalen](mdb-get-started.md)

- [Administrer firewallindstillinger i Microsoft Defender til virksomheder](mdb-custom-rules-firewall.md)

- [Politik-CSP – Defender](/windows/client-management/mdm/policy-csp-defender)