---
title: Overfør avancerede forespørgselsforespørgsler fra Microsoft Defender til slutpunkt
description: Få mere at vide om, hvordan du justerer dine Microsoft Defender til slutpunktsforespørgsler, så du kan bruge dem i Microsoft 365 Defender
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, Microsoft Defender til slutpunkt, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, kortlægning
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
ms.openlocfilehash: e64d1a56468d6e87d23c5720bb231e17ecd5679a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63597638"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Overfør avancerede forespørgselsforespørgsler fra Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Flyt dine avancerede arbejdsprocesser for jagt fra Microsoft Defender til Slutpunkt for proaktivt at lede efter trusler ved hjælp af et bredere datasæt. I Microsoft 365 Defender får du adgang til data fra andre Microsoft 365 sikkerhedsløsninger, herunder:

- Microsoft Defender til Slutpunkt
- Microsoft Defender til Office 365
- Microsoft Defender til skyapps
- Microsoft Defender for Identity

>[!NOTE]
>De fleste Microsoft Defender for [Endpoint-kunder kan Microsoft 365 Defender uden yderligere licenser](prerequisites.md#licensing-requirements). Hvis du vil starte overgangen fra dine avancerede arbejdsprocesser på jagt efter arbejdsprocesser fra Defender til Slutpunkt, [skal du Microsoft 365 Defender](m365d-enable.md).

Du kan skifte uden at påvirke dine eksisterende Defender for slutpunktsarbejdsprocesser. Gemte forespørgsler forbliver intakte, og brugerdefinerede registreringsregler fortsætter med at køre og generere beskeder. De vil dog være synlige i Microsoft 365 Defender. 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Skematabeller kun Microsoft 365 Defender skematabeller
Det [Microsoft 365 Defender avancerede søgeskema indeholder yderligere](advanced-hunting-schema-tables.md) tabeller, der indeholder data fra Microsoft 365 forskellige sikkerhedsløsninger. Følgende tabeller er kun tilgængelige i Microsoft 365 Defender:

| Tabelnavn | Beskrivelse |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Filer, IP-adresser, URL-adresser, brugere eller enheder, der er knyttet til beskeder |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Beskeder fra Microsoft Defender for Endpoint, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity, herunder oplysninger om alvorsgrad og trusselskategorier  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Oplysninger om filer, der er vedhæftet mails |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 mailbegivenheder, herunder levering af mail og blokering af begivenheder |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Sikkerhedshændelser, der forekommer efter levering, når Microsoft 365 har leveret mails til modtagerens postkasse |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Oplysninger om URL-adresser i mails |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Hændelser, der involverer en lokal domænecontroller, der kører Active Directory (AD). Denne tabel dækker en række identitetsrelaterede hændelser og systemhændelser på domænecontrolleren. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Kontooplysninger fra forskellige kilder, herunder Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Godkendelseshændelser på Active Directory og Microsoft-onlinetjenester |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Forespørgsler til Active Directory-objekter, f.eks. brugere, grupper, enheder og domæner |

>[!IMPORTANT]
> Forespørgsler og brugerdefinerede registreringer, der bruger skematabeller, der kun er tilgængelige i Microsoft 365 Defender, kan kun vises Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Tabellen Tilknyt DeviceAlertEvents
Tabellerne `AlertInfo` `AlertEvidence` erstatter tabellen `DeviceAlertEvents` i skemaet Microsoft Defender for Endpoint. Ud over data om enhedsadvarsler indeholder disse to tabeller data om beskeder om identiteter, apps og mails.

Brug følgende tabel til at kontrollere, hvordan `DeviceAlertEvents` kolonner knyttes til kolonner i tabellerne `AlertInfo` `AlertEvidence` .

>[!TIP]
>Ud over kolonnerne i følgende tabel indeholder tabellen mange andre kolonner, `AlertEvidence` som giver et mere beskedent billede af beskeder fra forskellige kilder. [Se alle advarselskolonner](advanced-hunting-alertevidence-table.md) 

| Kolonnen DeviceAlertEvents | Her finder du de samme data i Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` og  `AlertEvidence` tabeller |
| `Timestamp` | `AlertInfo` og  `AlertEvidence` tabeller |
| `DeviceId` | `AlertEvidence` tabel |
| `DeviceName` | `AlertEvidence` tabel |
| `Severity` | `AlertInfo` tabel |
| `Category` | `AlertInfo` tabel |
| `Title` | `AlertInfo` tabel |
| `FileName` | `AlertEvidence` tabel |
| `SHA1` | `AlertEvidence` tabel |
| `RemoteUrl` | `AlertEvidence` tabel |
| `RemoteIP` | `AlertEvidence` tabel |
| `AttackTechniques` | `AlertInfo` tabel |
| `ReportId` | Denne kolonne bruges typisk i Microsoft Defender til slutpunkt til at finde relaterede poster i andre tabeller. I Microsoft 365 Defender kan du hente relaterede data direkte fra `AlertEvidence` tabellen. |
| `Table` | Denne kolonne bruges typisk i Microsoft Defender til slutpunkt for yderligere oplysninger om begivenheder i andre tabeller. I Microsoft 365 Defender kan du hente relaterede data direkte fra `AlertEvidence` tabellen. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Juster eksisterende Microsoft Defender til slutpunktsforespørgsler
Microsoft Defender til slutpunktsforespørgsler fungerer, som de er, medmindre de refererer til `DeviceAlertEvents` tabellen. For at bruge disse forespørgsler i Microsoft 365 Defender skal du anvende disse ændringer:

- Erstat `DeviceAlertEvents` med `AlertInfo`.
- Joinforbindelse `AlertInfo` og tabellerne `AlertEvidence` på for `AlertId` at få tilsvarende data.

### <a name="original-query"></a>Oprindelig forespørgsel
Følgende forespørgsel bruger i `DeviceAlertEvents` Microsoft Defender til slutpunkt til at få de vigtige beskeder, der involverer _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>Ændret forespørgsel
Følgende forespørgsel er blevet justeret til brug i Microsoft 365 Defender. I stedet for at kontrollere filnavnet direkte fra `DeviceAlertEvents`, bliver det joinforbindelse `AlertEvidence` , og der kontrolleres for filnavnet i den pågældende tabel.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Overfør brugerdefinerede registreringsregler

Når Microsoft Defender til slutpunktsregler redigeres på Microsoft 365 Defender, fungerer de fortsat som før, hvis den resulterende forespørgsel kun kigger på enhedstabeller. 

Eksempelvis leveres beskeder, der genereres af brugerdefinerede registreringsregler, som kun forespørger på enhedstabeller, fortsat til din SIEM og genererer mailbeskeder, afhængigt af hvordan du har konfigureret disse i Microsoft Defender til slutpunkt. Eventuelle eksisterende regler for undertrykkelse i Defender til Slutpunkt vil også fortsat være gældende.

Når du redigerer en Defender til slutpunkt-regel, så den forespørger efter identitets- og mailtabeller, som kun er tilgængelige i Microsoft 365 Defender, flyttes reglen automatisk til Microsoft 365 Defender. 

Beskeder, der genereres af den overførte regel:

- Er ikke længere synlige i Defender for Endpoint-portalen (Microsoft Defender Security Center)
- Stop med at blive leveret til din SIEM eller generer mailmeddelelser. Du kan løse denne ændring ved at konfigurere Microsoft 365 Defender for at få beskederne. Du kan bruge den [Microsoft 365 Defender-API](api-incident.md) til at modtage beskeder om kunderegistreringsbeskeder eller relaterede hændelser.
- Vil ikke blive undertrykket af Microsoft Defender for Endpoint suppression rules. Hvis du vil forhindre, at der genereres beskeder for bestemte brugere, enheder eller postkasser, skal du ændre de tilsvarende forespørgsler for at udelukke disse enheder eksplicit.

Hvis du redigerer en regel på denne måde, bliver du bedt om at bekræfte, før disse ændringer anvendes.

Nye beskeder, der genereres af brugerdefinerede registreringsregler i Microsoft 365 Defender, vises på en beskedside med følgende oplysninger:

- Titel og beskrivelse for besked 
- På påvirkede aktiver
- Handlinger, der er foretaget som svar på beskeden
- Forespørgselsresultater, der udløste beskeden 
- Oplysninger om reglen til registrering af brugerdefineret 
 
> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Et eksempel på en påmindelsesside, der viser nye beskeder, der genereres af brugerdefinerede registreringsregler i Microsoft 365 Defender portal" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>Skrive forespørgsler uden DeviceAlertEvents

I Microsoft 365 Defender findes tabellerne `AlertInfo` `AlertEvidence` og disse for at tage højde for de forskellige sæt oplysninger, der følger med beskeder fra forskellige kilder. 

`DeviceAlertEvents` Hvis du vil have de samme oplysninger, du brugte til at få besked fra tabellen i skemaet for Microsoft Defender til slutpunkt, `AlertInfo` `ServiceSource` `AlertEvidence` skal du filtrere tabellen efter og derefter joinfornye hvert entydige id med tabellen, som indeholder detaljerede oplysninger om begivenheder og enheder. 

Se eksempelforespørgslen nedenfor:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Denne forespørgsel giver mange flere kolonner end `DeviceAlertEvents` i skemaet Microsoft Defender for Slutpunkt. For at holde resultaterne overskuelige skal du bruge `project` til kun at hente de kolonner, du er interesseret i. Eksemplet nedenfor projektkolonner, som kunne være interesseret i, når undersøgelsen registrerede PowerShell-aktivitet:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

Hvis du vil filtrere efter bestemte enheder, der er involveret i beskederne, `EntityType` kan du gøre det ved at angive enhedstypen og den værdi, du vil filtrere efter. Følgende eksempel søger efter en bestemt IP-adresse:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId 
| where EntityType == "Ip" and RemoteIP == "192.88.99.01" 
```

## <a name="see-also"></a>Se også
- [Slå Microsoft 365 Defender](advanced-hunting-query-language.md)
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Avanceret jagt i Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
