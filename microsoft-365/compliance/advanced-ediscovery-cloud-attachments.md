---
title: Indsaml vedhæftede filer i skyen i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Brug samlinger i Microsoft Purview eDiscovery (Premium) til at indsamle vedhæftede filer i skyen til gennemsyn i en undersøgelse eller sag.
ms.openlocfilehash: 0a0d3dab3942dbdfcfa896d8e2f59fd2e2dca813
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935714"
---
# <a name="collect-cloud-attachments-in-microsoft-purview-ediscovery-premium-preview"></a>Indsaml vedhæftede filer i skyen i Microsoft Purview eDiscovery (Premium) (prøveversion)

Vedhæftede filer i skyen er links til dokumenter, der typisk gemmes på SharePoint websted og OneDrive. Så i stedet for at vedhæfte en faktisk kopi af et dokument i en mail eller en Teams chatsamtale, har du mulighed for at dele et link til filen. Vedhæftede filer i skyen er en effektiv måde at dele dokumenter og samarbejde med andre i din organisation på. Men vedhæftede filer i skyen udgør udfordringer under eDiscovery-arbejdsprocessen, fordi det kun er linket til vedhæftede filer i skyen og ikke det faktiske indhold i det delte dokument, der returneres i en eDiscovery-søgning. For at løse denne udfordring indeholder eDiscovery (Premium) to løsninger til indsamling af vedhæftede filer i skyen:  

- Indsamling af den direkte version af et dokument, der er knyttet til i en vedhæftet fil i skyen.

- Indsamler versionen af dokumentet på det tidspunkt, det blev delt i en vedhæftet fil i skyen.

## <a name="collecting-cloud-attachments"></a>Indsamling af vedhæftede filer i skyen

Når du opretter en kladdesamling, og søgeresultaterne indeholder elementer, der indeholder vedhæftede filer i skyen, skal du have mulighed for at indsamle målet for den vedhæftede fil i skyen, når du overfører kladdesamlingen til et korrektursæt. Når du vælger denne indstilling, føjer eDiscovery (Premium) de dokumenter, der er sammenkædet med i den vedhæftede fil i skyen, til korrektursættet. Dette giver dig mulighed for at gennemse destinationsdokumenterne og afgøre, om dokumentet er relevant for din sag eller undersøgelse.

På følgende skærmbillede kan du se muligheden for at inkludere mål for vedhæftede filer i skyen, når du sender en samling til et korrektursæt.

![Muligheden for at inkludere vedhæftede filer i skyen, når en samling bindes til et anmeldelsessæt](../media/CollectCloudAttachments1.png)

> [!NOTE]
>- Hvis du bruger det [nye sagsformat](advanced-ediscovery-new-case-format.md) i eDiscovery (Premium), er indstillingen til at medtage vedhæftede filer i skyen i korrektursættet valgt som standard og kan ikke fjernes.<br/>
>- Du har også mulighed for at inkludere alle versioner (ud over den version, der blev delt) af vedhæftede filer i skyen i korrektursættet.  
Hvis du vil have en vejledning i, hvordan du sender en samling til et korrektursæt, skal du se [Anvend en kladdesamling på et korrektursæt](commit-draft-collection.md).

## <a name="collecting-the-version-shared-in-a-cloud-attachment"></a>Indsamling af den version, der deles i en vedhæftet fil i skyen

EDiscovery-arbejdsprocessen (Premium) til indsamling af vedhæftede filer i skyen omfatter kun tilføjelse af den nyeste version af en vedhæftet fil i skyen i et korrektursæt. Det betyder, at den version, der indsamles og føjes til et korrektursæt, kan være anderledes end den version, der oprindeligt blev delt i den vedhæftede fil i cloudmiljøet. Det er derfor muligt, at indhold, der var til stede i den vedhæftede fil i skyen på det tidspunkt, den blev delt, er fjernet og ikke findes i den aktuelle version, der er føjet til korrektursættet.

Organisationer har nu mulighed for at bruge Microsoft 365 opbevaringsmærkater til at bevare versionen af et dokument på det tidspunkt, hvor det blev delt som en vedhæftet fil i skyen. For at gøre dette kan din organisation oprette en opbevaringsmærkat, vælge indstillingen Anvend mærkaten på vedhæftede filer i skyen og derefter automatisk anvende mærkaten på dokumenter, der er gemt i SharePoint og OneDrive. Når du har konfigureret denne konfiguration, oprettes der en kopi af et dokument på det tidspunkt, hvor filen deles. Hvis dokumentet ændres og deles igen som en vedhæftet fil i skyen, bevares den ændrede version også. Hvis filen ændres og deles igen, bevares en ny kopi af filen som en ny version.

Hvis du bevarer de delte versioner af vedhæftede filer i skyen, kan det hjælpe din organisation med at sikre bevarelse og samling af potentielt relevant indhold i den specifikke version af dokumentet, der blev delt i stedet for den aktuelle liveversion. Når du har implementeret denne opbevaringsløsning, indsamles både den aktuelle liveversion af en vedhæftet fil i skyen og den version, der blev delt i den vedhæftede fil i cloudmiljøet, og føjes til et korrektursæt.

Du kan finde oplysninger om, hvordan du konfigurerer en opbevaringsmærkat og automatisk anvender den på vedhæftede filer i skyen, under [Anvend automatisk mærkater på vedhæftede filer i skyen](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments).

På følgende skærmbillede kan du se et vedhæftet dokument i skyen med navnet *XYZ Research.docx*, der blev føjet til et korrektursæt. Dokumentet blev delt som en vedhæftet fil i skyen i en chatsamtale Teams. Korrektursættet indeholder også den version, der oprindeligt blev delt i den vedhæftede fil i skyen. Bemærk, at navnet på denne version af den vedhæftede fil i skyen genereres af systemet, og forfatteren identificeres som **SharePoint**.

![Den version af en vedhæftet fil i skyen, der blev delt, og som blev vist i et anmeldelsessæt](../media/CollectCloudAttachments2.png)

Desuden har den aktuelle liveversion og den version, der blev delt, den samme **FamilyId-egenskabsværdi**, som er det samme som **FamilyId** for det overordnede objekt (f.eks. en mail eller en Teams chatsamtale). Det giver dig mulighed for at gruppere vedhæftede filer i skyen med det element, hvor de blev delt.

Når du har implementeret opbevaringsmærkaten og automatisk anvender mærkaten på SharePoint dokumenter, vælger du stadig muligheden for at indsamle vedhæftede filer i skyen, når du sender en kladdesamling til et korrektursæt. Når vedhæftede filer i skyen indsamles, føjes både den aktuelle liveversion og den version, der oprindeligt blev delt, til korrektursættet.
