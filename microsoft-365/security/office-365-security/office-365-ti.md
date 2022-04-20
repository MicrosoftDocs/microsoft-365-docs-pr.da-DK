---
title: Trusselsundersøgelse & svarfunktioner – Microsoft Defender for Office 365 Plan 2
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
description: Få mere at vide om trusselsundersøgelses- og svarfunktioner i Microsoft Defender for Office 365 Plan.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c972a42730f4d21b73227a8b8a9900223109d590
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972029"
---
# <a name="threat-investigation-and-response"></a>Trusselsundersøgelse og -svar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Trusselsundersøgelses- og svarfunktioner i [Microsoft Defender for Office 365](defender-for-office-365.md) hjælpe sikkerhedsanalytikere og administratorer med at beskytte deres organisations Microsoft 365 for erhvervsbrugere ved at:

- Gør det nemt at identificere, overvåge og forstå cyberangreb.
- Hjælp til hurtigt at håndtere trusler i Exchange Online, SharePoint Online, OneDrive for Business og Microsoft Teams.
- At give indsigt og viden for at hjælpe sikkerhedshandlinger med at forhindre cyberangreb mod deres organisation.
- Anvender [automatiseret undersøgelse og svar i Office 365](automated-investigation-response-office.md) for kritiske mailbaserede trusler.

Trusselsundersøgelses- og svarfunktioner giver indsigt i trusler og relaterede svarhandlinger, der er tilgængelige på Microsoft 365 Defender-portalen. Denne indsigt kan hjælpe din organisations sikkerhedsteam med at beskytte brugerne mod mail- eller filbaserede angreb. Funktionerne hjælper med at overvåge signaler og indsamle data fra flere kilder, f.eks. brugeraktivitet, godkendelse, mail, kompromitterede pc'er og sikkerhedshændelser. Beslutningstagere i virksomheden og dit team af sikkerhedshandlinger kan bruge disse oplysninger til at forstå og reagere på trusler mod din organisation og beskytte dine immaterielle rettigheder.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Få kendskab til trusselsundersøgelses- og svarværktøjer

Trusselsundersøgelses- og svarfunktioner i Microsoft 365 Defender portalen på <https://security.microsoft.com> er et sæt værktøjer og svararbejdsprocesser, der omfatter:

- [Explorer](#explorer)
- [Hændelser](#incidents)
- [Oplæring i angrebssimulering](attack-simulation-training.md)
- [Automatiseret undersøgelse og svar](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

Brug [Stifinder (og registreringer i realtid)](threat-explorer.md) til at analysere trusler, se mængden af angreb over tid og analysere data efter trusselsfamilier, infrastruktur for hackere med mere. Explorer (også kaldet Threat Explorer) er startsted for alle sikkerhedsanalytikeres undersøgelsesarbejdsprocesser.

:::image type="content" source="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png" alt-text="Siden Threat Explorer" lightbox="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png":::

Hvis du vil have vist og bruge denne rapport på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Mail & samarbejdsoversigt**\>. Du kan også gå direkte til siden **Stifinder** ved at bruge <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Threat Intelligence-forbindelse

Denne funktion er kun tilgængelig, hvis du har et aktivt Office 365 E5-abonnement eller Threat Intelligence-tilføjelsesprogrammet. Du kan få flere oplysninger på produktsiden Office 365 Enterprise E5.

Når du aktiverer denne funktion, kan du integrere data fra Microsoft Defender for Office 365 i Microsoft 365 Defender for at udføre en omfattende sikkerhedsundersøgelse på tværs af Office 365 postkasser og Windows enheder.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

Hvis du vil modtage kontekstafhængig enhedsintegration i Office 365 Threat Intelligence, skal du aktivere indstillingerne for Defender for Endpoint på dashboardet Sikkerhed & Overholdelse.

### <a name="incidents"></a>Hændelser

Brug listen Hændelser (dette kaldes også Undersøgelser) for at få vist en liste over hændelser i flightsikkerhed. Hændelser bruges til at spore trusler, f.eks. mistænkelige mails, og til at udføre yderligere undersøgelse og afhjælpning.

:::image type="content" source="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png" alt-text="Listen over aktuelle trusselshændelser i Office 365" lightbox="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png":::

Hvis du vil have vist listen over aktuelle hændelser for din organisation på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Hændelser & beskeder** \> **Hændelser**. Du kan også gå direkte til siden **Hændelser** ved at bruge <https://security.microsoft.com/incidents>.

:::image type="content" source="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png" alt-text="Siden Gennemse i Security & Compliance Center" lightbox="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png":::

### <a name="attack-simulation-training"></a>Oplæring i angrebssimulering

Brug træning i simulering af angreb til at konfigurere og køre realistiske cyberangreb i din organisation, og identificer sårbare personer, før et rigtigt cyberangreb påvirker din virksomhed. Du kan få mere at vide under [Simuler et phishing-angreb](attack-simulation-training.md).

Hvis du vil have vist og bruge denne funktion på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Mail & samarbejdeTræning** >  af **simulering af simulering**. Du kan også gå direkte til træningssiden **for simulering af angreb** ved at bruge <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>Automatiseret undersøgelse og svar

Brug air-funktioner (automatiseret undersøgelse og svar) til at spare tid og kræfter på at korrelere indhold, enheder og personer, der er i fare for trusler i din organisation. AIR-processer kan begynde, når visse beskeder udløses, eller når de startes af dit sikkerhedsteam. Du kan få mere at vide [under Automatiseret undersøgelse og svar i Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Trusselsintelligenswidgets

Som en del af tilbuddet på Microsoft Defender for Office 365 Plan 2 kan sikkerhedsanalytikere gennemse detaljer om en kendt trussel. Dette er nyttigt for at afgøre, om der er yderligere forebyggende foranstaltninger/trin, der kan træffes for at beskytte brugerne.

:::image type="content" source="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png" alt-text="Ruden Sikkerhedstendenser, der viser oplysninger om de seneste trusler" lightbox="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png":::

## <a name="how-do-we-get-these-capabilities"></a>Hvordan får vi disse funktioner?

Microsoft 365 trusselsundersøgelses- og svarfunktioner er inkluderet i Microsoft Defender for Office 365 Plan 2, som er inkluderet i Enterprise E5 eller som et tilføjelsesprogram til visse abonnementer. Du kan få mere at vide [under Defender for Office 365 Plan 1 og Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>Påkrævede roller og tilladelser

Microsoft Defender for Office 365 bruger rollebaseret adgangskontrol. Tilladelser tildeles via visse roller i Azure Active Directory, Microsoft 365 Administration eller Microsoft 365 Defender-portalen.

> [!TIP]
> Selvom nogle roller, f.eks. Sikkerhedsadministrator, kan tildeles på Microsoft 365 Defender-portalen, kan du overveje enten at bruge Microsoft 365 Administration eller Azure Active Directory i stedet. Du kan få oplysninger om roller, rollegrupper og tilladelser i følgende ressourcer:
>
> - [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md)
> - [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)

|Aktivitet|Roller og tilladelser|
|---|---|
|Brug dashboardet Administration af sårbarheder & Threat & (eller det nye [sikkerhedsdashboard](security-dashboard.md)) <p> Få vist oplysninger om de seneste eller aktuelle trusler|Et af følgende: <ul><li>**Global administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Brug [Stifinder (og registreringer i realtid)](threat-explorer.md) til at analysere trusler|Et af følgende: <ul><li>**Global administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Vis hændelser (også kaldet Undersøgelser) <p> Føj mails til en hændelse|Et af følgende: <ul><li>**Global administrator**</li><li>**Sikkerhedsadministrator**</li><li>**Sikkerhedslæser**</li></ul> <p> Disse roller kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>).|
|Udløs mailhandlinger i en hændelse <p> Find og slet mistænkelige mails|Et af følgende: <ul><li>**Global administrator**</li><li>**Sikkerhedsadministrator** plus rollen **Søg og Fjern**</li></ul> <p> Rollerne **Global administrator** og **Sikkerhedsadministrator** kan tildeles enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>). <p> Rollen **Søg og Fjern** skal tildeles i **rollerne Mail & samarbejde** på Microsoft 36 Defender-portalen (<https://security.microsoft.com>).|
|Integrer Microsoft Defender for Office 365 Plan 2 med Microsoft Defender for Endpoint <p> Integrer Microsoft Defender for Office 365 Plan 2 med en SIEM-server|Rollen **Global administrator** eller **Sikkerhedsadministrator** tildelt i enten Azure Active Directory (<https://portal.azure.com>) eller Microsoft 365 Administration (<https://admin.microsoft.com>). <p> --- **Plus** --- <p> En relevant rolle, der er tildelt i yderligere programmer (f.eks[. Microsoft Defender Security Center](/windows/security/threat-protection/microsoft-defender-atp/user-roles) eller din SIEM-server).|

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om Threat Trackers – Ny og Bemærkelsesværdig](threat-trackers.md)
- [Find og undersøg ondsindet mail, der blev leveret (Office 365 Threat Investigation og Response)](investigate-malicious-email-that-was-delivered.md)
- [Integrer Office 365 Threat Investigation og Response med Microsoft Defender for Endpoint](integrate-office-365-ti-with-mde.md)
- [Simuler et phishing-angreb](attack-simulation-training.md)
