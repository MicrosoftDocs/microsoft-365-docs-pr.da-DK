---
title: Få vist rapporter til forebyggelse af datatab
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
description: Brug DLP-rapporterne i Office 365 til at få vist antallet af DLP-politik match, tilsidesættelser eller falske positive og se, om de er mest populære over tid.
ms.openlocfilehash: cbf03a4d981d4b37bd22db8fa08c728b77318ddf
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63589156"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Få vist rapporter til forebyggelse af datatab

Når du har oprettet dine politikker til forebyggelse af datatab (DLP), skal du kontrollere, at de virker efter hensigten, og hjælpe dig med at overholde reglerne. Med DLP-rapporterne i Security &amp; Compliance Center kan du hurtigt få vist:
  
- **DLP-politik matches** Denne rapport viser antallet af DLP-politik match over tid. Du kan filtrere rapporten efter dato, placering, politik eller handling. Du kan bruge denne rapport til at: 
    
  - Finjuster eller tilpas dine DLP-politikker, mens du kører dem i testtilstand. Du kan få vist den bestemte regel, der matcher indholdet.
    
  - Fokuser på bestemte tidsperioder, og forstå årsagerne til stigninger i spidsbelastninger og tendenser.
    
  - Opdag forretningsprocesser, der overtræder din organisations DLP-politikker.
    
  - Forstå eventuelle forretningsmæssige konsekvenser af DLP-politikkerne ved at se, hvilke handlinger der anvendes på indhold.
    
  - Kontrollér overholdelse af en bestemt DLP-politik ved at vise eventuelle matches for den pågældende politik.
    
  - Få vist en liste over de mest populære brugere og gentage brugere, der bidrager til hændelser i organisationen.
    
  - Få vist en liste over de vigtigste typer af følsomme oplysninger i organisationen.
    
- **DLP-hændelser** Denne rapport viser også politik match over tid, f.eks. rapporten om match af politik. Men rapporten med match til politikken viser match på et regelniveau. Hvis en mail f.eks. matcher tre forskellige regler, viser politikken tre forskellige linjeelementer. I modsætning hertil viser hændelsesrapporten matches på et elementniveau; Hvis en mail f.eks. matcher tre forskellige regler, viser hændelsesrapporten et enkelt linjeelement for det pågældende indholdselement. 
    
  Da antallet af rapporter sammenlægges på en anden måde, er rapporten over politikoverensstemmelse bedre til at identificere match med bestemte regler og finjustere DLP-politikker. Rapporten over hændelser er bedre til at identificere bestemte dele af indhold, der er problematisk for dine DLP-politikker.
    
- **Falske DLP-positive og -tilsidesættelser** Hvis din DLP-politik tillader brugere at tilsidesætte den eller rapportere en falsk positiv, viser denne rapport antallet af sådanne forekomster over tid. Du kan filtrere rapporten efter dato, placering eller politik. Du kan bruge denne rapport til at: 
    
  - Finjuster eller finjuster dine DLP-politikker ved at se, hvilke politikker der har et stort antal falske positive.
    
  - Få vist begrundelserne, som er indsendt af brugere, når de løser et politiktip ved at tilsidesætte politikken.
    
  - Find ud af, hvor DLP-politikker er i konflikt med gyldige forretningsprocesser ved at foretage et stort antal brugertilsidesættelser.
    
Alle DLP-rapporter kan vise data fra den seneste fire måneders periode. Det kan tage op til 24 timer, før de nyeste data vises i rapporterne.
  
Du kan finde disse rapporter i Dashboard for Security &amp; Compliance **Center-rapporter** \> \>.
  
![Rapport over DLP-politik match.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)
  
## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Få vist den begrundelse, der er indsendt af en bruger for en tilsidesættelse

Hvis din DLP-politik tillader brugere at tilsidesætte den, kan du bruge rapporten falsk positiv og tilsidesætte til at få vist den tekst, der er indsendt af brugere, i politiktip.
  
![Justeringsfelt i detaljer for rapporten DLP falsk positiv og tilsidesæt.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)
  
## <a name="take-action-on-insights-and-recommendations"></a>Tag skridtet videre med viden og anbefalinger

Rapporter kan vise indsigt og anbefalinger, hvor du kan klikke på det røde advarselsikon for at få vist detaljer om potentielle problemer og gøre noget ved det.
  
![Klik på et Insights-ikon for at se detaljer og handlinger, du skal udføre.](../media/51782036-7299-4960-8175-75c2b1637159.png)
  
## <a name="permissions-for-dlp-reports"></a>Tilladelser for DLP-rapporter

Hvis du vil have vist DLP-rapporter & Security & Compliance Center, skal du have tildelt:

- **Sikkerhedslæserrolle** <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Som standard er denne rolle tildelt rollegrupperne Organisationsadministration og Sikkerhedslæser i Exchange Administration.

- **Kun visningsstyring af DLP-overholdelse** i sikkerheds- & Overholdelsescenter. Denne rolle er som standard tildelt rollegrupperne Overholdelsesadministrator, Organisationsadministration, Sikkerhedsadministrator og Sikkerhedslæser i Sikkerhedscenter & Overholdelsescenter.

- **Rollen Kun visningsmodtagere** <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Som standard er denne rolle tildelt rollegrupperne Styring af overholdelse, Organisationsadministration og View-Only Organisationsadministration i Exchange Administration.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Find cmdlet'er til DLP-rapporterne

Hvis du vil bruge de fleste af cmdlet'er til Security &amp; Compliance Center, skal du:
  
1. [Forbind til sikkerhed &amp; Overholdelsescenter ved hjælp af Remote PowerShell](/powershell/exchange/connect-to-scc-powershell)
    
2. Brug en af disse [Security &amp; Compliance Center-cmdlet'er](/powershell/exchange/exchange-online-powershell)
    
Men DLP-rapporter skal trække data fra Office 365, herunder Exchange Online. Af denne grund er cmdlet'er til DLP-rapporterne tilgængelige i Exchange Online Powershell – ikke i Security &amp; Compliance Center Powershell. For at bruge cmdlet'er til DLP-rapporterne skal du derfor:
  
1. [Forbind at Exchange Online ved hjælp af Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. Brug en af disse cmdlet'er til DLP-rapporterne:
    
      - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
    
      - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
