---
title: Kom i gang med at bruge simuleringskursus til angreb
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan lære at bruge simulering af angreb til at køre simulerede phishing- og adgangskodeangreb i deres Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2-organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 244d0ae912a5cc2dc163b62f44b44877c0318b88
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507405"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Kom i gang med at bruge simulering af angreb i Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Hvis din organisation har Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2, som omfatter funktioner til trusselsundersøgelse og [svar, kan](office-365-ti.md) du bruge simulering af angreb på Microsoft 365 Defender-portalen til at køre realistiske angrebsscenarier i organisationen. Disse simulerede angreb kan hjælpe dig med at identificere og finde følsomme brugere, før et rigtigt angreb påvirker din bundlinje. Læs denne artikel for at få mere at vide.

> [!NOTE]
> Kursus i angrebssimulering erstatter den gamle AngrebSv1-oplevelse, der var tilgængelig i Security & Compliance Center på **Threat management** \> **Attack eller** <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender, skal du gå til <https://security.microsoft.com>. Der findes kursus i simulering af angreb **under Mail- og samarbejdssimulering** \> **af angreb**. For at gå direkte til simuleringskursus for angreb skal du bruge <https://security.microsoft.com/attacksimulator>.

- Du kan finde flere oplysninger om tilgængeligheden af angrebssimuleringskursus på tværs Microsoft 365 forskellige abonnementer [Microsoft Defender for Office 365 beskrivelse af tjenesten](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Du skal have tildelt tilladelser **i Azure Active Directory,** før du kan udføre procedurerne i denne artikel. Du skal specifikt være medlem af en af følgende roller:
  - **Global Administrator**
  - **Sikkerhedsadministrator**
  - **Angrebssimuleringsadministratorer**<sup>\*</sup>: Opret og administrer alle aspekter af angrebssimuleringskampagner.
  - **Angrebsforfatter:**<sup>\*</sup> Opret angrebs-nyttedata, som en administrator kan starte på et senere tidspunkt.

  <sup>\*</sup>Tilføjelse af brugere til denne rolle i Microsoft 365 Defender-portalen understøttes ikke i øjeblikket.

  Du kan få mere at [vide under Tilladelser i Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) eller [Om administratorroller](../../admin/add-users/about-admin-roles.md).

- Der er ingen tilsvarende PowerShell-cmdlet'er til kursus i angrebssimulering.

- Angrebssimulering og kursusrelaterede data gemmes sammen med andre kundedata til Microsoft 365 tjenester. Du kan finde flere [oplysninger Microsoft 365 dataplaceringer](../../enterprise/o365-data-locations.md). Angrebssimulering er tilgængelig i følgende områder: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, PASCAL, CHE, NOR, ZAF, ARE og DEU.

  > [!NOTE]
  > NOR, ZAF, ARE og DEU er de nyeste tilføjelser. Alle funktioner undtagen rapporterede mailtelemetri vil være tilgængelige i disse områder. Vi arbejder på at aktivere dette og underretter vores kunder, så snart rapporterede mailtelemetri bliver tilgængelige.

- Pr. 15. juni 2021 findes der kursus i simulering af angreb GCC. Hvis din organisation har Office 365 G5 GCC eller Microsoft Defender for Office 365 (Plan 2) for Government, kan du bruge kursus i angrebssimulering på Microsoft 365 Defender-portalen til at køre realistiske angrebsscenarier i din organisation som beskrevet i denne artikel. Kursus om angrebssimulering er endnu ikke tilgængeligt i GCC High- eller DoD-miljøer.

> [!NOTE]
> Kursus om angrebssimulering tilbyder et undersæt af funktioner til E3-kunder som en prøveversion. Prøveversionen indeholder muligheden for at bruge en nyttelast ved indsamling af legitimationsoplysninger og muligheden for at vælge "ISA Phishing" eller "Mass Market Phishing"-kursusoplevelser. Ingen andre egenskaber er en del af E3-prøveversionen.

## <a name="simulations"></a>Simulering

*Phishing* er et generisk udtryk for mailangreb, der forsøger at stjæle følsomme oplysninger i meddelelser, der ser ud til at være fra legitime eller afsendere, der er tillid til. *Phishing* er en del af et undersæt af teknikker, vi klassificerer som _social engineering_.

I angrebssimuleringskursus er der flere typer af social engineering-teknikker tilgængelige:

- **Indsamling af legitimationsoplysninger**: En hacker sender modtageren en meddelelse, der indeholder en URL-adresse. Når modtageren klikker på URL-adressen, kommer modtageren til et websted, der typisk viser en dialogboks, hvor brugeren bliver bedt om at angive sit brugernavn og sin adgangskode. Destinationssiden er typisk tema til at repræsentere et velkendt websted for at opbygge tillid til brugeren.

- **Vedhæftet malware**: En hacker sender modtageren en meddelelse, der indeholder en vedhæftet fil. Når modtageren åbner den vedhæftede fil, køres en tilfældig kode (f.eks. en makro) på brugerens enhed for at hjælpe hackeren med at installere yderligere kode eller yderligere grave sig ind.

- **Link i vedhæftet** fil: Dette er en hybrid af en indsamling af legitimationsoplysninger. En hacker sender modtageren en meddelelse, der indeholder en URL-adresse i en vedhæftet fil. Når modtageren åbner den vedhæftede fil og klikker på URL-adressen, kommer modtageren til et websted, der typisk viser en dialogboks, hvor brugeren bliver bedt om at angive sit brugernavn og sin adgangskode. Destinationssiden er typisk tema til at repræsentere et velkendt websted for at opbygge tillid til brugeren.

- **Link til malware**: En hacker sender modtageren en meddelelse, der indeholder et link til en vedhæftet fil på et kendt websted til fildeling (f.eks. SharePoint Online eller Dropbox). Når modtageren klikker på URL-adressen, åbnes den vedhæftede fil, og der køres en vilkårlig kode (f.eks. en makro) på brugerens enhed for at hjælpe hackeren med at installere yderligere kode eller for at forskane sig selv.

- **Drive-by-url**: En hacker sender modtageren en meddelelse, der indeholder en URL-adresse. Når modtageren klikker på URL-adressen, kommer de til et websted, der forsøger at køre baggrundskode. Denne baggrundskode forsøger at indsamle oplysninger om modtageren eller anvende tilfældig kode på dennes enhed. Destinationswebstedet er typisk et velkendt websted, der er blevet kompromitteret eller en klon af et velkendt websted. Kendskab til webstedet hjælper med at overbevise brugeren om, at linket er sikkert at klikke på. Denne metode er også kendt som et _vandings hulangreb_.

> [!NOTE]
> Kontrollér tilgængeligheden af den simulerede url-adresse til phishing i dine understøttede webbrowsere, før du bruger URL-adressen i en phishingkampagne. Vi arbejder med mange leverandører af URL-omdømme til altid at tillade disse simulerings-URL-adresser, men vi har ikke altid fuld dækning (f.eks. Google Pengeskab Browsing). De fleste leverandører tilbyder vejledning, der gør det muligt altid at tillade bestemte URL-adresser (f.eks. <https://support.google.com/chrome/a/answer/7532419>).

De URL-adresser, der bruges af angrebssimuleringskursus, er beskrevet på følgende liste:

- <https://www.mcsharepoint.com>
- <https://www.attemplate.com>
- <https://www.doctricant.com>
- <https://www.mesharepoint.com>
- <https://www.officence.com>
- <https://www.officenced.com>
- <https://www.officences.com>
- <https://www.officentry.com>
- <https://www.officested.com>
- <https://www.prizegives.com>
- <https://www.prizemons.com>
- <https://www.prizewel.com>
- <https://www.prizewings.com>
- <https://www.shareholds.com>
- <https://www.sharepointen.com>
- <https://www.sharepointin.com>
- <https://www.sharepointle.com>
- <https://www.sharesbyte.com>
- <https://www.sharession.com>
- <https://www.sharestion.com>
- <https://www.templateau.com>
- <https://www.templatent.com>
- <https://www.templatern.com>
- <https://www.windocyte.com>

### <a name="create-a-simulation"></a>Opret en simulering

Du kan finde en trinvis vejledning i, hvordan du opretter og sender en ny simulering, [under Simulere et phishingangreb](attack-simulation-training.md).

### <a name="create-a-payload"></a>Opret en nyttedata

For at få en trinvis vejledning i, hvordan du opretter en nyttelast til brug i en simulering, skal du se Opret en [brugerdefineret nyttelast til simulering af angreb](attack-simulation-training-payloads.md).

### <a name="gaining-insights"></a>Få indsigt

For at få en trinvis vejledning i, hvordan du får indsigt i rapportering, skal du se [Få indsigt via simulering af angreb](attack-simulation-training-insights.md).

> [!NOTE]
> **Angrebskæder** bruger Pengeskab Links i Defender for Office 365 til sikkert at spore klikdata for URL-adressen i den meddelelse om nyttedata, der sendes til målrettede modtagere af en phishingkampagne, selvom indstillingen Spor brugerklik i Pengeskab Links-politikker er slået fra.
