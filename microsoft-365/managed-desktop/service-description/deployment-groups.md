---
title: Installationsgrupper for enheder
description: Installationsgrupperne, der bruges til at administrere opdateringer og andre ændringer
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 624bde84da9a0c35f5814e3b6c67c2d190683fc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606591"
---
# <a name="device-deployment-groups"></a>Installationsgrupper for enheder

Microsoft Managed Desktop bruger installationsgrupper til at administrere frigivelsen af opdateringer og konfigurationsændringer på enheder. Enheder føjes automatisk til installationsgrupper ("ringe" eller "opdateringsgrupper"), når de er tilmeldt Microsoft Managed Desktop. Installationsgrupper gør det muligt for enheder at modtage ændringer i en faseret tidslinje.

Det kan være en ide kun at tildele bestemte enheder til testformål eller udpege bestemte tidlige brugere til at modtage ændringerne først. Hvis du har kritiske enheder, f.eks. dem, der bruges af ledere, eller som laver forretningskritiske funktioner, kan det være en ide at beholde dem i den gruppe, der får opdateringer om den langsommeste kadence. Microsoft Managed Desktop giver dig mulighed for at angive, at en enhed skal forblive i en af følgende grupper.

| Gruppe | Beskrivelse |
| ----- | ----- |
| Test | Gruppen Test er bedst til enheder, der bruges til test, eller brugere, der kan benytte hyppige ændringer, eksponering for nye funktioner og kan give tidlig feedback.<br><br>Denne gruppe modtager ofte ændringer, og oplevelser i denne gruppe har en stærk effekt. Testgruppen er undtaget fra alle etablerede serviceaftaler og brugersupport. Det er bedst kun at flytte nogle få enheder i starten og derefter gennemse brugeroplevelsen. Microsoft Managed Desktop tildeler ikke automatisk enheder til denne gruppe. Denne gruppe indeholder kun enheder, du angiver.
| Første | The First group is ideal for early adopters, volunteer, designated validators, IT pros, or representatives of business functions. Det vil sige personer, der kan validere ændringer og give dig feedback på oplevelsen.
| Hurtig | Fast-gruppen er ideel til repræsentanter for virksomhedsfunktioner. Disse personer kan validere ændringer før bred udrulning.
| Bred | Gruppen Bred modtager ændringer sidst.<br><br>Det meste af din organisation vil typisk være i denne gruppe. Du kan angive enheder, der skal være i denne gruppe. Disse enheder bør modtage ændringer, sidst fordi de udfører forretningskritiske funktioner eller tilhører brugere i vigtige roller.
| Automatisk | Vælg Automatisk, når Microsoft Managed Desktop automatisk skal tildele enheder til en af de andre grupper.<br><br>Vi tildeler ikke automatisk enheder til Test. Hvis du vil frigive en enhed, som du tidligere har angivet, så den kan tildeles automatisk igen, skal du vælge denne indstilling.

Du kan finde flere oplysninger om, Windows opdateringer administreres i grupper, under [Hvordan opdateringer håndteres i Microsoft Managed Desktop](updates.md).

## <a name="labels"></a>Etiketter

Den gruppe, der er tildelt efter kolonne, indeholder følgende etiketter:

| Etiket | Beskrivelse |
| ----- | ----- |
| Administrator | Enheden er i en gruppe, du har angivet. |
| Automatisk | Microsoft-administreret skrivebord tildelte gruppen. |
| Afventer | Enheden er i gang med at flytte til en gruppe. |

Kolonnen **Gruppe** viser altid den gruppe, enheden aktuelt er i, og den opdateres kun, når flytningen er fuldført.

> [!IMPORTANT]
> Forsøg ikke at ændre medlemskabet af disse grupper direkte. Følg altid de trin, der er beskrevet [i Tildel enheder til en installationsgruppe](../working-with-managed-desktop/assign-deployment-group.md).
