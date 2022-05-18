---
title: Administrer og overvåg prioritetskonti
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
description: Overvåg mislykkede og forsinkede mails, der sendes til eller fra konti, der har stor forretningsmæssig indvirkning.
ms.openlocfilehash: edf2c2b1994e1647c4df9b639386cc43dc312c80
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465860"
---
# <a name="manage-and-monitor-priority-accounts-in-microsoft-365"></a>Administrer og overvåg prioritetskonti i Microsoft 365

I hver Microsoft 365 organisation er der personer, der er vigtige, f.eks. direktører, ledere, ledere eller andre brugere, der har adgang til følsomme, beskyttede oplysninger eller oplysninger med høj prioritet.

For at hjælpe din organisation med at beskytte disse konti kan du nu angive bestemte brugere som prioriterede konti og udnytte appspecifikke funktioner, der giver dem ekstra beskyttelse. I fremtiden understøtter flere apps og funktioner prioriterede konti, og til at starte med har vi annonceret to funktioner: **prioriteret kontobeskyttelse** og **premium overvågning af mailflow**.

- **Prioritetskontobeskyttelse** – Microsoft Defender for Office 365 (tidligere Office 365 Advanced Threat Protection) understøtter prioritetskonti som tags, der kan bruges i filtre i beskeder, rapporter og undersøgelser. Du kan få flere oplysninger [i Brugerkoder i Microsoft Defender for Office 365](../../security/office-365-security/user-tags.md).

  Et naturligt spørgsmål er: "Er alle brugere ikke en prioritet? Hvorfor ikke angive alle brugere som prioritetskonti?" Ja, alle brugere har en prioritet, men prioritetskontobeskyttelse giver følgende yderligere fordele:

  - **Yderligere heuristik**: Vores analyse af mailflow i Microsoft-datacentrene angiver, at mønstre for mailflow for virksomhedsledere er anderledes end den gennemsnitlige medarbejder. Prioritetskontobeskyttelse tilbyder yderligere heuristik, der er specifikt skræddersyet til virksomhedens direktører, som ikke ville være til gavn for en almindelig medarbejder.
  - **Yderligere synlighed i rapportering**: Faktisk er oplysninger for alle brugere (eller alle berørte brugere) allerede tilgængelige i beskeder, rapporter og undersøgelser. Prioritetskonti tagget som et filter giver dig mulighed for specifikt at målrette dine undersøgelser.

- **Premium Overvågning af mail Flow** – Et sundt mailflow kan være afgørende for virksomhedens succes, og leveringsforsinkelser eller -fejl kan have en negativ indvirkning på virksomheden. Du kan vælge en tærskel for mislykkede eller forsinkede mails, modtage beskeder, når denne grænse er overskredet, og få vist en rapport over mailproblemer for prioritetskonti. Du kan få flere oplysninger i [Rapporten Mailproblemer for prioritetskonti i den moderne EAC](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Du kan få oplysninger om bedste praksis for sikkerhed for prioriterede konti under [Sikkerhedsanbefalinger for prioriterede konti](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Før du begynder

Funktionen **Prioritetskontobeskyttelse** , der er beskrevet i dette emne, er kun tilgængelig for organisationer, der opfylder følgende krav:

- Microsoft Defender for Office 365 Plan 2, herunder dem med Office 365 E3, Office 365 E5, Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed.

Funktionen **Premium Mail Flow Overvågning**, der er beskrevet i dette emne, er kun tilgængelig for organisationer, der opfylder følgende krav:

- Din organisation skal have et licensantal på mindst 5.000 fra et af eller en kombination af følgende produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Din organisation kan f.eks. have 3.000 Office 365 E3 licenser og 2.500 Microsoft 365 E5 i alt 5.500 licenser fra de kvalificerende produkter.
- Din organisation skal have mindst 50 aktive brugere om måneden for en eller flere vigtige arbejdsbelastninger – Teams, One Drive for Business, SharePoint Online, Exchange Online og Office apps.

> [!NOTE]
> Du kan overvåge op til 250 prioritetskonti.

Når du anvender prioritetskontobeskyttelse på en postkasse, skal du også anvende prioritetskontobeskyttelse på brugere, der har adgang til postkassen (f.eks. den administrerende direktør og den administrerende direktørs chefassistent, der administrerer den administrerende direktørs kalender).

### <a name="add-priority-accounts-from-the-setup-page"></a>Tilføj prioritetskonti fra siden Konfiguration

Tilføj prioritetskonti fra **siden Konfiguration**.

1. Gå til Microsoft 365 Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **SetupOrganizational** >  knowledge, og vælg **Vis** under **Overvåg dine vigtigste konti**.

3. Vælg **Kom i gang** eller **Administrer**.

4. Skriv navnet eller mailadressen på den person, du vil føje til listen med prioritetskonti, i søgefeltet på siden **Tilføj prioritetskonti** . Du kan også angive din mailgrænse for mislykkede eller forsinkede mails og få en ugentlig rapport over problemer for prioriterede konti.

5. Vælg brugeren, og vælg **Gem**.

Du kan også tilføje prioritetskonti fra siden Aktive brugere.

### <a name="add-priority-accounts-from-active-users-page"></a>Siden Tilføj prioritetskonti fra siden Aktive brugere

Tilføj prioritetskonti fra siden Aktive brugere.

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **BrugereAktive**  >  brugere, og vælg de tre prikker (flere handlinger) øverst på siden. Vælg **Administrer prioritetskonti**.

3. Vælg **Tilføj konti**, og skriv navnet på den person, du vil føje til listen **prioritetskonti** , i søgefeltet på siden Tilføj prioritetskonti.

4. Vælg brugeren, og vælg **Gem**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Fjern en bruger fra listen over prioritetskonti

1. Gå til Microsoft 365 Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **SetupOrganizational** >  knowledge, og vælg **Vis** under **Overvåg dine vigtigste konti**.

3. På siden **Overvåg dine fleste konti** skal du vælge **Prioritetskonti** under **Administrer denne funktion**.

4. På siden **Prioritetskonti** skal du vælge den eller de brugere, du vil fjerne fra listen, og vælge **Fjern konti**.

## <a name="related-topics"></a>Relaterede emner

[Brug af prioritetskonti i Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
