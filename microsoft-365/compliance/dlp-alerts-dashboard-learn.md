---
title: Få mere at vide om dashboardet med DLP-beskeder
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Få mere at vide om beskeder til forebyggelse af datatab og dashboardet for beskeder.
ms.openlocfilehash: 1551b247e3302af6dc8ed9af62a88f2c24415122
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636155"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Få mere at vide om dashboardet til forebyggelse af datatab

Når kriterierne i en DLP-politik (Microsoft Purview Forebyggelse af datatab) matches af de handlinger, en bruger foretager på et følsomt element, kan politikken generere en besked. Denne situation kan resultere i en stor mængde beskeder. DLP-beskeder indsamles i beskeddashboardet. Dashboardet med beskeder giver dig et enkelt sted, hvor du kan foretage en grundig undersøgelse af alle detaljer om politikmatch.  

<!-- [Microsoft Purview compliance portal](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Arbejdsbyrde

Dashboardet [DLP til administration af beskeder](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> viser beskeder om DLP-politikker for disse arbejdsbelastninger:

- Exchange
- SharePoint
- OneDrive
- Teams
- Windows 10 enheder 

> [!TIP]
> Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md) , som er berettiget til [Teams DLP](dlp-microsoft-teams.md) , får vist deres DLP-politikbeskeder for slutpunkter og Teams DLP-politikbeskeder på dashboardet til administration af DLP-beskeder.

## <a name="single-alert-and-aggregate-alert"></a>Enkelt besked og samlet besked

Der er to typer beskeder, der kan konfigureres i DLP-politikker.

**Enkelthændelsesbeskeder** bruges typisk i politikker, der overvåger meget følsomme hændelser, der forekommer i en lav mængde, f.eks. en enkelt mail med 10 eller flere kundekreditkortnumre, der sendes uden for din organisation.

**Aggregerede hændelsesbeskeder** bruges typisk i politikker, der overvåger hændelser, der forekommer i en højere mængde over en tidsperiode. En samlet besked kan f.eks. udløses, når der sendes 10 individuelle mails hver med ét kundekreditkortnummer uden for din organisation over 48 timer.

## <a name="types-of-events"></a>Typer af hændelser

Her er nogle af de hændelser, der er knyttet til en besked. I brugergrænsefladen kan du vælge en bestemt hændelse for at få vist dens detaljer. 

### <a name="event-details"></a>Oplysninger om begivenhed

|Egenskabsnavn  |Beskrivelse  |Hændelsestyper  |
|---------|---------|---------|
|ID |entydigt id, der er knyttet til hændelsen |alle hændelser |
|Placering |arbejdsbelastning, hvor hændelsen blev registreret|alle hændelser |
|tidspunkt for aktivitet     |tidspunktet for den brugeraktivitet, der opfylder kriterierne i DLP-politikken |

### <a name="affected-entities"></a>Berørte enheder

|Egenskabsnavn |Beskrivelse| Hændelsestyper|
|---------|---------|---------|
|Bruger | bruger, der har foretaget den handling, der forårsagede, at politikken blev matchet | alle hændelser|
|Værtsnavn | værtsnavn på den computer, hvor DLP-politikken blev matchet | enhedshændelser|
|IP-adresse | IP-adressen på den computer, hvor DLP-politikken blev matchet | enhedshændelser|
|sha1 |SHA-1-hash for filen | enhedshændelser|
|sha256 | SHA-256-hash for filen | enhedshændelser|
|MDATP-enheds-id | MDATP-id for slutpunktsenhed|
|filstørrelse | filens størrelse| SharePoint-, OneDrive- og enhedshændelser|
|filsti | den absolutte sti til det element, der er involveret i DLP-politikmatch | Hændelser for SharePoint, OneDrive og enheder|
|mailmodtagere |Hvis en mail var det følsomme element, der svarede til DLP-politikken, indeholder dette felt modtagerne af den pågældende mail| Exchange-hændelser|
|mailemne |emne i den mail, der svarede til DLP-politikken |Exchange-hændelser|
|vedhæftede filer i mails | navnene på de vedhæftede filer i den mail, der matcher DLP-politikken| Exchange-hændelser|
|webstedsejer |navnet på webstedets ejer| SharePoint- og OneDrive-hændelser|
|URL-adresse til websted |fuld af URL-adressen til det SharePoint- eller OneDrive-websted, hvor DLP-politikken fandt sted |SharePoint- og OneDrive-hændelser|
|filen er oprettet |tidspunktet for oprettelsen af den fil, der svarede til DLP-politikken |SharePoint- og OneDrive-hændelser|
|senest ændret i filen | sidste gang, den fil, der svarede til DLP-politikken, blev ændret | SharePoint- og OneDrive-hændelser|
|filstørrelse | størrelsen på den fil, der svarede til DLP-politikken |SharePoint- og OneDrive-hændelser|
|filejer |ejer af den fil, der svarede til DLP-politikken |SharePoint- og OneDrive-hændelser|  

### <a name="policy-details"></a>Oplysninger om politik

|Egenskabsnavn |Beskrivelse |Hændelsestyper |
|---------|---------|---------|
|DLP-politik matcher |navnet på den tilsvarende DLP-politik |alle hændelser|
|regel, der stemmer overens |navnet på den tilsvarende DLP-politikregel |alle hændelser|
|registrerede følsomme informationstyper (SIT)|SIT'er, der blev registreret som en del af DLP-politikmatch |alle hændelser|
|handlinger, der er foretaget |handlinger, der blev udført, som forårsagede, at DLP-politikken blev matchet| alle hændelser|
|overtræder handling | handling på slutpunktsenheden, der har hævet DLP-beskeden| enhedshændelser | 
|politik for brugeroverrode |tilsidesættede brugeren politikken via et politiktip | alle hændelser|
|brug justering af tilsidesættelse |teksten til den årsag, som brugeren har angivet for tilsidesættelsen | alle hændelser|   

## <a name="see-also"></a>Se også

- [Kom i gang med dashboardet til advarsel om forebyggelse af datatab](dlp-alerts-dashboard-get-started.md)
- [Her skal du starte med forebyggelse af datatab](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
