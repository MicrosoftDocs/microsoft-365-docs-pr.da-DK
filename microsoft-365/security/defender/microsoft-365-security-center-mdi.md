---
title: Microsoft Defender for Identity i Microsoft 365 Defender
description: Få mere at vide om ændringer fra Microsoft Defender for Identity til Microsoft 365 Defender
keywords: Introduktion til Microsoft 365 Defender, Microsoft Defender for Identity, NDI
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 07/06/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 53c43c3196a22a97b2f11105f5145bd62229b137
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/11/2022
ms.locfileid: "66858955"
---
# <a name="microsoft-defender-for-identity-in-microsoft-365-defender"></a>Microsoft Defender for Identity i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Identity](/defender-for-identity/)

Microsoft Defender for Identity er nu en del af Microsoft 365 Defender. På Microsoft 365 Defender-portalen kan sikkerhedsadministratorer udføre deres sikkerhedsopgaver på én placering. Dette forenkler arbejdsprocesser og tilføjer funktionaliteten af de andre Microsoft 365 Defender tjenester. Microsoft 365 Defender er hjemsted for overvågning og administration af sikkerhed på tværs af dine Microsoft-identiteter, -data, -enheder, -apps og -infrastruktur.

Microsoft Defender for Identity bidrager identitetsfokuserede oplysninger til de hændelser og beskeder, som Microsoft 365 Defender præsenterer. Disse oplysninger er vigtige for at levere kontekst og korrelere beskeder fra de andre produkter i Microsoft 365 Defender.

## <a name="quick-reference"></a>Hurtig reference

I nedenstående tabel vises ændringerne i navigationen mellem Microsoft Defender for Identity og Microsoft 365 Defender.

| **Defender for** Identitet  | **Microsoft 365 Defender**                                   |
| -------------------------- | ------------------------------------------------------------ |
| Tidslinjen                   | kø for Microsoft 365 Defender beskeder/hændelser                |
| Rapporter                    | Forbliver i den [klassiske Defender for Identity-portal](/defender-for-identity/classic-workspace-portal). <br> Brugerdefinerede rapporter kan oprettes på Microsoft 365 Defender portalen ved hjælp af [Avanceret jagt](#advanced-hunting-new).               |
| Brugerside                  | Microsoft 365 Defender brugerside                             |
| Enhedsside                | siden Microsoft 365 Defender enhed                           |
| Gruppeside                 | sideruden Microsoft 365 Defender grupper                      |
| Beskedside                 | siden Microsoft 365 Defender besked                            |
| Søg                     | Microsoft 365 Defender søgning                                |
| Sundhedscenter              | Indstillinger -> identiteter -> sensorer                            |
| Objektaktiviteter          | Avanceret jagt                                             |
| Indstillinger                   | Indstillinger – > identiteter                                       |
| Brugere og konti         | Assets –> Identities                                         |
| Sikkerhedsholdning for identitet  | [Microsoft Defender for Identity vurderinger af sikkerhedsholdning](/defender-for-identity/security-assessment) |
| Onboarding af et nyt arbejdsområde | Indstillinger – > identiteter (automatisk)                       |

## <a name="whats-changed"></a>Hvad er ændret

### <a name="defender-for-identity-settings"></a>Indstillinger for Defender for Identity

Hvis du vil have adgang til Microsoft Defender for Identity konfigurationsindstillinger, [skal du](https://security.microsoft.com) gå til **Indstillinger** og derefter **Identiteter** i Microsoft 365 Defender.

### <a name="defender-for-identity-security-posture"></a>Sikkerhedsholdning i Defender for Identity

Alle vurderinger af administration af identitetssikkerhedsholdning, der tidligere var tilgængelige i Defender for Cloud Apps, er nu tilgængelige i Microsoft Secure Score, som du kan finde på <https://security.microsoft.com/securescore> [Microsoft 365 Defender-portalen](https://security.microsoft.com). Du kan få flere oplysninger under [vurderinger af Microsoft Defender for Identity sikkerhedsholdning](/defender-for-identity/security-assessment).

### <a name="global-search"></a>Global søgning

Global søgning i Microsoft 365 Defender (ved hjælp af søgelinjen øverst på siden) gør det muligt for sikkerhedsteams at søge efter alle enheder, der overvåges af Microsoft 365 Defender, f.eks. identitet, slutpunkt, Office 365 data og meget mere. Resultaterne kan interageres direkte med på søgerullelisten, eller sikkerhedsteams kan vælge at vælge **Alle brugere** eller **Alle enheder**  for at se alle enheder, der er knyttet til det pågældende søgeord.

### <a name="onboarding-and-administration"></a>Onboarding og administration

Onboardingprocessen er nu automatisk for nye kunder, uden at det er nødvendigt at konfigurere et arbejdsområde manuelt. Derudover er alle administratorfunktionerne tilgængelige i menuen **Identiteter** i Microsoft 365 Defender indstillinger.

### <a name="alerting-and-incident-correlation"></a>Besked- og hændelseskorrelation

Defender for Identity-beskeder er nu inkluderet i Microsoft 365 Defender beskedkø, hvilket gør dem tilgængelige for funktionen til automatisk hændelseskorrelation. Dette sikrer, at alle beskeder er tilgængelige på ét sted, og at omfanget af et brud kan bestemmes hurtigere end før. Du kan få flere oplysninger under [Sikkerhedsbeskeder om identitet i Defender for Microsoft 365 Defender](/defender-for-identity/manage-security-alerts).

### <a name="advanced-hunting-new"></a>Avanceret jagt (ny)

Du kan nu proaktivt søge efter trusler og skadelig aktivitet ved hjælp af avancerede jagtforespørgsler. Disse effektive forespørgsler kan bruges til at finde og gennemse trusselsindikatorer og enheder for både kendte og potentielle trusler.

Brugerdefinerede registreringsregler kan bygges fra avancerede jagtforespørgsler for at hjælpe dig med proaktivt at holde øje med hændelser, der kan være tegn på brudaktivitet og forkert konfigurerede enheder. Du kan finde flere oplysninger under [Proaktiv jagt efter trusler med avanceret jagt i Microsoft 365 Defender](advanced-hunting-overview.md).

### <a name="alert-exclusions-updated"></a>Undtagelser for beskeder (opdateret)

Beskedgrænsefladen er mere brugervenlig, herunder tilføjelse af en nyttig søgefunktion. Desuden indeholder den nu globale undtagelser. Det betyder, at alle enheder kan udelades fra alle beskeder, der genereres af Defender for Identity, hvilket hjælper med eventuelle testscenarier, du måtte have. Du kan få flere oplysninger under [Konfigurer udeladelser af defender for identitetsregistrering i Microsoft 365 Defender](/defender-for-identity/exclusions).

### <a name="entity-profiles"></a>Enhedsprofiler

Defender for Identity-data er nu inkluderet i Microsoft 365-enhedsprofilerne for brugere og enheder.

### <a name="remediation-actions-new"></a>Afhjælpningshandlinger (nye)

Afhjælpningshandlinger for Defender for Identity, f.eks. deaktivering af konti eller krav om nulstilling af adgangskode, kan nu tages fra siden Microsoft 365 Defender bruger. Du kan få flere oplysninger under [Afhjælpningshandlinger i Microsoft Defender for Identity](/defender-for-identity/remediation-actions).

### <a name="lateral-movement-paths"></a>Tværgående bevægelsesstier

Ud over fanen **Tværgående bevægelsesstier** på brugersiden kan du også finde tværgående bevægelsesstier via funktionen **Avanceret jagt** og sikkerhedsvurderingen Af tværgående bevægelsesstier. Du kan få flere oplysninger [under Microsoft Defender for Identity LSP'er (Lateral Movement Paths).](/defender-for-identity/understand-lateral-movement-paths)

## <a name="related-videos"></a>Relaterede videoer

- [Ny til Microsoft Defender for Identity](https://www.microsoft.com/videoplayer/embed/RE4HcEU)

## <a name="related-information"></a>Relaterede oplysninger

- [Microsoft 365 Defender](microsoft-365-defender.md)
