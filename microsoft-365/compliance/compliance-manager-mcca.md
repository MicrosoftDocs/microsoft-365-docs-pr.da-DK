---
title: Microsoft Compliance Configuration Analyzer til Overholdelsesstyring
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Forstå, hvordan du bruger Microsoft Compliance Configuration Analyzer til hurtigt at komme i gang med Microsoft Purview Compliance Manager.
ms.openlocfilehash: a973412c2d40993b47343273675cee3922b57cdf
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012808"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Microsoft Compliance Configuration Analyzer til Overholdelsesstyring (prøveversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**I denne artikel:** Få mere at vide om, hvordan du installerer og kører værktøjet Microsoft Compliance Configure Analyzer for hurtigt at komme i gang med Microsoft Compliance Manger.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Oversigt over Microsoft Compliance Configuration Analyzer (MCCA) (prøveversion)

MCCA (Microsoft Compliance Configuration Analyzer) er et eksempelværktøj, der kan hjælpe dig med at komme i gang med [Microsoft Purview Compliance Manager](compliance-manager.md). MCCA er et PowerShell-baseret værktøj, der henter din organisations aktuelle konfigurationer og validerer dem i forhold til Microsoft 365 anbefalede bedste praksis. Disse bedste fremgangsmåder er baseret på et sæt kontrolelementer, der omfatter vigtige regler og standarder for databeskyttelse og datastyring.

MCCA kan hjælpe dig med hurtigt at se, hvilke forbedringshandlinger i Overholdelsesstyring der gælder for dit aktuelle Microsoft 365 miljø. Hver handling, der identificeres af MCCA, giver dig anbefalinger til implementering med direkte links til Overholdelsesstyring og den relevante løsning for at begynde at træffe korrigerende foranstaltninger.

En yderligere ressource til forståelse af MCCA er ved at gå til [VIGTIGT-vejledningen på GitHub](https://github.com/OfficeDev/MCCA#overview). Denne side indeholder detaljerede oplysninger om forudsætninger og giver fuld installationsvejledning. Du behøver ikke en GitHub konto for at få adgang til denne side.

**Tilgængelighed**: MCCA er tilgængelig for alle organisationer med Office 365- og Microsoft 365-licenser og doD-kunder (US Government Community) (GCC GCC).

## <a name="install-mcca-and-run-a-report"></a>Installér MCCA, og kør en rapport

Du kan installere MCCA-værktøjet ved hjælp af Windows PowerShell. Når du har downloadet og installeret værktøjet, behøver du ikke at gentage disse trin for at køre rapporter. Hver gang du åbner MCCA, bliver du bedt om dine legitimationsoplysninger til logon, og der genereres en ny, opdateret rapport.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>Trin 1: Installér Exchange Online PowerShell V2-modulet

Til at begynde med skal du bruge det Exchange Online PowerShell-modul (v2.0.3 eller nyere), der er tilgængeligt i PowerShell-galleriet. Du kan finde installationsvejledning under [Installér og vedligehold EXO V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-mcca"></a>Trin 2: Installér MCCA

Hvis du vil installere MCCA, skal du starte med at bruge PowerShell i administratortilstand. Følg nedenstående trin:

1. Vælg knappen Windows **Start**.
1. Skriv **PowerShell**, højreklik på **Windows PowerShell**, og vælg derefter **Kør som administrator**.
1. Skriv følgende ud for kommandoprompten:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>Trin 3: Kør en rapport

Når du har installeret MCCA, kan du køre MCCA og generere en rapport. Sådan kører du en rapport:

1. Åbn PowerShell
2. Kør cmdlet'en:

    ```powershell
    Get-MCCAReport
    ```

    Hvis du er GCC High-kunde, skal du angive en ekstra inputparameter for at køre rapporten:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Når MCCA kører, foretager den en indledende versionskontrol og beder om legitimationsoplysninger. Log på med din Microsoft 365 kontomailadresse ved prompten Skriv brugernavnet ([få vist de roller, der er berettiget til at oprette rapporter](#role-based-reporting)). Angiv derefter din adgangskode ved prompten om adgangskode.

Det tager derefter ca. 2-5 minutter at generere din rapport. Når du er færdig, åbnes der et browservindue, hvor din HTML-rapport vises. Hver gang du kører værktøjet, bliver du bedt om dine legitimationsoplysninger og genererer en ny rapport. Denne rapport gemmes lokalt i mappen C: \ Brugere \ *brugernavn* \ AppData \ Lokal \ Microsoft \ MCCA.

Du kan få adgang til tidligere genererede rapporter fra denne mappe.

## <a name="understanding-your-report"></a>Om din rapport

Din rapport afspejler data baseret på den dato og det klokkeslæt, hvor de blev genereret. Det øverste afsnit indeholder oplysninger om, hvornår det blev genereret, organisationens navn og lejer-id.

### <a name="geolocation-based-reporting"></a>Geoplaceringsbaseret rapportering

I afsnittet **Note** kan du se, at din rapport er tilpasset på baggrund af lejerens geografiske placering. Anbefalinger, der er angivet i værktøjet, er specifikke for dit land eller område.

Dit valg af geoplacering bruges til at vurdere følsomme informationstyper (SIT'er), der er relevante for den pågældende geoplacering, og generere en rapport, der stemmer overens med dit land eller område. Vælg geoplaceringer baseret på data, du har i din lejer.

Hvis du vil ændre oplysningerne om din rapports placering, skal du angive en inputparameter for geoplacering (-Geo). Du kan vælge enten en eller flere geoplaceringer, der gælder for din lejer.

Følg disse instruktioner for at køre en rapport, der er baseret på en bestemt placering:

1. Åbn PowerShell
2. Hvis du vil angive et bestemt område, skal du køre en cmdlet ved hjælp af tallene fra nedenstående tabel, der svarer til landet eller området. Angiv flere tal ved at adskille dem med et komma. Cmdlet'en nedenfor kører f.eks. en brugerdefineret rapport for Asia-Pacific og Japan:

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```

  | Input |  Land eller område |
  | :------------- | :------------: |
  | 1 | Asia-Pacific |
  | 2 | Australien |
  | 3 | Canada |
  | 4 | Europa (undtagen Frankrig) /Mellemøsten/Afrika |
  | 5 | Frankrig |
  | 6 | Indien |
  | 7 | Japan |
  | 8 | Sydkorea |
  | 9 | Nordamerika (undtagen Canada) |
  | 10 | Sydamerika |
  | 11 | Sydafrika |
  | 12 | Schweiz |
  | 13 | De Forenede Arabiske Emirater |
  | 14 | Storbritannien |

  > [!NOTE]
  > Betænkningen vil altid omfatte internationale følsomme informationtyper som SWIFT-kode, kreditkortnummer osv.

### <a name="role-based-reporting"></a>Rollebaseret rapportering

Din rapport tilpasses også på baggrund af din rolle.

I nedenstående tabel kan du se, hvilke roller der har adgang til hvilke sektioner i rapporten. Andre roller i din organisation (ikke angivet i tabellen nedenfor) kan muligvis ikke køre værktøjet, eller de kan køre værktøjet og have begrænset adgang til oplysninger i den endelige rapport.

![MCCA – roller.](../media/compliance-manager-mcca-roles.png "MCCA-roller")

Undtagelser:

1. Brugerne kan ikke generere rapport for IP bortset fra afsnittet "Brug IRM til Exchange Online".
2. Brugerne kan generere rapport for IP bortset fra afsnittet "Brug IRM til Exchange Online".
3. Brugerne vil kunne generere rapport for IP bortset fra afsnittet "Aktivér kommunikationsoverholdelse i O365".
4. Brugerne kan ikke oprette en rapport for IP bortset fra afsnittet "Aktivér overvågning i Office 365".
5. Brugerne kan generere en rapport for IP bortset fra afsnittet "Aktivér overvågning i Office 365".

### <a name="solutions-summary-section"></a>Afsnittet Løsningsoversigt

Afsnittet **Løsningsoversigt** i rapporten indeholder en oversigt over forbedringshandlinger, som din organisation kan udføre i Overholdelsesstyring for at hjælpe med at forbedre din overholdelse af angivne standarder.

![MCCA – oversigt over løsninger.](../media/compliance-manager-mcca-solutions.png "Skærmbilledet MCCA Solutions Summary")

MCCA evaluerer dine aktuelle konfigurationer i forhold til de anbefalede forbedringshandlinger i Overholdelsesstyring. Alle forbedringsforanstaltninger, som MCCA-værktøjet har identificeret som nødvendige, vil blive anført i dette afsnit.

Ud for hver Microsoft-løsning er der farvekodede felter, der angiver antallet af elementer, der svarer til forbedringshandlinger i Overholdelsesstyring. Handlingerne er opdelt i tre statustilstande:

- **OK**: de handlinger, der opfylder de anbefalede betingelser og ikke behøver opmærksomhed på nuværende tidspunkt
- **Forbedring**: foranstaltninger, der kræver opmærksomhed
- **Anbefaling**: Handlinger, der ikke kræver opmærksomhed, men som vi anbefaler bedste praksis for

Markér et felt for at få vist forbedringer og anbefalinger.

#### <a name="items-with-the-improvement-status"></a>Elementer med statussen Forbedring

Vælg rullelisten ud for mærkaten **Forbedring** til højre for forbedringshandlingen. Du får vist en hurtig oversigt og oplysninger om dine aktuelle indstillinger og de anbefalede forbedringshandlinger. Oversigten indeholder direkte links til Overholdelsesstyring, den relevante løsning på Microsoft Purview-overholdelsesportalen og relevant dokumentation.

Når du klikker på linket Overholdelsesstyring, kommer du til en filtreret visning af alle forbedringshandlinger i den løsning, som du endnu ikke har implementeret. Herfra kan du se antallet af point, du kan opnå for at øge din [score for overholdelse af angivne standarder](compliance-score-calculation.md), de vurderinger, de gælder for, samt de gældende regler og certificeringer.

I forbindelse med DLP er der en knap til **afhjælpningsscript** , der giver dig et forudoprettede PowerShell-script baseret på det, der anbefales. Du kan kopiere og indsætte det direkte i din PowerShell-konsol. Den opretter en DLP-politik i testtilstand

#### <a name="items-with-recommendation-status"></a>Elementer med anbefalingsstatus

Vælg rullelisten ud for mærkaten **Anbefaling** til højre for forbedringshandlingen. Du får vist en oversigt over din organisations aktuelle Microsoft 365 miljø, der er relateret til forbedringshandlingen, sammen med anbefalede bedste fremgangsmåder.

## <a name="resources"></a>Ressourcer

Du kan finde flere detaljerede oplysninger om installation, konfiguration og brug af MCCA i [VIGTIGT-vejledningen om GitHub](https://github.com/OfficeDev/MCCA#overview) (der kræves ingen GitHub konto).

Du kan få flere oplysninger om Windows PowerShell i [Sådan bruger du PowerShell-dokumentationen](/powershell/scripting/how-to-use-docs). Se også [Start Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
