---
title: Angiv administreret serviceudbyder sikkerhedsadgang (MSSP)
description: Få mere at vide om ændringer Microsoft Defender Security Center til Microsoft 365 Defender portalen
keywords: Introduktion til Microsoft 365 Defender-portalen, Microsoft Defender for Office 365, Microsoft Defender til Slutpunkt, MDO, MDE, enkelt rude med glas, konvergeret portal, sikkerhedsportal, defender security portal
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
manager: dansimp
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 641636528d35c148ceaa41827721e841dfafd4ec
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593520"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Angiv administreret serviceudbyder sikkerhedsadgang (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis du vil implementere en løsning med stedfortræderadgang for flere lejere, skal du gøre følgende:

1. [Aktivér rollebaseret adgangskontrol](/windows/security/threat-protection/microsoft-defender-atp/rbac) for Defender til slutpunkt via Microsoft 365 Defender, og opret forbindelse til Azure Active Directory (Azure AD).

2. Konfigurer [adgangspakker til styring](/azure/active-directory/governance/identity-governance-overview) af adgang til anmodning om og klargøring af adgang.

3. Administrer adgangsanmodninger og - [revisioner i Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Aktivér rollebaserede adgangskontrolelementer i Microsoft Defender til slutpunkt i Microsoft 365 Defender portal

1. **Opret adgangsgrupper for MSSP-ressourcer i AAD: Grupper**

    Disse grupper sammenkædes med de roller, du opretter i Defender til slutpunkt i Microsoft 365 Defender portal. Det gør du ved at oprette tre grupper i kundens AD-lejer. I vores eksempel på en fremgangsmåde opretter vi følgende grupper:

    - Niveau 1-analytiker
    - Niveau 2-analytiker
    - GODKENDERE fra MSSP-analytikere  

2. Opret Defender til slutpunktsroller for relevante adgangsniveauer i Customer Defender for Endpoint i Microsoft 365 Defender-portalroller og -grupper.

    Hvis du vil aktivere RBAC i kundeportalen til Microsoft 365 Defender, skal du åbne **tilladelsesroller > slutpunkter & grupper >** Roller med en brugerkonto med globale administrator- eller sikkerhedsadministratorrettigheder.

    ![Billede af MSSP-adgang.](../../media/mssp-access.png)

    Opret derefter RBAC-roller, så de opfylder behovet for MSSP SOC-niveau. Sammenkæd disse roller med de oprettede brugergrupper via "Tildelte brugergrupper".

    To mulige roller:

    - **Niveau 1-analytikere** <br>
      Udfør alle handlinger med undtagelse af direkte svar og administrer sikkerhedsindstillinger.

    - **Niveau 2-analytikere** <br>
      Niveau 1-funktioner med tilføjelsen til [live-svar](/windows/security/threat-protection/microsoft-defender-atp/live-response)

    Få mere at vide under [Brug rollebaseret adgangskontrol](/windows/security/threat-protection/microsoft-defender-atp/rbac).

## <a name="configure-governance-access-packages"></a>Konfigurere adgangspakker til styring

1. **Tilføj MSSP som forbundet organisation i AAD: Styring af identitet**

    Hvis du tilføjer MSSP som en forbundet organisation, giver det MSSP mulighed for at anmode om og få adgangs klargjort. 

    Det gør du ved i kundens AD-lejer at få adgang til identitetsstyring: Forbundet organisation. Tilføj en ny organisation, og søg efter din MSSP-analytikerlejer via lejer-id eller domæne. Vi anbefaler, at du opretter en separat AD-lejer til dine MSSP-analytikere.

2. **Opret et ressourcekatalog i Kundekatalog AAD: Styring af identitet**

    Ressourcekataloger er en logisk samling af adgangspakker, der er oprettet i kundens AD-lejer.

    Det gør du ved i kundens AD-lejer at få adgang til styring af identitet: kataloger og tilføje **Nyt katalog**. I vores eksempel kalder vi det **MSSP Accesses**.

    ![Billede af nyt katalog.](../../media/goverance-catalog.png)

    Få mere at vide under [Opret et katalog med ressourcer](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Opret adgangspakker til MSSP-ressourcer AAD: Styring af identitet**

    Access-pakker er en samling af rettigheder og adgange, som en anmoder vil få tildelt efter godkendelse. 

    Det gør du ved i kundens AD-lejer at få adgang til identitetsstyring: Adgangspakker og tilføje **ny adgangspakke**. Opret en adgangspakke til MSSP-godkendere og hvert analytikerniveau. Følgende niveau 1-analytikerkonfiguration opretter f.eks. en adgangspakke, som:

    - Kræver, at du er medlem af **AD-gruppens MSSP-analytikergodkendere** for at godkende nye anmodninger
    - Har årlige adgangsvurderinger, hvor SOC-analytikere kan anmode om en adgangsudvidelse
    - Brugere i MSSP SOC-lejeren kan kun anmode om det
    - Access udløber automatisk efter 365 dage

    ![Billede af ny adgangspakke.](../../media/new-access-package.png)

    Få mere at vide under [Opret en ny adgangspakke](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Giv adgangsanmodningslink til MSSP-ressourcer fra AAD: Styring af identitet**

    Linket til min Access-portal bruges af MSSP SOC-analytikere til at anmode om adgang via de adgangspakker, der oprettes. Linket er robust, hvilket betyder, at det samme link kan bruges over tid til nye analytikere. Analytikeranmodningen går ind i en kø til godkendelse af **MSSP-analytikergodkenderne**.

    ![Billede af egenskaber for adgang.](../../media/access-properties.png)

    Linket er placeret på oversigtssiden for hver adgangspakke.

## <a name="manage-access"></a>Administrer adgang

1. Gennemse og godkend adgangsanmodninger i Kunde og/eller MSSP myaccess.

    Anmodninger om adgang administreres i kunden My Access af medlemmer af gruppen MSSP-analytikergodkendere.

    Det gør du ved at få adgang til kundens myaccess ved hjælp af: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Eksempel: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Godkend eller afvis anmodninger **i sektionen** Godkendelser i brugergrænsefladen.

     På dette tidspunkt er analytikeradgang blevet klargjort, og hver enkelt analytiker bør kunne få adgang til kundens Microsoft 365 Defender portal:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` med de tilladelser og roller, de blev tildelt.

> [!IMPORTANT]
> Delegeret adgang til Microsoft Defender til slutpunkt i Microsoft 365 Defender-portalen giver i øjeblikket adgang til en enkelt lejer pr. browservindue.
