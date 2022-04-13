---
title: Delte enheder
description: Sådan og hvornår du skal bruge delt enhedstilstand
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 8c8d79313ee858ebcac8754b96046b517a3f614a
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835968"
---
# <a name="shared-devices"></a>Delte enheder

Microsoft Managed Desktop giver dig mulighed for at registrere enheder i "delt enhedstilstand" på samme måde som den delte enhedstilstand, der tilbydes af [Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

Enheder i denne tilstand er optimeret til situationer, hvor brugerne ikke er bundet til et enkelt skrivebord og ofte ændrer enheder. Det kan f.eks. være frontlinjearbejdere, f.eks. Du kan anvende en hvilken som helst af de Microsoft Managed Desktop [profiler](profiles.md) på enheder i denne tilstand. Enheder, der er registreret i denne tilstand, har nogle vigtige forskelle:

- [Enhedslager](#device-storage) er optimeret til delte brugere.
- [Inaktive konti](#deletion-of-inactive-accounts) slettes.
- [Gæstekonti](#guest-accounts) understøttes ikke som standard.
- [Microsoft 365 Licenser til programmer](#microsoft-365-apps-for-enterprise) til virksomheder er optimeret til delte enheder.

Da du vælger at bruge tilstanden delt enhed på registreringstidspunktet i Microsoft Managed Desktop skal du fjerne registreringen og registrere den igen, hvis du senere vil skifte fra denne tilstand.

## <a name="when-to-use-shared-device-mode"></a>Hvornår skal du bruge tilstanden delt enhed?

Brug tilstanden delt enhed i situationer, hvor brugerne ofte ændrer enheder.

Bankkontører kan f.eks. være placeret ét sted, hvor de administrerer indbetalinger, men flytter til et back office for at hjælpe kunder med realkreditlån. På hver af disse placeringer kører enheden forskellige programmer og er optimeret til disse opgaver, selvom de bruges af flere personer.

Plejepersonalet flytter typisk mellem lokaler og kontorer, når de interagerer med patienterne. De kan logge på en arbejdsstation på et kontor, men oprette forbindelse til deres fjernskrivebord og tage noter og gentage denne proces i et andet rum med en anden patient.

## <a name="when-not-to-use-shared-device-mode"></a>Når du ikke skal bruge delt enhedstilstand

Delt enhedstilstand er ikke et godt valg i disse situationer:

- Når en brugers filer skal gemmes lokalt i stedet for i cloudmiljøet.
- Hvis brugeroplevelsen skal være anderledes for forskellige brugere på enheden.
- Hvis sættet af programmer, som hver bruger har brug for, varierer meget.

## <a name="register-new-devices-using-the-windows-autopilot-self-deploying-mode-profile-in-microsoft-managed-desktop"></a>Registrer nye enheder ved hjælp af profilen til selvudrulning af Windows Autopilot i Microsoft Managed Desktop

Uanset om du eller en partner håndterer enhedsregistrering, kan du vælge at bruge profilen [Windows Autopilot til selvudrulningstilstand](/mem/autopilot/self-deploying) i Microsoft Managed Desktop.

### <a name="before-you-begin"></a>Før du begynder

Gennemse kravene til selvudrulning af Windows Autopilot:

> [!IMPORTANT]
> Du kan ikke automatisk tilmelde en enhed via Autopilot efter en indledende udrulning i selvudrulningstilstand. Slet i stedet enhedsposten i [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431). Hvis du vil slette enhedsposten fra Administration, skal du vælge **EnhederAlle** >  **enheder** > vælge de enheder, du vil slette, > **Slet**.  Du kan få flere oplysninger under [Opdateringer til Windows autopilotlogon og -udrulningsoplevelse](https://techcommunity.microsoft.com/t5/intune-customer-success/updates-to-the-windows-autopilot-sign-in-and-deployment/ba-p/2848452).

#### <a name="trusted-platform-module"></a>Platformmodul, der er tillid til

Selvudrulningstilstand bruger en enheds TPM 2.0-hardware til at godkende enheden i en organisations Azure Active Directory lejer. Enheder uden TPM 2.0 kan derfor ikke bruge denne tilstand. Enheder skal også understøtte attestation af TPM-enheder. Alle nye Windows enheder skal opfylde disse krav. TPM-attestationsprocessen kræver også adgang til et sæt HTTPS-URL-adresser, der er entydige for hver TPM-udbyder. Du kan få flere oplysninger i indstillingen autopilot selvudrulningstilstand og præklargøring af Autopilot i [Netværkskrav](/mem/autopilot/self-deploying#requirements). Du kan få flere oplysninger om krav til Windows Autopilot-software under [Windows Krav til Autopilot-software](/mem/autopilot/software-requirements).

> [!TIP]
> Hvis du forsøger at installere selvudrulningstilstand på en enhed, der ikke understøtter TPM 2.0, eller den er på en virtuel maskine, mislykkes processen, når du bekræfter enheden med følgende fejl: 0x800705B4 timeoutfejl (Virtuelle Hyper-V-TPM'er understøttes ikke). Bemærk også, at der kræves Windows 10 version 1903 eller nyere for at bruge selvudrulningstilstand på grund af problemer med attestation af TPM-enheder i Windows 10 version 1809. Da Windows 10 Enterprise 2019 LTSC er baseret på Windows 10 version 1809, understøttes selvudrulningstilstand heller ikke på Windows 10 Enterprise 2019 LTSC.
>
> Du kan finde flere oplysninger om andre kendte problemer og gennemse løsninger [under Windows Kendte problemer på Autopilot](/mem/autopilot/known-issues) og [Foretag fejlfinding af import og tilmelding af Autopilot-enheder](/mem/autopilot/troubleshoot-device-enrollment).

### <a name="steps-to-register-devices-to-use-the-windows-autopilot-self-deploying-mode-profile"></a>Trin til registrering af enheder til brug af selvudrulningstilstandsprofilen Windows Autopilot

Hvis du selv registrerer enheder, skal du importere nye enheder til bladet Windows Autopilot-enheder.

**Sådan importerer du nye enheder til bladet Windows Autopilot-enheder:**

1. Indsaml [hardwarehashen](../get-started/manual-registration.md#obtain-the-hardware-hash) for nye enheder, du vil tildele profilen Windows Autopilot Selvinstallationstilstand.
2. Gå til [Microsoft Endpoint Manager-portalen](https://endpoint.microsoft.com).
2. Vælg **Enheder** i navigationsmenuen til venstre.
3. Vælg **Windows** i afsnittet **Efter platform**. Vælg derefter **Windows Tilmelding**.
4. I afsnittet **Windows Autopilot Deployment Program** skal du vælge **Enheder**.
5. [Importér](../get-started/manual-registration.md#register-devices-by-using-the-admin-portal) den .CSV fil, der indeholder alle de hardwarehashes, der blev indsamlet i trin #1.
6. Når du har uploadet Windows Autopilot-enheder, skal du redigere de importerede enheders gruppemærkeattribut, så Microsoft Managed Desktop kan registrere dem ved hjælp af den selvudrullende tilstandsprofil Windows Autopilot. Nedenfor kan du se attributterne for gruppemærket. Du skal føje **-Shared** til gruppemærket, som vist i nedenstående tabel:

| Enhedsprofil | Autopilotgruppemærke (standardtilstand) | Gruppekode (tilstand for delt enhed) |
| ----- | ----- | ----- |
| Følsomme data | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Power-bruger | Microsoft365Managed_PowerUser | Understøttes ikke |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

> [!WARNING]
> Prøv ikke at redigere attributten for gruppefanen ved at føje **-Shared** til enheder, der tidligere er importeret til Windows Autopilot. Enheder, der allerede er importeret til Windows Autopilot, og som bruger et af Microsoft Managed Desktop gruppemærker, der starter med *Microsoft365Managed_*, men uden **at -Shared** tilføjes i starten, er allerede en del af en anden Azure Active Directory gruppe. Denne Azure Active Directory gruppe har ikke fået tildelt den Windows autopilotens selvudrulningstilstandsprofil. Hvis du skal omforme en eksisterende enhed til at være en delt enhed, skal du slette og registrere enheden igen i Windows Autopilot igen.

Hvis du har en partnertilmeldingsenheder, skal du følge trinnene i [Partnerregistrering](../get-started/partner-registration.md), men føje **-Delt** til gruppemærket, som vist i tabellen ovenfor.

## <a name="consequences-of-shared-device-mode"></a>Konsekvenser af delt enhedstilstand

### <a name="device-storage"></a>Enhedslager

Brugere af delte enheder skal have sikkerhedskopieret deres data i skyen, så de kan følge dem til andre enheder. Når du har registreret enheder i delt enhedstilstand, skal du sørge for at aktivere [omdirigeringsfunktionerne](/onedrive/redirect-known-folders) for OneDrive [filer on-demand](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) og kendte mapper. Denne fremgangsmåde minimerer den effekt, som hver brugerprofil har på enhedens lager. Enheder i delt enhedstilstand sletter automatisk brugerprofiler, hvis den ledige diskplads falder til under 25 %. Denne aktivitet er planlagt til midnat på enhedens lokale tidspunkt, medmindre lageret bliver kritisk begrænset.

Microsoft Managed Desktop bruger [CSP'en for SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) til at udføre disse handlinger, så sørg for, at du ikke selv bruger disse CSP'er.

> [!IMPORTANT]
> Oplær dine brugere, at når de har downloadet en stor fil, skal de bekræfte, at de kan se det grønne kontrolikon på filen, før de logger af. Hvis vedkommendes konto slettes som en del af oprydningshandlinger, og filen ikke uploades fuldstændigt i OneDrive, vil filen gå tabt permanent.

### <a name="deletion-of-inactive-accounts"></a>Sletning af inaktive konti

Tilstanden Delt enhed fjerner alle konti, der ikke er logget på i mere end 30 dage.

### <a name="guest-accounts"></a>Gæstekonti

Enheder i delt enhedstilstand tillader kun konti, der er tilsluttet et domæne. Hvis du har brug for gæstekonti på en enhed, kan du sende en [anmodning om ændring](../working-with-managed-desktop/admin-support.md) for at anmode om, at de aktiveres.

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

[Microsoft 365 Apps for enterprise](/microsoft-365/managed-desktop/get-started/m365-apps) giver typisk en bestemt bruger mulighed for at installere disse apps på kun fem enheder på samme tid. I delt enhedstilstand tæller appsene ikke med i forhold til grænsen, så de kan bruge dem, mens de roaming mellem enheder. Udrulning og opdateringer af Microsoft 365 Apps for enterprise fungerer som normalt.

### <a name="device-profiles"></a>Enhedsprofiler

I delt enhedstilstand kan du kun have én [enhedsprofil](profiles.md) på en given enhed. Power-brugerprofilen understøttes heller ikke i øjeblikket i delt enhedstilstand.

### <a name="apps-and-policies-assigned-to-users"></a>Apps og politikker, der er tildelt til brugere

På delte enheder skal du tildele alle apps eller politikker, som du administrerer dig selv, til *enhedsgrupper* og ikke brugergrupper. Tildeling til enhedsgrupper sikrer, at hver bruger har en mere ensartet oplevelse. Undtagelsen er [Firmaportal](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Begrænsninger for delt enhedstilstand

### <a name="windows-hello"></a>Windows Hello

Windows Hello bruger chipkortemulering til at [cachelagre bruger-PIN'er](/windows/security/identity-protection/hello-for-business/hello-faq) på en sikker måde, hvilket minimerer det antal gange, brugerne skal godkende. Men Windows tillader kun 10 chipkort ad gangen på en given enhed. Når en 11. bruger logger på for første gang, mister en af de eksisterende konti deres chipkort. De kan logge på, men deres pinkode cachelagres ikke.

### <a name="universal-print"></a>Universel udskrivning

Når Universal print installerer en printer til en enkelt bruger på en delt enhed, bliver printeren tilgængelig for alle brugere af den pågældende enhed. Det er ikke muligt at isolere printere mellem brugere på delte enheder.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Begrænsninger for delt enhedstilstand i den offentlige prøveversion

### <a name="primary-user"></a>Primær bruger

Hver Microsoft Intune enhed har en primær bruger, som tildeles, når en enhed konfigureres af Autopilot. Men når enheder deles, kræver Intune, at den primære bruger fjernes.

> [!IMPORTANT]
> Mens tilstanden for delte enheder er i offentlig prøveversion, skal du sørge for at fjerne den primære bruger ved at følge disse trin: Log på Microsoft Endpoint Manager Administration, vælg **EnhederAlle**> **enheder**, vælg en enhed, vælg derefter **EgenskaberFjern**> **primær bruger**, og slet den bruger, der er angivet der.

### <a name="deploying-apps-with-company-portal"></a>Udrulning af apps med Firmaportal

Nogle apps behøver sandsynligvis ikke at være til stede på alle enheder, så du foretrækker måske, at brugerne kun installerer disse apps, når de har brug for dem[, fra Firmaportal](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Managed Desktop deaktiverer som standard Firmaportal for enheder i delt enhedstilstand. Hvis du vil have aktiveret Firmaportal, kan du sende en [ændringsanmodning](../working-with-managed-desktop/admin-support.md). Du skal dog være opmærksom på nogle begrænsninger i denne funktion i denne offentlige prøveversion:

- Hvis du vil gøre en app tilgængelig for brugere i Firmaportal, skal [du tildele en brugergruppe](/mem/intune/apps/apps-deploy) til den pågældende app i Intune og derefter føje hver bruger til den pågældende brugergruppe.
- Enheder kan ikke have en [primær bruger](#primary-user).
- Hvis du vil fjerne en app, som en bruger har installeret via Firmaportal, skal du fjerne appen fra alle brugere på den pågældende enhed.

> [!CAUTION]
> Firmaportal understøtter ikke programmer, der er tildelt enhedsgrupper, som tilgængelige.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Geninstallation af Microsoft 365 Apps for Enterprise

Hvis Microsoft 365 Apps skal geninstalleres i den offentlige prøveversion, skal brugerne kontakte deres lokale supportmedarbejdere for at anmode om at få en agent til at hæve og geninstallere Microsoft 365 Apps for enterprise på den pågældende enhed.

### <a name="microsoft-teams"></a>Microsoft Teams

Når en bruger starter Teams første gang, bliver vedkommende bedt om at opdatere appen, før vedkommende kan bruge den. Når de tillader opdateringen, holder Teams sig opdateret i baggrunden.
