---
title: Konfigurere og få vist beskeder om politikker til forebyggelse af datatab
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
description: Få mere at vide om, hvordan du definerer og administrerer beskeder om politikker til forebyggelse af datatab.
ms.openlocfilehash: 9b8ee897502f76dbdb63e3fbac99e4223f378a1a
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63594350"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Konfigurere og få vist beskeder om politik til forebyggelse af datatab

Politikker til forebyggelse af datatab (DLP) kan træffe beskyttende handlinger for at forhindre utilsigtet deling af følsomme elementer. Når der sker en handling på et følsomt element, kan du få besked ved at konfigurere beskeder for DLP. Denne artikel viser, hvordan du definerer omfattende politikker for påmindelser, der er knyttet til dine politikker til forebyggelse af datatab (DLP). Du kan se, hvordan du kan bruge det nye dashboard til administration af DLP-beskeder i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> til at få vist beskeder, hændelser og tilknyttede metadata for DLP-politikbrud.

## <a name="features"></a>Funktioner

Følgende funktioner er en del af dette:

-   **Dashboard til administration af DLP-beskeder**: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">I Microsoft 365 Overholdelsescenter</a> viser dette dashboard beskeder for DLP-politikker, der håndhæves på følgende arbejdsbelastninger:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Enheder
-   **Avancerede konfigurationsindstillinger for** beskeder: Disse indstillinger er en del af flowet til oprettelse af DLP-politikker. Brug dem til at oprette omfattende konfigurationer af beskeder. Du kan oprette en besked ved en enkelt begivenhed eller en samlet besked baseret på antallet af hændelser eller størrelsen af de sammensatte data.

## <a name="before-you-begin"></a>Før du begynder

Før du begynder, skal du kontrollere, at du har de nødvendige forudsætninger:

-   Licensering til dashboardet til administration af DLP-beskeder
-   Licensering til konfigurationsindstillinger for beskeder
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licensering til dashboardet til administration af DLP-beskeder

Alle berettigede lejere til Office 365 DLP kan få adgang til det nye DLP-dashboard til administration af beskeder. For at komme i gang bør du være berettiget til Office 365 DLP til Exchange Online, SharePoint Online og OneDrive for Business. Du kan finde flere oplysninger om licenskravene for Office 365 DLP i Hvilke licenser giver en bruger rettigheder til at [drage fordel af tjenesten?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md), der er berettiget til [Teams DLP](dlp-microsoft-teams.md), vil få vist deres slutpunktsbeskeder om DLP-politik og Teams DLP-politikbeskeder i dashboardet til administration af DLP-beskeder.

### <a name="licensing-for-alert-configuration-options"></a>Licensering til konfigurationsindstillinger for beskeder

- **Konfiguration af** en enkelt begivenhed: Organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, kan kun oprette påmindelsespolitikker, når der udløses en besked, hver gang der sker en aktivitet.
- **Konfiguration af aggregeret** påmindelse: Hvis du vil konfigurere aggregerede påmindelsespolitikker baseret på en grænseværdi, skal du have en af følgende konfigurationer:
  - Et E5- eller G5-abonnement
  - Et E1-, F1- eller G1- eller E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Microsoft 365 licens til eDiscovery og overvågning af tilføjelsesprogrammet

### <a name="roles"></a>Roller

Hvis du vil have vist dashboardet til administration af DLP-beskeder eller redigere konfigurationsindstillingerne for påmindelser i en DLP-politik, skal du være medlem af en af disse rollegrupper:

-   Overholdelsesadministrator
-   Dataadministrator for overholdelse af regler og standarder
-   Sikkerhedsadministrator
-   Sikkerhedsoperator
-   Sikkerhedslæser

For at få adgang til dashboardet til administration af DLP-beskeder skal du have rollen Administrer vigtige beskeder og en af følgende roller:

-   Administration af DLP-overholdelse
-   View-Only DLP-overholdelsesstyring

## <a name="alert-configuration-experience"></a>Påmindelseskonfigurationsoplevelse

Hvis du er berettiget til samlede [konfigurationsindstillinger](#licensing-for-alert-configuration-options) for beskeder, kan du se følgende indstillinger indbygget i DLP-politikforfatteroplevelsen.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Skærmbillede, der viser indstillinger for hændelsesrapporter for brugere, der er berettiget til samlede konfigurationsindstillinger for beskeder." border="false":::

Med denne konfiguration kan du konfigurere en politik til at generere en besked:

- hver gang en aktivitet opfylder politikbetingelserne
- når den definerede grænseværdi er nået eller overskredet
- baseret på antallet af aktiviteter
- baseret på mængden af eksfiltrerede data

For at forhindre en strøm af meddelelsesmails bliver alle forekomster, der forekommer inden for et minuttidsvindue, og som er for den samme DLP-regel og på den samme placering, grupperet sammen i den samme besked. Funktionen til et minuts aggregeringstidsvindue er tilgængelig i: 

- Et E5- eller G5-abonnement
- Et E1-, F1- eller G1- eller E3- eller G3-abonnement, der indeholder en af følgende funktioner:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft 365 E5 Overholdelse
    - Microsoft 365 licens til eDiscovery og overvågning af tilføjelsesprogrammet
 
For organisationer, der har et E1-, F1- eller G1-abonnement eller et E3- eller G3-abonnement, er aggregeringstidsvinduet 15 minutter.

## <a name="dlp-alert-management-dashboard"></a>Dashboard til administration af DLP-beskeder

Sådan arbejder du med dashboardet til administration af DLP-beskeder:

1.  I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter skal</a> du gå til **Forebyggelse af datatab**.

2.  Vælg fanen **Beskeder for** at få vist DLP-beskeddashboardet.

    -   Vælg filtre for at afgrænse listen over beskeder. Vælg **Tilpas kolonner for** at få vist de egenskaber, du vil have vist. Du kan også vælge at sortere beskederne i stigende eller faldende rækkefølge i en hvilken som helst kolonne.
    -   Vælg en besked for at få vist detaljer:

        :::image type="content" source="../media/alert-details.png" alt-text="Skærmbillede, der viser beskedoplysninger på dashboardet til administration af DLP-beskeder." border="false":::

1.  Vælg fanen **Hændelser** for at få vist alle de hændelser, der er knyttet til beskeden. Du kan vælge en bestemt hændelse for at få vist dens detaljer. I følgende tabel vises nogle af detaljerne om begivenheden.
    
    | Kategori          | Egenskabsnavn                 | Beskrivelse                                                                | Gældende hændelsestyper                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Oplysninger om begivenhed*||
    |      | Id                            | Entydigt id, der er knyttet til begivenheden                                        | Alle begivenheder                               |
    |                   | Placering                      | Arbejdsbelastning, hvor hændelsen blev registreret                                      | Alle begivenheder                               |
    |                   | Aktivitetstid              | Klokkeslæt for den brugeraktivitet, der forårsagede DLP-overtrædelse                    | Alle begivenheder                               |
    |*På påvirkede enheder*||
    |  | Bruger                          | Bruger, der var skyld i DLP-overtrædelse                                          | Alle begivenheder                               |
    |                   | Værtsnavn                      | Værtsnavn på den computer, hvor DLP-overtrædelse blev registreret              | Enheders begivenheder                           |
    |                   | IP-adresse                    | Computerens IP-adresse                                                  | Enheders begivenheder                           |
    |                   | Filsti                     | Absolut sti for den fil, der er involveret i overtrædelse                        | SharePoint, OneDrive og enheder |
    |                   | Mailmodtagere              | Modtagere af mail, der overtræder DLP-politikken                       | Exchange begivenheder                          |
    |                   | Mailens emne                 | Emnet for den mail, der overtræder DLP-politikken                          | Exchange begivenheder                          |
    |                   | Vedhæftede filer i mails             | Navnene på de vedhæftede filer i den mail, der overtræder DLP-politikken         | Exchange begivenheder                          |
    |                   | Webstedsejer                    | Navnet på ejeren af webstedet                                                     | SharePoint og OneDrive begivenheder           |
    |                   | URL-adresse til websted                      | Den fulde URL-adresse til SharePoint eller OneDrive websted                                | SharePoint og OneDrive begivenheder           |
    |                   | Fil oprettet                  | Tidspunkt for oprettelse af filer                                                      | SharePoint og OneDrive begivenheder           |
    |                   | Filen er senest ændret            | Klokkeslæt for den seneste ændring af filen                                  | SharePoint og OneDrive begivenheder           |
    |                   | Filstørrelse                     | Filens størrelse                                                           | SharePoint og OneDrive begivenheder           |
    |                   | Filejer                    | Ejeren af filen                                                          | SharePoint og OneDrive begivenheder           |
    |*Politikdetaljer*||
    |     | DLP-politik matchet            | Navnet på den DLP-politik, der blev matchet                                    | Alle begivenheder                               |
    |                   | Matchet regel                  | Navnet på DLP-reglen i DLP-politikken, der blev matchet                    | Alle begivenheder                               |
    |                   | Der er registreret følsomme oplysningstyper | Typer af følsomme oplysninger, der blev registreret som en del af DLP-politikken | Alle begivenheder                               |
    |                   | Handlinger, der er foretaget                 | Handlinger, der er taget som en del af den matchede DLP-politik                          | Alle begivenheder                               |
    |                   | Politik for overrode af brugere          | Om brugeren overrokerer politikken via politiktip                | Alle begivenheder                               |
    |                   | Tilsidesætte justeringstekst   | Begrundelse angivet for at tilsidesætte politiktip                          | Alle begivenheder                               |
    
1.  Vælg fanen **Typer af følsomme oplysninger** for at få vist detaljer om de typer af følsomme oplysninger, der registreres i indholdet. Detaljer omfatter tillid og optælling.

2.  Når du har undersøgt beskeden, skal **du vælge Administrer** besked for at ændre status (**Aktiv**, **Undersøges**, **Afvist** eller **Løst**). Du kan også tilføje kommentarer og tildele beskeden til en person i organisationen.

    -   Hvis du vil se en oversigt over arbejdsprocesstyring, skal du **vælge Administrationslog**.
    -   Når du har taget den nødvendige handling for beskeden, skal du angive status for beskeden **til Løst**.
