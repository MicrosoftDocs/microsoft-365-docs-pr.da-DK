---
title: Rediger eller opret indstillinger for enhedsbeskyttelse til Windows 10 pc'er
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: Få mere at vide om de indstillinger, der er Microsoft 365 til virksomheder, for at Windows 10 enheder.
ms.openlocfilehash: 26a9921d1c950990adcb4a28516ce2207fb3bcd1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63600952"
---
# <a name="edit-or-create-device-protection-settings-for-windows-10-pcs"></a>Rediger eller opret indstillinger for enhedsbeskyttelse til Windows 10 pc'er

Denne artikel gælder for Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

Når du har konfigureret standardindstillingerne Windows-beskyttelse på siden Konfiguration, kan du tilføje nye, der gælder for enten alle brugere eller en række brugere. Du kan også redigere dem, du har oprettet.

## <a name="watch-create-protection-settings-for-windows-10-devices"></a>Se: Opret beskyttelsesindstillinger for Windows 10 enheder

Se en video om, hvordan du sikrer Windows 10 enheder med Microsoft 365 Business Premium:
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. I venstre navigationslinje skal du vælge **Tilføjelse af** \> **enheder-politikker**\>.
3. Angiv et **entydigt** navn for denne politik i ruden Tilføj politik. 
4. Under **Politiktype skal** du vælge **Windows 10 Enhedskonfiguration**.
5. **Udvid Secure Windows 10-enheder** \> konfigurer indstillingerne efter dine ønsker. Du kan finde flere oplysninger [under Tilgængelige indstillinger](#available-settings). 
    
    Du kan altid bruge linket **Nulstil standardindstillingerne** for at vende tilbage til standardindstillingen. 
    
    ![Tilføj politikrude med Windows 10 Enhedskonfiguration markeret.](../../media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. Beslut **derefter Who får disse indstillinger?** Hvis du ikke vil bruge standardsikkerhedsgruppen Alle  brugere, skal du vælge **Skift og søge** efter den sikkerhedsgruppe, der får disse indstillinger \> **Vælg**.
7. Til sidst skal **du** vælge Udført for at gemme politikken og tildele den til enheder. 

## <a name="edit-windows-10-protection-settings"></a>Rediger Windows 10 indstillinger for beskyttelse
 
1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. I venstre navigationslinje skal du **vælge Enheders** \> **politikker** .
1. Vælg en eksisterende Windows, og vælg derefter **Rediger**.
1. Vælg **Rediger** ud for en indstilling, du vil ændre, og klik derefter **på Gem**.

## <a name="available-settings"></a>Tilgængelige indstillinger

Alle indstillinger er som standard **til.** Følgende indstillinger er tilgængelige.
  
Få mere at vide under [Hvordan er beskyttelsesfunktionerne i Microsoft 365 Premium til indstillinger i Intune](map-protection-features-to-intune-settings.md). 


|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Beskyt pc'er mod virus og andre trusler ved hjælp af Windows Defender Antivirus  <br/> |Kræver, Windows Defender Antivirus er slået til for at beskytte pc'er mod risici ved at forbinde til internettet.  <br/> |
|Beskyt pc'er mod webbaserede trusler i Microsoft Edge  <br/> |Slår indstillinger i Edge til for at beskytte brugere mod skadelige websteder og downloads.  <br/> |
|Brug regler, der reducerer enheders angrebsoverflade  <br/> |Når dette er slået til, hjælper reduktion af angrebsoverfladen med at blokere for handlinger og apps, som typisk benyttes af malware til at inficere enheder. Denne indstilling er kun tilgængelig, hvis Windows Defender Antivirus er indstillet til Til. Se [Reducer angrebsoverfladerne for](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) at få mere at vide.  <br/> |
|Beskyt mapper mod trusler som f.eks. ransomware  <br/> |Denne indstilling bruger kontrolleret mappeadgang til at beskytte virksomhedsdata mod ændringer fra mistænkelige eller skadelige apps, f.eks ransomware. Disse typer af apps er blokeret fra at foretage ændringer i beskyttede mapper. Denne indstilling er kun tilgængelig, hvis Windows Defender Antivirus er indstillet til Til. Se [Beskyt mapper med styret mappeadgang for at få](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA) mere at vide.  <br/> |
|Forhindre netværksadgang til potentielt skadeligt indhold på internettet  <br/> |Brug denne indstilling til at blokere udgående brugerforbindelser til internetadresser med dårligt ry, som kan hoste forsøg på phishing, udnyttelse eller andet skadeligt indhold. Denne indstilling er kun tilgængelig, hvis Windows Defender Antivirus er indstillet til **Til**. Du kan få mere at vide [under Beskyt dit netværk](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus).  <br/> |
|Hjælp med at beskytte filer og mapper på pc'er mod uautoriseret adgang med BitLocker  <br/> |BitLocker beskytter data ved at kryptere harddiske på computeren og beskytter mod dataeksponering, hvis en computer mistes eller bliver stjålet. Du kan finde flere oplysninger under [Ofte stillede spørgsmål om BitLocker](/windows/security/information-protection/BitLocker/BitLocker-frequently-asked-questions).  <br/> |
|Tillad brugere at downloade apps fra Microsoft Store  <br/> |Giver brugere mulighed for at downloade og installere apps fra Microsoft Store. Apps indeholder alt fra spil til produktivitetsværktøjer, så vi lader denne indstilling være slået **Til**, men du kan slå den fra, hvis du vil have ekstra sikkerhed.  <br/> |
|Give brugere adgang til Cortana  <br/> |Cortana kan være meget nyttig! Cortana kan slå indstillingerne til eller fra for dig, give vejledning, og sørge for, at du når dine aftaler til tiden, så vi holder **denne indstilling slået** Til som standard.  <br/> |
|Tillad brugere at modtage Windows tip og reklamer fra Microsoft  <br/> |Windows kan være praktiske og hjælpe med at orientere brugerne, når der frigives nye funktioner.  <br/> |
|Hold Windows 10-enheder opdateret automatisk  <br/> |Sørg for, Windows 10-enheder automatisk modtager de seneste opdateringer.  <br/> |
|Slå enhedsskærmen fra, når den er inaktiv i denne periode  <br/> |Sørg for, at virksomhedsdata er beskyttet, hvis en bruger er inaktiv. En bruger arbejder måske på et offentligt sted, f.eks. en café, og går væk eller bliver forstyrret et øjeblik, så deres enhed er sårbar over for tilfældige blikke. Med denne indstilling kan du styre, hvor længe brugeren kan være inaktiv, før skærmen slukker.  <br/> |

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)