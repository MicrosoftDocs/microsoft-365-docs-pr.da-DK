---
title: Trin 5. Enheds- og appadministration for din Microsoft 365 for virksomhedslejere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Installér den korrekte indstilling for enheds- og appadministration for Microsoft 365 lejere.
ms.openlocfilehash: 09fd96977fbde0f546049d24b1705d27b4c92080
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63592570"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Trin 5. Enheds- og appadministration for din Microsoft 365 for virksomhedslejere

Microsoft 365 til virksomheder indeholder funktioner til administration af enheder og brug af apps på disse enheder i din organisation med administration af mobilenheder (MDM) og administration af mobilprogrammer (MAM). Du kan administrere iOS-, Android-, macOS- Windows-enheder for at beskytte adgangen til organisationens ressourcer, herunder dine data. Du kan f.eks. forhindre mails i at blive sendt til personer uden for organisationen eller isolere virksomhedsdata fra personlige data på din medarbejders personlige enheder.

Her er et eksempel på validering og administration af brugere, deres enheder og deres brug af lokale produktivitetsapps og skyproduktivitetsapps som Microsoft Teams.

![Validering og administration af brugere, enheder og apps.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

For at hjælpe dig med at sikre og beskytte din organisations ressourcer indeholder Microsoft 365 til virksomheder funktioner til at administrere enheder og deres adgang til apps. Der er to muligheder for enhedshåndtering:

- Microsoft Intune, som er en omfattende enheds- og appadministrationsløsning til virksomheder.
- Basic Mobility and Security, som er et undersæt af Intune-tjenester, der følger med alle Microsoft 365-produkter til administration af enheder i organisationen. Du kan finde flere oplysninger [under Egenskaber for grundlæggende mobilitet og sikkerhed](../admin/basic-mobility-security/capabilities.md).

Hvis du har Microsoft 365 E3 eller E5, skal du bruge Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

Du bruger [Microsoft Intune til](/mem/intune/fundamentals/planning-guide) at administrere adgangen til din organisation ved hjælp af MDM eller MAM. MDM er, når brugerne "tilmelder" deres enheder i Intune. Når en enhed er tilmeldt, er den en administreret enhed, og den kan modtage organisationens politikker, regler og indstillinger. Du kan f.eks installere bestemte apps, oprette en adgangskodepolitik, installere en VPN-forbindelse og meget mere.

Brugere med deres egne personlige enheder vil muligvis ikke registrere deres enheder eller administreres af Intune og organisationens politikker. Men du skal stadig beskytte din organisations ressourcer og data. I dette scenarie kan du beskytte dine apps ved hjælp af MAM. Du kan f.eks. bruge en MAM-politik, der kræver, at en bruger angiver en pinkode, når der SharePoint på enheden.

Du kan også se, hvordan du skal administrere personlige enheder og enheder, der ejes af organisationen. Det kan være en god ide at behandle enheder forskelligt, afhængigt af deres anvendelse.

## <a name="identity-and-device-access-configurations"></a>Konfigurationer for identitets- og enhedsadgang

Microsoft leverer et sæt konfigurationer til identitets [- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) for at sikre en sikker og produktiv arbejdsstyrke. Disse konfigurationer omfatter brug af:

- Politikker for betinget adgang til Azure AD
- Microsoft Intune politikker for enhedsoverholdelse og appbeskyttelse
- Sikkerhedspolitikker for Azure AD Identity Protection
- Yderligere politikker for skyapps

Her er et eksempel på anvendelsen af disse indstillinger og politikker til at validere og begrænse brugere, deres enheder og deres brug af lokale produktivitetsapps og skyproduktivitetsapps som Microsoft Teams.

![Konfigurationer af identitets- og enhedsadgang for krav og begrænsninger for brugere, deres enheder og deres brug af apps.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Til enhedsadgang og appadministration skal du bruge konfigurationerne i følgende artikler:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles identitets- og enhedsadgangspolitikker](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Resultater af trin 5

Til enheds- og appadministration for din Microsoft 365-lejer har du fastlagt Intune-indstillingerne og -politikkerne for at validere og begrænse brugere, deres enheder og deres brug af lokale produktivitetsapps og produktivitetsapps i skyen.

Her er et eksempel på en lejer med administration af enheder og apps i Intune med de nye elementer fremhævet.

![Eksempel på en lejer med administration af enheder og apps i Intune.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

I denne illustration har lejeren:

- Enheder, der ejes af organisationer, som er tilmeldt Intune.
- Politikker for Intune-enhed og -app for tilmeldte og personlige enheder.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Løbende vedligeholdelse af enheds- og appadministration

Du kan løbende få brug for at: 

- Administrer tilmelding af enheder.
- Revidere dine indstillinger og politikker for flere apps, enheder og sikkerhedskrav.