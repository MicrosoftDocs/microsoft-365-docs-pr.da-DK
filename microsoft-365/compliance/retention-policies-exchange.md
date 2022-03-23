---
title: Få mere at vide om opbevaring af Exchange
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
description: Få mere at vide om, hvordan opbevaring fungerer Exchange.
ms.openlocfilehash: f92df4bd25ddeff44472865c9ae221014050afaa
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63590069"
---
# <a name="learn-about-retention-for-exchange"></a>Få mere at vide om opbevaring af Exchange

Oplysningerne i denne artikel tillæg Få [mere at vide om opbevaring](retention.md), fordi de indeholder oplysninger, der er specifikke for Exchange.  For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring af Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring af Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i opbevaring og sletning

Følgende Exchange elementer fra brugerpostkasser og delte postkasser kan bevares og slettes ved hjælp af opbevaringspolitikker og opbevaringsmærkater: Mails (omfatter modtagne meddelelser, kladder, sendte meddelelser) med eventuelle vedhæftede filer, opgaver, når de har en slutdato, og noter. 

Kalenderelementer, der har en slutdato, understøttes i opbevaringspolitikker, men understøttes ikke til opbevaringsetiketter.

Kontakter og eventuelle opgaver og kalenderelementer, der ikke har en slutdato, understøttes ikke.

Andre elementer, der er gemt i en postkasse, f.eks. Skype mails Teams, medtages ikke i opbevaringspolitikker eller navne for Exchange. Disse elementer har deres egne opbevaringspolitikker.

## <a name="how-retention-works-for-exchange"></a>Sådan fungerer opbevaring for Exchange

Både en postkasse og en offentlig mappe bruger mappen [Genoprettelige elementer til](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) at bevare elementer. Kun personer, der har fået tildelt eDiscovery-tilladelser, kan få vist elementer i en anden brugers mappe Genoprettelige elementer.
  
Når en bruger sletter en meddelelse i en anden mappe end mappen Slettet post, flyttes meddelelsen som standard til mappen Slettet post. En bruger kan dog blød slette et element (Skift+Delete) i en hvilken som helst mappe, hvilket tilsidesætter mappen Slettet post og flytter elementet direkte til mappen Genoprettelige elementer.
  
Når du anvender opbevaringsindstillinger Exchange data, evaluerer et timerjob med jævne mellemrum elementer i mappen Genoprettelige elementer. Hvis et element ikke stemmer overens med reglerne i mindst én opbevaringspolitik eller opbevaringsmærkat for at bevare elementet, slettes det permanent (også kaldet permanent slettet) fra mappen Genoprettelige elementer.

> [!NOTE]
> På grund af det første princip for opbevaring er permanent sletning altid suspenderet [, hvis](retention.md#the-principles-of-retention-or-what-takes-precedence) det samme element skal bevares på grund af en anden opbevaringspolitik eller opbevaringsmærkat, eller det er under eDiscovery-fasthold af juridiske eller lovmæssige årsager.

Det kan tage op til syv dage at køre timerjobbet, Exchange timerjobplaceringen skal indeholde mindst 10 MB.
  
Når en bruger forsøger at ændre egenskaberne for et postkasseelement – f.eks. emne, brødtekst, vedhæftede filer, afsendere og modtagere eller dato, der sendes eller modtages for en meddelelse – gemmes en kopi af det oprindelige element i mappen Genoprettelige elementer, før ændringen bekræftes. Denne handling sker for hver efterfølgende ændring. Når opbevaringsperioden er slut, slettes kopier i mappen Genoprettelige elementer permanent.

Når opbevaringsindstillingerne er anvendt på Exchange indhold, afhænger de stier, som indholdet tager, af, om opbevaringsindstillingerne skal bevares og slettes, kun bevares eller slettes.

Når opbevaringsindstillingerne skal bevares og slettes:

![Diagram over opbevaringsflow i mail og offentlige mapper.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. Hvis elementet ændres eller **slettes permanent** af brugeren (skift+Delete eller slettet fra Slettet post) i løbet af opbevaringsperioden: Elementet flyttes (eller kopieres, ved redigering) til mappen Genoprettelige elementer. Her kører et timerjob med jævne mellemrum og identificerer elementer, hvis opbevaringsperiode er udløbet, og disse elementer slettes permanent inden for 14 dage efter opbevaringsperiodens afslutning. Bemærk, at 14 dage er standardindstillingen, men de kan konfigureres op til 30 dage.

2.  Hvis elementet ikke ændres eller slettes under opbevaringsperioden: Den samme proces kører med jævne mellemrum på alle mapper i postkassen og identificerer elementer, hvis opbevaringsperiode er udløbet, og disse elementer slettes permanent inden for 14 dage efter opbevaringsperiodens afslutning. Bemærk, at 14 dage er standardindstillingen, men de kan konfigureres op til 30 dage. 

Når opbevaringsindstillingerne kun bevares eller slettes, er der variationer af bevarings- og sletningsstier for indholdsstier:

### <a name="content-paths-for-retain-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger, der kun kan bevares

1.  Hvis elementet ændres eller slettes i opbevaringsperioden: En kopi af det oprindelige element oprettes i mappen Genoprettelige elementer og bevares indtil slutningen af opbevaringsperioden, når kopien i mappen Genoprettelige elementer slettes permanent inden for 14 dage efter, at elementet udløber. 

2. **Hvis elementet ikke ændres eller slettes i løbet** af en opbevaringsperiode: Der sker intet før og efter opbevaringsperioden; elementet forbliver på dets oprindelige placering.

### <a name="content-paths-for-delete-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger kun for slette

1. **Hvis elementet** ikke slettes i løbet af den konfigurerede periode: Ved slutningen af den konfigurerede periode i opbevaringspolitikken flyttes elementet til mappen Genoprettelige elementer. 

2. **Hvis elementet slettes i løbet** af den konfigurerede periode: Elementet flyttes straks til mappen Genoprettelige elementer. Hvis en bruger sletter elementet derfra eller tømmer mappen Genoprettelige elementer, slettes elementet permanent. Ellers slettes elementet permanent, efter at det har været i mappen Genoprettelige elementer i 14 dage. 

## <a name="user-notification-of-expiry-date"></a>Brugermeddelelse om udløbsdato

Opbevaringspolitikker for Exchange har, i modsætning til opbevaringspolitikker for den anden Microsoft 365-arbejdsbelastning, en brugertilstedeværelse ved øverst i hver mail at vise navnet på den opbevaringspolitik, der har den korteste udløbsdato for elementet, og den beregnede udløbsdato for det pågældende element. Brugerne får ikke vist denne meddelelse, hvis opbevaringspolitikken ikke sletter elementer (bevar kun).

Hvis der anvendes en opbevaringsetiket på en mail, vises navnet på den pågældende etiket og den tilsvarende udløbsdato altid, og navnet og datoen erstattes fra enhver opbevaringspolitik, der anvendes på postkassen.

Husk i denne kontekst, at udløbsdatoen for, hvornår en mail slettes, er, når brugerne kan forvente, at mailen automatisk flyttes til mappen Genoprettelige elementer (hvis den ikke allerede er der). Mails i mappen Genoprettelige elementer slettes ikke permanent, men forbliver der med henblik på overholdelse, hvis de er underlagt opbevaringsindstillinger for at bevare dem, eller de er under et eDiscovery-hold af juridiske eller lovmæssige årsager.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger forlader organisationen, og brugerens postkasse er inkluderet i en opbevaringspolitik, bliver postkassen en inaktiv postkasse, når brugerens Microsoft 365-konto slettes. Indholdet af en inaktiv postkasse er stadig underlagt eventuelle opbevaringspolitik, der blev placeret i postkassen, før den blev gjort inaktiv, og indholdet er tilgængeligt for en eDiscovery-søgning. Du kan finde flere oplysninger [i Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md).

Når opbevaringsindstillingerne ikke længere er gældende, fordi dataene slettes permanent, eller opbevaringsperioden er udløbet, kan den Exchange-administratoren nu slette den [inaktive postkasse](delete-an-inactive-mailbox.md). I dette scenarie slettes den inaktive postkasse ikke automatisk.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du er ny bruger af konfiguration af opbevaring i Microsoft 365, skal du se [Introduktion til informationsstyring](get-started-with-information-governance.md).

Hvis du er klar til at konfigurere en opbevaringspolitik eller en opbevaringsmærkat til Exchange, skal du se følgende instruktioner:
- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)
- [Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)