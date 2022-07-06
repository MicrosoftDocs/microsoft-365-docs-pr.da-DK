---
title: Bevar Bcc- og udvidede distributionsgruppemodtagere for eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: In-Place venteposition, procesretsholdning og Microsoft 365-opbevaringspolitikker giver dig mulighed for at bevare postkasseindhold, så det opfylder de lovmæssige krav til overholdelse af angivne standarder og eDiscovery-krav.
ms.openlocfilehash: de1a04c223856e1257e03e5dd47ae6d5e88033eb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637081"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Bevar Bcc- og udvidede distributionsgruppemodtagere for eDiscovery
  
Med procesførelser, eDiscovery-ventepositioner og [Microsoft 365-opbevaringspolitikker](./retention.md) (oprettet i Microsoft Purview-compliance-portal) kan du bevare postkasseindhold, så det opfylder de lovmæssige krav til overholdelse af angivne standarder og krav til eDiscovery. Oplysninger om modtagere, der er direkte adresseret i felterne Til og Cc i en meddelelse, medtages som standard i alle meddelelser. Men din organisation kan kræve muligheden for at søge efter og gengive oplysninger om alle modtagere af en meddelelse. Dette omfatter:
  
- **Modtagere, der er adresseret ved hjælp af Bcc-feltet i en meddelelse:** Bcc-modtagere gemmes i meddelelsen i afsenderens postkasse, men medtages ikke i brevhoveder i meddelelsen, der leveres til modtagere. 
    
- **Udvidede distributionsgruppemodtagere:** Modtagere, der modtager meddelelsen, fordi de er medlemmer af en distributionsgruppe, som meddelelsen er adresseret til, enten i felterne Til, Cc eller Bcc. 
    
Exchange Online og Exchange Server 2013 (kumulativ opdatering 7 og nyere versioner) bevarer oplysninger om Bcc og udvidede modtagere af distributionsgrupper. Du kan søge efter disse oplysninger ved hjælp af et eDiscovery-værktøj på overholdelsesportalen.
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Sådan bevares Bcc-modtagere og udvidede modtagere af distributionsgrupper

Som tidligere nævnt gemmes oplysninger om Bcc-modtagere sammen med meddelelsen i afsenderens postkasse. Disse oplysninger er indekseret og tilgængelige for eDiscovery-søgninger og ventepositioner.

Oplysninger om udvidede modtagere af distributionsgrupper gemmes sammen med meddelelsen, når du har placeret en postkasse i In-Place venteposition eller procesførelsesventeposition. I Office 365 gemmes disse oplysninger også, når der anvendes en Microsoft 365-opbevaringspolitik på en postkasse. Medlemskab af distributionsgruppe bestemmes på det tidspunkt, hvor meddelelsen sendes. Den udvidede modtagerliste, der er gemt sammen med meddelelsen, påvirkes ikke af ændringer af medlemskabet af gruppen, når meddelelsen er sendt.

|Oplysninger om...|Er gemt i...|Er gemt som standard?|Er tilgængelig for...|
|---|---|---|---|
|Modtagere af til og Cc|Meddelelsesegenskaber i afsenderens og modtagernes postkasser.|Ja|Afsender, modtagere og overholdelsesofficerer|
|Bcc-modtagere|Egenskaben Message i afsenderens postkasse.|Ja|Afsendere og overholdelsesofficerer|
|Udvidede distributionsgruppemodtagere|Meddelelsesegenskaber i afsenderens postkasse.|Nej. Udvidede modtageroplysninger for distributionsgruppen gemmes, når en postkasse er placeret i venteposition In-Place eller procesførelse eller tildelt en Microsoft 365-opbevaringspolitik.|Overholdelsesofficerer|

## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Søger efter meddelelser, der er sendt til Bcc, og udvidede modtagere af distributionsgrupper

Når du søger efter meddelelser, der er sendt til en modtager, indeholder eDiscovery-søgeresultaterne nu meddelelser, der er sendt til en distributionsgruppe, som modtageren er medlem af. I følgende tabel vises de scenarier, hvor meddelelser, der sendes til Bcc og udvidede modtagere af distributionsgrupper, returneres i eDiscovery-søgninger.

Scenarie 1: John er medlem af distributionsgruppen US-Sales. I denne tabel vises eDiscovery-søgeresultater, når Bob sender en meddelelse til John direkte eller indirekte via en distributionsgruppe.

|Når du søger i Bobs postkasse efter meddelelser, der er sendt...|Og beskeden sendes med...|Skal resultaterne indeholde meddelelse?|
|---|---|---|
|Til:John|John på TIL|Ja|
|Til:John|US-Sales til|Ja|
|Til:SALG I USA|US-Sales til|Ja|
|Cc:John|John på CC|Ja|
|Cc:John|US-Sales på CC|Ja|
|Cc:US-Sales|US-Sales på CC|Ja|

Scenarie 2: Bob sender en mail til John (Til/Cc) og Jack (Bcc direkte eller indirekte via en distributionsgruppe). I nedenstående tabel vises eDiscovery-søgeresultater.

|Når du søger...|For meddelelser, der er sendt...|Skal resultaterne indeholde meddelelse?|Bemærkninger|
|---|---|---|---|
|Bobs postkasse|Til/Cc:John|Ja|Viser, at Jack var Bcc'ed.|
|Bobs postkasse|Bcc:Jack|Ja|Viser, at Jack var Bcc'ed.|
|Bobs postkasse|Bcc:Jack (via distributionsgruppe)|Ja|Listen over medlemmer af Bcc'ed-distributionsgruppen, der blev udvidet, da meddelelsen blev sendt, er synlig i eDiscovery-søgeeksemplet, eksporten og loggene.|
|Johns postkasse|Til/Cc:John|Ja|Ingen angivelse af Bcc-modtagere.|
|Johns postkasse|Bcc:Jack (direkte eller via distributionsgruppe)|Nej|Bcc-oplysninger gemmes ikke i den meddelelse, der leveres til modtagere. Du skal søge i afsenderens postkasse.|
|Jacks postkasse|Til/Cc:John (direkte eller via distributionsgruppe)|Ja|Til/Cc-oplysninger er inkluderet i meddelelsen, der leveres til alle modtagere.|
|Jacks postkasse|Bcc:Jack (direkte eller via distributionsgruppe)|Nej|Bcc-oplysninger gemmes ikke i den meddelelse, der leveres til modtagere. Du skal søge i afsenderens postkasse.|

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

 **Q. Hvornår og hvor gemmes Bcc-modtageroplysningerne?**

A. Bcc-modtageroplysningerne bevares som standard i den oprindelige meddelelse i afsenderens postkasse. Hvis Bcc-modtageren er en distributionsgruppe, udvides medlemskabet af distributionsgruppen kun, hvis afsenderens postkasse er i venteposition eller er tildelt til en Microsoft 365-opbevaringspolitik.

 **Q. Hvornår og hvor gemmes listen over udvidede modtagere af distributionsgrupper?**

A. Gruppemedlemskab udvides, når meddelelsen sendes. Listen over medlemmer af den udvidede distributionsgruppe gemmes i den oprindelige meddelelse i afsenderens postkasse. Afsenderens postkasse skal være på In-Place venteposition, procesførelsesholdning eller tildelt en Microsoft 365-opbevaringspolitik.

 **Q. Kan modtagerne af To/Cc se, hvilke modtagere der blev Bcc'ed?**

A. Nej. Disse oplysninger er ikke inkluderet i brevhoveder og er ikke synlige for To/Cc-modtagere. Afsenderen kan se feltet Bcc, der er gemt i den oprindelige meddelelse, som er gemt i postkassen. Overholdelsesansvarlige kan se disse oplysninger, når de søger i afsenderens postkasse.

 **Q. Hvordan kan jeg sikre, at udvidede modtagere af distributionsgrupper altid bevares?**

A. Hvis du vil sikre, at udvidede medlemmer af distributionsgruppen altid bevares med en meddelelse, skal [du placere alle postkasser i venteposition](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) eller oprette en Microsoft 365-opbevaringspolitik for hele organisationen.

 **Q. Hvilke typer grupper understøttes?**

A. Distributionsgrupper, mailaktiverede sikkerhedsgrupper og dynamiske distributionsgrupper understøttes.

 **Q. Er der en grænse for antallet af distributionsgruppemodtagere, der udvides og gemmes i meddelelsen?**

A. Op til 10.000 medlemmer af en distributionsgruppe bevares.

 **Q. Understøttes indlejrede distributionsgrupper?**

A. Ja, 25 niveauer af indlejrede distributionsgrupper udvides.

 **Q. Hvor er modtageroplysningerne for Bcc og den udvidede distributionsgruppe synlige?**

A. Bcc-oplysninger og udvidede modtagere af distributionsgrupper er synlige for overholdelsesofficerer, når der udføres en eDiscovery-søgning. Bcc- og udvidede modtagere af distributionsgrupper inkluderes i søgeresultater, der kopieres til en registreringspostkasse eller eksporteres til en PST-fil og i eDiscovery-logfilen, der er inkluderet i søgeresultaterne. Bcc-modtageroplysninger er også tilgængelige i søgeeksemplet.

 **Q. Hvad sker der, hvis et medlem af en distributionsgruppe er skjult fra organisationens globale adresseliste??**

A. Der er ingen indvirkning. Hvis modtagerne er skjult fra den globale adresseliste, er de stadig inkluderet på listen over modtagere for den udvidede distributionsgruppe.
