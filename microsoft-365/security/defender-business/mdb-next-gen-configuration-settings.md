---
title: Om konfigurationsindstillinger for næste generation af beskyttelse i Microsoft Defender til virksomheder
description: Forstå beskyttelsesindstillinger for antivirus og næste generation i Defender for Business, slutpunktsikkerhed for små og mellemstore virksomheder.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 69eea26df1f96b72ef66e53e46d679f40f0294b7
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772471"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Om næste generations konfigurationsindstillinger i Microsoft Defender til virksomheder

Næste generations beskyttelse i Defender for Business omfatter robust beskyttelse mod antivirus og antimalware. Standardpolitikkerne er designet til at beskytte dine enheder og brugere uden at hindre produktiviteten. Du kan også tilpasse politikkerne, så de passer til dine forretningsbehov. Og hvis du bruger Microsoft Intune, kan du bruge Microsoft Endpoint Manager Administration til at administrere dine sikkerhedspolitikker.

**I denne artikel beskrives**:

- [Næste generations beskyttelsesindstillinger](#next-generation-protection-settings-and-options)
- [Andre forudkonfigurerede indstillinger i Defender for Business](#other-preconfigured-settings-in-defender-for-business) 
- [Standardindstillinger og Microsoft Intune for Defender for Business](#defender-for-business-default-settings-and-microsoft-intune)

## <a name="next-generation-protection-settings-and-options"></a>Næste generations beskyttelsesindstillinger

I følgende tabel vises indstillinger og indstillinger.

| Indstilling | Beskrivelse |
|:---|:---|
| **Beskyttelse i realtid**  |  |
| **Slå beskyttelse i realtid til** | Aktiveret som standard finder og stopper beskyttelse i realtid malware fra at køre på enheder. *Vi anbefaler, at beskyttelse i realtid er slået til.*<p>Når beskyttelse i realtid er slået til, konfigurerer den følgende indstillinger:<ul><li>Overvågning af funktionsmåde er slået til ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)).</li><li>Alle downloadede filer og vedhæftede filer scannes ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)).</li><li>Scripts, der bruges i Microsoft-browsere, scannes ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)).</li></ul>   |
| **Blok ved første øjekast** | Aktiveret som standard blokerer ved første øjekast malware inden for sekunder efter registrering, øger den tid (i sekunder), der tillades til at indsende eksempelfiler til analyse, og indstiller dit registreringsniveau til Høj. *Vi anbefaler, at blok ved første øjekast er slået til.*<p>Når blok ved første øjekast er slået til, konfigurerer den følgende indstillinger for Microsoft Defender Antivirus:<ul><li>Blokering og scanning af mistænkelige filer er indstillet til niveauet Høj blokering ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)).</li><li>Det antal sekunder, en fil skal blokeres og kontrolleres, er indstillet til 50 sekunder ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)).</li></ul> <p>**Vigtigt** Hvis blok ved første øjekast er slået fra, påvirker `CloudBlockLevel` det og `CloudExtendedTimeout` for Microsoft Defender Antivirus.  |
| **Slå netværksbeskyttelse til** | Når netværksbeskyttelse er slået til, hjælper den med at beskytte mod phishing,udnytte-hostingwebsteder og skadeligt indhold på internettet. Det forhindrer også brugerne i at slå netværksbeskyttelse fra.<p>Netværksbeskyttelse kan angives til følgende tilstande:<ul><li>**Bloktilstand** er standardindstillingen. Det forhindrer brugerne i at besøge websteder, der anses for usikre. *Vi anbefaler, at netværksbeskyttelse er indstillet til bloktilstand.*</li><li>**Overvågningstilstand** giver brugerne mulighed for at besøge websteder, der kan være usikre, og sporer netværksaktivitet til/fra sådanne websteder.</li><li>**Deaktiveret tilstand** blokerer hverken brugere fra at besøge websteder, der kan være usikre, eller sporer netværksaktivitet til/fra sådanne websteder.</li></ul> |
| **Oprydning**  |  |
| **Handling, der skal udføres på potentielt uønskede apps (PUA)** | PUA kan omfatte reklamesoftware; bundling software, der tilbyder at installere anden usigneret software; software, der forsøger at undgå sikkerhedsfunktioner. Selvom PUA ikke nødvendigvis er en virus, malware eller anden type trussel, kan det påvirke enhedens ydeevne.<p>PUA-beskyttelse blokerer elementer, der registreres som PUA. Du kan angive PUA-beskyttelse til følgende:<ul><li>**Aktiveret** er standardindstillingen. Det blokerer elementer, der registreres som PUA på enheder. *Vi anbefaler, at PUA-beskyttelse bevares aktiveret.*</li><li>**Overvågningstilstand** udfører ingen handling på elementer, der er registreret som PUA.</li><li>**Disabled** registrerer eller udfører ikke handlinger på elementer, der kan være PUA.</li></ul> |
| **Skan**   |  |
| **Planlagt scanningstype** | Overvej at køre en ugentlig antivirusscanning på dine enheder. Du kan vælge mellem følgende indstillinger for scanningstype:<ul><li>**Quickscan** kontrollerer placeringer, f.eks. registreringsdatabasenøgler og startmapper, hvor malware kan registreres til at starte sammen med en enhed. *Vi anbefaler, at du bruger quickscan-indstillingen.*</li><li>**Fullscan** kontrollerer alle filer og mapper på en enhed.</li><li>**Deaktiveret** betyder, at der ikke foretages nogen planlagte scanninger. Brugerne kan stadig køre scanninger på deres egne enheder. (Generelt anbefaler vi ikke, at planlagte scanninger deaktiveres).</li></ul><p> [Få mere at vide om scanningstyper](../defender-endpoint/schedule-antivirus-scans.md). |
| **Dag i ugen for at køre en planlagt scanning** | Vælg en dag, som dine normale, ugentlige antivirusscanninger skal køre. |
| **Tidspunkt på dagen til kørsel af en planlagt scanning** | Vælg et tidspunkt, hvor du vil køre de regelmæssigt planlagte antivirusscanninger, der skal køres. |
| **Brug lav ydeevne** | Denne indstilling er som standard slået fra. *Vi anbefaler, at du holder denne indstilling slået fra.* Du kan dog aktivere denne indstilling for at begrænse enhedens hukommelse og de ressourcer, der bruges under planlagte scanninger. <p>**Vigtigt** Hvis du slår **Brug lav ydeevne** til, konfigureres følgende indstillinger for Microsoft Defender Antivirus:<ul><li>Arkivfiler scannes ikke ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)).</li><li>Scanninger tildeles en lav CPU-prioritet ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)).</li><li>Hvis en komplet antivirusscanning går tabt, køres der ingen indfangningsscanning ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)).</li><li>Hvis en hurtig antivirusscanning overses, køres der ingen indfangningsscanning ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)).</li><li>Reducerer den gennemsnitlige CPU-belastningsfaktor under en antivirusscanning fra 50 % til 20 % ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)).</li></ul> |
| **Brugeroplevelse**   |  |
| **Tillad brugere at få adgang til appen Windows Sikkerhed** | Slå denne indstilling til for at give brugerne mulighed for at åbne appen Windows Sikkerhed på deres enheder. Brugerne kan ikke tilsidesætte indstillinger, som du konfigurerer i Defender for Business, men de kan køre en hurtig scanning eller få vist registrerede trusler. |
| **Antivirusudeladelser** | Udeladelser er processer, filer eller mapper, der springes over af Microsoft Defender Antivirus-scanninger. *Generelt skal du ikke definere undtagelser.* Microsoft Defender Antivirus indeholder mange automatiske undtagelser, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler.<p>[Få mere at vide om undtagelser](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md). |
| **Behandl udeladelser** | Procesudeladelser forhindrer, at filer, der åbnes af bestemte processer, scannes af Microsoft Defender Antivirus. <p>[Få mere at vide om procesudeladelser](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). |
| **Undtagelser for filtypenavne** | Udeladelser fra filtypenavne forhindrer, at filer med bestemte filtypenavne scannes af Microsoft Defender Antivirus.<p>[Få mere at vide om undtagelser for filtypenavne](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md). |
| **Fil- og mappeudeladelser** | Fil- og mappeudeladelser forhindrer filer i bestemte mapper i at blive scannet af Microsoft Defender Antivirus. <p>[Få mere at vide om fil- og mappeudeladelser](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md). |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Andre forudkonfigurerede indstillinger i Defender for Business

Følgende sikkerhedsindstillinger forudkonfigureres i Defender for Business:

- Scanning af flytbare drev er slået til ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)).
- Daglige hurtige scanninger har ikke et forudindstillet tidspunkt ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)).
- Sikkerhedsintelligensopdateringer kontrolleres, før en antivirusscanning kører ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan)).
- Sikkerhedsintelligenskontroller finder sted hver fjerde time ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)).

## <a name="defender-for-business-default-settings-and-microsoft-intune"></a>Standardindstillinger og Microsoft Intune for Defender for Business

I følgende tabel beskrives indstillinger, der er forudkonfigureret for Defender for Business, og hvordan disse indstillinger svarer til det, du kan se i Intune (administreres i Microsoft Endpoint Manager Administration). Hvis du bruger den [forenklede konfigurationsproces i Defender for Business](mdb-simplified-configuration.md), behøver du ikke at redigere disse indstillinger.

| Indstilling  | Beskrivelse  |
|---------|---------|
| [Skybeskyttelse](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Cloudbeskyttelse kaldes nogle gange cloudbaseret beskyttelse eller Microsoft Maps (Advanced Protection Service), cloudbeskyttelse fungerer sammen med Microsoft Defender Antivirus og Microsoft-cloudmiljøet til at identificere nye trusler, nogle gange endda før en enkelt enhed påvirkes. [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) er som standard slået til. <p>[Få mere at vide om cloudbeskyttelse](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Overvågning af indgående og udgående filer](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) er indstillet til at overvåge alle filer for at overvåge indgående og udgående filer.         |
| [Scan netværksfiler](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) er som standard ikke aktiveret, og netværksfiler scannes ikke. |
| [Scan mails](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) er som standard ikke aktiveret, og mails scannes ikke. |
| [Antal dage (0-90) til at holde malware i karantæne](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Indstillingen [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) er som standard angivet til nul (0) dage. Artefakter, der er i karantæne, fjernes ikke automatisk.  |
| [Indsend eksempelsamtykke](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) er som standard angivet til automatisk at sende sikre eksempler. Eksempler på sikre eksempler omfatter `.bat`, `.scr`, `.dll`og `.exe` filer, der ikke indeholder personidentificerbare oplysninger. Hvis en fil indeholder pii, modtager brugeren en anmodning om, at eksempelafsendelsen kan fortsætte.<p>[Få mere at vide om cloudbeskyttelse og indsendelse af eksempler](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md). |
| [Scan flytbare drev](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) er som standard konfigureret til at scanne flytbare drev, f.eks. USB-tommelfingerdrev på enheder.<p>[Få mere at vide om politikindstillinger for antimalware](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings).   |
| [Kør daglig hurtigsøgningstid](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) er som standard angivet til 02:00.<p>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Søg efter signaturopdateringer, før du kører scanningen](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) er som standard konfigureret til at søge efter sikkerhedsintelligensopdateringer, før der køres antivirus-/antimalwarescanninger.<p>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) og [sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Hvor ofte (0-24 timer) der skal søges efter sikkerhedsopdateringer](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) er som standard konfigureret til at søge efter sikkerhedsintelligensopdateringer hver fjerde time.<p>[Få mere at vide om scanningsindstillinger](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) og [sikkerhedsintelligensopdateringer](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Se også

- [Besøg Microsoft 365 Defender-portalen](mdb-get-started.md)
- [Administrer firewallindstillinger i Defender for Business](mdb-custom-rules-firewall.md)
- [Politik-CSP – Defender](/windows/client-management/mdm/policy-csp-defender)
