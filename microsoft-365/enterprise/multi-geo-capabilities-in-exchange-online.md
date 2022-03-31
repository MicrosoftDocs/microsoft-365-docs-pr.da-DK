---
title: Exchange Multi-Geo
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Lær om multi-geo-funktioner i Exchange Online, f.eks funktionsbegrænsninger og postkasseplacering.
ms.openlocfilehash: c45c5c8e8856206fc2afc3e08005821f24dcd028
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63601596"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Multi-Geo Capabilities in Exchange Online

I et miljø med flere geografiske oplysninger kan du vælge placeringen Exchange Online postkasseindhold (in restdata) pr. bruger.

Du kan placere postkasser i satellit geografiske placeringer ved at:

- Oprettelse af en Exchange Online postkasse direkte i en satellits geoplacering.

- Flytte en eksisterende Exchange Online til en satellits geoplacering ved at ændre brugerens foretrukne dataplacering.

- Onboarding af en postkasse fra en lokal Exchange direkte til en satellit geoplacering.

## <a name="mailbox-placement-and-moves"></a>Placering og flytning af postkasse

Når Microsoft har fuldført de nødvendige multi-geo-konfigurationstrin, vil Exchange Online overholde **attributten PreferredDataLocation** for brugerobjekter i Azure AD.

Exchange Online synkroniserer **egenskaben PreferredDataLocation** fra Azure AD til **egenskaben MailboxRegion** i Exchange Online-katalogtjenesten. Værdien af **MailboxRegion bestemmer** den geoplacering, hvor brugerpostkasser og eventuelle tilknyttede arkivpostkasser placeres. Det er ikke muligt at konfigurere en brugers primære postkasse og arkivpostkasser til at ligge på forskellige geoplaceringer. Der kan kun konfigureres én geoplacering pr. bruger-objekt.

- Når **PreferredDataLocation** er konfigureret på en bruger med en eksisterende postkasse, sættes postkassen i en samlet kø og flyttes automatisk til den angivne geoplacering.

- Når **PreferredDataLocation** er konfigureret på en bruger uden en eksisterende postkasse, bliver den klargjort til den angivne geoplacering, når du klargør postkassen.

- Når **PreferredDataLocation** ikke er angivet for en bruger, bliver den klargjort på den centrale geoplacering, når du klargør postkassen.

- Hvis **PreferredDataLocation-koden** er forkert (f.eks. en slåfejl i NAN i stedet for NAM), klargøres postkassen på den centrale geoplacering.

**Bemærk**! Multi-geo-funktioner og Skype for Business Online-møder, der er hostet regionalt, bruger begge **egenskaben PreferredDataLocation** på brugerobjekter til at finde tjenester. Hvis du konfigurerer **PreferredDataLocation-værdier** for brugerobjekter til regionale møder, flyttes postkassen for disse brugere automatisk til den angivne geoplacering, når multi-geo er aktiveret på Microsoft 365-lejeren.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Funktionsbegrænsninger for multi-geo i Exchange Online

- Sikkerheds- og overholdelsesfunktioner (f.eks. overvågning og eDiscovery), der findes i Exchange Administration (EAC), er ikke tilgængelige i multi-geo organisationer. I stedet skal du bruge Microsoft 365 [Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) til at konfigurere funktioner til sikkerhed og overholdelse.

- Outlook til Mac brugere kan opleve et midlertidigt tab af adgang til deres onlinearkivmappe, mens du flytter deres postkasse til en ny geoplacering. Denne betingelse opstår, når brugerens primære postkasser og arkivpostkasser er på forskellige geoplaceringer, fordi flytninger af postkasser på tværs af geografiske placeringer kan være fuldført på forskellige tidspunkter.

- Brugere kan ikke dele *postkassemapper på* tværs af geografiske placeringer i Outlook på internettet (tidligere kaldet Outlook Web App eller OWA). En bruger i EU kan f.eks. ikke bruge Outlook på internettet til at åbne en delt mappe i en postkasse, der er placeret i USA. Brugere af Outlook på internettet kan dog åbne andre postkasser  på forskellige geografiske placeringer ved hjælp af et separat browservindue som beskrevet i Åbn en anden persons postkasse i et separat [browservindue i Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Bemærk**! Mappedeling på tværs af geografiske postkasser understøttes i Outlook på Windows.

- Offentlige mapper understøttes i organisationer med flere geografiske geografiske oplysninger. Offentlige mapper skal dog forblive på den centrale geoplacering. Du kan ikke flytte offentlige mapper til satellit geografiske placeringer.

- I et multi-geo-miljø understøttes overvågning af postkasser på tværs af geografiske miljøer ikke. Hvis en bruger f.eks. har fået tildelt adgangstilladelse til en delt postkasse på en anden geoplacering, logføres postkassehandlinger, der udføres af den pågældende bruger, ikke i postkassens overvågningslog for den delte postkasse. Exchange overvågningshændelser for administratorer er også kun tilgængelige for standardplaceringen. Du kan få mere at vide [under Administrere postkasserevision](../compliance/enable-mailbox-auditing.md).
