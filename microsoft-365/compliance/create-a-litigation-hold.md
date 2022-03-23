---
title: Opret en retslig venteposition
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Få mere at vide om, hvordan du placerer en postkasse i retslig tilbageholdelse og bevarer alt postkasseindhold under en undersøgelse.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: d105813d7e34ece7641421bc7fed10919dda618e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587275"
---
# <a name="create-a-litigation-hold"></a>Opret en retslig venteposition

Du kan placere en postkasse i retslig tilbageholdelse for at bevare alt postkasseindhold, herunder slettede elementer og de oprindelige versioner af ændrede elementer. Når du placerer en brugerpostkasse i retslig venteposition, bevares indhold i brugerens arkivpostkasse (hvis den er aktiveret) også. Når du opretter en venteposition, kan du angive en varighed for venteposition (også kaldet tidsbaseret *venteposition*), så slettede og ændrede elementer bevares i en bestemt periode og derefter slettes permanent fra postkassen. Eller du kan blot bevare indhold på ubestemt tid (kaldet uendeligt *venteposition*), eller indtil retslig tilbageholdelse fjernes. Hvis du angiver en varighed af venteposition, beregnes den fra den dato, hvor meddelelsen modtages, eller et postkasseelement oprettes. 
  
Her er, hvad der sker, når du opretter en retslig venteposition.
  
- Elementer, der slettes permanent af brugeren, bevares i mappen genoprettelige elementer i brugerens postkasse i hele venteposition.

- Elementer, der er blevet slettet fra mappen Genoprettelige elementer af brugeren, bevares i venteposition.

- Lagerkvoten for mappen Genoprettelige elementer øges fra 30 GB til 110 GB.

- Elementer i brugerens primære og arkivpostkasser bevares

## <a name="assign-an-exchange-online-plan-2-license"></a>Tildele en Exchange Online Plan 2-licens

Hvis du vil placere Exchange Online postkasse i retslig venteposition, skal den være tildelt Exchange Online Plan 2-licens. Hvis en postkasse er tildelt en Exchange Online Plan 1-licens, skal du tildele den en separat Exchange Online-arkivering for at placere den i venteposition.

> [!NOTE]
> For Office 365 Education virksomheder understøttes retslig venteposition i Office 365 A1 abonnementer, som omfatter en Exchange Online Plan 1-licens med supplerende funktioner. Du kan finde flere oplysninger i afsnittet "Exchange Online funktioner" i [Office 365 Education tjenestebeskrivelse](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features).

## <a name="place-a-mailbox-on-litigation-hold"></a>Placere en postkasse i retslig venteposition

Her er trinnene til at placere en postkasse i retslig venteposition ved hjælp af Microsoft 365 Administration.

1. Gå til fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Microsoft 365 Administration</a> klik derefter på **UsersActive** >  users.

2. Vælg den bruger, du vil placere i retslig venteposition.

3. På pop op-siden med egenskaber skal du klikke på **fanen Mail** og derefter under Flere handlinger **klikke på** **Administrer retslig venteposition**.

   ![Klik på Administrer retslig venteposition på pop op-siden Mail på brugeregenskaber.](../media/M365AdminCenterLitHold1.png)

4. På pop **op-siden Administrer** retslige ventepositioner skal du markere **afkrydsningsfeltet** Aktiver retslig venteposition og derefter angive følgende valgfrie oplysninger:

    1. **Varighed af venteposition (dage)**: Brug dette felt til at oprette et tidsbaseret venteposition, og angiv, hvor lang tid postkasseelementer opbevares, når postkassen er sat i retslig venteposition. Varigheden beregnes ud fra den dato, hvor et postkasseelement modtages eller oprettes. Når ventepositionen udløber for et bestemt element, bevares det pågældende element ikke længere. Hvis du lader dette felt være tomt, bevares elementer på ubestemt tid, eller indtil ventepositionen fjernes. Brug dage til at angive varigheden.

    2. **Bemærk, at brugeren er synlig**: Brug dette felt til at informere brugeren om, at brugerens postkasse er i retslig venteposition. Noten vises på siden Kontooplysninger i brugerens postkasse, hvis de bruger Outlook 2010 eller nyere. Brugerne kan få adgang til denne side ved at **klikke på** Filer Outlook.

    3. **Webside med flere oplysninger for brugeren: Brug dette** felt til at dirigere brugeren til et websted for at få flere oplysninger om retslig venteposition. Denne URL-adresse vises på siden Kontooplysninger i brugerens postkasse, hvis de bruger Outlook 2010 eller nyere. Brugerne kan få adgang til denne side ved at **klikke på** Filer Outlook.

. Klik **på Gem ændringer** på pop **op-siden Retslig** venteposition for at oprette ventepositionen.

   Systemet viser et banner, der fortæller, at det kan tage op til 240 minutter, før ændringen træder i kraft.

### <a name="create-a-litigation-hold-using-powershell"></a>Opret en retslig venteposition ved hjælp af PowerShell

Du kan også oprette en retslig venteposition ved at køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

Den forrige kommando bevarer elementer på ubestemt tid, fordi varigheden af ventepositionen ikke er angivet. Hvis du vil oprette en tidsbaseret venteposition, skal du bruge følgende kommando:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Du kan også køre følgende kommando for at bekræfte, om postkassen er placeret i retslig venteposition:

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled
```

Værdien Sand angiver *,* at postkassen er i retslig venteposition/

Du kan få mere at vide [under Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Hvordan fungerer retslig venteposition?

I den normale arbejdsproces for slettede elementer flyttes et postkasseelement til undermappen Sletninger i mappen Genoprettelige elementer, når en bruger sletter det permanent (Skift +Delete) eller sletter det fra mappen Slettet post. En sletningspolitik (som er et opbevaringsmærke, der er konfigureret med en Slet-opbevaringshandling) flytter også elementer til undermappen til sletninger, når en opbevaringsperiode udløber. Når en bruger fjerner et element i mappen Genoprettelige elementer, eller når opbevaringsperioden for slettede elementer udløber for et element, flyttes det til undermappen Fjernet i mappen Genoprettelige elementer og markeres til permanent sletning. Den bliver fjernet Exchange næste gang postkassen behandles af MFA (Managed Folder Assistant).

Når en postkasse er placeret i retslig venteposition, bevares elementer i undermappen Fjernet i den venteposition, der er angivet i Retslig venteposition. Varigheden af ventepositionen beregnes ud fra den oprindelige dato, hvor et element blev modtaget eller oprettet, og definerer, hvor længe elementer i undermappen Fjernet opbevares. Når varigheden af ventepositionen udløber for et element i undermappen Fjernet, markeres elementet til permanent sletning og fjernes fra Exchange næste gang postkassen behandles af MFA'en. Hvis der er sat en ubestemt venteposition på en postkasse, vil elementer aldrig blive fjernet fra undermappen Fjernet.

Følgende illustration viser undermapperne i mapperne Genoprettelige elementer og arbejdsprocessen til venteposition.

![Livscyklus for retslig venteposition.](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> Hvis en venteposition, der er knyttet til en eDiscovery-sag, placeres i en postkasse, flyttes slettede elementer fra undermappen sletninger til undermappen DiscoveryHolds og bevares, indtil postkassen frigives fra eDiscovery-ventepositionen.
