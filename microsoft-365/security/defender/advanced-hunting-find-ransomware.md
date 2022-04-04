---
title: Find ransomware med avanceret jagt
description: Brug avanceret jagt til at finde enheder, der kan blive påvirket af ransomware.
keywords: avanceret jagt, ransomware, trusselssøgning, cybertrusler på jagt, søgning, forespørgsel, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-ransomware
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e90661932880ee146b8b1b81f8412e97d674749d
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755750"
---
# <a name="hunt-for-ransomware"></a>Lede efter ransomware

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Ransomware har udviklet sig hurtigt fra at være simpel malware fra varer, der påvirker individuelle computerbrugere, til en trussel mod virksomheder, der i alvorlig grad påvirker brancher og offentlige institutioner. Selvom [Microsoft 365 Defender indeholder](microsoft-365-defender.md) mange funktioner, der registrerer og blokerer ransomware og tilhørende indtrængen, kan proaktive kontroller for tegn på kompromis hjælpe dig med at holde dit netværk beskyttet.

> [Læs om human-drevet ransomware](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

Når [du har avanceret](advanced-hunting-overview.md) Microsoft 365 Defender, kan du oprette forespørgsler, der finder individuelle artefakter, der er knyttet til ransomware-aktivitet. Du kan også køre mere avancerede forespørgsler, der kan søge efter tegn på aktivitet og afveje disse tegn for at finde enheder, der kræver øjeblikkelig handling.

## <a name="signs-of-ransomware-activity"></a>Tegn på ransomware-aktivitet
Microsoft-sikkerhedseksperter har observeret forskellige almindelige, men diskrete artefakter i mange ransomware-kampagner, der er lanceret af avancerede indtrængere. Disse tegn involverer hovedsageligt brug af systemværktøjer til at forberede kryptering, forhindre registrering og klar analyse beviser.

| Ransomware-aktivitet | Almindelige værktøjer | Formål |
|--|--|--|
| Stop processer | _taskkill.exe_, _net stop_ | Sørg for, at filer, der er målrettet kryptering, ikke er låst af forskellige programmer. |
| Slå tjenester fra | _sc.exe_ | - Sørg for, at filer, der er målrettet kryptering, ikke er låst af forskellige programmer.<br>- Undgå, at sikkerhedssoftware forstyrrer kryptering og anden ransomware-aktivitet.<br>- Stop sikkerhedskopieringssoftware i at oprette genoprettelige kopier.  |
| Slet logfiler og filer | _cipher.exe_, _wevtutil_, _fsutil.exe_ | Fjern beviser, der kan dokumenteres. |
| Slet skyggekopier  | _vsadmin.exe_, _wmic.exe_ | Fjern kopier af drevskygge, der kan bruges til at gendanne krypterede filer. |
| Slette og stoppe sikkerhedskopier | _wbadmin.exe_ | Slet eksisterende sikkerhedskopier, og stop planlagte sikkerhedskopieringsopgaver, hvilket forhindrer gendannelse efter kryptering. |
| Rediger startindstillinger | _bcdedit.exe_ | Slå advarsler og automatiske reparationer fra efter startfejl, der kan skyldes krypteringsprocessen. |
| Slå gendannelsesværktøjer fra | _schtasks.exe__regedit.exe_. | De slå Systemgendannelse og andre indstillinger for systemgendannelse fra. |

## <a name="check-for-individual-signs-of-ransomware-activity"></a>Kontrollér for individuelle tegn på ransomware-aktivitet
Mange aktiviteter, der udgør ransomware-adfærd, herunder de aktiviteter, der er beskrevet i den foregående sektion, kan være tilsnit. Når du bruger følgende forespørgsler til at finde ransomware, skal du køre mere end én forespørgsel for at kontrollere, om de samme enheder udviser forskellige tegn på mulig ransomware-aktivitet.

### <a name="stopping-multiple-processes-using-_taskkillexe_"></a>Stoppe flere processer med _taskkill.exe_
Denne forespørgsel kontrollerer, om der er forsøg på at stoppe mindst 10 separate processer ved _hjælptaskkill.exe_ værktøj. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RS2vCUBCFz7rgfwiuIkit3eumVSgtpYvuS9SLDTY2eLUvxN_eb8YHKlFkyNzJzDkn505aailRX7mmGlFlmhNBhUrOSGeuT3L0s6QqNaMagolEcMyCbApjx2e8TYhcH8Q1mB-emq50z_lF39gvBzo9-gEF-6Yhlyh9653ejCfRK6zCsaZfuJOu-x2jkqqN-0Yls-8-gp6dZ52OVuT6Sad1plulyN0KIkMt15_zt7zHDe8OBwv3btoJToa7Tnp0T8Ou9WzfT761gPOm3_FQ16Zxp2qcCdg33_rlyokG-iXv7_4BRNMnhkortmvTW6rqnZ7bgP2Vtm70D3d9wcFaAgAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using taskkill.exe
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10
```
  
### <a name="stopping-processes-using-_net-stop_"></a>Stoppe processer ved hjælp _af netstop_
Denne forespørgsel kontrollerer, om der er forsøg på at stoppe mindst 10 separate processer ved hjælp af _kommandoen net stop_ . [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RQUvDUBCE5yz0P4ScUijWereXVkGQIti7aA1pqakhL7VVxN_ebzc1NBChPLJv2Z2ZN5sdaqhId1ppozeyF1WcVLkK7kCl0gcx-F2QFSrJFmACJ3XMlmgKGfmGWnXC6OlCU2qfIIz12OLfUk_h2FuG_IG505JayRdpDit3bIW33B2M3WeGSqIRrvudTJvpnWzmPKvc6JcYHx1eEvd8savV07e9TchzTt198AlNZ0kluNLfjHHjIPAvak4J_tvx9XtPR6ypbn1icxShvGgqyVkO-hrAm7VUrRcaTWOs6T_7hs7XjfSqL-Lpvu5BDLxjqKRjI9a9Juvew__T2x5HutIB3T1qt4QCAAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using net stop
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10
```
### <a name="deletion-of-data-on-multiple-drives-using-_cipherexe_"></a>Sletning af data på flere drev ved _hjælp afcipher.exe_
Denne forespørgsel kontrollerer, om der er forsøg på at slette data på flere drev _ved hjælpcipher.exe_. Denne aktivitet udføres typisk af ransomware for at forhindre gendannelse af data efter kryptering. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI1SXUvDQBCcZ8H_cOQpgWLoD7AvVUEo4oPvElO1pblUcmn9QPztzk6TEuEsIdzdZndndm73cuRwWGDLb0PrhWfDs8Qab1jhmX8X3D-4HJbcK66W0Rqv8hT8K4RsiPW0PHbMasVQdbiGf3vaAec4wxWtPT0lz3vhSsUCrpVVE33I_Cb6vdNhTA9EeeVaVc8KDjOugmq2SDFlrSyKvCHS1NwJZ55L_HBPondNGDGWXP2JdyMnv927UnXHWwf6l4MunupXTOPfXszVT8_smriFOCxrRU-QclOQDLgCNRwQ1u8vZc8H2o1xp-7a7U1NefSko6pnmKjakNVi4chpiA39j-rGeF6HJ3xyH76NW2ZMFLGsNDJ9i05pZSPmVdDfq-jncfqtOuU5zSuQz6Zq92w7Hfbm-9cUm-d_vZ9J9S81O2KIfAMAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for cipher.exe deleting data from multiple drives
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine),
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1
```

### <a name="clearing-of-forensic-evidence-from-event-logs-using-_wevtutil_"></a>Rydning af nyttige beviser fra hændelseslogfiler ved hjælp _af wevtutil_
Denne forespørgsel kontrollerer, om der er forsøg på at rydde mindst 10 logposter fra hændelseslogfiler ved hjælp _af wevtutil_. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWRTU_CQBCG37OJ_2HDqSQkwMGjXgoHEg4cUI-m2hUaqGu6BaPxx_vsEFCTxmA225nOvB_tzFBDOc0VOBuyZ2JD3CnKEwMVpzfyPbVWlba8t9Sdnsi9CsPXdLfWf7Wq4xm0QuVSF5oYv4LhtQAfLIucKXWvF5gH5Ke5rak1prKEVRu2xalG3emGW6AdlGmsUv1O5m-fnLzmFHiV_G9FTKg1lUjs6Z5vucPvljsD0TOXhP6_Vm7841dFZnPAN2A_DDu36eSnCSbNnc3B6Zpb4nasZGf59zWA963orZdcEiKelBNvQ_fBNny-utOj3nn-3OUMxMA6CZV1bCt1r8i6d_TXFNKWxxrpC48hm8miAgAA&runQuery=true&timeRangeId=week)

```kusto
// Look for use of wevtutil to clear multiple logs
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10
```

### <a name="turning-off-services-using-_scexe_"></a>De slår tjenester fra ved _hjælpsc.exe_
Denne forespørgsel kontrollerer, om der er forsøg på at deaktivere mindst 10 eksisterende tjenester, der _brugersc.exe_. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAKWST2vCQBDF31nodwg5RZCqhx7bi3ooeCjovaQxraIxxfU_fvj-ZoiiEIqlhM3Ozrz3ZnZm22or0lAl3xzrk33FHpTpUbn2rEgTzfCk-tACa6kvR-Qgt5wzrKAHNdTHOnveiJZVLGiAP4e5rpAnFHaauoZlGMMqHLsmT6FvfC-slFylEnWpoVnLvM3Twy74UnJNuJdVa6gpnsAe-81iVzbE3_kZiCV9mlHZf3Sue5pzii-3C9pU3BWYo_NGKPdvGJZh4x2N9Owzyi6e5K5qmmrVKg_9dNY11hzvu0_8fu0ItQP_6zfxCqLlEUMlNVO36BNW_ax_74K9l646-gFts39I1AIAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for sc.exe disabling services
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10
```

### <a name="turning-off-system-restore"></a>De slår Systemgendannelse fra
Denne forespørgsel identificerer forsøg på at stoppe Systemgendannelse og forhindre systemet i at oprette gendannelsespunkter, som kan bruges til at gendanne data, der er krypteret med ransomware. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAK2S3UrDQBCFz7XgO6y9id4o6HWvrIVCkaJPENOYFNumZGO1ID673w4xJA1isbJMZnZ-zpzM7EiptlooQc9UqjDLc-7wp1qrwj7Via44MzK35FTotTI5PXMr0aVe8cy15NzoGo-zqg_0m3KQSsRpQtbC6uMGpdt3jHeJfU_GymqG-uQb9XpcEn1HIuvmGpZT0Aq99Dim4G3ousNO8K04sSE6EEN22kL6jvzO-LaDNW2QzqxLmGBsPo9vUMt_oA8Na3DQv3vwcmPiifpmds48jkhut8T2FLikxm_T4bI_m_6uQt-wrXO28lPPSBcdziOqPFlP9RYy47tDKtuZM07hVtSvaJ_HYRPL63-NyMgtmtWv5684jy2WDx2O0ZEM562ZBLQvURxur6gDAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
//Pivoting for rundll32  
| where InitiatingProcessFileName =~ 'rundll32.exe'   
//Looking for empty command line   
and InitiatingProcessCommandLine !contains " " and InitiatingProcessCommandLine != ""  
//Looking for schtasks.exe as the created process  
and FileName in~ ('schtasks.exe')  
//Disabling system restore   
and ProcessCommandLine has 'Change' and ProcessCommandLine has 'SystemRestore' 
and ProcessCommandLine has 'disable'
```

### <a name="backup-deletion"></a>Sletning af sikkerhedskopi
Denne forespørgsel identificerer brugen af datawmic.exe _at_ slette øjebliksbilleder af øjebliksbilleder af øjebliksbilleder før kryptering. [Kør forespørgsel](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWS2wqCQBCG_-ugd5CupTfoqgMIEV70AqFLGp5QyYLo2fsavEjxwlhWZ7-df2Z2dndyuitVxD9UrdKshrGHOxVqsZda6CVPnRJYzfR0QJVhnXRRbmSjN98VXrlFXEMfzNWkfphti50zLmSMdURfmFcCaSxqY3aMX4eqVKUn1OsV_8eLWX_rbwcVVhblBovY8bT76U-AxoedWeeWp7WzV0YDMqSQFNZavuuopnHH_Iku-lbJnLPMyxnYDTp4bZ5P9M5uNpsZIWSn7l_CuNoPSggb4z4CAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
| where FileName =~ "wmic.exe"
| where ProcessCommandLine has "shadowcopy" and ProcessCommandLine has "delete"
| project DeviceId, Timestamp, InitiatingProcessFileName, FileName,
ProcessCommandLine, InitiatingProcessIntegrityLevel, InitiatingProcessParentFileName
```

## <a name="check-for-multiple-signs-of-ransomware-activity"></a>Kontrollér, om der er flere tegn på ransomware-aktivitet
I stedet for at køre flere forespørgsler separat, kan du også bruge en omfattende forespørgsel, der kontrollerer, om der er flere tegn på ransomware-aktivitet for at identificere påvirkede enheder. Følgende konsoliderede forespørgsel:
- Søger efter både relativt konkret og diskrete tegn på ransomware-aktivitet
- Afvejer tilstedeværelsen af disse tegn
- Identificerer enheder med en højere risiko for at blive mål for ransomware 

Når den køres, returnerer denne konsoliderede forespørgsel en liste over enheder, der har udviser flere tegn på angreb. Antallet af hver type ransomware-aktivitet vises også. For at køre denne konsoliderede forespørgsel skal du kopiere den direkte til den avancerede [forespørgselseditor](https://security.microsoft.com/advanced-hunting). 

```kusto
// Find attempts to stop processes using taskkill.exe
let taskKill = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10;
// Find attempts to stop processes using net stop
let netStop = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10;
// Look for cipher.exe deleting data from multiple drives
let cipher = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine), 
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1;
// Look for use of wevtutil to clear multiple logs
let wevtutilClear = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10;
// Look for sc.exe disabling services
let scDisable = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10;
// Main query for counting and aggregating evidence
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "vssadmin.exe" and ProcessCommandLine has_any("list shadows", "delete shadows")
or FileName =~ "fsutil.exe" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal"
or ProcessCommandLine has("bcdedit") and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures")
or ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup")
or (ProcessCommandLine has "wevtutil" and ProcessCommandLine has "cl") 
or (ProcessCommandLine has "wmic" and ProcessCommandLine has "shadowcopy delete")
or (ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled")
| extend Bcdedit = iff(ProcessCommandLine has "bcdedit" and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures"), 1, 0)
| extend ShadowCopyDelete = iff (ProcessCommandLine has "shadowcopy delete", 1, 0)
| extend VssAdminShadows = iff(ProcessCommandLine has "vssadmin" and ProcessCommandLine has_any("list shadows", "delete shadows"), 1, 0)
| extend Wbadmin = iff(ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup"), 1,0)
| extend Fsutil = iff(ProcessCommandLine has "fsutil" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal", 1, 0)
| summarize FirstActivity = min(Timestamp), ReportId = any(ReportId), Commands = make_set(ProcessCommandLine) by DeviceId, Fsutil, Wbadmin, ShadowCopyDelete, Bcdedit, VssAdminShadows, bin(Timestamp, 6h)
// Joining extra evidence
| join kind=leftouter (wevtutilClear) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (cipher) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (netStop) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (taskKill) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (scDisable) on $left.DeviceId == $right.DeviceId
| extend WevtutilUse = iff(LogClearCount > 10, 1, 0)
| extend CipherUse = iff(CipherCount > 1, 1, 0)
| extend NetStopUse = iff(netStopCount > 10, 1, 0)
| extend TaskkillUse = iff(taskKillCount > 10, 1, 0)
| extend ScDisableUse = iff(ScDisableCount > 10, 1, 0)
// Adding up all evidence
| mv-expand CommandList = NetStopList, TaskKillList, ClearedLogList, CipherList, Commands, ScDisableList
// Format results
| summarize BcdEdit = iff(make_set(Bcdedit) contains "1" , 1, 0), NetStop10PlusCommands = iff(make_set(NetStopUse) contains "1", 1, 0), Wevtutil10PlusLogsCleared = iff(make_set(WevtutilUse) contains "1", 1, 0),
CipherMultipleDrives = iff(make_set(CipherUse) contains "1", 1, 0), Fsutil = iff(make_set(Fsutil) contains "1", 1, 0), ShadowCopyDelete = iff(make_set(ShadowCopyDelete) contains "1", 1, 0),
Wbadmin = iff(make_set(Wbadmin) contains "1", 1, 0), TaskKill10PlusCommand = iff(make_set(TaskkillUse) contains "1", 1, 0), VssAdminShadow = iff(make_set(VssAdminShadows) contains "1", 1, 0), 
ScDisable = iff(make_set(ScDisableUse) contains "1", 1, 0), TotalEvidenceCount = count(CommandList), EvidenceList = make_set(Commands), StartofBehavior = min(FirstActivity) by DeviceId, bin(Timestamp, 1d)
| extend UniqueEvidenceCount = BcdEdit + NetStop10PlusCommands + Wevtutil10PlusLogsCleared + CipherMultipleDrives + Wbadmin + Fsutil + TaskKill10PlusCommand + VssAdminShadow + ScDisable + ShadowCopyDelete
| where UniqueEvidenceCount > 2
```
### <a name="understand-and-tweak-the-query-results"></a>Forstå og justere forespørgselsresultaterne
Den konsoliderede forespørgsel returnerer følgende resultater:

- **DeviceId** – identificerer den påvirkede enhed 
- **TimeStamp** – første gang nogen tegn på ransomware-aktivitet blev observeret på enheden
- **Specifikke tegn på aktivitet –** antallet for hvert tegn, der vises i flere kolonner, f.eks _. BCDEdit_ eller _FsUtil_
- **TotalEvidenceCount** – antal observerede tegn
- **UniqueEvidenceCount** – antal typer af observerede tegn

:::image type="content" source="../../media/advanced-hunting-ransomware-query.png" alt-text="Et eksempel på en konsolideret forespørgsel om ransomware-aktivitet i Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-ransomware-query.png":::

*Forespørgselsresultater, der viser påvirkede enheder og optællinger af forskellige tegn på ransomware-aktivitet*

Som standard viser forespørgselsresultatet kun enheder, der har mere end to typer ransomware-aktivitet. Hvis du vil have vist alle enheder med tegn på ransomware-aktivitet, `where` skal du ændre følgende operator og angive tallet til nul (0). Hvis du vil se færre enheder, skal du angive et højere tal. 

```kusto
| where UniqueEvidenceCount > 2
```

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)

## <a name="more-ransomware-resources"></a>Flere ransomware-ressourcer

Vigtige oplysninger fra Microsoft:

- [Den voksende trussel om ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human ransomware](/security/compass/human-operated-ransomware)
- [Beskyt hurtigt mod ransomware og afpressning](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (se side 10-19)
- [Ransomware: En pervasiv og løbende rapport over](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) trusler mod trusler i Microsoft 365 Defender-portalen

Microsoft 365:

- [Installér ransomware-beskyttelse for din Microsoft 365 lejer](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maksimere ransomware-fleksibilitet med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Gendan efter en ransomware-angreb](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Beskyttelse mod malware og ransomware](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Beskyt din Windows-pc mod ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Håndtering af ransomware i SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Rapporter om trusselsanalyse for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) i Microsoft 365 Defender-portalen

Microsoft Azure:

- [Azure-forsvar til ransomware-angreb](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maksimere ransomware-fleksibilitet med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan for sikkerhedskopiering og gendannelse for at beskytte dig mod ransomware](/security/compass/backup-plan-to-protect-against-ransomware)
- [Hjælp med at beskytte mod ransomware Microsoft Azure sikkerhedskopiering](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutters video)
- [Genoprettelse af identitet efter identitet, der er identiteter, er blevet genoprettet](/azure/security/fundamentals/recover-from-identity-compromise)
- [Avanceret registrering af multistage-angreb i Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Registrering af fusion til ransomware i Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender til skyapps:

-  [Opret anomaliregistreringspolitikker i Defender til skyapps](/cloud-app-security/anomaly-detection-policy)

Blogindlæg for Microsoft-sikkerhedsteamet:

- [Tre trin til at forebygge og genoprette fra ransomware (september 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [En vejledning i at bekæmpe human ransomware: Del 1 (september 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Vigtige trin til, hvordan Microsofts registrerings- og svarteam (AFS) udfører undersøgelser af ransomware-hændelser.

- [En vejledning til at bekæmpe human ransomware: Del 2 (september 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Anbefalinger og bedste fremgangsmåder.

- [Bliv robust ved at forstå risici i cybersikkerhed: Del 4 – navigering i aktuelle trusler (maj 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Se **afsnittet ransomware** .

- [Ransomware-angreb drevet af mennesker: En undgåelig nedbrud (marts 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Omfatter angrebskædeanalyser af faktiske angreb.

- [Ransomware-svar – for at betale eller ej at betale? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Bing reagerer på ransomware-angreb med gennemsigtighed (december 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
