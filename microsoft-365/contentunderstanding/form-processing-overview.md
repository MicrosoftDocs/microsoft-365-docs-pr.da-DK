---
title: Oversigt over formularbehandling i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du bruger AI Build til at oprette modeller til formularbehandling i Microsoft SharePoint Syntex.
ms.openlocfilehash: 7b9ff8b8a1014dfb47aa7061caf31599e497c18a
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463181"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over formularbehandling i Microsoft SharePoint Syntex

 ![AI Builder.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex bruger Microsoft Power Apps [AI Builder-formularbehandling](/ai-builder/overview) til at oprette modeller i SharePoint dokumentbiblioteker.

Du kan bruge AI Builder-formularbehandling til at oprette AI-modeller, der bruger teknologi til maskinel indlæring til at identificere og udtrække nøgleværdipar og tabeldata fra strukturerede eller semi-strukturerede dokumenter, f.eks. formularer og fakturaer.

Organisationer modtager ofte fakturaer i store mængder fra forskellige kilder, f.eks. mail, fax og mail. Det kan tage lang tid at behandle disse dokumenter og manuelt indtaste dem i en database. Ved at bruge KUNSTIG intelligens til at udtrække tekst, nøgle-/værdipar og tabeller fra dine dokumenter automatiserer formularbehandling denne proces. 

> [!NOTE]
> Se [SharePoint Syntex: Introduktionsvejledning](./adoption-getstarted.md) for at få flere oplysninger om eksempler på formularbehandlingsscenarier.

Du kan f.eks. oprette en model til formularbehandling, der identificerer alle indkøbsordredokumenter, der uploades til dokumentbiblioteket. Fra hver indkøbsordre kan du derefter udtrække og få vist bestemte data, der er vigtige for dig, f.eks *. ordrenummer*, *dato* eller *samlede omkostninger*.

![Dokumentbiblioteksvisning.](../media/content-understanding/doc-lib-done.png)</br>  

Du kan bruge eksempelfiler til at oplære din model og definere de oplysninger, der skal udtrækkes fra formularen. Layoutet af dit dokument lærer du ved at oplære din model. Du skal kun bruge fem formulardokumenter for at komme i gang. AI Builder analyserer dine eksempelfiler for nøgleværdipar, og du kan også manuelt identificere dem, der muligvis ikke er registreret.  Med AI Builder kan du teste nøjagtigheden af din model på dine eksempelfiler.

Når du har oplært og publiceret din model, opretter din model et [Power Automate flow](/power-automate/getting-started). Flowet kører, når en fil uploades til SharePoint dokumentbibliotek, og udtrækker data, der er identificeret i modellen. De udtrukne data vises i kolonner i visningen af din models dokumentbibliotek.

En Office 365 administrator skal [aktivere formularbehandling](./set-up-content-understanding.md) for SharePoint dokumentbibliotek, for at brugerne kan [oprette en formularbehandlingsmodel](create-a-form-processing-model.md) i den. Du kan vælge webstederne under konfigurationen eller efter konfigurationen i dine administrationsindstillinger.

## <a name="file-limitations"></a>Filbegrænsninger

Når du bruger modeller til formularbehandling, skal du notere [dig kravene og begrænsningerne for filbrug](/ai-builder/form-processing-model-requirements).

## <a name="supported-languages"></a>Understøttede sprog

Formularbehandling understøtter dokumenter på mere end 73 sprog. Du kan se en liste over sprog under [Understøttelse af formularbehandlingssprog](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

## <a name="multi-geo-environments"></a>Multi-Geo-miljøer

Når du konfigurerer SharePoint Syntex i et [Multi-Geo-miljø Microsoft 365](../enterprise/microsoft-365-multi-geo.md), kan du kun konfigurere det til at bruge formularbehandling på den centrale placering. Hvis du vil bruge formularbehandling på en satellitplacering, skal du kontakte Microsoft Support.

## <a name="custom-environments"></a>Brugerdefinerede miljøer

Hvis du bruger et brugerdefineret miljø (i stedet for standardmiljøet) til behandling af Power Platform, er der yderligere konfigurationskrav. Du kan få flere oplysninger under [Brugerdefinerede Power Platform-miljøer](set-up-content-understanding.md#requirements).


## <a name="see-also"></a>Se også
  
[dokumentation til Power Automate](/power-automate/)

[Opret en model for formularbehandling](create-a-form-processing-model.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Oplæring: Øg virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)