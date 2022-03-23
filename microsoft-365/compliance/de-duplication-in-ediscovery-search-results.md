---
title: Afplikning i eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om, hvordan du fjerner duplikerede eDiscovery-søgeresultater, så kun én kopi af en mail eksporteres.
ms.openlocfilehash: d09a0e09166928627be01d623963146cfd416bd2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587688"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>Afplikning i eDiscovery-søgeresultater

I denne artikel beskrives det, hvordan duplikering af eDiscovery-søgeresultater fungerer, og begrænsningerne ved duplikeringsalgoritmen fjernes.
  
Når du bruger eDiscovery-værktøjer til at eksportere resultaterne af en eDiscovery-søgning, har du mulighed for at duplikere de resultater, der eksporteres. Hvad betyder det? Når du aktiverer duplikering (duplikering er som standard ikke aktiveret), eksporteres der kun én kopi af en mail, selvom der kan være fundet flere forekomster af den samme meddelelse i de postkasser, der blev søgt i. Du kan bruge duplikering til at spare tid ved at reducere antallet af elementer, du skal gennemse og analysere, når søgeresultaterne er eksporteret. Men det er vigtigt at forstå, hvordan duplikering fungerer, og at du er opmærksom på, at der er begrænsninger for algoritmen, der kan medføre, at et entydigt element markeres som en dublet under eksporten.
  
## <a name="how-duplicate-messages-are-identified"></a>Sådan identificeres dublerede meddelelser

eDiscovery-værktøjer bruger en kombination af følgende mailegenskaber til at afgøre, om en meddelelse er en dublet:
  
- **InternetMessageId** – Denne egenskab angiver Internetmeddelelses-id'et for en mail, som er en GUID (Globally Unique Identifier), der refererer til en bestemt version af en bestemt meddelelse. Dette id genereres af afsenderens mailklientprogram eller værtsmailsystem, der sender meddelelsen. Hvis en person sender en meddelelse til mere end én modtager, er internetmeddelelses-id'et det samme for hver forekomst af meddelelsen. Efterfølgende revisioner af den oprindelige meddelelse modtager en anden meddelelses-id. 

- **Samtaletop –** Denne egenskab angiver emnet for samtaletråden i en meddelelse. Værdien af egenskaben **ConversationTopic** er den streng, der beskriver det overordnede emne i samtalen. En samtale består af en indledende meddelelse og alle meddelelser, der sendes som svar på den oprindelige meddelelse. Meddelelser i den samme samtale har samme værdi for **egenskaben ConversationTopic** . Værdien af denne egenskab er typisk linjen Emne fra den oprindelige meddelelse, der afsvarede samtalen. 

- **BodyTagInfo** – Dette er en intern Exchange butiksegenskab. Værdien af denne egenskab beregnes ved at kontrollere forskellige attributter i meddelelsens brødtekst. Denne egenskab bruges til at identificere forskelle i brødteksten i meddelelser. 

Under eDiscovery-eksportprocessen sammenlignes disse tre egenskaber for hver meddelelse, der opfylder søgekriterierne. Hvis disse egenskaber er identiske for to (eller flere) meddelelser, bestemmes disse meddelelser som dubletter, og det betyder, at der kun eksporteres én kopi af meddelelsen, hvis duplikering er aktiveret. Den meddelelse, der eksporteres, kaldes "kildeelementet". Oplysninger om dublerede meddelelser er inkluderet **iResults.csv** **ogManifest.xml** , der er inkluderet i de eksporterede søgeresultater. I filen **Results.csv** identificeres en dubletmeddelelse ved at have en værdi i kolonnen **Dupliker til** element. Værdien i denne kolonne svarer til værdien i kolonnen **Elementidentitet** for den meddelelse, der blev eksporteret. 
  
Følgende grafik viser, hvordan duplikerede meddelelser vises i **Results.csvog** **Manifest.xml** , der eksporteres med søgeresultaterne. Disse rapporter omfatter ikke de mailegenskaber, der er beskrevet tidligere, og som bruges i algoritmen til afplikering. I stedet indeholder rapporterne egenskaben **Elementidentitet**, der tildeles elementer af Exchange lager. 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv rapport (vist i Excel)
  
![Få vist oplysninger om dublerede elementer Results.csv rapporten.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml rapport (vist i Excel)
  
![Få vist oplysninger om dublerede elementer Manifest.xml rapporten.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
Desuden medtages andre egenskaber fra dublerede meddelelser i eksportrapporterne. Dette omfatter den postkasse, den duplikerede meddelelse findes i, om meddelelsen blev sendt til en distributionsgruppe, og om meddelelsen var Cc'd eller Bcc til en anden bruger.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Begrænsninger for algoritmen til afplikering

Der er nogle kendte begrænsninger for algoritmen til duplikering, der kan medføre, at entydige elementer markeres som dubletter. Det er vigtigt at forstå disse begrænsninger, så du kan beslutte, om du vil bruge den valgfri funktion til afplikering.
  
Der er én situation, hvor funktionen til afplikering kan identificere en meddelelse som en dublet og ikke eksportere den (men stadig citere den som en dublet i eksportrapporterne). Dette er meddelelser, som en bruger redigerer, men ikke sender. Lad os f.eks. sige, at en bruger markerer en meddelelse i Outlook, kopierer indholdet af meddelelsen og derefter indsætter den i en ny meddelelse. Derefter ændrer brugeren en af kopierne ved at fjerne eller tilføje en vedhæftet fil eller ændre emnelinjen eller selve brødteksten. Hvis disse to meddelelser svarer til forespørgslen fra en eDiscovery-søgning, eksporteres kun én af meddelelserne, hvis duplikering er aktiveret, når søgeresultaterne eksporteres. Så selvom den oprindelige meddelelse eller den kopierede meddelelse blev ændret, blev ingen af de reviderede meddelelser sendt, og derfor blev værdierne for **egenskaberne InternetMessageId**, **ConversationTopic** og **BodyTagInfo** ikke opdateret. Men som beskrevet tidligere vises begge meddelelser i eksportrapporterne 
  
Unikke meddelelser kan også markeres som dubletter, når funktionen til beskyttelse af kopiér på skrive-siden er aktiveret, som i tilfælde af at en postkasse er i retslig venteposition eller In-Place venteposition. Funktionen Kopiér ved skrivning kopierer den oprindelige meddelelse (og gemmer den i mappen Versioner i brugerens mappe med genoprettelige elementer), før ændringen af det oprindelige element gemmes. I dette tilfælde kan den reviderede kopi og den oprindelige meddelelse (i mappen Genoprettelige elementer) betragtes som dublerede meddelelser, og derfor eksporteres kun én af dem.
  
> [!IMPORTANT]
> Hvis begrænsningerne af duplikeringsalgoritmen kan påvirke kvaliteten af dine søgeresultater, skal du ikke aktivere duplikering, når du eksporterer elementer. Hvis de situationer, der er beskrevet i dette afsnit, sandsynligvis ikke er en faktor i søgeresultaterne, og du vil reducere det antal elementer, der mest sandsynligt er dubletter, bør du overveje at aktivere duplikering. 
  
## <a name="more-information"></a>Flere oplysninger

- Oplysningerne i denne artikel er relevante, når du eksporterer søgeresultater ved hjælp af et af følgende eDiscovery-værktøjer:

  - Indholdssøgning i overholdelsescenter i Office 365

  - In-Place eDiscovery i Exchange Online

  - eDiscovery-center i SharePoint Online

- Du kan finde flere oplysninger om eksport af søgeresultater i:

  - [Eksportér indholdssøgning](export-search-results.md)

  - [Eksportere en rapport for indholdssøgning](export-a-content-search-report.md)

  - [Eksportér In-Place eDiscovery-søgeresultater til en PST-fil](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - [Eksportér indhold, og opret rapporter i eDiscovery-centeret](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
