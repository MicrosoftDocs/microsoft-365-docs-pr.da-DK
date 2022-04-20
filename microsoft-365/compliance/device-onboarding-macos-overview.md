---
title: Onboard macOS-enheder i Microsoft 365 oversigt
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Få mere at vide om onboarding af macOS-enheder i overholdelsesløsninger
ms.openlocfilehash: 6cc3323a94ee609c3c6674c12eb99fad3f18f3b4
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952710"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview"></a>Onboard macOS-enheder i Microsoft 365 oversigt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

MacOS-enheder kan onboardes i Microsoft Purview-løsninger ved hjælp af enten Intune eller JAMF-Pro. Onboardingprocedurerne varierer, afhængigt af hvilken administrationsløsning du bruger. Hvis dine macOS-enheder allerede er blevet onboardet i Microsoft Defender for Endpoint (MDE), er der færre trin. Se [Næste trin](#next-steps) for at få links til de relevante procedurer for dig.

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

## <a name="before-you-begin"></a>Før du begynder

Før du kommer i gang med Endpoint DLP på macOS-enheder (Catalina 10.15 eller nyere), bør du blive fortrolig med disse artikler:

- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)

Hvis du slet ikke er bekendt med DLP, bør du også gøre dig bekendt med disse artikler:

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Reference til politik til forebyggelse af datatab](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Hvis du ikke er bekendt med Insider Risk, bør du gøre dig bekendt med disse artikler:

 - [Styring af insider-risiko](insider-risk-management.md)
 - [Plan for styring af insider-risiko](insider-risk-management-plan.md#plan-for-insider-risk-management)

Dine macOS-enheder skal allerede administreres via Intune eller JAMF-Pro.
 
- Hvis du vil onboarde i Intune, skal du se [Installationsvejledning: Administrer macOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) og [Tilmeld din Mac med Intune-firmaportal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- For at komme ombord i JAMF Pro se, [JAMF Pro administratorvejledning](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) og [JAMF Pro installations- og konfigurationsvejledning til Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- Installér v95+ Edge-browseren på dine macOS-enheder 

## <a name="licensing-guidance"></a>Licensvejledning

Se [Microsoft 365 licensvejledning til beskyttelse af oplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>Aktiviteter, der kan begrænses på macOS 

Når en macOS-enhed er onboardet i Microsoft Purview-løsninger, kan du overvåge og begrænse disse handlinger med DLP-politikker (forebyggelse af datatab).

**Kopiér til et flytbart USB-medie** – når denne handling gennemtvinges, blokeres, advares eller overvåges kopiering eller flytning af beskyttede filer fra en slutpunktsenhed til flytbare USB-medier 

**Kopiér til netværksshares** – når denne handling gennemtvinges, blokerer, advarer eller overvåger kopiering eller flytning af beskyttede filer fra en slutpunktsenhed til et netværksshare 

**Udskriv** – når denne handling gennemtvinges, blokerer, advarer eller overvåger den, når beskyttede filer udskrives fra en slutpunktenhed 

**Kopiér til Udklipsholder** – når denne handling gennemtvinges, blokerer, advarer eller overvåger den data i en beskyttet fil, der kopieres til en udklipsholder på en slutpunktsenhed 

**Upload til skyen** – denne handling blokerer, advarer eller overvåger, når beskyttede filer forhindres i eller må uploades til cloudtjenester baseret på listen over tilladte/ikke-tilladte domæner i globale indstillinger. Når denne handling er indstillet til at advare eller blokere, blokeres andre browsere (defineret på listen over ikke-tilladte browsere under Globale indstillinger) fra at få adgang til filen. 

**Tilgås af ikke-tilladte apps** – når denne handling gennemtvinges, forhindrer denne handling programmer, der findes på listen over ikke-tilladte apps (som defineret i Globale indstillinger), i at få adgang til beskyttede filer på en slutpunktsenhed. Eksempelscenarier 

## <a name="onboarding-devices-into-device-management"></a>Onboarding af enheder i enhedshåndtering

Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres på Microsoft Purview-overholdelsesportalen.

Når du vil onboarde enheder, der endnu ikke er onboardet, skal du downloade det relevante script og installere det på disse enheder. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Åbn [microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) **Indstillinger** side, og vælg **Aktivér enhedsovervågning**.

   > [!NOTE]
   > Selvom det normalt tager ca. 60 sekunder, før onboarding af enheder er aktiveret, skal du vente op til 30 minutter, før du engagerer dig i Microsoft-support.

2. Åbn siden Indstillinger for Overholdelsescenter, og vælg **Slå macOS-enhedsovervågning** til.

## <a name="next-steps"></a>Næste trin

Det er nødvendigt at overføre enheder til Microsoft Purview-løsninger for at modtage DLP-sensortelemetri og gennemtvinge politikker til forebyggelse af datatab. 

Emne | Beskrivelse
:---|:---
|[Onboarde og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Intune](device-onboarding-offboarding-macos-intune.md)|MacOS-enheder, der administreres via Intune
|[Onboarde og offboard macOS-enheder i overholdelsesløsninger ved hjælp af Intune til Microsoft Defender for Endpoint kunder](device-onboarding-offboarding-macos-intune-mde.md) |MacOS-enheder, der administreres via Intune, og som har Microsoft Defender for Endpoint (MDE) installeret på dem
|[Onboard og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md) | Til macOS-enheder, der administreres via JAMF-Pro
|[Onboarde og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF-Pro til Microsoft Defender for Endpoint kunder](device-onboarding-offboarding-macos-jamfpro-mde.md)|MacOS-enheder, der administreres via JAMF-Pro, og som har Microsoft Defender for Endpoint (MDE) installeret på dem


## <a name="related-topics"></a>Relaterede emner

- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Supportmatrix til tip til DLP-politik på tværs af Microsoft-apps](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
