---
title: Få mere at vide om automatisk udvidelse af arkivering
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 37cdbb02-a24a-4093-8bdb-2a7f0b3a19ee
description: Få mere at vide om automatisk udvidelse af arkivering, som giver ekstra arkivlager til Exchange Online-postkasser.
ms.openlocfilehash: fc3e40e72ad287e7d7e696557422420cccbd4ee1
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922433"
---
# <a name="learn-about-auto-expanding-archiving"></a>Få mere at vide om automatisk udvidelse af arkivering

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I Office 365 giver arkivpostkasser brugerne ekstra lagerplads på postkassen. Når en brugers arkivpostkasse er aktiveret, er der op til 100 GB ekstra lagerplads tilgængelig. Tidligere, da lagerkvoten på 100 GB blev nået, måtte organisationer kontakte Microsoft for at anmode om ekstra lagerplads til en arkivpostkasse. Det er ikke længere tilfældet.

Arkiveringsfunktionen i Microsoft 365 (kaldet *automatisk udvidelse af arkivering*) leverer op til 1,5 TB ekstra lagerplads i arkivpostkasser. Når lagerkvoten i arkivpostkassen er nået, øger Microsoft 365 automatisk (og trinvist) arkivets størrelse, indtil arkivpostkassen når 1,5 TB.

Du kan finde en trinvis vejledning i, hvordan du aktiverer automatisk udvidelse af arkivering, under [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).

> [!NOTE]
> Arkivering, der automatisk udvides, understøtter også delte postkasser. Hvis du vil aktivere arkivet for en delt postkasse, kræves der en Exchange Online Plan 2-licens eller en Exchange Online Plan 1-licens med en Exchange Online-arkiveringslicens.

## <a name="how-auto-expanding-archiving-works"></a>Sådan fungerer automatisk udvidelse af arkivering

Som tidligere forklaret, oprettes der ekstra lagerplads i postkassen, når en brugers arkivpostkasse er aktiveret. Når automatisk udvidelse af arkivering er aktiveret, kontrollerer Microsoft 365 jævnligt størrelsen af arkivpostkassen. Når en arkivpostkasse nærmer sig sin lagergrænse, opretter Microsoft 365 automatisk ekstra lagerplads til arkivet. Hvis brugeren løber tør for denne ekstra lagerplads, føjer Microsoft 365 mere lagerplads til brugerens arkiv. Denne proces fortsætter, indtil brugerens arkiv når en størrelse på 1,5 TB. Denne proces sker automatisk, hvilket betyder, at administratorer ikke behøver at anmode om yderligere arkivlager eller administrere automatisk udvidelse af arkivering.

Her er et hurtigt overblik over processen.

![Oversigt over arkiveringsprocessen, der automatisk udvides.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. Arkivering er aktiveret for en brugerpostkasse eller en delt postkasse. Der oprettes en arkivpostkasse med 100 GB lagerplads, og advarselskvoten for arkivpostkassen er indstillet til 90 GB.

2. En administrator aktiverer automatisk udvidelse af arkivering for postkassen. Hvis postkassen har en politik for bevarelse eller bevarelse anvendt på den, øges lagerkvoten for arkivpostkassen til 110 GB, og kvoten for arkivadvarsel øges til 100 GB.
    
    Når arkivpostkassen (herunder mappen Gendan elementer) når sin lagerkvote, konverteres arkivpostkassen derefter til et arkiv, der automatisk udvides. Der tilføjes ekstra lagerplads, indtil den når en maksimal størrelse på 1,5 TB. Det kan tage op til 30 dage, før den ekstra lagerplads klargøres.

3. Microsoft 365 tilføjer automatisk mere lagerplads, når det er nødvendigt.

> [!IMPORTANT]
> Automatisk udvidelse af arkivering understøttes kun for postkasser, der bruges til individuelle brugere (eller delte postkasser) med en vækstrate, der ikke overstiger 1 GB pr. dag. En brugers arkivpostkasse er kun beregnet til den pågældende bruger. Det er ikke tilladt at bruge journaling, transportregler eller regler for automatisk videresendelse til kopiering af meddelelser til en arkivpostkasse. Microsoft forbeholder sig ret til at nægte yderligere arkivering i tilfælde, hvor en brugers arkivpostkasse bruges til at gemme arkivdata for andre brugere eller i andre tilfælde af upassende brug.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Hvad flyttes til den ekstra lagerplads til arkivet?

Mapper kan blive flyttet for at gøre effektiv brug af automatisk udvidelse af arkivlageret. Microsoft 365 bestemmer, hvilke mapper der flyttes, når der føjes ekstra lagerplads til arkivet. Når en mappe flyttes, oprettes der nogle gange automatisk en eller flere undermapper, og elementer fra den oprindelige mappe distribueres til disse mapper for at lette flytningen. Når du får vist arkivdelen af mappelisten i Outlook, vises disse undermapper under den oprindelige mappe. Den navngivningskonvention, som Microsoft 365 bruger til at navngive disse undermapper, er **\<folder name\>_yyyy (oprettet på mmm dd, yyyy h_mm)**, hvor:

- **yyyy** er det år, meddelelserne i mappen blev modtaget.

- **mmm dd, yyyy h_m** er den dato og det klokkeslæt, hvor undermappen blev oprettet af Office 365 i UTC-format, baseret på brugerens tidszone og internationale indstillinger i Outlook.

På følgende skærmbilleder vises en mappeliste før og efter, at meddelelser flyttes til et arkiv, der automatisk er udvidet.

 **Før ekstra lagerplads tilføjes**

![Mappeliste over arkivpostkasser, før arkivet til automatisk udvidelse klargøres.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Når der er tilføjet ekstra lagerplads**

![Mappeliste over arkivpostkasse, når arkivet til automatisk udvidelse er klargjort.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Som tidligere beskrevet flytter Microsoft 365 elementer til undermapper (og navngiver dem ved hjælp af navngivningskonventionen, der er beskrevet ovenfor) for at hjælpe med at distribuere indhold til et hjælpearkiv. Men det er ikke altid tilfældet at flytte elementer til undermapper. Nogle gange kan en hel mappe flyttes til et hjælpearkiv. I dette tilfælde bevarer mappen det oprindelige navn.  Det vil ikke være synligt på mappelisten i Outlook, at mappen er flyttet til et hjælpearkiv.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Outlook-krav til adgang til elementer i et automatisk udvidet arkiv

Brugerne skal bruge en af følgende Outlook-klienter for at få adgang til meddelelser, der er gemt i et automatisk udvidet arkiv:

- Outlook som en del af Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus)

- Outlook som en del af Microsoft 365 Apps for business (tidligere kaldet Office 365 Business)

- Outlook 2016 eller Outlook 2019 til Windows

- Outlook på internettet

- Outlook 2016 eller Outlook 2019 til Mac

Her er nogle ting, du skal overveje, når du bruger Outlook eller Outlook på internettet til at få adgang til meddelelser, der er gemt i et automatisk udvidet arkiv.

- Du kan få adgang til alle mapper i arkivpostkassen, herunder dem, der er flyttet til det automatisk udvidede lagerområde.

- Hvis en arkivpostkasse har mindst ét automatisk udvidet lagerområde, kan du ikke slette en mappe fra arkivpostkassen eller fra hjælpearkivet. Det vil sige, at når der er klargjort et automatisk udvidet lagerområde, kan du ikke slette nogen mapper i arkivet.

- Du kan slette elementer i et automatisk udvidet lagerområde. Du kan dog ikke bruge funktionen Gendan slettet post til at gendanne et element, når automatisk udvidelse af arkivering er aktiveret for en postkasse.

- Søg efter automatisk udvidet arkivering er tilgængelig i Outlook til internettet (OWA). På samme måde som med Onlinearkiv kan du søge efter elementer, der er flyttet til et ekstra lagerområde. Når arkivet er valgt som søgeområde i OWA, søges der i alle arkiver (herunder automatisk udvidede arkiver) og deres tilsvarende undermapper. Bemærk, at søgning ikke understøttes for funktionen automatisk udvidet arkiv i en arkivsituation, der kun findes i skyen (primær postkasse stadig i det lokale miljø).

- Automatisk udvidet arkivsøgning er tilgængelig i Outlook til Windows i Månedlig Enterprise-kanal. Med denne opdatering er området Aktuel postkasse tilgængeligt, så du kan søge i det automatisk udvidede arkiv. Bemærk, at søgning ikke understøttes for funktionen automatisk udvidet arkiv i en arkivsituation, der kun findes i skyen (primær postkasse stadig i det lokale miljø). Du kan finde flere oplysninger om dette og andre supportfunktioner til Microsoft Search under [Sådan bruger Outlook til Windows forbindelse til Exchange Online Microsoft Search](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045). 

- Antallet af elementer i Outlook og antal læste/ulæste (i Outlook og Outlook på internettet) i et arkiv, der automatisk udvides, er muligvis ikke nøjagtige.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Arkivering og andre funktioner til overholdelse af angivne standarder, der automatisk udvides

I dette afsnit forklares funktionaliteten mellem automatisk udvidelse af arkivering og andre funktioner til overholdelse af angivne standarder og datastyring.

- **eDiscovery:** Når du bruger et eDiscovery-værktøj, f.eks. indholdssøgning eller In-Place eDiscovery, søges der også i de ekstra lagerområder i et automatisk udvidet arkiv.

- **Fastholdelse:** Når du sætter en postkasse i venteposition ved hjælp af værktøjer som f.eks. Litigation Hold i Exchange Online eller eDiscovery-sagsbevaring og opbevaringspolitikker på Microsoft Purview-overholdelsesportalen, sættes indhold, der er placeret i et automatisk udvidet arkiv, også i venteposition.

- **Administration af meddelelsesposter (MRM):** Hvis du bruger POLITIKKER for MRM-sletning i Exchange Online til permanent at slette udløbne postkasseelementer, slettes udløbne elementer, der er placeret i det automatisk udvidede arkiv, også.

- **Importér tjeneste:** Du kan bruge office 365-importtjenesten til at importere PST-filer til en brugers automatisk udvidede arkiv. Du kan importere op til 100 GB data fra PST-filer til brugerens arkivpostkasse.

## <a name="next-steps"></a>Næste trin

Du kan finde flere tekniske oplysninger om automatisk udvidelse af arkivering i [Microsoft 365: Ofte stillede spørgsmål om automatisk udvidelse af arkiver](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).

Hvis du er klar til at aktivere automatisk udvidelse af arkivering, skal du se [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).
