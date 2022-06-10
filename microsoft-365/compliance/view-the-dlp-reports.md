---
title: Få vist rapporterne til forebyggelse af datatab
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/7/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Brug DLP-rapporterne i Office 365 til at få vist antallet af DLP-politikforekomster, -tilsidesættelser eller falske positiver, og se, om de er opad- eller nedadgående over tid.
ms.openlocfilehash: b264a0e0b76397be99d7586ac793dac501b6672e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011609"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Få vist rapporterne til forebyggelse af datatab

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har oprettet dine DLP-politikker (Forebyggelse af datatab i Microsoft Purview), skal du bekræfte, at de fungerer efter hensigten og hjælper dig med at overholde angivne standarder. Med DLP-rapporterne på Microsoft Purview-overholdelsesportalen kan du hurtigt få vist:

- **DLP-politikforekomster** Denne rapport viser antallet af DLP-politikforekomster over tid. Du kan filtrere rapporten efter dato, placering, politik eller handling. Du kan bruge denne rapport til at:

  - Tilpas eller afgræns dine DLP-politikker, når du kører dem i testtilstand. Du kan få vist den specifikke regel, der matcher indholdet.

  - Fokuser på specifikke tidsperioder, og forstå årsagerne til stigninger og tendenser.

  - Find forretningsprocesser, der overtræder organisationens DLP-politikker.

  - Forstå enhver forretningsvirkning af DLP-politikkerne ved at se, hvilke handlinger der anvendes på indhold.

  - Kontrollér overholdelse af en bestemt DLP-politik ved at vise eventuelle match for den pågældende politik.

  - Få vist en liste over de mest populære brugere, og gentag brugere, der bidrager til hændelser i din organisation.

  - Få vist en liste over de vigtigste typer følsomme oplysninger i din organisation.

- **DLP-hændelser** Denne rapport viser også politikforekomster over tid, ligesom politikken matcher rapporten. Politikken stemmer dog overens med, at rapporten viser matches på regelniveau. Hvis en mail f.eks. matchede tre forskellige regler, viser rapporten, der stemmer overens med politikken, tre forskellige linjeelementer. Rapporten over hændelser viser derimod matches på elementniveau. Hvis en mail f.eks. matchede tre forskellige regler, viser hændelsesrapporten et enkelt linjeelement for den pågældende del af indholdet.

  Da antallet af rapporter aggregeres forskelligt, er rapporten med politikker bedre til at identificere overensstemmelser med bestemte regler og finjustere DLP-politikker. Hændelsesrapporten er bedre til at identificere bestemte indholdsdele, der er problematiske for dine DLP-politikker.

- **DLP-falske positiver og tilsidesættelser** Hvis din DLP-politik giver brugerne mulighed for at tilsidesætte den eller rapportere en falsk positiv, viser denne rapport en optælling af sådanne forekomster over tid. Du kan filtrere rapporten efter dato, placering eller politik. Du kan bruge denne rapport til at:

  - Tilpas eller forfin dine DLP-politikker ved at se, hvilke politikker der medfører et højt antal falske positiver.

  - Få vist de begrundelser, som brugerne har sendt, når de løser et politiktip, ved at tilsidesætte politikken.

  - Find ud af, hvor DLP-politikker er i konflikt med gyldige forretningsprocesser ved at pådrage sig et stort antal brugertilsidesættelser.

Alle DLP-rapporter kan vise data fra den seneste firemåneders tidsperiode. Det kan tage op til 24 timer, før de nyeste data vises i rapporterne.

Du kan finde disse rapporter på **Microsoft** Purview-overholdelsesportalen \> **Dashboard til rapporter**\>.

![DLP-politik stemmer overens med rapporten.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)

## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Få vist den begrundelse, der er sendt af en bruger for en tilsidesættelse

Hvis din DLP-politik giver brugerne mulighed for at tilsidesætte den, kan du bruge rapporten falsk positiv og tilsidesættelse til at få vist den tekst, der er sendt af brugerne, i politiktip.

![Berettigelsesfelt i detaljer om DLP-rapporten falsk positiv og tilsidesættelse af rapport.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)

## <a name="take-action-on-insights-and-recommendations"></a>Udfør en handling på baggrund af indsigt og anbefalinger

Rapporter kan vise indsigt og anbefalinger, hvor du kan klikke på det røde advarselsikon for at få vist detaljer om potentielle problemer og udføre en eventuel afhjælpningshandling.

![Klik på et indsigtsikon for at få vist detaljer og handlinger, der skal udføres.](../media/51782036-7299-4960-8175-75c2b1637159.png)

## <a name="permissions-for-dlp-reports"></a>Tilladelser til DLP-rapporter

Hvis du vil have vist DLP-rapporter i Security & Compliance Center, skal du være tildelt:

- **Rollen Sikkerhedslæser** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Denne rolle er som standard tildelt rollegrupperne Organisationsadministration og Sikkerhedslæser i Exchange Administration.

- **Vis kun rollen DLP Compliance Management** i Security & Compliance Center. Denne rolle tildeles som standard rollegrupperne Overholdelsesadministrator, Organisationsadministration, Sikkerhedsadministrator og Sikkerhedslæser i Security & Compliance Center.

- **Rollen Kun visningsmodtagere** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Denne rolle er som standard tildelt rollegrupperne Overholdelsesstyring, Organisationsadministration og View-Only Organisationsadministration i Exchange Administration.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Find cmdlet'erne til DLP-rapporterne

Hvis du vil bruge cmdlet'erne til DLP-rapportering, skal du gøre følgende:

1. [PowerShell Forbind til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell)

2. Brug disse cmdlet'er:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
   - [Get-DlpSiDetectionsReport](/powershell/module/exchange/get-dlpsidetectionsreport)

DLP-rapporter skal dog hente data fra hele Microsoft 365, herunder Exchange Online. Derfor er følgende cmdlet'er til DLP-rapporter tilgængelige i Exchange Online Powershell. Hvis du vil bruge cmdlet'erne til disse DLP-rapporter, skal du gøre følgende:

1. [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Brug disse cmdlet'er:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-MailDetailDlpPolicyReport](/powershell/module/exchange/get-maildetaildlppolicyreport)
