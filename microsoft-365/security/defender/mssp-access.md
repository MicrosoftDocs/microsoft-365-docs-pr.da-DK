---
title: Angiv mssp-adgang (managed security service provider)
description: Få mere at vide om ændringer fra Microsoft Defender Security Center til Microsoft 365 Defender-portalen
keywords: Introduktion til Microsoft 365 Defender-portalen, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, enkelt glasrude, konvergeret portal, sikkerhedsportal, defender security portal
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
ms.openlocfilehash: 4eccd4d6140810bae4caef5e194082aeb3054217
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102366"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Angiv mssp-adgang (managed security service provider) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis du vil implementere en delegeret adgangsløsning med flere lejere, skal du benytte følgende fremgangsmåde:

1. Aktivér [rollebaseret adgangskontrol](/microsoft-365/security/defender-endpoint/rbac) for Defender for Endpoint via Microsoft 365 Defender-portalen, og opret forbindelse til Azure Active Directory (Azure AD)-grupper.

2. Konfigurer [rettighedsstyring for eksterne brugere](/azure/active-directory/governance/entitlement-management-external-users) i Azure AD Identitetsstyring for at aktivere adgangsanmodninger og klargøring.

3. Administrer adgangsanmodninger og overvågninger i [Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Aktivér rollebaserede adgangskontrolelementer i Microsoft Defender for Endpoint på Microsoft 365 Defender portal

1. **Opret adgangsgrupper for MSSP-ressourcer i Customer AAD: Grupper**

    Disse grupper knyttes til de roller, du opretter i Defender for Endpoint på Microsoft 365 Defender portal. Det gør du ved at oprette tre grupper i kundens AD-lejer. I vores eksempeltilgang opretter vi følgende grupper:

    - Niveau 1-analytiker
    - Niveau 2-analytiker
    - MSSP-analytikere  

2. Opret Defender for Endpoint-roller for relevante adgangsniveauer i Customer Defender for Endpoint i Microsoft 365 Defender portalroller og -grupper.

    Hvis du vil aktivere RBAC i kundeportalen Microsoft 365 Defender, skal du få adgang til **tilladelser > slutpunktsroller & grupper > roller** med en brugerkonto med rettigheder som global administrator eller sikkerhedsadministrator.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Oplysningerne om MSSP-adgangen på Microsoft 365 Defender-portalen" lightbox="../../media/mssp-access.png":::

    Opret derefter RBAC-roller for at opfylde MSSP SOC-niveaubehov. Sammensæt disse roller med de oprettede brugergrupper via "Tildelte brugergrupper".

    To mulige roller:

    - **Niveau 1-analytikere** <br>
      Udfør alle handlinger undtagen direkte svar og administrer sikkerhedsindstillinger.

    - **Niveau 2-analytikere** <br>
      Niveau 1-funktioner med tilføjelsen til [live-svar](/microsoft-365/security/defender-endpoint/live-response).

    Du kan få flere oplysninger under [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](/microsoft-365/security/defender-endpoint/rbac).

## <a name="configure-governance-access-packages"></a>Konfigurer adgangspakker til styring

1. **Tilføj MSSP som forbundet organisation i Customer AAD: Identity Governance**

    Tilføjelse af MSSP'en som en forbundet organisation gør det muligt for MSSP at anmode om og få klargjort adgang. 

    Det gør du ved at få adgang til Identitetsstyring i kundens AD-lejer: Forbundet organisation. Tilføj en ny organisation, og søg efter din MSSP-analytikerlejer via lejer-id eller domæne. Vi anbefaler, at du opretter en separat AD-lejer til dine MSSP-analytikere.

2. **Opret et ressourcekatalog i Kunde-AAD: Identitetsstyring**

    Ressourcekataloger er en logisk samling af adgangspakker, der er oprettet i kundens AD-lejer.

    Det gør du ved at få adgang til Identitetsstyring i kundens AD-lejer: Kataloger og tilføje **Nyt katalog**. I vores eksempel kalder vi det **MSSP Accesses**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Et nyt katalog på Microsoft 365 Defender-portalen" lightbox="../../media/goverance-catalog.png":::


    Du kan finde flere oplysninger under [Opret et katalog over ressourcer](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Opret adgangspakker til MSSP-ressourcer Customer AAD: Identity Governance**

    Adgangspakker er den samling af rettigheder og adgange, som en anmoder tildeles ved godkendelse. 

    Det gør du ved at få adgang til identitetsstyring i kundens AD-lejer: Adgangspakker og tilføje **ny adgangspakke**. Opret en adgangspakke til MSSP-godkenderne og hvert analytikerniveau. Følgende niveau 1-analytikerkonfiguration opretter f.eks. en adgangspakke, der:

    - Kræver, at et medlem af AD-gruppen **MSSP-analytikergodkendere godkendere** for at godkende nye anmodninger
    - Har årlige adgangsgennemgange, hvor SOC-analytikerne kan anmode om en adgangsudvidelse
    - Brugere i MSSP SOC-lejeren kan kun anmode om det
    - Access udløber automatisk efter 365 dage

    :::image type="content" source="../../media/new-access-package.png" alt-text="Oplysningerne om en ny adgangspakke på Microsoft 365 Defender-portalen" lightbox="../../media/new-access-package.png":::

    Du kan få flere oplysninger under [Opret en ny adgangspakke](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Angiv et link til anmodning om adgang til MSSP-ressourcer fra Customer AAD: Identity Governance**

    Linket Til My Access-portalen bruges af MSSP SOC-analytikere til at anmode om adgang via de oprettede adgangspakker. Linket er holdbart, hvilket betyder, at det samme link kan bruges over tid for nye analytikere. Analytikeranmodningen sættes i kø til godkendelse af **MSSP-analytikergodkendere**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Adgangsegenskaberne på Microsoft 365 Defender-portalen" lightbox="../../media/access-properties.png":::

    Linket er placeret på oversigtssiden for hver adgangspakke.

## <a name="manage-access"></a>Administrer adgang

1. Gennemse og godkend adgangsanmodninger i Kunde og/eller MSSP myaccess.

    Anmodninger om adgang administreres i kunden My Access af medlemmer af gruppen MSSP Analyst Approvers.

    Det gør du ved at få adgang til kundens myaccess ved hjælp af: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Eksempel: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Godkend eller afvis anmodninger i afsnittet **Godkendelser** i brugergrænsefladen.

     På dette tidspunkt er der klargjort analytikeradgang, og hver analytiker bør kunne få adgang til kundens Microsoft 365 Defender portal:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` med de tilladelser og roller, de blev tildelt.
