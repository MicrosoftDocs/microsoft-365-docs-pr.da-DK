---
title: Multi-Geo Capabilities in Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: Få mere at vide Teams, hvordan Microsoft 365 fungerer med Microsoft 365 Multi-Geo.
ms.openlocfilehash: 0315a9ff0429c5e00c662bd7345a3b6a39a591c3
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63593330"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>Multi-Geo-funktioner i Microsoft Teams

Multi-Geo capabilities in Teams enable Teams chat data to be stored at rest in a specified geo location. Chatdata består af chatmeddelelser, herunder private beskeder, kanalmeddelelser og billeder, der bruges i chatsamtaler.

Teams bruger foretrukken dataplacering (PDL) til brugere og grupper til at bestemme, hvor data skal lagres. Hvis PDL'en ikke er angivet eller er ugyldig, gemmes data på lejerens centrale placering.

> [!NOTE]
> Multi-Geo-funktioner i Teams udrulles i juli 2021. Dine chat- og kanalmeddelelser overføres automatisk til den korrekte geoplacering i løbet af de næste par kvartaler. Alle nye PDL-ændringer behandles, når lejeren har fuldført den indledende synkronisering, og nye PDL-ændringer ud over dette vil blive sat i kø og behandlet i den rækkefølge, de modtages.

## <a name="user-chat"></a>Brugerchat

Brugerchat omfatter en-til-en, en-til-mange og private mødemeddelelser.

Når en ny bruger oprettes, Teams læser brugerens PDL og gemmer alle deres chatdata på den pågældende geoplacering.

For eksisterende brugere føjes den pågældende brugers chatdata til en overførselskøen, så de kan flyttes til den angivne geoplacering, hvis en administrator tilføjer eller ændrer PDL for en bruger.

Lagerplaceringen for en en til en- eller en til mange-chat er baseret på PDL'en for den person, der oprettede chatten. Hvis den pågældende brugers PDL ændres, overføres chatten til den nye geoplacering. Lagerplaceringen for en mødechat er baseret på PDL'en for mødearrangøren.

Hvis du vil finde den aktuelle placering af en Teams, skal du [oprette forbindelse Teams PowerShell](/powershell/module/teams/connect-microsoftteams) og køre følgende kommando:

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>Kanalmeddelelser

Hver Microsoft 365 gruppe har en foretrukken dataplacering (PDL), som angiver den geoplacering, hvor relaterede data skal gemmes. Teams PDF-filen for den gruppe, der er knyttet til hvert team, til at bestemme, hvor teamets kanalmeddelelsesdata skal lagres. Dette omfatter private kanaler og chat, der foregår i et kanalmøde.

Når en bruger opretter et nyt team, bestemmer brugerens PDL, hvad PDL er tildelt til Microsoft 365 gruppe. Gruppen PDL bestemmer, hvor teamets data gemmes. Hvis den pågældende brugers PDL senere ændres, ændres gruppens PDL ikke.

For eksisterende teams tilføjes eller ændres PDL for den Microsoft 365-gruppe, der er tilbage for et team, føjes teamets kanalmeddelelsesdata til en overførselskøen, så de flyttes til den angivne geoplacering.

Ændring af PDF-filen for Microsoft 365 gruppekøer dataene i Teams at overføre til den valgte placering. Dette overfører dog ikke automatisk det eller SharePoint websted eller de filer, der er knyttet til gruppen. Du skal flytte webstedet separat ved at følge procedurerne i Flytte [et SharePoint websted til en anden geoplacering](/microsoft-365/enterprise/move-sharepoint-between-geo-locations). Sørg for at udføre begge trin for at Teams data og SharePoint data for én gruppe på forskellige steder.

Hvis du vil finde den aktuelle placering af et teams data, skal du [oprette forbindelse Teams PowerShell](/powershell/module/teams/connect-microsoftteams) og køre følgende kommando:

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>Brugeroplevelse

Teams Multi-Geo problemfrit for slutbrugeren. Når du ændrer PDF-filen for en bruger eller gruppe, sættes de respektive data i kø til overførsel, og overførslen sker automatisk uden nogen indvirkning for brugeren eller brugerens Teams-klient, selvom de er aktive, mens overførslen sker.

## <a name="see-also"></a>Se også

[Microsoft 365 multi-geo-lejerkonfiguration](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[Administration af et multi-geo-miljø](administering-a-multi-geo-environment.md)

[Administration Exchange Online postkasser i et multi-geo-miljø](administering-exchange-online-multi-geo.md)
