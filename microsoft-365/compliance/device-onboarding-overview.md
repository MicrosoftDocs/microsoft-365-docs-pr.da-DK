---
title: Onboard Windows 10 eller Windows 11 enheder i Microsoft 365 oversigt
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
description: Onboard Windows 10 og Windows 11 enheder i Microsoft 365
ms.openlocfilehash: ea1038554349b6c035c52bd3d3429d71d7d866bc
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387127"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Onboard Windows 10 og Windows 11 enheder i Microsoft 365 oversigt

**Gælder for:**

- [Forebyggelse af datatab på slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Forebyggelse af datatab på slutpunkter (Endpoint DLP) og insider-risikostyring kræver, at Windows 10 Windows- og Windows 11-enheder er onboardet til tjenesten, så de kan sende overvågningsdata til tjenesterne.
 
Slutpunkt DLP gør det muligt at overvåge Windows 10 eller Windows 11 enheder og registrere, når følsomme elementer bruges og deles. Dette giver dig den synlighed og kontrol, du skal bruge for at sikre, at de bruges og beskyttes korrekt, og for at forhindre risikabel adfærd, der kan kompromittere dem. Du kan finde flere oplysninger om alle Microsofts DLP-tilbud i [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md). Du kan få mere at vide om Endpoint DLP under [Få mere at vide om forebyggelse af datatab i Slutpunkt](endpoint-dlp-learn-about.md).

Insider-risikostyring bruger den fulde bredde i tjenesten og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikabel brugeraktivitet. Insider-risikostyring giver dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer og træffe foranstaltninger for at reducere disse risici ved hjælp af logge fra Microsoft 365 og Microsoft Graph. Få mere at vide under [Få mere at vide om insider-risikostyring i Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365).

Onboarding af enheder deles på tværs Microsoft 365 Microsoft Defender for Endpoint (MDE). Hvis du allerede har onboardede enheder til MDE, vises de på listen over administrerede enheder, og der er ikke brug for yderligere trin for at onboarde disse bestemte enheder. Onboardingenheder i Compliance Center onboarder dem også i MDE.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Kontrollér licenskravene [her](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>Tilladelser

For at aktivere enhedshåndtering skal den konto, du bruger, være medlem af en af disse roller:

- Global administrator
- Sikkerhedsadministrator
- Overholdelsesadministrator

Hvis du vil bruge en brugerdefineret konto til at få vist indstillingerne for enhedsadministration, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator
- Dataadministrator for overholdelse af regler og standarder
- Global læser

Hvis du vil bruge en brugerdefineret konto til at få adgang til onboarding-/offboarding-siden, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator

Hvis du vil bruge en brugerdefineret konto til at slå enhedsovervågning til/fra, skal den være i en af disse roller:

- Global administrator
- Overholdelsesadministrator

### <a name="prepare-your-windows-devices"></a>Forbered dine Windows enheder

Sørg for, at Windows enheder, du skal bruge til onboarding, opfylder disse krav.

1. Skal køre Windows 10 x64 build 1809 eller nyere eller Windows 11.

2. Antimalware-klientversion er 4.18.2110 eller nyere. Kontrollér din aktuelle version ved at Windows Sikkerhed appen, vælge ikonet Indstillinger og derefter vælge Om. Versionsnummeret er angivet under Klientversionen af antimalware. Opdater til den nyeste Antimalware-klientversion ved at installere Windows Update KB4052623.

   > [!NOTE]
   > Ingen af Windows Sikkerhed komponenter skal være aktive, men beskyttelse [i realtid og overvågning](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) af funktionsmåde) skal være aktiveret.

3. Følgende trin Windows opdateringer til Windows 10 installeres for enheder, der overvåges.

   > [!NOTE]
   > Disse opdateringer er ikke en forudsætning for at kunne onboarde en enhed, men indeholder rettelser til vigtige problemer, som derfor skal installeres, før produktet bruges.
   >
    > - Til Windows 10 1809 - KB4559003, KB4577069, KB4580390
    > - For Windows 10 1903 eller 1909 – KB4559004, KB4577062, KB4580386
    > - Til Windows 10 2004 – KB4568831, KB4577063

4. Alle enheder skal være en af følgende:

   - [Azure Active Directory (Azure AD) er tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
   - [Hybrid Azure AD-tilknyttet](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD registreret](/azure/active-directory/user-help/user-help-register-device-on-network)

5. En understøttet version Microsoft Office installeret og opdateret. For at opnå den mest robuste beskyttelse og brugeroplevelse skal du Microsoft 365 Apps version 16.0.14701.0 eller nyere installeret.
> [!NOTE]
   > - Hvis du kører Office 365 - KB 4577063 er påkrævet.
   > - Hvis du er på Månedlig virksomhedskanal i Microsoft 365 Apps versionerne 2004-2008, skal du opdatere til version 2009 eller nyere. Se [Opdateringsoversigt for Microsoft 365 Apps (angivet efter dato)](/officeupdates/update-history-microsoft365-apps-by-date) for aktuelle versioner. Du kan få mere at vide om kendte problemer i afsnittet Office Suite i Produktbemærkninger til udgivelser [for Aktuel kanal i 2020](/officeupdates/current-channel#version-2010-october-27).

6. Hvis du har slutpunkter, der bruger en enhedsproxy til at oprette forbindelse til internettet, skal du følge fremgangsmåden i Konfigurer enhedsproxy og [indstillinger for internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Onboarding-Windows 10 eller Windows 11 enheder

Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres i Microsoft 365 Overholdelse.

Når du vil onboarde enheder, der endnu ikke er blevet onboardet, skal du downloade det relevante script og udrulle det på disse enheder. Følg fremgangsmåderne for onboarding af enheder nedenfor.

Hvis du allerede har enheder onboardet i [Microsoft Defender for Endpoint](/windows/security/threat-protection/), vises de allerede på listen over administrerede enheder.

I dette installationsscenarie kan du onboarde Windows 10 eller Windows 11 enheder, der endnu ikke er blevet onboardet.

1. Åbn [Microsofts center til overholdelse af regler og standarder](https://compliance.microsoft.com). Vælg **Indstillinger** >  **Enable device monitoring**.

   > [!NOTE]
   > Det tager som regel ca. 60 sekunder, før onboarding af enheder er aktiveret, men det kan tage op til 30 minutter, før du går i gang med Microsoft Support.

2. Åbn siden med indstillinger for Overholdelsescenter, **og vælg Aktiv Windows af enheder**.

3. Vælg **Enhedshåndtering** for at åbne **listen** Enheder. 

> [!NOTE]
> Hvis du tidligere har installeret Microsoft Defender for Endpoint, vises alle de enheder, der blev onboardet under processen, på **listen** Enheder. Der er ingen grund til at onboarde dem igen.

4. Vælg **Onboarding** for at starte onboardingprocessen.

5. Vælg den måde, du vil installere på disse yderligere enheder på listen **Installationsmetode** , og **download derefter pakke**.

6. Vælg den relevante fremgangsmåde, der skal følges, i tabellen nedenfor:

Emne | Beskrivelse
:---|:---
[Onboard Windows 10 eller 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md) | Brug Gruppepolitik til at installere konfigurationspakken på enheder.
[Onboard Windows 10 eller 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Du kan enten bruge Microsoft Endpoint Configuration Manager (aktuel forgrening) version 1606 eller Microsoft Endpoint Configuration Manager (aktuel forgrening) version 1602 eller tidligere til at installere konfigurationspakken på enheder.
[Onboard Windows 10 eller 11 enheder ved hjælp af Enhedshåndtering mobilværktøjer](device-onboarding-mdm.md) | Brug mobilværktøjer Enhedshåndtering eller Microsoft Intune til at installere konfigurationspakken på enheden.
[Onboard Windows 10 eller 11 enheder ved hjælp af et lokalt script](device-onboarding-script.md) | Lær at bruge det lokale script til at installere konfigurationspakken på slutpunkter.
[Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md) | Få mere at vide om, hvordan du bruger konfigurationspakken til at konfigurere VDI-enheder.

Når en enhed er onboardet, bør den være synlig på listen over enheder og også starte rapportering af overvågningsaktivitetslogfiler til Aktivitetsstifinder.

### <a name="viewing-endpoint-dlp-alerts-in-dlp-alerts-management-dashboard"></a>Visning af slutpunkt-DLP-beskeder i dashboardet til administration af DLP-beskeder

1. Åbn siden forebyggelse af datatab i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> vælg Beskeder.

2. Se procedurerne i Sådan konfigurerer og får du vist beskeder [for dine DLP-politikker for](dlp-configure-view-alerts-policies.md) at få vist beskeder for dine Slutpunkt DLP-politikker.

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>Visning af slutpunkt-DLP-data i Aktivitetsstifinder

1. Åbn siden [Dataklassificering](https://compliance.microsoft.com/dataclassification?viewid=overview) for dit domæne i Microsoft 365 overholdelsescenter, og vælg Aktivitetsstifinder.

2. Se procedurerne i Introduktion til [Aktivitetsstifinder for at](data-classification-activity-explorer.md) få adgang til og filtrere alle data til dine slutpunktsenheder.

   > [!div class="mx-imgBorder"]
   > ![Filter til aktivitetsstifinder til slutpunktsenheder.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)


## <a name="see-also"></a>Se også

- [Få mere at vide om insider-risikostyring i Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Onboardingværktøjer og metoder til Windows 10 computere](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Enheder, der er forbundet til Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
