---
title: Krav til Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) skal du få en liste over krav til brug af Microsoft 365 Lighthouse.
ms.openlocfilehash: 79084edf573f90ee4d977528c45fdfbfcedff36f
ms.sourcegitcommit: 852075d8d8a4ca052f69e854396d1565ef713500
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65692701"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Krav til Microsoft 365 Lighthouse

Microsoft 365 Lighthouse er en administrationsportal, der hjælper MSP'er (Managed Service Providers) med at sikre og administrere enheder, data og brugere i stor skala til SMB-kunder (Managed Service Providers).

MSP'er skal være tilmeldt programmet Cloud Solution Provider (CSP) som indirect reseller eller Direct Bill-partner for at bruge Lighthouse.

Desuden skal hver MSP-kundelejer kvalificere sig til Lighthouse ved at opfylde følgende krav:

- Der skal være konfigureret uddelegeret adgang for MSP'en (Managed Service Provider) for at kunne administrere kundelejer*
- Der skal være mindst én Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Business eller Microsoft Defender til virksomheder licens
- Der må ikke være mere end 1000 licenserede brugere

*Der kræves delegerede Administration rettigheder (DAP) for at onboarde kunder til Lighthouse. Vi anbefaler også, at du opretter GDAP (Granular Delegated Administration Privileges) med dine kunder for at muliggøre mere sikker delegeret adgang. Mens DAP og GDAP eksisterer, har GDAP forrang for kunder, hvor begge modeller er på plads. Snart vil kunder med kun GDAP (og ingen DAP) kunne onboarde til Lighthouse.

## <a name="requirements-for-enabling-device-management"></a>Krav til aktivering af enhedshåndtering

Hvis du vil have vist kundelejerenheder på siderne til enhedshåndtering, skal en MSP:

- Tilmeld alle kundeenheder i Microsoft Endpoint Manager (MEM). Du kan få flere oplysninger under [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).
- Tildel overholdelsespolitikker til alle kundeenheder. Du kan få flere oplysninger under [Opret en politik for overholdelse af regler og standarder i Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Krav til aktivering af brugeradministration

Kundens data skal have licens til Azure Active Directory Premium P1 eller nyere, før kundedata vises i rapporter på sider til brugeradministration, herunder risikoberigede brugere, multifaktorgodkendelse og nulstilling af adgangskode. Azure AD Premium P1 er inkluderet i Microsoft 365 Business Premium og Microsoft 365 E3. Azure AD Premium P2 er inkluderet i Microsoft 365 E5.

## <a name="requirements-for-enabling-threat-management"></a>Krav til aktivering af trusselsstyring

Hvis du vil have vist kundelejerenheder og trusler på siderne til trusselsstyring, skal du tilmelde alle kunders lejerenheder i Microsoft Endpoint Manager (MEM) og beskytte dem ved at køre Microsoft Defender Antivirus.

Du kan få flere oplysninger under [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).

Microsoft Defender Antivirus er en del af Windows operativsystem og er som standard aktiveret på enheder, der kører Windows 10.

> [!NOTE]
> Hvis du bruger en antivirusløsning, der ikke er fra Microsoft, og ikke Microsoft Defender Antivirus, deaktiveres Microsoft Defender Antivirus automatisk. Når du fjerner den antivirusløsning, der ikke er Microsoft, aktiveres Microsoft Defender Antivirus automatisk for at beskytte dine Windows enheder mod trusler.

## <a name="related-content"></a>Relateret indhold

[Konfigurer sikkerhed Microsoft 365 Lighthouse Portal](m365-lighthouse-configure-portal-security.md) (artikel)\
[Oversigt over siden Med enhedsoverholdelse i Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (artikel)\
[Oversigt over siden Brugere i Microsoft 365 Fyrtårn](m365-lighthouse-users-page-overview.md) (artikel)\
[Oversigt over siden Threat management i Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)
