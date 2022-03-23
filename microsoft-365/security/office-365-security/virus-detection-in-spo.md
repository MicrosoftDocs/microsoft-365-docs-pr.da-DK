---
title: Indbygget virusbeskyttelse i SharePoint Online, OneDrive og Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Få mere at vide SharePoint Online registrerer virus i filer, som brugere overfører og forhindrer brugere i at hente eller synkronisere filerne.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ddb424458e991becefb98efbad5b2a86c5f9441c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587519"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Indbygget virusbeskyttelse i SharePoint Online, OneDrive og Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)

Microsoft 365 bruger et almindeligt virusdetektionsprogram til scanning af filer, som brugere overfører til SharePoint Online, OneDrive og Microsoft Teams. Denne beskyttelse er inkluderet i alle abonnementer, der SharePoint online, OneDrive og Microsoft Teams.

> [!IMPORTANT]
> De indbyggede antivirusfunktioner er en metode til at hjælpe med at inddæmme virusser. De skal ikke bruges som et enkelt forsvarspunkt mod malware i dit miljø. Vi opfordrer alle kunder til at undersøge og implementere beskyttelse mod malware på forskellige lag og anvende bedste fremgangsmåder for sikring af deres virksomhedsinfrastruktur. Du kan finde flere oplysninger om strategier og bedste fremgangsmåder under [Oversigt over sikkerhed](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Hvad sker der, hvis en inficeret fil overføres til SharePoint Online?

Virusdetektionsprogrammet Microsoft 365 køre asynkront (uafhængigt af filoverførsler) i SharePoint Online. **Alle filer scannes ikke automatisk**. Heuristics afgør, hvilke filer der skal scannes. Når der findes en fil, der indeholder en virus, markeres filen med flag. I april 2018 fjernede vi grænsen på 25 MB for scannede filer.

Der sker følgende:

1. En bruger overfører en fil til SharePoint Online.
2. SharePoint Online som en del af sine virusscanningsprocesser afgør senere, om filen opfylder kriterierne for en scanning.
3. Hvis filen opfylder kriterierne for en scanning, scanner virusdetektionsprogrammet filen.
4. Hvis der findes en virus i den scannede fil, indstiller virusprogrammet en egenskab i filen, der angiver, at den er inficeret.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Hvad sker der, når en bruger forsøger at downloade en inficeret fil ved hjælp af browseren?

Hvis en fil er inficeret, kan brugere ikke downloade filen fra SharePoint Online ved hjælp af en browser.

Der sker følgende:

1. En bruger åbner en webbrowser og forsøger at downloade en inficeret fil fra SharePoint Online.
2. Brugeren får en advarsel om, at der er detekteret en virus. Som standard har brugeren mulighed for at downloade filen og forsøge at rense den ved hjælp af antivirussoftwaren på sin egen enhed.

> [!NOTE]
>
> Administratorer kan bruge parameteren *DisallowInfectedFileDownload* på [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/Set-SPOTenant) i SharePoint Online PowerShell til at forhindre brugere i at downloade inficeret filer, selv i vinduet med advarsel om antivirus. Du kan finde en vejledning [under Brug SharePoint Online PowerShell til at forhindre brugere i at downloade skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).
>
> Så snart du aktiverer parameteren *DisallowInfectedFileDownload* , blokeres adgangen til de registrerede/blokerede filer helt for brugere og administratorer.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Hvad sker der, når OneDrive-synkronisering forsøger at synkronisere en inficeret fil?

Når en skadelig fil uploades til OneDrive, synkroniseres den til den lokale computer, før den markeres som malware. Når den er markeret som malware, kan brugeren ikke længere åbne den synkroniserede fil fra sin lokale computer.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Udvidede funktioner med Microsoft Defender til Office 365

Microsoft 365 organisationer, der har [Microsoft Defender til Office 365](defender-for-office-365.md) inkluderet i deres abonnement eller købt som et tilføjelsesprogrammet, kan aktivere Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams for forbedret rapportering og beskyttelse. Du kan finde flere oplysninger [Pengeskab vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>Relaterede artikler

[Beskyttelse mod malware og ransomware i Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

Du kan finde flere oplysninger om antivirus i SharePoint Online, OneDrive og Microsoft Teams i Beskyt mod trusler og Slå [](protect-against-threats.md) [Pengeskab Vedhæftede filer til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).
