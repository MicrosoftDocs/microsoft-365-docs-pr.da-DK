---
title: Kom i gang med fejlfindingstilstand i Microsoft Defender for Endpoint
description: Aktivér Microsoft Defender for Endpoint fejlfindingstilstand for at løse forskellige antivirusproblemer.
keywords: antivirus, fejlfinding, fejlfindingstilstand, manipulationsbeskyttelse, kompatibilitet
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: eee3e07825b2775b4eff1b5fb45a6e1f86fc3a1b
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858839"
---
# <a name="get-started-with-troubleshooting-mode-in-microsoft-defender-for-endpoint"></a>Kom i gang med fejlfindingstilstand i Microsoft Defender for Endpoint 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Microsoft Defender for Endpoint fejlfindingstilstand giver dig mulighed for at foretage fejlfinding af forskellige Microsoft Defender-antivirusfunktioner ved at aktivere dem fra enheden og teste forskellige scenarier, også selvom de styres af organisationspolitikken. Fejlfindingstilstanden er deaktiveret som standard og kræver, at du aktiverer den for en enhed (og/eller gruppe af enheder) i en begrænset periode. Bemærk, at dette udelukkende er en funktion, der kun er til virksomheder, og som kræver Microsoft 365 Defender adgang.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Brug fejlfindingstilstand til at deaktivere/ændre den indstilling for beskyttelse mod ændring, der skal udføres:

  - Funktionel fejlfinding /programkompatibilitet i Microsoft Defender Antivirus (falske positive programblokke).
  - Fejlfinding af ydeevnen i Microsoft Defender Antivirus ved hjælp af fejlfindingstilstand og manipulation af beskyttelse mod ændring og andre antivirusindstillinger.

- Hvis der opstår en ændringshændelse (f.eks. ændres eller slettes snapshottet `MpPreference` ), afsluttes fejlfindingstilstanden, og beskyttelse mod ændring aktiveres på enheden.

- Lokale administratorer med de relevante tilladelser kan ændre konfigurationer for individuelle slutpunkter, der normalt er låst af en politik. Det kan være nyttigt at have en enhed i fejlfindingstilstand, når du diagnosticerer ydeevne- og kompatibilitetsscenarier for Microsoft Defender Antivirus.

  - Lokale administratorer kan ikke deaktivere Microsoft Defender Antivirus eller fjerne det.
  - Lokale administratorer kan konfigurere alle andre sikkerhedsindstillinger i Microsoft Defender Antivirus-pakken (f.eks. cloudbeskyttelse, manipulationsbeskyttelse).

- Administratorer med tilladelserne "Administrer sikkerhedsindstillinger" har adgang til at aktivere fejlfindingstilstand.

- Microsoft Defender for Endpoint indsamler logge og undersøgelsesdata i hele fejlfindingsprocessen.

  - Snapshot af `MpPreference` tages, før fejlfindingstilstanden starter.
  - Det andet snapshot tages, lige før fejlfindingstilstanden udløber.
  - Der indsamles også driftslogge fra under fejlfindingstilstand.

  - Alle ovenstående logge og snapshots indsamles og vil være tilgængelige for en administrator, der kan indsamle ved hjælp af funktionen [Indsaml undersøgelsespakke](respond-machine-alerts.md#collect-investigation-package-from-devices) på enhedssiden. Bemærk, at Microsoft ikke fjerner disse data fra enheden, før en administrator indsamler dem.

- Administratorer kan også gennemse de ændringer i indstillinger, der sker i fejlfindingstilstand i **Logbog** på enhedssiden.

- Fejlfindingstilstanden slukkes automatisk, når udløbstiden er nået (den varer i 3 timer). Efter udløb bliver alle politikadministrerede konfigurationer skrivebeskyttet igen og vender tilbage til, hvordan det var, før fejlfindingstilstanden blev slået til.

- Det kan tage op til 15 minutter fra det tidspunkt, hvor kommandoen sendes fra Microsoft 365 Defender, til den bliver aktiv på enheden.

- Meddelelsen sendes til slutbrugeren, når fejlfindingstilstanden starter, og når fejlfindingstilstanden slutter. Der sendes også en advarsel, der giver besked om, at den snart slutter.

- Starten og slutningen af fejlfindingstilstanden identificeres på **enhedens tidslinje** på enhedssiden.

- Du kan forespørge om alle fejlfindingstilstandshændelser i avanceret jagt.

> [!NOTE]
> Ændringer i politikstyring anvendes på computeren, når den aktivt er i fejlfindingstilstand. Ændringerne træder dog først i kraft, når fejlfindingstilstanden udløber. Derudover anvendes opdateringer af Microsoft Defender Antivirus Platform ikke under fejlfindingstilstand. Platformopdateringer anvendes, når fejlfindingstilstanden slutter med en Windows-opdatering.

## <a name="prerequisites"></a>Forudsætninger

- En enhed, der kører Windows 10 (version 19044.1618 eller nyere), Windows 11, Windows Server 2019 eller Windows Server 2022.

  Semester/Redstone|Operativsystemversion|Udgivelse
  :---|:---|:---
  21H2/SV1|>=22000.593|[KB5011563: Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011563)
  20H1/20H2/21H1|>=19042.1620<br/> >=19041.1620<br/> >=19043.1620|[KB5011543: Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011543)
  Windows Server 2022|>=20348.617|[KB5011558: Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011558)
  Windows Server 2019 (RS5)|>=17763.2746|[KB5011551: Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011551)

- Hvis fejlfindingstilstanden skal anvendes, skal Microsoft Defender for Endpoint være tilmeldt af lejeren og være aktiv på enheden.

- Enheden skal aktivt køre Microsoft Defender Antivirus, version 4.18.2203 eller nyere.

## <a name="enable-the-troubleshooting-mode"></a>Aktivér fejlfindingstilstanden

1. Gå til Microsoft 365 Defender-portalen (<https://security.microsoft.com>), og log på.

2. Gå til enhedssiden/maskinsiden for den enhed, du vil aktivere fejlfindingstilstand for. Vælg **Slå fejlfindingstilstand til**. Bemærk, at dette kræver tilladelserne "Administrer sikkerhedsindstillinger i Security Center" for Microsoft Defender for Endpoint.

   :::image type="content" source="../../media/ts-mode-menu.png" alt-text="Slå fejlfindingstilstand til" lightbox="../../media/ts-mode-menu.png":::

3. Bekræft, at du vil aktivere fejlfindingstilstand for enheden.

   :::image type="content" source="../../media/ts-mode-conf-flyout.png" alt-text="Konfigurations-pop op-vinduet" lightbox="../../media/ts-mode-conf-flyout.png":::

4. Enhedssiden viser, at enheden nu er i fejlfindingstilstand.

   :::image type="content" source="../../media/ts-mode-option-greyed-out.png" alt-text="Enheden er nu i fejlfindingstilstand" lightbox="../../media/ts-mode-option-greyed-out.png":::

## <a name="advanced-hunting-queries"></a>Avancerede jagtforespørgsler

Her er nogle færdigbyggede avancerede jagtforespørgsler, der giver dig indblik i de fejlfindingshændelser, der forekommer i dit miljø. Du kan også bruge disse forespørgsler til at [oprette registreringsregler](/defender/custom-detection-rules.md#create-a-custom-detection-rule) , der giver dig besked, når enhederne er i fejlfindingstilstand.

### <a name="get-troubleshooting-events-for-a-particular-device"></a>Hent fejlfindingshændelser for en bestemt enhed
Søg efter deviceId eller deviceName ved at udkommentere de respektive linjer.  
```kusto
//let deviceName = "<deviceName>";   // update with device name
let deviceId = "<deviceID>";   // update with device id
DeviceEvents
| where DeviceId == deviceId
//| where DeviceName  == deviceName
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| project Timestamp,DeviceId, DeviceName, _tsmodeproperties,
 _tsmodeproperties.TroubleshootingState, _tsmodeproperties.TroubleshootingPreviousState, _tsmodeproperties.TroubleshootingStartTime,
 _tsmodeproperties.TroubleshootingStateExpiry, _tsmodeproperties.TroubleshootingStateRemainingMinutes,
 _tsmodeproperties.TroubleshootingStateChangeReason, _tsmodeproperties.TroubleshootingStateChangeSource
```

### <a name="devices-currently-in-troubleshooting-mode"></a>Enheder i øjeblikket i fejlfindingstilstand  

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
|summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| order by Timestamp desc
```

### <a name="count-of-troubleshooting-mode-instances-by-device"></a>Antal forekomster af fejlfindingstilstand efter enhed

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(30d)  // choose the date range you want
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| sort by count_
```

### <a name="total-count"></a>Samlet antal

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(2d) //beginning of time range
| where Timestamp < ago(1d) //end of time range
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count()
| where count_ > 5          // choose your max # of TS mode instances for your time range
```

## <a name="related-topic"></a>Relateret emne

- [Scenarier for fejlfindingstilstand](troubleshooting-mode-scenarios.md)
- [Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md)
