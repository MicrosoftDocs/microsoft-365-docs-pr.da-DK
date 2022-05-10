---
title: Få mere at vide om Administration af Microsoft Purview-datalivscyklus
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Få mere at vide om, hvordan Administration af Microsoft Purview-datalivscyklus hjælper dig med at bevare det, du har brug for, og slette det, du ikke har brug for.
ms.openlocfilehash: d5d91bef4332722d148bfdf136df03e75bb85734
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286861"
---
# <a name="learn-about-data-lifecycle-management"></a>Få mere at vide om administration af datalivscyklus

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Data Lifecycle Management (tidligere Microsoft Information Governance) giver dig værktøjer og funktioner til at bevare det indhold, du skal beholde, og slette det indhold, du ikke har. Det er ofte nødvendigt at bevare og slette indhold i forbindelse med overholdelse af angivne standarder og lovmæssige krav, men sletning af indhold, der ikke længere har forretningsmæssig værdi, hjælper dig også med at administrere risici og ansvar. Det reducerer f.eks. din angrebsoverflade.

**Opbevaringspolitikker** er hjørnestenen i administration af datalivscyklus. Brug disse politikker til Microsoft 365 arbejdsbelastninger, der omfatter Exchange, SharePoint, OneDrive, Teams og Yammer. Konfigurer, om indhold for disse tjenester skal bevares på ubestemt tid eller i en bestemt periode, hvis brugerne redigerer eller sletter det. Eller du kan konfigurere politikken til automatisk at slette indholdet permanent efter en angivet periode, hvis det ikke allerede er slettet. Du kan også kombinere disse to handlinger for at bevare og derefter slette, hvilket er en meget typisk konfiguration. Du kan f.eks. bevare mailen i tre år og derefter slette den.

Når du konfigurerer en opbevaringspolitik, kan du målrette alle instanser i din organisation (f.eks. alle postkasser og alle SharePoint websteder) eller individuelle forekomster (f.eks. kun postkasserne for bestemte afdelinger eller områder eller bare valgte SharePoint websteder).

Hvis du har brug for undtagelser for individuelle mails eller dokumenter, f.eks. en længere opbevaringsperiode for juridiske dokumenter, gør du dette med **opbevaringsmærkater** , som du publicerer til apps, så brugerne kan anvende dem eller automatisk anvende dem ved at undersøge indholdet.

Du kan finde flere oplysninger om opbevaringspolitikker og opbevaringsmærkater, og hvordan opbevaring fungerer i Microsoft 365, under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md). 

> [!NOTE]
> Hvis du har brug for at administrere elementer af høj værdi for forretningsrelaterede, juridiske eller lovmæssige krav til registrering, skal du bruge opbevaringsmærkater med [datastyring](records-management.md) i stedet for opbevaringsmærkater med administration af datalivscyklus.

Andre funktioner til administration af datalivscyklusser, der kan hjælpe dig med at bevare det, du har brug for, og slette det, du ikke har brug for:

- **Arkivering af postkasser** for at give brugerne ekstra lagerplads i postkassen og automatisk udvidelse af arkivering for postkasser, der har brug for mere end 100 GB lagerplads. En standardarkiveringspolitik flytter automatisk mail til arkivpostkassen, og hvis det er nødvendigt, kan du tilpasse denne politik. Du kan finde flere oplysninger om arkivering af [postkasser under Få mere at vide om arkivpostkasser](archive-mailboxes.md).
    
- **Inaktive postkasser** , der bevarer postkasseindhold, når medarbejdere forlader organisationen. Du kan finde flere oplysninger om inaktive postkasser under [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

- **Importér tjenesten for PST-filer** ved hjælp af netværksoverførsel eller drevforsendelse. Du kan finde flere oplysninger under [Få mere at vide om import af din organisations PST-filer](importing-pst-files-to-office-365.md).

## <a name="deployment-guidance"></a>Installationsvejledning

Du kan finde en installationsvejledning til administration af datalivscyklus, der omfatter en anbefalet oversigt over udrulning, licensoplysninger, tilladelser, en liste over understøttede scenarier og slutbrugerdokumentation under [Kom i gang med administration af datalivscyklus](get-started-with-information-governance.md).

Leder du efter udrulningsvejledning til beskyttelse af dine data? Se [Installér en løsning til beskyttelse af oplysninger med Microsoft Purview](information-protection-solution.md).

