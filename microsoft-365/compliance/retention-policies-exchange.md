---
title: Få mere at vide om opbevaring for Exchange
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
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan opbevaring fungerer for Exchange.
ms.openlocfilehash: b49a21f5358bb8d4b25c1b164d30180f1fa265d9
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285940"
---
# <a name="learn-about-retention-for-exchange"></a>Få mere at vide om opbevaring for Exchange

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Oplysningerne i denne artikel supplerer [Få mere at vide om opbevaring](retention.md), fordi den indeholder oplysninger, der er specifikke for Exchange.  For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring for Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring for Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i forbindelse med opbevaring og sletning

Følgende Exchange elementer fra brugerpostkasser og delte postkasser kan bevares og slettes ved hjælp af opbevaringspolitikker og opbevaringsbeskrivelser: Mails (indeholder modtagne meddelelser, kladder, sendte meddelelser) med vedhæftede filer, opgaver, når de har en slutdato og noter. 

Kalenderelementer, der har en slutdato, understøttes for opbevaringspolitikker, men understøttes ikke for opbevaringsmærkater.

Kontakter og alle opgaver og kalenderelementer, der ikke har en slutdato, understøttes ikke.

Andre elementer, der er gemt i en postkasse, f.eks. Skype og Teams meddelelser, er ikke inkluderet i opbevaringspolitikker eller mærkater for Exchange. Disse elementer har deres egne opbevaringspolitikker.

Postkasser skal have mindst 10 MB data, før opbevaringsindstillinger gælder for dem, og opbevaringsmærkater kan publiceres til dem.

## <a name="how-retention-works-for-exchange"></a>Sådan fungerer opbevaring for Exchange

Både en postkasse og en offentlig mappe bruger [mappen Gendanbare elementer](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) til at bevare elementer. Det er kun personer, der har fået tildelt eDiscovery-tilladelser, der kan få vist elementer i en anden brugers mappe med elementer, der kan gendannes.
  
Når en bruger sletter en meddelelse i en anden mappe end mappen Slettet post, flyttes meddelelsen som standard til mappen Slettet post. En bruger kan dog slette et element (Skift+Slet) i en hvilken som helst mappe, som tilsidesætter mappen Slettet post og flytter elementet direkte til mappen Gendan elementer.
  
Når du anvender opbevaringsindstillinger på Exchange data, evaluerer et timerjob jævnligt elementer i mappen Gendanbare elementer. Hvis et element ikke stemmer overens med reglerne for mindst én opbevaringspolitik eller opbevaringsmærkat for at bevare elementet, slettes det permanent (også kaldet hårdt slettet) fra mappen Genoprettelige elementer.

> [!NOTE]
> På grund af det [første opbevaringsprincip](retention.md#the-principles-of-retention-or-what-takes-precedence) suspenderes permanent sletning altid, hvis det samme element skal bevares på grund af en anden opbevaringspolitik eller opbevaringsmærkat, eller den er omfattet af eDiscovery-ventepositioner af juridiske eller undersøgelsesmæssige årsager.

Det kan tage op til syv dage at køre timerjobbet, og den Exchange placering skal indeholde mindst 10 MB.
  
Når en bruger forsøger at ændre egenskaberne for et postkasseelement – f.eks. emne, brødtekst, vedhæftede filer, afsendere og modtagere eller dato for afsendelse eller modtagelse af en meddelelse – gemmes der en kopi af det oprindelige element i mappen Gendanbare elementer, før ændringen bekræftes. Denne handling sker for hver efterfølgende ændring. Ved slutningen af opbevaringsperioden slettes kopier i mappen Elementer, der kan gendannes, permanent.

Når opbevaringsindstillinger er anvendt på Exchange indhold, afhænger de stier, som indholdet følger, af, om opbevaringsindstillingerne skal bevares og slettes, kun bevares eller slettes.

Når opbevaringsindstillingerne skal bevares og slettes:

![Diagram over opbevaringsflow i mail og offentlige mapper.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Hvis elementet ændres eller slettes permanent** af brugeren (enten SKIFT+SLET eller slettet fra Slettet post) i opbevaringsperioden: Elementet flyttes (eller kopieres i tilfælde af redigering) til mappen Gendan elementer. Der kører et timerjob med jævne mellemrum og identificerer elementer, hvis opbevaringsperiode er udløbet, og disse elementer slettes permanent inden for 14 dage efter afslutningen af opbevaringsperioden. Bemærk, at 14 dage er standardindstillingen, men den kan konfigureres op til 30 dage.

2. **Hvis elementet ikke ændres eller slettes** i løbet af opbevaringsperioden: Den samme proces kører jævnligt på alle mapper i postkassen og identificerer elementer, hvis opbevaringsperiode er udløbet, og disse elementer slettes permanent inden for 14 dage efter afslutningen af opbevaringsperioden. Bemærk, at 14 dage er standardindstillingen, men den kan konfigureres op til 30 dage. 

Når opbevaringsindstillingerne kun bevares eller slettes, er indholdsstierne variationer af bevar og slet:

### <a name="content-paths-for-retain-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger kun for bevarelse

1. **Hvis elementet ændres eller slettes** i løbet af opbevaringsperioden: Der oprettes en kopi af det oprindelige element i mappen Gendanbare elementer og bevares indtil slutningen af opbevaringsperioden, når kopien i mappen Gendanbare elementer slettes permanent inden for 14 dage efter, at elementet udløber. 

2. **Hvis elementet ikke ændres eller slettes** i løbet af opbevaringsperioden: Der sker intet før og efter opbevaringsperioden. elementet forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-settings"></a>Indholdsstier til indstillinger for opbevaring, der kun kan slettes

1. **Hvis elementet ikke slettes** i den konfigurerede periode: I slutningen af den konfigurerede periode i opbevaringspolitikken flyttes elementet til mappen Gendanbare elementer. 

2. **Hvis elementet slettes** i den konfigurerede periode: Elementet flyttes straks til mappen Elementer, der kan gendannes. Hvis en bruger sletter elementet derfra eller tømmer mappen Gendanbare elementer, slettes elementet permanent. Ellers slettes elementet permanent, når det er i mappen Elementer, der kan gendannes i 14 dage. 

## <a name="user-notification-of-expiry-date"></a>Brugermeddelelse om udløbsdato

Opbevaringspolitikker for Exchange, i modsætning til opbevaringspolitikker for de andre Microsoft 365 arbejdsbelastninger, har en bruger tilstedeværelse ved at vise navnet på opbevaringspolitikken øverst i hver mail, der har den korteste udløbsdato for elementet, og den beregnede udløbsdato for det pågældende element. Brugerne kan ikke se denne meddelelse, hvis opbevaringspolitikken ikke sletter elementer (bevar kun).

Hvis der anvendes en opbevaringsmærkat på en mail, vises navnet på den pågældende etiket og den tilsvarende udløbsdato altid, og det erstatter navnet og datoen fra enhver opbevaringspolitik, der er anvendt på postkassen.

Husk, at i denne kontekst er udløbsdatoen for, hvornår en mail slettes, hvornår brugerne kan forvente, at mailen automatisk flyttes til mappen Gendanbare elementer (hvis de ikke allerede er der). Mails i mappen Elementer, der kan gendannes, slettes ikke permanent, men forbliver der af hensyn til overholdelse af angivne standarder, hvis de er underlagt nogen opbevaringsindstillinger for at bevare dem, eller de er i eDiscovery-venteposition af juridiske eller undersøgelsesmæssige årsager.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger forlader organisationen, og brugerens postkasse er inkluderet i en politik til opbevaring, bliver postkassen en inaktiv postkasse, når brugerens Microsoft 365 konto slettes. Indholdet af en inaktiv postkasse er stadig underlagt en opbevaringspolitik, der blev placeret i postkassen, før den blev gjort inaktiv, og indholdet er tilgængeligt for en eDiscovery-søgning. Du kan få flere oplysninger under [Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md).

Når opbevaringsindstillingerne ikke længere gælder, fordi dataene slettes permanent, eller opbevaringsperioden er udløbet, kan den Exchange administrator nu [slette den inaktive postkasse](delete-an-inactive-mailbox.md). I dette scenarie slettes den inaktive postkasse ikke automatisk.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du ikke har arbejdet med at konfigurere opbevaring i Microsoft 365, skal du se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).

Hvis du er klar til at konfigurere en opbevaringspolitik eller en opbevaringsmærkat for Exchange, skal du se følgende instruktioner:
- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)
