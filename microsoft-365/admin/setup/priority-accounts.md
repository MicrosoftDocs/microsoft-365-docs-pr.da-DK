---
title: Administrere og overvåge prioritetskonti
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
description: Overvåg mislykkede og forsinkede mails, der er sendt til eller fra konti, som har stor betydning for virksomheden.
ms.openlocfilehash: b8762885cc54859cf927653abb14858c0094ea12
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601644"
---
# <a name="manage-and-monitor-priority-accounts"></a>Administrere og overvåge prioritetskonti

I hver Microsoft 365 organisation er der personer, der er vigtige, f.eks. ledere, ledere eller andre brugere, der har adgang til følsomme, beskyttede eller højprioritetsoplysninger.

For at hjælpe organisationen med at beskytte disse konti kan du nu udpege bestemte brugere som prioritetskonti og udnytte appspecifikke funktioner, der giver dem ekstra beskyttelse. Fremover vil flere apps og funktioner understøtte prioritetskonti, og til at starte med har vi meddelt to **funktioner: prioritet** af kontobeskyttelse og førsteklasses **overvågning af mailflow**.

- **Prioritetskontobeskyttelse** – Microsoft Defender til Office 365 (tidligere Office 365 Advanced Threat Protection) understøtter prioritetskonti som mærker, der kan bruges i filtre i beskeder, rapporter og undersøgelser. Du kan finde flere oplysninger [i Brugermærker i Microsoft Defender for Office 365](../../security/office-365-security/user-tags.md).

  Et naturligt spørgsmål er: "Er ikke alle brugere en prioritet? Hvorfor ikke udpege alle brugere som prioritetskonti?" Ja, alle brugere er en prioritet, men prioritetskontobeskyttelse giver følgende yderligere fordele:

  - **Yderligere heuristics**: Vores analyse af mailflow i Microsoft-datacentre angiver, at mønstre for mailflow for ledere i virksomheden er anderledes end den gennemsnitlige medarbejder. Prioritetskontobeskyttelse giver yderligere heuristics, der er skræddersyet til virksomhedsledere, som ikke ville være til gavn for en almindelig medarbejder.
  - **Yderligere synlighed i rapportering**: Faktisk er oplysninger for alle brugere (eller alle berørte brugere) allerede tilgængelige i beskeder, rapporter og undersøgelser. Mærket prioritetskonti som et filter giver dig mulighed for specifikt at målrette dine undersøgelser.

- **Premium overvågning af mail Flow** – Sund mailflow kan være afgørende for virksomhedens succes, og forsinkelser eller fejl i leveringen kan have en negativ indvirkning på virksomheden. Du kan vælge en grænseværdi for mislykkede eller forsinkede mails, modtage beskeder, når denne grænse overskrides, og få vist en rapport over mailproblemer for prioritetskonti. Få mere at vide under [Mailproblemer for prioritetskonti-rapport i den moderne EAC](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Du kan finde de bedste fremgangsmåder for sikkerhedskonti i [Sikkerhedsanbefalinger for prioritetskonti](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Før du begynder

Funktionen **prioritetskontobeskyttelse** , der er beskrevet i dette emne, er kun tilgængelig for organisationer, der opfylder følgende krav:

- Microsoft Defender til Office 365 Plan 2, herunder personer med Office 365 E3, Office 365 E5, Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed.

Den **Premium funktion Flow mailovervågning**, der er beskrevet i dette emne, er kun tilgængelig for organisationer, der opfylder følgende krav:

- Din organisation skal have en licenstælling på mindst 5.000, fra en af eller en kombination af følgende produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Din organisation kan f.eks. have 3.000 Office 365 E3-licenser og 2.500 Microsoft 365 E5, i alt 5.500 licenser fra de kvalificerende produkter.
- Din organisation skal have mindst 50 månedlige aktive brugere til en eller flere centrale arbejdsbelastninger – Teams, One Drive for Business, SharePoint Online, Exchange Online og Office-apps.

> [!NOTE]
> Du kan overvåge op til 250 prioritetskonti.

Når du anvender prioritetskontobeskyttelse på en postkasse, skal du også anvende prioritetskontobeskyttelse for brugere, der har adgang til postkassen (f.eks. den administrerende direktør og den administrerende direktørs chefassistent, der administrerer den administrerende direktørs kalender).

### <a name="add-priority-accounts-from-the-setup-page"></a>Tilføj prioritetskonti fra siden Konfiguration

Tilføj prioritetskonti fra **siden Konfiguration**.

1. Gå til Microsoft 365 Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **Konfigurationsorganisering** > , og vælg **Vis** under **Overvåg dine vigtigste konti**.

3. Vælg **Kom i gang** eller **Administrer**.

4. Skriv **navnet eller mailadressen** på den person, du vil føje til listen over prioritetskonti, i søgefeltet på siden Tilføj prioritetskonti. Du kan også angive din grænseværdi for mail for mislykkede eller forsinkede mails og få en ugentlig rapport over problemer for prioritetskonti.

5. Vælg brugeren, og vælg **Gem**.

Du kan også tilføje prioritetskonti fra siden Aktive brugere.

### <a name="add-priority-accounts-from-active-users-page"></a>Siden Tilføj prioritetskonti fra aktive brugere

Tilføj prioritetskonti fra siden Aktive brugere.

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **BrugereAktivér**  >  brugere, og vælg de tre prik (flere handlinger) øverst på siden. Vælg **Administrer prioritetskonti**.

3. Vælg **Tilføj konti**, og skriv navnet  på den person, du vil føje til listen prioritetskonti, i søgefeltet på siden Tilføj prioritetskonti.

4. Vælg brugeren, og vælg **Gem**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Fjerne en bruger fra listen over prioritetskonti

1. Gå til Microsoft 365 Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **Konfigurationsorganisering** > , og vælg **Vis** under **Overvåg dine vigtigste konti**.

3. På siden **Overvåg dine fleste konti** skal du vælge **Prioritetskonti** under **Administrer denne funktion**.

4. På siden **Prioritetskonti** skal du vælge den eller de brugere, du vil fjerne fra listen, og vælge **Fjern konti**.

## <a name="related-topics"></a>Relaterede emner

[Brug af prioritetskonti i Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
