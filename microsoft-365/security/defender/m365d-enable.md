---
title: Slå Microsoft 365 Defender til
description: Få mere at vide om, hvordan du aktiverer Microsoft 365 Defender og begynder at integrere din sikkerhedshændelse og dit svar.
keywords: kom i gang, aktivér Microsoft 365 Defender, Microsoft 365 Defender, M365, sikkerhed, dataplacering, påkrævede tilladelser, licensberettigelse, indstillingsside
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
ms.collection:
- M365-security-compliance
- m365solution-getstarted
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0fa1a47bb5a4a09c22649866bb6c5c6039dc2850
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66895025"
---
# <a name="turn-on-microsoft-365-defender"></a>Slå Microsoft 365 Defender til

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) samler din proces for svar på hændelser ved at integrere vigtige funktioner på tværs af Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps og Microsoft Defender for Identity. Denne samlede oplevelse tilføjer effektive funktioner, du kan få adgang til på Microsoft 365 Defender-portalen.

Microsoft 365 Defender aktiveres automatisk, når berettigede kunder med de nødvendige tilladelser besøger Microsoft 365 Defender Portal. Læs denne artikel for at forstå forskellige forudsætninger, og hvordan Microsoft 365 Defender klargøres.

## <a name="check-license-eligibility-and-required-permissions"></a>Kontrollér licensberettigelse og påkrævede tilladelser

En licens til et Microsoft 365-sikkerhedsprodukt giver dig generelt ret til at bruge Microsoft 365 Defender uden yderligere licensomkostninger. Vi anbefaler, at du får en Microsoft 365 E5-, E5 Security-, A5- eller A5-sikkerhedslicens eller en gyldig kombination af licenser, der giver adgang til alle understøttede tjenester.

Du kan finde detaljerede licensoplysninger, ved at [læse licenskravene](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Kontrollér din rolle

Du skal have en af følgende roller for at aktivere Microsoft 365 Defender:

- Global administrator
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Global læser
- Sikkerhedslæser
- Administrator for overholdelse af angivne standarder
- Administrator for overholdelsesdata
- Programadministrator
- Administrator for skyapp

[Få vist dine roller i Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Understøttede tjenester

Microsoft 365 Defender samler data fra de forskellige understøttede tjenester, som du allerede har installeret. Den behandler og gemmer data centralt for at identificere ny indsigt og gøre centraliserede svararbejdsprocesser mulige. Det gør den uden at påvirke eksisterende udrulninger, indstillinger eller data, der er knyttet til de integrerede tjenester.

For at få den bedste beskyttelse og optimere Microsoft 365 Defender anbefaler vi, at du installerer alle relevante understøttede tjenester på dit netværk. Du kan få flere oplysninger ved at [læse om installation af understøttede tjenester](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>Onboard til tjenesten
Det er nemt at onboarde Microsoft 365 Defender. Vælg et element i navigationsmenuen, f.eks. **Hændelser og underretninger**, **Jagt**, **Handlingscenter** eller **Trusselsanalyse** for at starte onboardingprocessen. 

### <a name="data-center-location"></a>Placering af datacenter

Microsoft 365 Defender gemmer og behandler data på [samme placering, der bruges af Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Hvis du ikke har Microsoft Defender for Endpoint, vælges der automatisk en ny datacenterplacering baseret på placeringen af aktive Microsoft 365-sikkerhedstjenester. Den valgte datacenterplacering vises på skærmen.

Vælg **Har du brug for hjælp?** på Microsoft 365 Defender-portalen for at kontakte Microsoft Support om klargøring af Microsoft 365 Defender på en anden placering i datacenteret.

> [!NOTE]
> Tidligere blev Microsoft Defender for Endpoint automatisk klargjort i EU-datacentre, når det var aktiveret via Microsoft Defender for Cloud. Microsoft 365 Defender klargøres automatisk i det samme EU-datacenter for kunder, der tidligere har klargjort Defender for Endpoint på denne måde.

### <a name="confirm-that-the-service-is-on"></a>Bekræft, at tjenesten er slået til

Når tjenesten er klargjort, tilføjer den:

- [Administration af hændelser](incidents-overview.md)
- [Beskedkøer](investigate-alerts.md)
- Et handlingscenter til administration af [automatiserede undersøgelser og svar](m365d-autoir.md)
- Funktioner til [Avanceret jagt på trusler](advanced-hunting-overview.md)
- Trusselsanalyse

:::image type="content" source="../../media/overview-incident.png" alt-text="Navigationsruden på Microsoft 365 Defender-portalen med Microsoft 365 Defender-funktioner" lightbox="../../media/overview-incident.png":::
*Microsoft 365 Defender-portal med administration af hændelser og andre funktioner*

### <a name="getting-microsoft-defender-for-identity-data"></a>Henter Microsoft Defender for Identity-data 
Hvis du vil aktivere integrationen med Microsoft Defender for Cloud Apps, skal du logge på Microsoft Defender for Cloud Apps mindst én gang.

## <a name="get-assistance"></a>Få hjælp

Hvis du vil have svar på de oftest stillede spørgsmål om at aktivere Microsoft 365 Defender, skal du [læse ofte stillede spørgsmål](m365d-enable-faq.md).

Microsofts supportmedarbejdere kan hjælpe med at klargøre eller fjerne tjenesten og relaterede ressourcer på din lejer. Vælg **Har du brug for hjælp?** på Microsoft 365 Defender-portalen. Når du kontakter support, skal du omtale Microsoft 365 Defender.

## <a name="related-topics"></a>Relaterede emner

- [Ofte stillede spørgsmål](m365d-enable-faq.md)
- [Licenskrav og andre forudsætninger](prerequisites.md)
- [Udrul understøttede tjenester](deploy-supported-services.md)
- [Oversigt over Microsoft 365 Defender-portalen](microsoft-365-defender.md)
- [Oversigt over Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md)
- [Oversigt over Defender for Office 365](../office-365-security/defender-for-office-365.md)
- [Oversigt over Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Oversigt over Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender for Endpoint-datalager](../defender-endpoint/data-storage-privacy.md)
