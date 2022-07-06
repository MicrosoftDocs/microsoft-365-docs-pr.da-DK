---
title: Konfigurer og få vist beskeder for DLP-politikker
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
description: Få mere at vide om, hvordan du definerer og administrerer beskeder for politikker til forebyggelse af datatab.
ms.openlocfilehash: 60d5188b9288b1e131e36e145f7abb98a34d5ead
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627641"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Konfigurer og få vist beskeder for politikker til forebyggelse af datatab

Microsoft Purview Forebyggelse af datatab politikker (DLP) kan udføre beskyttende handlinger for at forhindre utilsigtet deling af følsomme elementer. Når der udføres en handling på et følsomt element, kan du få besked ved at konfigurere beskeder for DLP. I denne artikel kan du se, hvordan du definerer omfattende beskedpolitikker, der er knyttet til politikker til forebyggelse af datatab (DLP). Du kan se, hvordan du bruger det nye dashboard til administration af DLP-beskeder i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> til at få vist beskeder, hændelser og tilknyttede metadata for DLP-politikovertrædelser.

## <a name="features"></a>Funktioner

Følgende funktioner er en del af dette:

-   **Dashboard til administration af DLP-beskeder**: I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> viser dette dashboard beskeder om DLP-politikker, der gennemtvinges for følgende arbejdsbelastninger:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Enheder
-   **Avancerede konfigurationsindstillinger for beskeder**: Disse indstillinger er en del af DLP-politikudviklerflowet. Brug dem til at oprette omfattende konfigurationer af beskeder. Du kan oprette en enkelt hændelsesbesked eller en samlet besked baseret på antallet af hændelser eller størrelsen af de lækkede data.

## <a name="before-you-begin"></a>Før du begynder

Før du begynder, skal du sørge for, at du har de nødvendige forudsætninger:

-   Licenser til dashboardet til administration af DLP-beskeder
-   Licenser til konfigurationsindstillinger for beskeder
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licenser til dashboardet til administration af DLP-beskeder

Alle berettigede lejere til Office 365 DLP kan få adgang til det nye dashboard til administration af DLP-beskeder. For at komme i gang skal du være berettiget til Office 365 DLP til Exchange Online, SharePoint Online og OneDrive for Business. Du kan få flere oplysninger om licenskravene til Office 365 DLP under [Hvilke licenser giver en bruger ret til at drage fordel af tjenesten?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md) , som er berettiget til [Teams DLP](dlp-microsoft-teams.md) , får vist deres DLP-politikbeskeder for slutpunkter og Teams DLP-politikbeskeder på dashboardet til administration af DLP-beskeder.

### <a name="licensing-for-alert-configuration-options"></a>Licenser til konfigurationsindstillinger for beskeder

- **Konfiguration af en enkelt hændelsesbesked**: Organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, kan kun oprette beskedpolitikker, hvis en besked udløses, hver gang der forekommer en aktivitet.
- **Samlet konfiguration af beskeder**: Hvis du vil konfigurere samlede politikker for beskeder baseret på en tærskel, skal du have en af følgende konfigurationer:
  - Et E5- eller G5-abonnement
  - Et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Licens til Microsoft 365 eDiscovery- og overvågningstilføjelsesprogram

### <a name="roles"></a>Roller

Hvis du vil have vist dashboardet til administration af DLP-beskeder eller redigere indstillingerne for konfiguration af beskeder i en DLP-politik, skal du være medlem af en af disse rollegrupper:

-   Administrator for overholdelse af angivne standarder
-   Administrator for overholdelsesdata
-   Sikkerhedsadministrator
-   Sikkerhedsoperator
-   Sikkerhedslæser

Hvis du vil have adgang til dashboardet til administration af DLP-beskeder, skal du have rollen Administrer beskeder og en af følgende roller:

-   Administration af DLP-overholdelse
-   administration af DLP-overholdelse af View-Only

## <a name="alert-configuration-experience"></a>Oplevelse af konfiguration af beskeder

Hvis du er berettiget til [aggregerede konfigurationsindstillinger for beskeder](#licensing-for-alert-configuration-options), kan du se følgende indstillinger indbygget i oplevelsen til oprettelse af DLP-politik.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til aggregerede konfigurationsindstillinger for beskeder." border="false":::

Denne konfiguration giver dig mulighed for at konfigurere en politik til at generere en besked:

- hver gang en aktivitet stemmer overens med politikbetingelserne
- når den definerede grænse nås eller overskrides
- baseret på antallet af aktiviteter
- baseret på mængden af exfiltrated data

For at forhindre en strøm af meddelelsesmails grupperes alle match, der forekommer inden for et minuts tidsrum, og som er for den samme DLP-regel og på samme placering, sammen i den samme besked. Funktionen til aggregeringstid på ét minut er tilgængelig i: 

- Et E5- eller G5-abonnement
- Et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Licens til Microsoft 365 eDiscovery- og overvågningstilføjelsesprogram
 
For organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, er sammenlægningstidsvinduet 15 minutter.

## <a name="dlp-alert-management-dashboard"></a>Dashboard til administration af DLP-beskeder

Sådan arbejder du med dashboardet til administration af DLP-beskeder:

1.  I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal skal du</a> gå til **Forebyggelse af datatab**.

2.  Vælg fanen **Beskeder** for at få vist dashboardet med DLP-beskeder.

    -   Vælg filtre for at tilpasse listen over beskeder. Vælg **Tilpas kolonner** for at få vist de egenskaber, du vil se. Du kan også vælge at sortere beskederne i stigende eller faldende rækkefølge i en hvilken som helst kolonne.
    -   Vælg en besked for at få vist detaljer:

        :::image type="content" source="../media/alert-details.png" alt-text="Skærmbillede, der viser beskedoplysninger på dashboardet til administration af DLP-beskeder." border="false":::

1.  Vælg fanen **Hændelser** for at få vist alle de hændelser, der er knyttet til beskeden. Du kan vælge en bestemt hændelse for at få vist dens detaljer. I følgende tabel vises nogle af hændelsesdetaljerne.
    
    | Kategori          | Egenskabsnavn                 | Beskrivelse                                                                | Relevante hændelsestyper                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Oplysninger om begivenhed*||
    |      | Id                            | Entydigt id, der er knyttet til hændelsen                                        | Alle hændelser                               |
    |                   | Placering                      | Arbejdsbelastning, hvor hændelsen blev registreret                                      | Alle hændelser                               |
    |                   | Tidspunkt for aktivitet              | Tidspunktet for den brugeraktivitet, der forårsagede DLP-fejlen                    | Alle hændelser                               |
    |*Påvirkede enheder*||
    |  | Bruger                          | Bruger, der forårsagede DLP-fejlen                                          | Alle hændelser                               |
    |                   | Værtsnavn                      | Værtsnavnet på den computer, hvor DLP-fejlen blev registreret              | Enhedshændelser                           |
    |                   | IP-adresse                    | Computerens IP-adresse                                                  | Enhedshændelser                           |
    |                   | Filsti                     | Absolut sti til den fil, der er involveret i fejlen                        | Hændelser for SharePoint, OneDrive og enheder |
    |                   | Mailmodtagere              | Modtagere af den mail, der har overtrådt DLP-politikken                       | Exchange-hændelser                          |
    |                   | Mailemne                 | Emnet for den mail, der overtrådte DLP-politikken                          | Exchange-hændelser                          |
    |                   | Vedhæftede filer i mails             | Navnene på de vedhæftede filer i den mail, der overtrådte DLP-politikken         | Exchange-hændelser                          |
    |                   | Webstedsejer                    | Navnet på webstedets ejer                                                     | SharePoint- og OneDrive-hændelser           |
    |                   | URL-adresse til websted                      | Fuldstændig URL-adresse til SharePoint- eller OneDrive-webstedet                                | SharePoint- og OneDrive-hændelser           |
    |                   | Filen er oprettet                  | Tidspunkt for filoprettelse                                                      | SharePoint- og OneDrive-hændelser           |
    |                   | Filen blev senest ændret            | Tidspunkt for seneste ændring af filen                                  | SharePoint- og OneDrive-hændelser           |
    |                   | Filstørrelse                     | Filens størrelse                                                           | SharePoint- og OneDrive-hændelser           |
    |                   | Filejer                    | Ejer af filen                                                          | SharePoint- og OneDrive-hændelser           |
    |*Oplysninger om politik*||
    |     | DLP-politik matcher            | Navnet på den DLP-politik, der blev matchet                                    | Alle hændelser                               |
    |                   | Regel, der stemmer overens                  | Navnet på DLP-reglen i den DLP-politik, der blev matchet                    | Alle hændelser                               |
    |                   | Der blev fundet følsomme infotyper | Følsomme oplysningstyper, der blev registreret som en del af DLP-politikken | Alle hændelser                               |
    |                   | Udførte handlinger                 | Handlinger, der udføres som en del af den tilsvarende DLP-politik                          | Alle hændelser                               |
    |                   | Politik for brugeroverrode          | Angiver, om brugeren tilsidesætter politikken via politiktip                | Alle hændelser                               |
    |                   | Tilsidesæt justeringstekst   | Begrundelse for tilsidesættelse af politiktip                          | Alle hændelser                               |
    
1.  Vælg fanen **Følsomme oplysningstyper** for at få vist oplysninger om de følsomme oplysningstyper, der er registreret i indholdet. Detaljer omfatter tillid og antal.

2.  Når du har undersøgt beskeden, skal du vælge **Administrer besked** for at ændre status (**aktiv**, **undersøgelse**, **afvist** eller **løst**). Du kan også tilføje kommentarer og tildele beskeden til en person i din organisation.

    -   Hvis du vil se historikken for administration af arbejdsprocesser, skal du vælge **Administrationslog**.
    -   Når du har foretaget den nødvendige handling for beskeden, skal du angive status for beskeden til **Løst**.
