---
title: Deduplikering i eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 12/21/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5af334b6-a15d-4f73-97f8-1423457d9f6b
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du fjerner dublerede eDiscovery-søgeresultater, så der kun eksporteres én kopi af en mail.
ms.openlocfilehash: 4456ecfb4684562d8ddf7da21c463859f2d9bec2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090999"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>Deduplikering i eDiscovery-søgeresultater

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel beskrives det, hvordan deduplikering af eDiscovery-søgeresultater fungerer, og det forklares, hvilke begrænsninger der er i algoritmen for deduplikering.
  
Når du bruger eDiscovery-værktøjer til at eksportere resultaterne af en eDiscovery-søgning, har du mulighed for at fjerne duplikering af de resultater, der eksporteres. Hvad betyder det? Når du aktiverer deduplikering (som standard er deduplikering ikke aktiveret), eksporteres der kun én kopi af en mail, selvom der er fundet flere forekomster af den samme meddelelse i de postkasser, der blev søgt i. Deduplikering hjælper dig med at spare tid ved at reducere det antal elementer, du skal gennemse og analysere, når søgeresultaterne er eksporteret. Men det er vigtigt at forstå, hvordan deduplikering fungerer, og være opmærksom på, at der er begrænsninger for algoritmen, der kan medføre, at et entydigt element markeres som en dublet under eksporten.
  
## <a name="how-duplicate-messages-are-identified"></a>Sådan identificeres dublerede meddelelser

eDiscovery-værktøjer bruger en kombination af følgende mailegenskaber til at afgøre, om en meddelelse er dublet:
  
- **InternetMessageId** – Denne egenskab angiver internetmeddelelses-id'et for en mail, som er et globalt entydigt id, der refererer til en bestemt version af en bestemt meddelelse. Dette id genereres af afsenderens mailklientprogram eller værtsmailsystem, der sender meddelelsen. Hvis en person sender en meddelelse til mere end én modtager, er internetmeddelelses-id'et det samme for hver forekomst af meddelelsen. Efterfølgende ændringer af den oprindelige meddelelse modtager et andet meddelelses-id. 

- **ConversationTopic** – Denne egenskab angiver emnet i en meddelelses samtaletråd. Værdien af egenskaben **ConversationTopic** er den streng, der beskriver det overordnede emne i samtalen. En samtale består af en indledende meddelelse og alle meddelelser, der sendes som svar på den første meddelelse. Meddelelser i den samme samtale har samme værdi for egenskaben **ConversationTopic** . Værdien af denne egenskab er typisk emnelinjen fra den indledende meddelelse, der forgrenede samtalen. 

- **BodyTagInfo** – Dette er en intern Exchange store-egenskab. Værdien af denne egenskab beregnes ved at kontrollere forskellige attributter i meddelelsens brødtekst. Denne egenskab bruges til at identificere forskelle i meddelelsesteksten. 

Under eDiscovery-eksportprocessen sammenlignes disse tre egenskaber for hver meddelelse, der opfylder søgekriterierne. Hvis disse egenskaber er identiske for to (eller flere) meddelelser, bestemmes det, at disse meddelelser er dubletter, og resultatet er, at kun én kopi af meddelelsen eksporteres, hvis deduplikering er aktiveret. Den eksporterede meddelelse kaldes "kildeelementet". Oplysninger om dublerede meddelelser er inkluderet i **deResults.csv** og **Manifest.xml** rapporter, der er inkluderet i de eksporterede søgeresultater. I den **Results.csv** fil identificeres en dubletmeddelelse ved at have en værdi i kolonnen **Dupliker til element** . Værdien i denne kolonne svarer til værdien i kolonnen **Elementidentitet** for den meddelelse, der blev eksporteret. 
  
Følgende grafik viser, hvordan duplikerede meddelelser vises i **Results.csv** og **Manifest.xml** rapporter, der eksporteres med søgeresultaterne. Disse rapporter indeholder ikke de mailegenskaber, der tidligere er beskrevet, som bruges i algoritmen til deduplikering. Rapporterne indeholder i stedet egenskaben **Elementidentitet**, der er tildelt elementer af Exchange butik. 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv rapport (vist i Excel)
  
![Visning af oplysninger om dubletelementer i rapporten Results.csv.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml rapport (vist i Excel)
  
![Visning af oplysninger om dubletelementer i rapporten Manifest.xml.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
Derudover medtages andre egenskaber fra duplikerede meddelelser i eksportrapporterne. Dette omfatter den postkasse, hvor dubletten findes, om meddelelsen blev sendt til en distributionsgruppe, og om meddelelsen var Cc'd eller Bcc'd til en anden bruger.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Begrænsninger for algoritmen til deduplikering

Der er nogle kendte begrænsninger for algoritmen til deduplikering, der kan medføre, at entydige elementer markeres som dubletter. Det er vigtigt at forstå disse begrænsninger, så du kan beslutte, om du vil bruge den valgfri deduplikeringsfunktion.
  
Der er én situation, hvor funktionen til deduplikering ved en fejl kan identificere en meddelelse som en dublet og ikke eksportere den (men stadig nævne den som en dublet i eksportrapporterne). Det er meddelelser, som en bruger redigerer, men som ikke sender. Lad os f.eks. sige, at en bruger vælger en meddelelse i Outlook, kopierer indholdet af meddelelsen og derefter indsætter den i en ny meddelelse. Derefter ændrer brugeren en af kopierne ved at fjerne eller tilføje en vedhæftet fil eller ændre emnelinjen eller selve brødteksten. Hvis disse to meddelelser stemmer overens med forespørgslen i en eDiscovery-søgning, eksporteres kun én af meddelelserne, hvis deduplikering er aktiveret, når søgeresultaterne eksporteres. Så selvom den oprindelige meddelelse eller den kopierede meddelelse blev ændret, blev ingen af de reviderede meddelelser sendt, og derfor blev værdierne for egenskaberne **InternetMessageId**, **ConversationTopic** og **BodyTagInfo** ikke opdateret. Men som tidligere forklaret, vises begge meddelelser i eksportrapporterne 
  
Entydige meddelelser kan også markeres som dubletter, når funktionen beskyttelse mod kopiering ved skrivning er aktiveret, f.eks. hvis en postkasse er sat i venteposition eller In-Place venteposition. Funktionen Kopiér ved skrivning kopierer den oprindelige meddelelse (og gemmer den i mappen Versioner i brugerens mappe Genoprettelige elementer), før revisionen af det oprindelige element gemmes. I dette tilfælde kan den reviderede kopi og den oprindelige meddelelse (i mappen Gendanbare elementer) betragtes som dublerede meddelelser, og derfor eksporteres kun én af dem.
  
> [!IMPORTANT]
> Hvis begrænsningerne i algoritmen til deduplikering kan påvirke kvaliteten af dine søgeresultater, bør du ikke aktivere deduplikering, når du eksporterer elementer. Hvis det er usandsynligt, at de situationer, der er beskrevet i dette afsnit, er en faktor i dine søgeresultater, og du vil reducere det antal elementer, der med størst sandsynlighed vil være dubletter, bør du overveje at aktivere deduplikering. 
  
## <a name="more-information"></a>Flere oplysninger

- Oplysningerne i denne artikel gælder, når du eksporterer søgeresultater ved hjælp af et af følgende eDiscovery-værktøjer:

  - Indholdssøgning i overholdelsescenter i Office 365

  - In-Place eDiscovery i Exchange Online

  - eDiscovery Center i SharePoint Online

- Du kan finde flere oplysninger om eksport af søgeresultater under:

  - [Eksportér indholdssøgning](export-search-results.md)

  - [Eksportér en indholdssøgningsrapport](export-a-content-search-report.md)

  - [Eksportér In-Place eDiscovery-søgeresultater til en PST-fil](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - [Eksportér indhold, og opret rapporter i eDiscovery Center](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
