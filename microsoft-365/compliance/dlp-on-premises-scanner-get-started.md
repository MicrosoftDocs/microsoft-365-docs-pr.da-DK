---
title: Introduktion til Microsoft 365 lokal scanner til forebyggelse af datatab
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Konfigurer Microsoft 365 lokal scanner til forebyggelse af datatab
ms.openlocfilehash: 1586489389931b3df19a1c84f0ae49ac7ff9c099
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/21/2022
ms.locfileid: "63602995"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Kom i gang med den lokale scanner til forebyggelse af datatab

I denne artikel gennemgås forudsætningerne for og konfigurationen Microsoft 365 en lokal scanner til forebyggelse af datatab.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Før du går i gang med en lokal DLP-scanner, skal du bekræfte dit [Microsoft 365 og](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) eventuelle tilføjelser. Den administratorkonto, der konfigurerer DLP-reglerne, skal tildeles en af følgende licenser:

- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft 365 E5 information protection & styring 


Du kan finde flere oplysninger om [licenser i: Microsoft 365 licensvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> Alle brugere, der bidrager til den scannede placering ved enten at tilføje filer eller forbruge filer, skal have en licens, ikke kun scannerbrugeren.

### <a name="permissions"></a>Tilladelser

Data fra en lokal DLP-scanner kan vises i [Aktivitetsoversigt](data-classification-activity-explorer.md). Der er fire roller, der giver tilladelse til Aktivitetsstifinder. Den konto, du bruger til at få adgang til dataene, skal være medlem af en af dem.

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

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

### <a name="dlp-on-premises-scanner-prerequisites"></a>Forudsætninger for DLP-scanner i det lokale miljø

- AIP-scanneren (Azure Information Protection) implementerer matchende DLP-politikker og håndhævelse af politikker. Scanneren er installeret som en del af AIP-klienten, så din installation skal opfylde alle forudsætningerne for AIP, AIP-klienten og den samlede AIP-etiketscanner.
- Installér AIP-klienten og scanneren. Du kan finde [flere oplysninger Installér den samlede AIP-etiketklient](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) og [], under Konfiguration og installation af [den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner-configure-install).
- Der skal være mindst én etiket og politik publiceret i lejeren, også selvom alle dine registreringsregler kun er baseret på typer af følsomme oplysninger.

## <a name="deploy-the-dlp-on-premises-scanner"></a>Installér den lokale DLP-scanner

1. Følg fremgangsmåderne i [Installér den samlede AIP-etiketklient](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Følg fremgangsmåderne i [Konfiguration og installation af Den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner-configure-install) for at fuldføre installationen af scanneren.
    1. Konfiguration af netværksregistreringsjob er et valgfrit trin. Du kan springe det over og definere specifikke lagre, der skal scannes i dit indholdsscanningsjob.
    2. Du skal oprette et indholdsscanningsjob og angive de lagerfiler, der skal evalueres af DLP-programmet.
    3. Aktivér DLP-regler i det oprettede  indholdsscanningsjob **, og** angiv indstillingen Gennemtving til Fra, medmindre du vil fortsætte direkte til DLP-gennemtvingelsesfasen.
3. Kontrollér, at dit indholdsscanningsjob er tildelt den rigtige klynge. Hvis du stadig ikke har oprettet et indholdsscanningsjob, skal du oprette en ny og tildele det til den klynge, der indeholder scannernoderne.

4. Forbind til [Azure Information Protection-udvidelsen i Azure-portalen](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade), og føj dine lagre til det indholdsscanningsjob, der udfører scanningen.

5. Gør et af følgende for at køre scanningen:
    1. angiv scannertidsplanen
    1. skal du bruge **den manuelle** indstilling Scan nu i portalen
    1. eller kør **Start-AIPScan** PowerShell-cmdlet

   > [!IMPORTANT]
   > Husk, at scanneren kører en delta-scanning af lageret som standard, og de filer, der allerede er scannet i den forrige scanningscyklus, ignoreres, medmindre filen er blevet ændret, eller du har startet en fuld scanning igen. Fuld genscanning kan **startes** ved hjælp af indstillingen Genscan alle filer i brugergrænsefladen eller ved at køre **Start-AIPScan-Reset**.

6.  Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) i Microsoft 365 Compliance Center.

7. Vælg **Opret politik,** og opret en test-DLP-politik. Se [Opret en DLP-politik ud fra en skabelon, hvis](create-a-dlp-policy-from-a-template.md) du har brug for hjælp til at oprette en politik. Sørg for at køre det i en test, indtil du er fortrolig med denne funktion. Brug disse parametre til din politik:
    1. Omfang DLP-reglen for en lokal scanner til bestemte placeringer, hvis det er nødvendigt. Hvis du **områdeplaceringer til** **Alle**, vil alle filer, der scannes af scanneren, være underlagt DLP-reglens matchning og håndhævelse.
    1. Når du angiver placeringerne, kan du bruge enten udeladelses- eller inklusionslisten. Du kan enten angive, at reglen kun er relevant for stier, der matcher en af de mønstre, der er angivet på inklusionslisten, eller alle filer, undtagen de filer, der matcher det mønster, der er angivet i inklusionslisten. Ingen lokale stier understøttes. Her er nogle eksempler på gyldige stier:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\mappe1
      - \*hemmeligt\*.docx
      - \*hemmeligt\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///HR 
    3. Her er nogle eksempler på uacceptabel brug af værdier:
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> Udeladelseslisten tilsidesætter listen med medtagelser.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>Visning af lokale DLP-scannerbeskeder i dashboardet til administration af DLP-beskeder

1. Åbn siden [til forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) i Microsoft 365 Overholdelsescenter, og **vælg Beskeder**.

2. Se procedurerne i Sådan konfigurerer og får du vist beskeder [for dine DLP-politikker for](dlp-configure-view-alerts-policies.md) at få vist beskeder for dine Slutpunkt DLP-politikker.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Visning af DLP-scanner i det lokale miljø i Aktivitetsoversigt og overvågningslog

> [!NOTE]
> Den lokale scanner kræver, at overvågning er aktiveret. I Microsoft 365 er overvågning aktiveret som standard.

1. Åbn siden [Dataklassificering](https://compliance.microsoft.com/dataclassification?viewid=overview) for dit domæne i Microsoft 365 Overholdelsescenter, og vælg Aktivitetsstifinder.

2. Se fremgangsmåderne i Introduktion [til Aktivitetsstifinder for at](data-classification-activity-explorer.md) få adgang til og filtrere alle data til dine lokale scannerplaceringer.

3. Åbn [overvågningsloggen i Overholdelsescenter](https://security.microsoft.com/auditlogsearch). DLP-regel matchene er tilgængelige i brugergrænsefladen for overvågningsloggen eller tilgængelige via [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 


## <a name="next-steps"></a>Næste trin
Nu hvor du har installeret en testpolitik for DLP-placeringer i det lokale miljø og kan se aktivitetsdataene i Aktivitetsoversigt, er du klar til at gå videre til næste trin, hvor du opretter DLP-politikker, der beskytter dine følsomme elementer.

- [Brug af DLP lokalt](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Se også

- [Få mere at vide om lokal DLP-scanner](dlp-on-premises-scanner-learn.md)
- [Brug en lokal DLP-scanner](dlp-on-premises-scanner-use.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
