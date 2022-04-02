---
title: Slå Microsoft 365 Defender
description: Få mere at vide om, Microsoft 365 Defender du kan aktivere og begynde at integrere din sikkerhedshændelse og -svar.
keywords: kom i gang, Microsoft 365 Defender, Microsoft 365 Defender, M365, sikkerhed, dataplacering, påkrævede tilladelser, berettigelse til licens, siden indstillinger
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2a99dbaf50b582df4203fc9c8e1d04e0a3f6d807
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498634"
---
# <a name="turn-on-microsoft-365-defender"></a>Slå Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) forener processen for svar på hændelser ved at integrere vigtige funktioner på tværs Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps og Microsoft Defender for Identity. Denne samlede oplevelse tilføjer effektive funktioner, du kan få adgang til i Microsoft 365 Defender-portalen.

Microsoft 365 Defender automatisk, når berettigede kunder med de nødvendige tilladelser går til Microsoft 365 Defender-portalen. Læs denne artikel for at forstå forskellige forudsætninger, og hvordan Microsoft 365 Defender er klargjort.

## <a name="check-license-eligibility-and-required-permissions"></a>Kontrollér licensberettigelse og påkrævede tilladelser

En licens til et Microsoft 365-sikkerhedsprodukt giver dig generelt mulighed for at bruge Microsoft 365 Defender uden ekstra licensomkostninger. Vi anbefaler, at du får en Microsoft 365 E5-, E5-, A5- eller A5-sikkerhedslicens eller en gyldig kombination af licenser, der giver adgang til alle understøttede tjenester.

Du kan få detaljerede oplysninger om [licenser ved at læse licenskravene](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Kontrollér din rolle

Du skal være en af følgende roller for at aktivere Microsoft 365 Defender:

- Global Administrator
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Global læser
- Sikkerhedslæser
- Overholdelsesadministrator
- Dataadministrator for overholdelse af regler og standarder
- Programadministrator
- Administrator for skyprogram

[Få vist dine roller i Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Understøttede tjenester

Microsoft 365 Defender samler data fra de forskellige understøttede tjenester, du allerede har installeret. Den behandler og gemmer data centralt for at identificere ny indsigt og gøre centraliseret svararbejdsprocesser mulige. Det gør den uden at påvirke eksisterende installationer, indstillinger eller data, der er knyttet til de integrerede tjenester.

For at få den bedste beskyttelse og optimere Microsoft 365 Defender, anbefaler vi, at du installerer alle relevante understøttede tjenester på dit netværk. Du kan få mere at [vide om installation af understøttede tjenester](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>Onboard til tjenesten
Onboarding til Microsoft 365 Defender er nemt. I **navigationsmenuen** skal du vælge et element, f.eks hændelser & beskeder **, jagt****,** handlingscenter eller **trusselsanalyse** for at starte onboardingprocessen. 

### <a name="data-center-location"></a>Datacenterplacering

Microsoft 365 Defender lagrer og behandler data på den [samme placering, der bruges af Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Hvis du ikke har en Microsoft Defender for Endpoint, vælges der automatisk en ny datacenterplacering baseret på placeringen af aktive Microsoft 365 sikkerhedstjenester. Den valgte datacenterplacering vises på skærmen.

Vælg **Har du brug for hjælp?** Microsoft 365 Defender-portalen for at kontakte Microsoft support om klargøring Microsoft 365 Defender en anden datacenterplacering.

> [!NOTE]
> Tidligere blev dataene Microsoft Defender for Endpoint (EU) automatisk klargjort i DATAcentre i EU, når de er slået til via Microsoft Defender for Cloud. Microsoft 365 Defender bliver automatisk klargjort i det samme EU-datacenter for kunder, der tidligere har klargjort Defender til Slutpunkt på denne måde.

### <a name="confirm-that-the-service-is-on"></a>Bekræft, at tjenesten er tændt

Når tjenesten er klargjort, tilføjes følgende:

- [Håndtering af hændelser](incidents-overview.md)
- [Kø til beskeder](investigate-alerts.md)
- Et handlingscenter til administration [af automatiseret undersøgelse og svar](m365d-autoir.md)
- [Avancerede muligheder for](advanced-hunting-overview.md) jagt
- Trusselsanalyse

:::image type="content" source="../../media/overview-incident.png" alt-text="Navigationsruden i Microsoft 365 Defender med Microsoft 365 Defender funktioner" lightbox="../../media/overview-incident.png":::
*Microsoft 365 Defender-portalen med hændelsesstyring og andre funktioner*

### <a name="getting-microsoft-defender-for-identity-data"></a>Hente Microsoft Defender for Identity data 
For at aktivere integration Microsoft Defender for Cloud Apps, skal du logge på siden Microsoft Defender for Cloud Apps én gang.

## <a name="get-assistance"></a>Få hjælp

Hvis du vil have svar på de oftest stillede spørgsmål om aktivering af Microsoft 365 Defender, kan du [læse Ofte stillede spørgsmål](m365d-enable-faq.md).

Microsofts supportmedarbejdere kan hjælpe med at klargøre eller fjerne tjenesten og relaterede ressourcer på din lejer. Hvis du har brug for hjælp, **skal du vælge Har** du brug for hjælp? Microsoft 365 Defender-portalen. Når du kontakter support, skal du nævne Microsoft 365 Defender.

## <a name="related-topics"></a>Relaterede emner

- [Ofte stillede spørgsmål](m365d-enable-faq.md)
- [Licenskrav og andre forudsætninger](prerequisites.md)
- [Installér understøttede tjenester](deploy-supported-services.md)
- [Microsoft 365 Defender oversigt](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint oversigt](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender for Office 365 oversigt](../office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps oversigt](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender for Identity oversigt](/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender for Endpoint datalager](../defender-endpoint/data-storage-privacy.md)
