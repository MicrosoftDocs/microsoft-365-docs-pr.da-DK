---
title: Kom i gang med dashboardet DLP-beskeder
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Kom i gang med at definere og administrere beskeder for politikker til forebyggelse af datatab.
ms.openlocfilehash: de980fadbc6b6091a0257c032dacab4220704f62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625451"
---
# <a name="get-started-with-the-data-loss-prevention-alerts-dashboard"></a>Kom i gang med dashboardet til forebyggelse af datatab

Microsoft Purview Forebyggelse af datatab politikker (DLP) kan udføre beskyttende handlinger for at forhindre utilsigtet deling af følsomme elementer. Når der udføres en handling på et følsomt element, kan du få besked ved at konfigurere beskeder for DLP. I denne artikel kan du se, hvordan du definerer omfattende beskedpolitikker, der er knyttet til politikker til forebyggelse af datatab (DLP). Du kan se, hvordan du bruger [dashboardet til administration af DLP-beskeder](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> til at få vist beskeder, hændelser og tilknyttede metadata for DLP-politikovertrædelser.

Hvis du ikke kender DLP-beskeder, skal du gennemse [Få mere at vide om dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Før du begynder

Før du begynder, skal du sørge for, at du har de nødvendige forudsætninger:

-   Licenser til dashboardet til administration af DLP-beskeder
-   Licenser til konfigurationsindstillinger for beskeder
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licenser til dashboardet til administration af DLP-beskeder

Alle berettigede lejere til DLP kan få adgang til dashboardet til administration af DLP-beskeder. For at komme i gang skal du være berettiget til Microsoft Purview DLP til Exchange Online, SharePoint Online og OneDrive for Business. Du kan få flere oplysninger om licenskravene til DLP under [Hvilke licenser giver en bruger ret til at drage fordel af tjenesten?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md) , som er berettiget til [Teams DLP](dlp-microsoft-teams.md) , får vist deres DLP-politikbeskeder for slutpunkter og Teams DLP-politikbeskeder på dashboardet til administration af DLP-beskeder.

**Indholdseksempelfunktionen** er kun tilgængelig for disse licenser:

- Microsoft 365 (E5)
- Office 365 (E5)
- Tilføj avanceret overholdelse (E5)
- Microsoft 365 E5/A5 Information Protection og styring
- overholdelse af Microsoft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>Licenser til konfigurationsindstillinger for beskeder

**Konfiguration af en enkelt hændelsesbesked**: Organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, kan kun oprette beskedpolitikker, hvis en besked udløses, hver gang der forekommer en aktivitet.

**Samlet konfiguration af beskeder**: Hvis du vil konfigurere samlede politikker for beskeder baseret på en tærskel, skal du bruge en af disse licenskonfigurationer:

- Et E5- eller G5-abonnement
- Et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Licens til Microsoft 365 eDiscovery- og overvågningstilføjelsesprogram

### <a name="roles"></a>Roller

Hvis du vil have vist dashboardet til administration af DLP-beskeder eller redigere indstillingerne for konfiguration af beskeder i en DLP-politik, skal du være medlem af en af disse rollegrupper:

- Administrator for overholdelse af angivne standarder
- Administrator for overholdelsesdata
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Sikkerhedslæser

Hvis du vil have adgang til dashboardet til administration af DLP-beskeder, skal du bruge følgende:

- Administrer beskeder

og en af disse to roller:

- Administration af DLP-overholdelse
- administration af DLP-overholdelse af View-Only

Du skal være medlem af for at få adgang til prøveversionsfunktionen Indhold og de matchende følsomme indholds- og kontekstfunktioner:

- Indholdsoversigt - rollegruppe for indholdsfremviser

som har forhåndstildelingen af rollen indholdsfremviser til dataklassificering.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

## <a name="dlp-alert-configuration"></a>Konfiguration af DLP-besked

Hvis du vil vide mere om, hvordan du konfigurerer en besked i din DLP-politik, skal du se [Hvor du starter med forebyggelse af datatab](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Konfigurationen af organisationens opbevaringspolitik for overvågningslog styrer, hvor længe en besked forbliver synlig i konsollen. Se [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md#manage-audit-log-retention-policies) for at få flere oplysninger.

### <a name="aggregate-event-alert-configuration"></a>Samlet konfiguration af hændelsesbeskeder

Hvis din organisation har licens til [aggregerede konfigurationsindstillinger for beskeder](#licensing-for-alert-configuration-options), kan du se disse indstillinger, når du opretter eller redigerer en DLP-politik.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til aggregerede konfigurationsindstillinger for beskeder." border="false":::

Denne konfiguration giver dig mulighed for at konfigurere en politik til at generere en besked, hver gang en aktivitet stemmer overens med politikbetingelserne, eller når en bestemt grænse overskrides, baseret på antallet af aktiviteter eller baseret på mængden af eksfiltrerede data.

### <a name="single-event-alert-configuration"></a>Konfiguration af en enkelt hændelsesbesked

Hvis din organisation har licens til [konfigurationsindstillinger for enkelthændelsesbeskeder](#licensing-for-alert-configuration-options), får du vist disse indstillinger, når du opretter eller redigerer en DLP-politik. Brug denne indstilling til at oprette en besked, der udløses, hver gang en DLP-regel matcher.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til konfigurationsindstillinger for en enkelt hændelsesbesked." border="false":::

## <a name="investigate-a-dlp-alert"></a>Undersøg en DLP-besked

Sådan arbejder du med dashboardet til administration af DLP-beskeder:

1. I Microsoft Purview-compliance-portal skal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">du</a> gå til **Forebyggelse af datatab**.
2. Vælg fanen **Beskeder** for at få vist dashboardet med DLP-beskeder.
3. Vælg en besked for at få vist detaljer:

:::image type="content" source="../media/alert-details.png" alt-text="Skærmbillede, der viser beskedoplysninger på dashboardet til administration af DLP-beskeder." border="false":::

4. Vælg fanen **Hændelser** for at få vist alle de hændelser, der er knyttet til beskeden. Du kan vælge en bestemt hændelse for at få vist dens detaljer. Du kan se en liste over nogle af de tilgængelige hændelsesoplysninger under [Få mere at vide om dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-learn.md).
5. Vælg **Detaljer** for at åbne siden **Oversigt** for beskeden. Oversigtssiden indeholder en oversigt:
    1. af, hvad der skete
    1. der udførte de handlinger, der forårsagede, at politikken blev matchet
    1. oplysninger om den tilsvarende politik m.m. 

6. Vælg fanen **Hændelser** for at få adgang til:
    1. indhold, der er involveret
    1. overensstemmende følsomme oplysningstyper
    1. Metadata

7. Vælg fanen **Følsomme oplysningstyper** for at få vist oplysninger om de følsomme oplysningstyper, der er registreret i indholdet. Detaljer omfatter tillid, antal og det indhold, der stemmer overens med typen af følsomme oplysninger.

8. Når du har undersøgt beskeden, skal du gå tilbage til fanen **Oversigt** , hvor du kan administrere triage og administrere fordelingen af beskeden og tilføje kommentarer.

- Hvis du vil se historikken for administration af arbejdsprocesser, skal du vælge **Administrationslog**.
- Når du har foretaget den nødvendige handling for beskeden, skal du angive status for beskeden til **Løst**.

## <a name="see-also"></a>Se også

- [Få mere at vide om beskeder til forebyggelse af datatab og dashboardet til beskeder](dlp-alerts-dashboard-learn.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
