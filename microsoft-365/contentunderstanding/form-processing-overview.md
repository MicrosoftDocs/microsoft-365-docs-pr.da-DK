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
ms.openlocfilehash: a3a3d1fa0e160b96d487a5eeb03c69f9e4fe7fb3
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507383"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over formularbehandling i Microsoft SharePoint Syntex

 ![AI Builder.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex bruger microsoft Power Apps [AI Builder-formularbehandling](/ai-builder/overview) til at oprette modeller SharePoint dokumentbiblioteker.

Du kan bruge AI Builder-formularbehandling til at oprette AI-modeller, der bruger maskinlæringsteknologi til at identificere og udtrække nøgleværdipar og tabeldata fra strukturerede eller semistrukturerede dokumenter, f.eks. formularer og fakturaer.

Organisationer modtager ofte fakturaer med store mængder fra forskellige kilder, f.eks. mail, fax, mail osv. Det kan tage lang tid at behandle disse dokumenter og indtaste dem manuelt i en database. Når du bruger AI til at udtrække tekst, nøgle-/værdipar og tabeller fra dine dokumenter, automatiserer formularbehandling denne proces. 

> [!NOTE]
> Se SharePoint Syntex[: Introduktion for at få mere at](./adoption-getstarted.md) vide om eksempler på scenarie for formularbehandling.

Du kan f.eks. oprette en formularbehandlingsmodel, der identificerer alle indkøbsordredokumenter, der overføres til dokumentbiblioteket. Fra hver indkøbsordre kan du derefter udtrække og få vist specifikke data, der er vigtige for dig, f.eks. *Købsordrenummer**,* Dato eller *Samlede omkostninger*.

![Dokumentbiblioteksvisning.](../media/content-understanding/doc-lib-done.png)</br>  

Du kan bruge eksempelfiler til at oplære din model og definere de oplysninger, der skal udtrækkes fra din formular. Layoutet i dit dokument læres ved at uddanne din model. Du skal kun bruge fem formulardokumenter for at komme i gang. AI Builder analyserer eksempelfilerne for par med nøgleværdier, og du kan også manuelt identificere dem, der måske ikke er blevet fundet.  Med AI Builder kan du teste nøjagtigheden af din model på dine eksempelfiler.

Når du har trænet og publicere din model, skaber din model [Power Automate flow](/power-automate/getting-started). Flowet kører, når en fil uploades til SharePoint-dokumentbiblioteket og udtrækker data, der er blevet identificeret i modellen. De udtrukne data vises i kolonner i modellens dokumentbiblioteksvisning.

En Office 365 administrator skal aktivere behandling af [formular for SharePoint](./set-up-content-understanding.md) dokumentbibliotek, for at brugerne kan oprette en [formularbehandlingsmodel](create-a-form-processing-model.md) i den. Du kan vælge webstederne under installationen eller efter konfigurationen i administrationsindstillingerne.

### <a name="file-limitations"></a>Filbegrænsninger

Når du bruger modeller til formularbehandling, skal du huske [at notere krav og begrænsninger for filforbrug](/ai-builder/form-processing-model-requirements).

### <a name="supported-languages"></a>Understøttede sprog

Formularbehandling understøtter dokumenter på mere end 73 sprog. Du kan finde en liste over sprog i [Understøttelse af sprog til behandling af formular](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

### <a name="multi-geo-environments"></a>Multi-Geo-miljøer

Når du konfigurerer SharePoint Syntex et [Microsoft 365 Multi-Geo-miljø](../enterprise/microsoft-365-multi-geo.md), kan du kun konfigurere det til at bruge formularbehandling på den centrale placering. Hvis du vil bruge formularbehandling på en satellitplacering, skal du kontakte Microsoft Support.






## <a name="see-also"></a>Se også
  
[Power Automate dokumentation](/power-automate/)

[Oprette en formularbehandlingsmodel](create-a-form-processing-model.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Kursus: Forbedr virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)