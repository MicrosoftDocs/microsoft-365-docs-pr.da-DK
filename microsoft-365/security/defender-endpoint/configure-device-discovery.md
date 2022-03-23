---
title: Konfigurer enhedsregistrering
description: Få mere at vide om, hvordan du konfigurerer registrering af Microsoft 365 Defender ved hjælp af grundlæggende opdagelse eller standardregistrering
keywords: basic, standard, configure endpoint discovery, device discovery
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 77dbdb290a0f8643bd24e1a3c561b823e5c2e4b3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593834"
---
# <a name="configure-device-discovery"></a>Konfigurer enhedsregistrering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Opdagelse kan konfigureres til at være i standard- eller grundlæggende tilstand. Brug standardindstillingen til aktivt at finde enheder i dit netværk, hvilket bedre garanterer registrering af slutpunkter og giver mere omfattende enhedsklassificering.

Du kan tilpasse listen over enheder, der bruges til at udføre standardregistrering. Du kan enten aktivere standardregistrering på alle onboardede enheder, der også understøtter denne funktion (i øjeblikket – Windows 10 eller nyere og kun Windows Server 2019- eller nyere enheder), eller du kan vælge et undersæt eller undersæt af dine enheder ved at angive deres enhedsmærker.

## <a name="set-up-device-discovery"></a>Konfigurer enhedsregistrering

Du kan konfigurere enhedsregistrering ved at følge disse konfigurationstrin <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">i Microsoft 365 Defender portal</a>:

Naviger **til Indstillinger** >  **Device Discovery**

1. Hvis du vil konfigurere Grundlæggende som registreringstilstand til brug på dine onboardede enheder, skal du **vælge Grundlæggende** og derefter vælge **Gem**
2. Hvis du har valgt at bruge Standard discovery, skal du vælge, hvilke enheder der skal bruges til aktiv søgning: alle enheder eller på et undersæt ved at angive deres enhedsmærker, og vælg derefter **Gem**

> [!NOTE]
>Standardregistrering anvender forskellige PowerShell-scripts til aktivt at undersøge enheder i netværket. Disse PowerShell-scripts er Microsoft-signerede og udføres fra følgende placering: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps`. F.eks. `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\UnicastScannerV1.1.0.ps1`.

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>Undgå, at enheder aktivt skiftes ved standardregistrering

Hvis der er enheder på dit netværk, der ikke aktivt skal scannes (f.eks. enheder, der bruges som honningkager til et andet sikkerhedsværktøj), kan du også definere en liste over udeladelser for at forhindre dem i at blive scannet. Bemærk, at enheder stadig kan findes ved hjælp af tilstanden Grundlæggende opdagelse og også kan findes via forsøg på at finde multicasts. Disse enheder vil blive fundet passivt, men vil ikke aktivt blive fundet.

Du kan konfigurere de enheder, der skal **udelukkes, på siden Udeladelse** .

## <a name="select-networks-to-monitor"></a>Vælg netværk, der skal overvåges

Microsoft Defender til Slutpunkt analyserer et netværk og afgør, om det er et virksomhedsnetværk, der skal overvåges, eller et ikke-virksomhedsnetværk, der kan ignoreres. For at identificere et netværk som virksomhed korrelerer vi netværks-id'er på tværs af alle lejers klienter, og hvis størstedelen af enhederne i organisationen rapporterer, at de har forbindelse til det samme netværksnavn med den samme standardgateway og DHCP-serveradresse, antager vi, at dette er et virksomhedsnetværk. Virksomhedens netværk vælges typisk til overvågning. Du kan imidlertid tilsidesætte denne beslutning ved at vælge at overvåge ikke-virksomhedsnetværk, hvor onboardede enheder findes.

Du kan konfigurere, hvor enhedsregistrering kan udføres, ved at angive, hvilke netværk der skal overvåges. Når et netværk overvåges, kan der udføres enhedsregistrering på det.

En liste over netværk, hvor registrering af enheder kan udføres, vises på **siden Overvågede** netværk.

> [!NOTE]
> Listen viser netværk, der blev identificeret som virksomhedens netværk. Hvis mindre end 50 netværk identificeres som virksomhedens netværk, vises der op til 50 netværk med de fleste onboardede enheder på listen.

Listen over overvågede netværk sorteres baseret på det samlede antal enheder, der er set på netværket inden for de seneste 7 dage.

Du kan anvende et filter for at få vist en af følgende tilstande for netværksregistrering:

- **Overvågede netværk** – Netværk, hvor registrering af enheder udføres.
- **Ignorerede** netværk – Dette netværk ignoreres, og enhedsregistrering udføres ikke på det.
- **Alle** – både overvågede og ignorerede netværk vises.

### <a name="configure-the-network-monitor-state"></a>Konfigurere netværkovervågningstilstanden

Du styrer, hvor enhedsregistrering finder sted. Overvågede netværk er det sted, hvor registrering af enheder udføres, og det er typisk virksomhedens netværk. Du kan også vælge at ignorere netværk eller vælge den indledende registreringsklassifikation, når du har ændret en tilstand.

Når du vælger den indledende registreringsklassifikation, skal du anvende den systembaserede standardtilstand for netværksovervågning. Når du vælger den systembaserede standardovervågningstilstand, betyder det, at netværk, der blev identificeret som virksomhedens netværk, overvåges, og netværk, der identificeres som ikke-virksomhed, ignoreres automatisk.

1. Vælg **Indstillinger > Enhedsregistrering**.
2. Vælg **Overvågede netværk**.
3. Få vist listen over netværk.
4. Vælg de tre prik ud for navnet på netværket.
5. Vælg, om du vil overvåge, ignorere eller bruge den indledende registreringsklassifikation.

    > [!WARNING]
    >
    > - Hvis du vælger at overvåge et netværk, der ikke er identificeret af Microsoft Defender for Endpoint som et virksomhedsnetværk, kan det medføre registrering af enheder uden for virksomhedens netværk, og kan derfor registrere hjemmeenheder eller andre enheder, som ikke er virksomheder.
    > - Hvis du vælger at ignorere et netværk, stopper det med at overvåge og opdage enheder i det pågældende netværk. Enheder, der allerede blev fundet, vil ikke blive fjernet fra lageret, men vil ikke længere blive opdateret, og detaljer vil blive bevaret, indtil dataopbevaringsperioden for Defender til Slutpunkt udløber.
    > - Før du vælger at overvåge ikke-virksomhedsnetværk, skal du sikre dig, at du har tilladelse til at gøre dette. <br>

6. Bekræft, at du vil foretage ændringen.

## <a name="explore-devices-in-the-network"></a>Udforsk enheder i netværket

Du kan bruge følgende avancerede forespørgsel til at få mere kontekst om hvert netværksnavn, der er beskrevet på listen over netværk. I forespørgslen vises alle onboardede enheder, der blev forbundet til et bestemt netværk inden for de seneste 7 dage.

```kusto
DeviceNetworkInfo
| where Timestamp > ago(7d)
| where ConnectedNetworks  != ""
| extend ConnectedNetworksExp = parse_json(ConnectedNetworks)
| mv-expand bagexpansion = array ConnectedNetworks=ConnectedNetworksExp
| extend NetworkName = tostring(ConnectedNetworks ["Name"]), Description = tostring(ConnectedNetworks ["Description"]), NetworkCategory = tostring(ConnectedNetworks ["Category"])
| where NetworkName == "<your network name here>"
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="get-information-on-device"></a>Få oplysninger om enheden

Du kan bruge følgende avancerede forespørgsel til at få de seneste komplette oplysninger på en bestemt enhed.

```kusto
DeviceInfo
| where DeviceName == "<device name here>" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="see-also"></a>Se også

- [Oversigt over enhedsregistrering](device-discovery.md)
- [Ofte stillede spørgsmål om enhedsregistrering](device-discovery-faq.md)
