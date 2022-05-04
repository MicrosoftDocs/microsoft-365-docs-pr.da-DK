---
title: Om bord på Windows 10- eller Windows 11 enheder i Microsoft 365 oversigt
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Onboarde Windows 10 og Windows 11 enheder i Microsoft 365
ms.openlocfilehash: 876bd3f2d825fc1b698d3c7b9a76b1c7f115aedf
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/04/2022
ms.locfileid: "65187893"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Onboard Windows 10- og Windows 11-enheder i Microsoft 365 oversigt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

Forebyggelse af datatab for slutpunkter (Slutpunkt DLP) og styring af insiderrisiko kræver, at Windows 10 Windows og Windows 11 enheder onboardes i tjenesten, så de kan sende overvågningsdata til tjenesterne.
 
Med Slutpunkt DLP kan du overvåge Windows 10 eller Windows 11 enheder og registrere, når følsomme elementer bruges og deles. Dette giver dig den synlighed og kontrol, du har brug for, for at sikre, at de bruges og beskyttes korrekt, og for at forhindre risikable funktionsmåder, der kan kompromittere dem. Du kan finde flere oplysninger om alle Microsofts DLP-tilbud under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md). Hvis du vil vide mere om Endpoint DLP, skal [du se Få mere at vide om forebyggelse af datatab for Slutpunkt](endpoint-dlp-learn-about.md).

Insiderrisikostyring bruger hele bredden af tjenesten og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikable brugeraktivitet. Ved hjælp af logge fra Microsoft 365 og Microsoft Graph giver insiderrisikostyring dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer og træffe foranstaltninger til at afhjælpe disse risici. Du kan finde flere oplysninger under [Få mere at vide om styring af insiderrisiko](insider-risk-management.md).

Onboarding af enheder deles på tværs af Microsoft 365 og Microsoft Defender for Endpoint (MDE). Hvis du allerede har onboardet enheder til MDE, vises de på listen over administrerede enheder, og der er ikke behov for yderligere trin for at onboarde disse specifikke enheder. Onboarding-enheder i Compliance Center onboarder dem også i MDE.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Se licenskravene [her](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>Tilladelser

Hvis du vil aktivere enhedshåndtering, skal den konto, du bruger, være medlem af en af disse roller:

- Global administrator
- Sikkerhedsadministrator
- Overholdelsesadministrator

Hvis du vil bruge en brugerdefineret konto til at få vist indstillingerne for enhedshåndtering, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator
- Administrator af overholdelsesdata
- Global læser

Hvis du vil bruge en brugerdefineret konto til at få adgang til onboarding-/offboarding-siden, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator

Hvis du vil bruge en brugerdefineret konto til at slå enhedsovervågning til/fra, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator

### <a name="prepare-your-windows-devices"></a>Forbered dine Windows enheder

Sørg for, at de Windows enheder, du har brug for at onboarde, opfylder disse krav.

1. Skal køre Windows 10 x64 build 1809 eller nyere eller Windows 11.

2. Antimalware-klientversionen er 4.18.2110 eller nyere. Kontrollér din aktuelle version ved at åbne Windows Sikkerhed app, vælge ikonet Indstillinger og derefter vælge Om. Versionsnummeret er angivet under Antimalware-klientversion. Opdater til den nyeste Antimalware-klientversion ved at installere Windows Update KB4052623.

   > [!NOTE]
   > Ingen af Windows Sikkerhed komponenter skal være aktive, men [overvågning af beskyttelse i realtid og overvågning af funktionsmåde](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)) skal aktiveres.

3. Følgende Windows Opdateringer til Windows 10 installeres for enheder, der overvåges.

   > [!NOTE]
   > Disse opdateringer er ikke en forudsætning for onboarding af en enhed, men indeholder rettelser til vigtige problemer, som derfor skal installeres, før du bruger produktet.
   >
    > - For Windows 10 1809 - KB4559003, KB4577069, KB4580390
    > - For Windows 10 1903 eller 1909 - KB4559004, KB4577062, KB4580386
    > - For Windows 10 2004 - KB4568831, KB4577063

4. Alle enheder skal være en af disse:

   - [Azure Active Directory (Azure AD) er tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
   - [Hybrid Azure AD-tilknyttet](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD registreret](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Der er installeret og opdateret en understøttet version af Microsoft Office. Du opnår den mest robuste beskyttelse og brugeroplevelse ved at sikre, at Microsoft 365 Apps version 16.0.14701.0 eller nyere er installeret.
> [!NOTE]
   > - Hvis du kører Office 365 – KB 4577063 er påkrævet.
   > - Hvis du bruger månedlig Enterprise Channel af Microsoft 365 Apps version 2004-2008, skal du opdatere til version 2009 eller nyere. Se [Opdateringshistorik for Microsoft 365 Apps (angivet efter dato)](/officeupdates/update-history-microsoft365-apps-by-date) for aktuelle versioner. Du kan få mere at vide om kendte problemer i afsnittet Office Suite i [produktbemærkninger til aktuelle kanalversioner i 2020](/officeupdates/current-channel#version-2010-october-27).

6. Hvis du har slutpunkter, der bruger en enhedsproxy til at oprette forbindelse til internettet, skal du følge procedurerne i [Konfigurer indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Onboarding af Windows 10- eller Windows 11 enheder

Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres på Microsoft Purview-overholdelsesportalen.

Når du vil onboarde enheder, der endnu ikke er onboardet, skal du downloade det relevante script og installere det på disse enheder. Følg onboardingprocedurerne for enheden nedenfor.

Hvis du allerede har enheder, der er onboardet i [Microsoft Defender for Endpoint](/windows/security/threat-protection/), vises de allerede på listen over administrerede enheder.

I dette installationsscenarie skal du onboarde Windows 10 eller Windows 11 enheder, der endnu ikke er onboardet.

1. Åbn [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com). Vælg **Indstillinger** >  **Enable enhedsovervågning**.

   > [!NOTE]
   > Selvom det normalt tager ca. 60 sekunder, før onboarding af enheder er aktiveret, skal du vente op til 30 minutter, før du engagerer dig i Microsoft-support.

2. Åbn siden Indstillinger for Overholdelsescenter, og vælg **Slå Windows enhedsovervågning til**.

3. Vælg **Enhedshåndtering** for at åbne listen **Enheder** . 

> [!NOTE]
> Hvis du tidligere har udrullet Microsoft Defender for Endpoint, vises alle de enheder, der blev onboardet under denne proces, på listen **Enheder**. Der er ingen grund til at onboarde dem igen.

4. Vælg **Onboarding** for at starte onboardingprocessen.

5. Vælg den måde, du vil installere på disse ekstra enheder på på listen **Installationsmetode** , og **download derefter pakken**.

6. Vælg den relevante procedure, der skal følges, i nedenstående tabel:

Emne | Beskrivelse
:---|:---
[Onboarde Windows 10 eller 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md) | Brug Gruppepolitik til at installere konfigurationspakken på enheder.
[Onboarde Windows 10 eller 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Du kan bruge enten Microsoft Endpoint Configuration Manager (aktuel forgrening) version 1606 eller Microsoft Endpoint Configuration Manager (aktuel forgrening) version 1602 eller tidligere til at installere konfigurationspakken på enheder.
[Onboarde Windows 10 eller 11 enheder ved hjælp af værktøjer til Enhedshåndtering til mobilenheder](device-onboarding-mdm.md) | Brug værktøjer til Enhedshåndtering mobilenheder eller Microsoft Intune til at installere konfigurationspakken på enheden.
[Onboarde Windows 10 eller 11 enheder ved hjælp af et lokalt script](device-onboarding-script.md) | Få mere at vide om, hvordan du bruger det lokale script til at installere konfigurationspakken på slutpunkter.
[Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md) | Få mere at vide om, hvordan du bruger konfigurationspakken til at konfigurere VDI-enheder.

## <a name="see-also"></a>Se også

- [Få mere at vide om styring af insider-risiko](insider-risk-management.md)
- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Onboardingværktøjer og -metoder til Windows 10 maskiner](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD tilsluttede enheder](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
