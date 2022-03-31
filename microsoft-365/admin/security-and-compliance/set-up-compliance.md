---
title: Forøg trusselsbeskyttelse til Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Konfigurer overholdelsesfunktioner for at forhindre datatab og hjælpe med at beskytte dine og dine kunders følsomme oplysninger.
ms.openlocfilehash: 69960c4f158a30d9d47d749ed1e7eb2d2d74f430
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63600951"
---
# <a name="set-up-compliance-features"></a>Konfigurer overholdelsesfunktioner

Dine Microsoft 365 Business Premium leveres med funktioner til beskyttelse af dine data og enheder og hjælper dig med at beskytte dine og dine kunders følsomme oplysninger.

## <a name="watch-set-up-dlp-features"></a>Se: Konfigurer DLP-funktioner

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Politikker til forebyggelse af datatab hjælper med at identificere og beskytte virksomhedens følsomme oplysninger, f.eks. CPR-numre eller medicinske journaler.

1. For at komme i gang skal [du gå til Administration](https://admin.microsoft.com) og vælge **Konfiguration**.
1. Rul ned **til Konfigurer forebyggelse af datatab**, og vælg **derefter** Vis og derefter **Administrer**.
1. Hvis du vil redigere en politik, skal du markere den, **vælge Rediger politik** og derefter vælge, hvad du vil ændre. Vælg f.eks Placeringer **for at ændre** , hvad der bliver scannet.
1. Hvis du vil oprette en ny politik, skal du **vælge Opret en politik**.
1. Du kan oprette en brugerdefineret politik eller starte med en skabelon. Hvis du f.eks. vil oprette en HIPAA-politik, skal du vælge skabelonen for medicin og sundhed og derefter vælge **US Health Insurance Act (HIPAA)**. Vælg **Næste**.
1. Gennemse dine indstillinger, og vælg **Opret**. Når din politik træder i kraft, blokeres mails, der indeholder de beskrevne følsomme oplysninger, og den afsender, der forsøgte at sende disse oplysninger, får vist en advarsel.

Se [Opret en DLP-politik ud](../../compliance/create-a-dlp-policy-from-a-template.md) fra en skabelon for et eksempel på, hvordan du konfigurerer en politik for at beskytte mod tab af personlige data. 
  
DLP leveres med mange klar-til-brug-politikskabeloner til mange forskellige lande/områder. Det kan f.eks. være Australien Financial Data, Canada Personal Information Act, USA Financial Data osv. Se [Hvad DLP-politikskabelonerne indeholder](../../compliance/what-the-dlp-policy-templates-include.md) for at få en komplet liste. Alle disse skabeloner kan aktiveres på samme måde som eksemplet på pii-skabelonen.
 
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Konfigurer mailopbevaring med Exchange Online-arkivering

 **Exchange Online-arkivering licensfunktioner** er med til at opretholde overholdelse og lovmæssige standarder ved at bevare mailindhold til eDiscovery. Det er også med til at reducere risikoen, hvis der er en advokatsag, og giver en metode til at gendanne data efter en sikkerhedsbrist, eller når du har brug for at gendanne slettede elementer. Du kan bruge retslig tilbageholdelse for at bevare hele en brugers indhold, eller du kan bruge opbevaringspolitikker til at tilpasse det, du vil bevare.
  
**Retslig venteposition:** Du kan bevare alt postkasseindhold, herunder slettede elementer, ved at sætte en brugers hele postkassen i venteposition. 
    
Sådan placerer du en postkasse i retslig venteposition i Administration:
    
1. I venstre navigationslinje skal du gå **til Aktive** \> **brugere for brugere**.
    
2. Vælg en bruger, hvis postkasse du vil placere i retslig venteposition. I brugerruden skal du udvide **Mailindstillinger**, og ud for **Flere indstillinger** skal du **vælge Rediger Exchange egenskaber**.
    
3. På brugerens postkasseside skal du vælge ** postkassefunktioner ** i venstre navigationslinje og derefter vælge linket Aktivér  under Retslig **venteposition**.
    
4. I dialogboksen **retslig venteposition** kan du angive varigheden af retslig venteposition i **feltet Varighed af retslig venteposition** . Lad feltet være tomt, hvis du vil placere et uendeligt sæt. Du kan også tilføje noter og dirigere ejeren af postkassen til et websted, som du muligvis skal forklare mere om retslig venteposition. \>**Gem**.
    
**Opbevaring:** Du kan aktivere brugerdefinerede opbevaringspolitikker, f.eks. for at bevare i et bestemt tidsrum eller slette indhold permanent i slutningen af en opbevaringsperiode. Du kan få mere at vide [under Oversigt over opbevaringspolitikker](../../compliance/retention.md).

## <a name="watch-set-up-sensitivity-labels"></a>Se: Konfigurer følsomhedsmærkater

Følsomhedsmærkater omfatter Azure Information Protection (AIP) Plan 1 og hjælper dig med at klassificere og eventuelt beskytte dine dokumenter og mails ved at anvende mærkater. Etiketter kan anvendes automatisk af administratorer, der definerer regler og betingelser, manuelt af brugerne eller ved hjælp af en kombination, hvor brugerne får anbefalinger.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

1. Vælg [Overholdelsesadministration](https://admin.microsoft.com) i Administration.
1. Vælg **Klassificering** og derefter **Følsomhedsmærkater**.
1. Vælg **Opret en etiket**, og når advarslen vises, skal du vælge **Ja**.
1. Gennemse dine indstillinger, og vælg **Opret**. Din etiket er blevet oprettet. Gentag denne proces for eventuelle yderligere etiketter, du ønsker.
1. Som standard vises etiketter i Office i følgende rækkefølge: **Fortrolig****, Intern** og **Offentlig**. Hvis du vil ændre rækkefølgen, skal du for hver etiket vælge de tre prik (flere handlinger) og derefter flytte navnet op eller ned. Tilladelser vises typisk fra det laveste til det højeste tilladelsesniveau.
1. Gennemse dine indstillinger, og vælg derefter **Publicer**.

For at dine etiketter skal fungere, skal hver enkelt bruger downloade Den samlede Azure Information Protection-etiketklient. Søg efter filer **påAzinfoProtection_UL.exe**, hent den derefter fra Microsoft Download Center, og kør den på dine brugeres computere.

Næste gang du åbner en Office-app f.eks. Word, kan du se de følsomhedsmærkater, der er blevet oprettet. Hvis du vil ændre eller anvende en etiket, skal du vælge Følsomhed og vælge en mærkat.

### <a name="install-the-azure-information-protection-client-manually"></a>Installer Azure Information Protection-klienten manuelt

Sådan installeres AIP-klienten manuelt:

1. Download **AzinfoProtection_UL.exe** Microsoft [Download Center](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Du kan kontrollere, at installationen virkede ved at få vist et Word-dokument og sørge for, **at indstillingen Følsomhed** er tilgængelig på **fanen** Hjem.
<br/>![Rullelisten Beskyttelse i et Word-dokument.](../../media/word-sensitivity.png)

Du kan finde flere oplysninger [under Installere klienten](/azure/information-protection/infoprotect-tutorial-step3).