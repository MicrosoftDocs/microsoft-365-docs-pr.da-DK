---
title: Kom i gang med at bruge kursus i angrebssimulering
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
description: Administratorer kan få mere at vide om, hvordan de bruger oplæring i simulering af angreb til at køre simulerede phishing- og adgangskodeangreb i deres Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2-organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 255d0f40cd360f2b4b3e5084f84989bdbe643319
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415612"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Kom i gang med at bruge oplæring i simulering af angreb i Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Hvis din organisation har Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2, som omfatter [funktioner til trusselsundersøgelse og svar](office-365-ti.md), kan du bruge oplæring i simulering af angreb på Microsoft 365 Defender portalen til at køre realistiske angrebsscenarier i din organisation. Disse simulerede angreb kan hjælpe dig med at identificere og finde sårbare brugere, før et reelt angreb påvirker bundlinjen. Læs denne artikel for at få mere at vide.

Se denne korte video for at få mere at vide om oplæring i simulering af angreb.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMhvB]

> [!NOTE]
> Oplæring i simulering af angreb erstatter den gamle Attack Simulator v1-oplevelse, der var tilgængelig i Security & Compliance Center på **Threat management** \> **Attack simulator** eller <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender-portalen, skal du gå til <https://security.microsoft.com>. Træning af simulering af angreb er tilgængelig på **e-mail og samarbejde** \> **Træning i simulering af angreb**. Hvis du vil gå direkte til Oplæring af simulering af angreb, skal du bruge <https://security.microsoft.com/attacksimulator>.

- Du kan få flere oplysninger om tilgængeligheden af oplæring i simulering af angreb på tværs af forskellige Microsoft 365 abonnementer i [Microsoft Defender for Office 365 tjenestebeskrivelse](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Du skal have tildelt tilladelser i **Azure Active Directory**, før du kan udføre procedurerne i denne artikel. Du skal især være medlem af en af følgende roller:
  - **Global administrator**
  - **Sikkerhedsadministrator**
  - Administratorer <sup>\*</sup>af **angrebssimulering**: Opret og administrer alle aspekter af angrebssimuleringskampagner.
  - Forfatter <sup>\*</sup>af **angrebsnyttedata**: Opret angrebsnyttedata, som en administrator kan starte senere.

  <sup>\*</sup>Tilføjelse af brugere til denne rolle i Microsoft 365 Defender-portalen understøttes ikke i øjeblikket.

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) eller [Om administratorroller](../../admin/add-users/about-admin-roles.md).

- Der er ingen tilsvarende PowerShell-cmdlet'er til oplæring i simulering af angreb.

- Simulering af angreb og oplæringsrelaterede data gemmes sammen med andre kundedata til Microsoft 365 tjenester. Du kan få flere oplysninger [under Microsoft 365 dataplaceringer](../../enterprise/o365-data-locations.md). Simulering af angreb er tilgængelig i følgende områder: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE og DEU.

  > [!NOTE]
  > NOR, ZAF, ARE og DEU er de seneste tilføjelser. Alle funktioner undtagen rapporteret mailtelemetri vil være tilgængelige i disse områder. Vi arbejder på at aktivere dette og giver vores kunder besked, så snart den rapporterede mailtelemetri bliver tilgængelig.

- Fra og med den 15. juni 2021 er træning til simulering af angreb tilgængelig i GCC. Hvis din organisation har Office 365 G5-GCC eller Microsoft Defender for Office 365 (Plan 2) for Government, kan du bruge oplæring i simulering af angreb på portalen Microsoft 365 Defender til at køre realistiske angrebsscenarier i din organisation, som beskrevet i denne artikel. Oplæring i simulering af angreb er endnu ikke tilgængelig i GCC high- eller dod-miljøer.

> [!NOTE]
> Oplæring i simulering af angreb tilbyder en delmængde af funktioner til E3-kunder som en prøveversion. Prøveversionen indeholder muligheden for at bruge nyttedata fra Credential Harvest og muligheden for at vælge 'ISA Phishing' eller 'Mass Market Phishing'-træningsoplevelser. Ingen andre funktioner er en del af E3-prøveversionen.

## <a name="simulations"></a>Simuleringer

*Phishing* er en generisk betegnelse for mailangreb, der forsøger at stjæle følsomme oplysninger i meddelelser, der ser ud til at være fra legitime afsendere eller afsendere, der er tillid til. *Phishing* er en del af en delmængde af teknikker, vi klassificerer som _social engineering_.

I Træning af simulering af angreb er der flere typer af social engineering-teknikker tilgængelige:

- **Høst af legitimationsoplysninger**: En hacker sender modtageren en meddelelse, der indeholder en URL-adresse. Når modtageren klikker på URL-adressen, føres vedkommende til et websted, der typisk viser en dialogboks, hvor brugeren bliver bedt om at angive sit brugernavn og sin adgangskode. Destinationssiden er typisk tema til at repræsentere et velkendt websted for at skabe tillid til brugeren.

- **Vedhæftet malware**: En hacker sender modtageren en meddelelse, der indeholder en vedhæftet fil. Når modtageren åbner den vedhæftede fil, køres der vilkårlig kode (f.eks. en makro) på brugerens enhed for at hjælpe hackeren med at installere yderligere kode eller yderligere forgrene sig.

- **Link i vedhæftet fil**: Dette er en hybrid af en høst af legitimationsoplysninger. En hacker sender modtageren en meddelelse, der indeholder en URL-adresse i en vedhæftet fil. Når modtageren åbner den vedhæftede fil og klikker på URL-adressen, føres vedkommende til et websted, der typisk viser en dialogboks, hvor brugeren bliver bedt om at angive sit brugernavn og sin adgangskode. Destinationssiden er typisk tema til at repræsentere et velkendt websted for at skabe tillid til brugeren.

- **Link til malware**: En hacker sender modtageren en meddelelse, der indeholder et link til en vedhæftet fil på et velkendt fildelingswebsted (f.eks. SharePoint Online eller Dropbox). Når modtageren klikker på URL-adressen, åbnes den vedhæftede fil, og der køres vilkårlig kode (f.eks. en makro) på brugerens enhed for at hjælpe hackeren med at installere yderligere kode eller yderligere at fortrætte sig selv.

- **Drive-by-URL**: En hacker sender modtageren en meddelelse, der indeholder en URL-adresse. Når modtageren klikker på URL-adressen, føres vedkommende til et websted, der forsøger at køre baggrundskode. Denne baggrundskode forsøger at indsamle oplysninger om modtageren eller installere vilkårlig kode på deres enhed. Destinationswebstedet er typisk et velkendt websted, der er blevet kompromitteret, eller en klon af et velkendt websted. Kendskab til hjemmesiden hjælper med at overbevise brugeren om, at linket er sikkert at klikke. Denne teknik er også kendt som et _vanding hul angreb_.

> [!NOTE]
> Kontrollér tilgængeligheden af den simulerede PHISHING-URL-adresse i dine understøttede webbrowsere, før du bruger URL-adressen i en phishing-kampagne. Selvom vi arbejder med mange leverandører af URL-omdømme for altid at tillade disse simulerings-URL-adresser, har vi ikke altid fuld dækning (f.eks. Google Pengeskab Browsing). De fleste leverandører indeholder en vejledning, der giver dig mulighed for altid at tillade bestemte URL-adresser (f.eks. <https://support.google.com/chrome/a/answer/7532419>).

De URL-adresser, der bruges til oplæring af simulering af angreb, er beskrevet på følgende liste:

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

Hvis du vil have en trinvis vejledning i, hvordan du opretter og sender en ny simulering, skal du se [Simuler et phishing-angreb](attack-simulation-training.md).

### <a name="create-a-payload"></a>Opret en nyttedata

Hvis du vil have en trinvis vejledning i, hvordan du opretter en nyttedata til brug i en simulering, skal du se [Opret en brugerdefineret nyttedata til oplæring i simulering af angreb](attack-simulation-training-payloads.md).

### <a name="gaining-insights"></a>Få indsigt

Hvis du vil have en trinvis vejledning i, hvordan du får indsigt i rapportering, skal du se [Få indsigt via oplæring i simulering af angreb](attack-simulation-training-insights.md).

> [!NOTE]
> Angrebssimulator bruger Pengeskab Links i Defender for Office 365 til sikkert at spore klikdata for URL-adressen i den nyttedatameddelelse, der sendes til målrettede modtagere af en phishing-kampagne, selvom indstillingen **Spor bruger klik** i Pengeskab Links-politikker er slået fra.
