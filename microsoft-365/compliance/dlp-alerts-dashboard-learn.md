---
title: Få mere at vide om dashboardet til forebyggelse af datatab
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
description: Få mere at vide om beskeder om forebyggelse af datatab og dashboardet for påmindelser.
ms.openlocfilehash: 375b16a3072f40ef8f366f7c1c4e8f714f195d63
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63592379"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Få mere at vide om dashboardet til forebyggelse af datatab

Når kriterierne i en politik til forebyggelse af datatab (DLP) matches af de handlinger, en bruger tager på et følsomt element, kan politikken generere en besked. Denne situation kan resultere i en stor mængde beskeder. DLP-beskeder indsamles i dashboardet for vigtige beskeder. Dashboardet til vigtige beskeder giver dig et enkelt sted at gå i gang med en grundig undersøgelse af alle detaljer om match af politik.  

<!-- [Microsoft 365 compliance center](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Arbejdsbelastninger

[Dashboardet til administration af DLP-beskeder](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">i Microsoft 365 Overholdelsescenter</a> viser beskeder for DLP-politikker for disse arbejdsbelastninger:

- Exchange
- SharePoint
- OneDrive
- Teams
- Windows 10 enheder 

> [!TIP]
> Kunder, der bruger [Slutpunkt DLP](endpoint-dlp-learn-about.md), der er berettiget til [Teams DLP](dlp-microsoft-teams.md), vil få vist deres slutpunktsbeskeder om DLP-politik og Teams DLP-politikbeskeder i dashboardet til administration af DLP-beskeder.

## <a name="single-alert-and-aggregate-alert"></a>Enkelt besked og samlet besked

Der findes to typer af beskeder, der kan konfigureres i DLP-politikker.

**Beskeder** om enkeltstående begivenheder bruges typisk i politikker, der overvåger meget følsomme begivenheder, der forekommer i en lav mængde, f.eks. en enkelt mail, hvor der sendes 10 eller flere kundekreditkortnumre uden for organisationen.

**Beskeder om sammenlægninger** bruges typisk i politikker, der overvåger for hændelser, der forekommer i en højere mængde over en tidsperiode. Der kan f.eks. blive udløst en samlet besked, når der sendes 10 individuelle mails hver med ét kundekreditkortnummer uden for din organisation over 48 timer.

## <a name="types-of-events"></a>Typer af hændelser

Her er nogle af de hændelser, der er knyttet til en besked. I brugergrænsefladen kan du vælge en bestemt hændelse for at få vist dens detaljer. 

### <a name="event-details"></a>Oplysninger om begivenhed

|Egenskabsnavn  |Beskrivelse  |Hændelsestyper  |
|---------|---------|---------|
|Id |entydigt id, der er knyttet til begivenheden |alle begivenheder |
|Placering |arbejdsbelastning, hvor hændelsen blev registreret|alle begivenheder |
|aktivitetstid     |tid for den brugeraktivitet, der opfylder kriterierne i DLP-politikken |

### <a name="affected-entities"></a>Påvirkede enheder

|Egenskabsnavn |Beskrivelse| Hændelsestyper|
|---------|---------|---------|
|bruger | bruger, der har taget den handling, der forårsagede politikmatchet | alle begivenheder|
|værtsnavn | værtsnavn på den computer, hvor DLP-politikoverensstemmelsen opstod | enhedshændelser|
|IP-adresse | IP-adressen på den computer, hvor DLP-politikoverensstemmelsen opstod | enhedshændelser|
|sha1 |SHA-1-hash på filen | enhedshændelser|
|sha256 | SHA-256-hash på filen | enhedshændelser|
|MDATP-enheds-id | MDATP-id for slutpunktsenhed|
|filstørrelse | størrelse på filen| SharePoint, OneDrive og enhedshændelser|
|filsti | den absolutte sti for det element, der er involveret i DLP-politik match | SharePoint, OneDrive og enheder|
|mailmodtagere |hvis en mail var det følsomme element, der matchede DLP-politikken, omfatter dette felt modtagerne af den pågældende mail| Exchange begivenheder|
|mail-emne |emne for den mail, der matchede DLP-politikken |Exchange begivenheder|
|vedhæftede filer i mails | navnene på de vedhæftede filer i den mail, der matchede DLP-politikken| Exchange begivenheder|
|webstedsejer |navnet på ejeren af webstedet| SharePoint og OneDrive begivenheder|
|URL-adresse til websted |fuld af URL-adressen på det SharePoint eller OneDrive websted, hvor DLP-politikoverensstemmelsen forekom |SharePoint og OneDrive begivenheder|
|fil oprettet |tidspunktet for oprettelse af den fil, der matchede DLP-politikken |SharePoint og OneDrive begivenheder|
|filen senest ændret | sidste gang, den fil, der matchede DLP-politikken, blev ændret | SharePoint og OneDrive begivenheder|
|filstørrelse | størrelsen på den fil, der matchede DLP-politikken |SharePoint og OneDrive begivenheder|
|filejer |ejeren af den fil, der matchede DLP-politikken |SharePoint og OneDrive begivenheder|  

### <a name="policy-details"></a>Politikdetaljer

|Egenskabsnavn |Beskrivelse |Hændelsestyper |
|---------|---------|---------|
|DLP-politik matchet |navnet på den matchede DLP-politik |alle begivenheder|
|regel matchet |navnet på den matchede DLP-politikregel |alle begivenheder|
|registrerede følsomme oplysningstyper (SIT)|SIT'er, der blev registreret som en del af DLP-politik match |alle begivenheder|
|handlinger, der er foretaget |handlinger, der blev foretaget, der forårsagede DLP-politikmatch| alle begivenheder|
|overtrædelse af handling | handling på slutpunktsenheden, der hævede DLP-beskeden| enhedshændelser | 
|politik for brugeroverrode |tilsidesættede brugeren politikken via et politiktip | alle begivenheder|
|brug tilsidesættelsesberettigelse |teksten til årsagen, der er angivet af brugeren til tilsidesættelsen | alle begivenheder|   

## <a name="see-also"></a>Se også

- [Introduktion til dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-get-started.md)
- [Hvor starter jeg med forebyggelse af datatab?](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
