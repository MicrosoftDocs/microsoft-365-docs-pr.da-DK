---
title: Bevar Bcc og udvidede distributionsgruppemodtagere for eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: In-Place af venteposition, retslig tilbageholdelse og Microsoft 365 opbevaringspolitikker giver dig mulighed for at bevare postkasseindhold for at overholde lovmæssige krav til overholdelse af regler og standarder og eDiscovery-krav.
ms.openlocfilehash: c157f2fb0b74e679bf1252b6f24208b77a657d8c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589165"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Bevar Bcc og udvidede distributionsgruppemodtagere for eDiscovery
  
Retslig tilbageholdelser, eDiscovery-ventende tilbageholdelser og [Microsoft 365](./retention.md) opbevaringspolitikker (oprettet i Microsoft 365 Overholdelsescenter) giver dig mulighed for at bevare postkasseindhold, så det opfylder lovmæssige krav til overholdelse af regler og standarder og eDiscovery-krav. Oplysninger om modtagere, der er adresseret direkte i felterne Til og Cc i en meddelelse, medtages som standard i alle meddelelser. Men din organisation kræver muligvis muligheden for at søge efter og gengive oplysninger om alle modtagerne af en meddelelse. Dette omfatter:
  
- **Modtagere, der er adresseret ved hjælp af feltet Bcc i en meddelelse:** Bcc-modtagere gemmes i meddelelsen i afsenderens postkasse, men medtages ikke i brevhoveder i meddelelsen, der er leveret til modtagerne. 
    
- **Udvidede distributionsgruppemodtagere:** Modtagere, der modtager meddelelsen, fordi de er medlemmer af en distributionsgruppe, som meddelelsen blev adresseret til, enten i felterne Til, Cc eller Bcc. 
    
Exchange Online og Exchange Server 2013 (kumulativ opdatering 7 og nyere versioner) bevarer oplysninger om Bcc og udvidede distributionsgruppemodtagere. Du kan søge efter disse oplysninger ved hjælp af et eDiscovery-værktøj i Microsoft 365 Overholdelsescenter. 
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Sådan bevares Bcc-modtagere og udvidede distributionsgruppemodtagere

Som nævnt tidligere gemmes oplysninger om Bcc-modtagere sammen med meddelelsen i afsenderens postkasse. Disse oplysninger er indekseret og tilgængelige for eDiscovery-søgninger og -indhold. 
  
Oplysninger om udvidede distributionsgruppemodtagere gemmes sammen med meddelelsen, når du placerer en postkasse på In-Place i Venteposition eller Retslig venteposition. I Office 365 gemmes disse oplysninger også, når der Microsoft 365 en opbevaringspolitik for en postkasse. Medlemskab af distributionsgruppen bestemmes på det tidspunkt, hvor meddelelsen sendes. Den udvidede liste over modtagere, der er gemt sammen med meddelelsen, påvirkes ikke af ændringer i medlemskabet af gruppen, når meddelelsen er sendt. 
  
| Oplysninger om... | Er gemt i... | Er gemt som standard? | Er tilgængelig for... |
|:-----|:-----|:-----|:-----|
|Til- og Cc-modtagere  <br/> |Meddelelsesegenskaber i afsenderens og modtagernes postkasser.  <br/> |Ja  <br/> |Afsender, modtagere og compliance officers  <br/> |
|Bcc-modtagere  <br/> |Meddelelsesegenskab i afsenderens postkasse.  <br/> |Ja  <br/> |Afsender og overholdelsesmedarbejdere  <br/> |
|Udvidede distributionsgruppemodtagere  <br/> |Meddelelsesegenskaber i afsenderens postkasse.  <br/> |Nej. Udvidede modtageroplysninger for distributionsgruppen gemmes, når en postkasse er placeret i venteposition In-Place retslig tilbageholdelse eller tildelt til en Microsoft 365 opbevaringspolitik.  <br/> |Overholdelsesmedarbejdere  <br/> |
   
## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Søge efter meddelelser, der er sendt til Bcc og udvidede distributionsgruppemodtagere

Når du søger efter meddelelser, der er sendt til en modtager, indeholder eDiscovery-søgeresultater nu meddelelser, der sendes til en distributionsgruppe, som modtageren er medlem af. Følgende tabel viser de scenarier, hvor meddelelser, der sendes til Bcc og udvidede distributionsgruppemodtagere returneres i eDiscovery-søgninger.
  
Scenarie 1: John er medlem af US-Sales distributionsgruppen. Denne tabel viser eDiscovery-søgeresultater, når Bob sender en meddelelse til John direkte eller indirekte via en distributionsgruppe.
  
| Når du søger efter meddelelser, der er sendt... | Og meddelelsen sendes med ... | Resultaterne medtager meddelelsen? |
|:-----|:-----|:-----|
|Til:John  <br/> |John på TO  <br/> |Ja  <br/> |
|Til:John  <br/> |US-Sales på TIL  <br/> |Ja  <br/> |
|Til:US-Salg  <br/> |US-Sales på TIL  <br/> |Ja  <br/> |
|Cc:John  <br/> |John på CC  <br/> |Ja  <br/> |
|Cc:John  <br/> |US-Sales på CC  <br/> |Ja  <br/> |
|Cc:US-Sales  <br/> |US-Sales på CC  <br/> |Ja  <br/> |
   
Scenarie 2: Bob sender en mail til John (Til/Cc) og Jack (Bcc direkte eller indirekte via en distributionsgruppe). Tabellen nedenfor viser eDiscovery-søgeresultater.
  
| Når du søger... | For sendte meddelelser... | Resultaterne medtager meddelelsen? | Bemærkninger |
|:-----|:-----|:-----|:-----|
|Bobs postkasse  <br/> |Til/Cc:John  <br/> |Ja  <br/> |Viser, at Jack var Bcc'er.  <br/> |
|Bobs postkasse  <br/> |Bcc:Jack  <br/> |Ja  <br/> |Viser, at Jack var Bcc'er.  <br/> |
|Bobs postkasse  <br/> |Bcc:Jack (via distributionsgruppe)  <br/> |Ja  <br/> |Liste over medlemmer af Bcc'ed-distributionsgruppen, som blev udvidet, da meddelelsen blev sendt, er synlig i eksempelvisning af eDiscovery-søgning, eksport og logfiler.  <br/> |
|Johns postkasse  <br/> |Til/Cc:John  <br/> |Ja  <br/> |Ingen angivelse af Bcc-modtagere.  <br/> |
|Johns postkasse  <br/> |Bcc:Jack (direkte eller via distributionsgruppe)  <br/> |Nej  <br/> |Bcc-oplysninger gemmes ikke i den meddelelse, der leveres til modtagerne. Du skal søge i afsenderens postkasse.  <br/> |
|Jacks postkasse  <br/> |Til/Cc:John (direkte eller via distributionsgruppe)  <br/> |Ja  <br/> |Til/Cc-oplysninger medtages i meddelelser, der leveres til alle modtagere.  <br/> |
|Jacks postkasse  <br/> |Bcc:Jack (direkte eller via distributionsgruppe)  <br/> |Nej  <br/> |Bcc-oplysninger gemmes ikke i den meddelelse, der leveres til modtagerne. Du skal søge i afsenderens postkasse.  <br/> |
   
## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

 **Q. Hvornår og hvor gemmes Bcc-modtageroplysninger?**
  
A. Bcc-modtageroplysninger bevares som standard i den oprindelige meddelelse i afsenderens postkasse. Hvis Bcc-modtageren er en distributionsgruppe, udvides medlemskab af distributionsgruppen kun, hvis afsenderens postkasse er sat i venteposition eller er tildelt en Microsoft 365 opbevaringspolitik.
  
 **Q. Hvornår og hvor gemmes listen over udvidede distributionsgruppemodtagere?**
  
A. Gruppemedlemskab udvides på det tidspunkt, hvor meddelelsen sendes. Listen over udvidede distributionsgruppemedlemmer gemmes i den oprindelige meddelelse i afsenderens postkasse. Afsenderens postkasse skal være i venteposition In-Place Hold, Retslig tilbageholdelse eller tildelt til en Microsoft 365 opbevaringspolitik.
  
 **Q. Kan til/Cc-modtagerne se, hvilke modtagere der blev Bcc'er?**
  
A. Nej. Disse oplysninger er ikke inkluderet i brevhoveder og er ikke synlige for Til/Cc-modtagere. Afsenderen kan se feltet Bcc gemt i den oprindelige meddelelse, der er gemt i vedkommendes postkasse. Compliance Officers kan se disse oplysninger, når de søger i afsenderens postkasse.
  
 **Q. Hvordan kan jeg sikre, at udvidede distributionsgruppemodtagere altid bevares?**
  
A. For at sikre at udvidede distributionsgruppemedlemmer altid [bevares](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) med en meddelelse, skal du placere alle postkasser i venteposition eller oprette en Microsoft 365 opbevaringspolitik for hele organisationen. 
  
 **Q. Hvilke typer grupper understøttes?**
  
A. Distributionsgrupper, mailaktiverede sikkerhedsgrupper og dynamiske distributionsgrupper understøttes. 
  
 **Q. Er der en grænse for antallet af distributionsgruppemodtagere, der udvides og gemmes i meddelelsen?**
  
A. Op til 10.000 medlemmer i en distributionsgruppe bevares.
  
 **Q. Understøttes indlejrede distributionsgrupper?**
  
A. Ja, 25 niveauer af indlejrede distributionsgrupper udvides.
  
 **Q. Hvor er oplysninger om Bcc og udvidede distributionsgrupper synlige?**
  
A. Oplysninger om Bcc og udvidede distributionsgruppemodtagere er synlige for Compliance officers, når du udfører en eDiscovery-søgning. Bcc og udvidede distributionsgruppemodtagere er inkluderet i søgeresultater, der kopieres til en postkasse i Discovery eller eksporteres til en PST-fil og i eDiscovery-logfilen i søgeresultaterne. Oplysninger om Bcc-modtagere findes også i forhåndsvisning af søgning.
  
 **Q. Hvad sker der, hvis et medlem af en distributionsgruppe er skjult fra organisationens globale adresseliste (GAL)?**
  
A. Det har ingen virkning. Hvis modtagerne er skjult fra den globale adresseliste, er de stadig medtaget på listen over modtagere i den udvidede distributionsgruppe.