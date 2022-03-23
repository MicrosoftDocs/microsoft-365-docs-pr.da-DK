---
title: Arbejd med rapporter
description: De forskellige rapporter, der er tilgængelige i Microsoft Managed Desktop
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 620e9d2bd95dc4782237af94966b5cb52579b656
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63594200"
---
# <a name="work-with-reports"></a>Arbejd med rapporter

Konsollen Microsoft Endpoint Manager samler rapportering fra flere produkter på ét sted for at hjælpe dig med at overvåge og undersøge problemer med konfigurationen og enhederne i din Azure AD-organisation ("lejer").

Microsoft Managed Desktop har en sektion i menuen  Rapporter, hvor du kan finde rapporter, der er specifikke for administrationen af de registrerede enheder i Microsoft Managed Desktop. Du kan filtrere rapporter Microsoft Endpoint Manager andre produktgrupper på flere forskellige steder i hele Microsoft Endpoint Manager. Du kan medtage eller udelade enheder, der administreres af Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-reports"></a>Microsoft-administrerede skrivebordsrapporter

Microsoft Managed Desktop indeholder adskillige rapporter og dashboards. It-administratorer i organisationen kan bruge disse rapporter og dashboards til at forstå forskellige aspekter af populationen af enheder. I Microsoft Endpoint Manager skal du gå til sektionen Rapporter under Microsoft Managed Desktop og vælge Administrerede enheder.

På fanen **Oversigt** finder du hurtige målepunkter for enhedsopdateringer. Vælg **Vis detaljer for** enhver metrik for at hente yderligere oplysninger til offlineanalyse, herunder det underliggende datasæt for metrikværdien.

Når du vælger **fanen** Rapporter, får du vist beskrivelser af de tilgængelige detaljerede rapporter. Disse rapporter er mere omfattende og understøtter datavisualisering og filtrering i portalen. Du kan også eksportere de underliggende data til offlineanalyse eller -distribution. Følgende rapporter er tilgængelige i dag:

| Rapport | Beskrivelse |
| ------ | ------ |
| [**Statusrapport for** enhed](device-status-report.md) (*i forhåndsvisning*) | Denne rapport viser din brug af Microsoft Managed Desktop-tjenesten baseret på enhedsaktivitet og brug. |
| **Tendens for enhedsstatus** (*i forhåndsvisning*) | Dette overvåger tendenser i enhedsstatus i løbet af de seneste 60 dage for dine Microsoft-administrerede stationære enheder. Tendenser kan hjælpe dig med at knytte enhedsstatus til andre ændringer over tid, f.eks. nye installationer. |
| [**Windows rapport over sikkerhedsopdateringer**](security-updates-report.md) (*i forhåndsvisning*) | Denne rapport viser, hvordan Windows sikkerhedsopdateringer frigives på tværs af dine Microsoft-administrerede computerenheder. |
| [**Anvendelsesrapport for** program](app-usage-report.md) | Denne rapport indeholder oplysninger om typisk appforbrug på tværs af dine Microsoft-administrerede skrivebordsenheder. For at enheder kan levere data til denne rapport, skal de være indstillet til det valgfrie diagnostiske dataniveau. |
| [**Service Metrics Report**](service-metrics-report.md) (*i forhåndsvisning*) | Denne rapport indeholder enkle oversigter over vigtige målepunkter for Microsoft Managed Desktop måned for måned. |

## <a name="endpoint-analytics"></a>Slutpunktsanalyse

Microsoft Managed Desktop er nu integreret [med slutpunktsanalyse](/mem/analytics/overview). Disse rapporter giver dig viden, der måler, hvordan organisationen fungerer, og kvaliteten af den oplevelse, der leveres til dine brugere. Du kan finde Slutpunktsanalyser **i menuen** Rapporter i [Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Hvis du vil pivote et resultat til kun at omfatte enheder, der administreres af Microsoft Managed Desktop, skal du gå til en hvilken som helst rapport, vælge rullelisten **Filter** og derefter vælge **Microsoft Managed Desktop-enheder**.

Hvis slutpunktsanalyser ikke blev konfigureret automatisk for din Azure AD-organisation ("lejer") under tilmeldingen, kan du gøre det selv. Få mere at vide under [Onboard i Endpoint analytics-portalen](/mem/analytics/enroll-intune#bkmk_onboard). Du kan tilmelde alle dine enheder, eller hvis du kun vil medtage Microsoft Managed Desktop-enheder, skal du vælge de moderne  enhedsgrupper på arbejdspladsen for Test, Først, Hurtig og Bred. Disse rapporter kræver muligvis andre tilladelser. Få mere at vide under [Tilladelser for at](/mem/analytics/overview#permissions) sikre, at du har roller, der er tildelt korrekt.

> [!NOTE]
> For bedre at respektere dine personlige oplysninger skal der være mere end 10 Microsoft-administrerede skrivebordsenheder tilmeldt Endpoint-analyser for at bruge dette filter.

## <a name="intune-reports"></a>Intune-rapporter

Microsoft Intune er en af de tjenester, vi bruger til at administrere enheder på dine vegne.

I nogle tilfælde kan det være nyttigt at bruge Intune-rapporter til specifikt at overvåge administrationen af dine Microsoft-administrerede skrivebordsenheder. Du kan udelade de enheder, vi administrerer, fra den rapport, du bruger til at administrere andre enheder. I følgende rapporter kan du filtrere muligheden for at medtage eller udelade Microsoft-administrerede skrivebordsenheder.

- [Alle enheder](/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Enhedsoverholdelse](/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Ikke-kompilerende enheder](/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Brugerdefinerede roller for Microsoft-administreret skrivebord garanterer kun adgang til rapporter fra Microsoft-administreret skrivebord. For at få adgang til andre Microsoft Endpoint Manager, f.eks. **Alle** enheder, skal du se [Rollebaseret adgangskontrol med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

## <a name="microsoft-managed-desktop-inventory-data"></a>Lagerdata for Microsoft Managed Desktop

Ud over de andre rapporter kan du eksportere oplysninger om de enheder, der administreres af Microsoft Managed Desktop. I Microsoft Endpoint Manager skal du gå til sektionen Enheder under  Microsoft Managed Desktop og vælge Enheder og bruge fanen  Eksportér alle til  [at downloade en detaljeret lagerrapport](device-inventory-report.md).
