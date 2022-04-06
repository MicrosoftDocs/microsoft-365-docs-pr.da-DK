---
title: Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du justerer dine Microsoft Defender for Endpoint forespørgsler, så du kan bruge dem i Microsoft 365 Defender
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, Microsoft Defender for Endpoint, søgning, forespørgsel, telemetri, brugerdefinerede opdagelser, skema, kusto, kortlægning
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 9fd00df5e61d37e5133f23e5f06973ceb99c4636
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666168"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Flyt dine avancerede arbejdsprocesser til jagt fra Microsoft Defender for Endpoint til proaktivt at jage efter trusler ved hjælp af et bredere datasæt. I Microsoft 365 Defender får du adgang til data fra andre Microsoft 365 sikkerhedsløsninger, herunder:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

>[!NOTE]
>De fleste Microsoft Defender for Endpoint kunder kan [bruge Microsoft 365 Defender uden yderligere licenser](prerequisites.md#licensing-requirements). Hvis du vil overgå dine avancerede arbejdsprocesser til jagt fra Defender for Endpoint, [skal du aktivere Microsoft 365 Defender](m365d-enable.md).

Du kan skifte uden at påvirke dine eksisterende Defender for Endpoint-arbejdsprocesser. Gemte forespørgsler forbliver intakte, og brugerdefinerede regler for registrering fortsætter med at køre og generere beskeder. De vil dog være synlige i Microsoft 365 Defender.

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Kun skematabeller i Microsoft 365 Defender

Det [Microsoft 365 Defender avancerede jagtskema](advanced-hunting-schema-tables.md) indeholder yderligere tabeller, der indeholder data fra forskellige Microsoft 365 sikkerhedsløsninger. Følgende tabeller er kun tilgængelige i Microsoft 365 Defender:

| Tabelnavn | Beskrivelse |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Filer, IP-adresser, URL-adresser, brugere eller enheder, der er knyttet til beskeder |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Beskeder fra Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps og Microsoft Defender for Identity , herunder oplysninger om alvorsgrad og trusselskategorier  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Oplysninger om filer, der er knyttet til mails |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 mailhændelser, herunder levering af mail og blokeringshændelser |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Sikkerhedshændelser, der opstår efter levering, efter Microsoft 365 har leveret mails til modtagerpostkassen |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Oplysninger om URL-adresser i mails |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Hændelser, der involverer en domænecontroller i det lokale miljø, som kører Active Directory (AD). Denne tabel dækker en række identitetsrelaterede hændelser og systemhændelser på domænecontrolleren. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Kontooplysninger fra forskellige kilder, herunder Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Godkendelseshændelser på Active Directory og Microsoft onlinetjenester |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Forespørgsler til Active Directory-objekter, f.eks. brugere, grupper, enheder og domæner |

>[!IMPORTANT]
> Forespørgsler og brugerdefinerede registreringer, der bruger skematabeller, som kun er tilgængelige i Microsoft 365 Defender, kan kun vises i Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Tilknyt tabellen DeviceAlertEvents

Tabellerne `AlertInfo` og `AlertEvidence` erstatter tabellen `DeviceAlertEvents` i det Microsoft Defender for Endpoint skema. Ud over data om enhedsbeskeder omfatter disse to tabeller data om beskeder om identiteter, apps og mails.

Brug følgende tabel til at kontrollere, hvordan `DeviceAlertEvents` kolonner knyttes til kolonner i tabellerne `AlertInfo` og `AlertEvidence` .

> [!TIP]
> Ud over kolonnerne i følgende tabel indeholder tabellen `AlertEvidence` mange andre kolonner, der giver et mere holistisk billede af beskeder fra forskellige kilder. [Se alle kolonnerne AlertEvidence](advanced-hunting-alertevidence-table.md)

| Kolonnen DeviceAlertEvents | Her kan du finde de samme data i Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` og  `AlertEvidence` tabeller |
| `Timestamp` | `AlertInfo` og  `AlertEvidence` tabeller |
| `DeviceId` | `AlertEvidence` Tabel |
| `DeviceName` | `AlertEvidence` Tabel |
| `Severity` | `AlertInfo` Tabel |
| `Category` | `AlertInfo` Tabel |
| `Title` | `AlertInfo` Tabel |
| `FileName` | `AlertEvidence` Tabel |
| `SHA1` | `AlertEvidence` Tabel |
| `RemoteUrl` | `AlertEvidence` Tabel |
| `RemoteIP` | `AlertEvidence` Tabel |
| `AttackTechniques` | `AlertInfo` Tabel |
| `ReportId` | Denne kolonne bruges typisk i Microsoft Defender for Endpoint til at finde relaterede poster i andre tabeller. I Microsoft 365 Defender kan du hente relaterede data direkte fra tabellen`AlertEvidence`. |
| `Table` | Denne kolonne bruges typisk i Microsoft Defender for Endpoint til yderligere hændelsesoplysninger i andre tabeller. I Microsoft 365 Defender kan du hente relaterede data direkte fra tabellen`AlertEvidence`. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Juster eksisterende Microsoft Defender for Endpoint forespørgsler

Microsoft Defender for Endpoint forespørgsler fungerer, som de er, medmindre de refererer til tabellen`DeviceAlertEvents`. Hvis du vil bruge disse forespørgsler i Microsoft 365 Defender, skal du anvende disse ændringer:

- Erstat `DeviceAlertEvents` med `AlertInfo`.
- Joinforbind tabellerne `AlertInfo` `AlertEvidence` `AlertId` og for at få tilsvarende data.

### <a name="original-query"></a>Oprindelig forespørgsel

Følgende forespørgsel bruger `DeviceAlertEvents` i Microsoft Defender for Endpoint til at hente de beskeder, der involverer _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### <a name="modified-query"></a>Ændret forespørgsel

Følgende forespørgsel er blevet justeret til brug i Microsoft 365 Defender. I stedet for at kontrollere filnavnet direkte fra `DeviceAlertEvents`joinforbinder `AlertEvidence` og søger den efter filnavnet i tabellen.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Overfør regler for brugerdefineret registrering

Når Microsoft Defender for Endpoint regler redigeres på Microsoft 365 Defender, fungerer de fortsat som før, hvis den resulterende forespørgsel kun ser på enhedstabeller.

Beskeder, der genereres af regler for brugerdefineret registrering, som kun forespørger enhedstabeller, vil f.eks. fortsat blive leveret til din SIEM og generere mailmeddelelser, afhængigt af hvordan du har konfigureret disse i Microsoft Defender for Endpoint. Alle eksisterende undertrykkelsesregler i Defender for Endpoint vil også fortsat være gældende.

Når du redigerer en Defender for Endpoint-regel, så den forespørger identitets- og mailtabeller, som kun er tilgængelige i Microsoft 365 Defender, flyttes reglen automatisk til Microsoft 365 Defender.

Beskeder genereret af den migrerede regel:

- Er ikke længere synlige i Defender for Endpoint Portal (Microsoft Defender Security Center)
- Stop med at blive leveret til din SIEM, eller opret mailmeddelelser. Du kan løse problemet ved at konfigurere meddelelser via Microsoft 365 Defender for at få beskederne. Du kan bruge [API'en Microsoft 365 Defender](api-incident.md) til at modtage meddelelser om kunderegistreringsbeskeder eller relaterede hændelser.
- Vil ikke blive undertrykt af Microsoft Defender for Endpoint undertrykkelsesregler. Hvis du vil forhindre, at der genereres beskeder for visse brugere, enheder eller postkasser, skal du ændre de tilsvarende forespørgsler for eksplicit at udelade disse enheder.

Hvis du redigerer en regel på denne måde, bliver du bedt om at bekræfte, før sådanne ændringer anvendes.

Nye beskeder, der genereres af regler for brugerdefineret registrering i Microsoft 365 Defender vises på en beskedside, der indeholder følgende oplysninger:

- Beskedtitel og -beskrivelse
- Påvirkede aktiver
- Handlinger, der udføres som svar på beskeden
- Forespørgselsresultater, der udløste beskeden
- Oplysninger om reglen for brugerdefineret registrering

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Et eksempel på en beskedside, der viser nye beskeder, der genereres af regler for brugerdefineret registrering på Microsoft 365 Defender portal" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>Skriv forespørgsler uden DeviceAlertEvents

I det Microsoft 365 Defender skema leveres tabellerne `AlertInfo` og `AlertEvidence` for at imødekomme det forskelligartede sæt oplysninger, der følger med beskeder fra forskellige kilder.

Hvis du vil hente de samme beskedoplysninger, som du brugte til at hente fra tabellen `DeviceAlertEvents` i det Microsoft Defender for Endpoint skema, skal du filtrere `AlertInfo` tabellen efter `ServiceSource` og derefter joinforbinde hvert entydige id med tabellen`AlertEvidence`, hvilket giver detaljerede oplysninger om hændelser og enheder.

Se eksempelforespørgslen nedenfor:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Denne forespørgsel giver mange flere kolonner end `DeviceAlertEvents` i Microsoft Defender for Endpoint skema. Hvis du vil holde resultaterne håndterbare, skal du kun bruge `project` til at hente de kolonner, du er interesseret i. I eksemplet nedenfor er der kolonner med projekter, som du kan være interesseret i, når undersøgelsen registrerede PowerShell-aktivitet:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

Hvis du vil filtrere efter bestemte objekter, der er involveret i beskederne, kan du gøre det ved at angive objekttypen i `EntityType` og den værdi, du vil filtrere efter. I følgende eksempel søges der efter en bestemt IP-adresse:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## <a name="see-also"></a>Se også

- [Slå Microsoft 365 Defender til](advanced-hunting-query-language.md)
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Avanceret jagt i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
