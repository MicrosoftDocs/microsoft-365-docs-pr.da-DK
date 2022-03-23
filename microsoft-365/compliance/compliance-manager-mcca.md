---
title: Microsoft Compliance Configuration Analyzer for Compliance Manager
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
description: Få mere at vide om, hvordan du bruger Microsoft Compliance Configuration Analyzer til at komme hurtigt i gang med Microsoft Compliance Manager.
ms.openlocfilehash: a679f0483431313672ac0dfa1101eb9909b6c060
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63589850"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Microsoft Compliance Configuration Analyzer for Compliance Manager (preview)

**I denne artikel:** Få mere at vide om, hvordan du installerer og kører værktøjet Microsoft Compliance Configure Analyzer for at komme hurtigt i gang med Microsoft Compliance Manger.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Oversigt over Microsoft Compliance Configuration Analyzer (MCCA) (preview)

Microsoft Compliance Configuration Analyzer (MCCA) er et eksempelværktøj, der kan hjælpe dig i gang med [Microsoft Compliance Manager](compliance-manager.md). MCCA er et PowerShell-baseret værktøj, der henter din organisations aktuelle konfigurationer og validerer dem mod Microsoft 365 anbefalede bedste fremgangsmåder. Disse bedste fremgangsmåder er baseret på et sæt af kontrolelementer, der indeholder vigtige bestemmelser og standarder for databeskyttelse og datastyring.

MCCA kan hjælpe dig med hurtigt at se, hvilke forbedringshandlinger i Overholdelsesstyring der gælder for dit Microsoft 365 miljø. Hver handling, der identificeres af MCCA, vil give dig anbefalinger til implementering med direkte links til Overholdelsesstyring og den løsning, der er relevant for at begynde at afhjælpe problemet.

En ekstra ressource til at forstå MCCA er ved at besøge [README-vejledningen på GitHub](https://github.com/OfficeDev/MCCA#overview). Denne side indeholder detaljerede oplysninger om forudsætninger og giver fuld installationsvejledning. Du behøver ikke en konto til GitHub at få adgang til denne side.

**Tilgængelighed**: MCCA er tilgængelig for alle organisationer med Office 365- og Microsoft 365-licenser og amerikanske Government Community (GCC) Moderate, GCC High- og Department of Defense-kunder (DoD).

## <a name="install-mcca-and-run-a-report"></a>Installér MCCA, og kør en rapport

Du kan installere MCCA-værktøjet ved hjælp Windows PowerShell. Når du har downloadet og installeret værktøjet, behøver du ikke at gentage disse trin for at køre rapporter. Hver gang du åbner MCCA, bliver du bedt om at angive dine logonoplysninger, og der genereres en ny, opdateret rapport.

### <a name="step-1-install-windows-powershell"></a>Trin 1: Installer Windows PowerShell

Til at begynde med skal du bruge det Exchange Online PowerShell-modul (v2.0.3 eller nyere), der er tilgængeligt i PowerShell-galleriet. [Få installationsvejledning.](https://www.powershellgallery.com/packages/ExchangeOnlineManagement/2.0.3)

### <a name="step-2-install-mcca"></a>Trin 2: Installér MCCA

Hvis du vil installere MCCA, skal du starte med at bruge PowerShell i administratortilstand. Følg nedenstående trin:

1. Vælg knappen **Windows Start.**
1. Skriv **PowerShell**, højreklik på en **Windows PowerShell**, og vælg derefter **Kør som administrator**.
1. Skriv følgende i kommandoprompten:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>Trin 3: Kør en rapport

Når du har installeret MCCA, kan du køre MCCA og oprette en rapport. Sådan kører du en rapport:

1. Åbn PowerShell
2. Kør cmdlet'en:

    ```powershell
    Get-MCCAReport
    ```

    Hvis du er en GCC High-kunde, skal du angive en ekstra inputparameter for at køre rapporten:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Når MCCA kører, kontrollerer den den oprindelige version og beder om legitimationsoplysninger. Når du bliver bedt om at indtaste brugernavnet, skal du logge på med din Microsoft 365 -kontos mailadresse (se [rollerne, der er berettiget til at oprette rapporter](#role-based-reporting)). Skriv din adgangskode ved prompten om adgangskoden.

Det tager derefter ca. 2-5 minutter at generere rapporten. Når det er gjort, åbnes et browservindue, som viser HTML-rapporten. Hver gang du kører værktøjet, beder det om dine legitimationsoplysninger og genererer en ny rapport. Denne rapport er gemt lokalt i mappen C: \ Brugere \ *brugernavn* \ AppData \ Local \ Microsoft \ MCCA.

Du kan få adgang til tidligere genererede rapporter fra denne mappe.

## <a name="understanding-your-report"></a>Forstå din rapport

Rapporten afspejler data baseret på den dato og det klokkeslæt, hvor de blev oprettet. Den øverste sektion indeholder oplysninger om, hvornår den blev oprettet, organisationens navn og lejer-id.

#### <a name="geolocation-based-reporting"></a>Geolocation-baseret rapportering

Afsnittet **Note** viser, at rapporten er tilpasset ud fra din lejers geografiske placering. Anbefalinger angivet i værktøjet, vil være specifikke for dit land eller område.

Dit valg af geoplacering bruges til at vurdere følsomme oplysningstyper, der er relevante for den pågældende geoplacering og genererer en rapport, der passer til dit land eller område. Vælg geoplaceringer baseret på data, du har i din lejer.

Hvis du vil ændre rapportens placeringsoplysninger, skal du angive en geoplaceringsinputparameter (-Geo). Du kan vælge enten en eller flere geoplaceringer, der er relevante for din lejer.

Følg disse instruktioner for at køre en rapport baseret på en bestemt placering:

1. Åbn PowerShell
2. Hvis du vil angive et bestemt område, skal du køre en cmdlet med tallene fra tabellen nedenfor, der svarer til landet eller området. Angiv flere tal ved at adskille dem med et komma. Eksempelvis kører nedenstående cmdlet en tilpasset rapport for Asia-Pacific og Japan:

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
  | 8 | Korea |
  | 9 | Nordamerika (undtagen Canada) |
  | 10 | Sydamerika |
  | 11 | Sydafrika |
  | 12 | Schweiz |
  | 13 | De Forenede Arabiske Emirater |
  | 14 | Storbritannien |


 > [!NOTE]
> Rapporten vil altid indeholde MCCA-understøttede internationale følsomme oplysningstyper som SWIFT-kode, kreditkortnummer osv.

#### <a name="role-based-reporting"></a>Rollebaseret rapportering

Rapporten bliver også tilpasset ud fra din rolle.

Tabellen nedenfor viser, hvilke roller der har adgang til hvilke sektioner i rapporten. Andre roller i organisationen (der ikke er angivet i tabellen nedenfor) kan muligvis ikke køre værktøjet, eller de kan køre værktøjet og har begrænset adgang til oplysninger i den endelige rapport.

![MCCA – roller.](../media/compliance-manager-mcca-roles.png "MCCA-roller")

Undtagelser:
1. Brugerne kan ikke generere rapport for IP bortset fra afsnittet "Brug IRM Exchange Online".
2. Brugerne vil kunne generere rapport for IP adskilt fra afsnittet "Brug IRM Exchange Online".
3. Brugerne vil kunne generere rapport for IP adskilt fra afsnittet "Aktivér overholdelse af kommunikationsreglerne i O365".
4. Brugere vil ikke kunne generere rapport for IP bortset fra afsnittet "Aktivér overvågning Office 365".
5. Brugerne vil kunne generere rapport for IP adskilt fra afsnittet "Aktivér overvågning Office 365".

#### <a name="solutions-summary-section"></a>Sektionen Løsningsoversigt

Afsnittet **Løsningsoversigt** i rapporten giver en oversigt over de forbedringshandlinger, din organisation kan udføre i Overholdelsesstyring for at forbedre din overholdelsesoverholdelse.

![MCCA – løsningsoversigt.](../media/compliance-manager-mcca-solutions.png "Skærmbilledet MCCA Solutions Summary")

MCCA evaluerer dine aktuelle konfigurationer i forhold til de anbefalede forbedringshandlinger i Overholdelsesstyring. Enhver forbedringshandling, der identificeres af MCCA-værktøjet som havende opmærksomhed, vil blive vist i dette afsnit.

Ud for hver Microsoft-løsning er der farvekodede felter, der angiver antallet af elementer, der svarer til forbedringshandlinger i Overholdelsesstyring. Handlingerne er opdelt i tre statustilstande:

- **OK**: De handlinger, der opfylder anbefalede betingelser og ikke kræver nogen opmærksomhed på nuværende tidspunkt
- **Forbedring**: Handlinger, der kræver opmærksomhed
- **Anbefaling**: handlinger, der ikke kræver opmærksomhed, men for hvilke vi anbefaler bedste fremgangsmåder
 
Markér et felt for at få vist forbedringer og anbefalinger.

**Elementer med status for forbedring**

Vælg rullemenuen ud for **forbedringsnavnet** til højre for forbedringshandlingen. Du får vist en hurtig oversigt over og detaljer om dine aktuelle indstillinger og de anbefalede forbedringshandlinger. Oversigten indeholder direkte links til Overholdelsesstyring, den gældende løsning i Microsoft 365 Overholdelsescenter og relevant dokumentation.

Når du klikker på linket Overholdelsesstyring, kommer du til en filtreret visning af alle forbedringshandlingerne inden for den pågældende løsning, som du endnu ikke har implementeret. Derfra kan du se antallet af point, du kan opnå for at øge din overholdelsesscore [, de](compliance-score-calculation.md) bedømmelser, de gælder for, samt de gældende bestemmelser og certificeringer.

For DLP er der en **Afhjælpningsscript-knap** , der giver dig et forudgenereret PowerShell-script, der er baseret på, hvad der anbefales. Du kan kopiere og indsætte den direkte i din PowerShell-konsol. Det opretter en DLP-politik i testtilstand

**Elementer med statussen Anbefaling**

Vælg rullemenuen ud for etiketten **Anbefaling til** højre for forbedringshandlingen. Du får vist en oversigt over organisationens aktuelle Microsoft 365, der er relateret til forbedringshandlingen, samt anbefalede bedste fremgangsmåder.

## <a name="resources"></a>Ressourcer

Du kan finde mere detaljerede oplysninger om installation, konfiguration og brug af MCCA i [README-vejledningen på GitHub](https://github.com/OfficeDev/MCCA#overview) (ingen GitHub konto påkrævet).

Hvis du vil have mere Windows PowerShell om [powershell-dokumentationen, skal du starte med Sådan bruger du PowerShell-dokumentationen](/powershell/scripting/how-to-use-docs). Se også [Starte Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
