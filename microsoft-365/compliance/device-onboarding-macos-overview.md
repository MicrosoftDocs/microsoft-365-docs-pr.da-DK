---
title: Onboard macOS-enheder Microsoft 365 oversigt (forhåndsvisning)
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
description: Få mere at vide om onboarding af macOS-enheder i Løsninger til overholdelse af regler og standarder
ms.openlocfilehash: 783179ae749ac7cd6de671435927ba5bbdbdacad
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387009"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview-preview"></a>Onboard macOS-enheder Microsoft 365 oversigt (forhåndsvisning)

MacOS-enheder kan onboardes i Microsoft 365 løsninger til overholdelse af regler og standarder ved hjælp Intune eller SYLF Pro. Onboarding-procedurerne varierer, afhængigt af hvilken administrationsløsning du bruger. Hvis dine macOS-enheder allerede er blevet onboardet Microsoft Defender for Endpoint (MDE), er der færre trin. Se [Næste trin](#next-steps) for at få links til de relevante procedurer for dig.

**Gælder for:**

- [Forebyggelse af datatab på slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Før du begynder

Før du går i gang med slutpunkt DLP på macOS-enheder (Catalina 10.15 eller nyere), skal du gøre dig bekendt med disse artikler:

- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)

Hvis du slet ikke kender DLP, bør du også gøre dig bekendt med disse artikler:

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Reference til politik til forebyggelse af datatab](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Hvis du ikke kender til Insider Risk, bør du gøre dig bekendt med følgende artikler:

 - [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
 - [Plan for insider-risikostyring](insider-risk-management-plan.md#plan-for-insider-risk-management)

Dine macOS-enheder skal allerede administreres via Intune eller SYLTEF Pro.
 
- For at komme i gang Intune du se [Installationsvejledning: Administrer macOS-enheder Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) [og Tilmeld din Mac med Intune-firmaportal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Du kan finde oplysninger om onboarding til SYLF Pro, ved at se [GUIDE](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro [for ADMINISTRATORER og SYLF Pro installations- og konfigurationsvejledning til Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- Installér browseren v95+ Edge på dine macOS-enheder 

## <a name="licensing-guidance"></a>Vejledning til licenser

Se Se [Microsoft 365 for informationsbeskyttelse](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>Aktiviteter, der kan begrænses på macOS 

Når en macOS-enhed er integreret i Microsoft 365-overholdelsesløsninger, kan du overvåge og begrænse disse handlinger med DLP-politikker (forebyggelse af datatab).

**Kopiér til et FLYTBART USB-medie** – når dette gennemtvinges, blokerer, advarer eller overvåges kopiering eller flytning af beskyttede filer fra en slutpunktsenhed til flytbare USB-medier 

**Kopiér til netværksshares** – når gennemtvinges, blokerer, advarer eller overvåges kopiering eller flytning af beskyttede filer fra en slutpunktsenhed til et netværksshare 

**Udskriv** – når gennemtvinges, blokerer, advarer eller overvåges denne handling, når beskyttede filer udskrives fra en slutpunktsenhed 

**Kopiér til Udklipsholder** – når gennemtvinges, blokeres, advares eller overvåges data i beskyttet fil, som kopieres til en udklipsholder på en slutpunktsenhed 

**Upload** til skyen – denne handling blokerer, advarer eller revisioner, når beskyttede filer er forhindret i eller tilladelse til at blive overført til skytjenester baseret på listen tillad/ikke-tilladte domæner i globale indstillinger. Når denne handling er indstillet til at advare eller blokere, blokeres andre browsere (defineret på listen over ikke-tilladte browsere under Globale indstillinger) fra at få adgang til filen. 

**Adgang tils af** ikke-tilladte apps – når denne handling gennemtvinges, forhindrer denne handling programmer, der findes på listen over ikke-tilladte apps (som defineret i Globale indstillinger), i at få adgang til beskyttede filer på en slutpunktsenhed. Eksempelscenarier 

## <a name="onboarding-devices-into-device-management"></a>Onboardingenheder i enhedshåndtering

Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres i Microsoft 365 Overholdelse.

Når du vil onboarde enheder, der endnu ikke er blevet onboardet, skal du downloade det relevante script og udrulle det på disse enheder. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Åbn [microsoft-overholdelsescenter på](https://compliance.microsoft.com) **Indstillinger** vælg **Aktivér enhedsovervågning**.

   > [!NOTE]
   > Det tager som regel ca. 60 sekunder, før onboarding af enheder er aktiveret, men det kan tage op til 30 minutter, før du går i gang med Microsoft Support.

2. Åbn siden med indstillinger for Overholdelsescenter, og vælg **Slå overvågning af macOS-enheder til**.

## <a name="next-steps"></a>Næste trin

Det er påkrævet at få Microsoft 365 enheder i gang med overholdelsesløsninger for at modtage DLP-sensortelemetri og håndhæve politikker til forebyggelse af datatab. 

Emne | Beskrivelse
:---|:---
|[Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp Intune (preview)](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)|For macOS-enheder, der administreres via Intune
|[Onboard og offboard macOS-enheder i Overholdelsesløsninger med Intune til Microsoft Defender for Endpoint kunder (preview)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview) |For macOS-enheder, der administreres via Intune, og som har Microsoft Defender for Endpoint (MDE) installeret på dem
|[Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview) | For macOS-enheder, der administreres via JAMF Pro
|[Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF Pro til Microsoft Defender for Endpoint kunder (preview)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)|For macOS-enheder, der administreres via SYLF Pro, og som har Microsoft Defender for Endpoint (MDE) installeret på dem


## <a name="related-topics"></a>Relaterede emner

- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Supportmatrix til DLP-politiktips på tværs af Microsoft-apps](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
