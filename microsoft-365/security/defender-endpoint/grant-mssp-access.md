---
title: Giv adgang til administreret serviceudbyder (MSSP)
description: Tag de nødvendige trin for at konfigurere MSSP-integration med Microsoft Defender for Endpoint
keywords: administreret sikkerheds serviceudbyder, mssp, konfigurer, integration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cb92b67b3f19c578d12eb9673d2f80d5fadd131f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591867"
---
# <a name="grant-managed-security-service-provider-mssp-access-preview"></a>Tildele administreret serviceudbyder sikkerhedsadgang (MSSP) (preview)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Hvis du vil implementere en løsning med stedfortræderadgang for flere lejere, skal du gøre følgende:

1. [Aktivér rollebaseret adgangskontrol](rbac.md) i Defender til slutpunkt, og opret forbindelse til Active Directory-grupper (AD).

2. Konfigurer [adgangspakker til styring](/azure/active-directory/governance/identity-governance-overview) af adgang til anmodning om og klargøring af adgang.

3. Administrer adgangsanmodninger og - [revisioner i Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint"></a>Aktivér rollebaserede adgangskontrolelementer i Microsoft Defender til slutpunkt

1. **Opret adgangsgrupper for MSSP-ressourcer i AAD: Grupper**

    Disse grupper sammenkædes med de roller, du opretter i Defender for Slutpunkt. Det gør du ved at oprette tre grupper i kundens AD-lejer. I vores eksempel på en fremgangsmåde opretter vi følgende grupper:

    - Niveau 1-analytiker
    - Niveau 2-analytiker
    - GODKENDERE fra MSSP-analytikere

2. Opret Defender til slutpunktsroller for relevante adgangsniveauer i Customer Defender for Endpoint.

    For at aktivere RBAC i kundeportalen til Microsoft 365 Defender skal du få adgang til **Indstillinger >-tilladelser >-roller** og "Aktivér roller" fra en brugerkonto med globale administrator- eller sikkerhedsadministratorrettigheder.

    ![Billede af MSSP-adgang.](images/mssp-access.png)

    Opret derefter RBAC-roller, så de opfylder behovet for MSSP SOC-niveau. Sammenkæd disse roller med de oprettede brugergrupper via "Tildelte brugergrupper".

    To mulige roller:

    - **Niveau 1-analytikere**

      Udfør alle handlinger med undtagelse af direkte svar og administrer sikkerhedsindstillinger.

    - **Niveau 2-analytikere**

      Niveau 1-funktioner med tilføjelsen til [live-svar](live-response.md)

    Få mere at vide under [Brug rollebaseret adgangskontrol](rbac.md).

## <a name="configure-governance-access-packages"></a>Konfigurere adgangspakker til styring

1. **Tilføj MSSP som forbundet organisation i AAD: Styring af identitet**

    Hvis du tilføjer MSSP som en forbundet organisation, giver det MSSP mulighed for at anmode om og få adgangs klargjort.

    Det gør du ved i kundens AD-lejer at få adgang til identitetsstyring: Forbundet organisation. Tilføj en ny organisation, og søg efter din MSSP-analytikerlejer via lejer-id eller domæne. Vi anbefaler, at du opretter en separat AD-lejer til dine MSSP-analytikere.

2. **Opret et ressourcekatalog i Kundekatalog AAD: Styring af identitet**

    Ressourcekataloger er en logisk samling af adgangspakker, der er oprettet i kundens AD-lejer.

    Det gør du ved i kundens AD-lejer at få adgang til styring af identitet: kataloger og tilføje **Nyt katalog**. I vores eksempel kalder vi det **MSSP Accesses**.

    ![Billede af nyt katalog.](images/goverance-catalog.png)

    Få mere at vide under [Opret et katalog med ressourcer](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Opret adgangspakker til MSSP-ressourcer AAD: Styring af identitet**

    Access-pakker er en samling af rettigheder og adgange, som en anmoder vil få tildelt efter godkendelse.

    Det gør du ved i kundens AD-lejer at få adgang til identitetsstyring: Adgangspakker og tilføje **ny adgangspakke**. Opret en adgangspakke til MSSP-godkendere og hvert analytikerniveau. Følgende niveau 1-analytikerkonfiguration opretter f.eks. en adgangspakke, som:

    - Kræver, at du er medlem af **AD-gruppens MSSP-analytikergodkendere** for at godkende nye anmodninger
    - Har årlige adgangsvurderinger, hvor SOC-analytikere kan anmode om en adgangsudvidelse
    - Brugere i MSSP SOC-lejeren kan kun anmode om det
    - Access udløber automatisk efter 365 dage

    > [!div class="mx-imgBorder"]
    > ![Billede af ny adgangspakke.](images/new-access-package.png)

    Få mere at vide under [Opret en ny adgangspakke](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Giv adgangsanmodningslink til MSSP-ressourcer fra AAD: Styring af identitet**

    Linket til min Access-portal bruges af MSSP SOC-analytikere til at anmode om adgang via de adgangspakker, der oprettes. Linket er robust, hvilket betyder, at det samme link kan bruges over tid til nye analytikere. Analytikeranmodningen går ind i en kø til godkendelse af **MSSP-analytikergodkenderne**.

    > [!div class="mx-imgBorder"]
    > ![Billede af egenskaber for adgang.](images/access-properties.png)

    Linket er placeret på oversigtssiden for hver adgangspakke.

## <a name="manage-access"></a>Administrer adgang

1. Gennemse og godkend adgangsanmodninger i Kunde og/eller MSSP myaccess.

    Anmodninger om adgang administreres i kunden My Access af medlemmer af gruppen MSSP-analytikergodkendere.

    Det gør du ved at få adgang til kundens myaccess ved hjælp af: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Eksempel: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Godkend eller afvis anmodninger **i sektionen** Godkendelser i brugergrænsefladen.

    På dette tidspunkt er analytikeradgang blevet klargjort, og hver enkelt analytiker bør kunne få adgang til kundens Microsoft 365 Defender portal:`https://security.microsoft.com/?tid=<CustomerTenantId>`

## <a name="related-topics"></a>Relaterede emner

- [Få adgang til MSSP-kundeportalen](access-mssp-portal.md)
- [Konfigurere beskeder](configure-mssp-notifications.md)
- [Hent beskeder fra kundelejeren](fetch-alerts-mssp.md)
