---
title: Introduktion til dashboardet til forebyggelse af datatab
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
description: Kom i gang med at definere og administrere beskeder om politikker til forebyggelse af datatab.
ms.openlocfilehash: d295a04c27231b937ca552feb06628f857528e34
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63597897"
---
# <a name="get-started-with-the-data-loss-prevention-alert-dashboard"></a>Introduktion til dashboardet til forebyggelse af datatab

Politikker til forebyggelse af datatab (DLP) kan træffe beskyttende handlinger for at forhindre utilsigtet deling af følsomme elementer. Når der sker en handling på et følsomt element, kan du få besked ved at konfigurere beskeder for DLP. Denne artikel viser, hvordan du definerer omfattende politikker for påmindelser, der er knyttet til dine politikker til forebyggelse af datatab (DLP). Du kan se, hvordan du bruger [dashboardet til administration af DLP-beskeder](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> til at få vist beskeder, hændelser og tilknyttede metadata for DLP-politikbrud.

Hvis du er ny bruger af DLP-beskeder, skal du gennemse Få mere at vide om dashboardet [til forebyggelse af datatab](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Før du begynder

Før du begynder, skal du kontrollere, at du har de nødvendige forudsætninger:

-   Licensering til dashboardet til administration af DLP-beskeder
-   Licensering til konfigurationsindstillinger for beskeder
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licensering til dashboardet til administration af DLP-beskeder

Alle berettigede lejere til Office 365 DLP kan få adgang til DLP-dashboardet for administration af beskeder. For at komme i gang bør du være berettiget til Office 365 DLP til Exchange Online, SharePoint Online og OneDrive for Business. Du kan finde flere oplysninger om licenskravene for Office 365 DLP i Hvilke licenser giver en bruger rettigheder til at [drage fordel af tjenesten?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md), der er berettiget til [Teams DLP](dlp-microsoft-teams.md), vil få vist deres slutpunktsbeskeder om DLP-politik og Teams DLP-politikbeskeder i dashboardet til administration af DLP-beskeder.

Funktionen **til forhåndsvisning** af indhold er kun tilgængelig for disse licenser:

- Microsoft 365 (E5)
- Office 365 (E5)
- Tilføjelsesprogrammet Avanceret overholdelse af regler og standarder (E5)
- Microsoft 365 E5/A5 Information Protection and Governance
- Microsoft 365 E5/A5-overholdelse

### <a name="licensing-for-alert-configuration-options"></a>Licensering til konfigurationsindstillinger for beskeder

**Konfiguration af** en enkelt begivenhed: Organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, kan kun oprette påmindelsespolitikker, når der udløses en besked, hver gang der sker en aktivitet.

**Samlet påmindelseskonfiguration**: Hvis du vil konfigurere aggregerede advarselspolitikker baseret på en grænseværdi, skal du bruge en af disse licenskonfigurationer:

- Et E5- eller G5-abonnement
- Et E1-, F1- eller G1- eller E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Microsoft 365 licens til eDiscovery og overvågning af tilføjelsesprogrammet

### <a name="roles"></a>Roller

Hvis du vil have vist dashboardet til administration af DLP-beskeder eller redigere konfigurationsindstillingerne for påmindelser i en DLP-politik, skal du være medlem af en af disse rollegrupper:

- Overholdelsesadministrator
- Dataadministrator for overholdelse af regler og standarder
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Sikkerhedslæser

For at få adgang til dashboardet til administration af DLP-beskeder skal du bruge:

- Administrer beskeder

og en af disse to roller:

- Administration af DLP-overholdelse
- View-Only DLP-overholdelsesstyring

For at få adgang til funktionen Indholdseksempel og Tilsvarende følsomt indhold og kontekstfunktioner skal du være medlem af:

- Rollegruppen Indholdsvisning i Indholdsoversigt

som har dataklassificeringens indholdsvisningsrolle tildelt på forhånd.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at vide om [dette under Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

## <a name="dlp-alert-configuration"></a>Konfiguration af DLP-besked

Du kan få mere at vide om, hvordan du konfigurerer en besked i din DLP-politik under [Hvor du skal starte med forebyggelse af datatab](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Din organizations audit log retention policy configuration controls how long an alert remains visible in the console. Se Administrere [opbevaringspolitikker for overvågningslogfiler](audit-log-retention-policies.md#manage-audit-log-retention-policies) for at få flere oplysninger.

### <a name="aggregate-event-alert-configuration"></a>Konfiguration af aggregeret hændelsesbesked

Hvis din organisation er licenseret til [aggregerede](#licensing-for-alert-configuration-options) konfigurationsindstillinger for beskeder, får du vist disse indstillinger, når du opretter eller redigerer en DLP-politik.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til samlede konfigurationsindstillinger for beskeder." border="false":::

Denne konfiguration gør det muligt at konfigurere en politik til at generere en besked, hver gang en aktivitet opfylder politikbetingelserne, eller når en bestemt grænseværdi overskrides, baseret på antallet af aktiviteter eller baseret på mængden af exfiltrated data.

### <a name="single-event-alert-configuration"></a>Konfiguration af enkelt hændelsesbesked

Hvis din organisation er licenseret til konfigurationsindstillinger for enkelt begivenhed, får du vist disse indstillinger, når du opretter eller redigerer en [DLP-politik](#licensing-for-alert-configuration-options). Brug denne indstilling til at oprette en besked, der hæves, hver gang der opstår et DLP-regelmatch.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til konfigurationsindstillinger for enkelthændelser." border="false":::

## <a name="investigate-a-dlp-alert"></a>Undersøg en DLP-besked

Sådan arbejder du med dashboardet til administration af DLP-beskeder:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter skal</a> du gå til **Forebyggelse af datatab**.
2. Vælg fanen **Beskeder for** at få vist DLP-beskeddashboardet.
3. Vælg en besked for at få vist detaljer:

:::image type="content" source="../media/alert-details.png" alt-text="Skærmbillede, der viser beskedoplysninger på dashboardet til administration af DLP-beskeder." border="false":::

4. Vælg fanen **Hændelser** for at få vist alle de hændelser, der er knyttet til beskeden. Du kan vælge en bestemt hændelse for at få vist dens detaljer. Du kan finde en liste over nogle af de tilgængelige detaljer om begivenheden i [Få mere at vide om dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-learn.md).
5. Vælg **Detaljer** for at åbne **siden** Oversigt for beskeden. Oversigtssiden indeholder en oversigt:
    1. af, hvad der skete
    1. hvem der udførte de handlinger, der forårsagede politikmatch
    1. oplysninger om den matchede politik og meget mere 

6. Vælg fanen **Begivenheder** for at få adgang til:
    1. involveret indhold
    1. typer af følsomme oplysninger, der er matchet
    1. metadata

7. Vælg fanen **Typer af følsomme oplysninger** for at få vist detaljer om de typer af følsomme oplysninger, der registreres i indholdet. Detaljer omfatter tillid, antal og det indhold, der svarer til typen af følsomme oplysninger.

8. Når du har undersøgt beskeden, skal du gå  tilbage til fanen Oversigt, hvor du kan administrere triage og administrere dispositionen af beskeden og tilføje kommentarer.

- Hvis du vil se en oversigt over arbejdsprocesstyring, skal du **vælge Administrationslog**.
- Når du har taget den nødvendige handling for beskeden, skal du angive status for beskeden **til Løst**.

## <a name="see-also"></a>Se også

- [Få mere at vide om beskeder om forebyggelse af datatab og dashboardet for påmindelser](dlp-alerts-dashboard-learn.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
