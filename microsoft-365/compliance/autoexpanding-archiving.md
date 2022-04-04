---
title: Få mere at vide om automatisk udvidende arkivering
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
description: Få mere at vide om automatisk udvidende arkivering, som indeholder ekstra arkivlager til Exchange Online postkasser.
ms.openlocfilehash: b55c0504f04f896377c1e1b0a4dccdacdb8bbc37
ms.sourcegitcommit: f941967b8bc2c24401795e41fd155365a0dbc645
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63761538"
---
# <a name="learn-about-auto-expanding-archiving"></a>Få mere at vide om automatisk udvidende arkivering

Arkivpostkasser Office 365 i Outlook brugere med yderligere lagerplads til postkasser. Når en brugers arkivpostkasse er aktiveret, får du adgang til op til 100 GB ekstra lagerplads. Tidligere, da lagerkvoten på 100 GB blev nået, skulle organisationer kontakte Microsoft for at anmode om yderligere lagerplads til en arkivpostkasse. Det er ikke længere tilfældet.

Arkiveringsfunktionen i Microsoft 365 (kaldet automatisk *arkivering*) indeholder op til 1,5 TB ekstra lagerplads i arkivpostkasser. Når lagerkvoten i arkivpostkassen er nået, Microsoft 365 (og trinvist) arkivets størrelse, indtil arkivpostkassen når 1,5 TB.

Du kan finde en trinvis vejledning til aktivering af automatisk udvidende arkivering i [Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md).

> [!NOTE]
> Automatisk udvidende arkivering understøtter også delte postkasser. For at aktivere arkivet for en delt postkasse skal du have en Exchange Online Plan 2-licens eller Exchange Online Plan 1-licens Exchange Online-arkivering licens.

## <a name="how-auto-expanding-archiving-works"></a>Sådan fungerer automatisk udvidende arkivering

Som beskrevet tidligere oprettes yderligere lagerplads til postkassen, når en brugers arkivpostkasse aktiveres. Når automatisk udvidende arkivering er aktiveret, kontrollerer Microsoft 365 med jævne mellemrum størrelsen på arkivpostkassen. Når en arkivpostkasse kommer tæt på dens lagergrænse, Microsoft 365 automatisk ekstra lagerplads til arkivet. Hvis brugeren løber tør for denne ekstra lagerplads, Microsoft 365 mere lagerplads til brugerens arkiv. Denne proces fortsætter, indtil brugerens arkiv når en størrelse på 1,5 TB. Denne proces sker automatisk, hvilket betyder, at administratorer ikke behøver at anmode om ekstra arkivlager eller administrere automatisk udvidende arkivering.

Her er en hurtig oversigt over processen.

![Oversigt over den automatisk udvidende arkiveringsproces.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. Arkivering er aktiveret for en brugerpostkasse eller en delt postkasse. En arkivpostkasse med 100 GB lagerplads oprettes, og advarselskvoten for arkivpostkassen er indstillet til 90 GB.

2. En administrator aktiverer automatisk udvidende arkivering for postkassen. Når arkivpostkassen (herunder mappen Genoprettelige elementer) når 90 GB, konverteres den til et automatisk udvidende arkiv, og Microsoft 365 tilføjer lagerplads til arkivet, indtil den når den maksimale størrelse på 1,5 TB. Det kan tage op til 30 dage, før den ekstra lagerplads er klargjort.

   > [!NOTE]
   > Hvis en postkasse er sat i venteposition eller er tildelt en opbevaringspolitik, øges lagerkvoten for arkivpostkassen til 110 GB, når automatisk udvidende arkivering er aktiveret. På samme måde øges arkivadvarselskvoten til 100 GB.

3. Microsoft 365 automatisk mere lagerplads, når det er nødvendigt.

> [!IMPORTANT]
> Automatisk udvidende arkivering understøttes kun for postkasser, der bruges til individuelle brugere (eller delte postkasser) med en væksthastighed, der ikke overstiger 1 GB pr. dag. En brugers arkivpostkasse er kun beregnet til den pågældende bruger. Det er ikke tilladt at bruge journalisering, transportregler eller regler for automatisk videresendelse til at kopiere meddelelser til en arkivpostkasse. Microsoft forbeholder sig ret til at afvise yderligere arkivering i tilfælde, hvor en brugers arkivpostkasse bruges til at lagre arkivdata for andre brugere eller i andre tilfælde af upassende brug.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Hvad flyttes til den ekstra arkivlagerplads?

Mapper kan flyttes, så de kan bruges effektivt til automatisk udvidende arkivlager. Microsoft 365 afgør, hvilke mapper der flyttes, når der føjes ekstra lagerplads til arkivet. Nogle gange, når en mappe flyttes, oprettes der automatisk en eller flere undermapper, og elementer fra den oprindelige mappe distribueres til disse mapper for at gøre det nemmere at flytte. Når du får vist arkivdelen af mappelisten i Outlook, vises disse undermapper under den oprindelige mappe. Den navngivningskonvention, Microsoft 365 bruger til at navngive disse **undermapper, er _yyyy (oprettet på dd mmm, yyyy h_mm), hvor:\<folder name\>**

- **yyyy** er det år, meddelelserne i mappen blev modtaget.

- **mmm dd, yyyy h_m** er den dato og det klokkeslæt, hvor undermappen blev oprettet i Office 365-format i UTC-format baseret på brugerens tidszone og internationale indstillinger i Outlook.

Følgende skærmbilleder viser en mappeliste før og efter meddelelser flyttes til et automatisk udvidet arkiv.

 **Før der tilføjes yderligere lagerplads**

![Mappeliste over arkivpostkasse, før automatisk udvidende arkiv klargøres.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Når ekstra lagerplads er tilføjet**

![Mappeliste over arkivpostkasse, når automatisk udvidende arkiv er klargjort.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Som beskrevet tidligere flytter Microsoft 365 elementer til undermapper (og navngive dem med den navngivningskonvention, der er beskrevet ovenfor) for at distribuere indhold til et hjælpearkiv. Men det er ikke altid muligt at flytte elementer til undermapper. Nogle gange kan en hel mappe flyttes til et hjælpearkiv. I dette tilfælde bevarer mappen det oprindelige navn.  Det fremgår ikke tydeligt på mappelisten i Outlook at mappen er blevet flyttet til et hjælpearkiv.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Outlook krav til adgang til elementer i et automatisk udvidet arkiv

For at få adgang til meddelelser, der er gemt i et automatisk udvidet arkiv, skal brugerne bruge en af følgende Outlook-klienter:

- Outlook som en del af en Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus)

- Outlook som en del af Microsoft 365 Apps for business (tidligere kaldet Office 365 Business)

- Outlook 2016 eller Outlook 2019 til Windows

- Outlook på internettet

- Outlook 2016 eller Outlook 2019 til Mac

Her er nogle ting, du skal overveje, når du bruger Outlook eller Outlook på internettet til at få adgang til meddelelser, der er gemt i et automatisk udvidet arkiv.

- Du kan få adgang til enhver mappe i arkivpostkassen, herunder dem, der er blevet flyttet til det automatisk udvidede lagringsområde.

- Hvis en arkivpostkasse har mindst ét automatisk udvidet lagringsområde, kan du ikke slette en mappe fra arkivpostkassen eller fra hjælpearkivet. Med andre ord kan du ikke slette nogen mapper i arkivet, når et automatisk udvidet lagringsområde er blevet klargjort.

- Du kan slette elementer i et automatisk udvidet lagringsområde. Du kan dog ikke bruge funktionen Gendan slettede elementer til at gendanne et element, når automatisk udvidende arkivering er aktiveret for en postkasse.

- Du kan søge efter automatisk udvidet arkivering i Outlook til internettet (OWA). Ligesom i onlinearkivet kan du søge efter elementer, der er blevet flyttet til et ekstra lagringsområde. Når arkiv er valgt som søgeområdet i OWA, søges der i alle arkiver (herunder automatisk udvidede arkiver) og deres tilsvarende undermapper. Bemærk, at søgning ikke understøttes af den automatiske udvidede arkiveringsfunktion i en arkivsituation, der kun findes i skyen (primær postkasse, der stadig er lokal).

- Automatisk udvidet arkivsøgning er tilgængelig i Outlook efter Windows i Månedlig virksomhedskanal. Med denne opdatering er området Aktuel postkasse tilgængelig, hvilket giver dig mulighed for at søge i det automatisk udvidede arkiv. Bemærk, at søgning ikke understøttes af den automatiske udvidede arkiveringsfunktion i en arkivsituation, der kun findes i skyen (primær postkasse, der stadig er lokal). Du kan finde flere oplysninger om denne og Microsoft Søg supportfunktioner i [Sådan Outlook du Windows, der har forbindelse Exchange Online til Microsoft Søg](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045). 

- Antallet af elementer i Outlook antallet af læste/ulæste (i Outlook og Outlook på internettet) i et automatisk udvidet arkiv er muligvis ikke nøjagtig.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Automatisk udvidende arkivering og andre funktioner til overholdelse af regler og standarder

I dette afsnit beskrives funktionerne mellem automatisk udvidende arkivering og andre funktioner til overholdelse af regler og standarder og datastyring.

- **eDiscovery:** Når du bruger et eDiscovery-værktøj, f.eks. indholdssøgning eller In-Place eDiscovery, søges der også i de ekstra lagringsområder i et automatisk udvidet arkiv.

- **Opbevaring:** Når du sætter en postkasse i venteposition ved hjælp af værktøjer som f.eks Retslig tilbageholdelse i Exchange Online eller eDiscovery-sagsarkiv og opbevaringspolitikker i Security and Compliance Center, placeres indhold, der findes i et automatisk udvidet arkiv, også i venteposition.

- **MESSAGING records management (MRM):** Hvis du bruger MRM-sletningspolitikker i Exchange Online til permanent at slette udløbne postkasseelementer, slettes udløbne elementer, der er placeret i det automatisk udvidede arkiv også.

- **Importtjeneste:** Du kan bruge tjenesten Office 365 til at importere PST-filer til en brugers automatisk udvidede arkiv. Du kan importere op til 100 GB data fra PST-filer til brugerens arkivpostkasse.

## <a name="next-steps"></a>Næste trin

Du kan finde flere tekniske oplysninger om automatisk udvidende arkivering [i Microsoft 365: Ofte stillede spørgsmål om automatisk udvidende arkiver](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).

Hvis du er klar til at aktivere automatisk udvidende arkivering, skal du [se Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md).
