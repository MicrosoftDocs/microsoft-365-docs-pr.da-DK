---
title: Opret en retslig fastfrysning
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Få mere at vide om, hvordan du placerer en postkasse på Litigation-venteposition og bevarer alt postkasseindholdet under en undersøgelse.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: ddc55ef097a02c4005e2dcae2ca19fd673cc4c62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631067"
---
# <a name="create-a-litigation-hold"></a>Opret en retslig fastfrysning

Du kan placere en postkasse i strid med procesførelse for at bevare alt postkasseindhold, herunder slettede elementer og de oprindelige versioner af ændrede elementer. Når du placerer en brugerpostkasse i stridsposition, bevares indholdet i brugerens arkivpostkasse (hvis den er aktiveret). Når du opretter en venteposition, kan du angive en varighed af venteposition (også kaldet en *tidsbaseret venteposition*), så slettede og ændrede elementer bevares i en bestemt periode og derefter slettes permanent fra postkassen. Eller du kan bare bevare indhold på ubestemt tid (kaldet en *uendelig venteposition*), eller indtil bevarelse af procesførelse er fjernet. Hvis du angiver en varighedsperiode for venteposition, beregnes den ud fra den dato, hvor der modtages en meddelelse, eller der oprettes et postkasseelement. 
  
Her er, hvad der sker, når du opretter en procesførelsesventeposition.
  
- Elementer, der slettes permanent af brugeren, bevares i mappen Elementer, der kan gendannes, i brugerens postkasse, så længe ventepositionen varer.

- Elementer, der fjernes fra mappen Gendanbare elementer af brugeren, bevares i ventepositionens varighed.

- Lagerkvoten for mappen Gendanbare elementer er steget fra 30 GB til 110 GB.

- Elementer i brugerens primære og arkivpostkasser bevares

## <a name="assign-an-exchange-online-plan-2-license"></a>Tildel en Exchange Online Plan 2-licens

Hvis du vil placere en Exchange Online postkasse i stridsposition, skal den tildeles en Exchange Online Plan 2-licens. Hvis en postkasse tildeles en Exchange Online Plan 1-licens, skal du tildele den en separat Exchange Online-arkivering licens for at placere den i venteposition.

> [!NOTE]
> For Office 365 Education organisationer understøttes bevarelse af procesførelser i Office 365 A1 abonnementer, som omfatter en Exchange Online Plan 1-licens med supplerende funktioner. Du kan få flere oplysninger i afsnittet "Exchange Online funktioner" i [beskrivelsen af Office 365 Education-tjenesten](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features).

## <a name="place-a-mailbox-on-litigation-hold"></a>Placer en postkasse i stridsposition

Her er trinnene til at placere en postkasse i en procesførelsesposition ved hjælp af Microsoft 365 Administration.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Microsoft 365 Administration</a>, og klik derefter på **Brugere** > **Aktive brugere**.

2. Vælg den bruger, du vil placere i en procesførelsesventeposition.

3. Klik på fanen **Mail** på siden med egenskaber, og klik derefter på **Administrer venteposition for procesførelse** under **Flere handlinger**.

   ![Klik på Administrer procesførelse på fanen Mail på pop op-siden med brugeregenskaber.](../media/M365AdminCenterLitHold1.png)

4. På pop op-vinduet **Administrer procesførelse i venteposition** skal du markere afkrydsningsfeltet **Slå procesførelse til i venteposition** og derefter angive følgende valgfrie oplysninger:

    1. **Varighed af venteposition (dage)**: Brug dette felt til at oprette en tidsbaseret venteposition og angive, hvor længe postkasseelementer opbevares, når postkassen er sat i strid med procesførelse. Varigheden beregnes ud fra den dato, hvor et postkasseelement modtages eller oprettes. Når varigheden af ventepositionen udløber for et bestemt element, bevares elementet ikke længere. Hvis du lader feltet være tomt, bevares elementerne på ubestemt tid, eller indtil ventepositionen fjernes. Brug dage til at angive varigheden.

    2. **Bemærk, at brugeren er synlig**: Brug dette felt til at informere brugeren om, at postkassen er sat i procesposition. Noten vises på siden Kontooplysninger i brugerens postkasse, hvis brugeren bruger Outlook 2010 eller nyere. Brugerne kan klikke på **Filer** i Outlook for at få adgang til denne side.

    3. **Webside med flere oplysninger til brugeren**: Brug dette felt til at dirigere brugeren til et websted for at få flere oplysninger om bevarelse af procesførelse. Denne URL-adresse vises på siden Kontooplysninger i brugerens postkasse, hvis brugeren bruger Outlook 2010 eller nyere. Brugerne kan klikke på **Filer** i Outlook for at få adgang til denne side.

. Klik på **Gem ændringer** på pop op-siden **Procesførelse** for at oprette ventepositionen.

   Systemet viser et banner, hvor der står, at det kan tage op til 240 minutter, før ændringen træder i kraft.

### <a name="create-a-litigation-hold-using-powershell"></a>Opret en litigation-venteposition ved hjælp af PowerShell

Du kan også oprette en litigation-venteposition ved at køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

Den forrige kommando bevarer elementer på ubestemt tid, fordi varigheden af ventepositionen ikke er angivet. Hvis du vil oprette en tidsbaseret venteposition, skal du bruge følgende kommando:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Du kan også køre følgende kommando for at kontrollere, om postkassen er sat i strid med procesførelse:

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled
```

Værdien *True* angiver, at postkassen er i procesventevent/

Du kan få flere oplysninger under [Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Hvordan fungerer litigation?

I den normale arbejdsproces for slettede elementer flyttes et postkasseelement til undermappen Sletninger i mappen Gendan elementer, når en bruger permanent sletter det (Skift + Slet) eller sletter det fra mappen Slettet post. En politik for sletning (som er et opbevaringsmærke, der er konfigureret med en sletningsopbevaringshandling) flytter også elementer til undermappen Sletninger, når opbevaringsperioden udløber. Når en bruger fjerner et element i mappen Gendan elementer, eller når opbevaringsperioden for slettede elementer udløber for et element, flyttes det til undermappen Fjern elementer i mappen Genoprettelige elementer og er markeret til permanent sletning. Den fjernes fra Exchange, næste gang postkassen behandles af MFA (Managed Folder Assistant).

Når en postkasse er sat i venteposition for procesførelse, bevares elementer i undermappen Fjern i den venteposition, der er angivet i Litigation-ventepositionen. Varigheden af ventepositionen beregnes ud fra den oprindelige dato, hvor et element blev modtaget eller oprettet, og definerer, hvor længe elementer i undermappen Renser opbevares. Når varigheden af ventepositionen udløber for et element i undermappen Fjern, markeres elementet til permanent sletning og fjernes fra Exchange, næste gang postkassen behandles af MFA. Hvis der er placeret en ubestemt venteposition på en postkasse, fjernes elementer aldrig fra undermappen Fjern.

På følgende illustration vises undermapperne i mapperne Gendanbare elementer og arbejdsprocessen for venteposition.

![Procesførelse holder livscyklus.](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> Hvis en venteposition, der er knyttet til en eDiscovery-sag, placeres i en postkasse, flyttes fjernede elementer fra undermappen Sletninger til undermappen DiscoveryHolds og bevares, indtil postkassen frigives fra eDiscovery-ventepositionen.
