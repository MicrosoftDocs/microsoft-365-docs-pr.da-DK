---
title: Trin 5. Enheds- og appadministration for dine Microsoft 365 til virksomhedslejere
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
description: Udrul den korrekte indstilling for administration af enheder og apps for dine Microsoft 365 lejere.
ms.openlocfilehash: 3999d30aaeee9ebfc2af90b0aeeeaea1b46986fb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419456"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Trin 5. Enheds- og appadministration for dine Microsoft 365 til virksomhedslejere

Microsoft 365 til virksomheder indeholder funktioner, der hjælper med at administrere enheder og brugen af apps på disse enheder i din organisation med ADMINISTRATION af mobilenheder (MDM) og MAM (Mobile Application Management). Du kan administrere iOS-, Android-, macOS- og Windows-enheder for at beskytte adgangen til organisationens ressourcer, herunder dine data. Du kan f.eks. forhindre, at mails sendes til personer uden for din organisation eller isolere organisationsdata fra personlige data på din arbejders personlige enheder.

Her er et eksempel på validering og administration af brugere, deres enheder og deres brug af lokale produktivitetsapps og cloudproduktivitetsapps som Microsoft Teams.

![Validering og administration af brugere, enheder og apps.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

For at hjælpe dig med at sikre og beskytte organisationens ressourcer indeholder Microsoft 365 til virksomheder funktioner, der kan hjælpe med at administrere enheder og deres adgang til apps. Der er to muligheder for enhedshåndtering:

- Microsoft Intune, som er en omfattende løsning til administration af enheder og apps til virksomheder.
- Basic Mobility and Security, som er en delmængde af Intune tjenester, der er inkluderet i alle Microsoft 365 produkter til administration af enheder i din organisation. Du kan få flere oplysninger under [Funktioner i Grundlæggende mobilitet og sikkerhed](../admin/basic-mobility-security/capabilities.md).

Hvis du har Microsoft 365 E3 eller E5, skal du bruge Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

Du kan bruge [Microsoft Intune](/mem/intune/fundamentals/planning-guide) til at administrere adgang til din organisation ved hjælp af MDM eller MAM. MDM er, når brugerne "tilmelder" deres enheder i Intune. Når en enhed er tilmeldt, er det en administreret enhed og kan modtage organisationens politikker, regler og indstillinger. Du kan f.eks. installere bestemte apps, oprette en adgangskodepolitik, installere en VPN-forbindelse og meget mere.

Brugere med deres egne personlige enheder vil muligvis ikke tilmelde deres enheder eller administreres af Intune og organisationens politikker. Men du skal stadig beskytte organisationens ressourcer og data. I dette scenarie kan du beskytte dine apps ved hjælp af MAM. Du kan f.eks. bruge en MAM-politik, der kræver, at en bruger angiver en pinkode, når der opnås adgang til SharePoint på enheden.

Du bestemmer også, hvordan du skal administrere personlige enheder og enheder, der ejes af organisationen. Det kan være en god idé at behandle enheder forskelligt, afhængigt af deres anvendelse.

## <a name="identity-and-device-access-configurations"></a>Konfigurationer af identitets- og enhedsadgang

Microsoft leverer et sæt konfigurationer til [identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) for at sikre en sikker og produktiv arbejdsstyrke. Disse konfigurationer omfatter brugen af:

- Azure AD politikker for betinget adgang
- Microsoft Intune politikker for enhedsoverholdelse og appbeskyttelse
- Azure AD politikker for brugerrisiko for identitetsbeskyttelse
- Yderligere politikker for cloudapps

Her er et eksempel på anvendelsen af disse indstillinger og politikker til at validere og begrænse brugere, deres enheder og deres brug af lokale apps og cloudproduktivitetsapps som Microsoft Teams.

![Konfigurationer af identitets- og enhedsadgang for krav og begrænsninger for brugere, deres enheder og deres brug af apps.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Brug konfigurationerne i disse artikler til enhedsadgang og appadministration:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Resultater af trin 5

I forbindelse med administration af enheder og apps for din Microsoft 365 lejer har du bestemt de Intune indstillinger og politikker for at validere og begrænse brugere, deres enheder og deres brug af lokale produktivitetsapps og cloudproduktivitetsapps.

Her er et eksempel på en lejer med Intune enheds- og appadministration med de nye elementer fremhævet.

![Eksempel på en lejer med Intune administration af enheder og apps.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

I denne illustration har lejeren:

- Enheder, der ejes af organisationen, og som er tilmeldt Intune.
- Intune politikker for enheder og apps for tilmeldte og personlige enheder.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Løbende vedligeholdelse af administration af enheder og apps

Du skal muligvis løbende: 

- Administrer tilmelding af enheden.
- Rediger dine indstillinger og politikker for yderligere apps, enheder og sikkerhedskrav.
