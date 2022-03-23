---
title: Trusselsundersøgelse & svarmuligheder – Microsoft Defender til Office 365 Plan 2
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om muligheder for trusselsundersøgelse og svar i Microsoft Defender Office 365 Plan.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ce7541010999b87e49880446594a79593a16a30a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587320"
---
# <a name="threat-investigation-and-response"></a>Trusselsundersøgelse og -svar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)


Funktionalitet for trusselsundersøgelse og svar i [Microsoft Defender for Office 365 hjælpe](defender-for-office-365.md) sikkerhedsanalytikere og administratorer med at beskytte deres Microsoft 365 for virksomhedsbrugere ved at:

- Gør det nemt at identificere, overvåge og forstå cyberangreb.
- Hjælper dig med hurtigt at håndtere trusler Exchange Online, SharePoint Online, OneDrive for Business og Microsoft Teams.
- Give indsigt og viden for at hjælpe sikkerhedshandlinger med at forhindre cyberangreb mod deres organisation.
- Anvend [automatiseret undersøgelse og svar Office 365](automated-investigation-response-office.md) svar på vigtige mailbaserede trusler.

Trusselsundersøgelse og svarmuligheder giver indsigt i trusler og relaterede svarhandlinger, der findes i Microsoft 365 Defender-portalen. Denne indsigt kan hjælpe organisationens sikkerhedsteam med at beskytte brugerne mod mail- eller filbaserede angreb. Funktionerne hjælper med at overvåge signaler og indsamle data fra flere kilder, f.eks. brugeraktivitet, godkendelse, mail, kompromitterede pc'er og sikkerhedshændelser. Forretnings beslutningstagere og dit sikkerhedsteam kan bruge disse oplysninger til at forstå og reagere på trusler mod din organisation og beskytte din immaterielle ejendom.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Blive fortrolig med værktøjer til trusselsundersøgelse og svar

Funktionalitet til trusselsundersøgelse og svar i Microsoft 365 Defender at er <https://security.microsoft.com> et sæt værktøjer og arbejdsprocesser for svar, der omfatter:

- [Stifinder](#explorer)
- [Hændelser](#incidents)
- [Kursus i angrebssimulering](attack-simulation-training.md)
- [Automatiseret undersøgelse og svar](automated-investigation-response-office.md)

### <a name="explorer"></a>Stifinder

Brug [Stifinder (og](threat-explorer.md) registreringer i realtid) til at analysere trusler, se mængden af angreb over tid og analysere data fra trusselsfamilier, hackerinfrastruktur og meget mere. Stifinder (også kaldet Threat Explorer) er udgangspunktet for en sikkerhedsanalytikers undersøgelsesarbejdsproces.

![Trusselsstifinder.](../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)

Hvis du vil have vist og bruge denne rapport Microsoft 365 Defender på , skal du <https://security.microsoft.com>gå **til & med Stifinder til** \> **samarbejde**. Du kan også gå direkte til **Stifinder-siden** ved hjælp af <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Threat Intelligence-forbindelse

Denne funktion er kun tilgængelig, hvis du har et aktivt Office 365 E5-abonnement eller tilføjelsesprogrammet Threat Intelligence. Du kan finde flere oplysninger Office 365 Enterprise siden med E5-produkter.

Når du slår denne funktion til, vil du kunne inkorporere data fra Microsoft Defender til Office 365 i Microsoft 365 Defender for at udføre en omfattende sikkerhedsundersøgelse på tværs af Office 365 postkasser og Windows enheder.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

Hvis du vil modtage kontekstafhængig enhedsintegration i Office 365 Threat Intelligence, skal du aktivere indstillingerne for Defender for Endpoint i dashboardet Security & Compliance.

### <a name="incidents"></a>Hændelser

Brug listen Hændelser (dette kaldes også undersøgelser) for at få vist en liste over sikkerhedshændelser for fly. Hændelser bruges til at spore trusler som f.eks. mistænkelige e-mail-meddelelser og til at foretage yderligere undersøgelser og afhjælpning.

![Liste over aktuelle trusselshændelser i Office 365.](../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)

Hvis du vil have vist listen over aktuelle hændelser for din organisation i Microsoft 365 Defender-portalen<https://security.microsoft.com>, skal du gå til **Hændelser & hændelser** \> **.** Eller du kan bruge til at **gå direkte til siden** Hændelser <https://security.microsoft.com/incidents>.

![I Security & Compliance Center skal du vælge Threat management \> Review.](../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png)

### <a name="attack-simulation-training"></a>Kursus i angrebssimulering

Brug angrebssimuleringskurser til at konfigurere og køre realistiske cyberangreb i din organisation og identificere følsomme personer, før et rigtigt cyberangreb påvirker din virksomhed. Du kan få mere at vide under [Simulere et phishingangreb](attack-simulation-training.md).

Hvis du vil have vist og bruge denne Microsoft 365 Defender på <https://security.microsoft.com>, skal du gå til Mail & **samarbejdeAttack-simuleringskursus** > . Du kan også gå direkte til siden til **simulering af angreb** ved at bruge <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>Automatiseret undersøgelse og svar

Brug automatiserede undersøgelses- og svarfunktioner (AIR) til at spare tid og besvær med at korrelere indhold, enheder og personer, der er i risiko for trusler i din organisation. AIR-processer kan starte, når der udløses bestemte beskeder, eller når sikkerhedsteamet starter. Du kan få mere at vide [ved at se automatiseret undersøgelse og svar Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Threat intelligence-widgets

Som en del af microsoft Defender for Office 365 Plan 2 kan sikkerhedsanalytikere gennemgå oplysninger om en kendt trussel. Dette er nyttigt til at afgøre, om der er yderligere forhindrende målinger/trin, der kan tages for at beskytte brugerne.

![Sikkerhedstendenser viser oplysninger om de seneste trusler.](../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png)

## <a name="how-do-we-get-these-capabilities"></a>Hvordan får vi disse egenskaber?

Microsoft 365 trusselsundersøgelse og svarfunktioner er inkluderet i Microsoft Defender til Office 365 Plan 2, som er inkluderet i Enterprise E5 eller som et tilføjelsesprogrammet til visse abonnementer. Du kan få mere at [vide under Defender Office 365 Plan 1 og Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>Påkrævede roller og tilladelser

Microsoft Defender til Office 365 bruger rollebaseret adgangskontrol. Tilladelser tildeles gennem bestemte roller i Azure Active Directory, Microsoft 365 Administration eller Microsoft 365 Defender portalen.

> [!TIP]
> Selvom nogle roller, f.eks. sikkerhedsadministrator, kan tildeles i Microsoft 365 Defender, kan du overveje at bruge enten den Microsoft 365 Administration eller Azure Active Directory i stedet. Du kan finde oplysninger om roller, rollegrupper og tilladelser i følgende ressourcer:
>
> - [Tilladelser i Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md)
> - [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)

<br>

****

|Aktivitet|Roller og tilladelser|
|---|---|
|Brug dashboardet til & til håndtering af sikkerhedsrisiko (eller det [nye dashboard Sikkerhed)](security-dashboard.md) <p> Få vist oplysninger om de seneste eller aktuelle trusler|Et af følgende: <ul><li>**Global Administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Brug [Stifinder (og registreringer i realtid)](threat-explorer.md) til at analysere trusler|Et af følgende: <ul><li>**Global Administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Få vist hændelser (også kaldet undersøgelser) <p> Føj mails til en hændelse|Et af følgende: <ul><li>**Global Administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Udløse mailhandlinger i en hændelse <p> Find og slet mistænkelige mails|Et af følgende: <ul><li>**Global Administrator**</li><li>**Sikkerhedsadministrator** plus **rollen Søg og Tøm**</li></ul> <p> **Rollerne Global** administrator **og sikkerhedsadministrator** kan tildeles i enten Azure Active Directory (<https://portal.azure.com>) eller Microsoft 365 Administration (<https://admin.microsoft.com>). <p> Rollen **Søg og tøm** skal være tildelt i & **i** samarbejdsrollerne i Microsoft 36 Defender-portalen (<https://security.microsoft.com>).|
|Integrer Microsoft Defender Office 365 Plan 2 med Microsoft Defender til Slutpunkt <p> Integrer Microsoft Defender Office 365 Plan 2 med en SIEM-server|Enten den **globale administrator** eller den **sikkerhedsadministratorrolle**, der er tildelt i Azure Active Directory (<https://portal.azure.com>) eller Microsoft 365 Administration (<https://admin.microsoft.com>). <p> --- **plus** --- <p> En passende rolle, der er tildelt i flere programmer ([f.eks. Microsoft Defender Security Center](/windows/security/threat-protection/microsoft-defender-atp/user-roles) eller din SIEM-server).|
|

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om Threat Trackers – nye og be noterede](threat-trackers.md)
- [Find og undersøg skadelige mails, der blev leveret (Office 365 trusselsundersøgelse og -svar)](investigate-malicious-email-that-was-delivered.md)
- [Integrer Office 365 trusselsundersøgelse og svar med Microsoft Defender til Slutpunkt](integrate-office-365-ti-with-mde.md)
- [Simulere et phishingangreb](attack-simulation-training.md)
