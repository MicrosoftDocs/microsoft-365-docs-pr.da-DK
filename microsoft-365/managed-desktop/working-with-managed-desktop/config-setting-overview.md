---
title: Konfigurerbare indstillinger for Microsoft Managed Desktop
description: Oplysninger om konfigurerbare indstillinger med Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, indstillinger, konfigurerbare indstillinger
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 910bd8d37853ce70acb6379599b0259446b0752e
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/28/2022
ms.locfileid: "63589094"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Konfigurerbare indstillinger – Microsoft Managed Desktop

Microsoft Managed Desktop installerer indstillinger og politikker, der anvendes på alle enheder, der administreres af Microsoft Managed Desktop. Du kan finde flere oplysninger under [Enhedskonfiguration](../service-description/device-policies.md).

Konfigurerbare indstillinger i Microsoft Managed Desktop giver it-administratorer en metode til at tilpasse og installere indstillinger, der er unikke for deres organisation og forretningsmæssige behov. Disse indstillinger er ud over enhedskonfigurationsindstillinger og politikker, der administreres af Microsoft Managed Desktop.  

Konfigurerbare indstillingsændringer foretages i skyen. De anvendes på dine Microsoft Managed Desktop-enheder i definerede installationsgrupper. Denne proces svarer til, hvordan Microsoft Managed Desktop administrerer ændringer i enhedskonfigurationsindstillinger og politikker, der er defineret og administreret af tjenesten. Ved at bruge den samme proces, som Microsoft Managed Desktop bruger til implementering af ændringer, fortsætter du med at flytte organisationen fremad ved hjælp af moderne praksisser for it-administration.

## <a name="when-to-use-configurable-settings"></a>Hvornår skal du bruge konfigurerbare indstillinger?

Brug konfigurerbare indstillinger i følgende scenarier:

| Scenarie | Beskrivelse |
| ------ | ------ |
| Onboardingproces | Microsoft Managed Desktop anbefaler, at du tilpasser konfigurerbare indstillinger, når du onboarder til Microsoft Managed Desktop-tjenesten, eller når du onboarder et stort antal enheder (20 eller flere). <br><br>Konfigurationskategorier er konfigureret i administrationsportalen for Microsoft-administreret skrivebord. Når du er blevet onboardet og har adgang til administrationsportalen, kan du bestemme, hvilke indstillingskategorier du vil tilpasse for din organisation. Når du har foretaget ændringerne, skal du foretage en fase for en installation og derefter installere ændringerne. |
| Bevar indstillinger | Gennemgå dine indstillinger regelmæssigt, og foretag de nødvendige opdateringer. Du skal muligvis foretage ændringer for at understøtte en ændring i din virksomhed. |

## <a name="setting-categories"></a>Angive kategorier

Følgende er de konfigurerbare indstillingskategorier, som du kan tilpasse:

| Kategori | Beskrivelse |
| ------ | ------ |
| [Skrivebordsbaggrundsbillede](config-setting-ref.md#desktop-background-picture) | Tilpas skrivebordsbaggrundsbilledet til Microsoft-administrerede skrivebordsenheder. |
| [Startsider i browseren](config-setting-ref.md#browser-start-pages) | Tilføj startsider til brug med Microsoft Edge. |
| [Webstedsliste i virksomhedstilstand](config-setting-ref.md#enterprise-mode-site-list-location) | Tilføj websteder og deres kompatibilitetstilstand. Websteder på listen starter i Internet Explorer. |
| [Websteder, der er tillid til](config-setting-ref.md#trusted-sites) | Tilføj pålidelige websteder, og angiv sikkerhedszoner for hvert websted. |
| [Undtagelser for proxywebsted](config-setting-ref.md#proxy) | Konfigurer dit proxyserveradressenummer og portnummer, og tilføj proxywebstedsundtagelser. |

Hver indstillingskategori kan tilpasses og installeres på egen hånd. Du kan installere ændringer i flere indstillingskategorier på samme tid. Du kan dog kun installere én ændring ad gangen til en indstillingskategori.

Eksempel:

- Du kan installere ændringer i skrivebordsbaggrundsbilledet og pålidelige websteder, hver især som deres egen installation, på samme tid.
- Du kan ikke installere to installationer på browserens startsider på samme tid. Den nyeste installation stopper tidligere installationer, der stadig er i gang.

## <a name="configurable-setting-process"></a>Konfigurerbar indstillingsproces

Microsoft Managed Desktop anbefaler, at du følger en proces som den nedenfor, når du bruger konfigurerbare indstillinger for din organisation:

| Trin  | Proces |
| ------ | ------ |
| **Trin 1: Plan** | <ol type="1"><li>Få mere at vide om konfigurerbare indstillinger, og beslut, hvilke indstillingskategorier du vil konfigurere for organisationen.</li> <li>Opret en tidslinje, når du forventer at implementere ændringer i hver gruppe.</li> <li>Planlæg kommunikation til dine brugere, der opfylder dine interne processer for administration af ændringer. Hvis du f.eks. tilføjer startsider i browseren, skal du give brugerne besked om, at de har et nyt sæt startsider i deres browser efter installationen.</li></ol> |
| **Trin 2: Konfigurer installation af trin og trin** | <ol type="1"><li>Foretag ændringer i konfigurerbare indstillinger i administrationsportalen for Microsoft-administreret skrivebord.</li><li>Indrul ændringerne i faser, så de er klar til installation.</li> <li>Husk at informere brugerne om ændringerne, og hvordan ændringerne vil ændre deres enhedsoplevelse.</li><li>Konfigurer og faseændringer i administrationsportalen for Microsoft-administreret skrivebord. Få mere at vide under [Tilpas konfigurerbare indstillinger](config-setting-ref.md).</li></ol>|
| **Trin 3: Kommuniker ændringer** | <ol type="1"><li>Kommunikere oplysninger om kommende ændringer til dine brugere.</li> <li>For hver installation skal du fuldføre den kommunikation, der er en del af dine processer til administration af ændringer. Du skal tydeligt kommunikere enhver ændring, der påvirker, hvordan en bruger fungerer, eller hvad brugeren får vist på sin enhed.</li></ol> |
| **Trin 4: Installér ændringer** | Installér dine ændringer, startende med gruppen Test. Du kan bruge gruppen Test til at validere og foretage fejlfinding af eventuelle problemer i en gruppe med færre enheder, før du implementerer ændringer på større grupper af enheder. <br><br>Hvis du løber ind i problemer, kan du gendanne ændringen, opdatere indstillingen og sætte en ny installation i gang. Microsoft Managed Desktop anbefaler, at du følger den strukturerede fremgangsmåde og installerer i grupper i denne rækkefølge: Test, Først, Hurtig og derefter Bred. <br><br>Alle konfigurerbare indstillinger administreres ved hjælp af administrationsportalen for Microsoft-administreret skrivebord. Du kan få mere at vide [under Installér ændringer](config-setting-deploy.md). |
| **Trin 5: Registrer ændringer** | Registrer status for dine ændringer i sektionen Installationsstatus. For hver indstilling kan du: <ul><li>**Registrere status:**  Spore status, når du har implementeret ændringen. Status ændres til **I gang** og derefter enten **Fuldført** eller **Mislykket**. Hvis en installation mislykkes, åbnes der automatisk en supportanmodning for Microsoft Managed Desktop-handlinger for at undersøge problemet.</li> <li>**Se version, der er installeret:** Hver udrullet ændring har et versionsnummer.</li><li>**Gendan ændringer:** Hvis du gendanner en ændring, stoppes den aktuelle installation. Den gendanner alle grupper til de seneste ændringer, der blev installeret i alle grupper. Du vender tilbage til den senest kendte gode indstillingsværdi.</li><li>**Valider ændringer:** Når installationen er fuldført, skal du validere, at ændringerne er blevet anvendt som forventet.</li></ul> |

Hvis en installation mislykkes, eller du ikke kan gendanne en ændring, skal du [åbne en supportanmodning med](admin-support.md) Microsoft Managed Desktop Operations.

Få mere at vide under [Installér og spor konfigurerbare indstillinger](config-setting-deploy.md).

## <a name="additional-resources"></a>Yderligere ressourcer

- [Reference til konfigurerbare indstillinger](config-setting-ref.md)
- [Installer konfigurerbare indstillinger](config-setting-deploy.md)
