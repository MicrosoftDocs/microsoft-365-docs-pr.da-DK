---
title: Kom i gang med scanner til forebyggelse af datatab i det lokale miljø
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
description: Konfigurer scanner til forebyggelse af datatab i det lokale miljø
ms.openlocfilehash: a1bcebfb48a502a9d7c484d266d91fe105603f84
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625429"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Kom i gang med forebyggelse af datatab i det lokale miljø

I denne artikel gennemgås forudsætningerne og konfigurationen af Microsoft Purview-scanner til forebyggelse af datatab i det lokale miljø.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Før du går i gang med DLP-scanner i det lokale miljø, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelsesprogrammer. Den administratorkonto, der konfigurerer DLP-reglerne, skal tildeles en af følgende licenser:

- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft 365 E5 Information Protection & styring 


Du kan finde komplette licensoplysninger under: [Vejledning til Microsoft 365-licenser om sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> Alle brugere, der bidrager til den scannede placering, enten ved at tilføje filer eller bruge filer, skal have en licens, ikke kun scannerbrugeren.

### <a name="permissions"></a>Tilladelser

Data fra DLP-scanner i det lokale miljø kan ses i [Aktivitetsoversigt](data-classification-activity-explorer.md). Der er fire roller, der giver tilladelse til aktivitetsoversigten. Den konto, du bruger til at få adgang til dataene, skal være medlem af en hvilken som helst af dem.

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Administrator af overholdelsesdata

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide om under [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

### <a name="dlp-on-premises-scanner-prerequisites"></a>DLP-forudsætninger for scanner i det lokale miljø

- AIP-scanneren (Azure Information Protection) implementerer DLP-politikmatchning og håndhævelse af politikker. Scanneren installeres som en del af AIP-klienten, så installationen skal opfylde alle forudsætningerne for AIP, AIP-klienten og AIP Unified Labeling Scanner.
- Installer AIP-klienten og -scanneren. Du kan få flere oplysninger [Installér AIP Unified Labeling-klienten](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) og [] under [Konfiguration og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install).
- Der skal være udgivet mindst ét navn og én politik i lejeren, selvom alle dine registreringsregler kun er baseret på typer af følsomme oplysninger.

## <a name="deploy-the-dlp-on-premises-scanner"></a>Installer DLP-scanneren i det lokale miljø

1. Følg procedurerne i [Installér AIP Unified Labeling-klienten](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Følg procedurerne i [Konfiguration og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install) for at fuldføre installationen af scanneren.
    1. Konfiguration af netværksregistreringsjob er et valgfrit trin. Du kan springe det over og definere specifikke lagre, der skal scannes i dit indholdsscanningsjob.
    2. Du skal oprette et indholdsscanningsjob og angive de lagre, der er vært for filer, som skal evalueres af DLP-programmet.
    3. Aktivér DLP-regler i det oprettede indholdsscanningsjob, og angiv indstillingen **Gennemtving** til **Fra**, medmindre du vil fortsætte direkte til DLP-håndhævelsesfasen.
3. Kontrollér, at du har fået tildelt et indholdsscanningsjob til den rette klynge. Hvis du stadig ikke har oprettet et indholdsscanningsjob, skal du oprette et nyt og tildele det til den klynge, der indeholder scannernoderne.

4. Opret forbindelse til [Azure Information Protection-udvidelsen i Azure Portal](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade), og føj dine lagre til det indholdsscanningsjob, der udfører scanningen.

5. Benyt en af følgende fremgangsmåder for at køre scanningen:
    1. angiv scannertidsplanen
    1. brug indstillingen **Scan nu** manuelt på portalen
    1. eller kør **Start-AIPScan PowerShell-cmdlet**

   > [!IMPORTANT]
   > Husk, at scanneren som standard kører en deltascanning af lageret, og at de filer, der allerede blev scannet i den forrige scanningscyklus, springes over, medmindre filen er ændret, eller du har startet en fuld scanning. Fuld rescan kan startes ved hjælp af indstillingen **Genscan alle filer** i brugergrænsefladen eller ved at køre **Start-AIPScan-Reset**.

6.  Åbn [siden forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) i Microsoft Purview-compliance-portal.

7. Vælg **Opret politik** , og opret en DLP-testpolitik. Se [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md) , hvis du har brug for hjælp til at oprette en politik. Sørg for at køre den i test, indtil du er fortrolig med denne funktion. Brug disse parametre til politikken:
    1. Afgræns DLP-reglen for scanner i det lokale miljø til bestemte placeringer, hvis det er nødvendigt. Hvis du angiver **placeringer** til **Alle**, vil alle filer, der scannes af scanneren, være underlagt matchning og håndhævelse af DLP-reglen.
    1. Når du angiver placeringerne, kan du bruge enten udeladelse eller medtagelsesliste. Du kan enten definere, at reglen kun er relevant for stier, der svarer til et af de mønstre, der er angivet på medtagelseslisten, eller alle filer, undtagen de filer, der svarer til det mønster, der er angivet på medtagelseslisten. Ingen lokale stier understøttes. Her er nogle eksempler på gyldige stier:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\mappe1
      - \*hemmelige\*.docx
      - \*hemmelighed\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///HR 
    3. Her er nogle eksempler på uacceptabel brug af værdier:
      - \*
      - \*\\A
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> Udeladelseslisten har forrang frem for medtagelseslisten.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>Visning af DLP-scannerbeskeder i det lokale miljø i dashboardet Administration af DLP-beskeder

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) i Microsoft Purview-compliance-portal, og vælg **Beskeder**.

2. Se procedurerne i [Sådan konfigurerer og får du vist beskeder for dine DLP-politikker for](dlp-configure-view-alerts-policies.md) at få vist beskeder for dine DLP-politikker for slutpunkter.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Visning af DLP-scanner i det lokale miljø i aktivitetsoversigt og overvågningslog

> [!NOTE]
> Scanneren i det lokale miljø kræver, at overvågning er aktiveret. I Microsoft 365 er overvågning aktiveret som standard.

1. Åbn [siden Dataklassificering](https://compliance.microsoft.com/dataclassification?viewid=overview) for dit domæne i Microsoft Purview-compliance-portal, og vælg Aktivitetsoversigt.

2. Se procedurerne i [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md) for at få adgang til og filtrere alle dataene til scannerplaceringerne i det lokale miljø.

3. Åbn [overvågningsloggen i Overholdelsescenter](https://security.microsoft.com/auditlogsearch). DLP-regelforekomsterne er tilgængelige i overvågningsloggens brugergrænseflade eller tilgængelige for [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 


## <a name="next-steps"></a>Næste trin
Nu, hvor du har installeret en testpolitik for DLP-placeringer i det lokale miljø og kan få vist aktivitetsdataene i Aktivitetsoversigt, er du klar til at gå videre til dit næste trin, hvor du opretter DLP-politikker, der beskytter dine følsomme elementer.

- [Brug af DLP i det lokale miljø](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Se også

- [Få mere at vide om DLP-scanner i det lokale miljø](dlp-on-premises-scanner-learn.md)
- [Brug DLP-scanner i det lokale miljø](dlp-on-premises-scanner-use.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
