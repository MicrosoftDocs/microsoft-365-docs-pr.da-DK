---
title: Enhedskonfiguration
description: Få mere at vide om standardpolitikker for Microsoft-administrerede skrivebordsenheder.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 19acff97a1541dcf6151b531696cf373e604371f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587868"
---
# <a name="device-configuration"></a>Enhedskonfiguration

<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Når der konfigureres en ny Microsoft-administreret skrivebordsenhed, sikrer vi, at konfigurationen er optimeret til Microsoft Managed Desktop.

Konfigurationen indeholder et sæt standardpolitikker, der er angivet som en del af onboardingprocessen. Disse politikker leveres ved hjælp af administration af mobilenheder (MDM), når det er muligt. Du kan finde flere oplysninger [under Administration af mobilenheder](/windows/client-management/mdm/).

>[!NOTE]
>Du kan undgå konflikter ved ikke at ændre disse politikker.

Enheder ankommer med et signaturbillede og sluttes derefter til Azure Active Directory domæne, når den første bruger logger på. Enheden installerer automatisk påkrævede politikker og programmer uden nogen handling fra din it-medarbejder.

## <a name="default-policies"></a>Standardpolitikker

Denne tabel fremhæver standardpolitikker, der anvendes på alle Microsoft-administrerede stationære computere under klargøring af enheder. Alle registrerede ændringer i objekter, der ikke er godkendt af Microsoft Managed Desktop Operations Team og administreres af Microsoft Managed Desktop, gendannes.

| Politik | Beskrivelse
| ----- | ----- |
| Grundlinje for sikkerhed | [Microsofts sikkerhedsplan](/windows/device-security/windows-security-baselines) for administration af mobilenheder er konfigureret for alle Microsoft-administrerede stationære computere. Denne grundlinje er branchestandardkonfigurationen. Den er offentligt udgivet, gennemtestet og gennemgået af Microsofts sikkerhedseksperter for at holde Microsoft-administrerede stationære computere og apps sikre på den moderne arbejdsplads. <br><br>For at afhjælpe trusler i det konstant skiftende sikkerhedstrusler opdateres Microsoft-sikkerhedslinjen og installeres på Microsoft Managed Desktop-enheder med Windows 10 funktionsopdateringen.<br><br>Du kan finde flere oplysninger [Windows oprindelige planer for sikkerhed](/windows/security/threat-protection/windows-security-baselines).
| Anbefalet sikkerhedsskabelon til Microsoft-administreret skrivebord | Denne skabelon er et sæt anbefalede ændringer af den grundlinje for sikkerhed, der optimerer brugeroplevelsen. Disse ændringer er dokumenteret [i Sikkerheds-tilføjelsesprogrammet](#security-addendum). Opdateringer til tilføjelsesprogrammet for politikker udføres efter behov.  
| Opdateringsinstallation | Brug Windows til virksomheder til at udføre en gradvis udrulning af softwareopdateringer. It-administratorer kan ikke ændre indstillingerne for politikkerne for installationsgruppen. Du kan finde flere oplysninger om gruppebaseret installation under [Hvordan opdateringer håndteres i Microsoft Managed Desktop](updates.md).
| Forbrugsafsluttede forbindelser | Opdateringer over forbrugsaf forbrugsafslutninger (f.eks. LTE-netværk) er som standard slået fra. Dog kan hver enkelt bruger slå denne indstilling til enkeltvis ved at **navigere Indstillinger navigationsindstillinger og derefter Opdateringer og derefter til Avancerede indstillinger**. <br><br>Hvis du vil tillade, at alle brugere aktiverer opdateringer over forbrugsaf forbrugserede [forbindelser, skal](../working-with-managed-desktop/admin-support.md) du sende en anmodning om ændring, som vil aktivere denne indstilling for alle enheder.
| Enhedsoverholdelse | Disse politikker er konfigureret for alle Microsoft-administrerede skrivebordsenheder. En enhed rapporteres som ikke-kompatibel, når den er drevet fra vores påkrævede sikkerhedskonfiguration.

## <a name="windows-diagnostic-data"></a>Windows diagnostiske data

 Enheder indstilles til at levere forbedrede diagnostiske data til Microsoft under et kendt kommercielt id. Som en del af Microsofts administrerede skrivebord kan it-administratorer ikke ændre disse indstillinger.

For kunder i GDPR-områder (General Data Protection Regulation) kan brugerne reducere niveauet af diagnostiske data, der leveres, men der vil være en reduktion af tjenesten. Microsoft-administreret skrivebord kan f.eks. ikke indsamle de data, der er nødvendige for at iterere om indstillinger og politikker, så det passer bedst til ydeevnen og sikkerhedsbehovet. Få mere at vide under [Konfigurer Windows diagnostiske data i organisationen.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="security-addendum"></a>Sikkerheds addendum

 I dette afsnit beskrives de politikker, der installeres ud over de standardpolitikker for Microsoft-administreret skrivebord, der er angivet i [Standardpolitikker](#default-policies). Denne konfiguration er designet med henblik på finansielle tjenester og meget regulerede brancher og er optimeret til det højeste sikkerhedsniveau, samtidig med at brugernes produktivitet bevares.

### <a name="additional-security-policies"></a>Yderligere sikkerhedspolitikker

 Disse politikker tilføjes for at øge sikkerheden for meget regulerede brancher:

| Politik | Beskrivelse |
| ----- | ----- |
|Sikkerhedsovervågning | Microsoft overvåger enheder, der [bruger Microsoft Defender til slutpunkt](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Hvis der registreres en trussel, underretter Microsoft kunden, isolerer enheden og retter problemet eksternt. |
 | Deaktiver PowerShell V2 | Microsoft fjernede PowerShell V2 i august 2017.<br><br>Denne funktion er deaktiveret på alle Microsoft-administrerede skrivebordsenheder. Du kan finde flere oplysninger om denne ændring [i Windows PowerShell 2.0 Udrådning](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/). |
