---
title: Sådan håndteres opdateringer i Microsoft Managed Desktop
description: At holde Microsoft-administreret skrivebord opdateret er en balance mellem hastighed og stabilitet.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: bf6ead692a82d485f6a8e3b3148bc05484c887a8
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63587247"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Sådan håndteres opdateringer i Microsoft Managed Desktop

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft Managed Desktop forbinder alle enheder til en moderne skybaseret infrastruktur.

At Windows, Office, drivere, firmware og Microsoft Store til Virksomheder-programmer opdateret er en balance mellem hastighed og stabilitet. Vi bruger opdateringsgrupper til at sikre, at opdateringer og politikker for operativsystemet rulles ud på en sikker måde. Du kan finde flere oplysninger i videoen [Microsoft Managed Desktop Change and Release Process](https://www.microsoft.com/videoplayer/embed/RE4mWqP).

Opdateringer, der udgives af Microsoft, er kumulative og kategoriseres som kvalitets- eller funktionsopdateringer. Du kan finde flere oplysninger [Windows Opdatering til virksomheder: Opdateringstyper](/windows/deployment/update/waas-manage-updates-wufb#update-types).

## <a name="update-groups"></a>Opdater grupper

Microsoft Managed Desktop bruger fire Azure AD-grupper til at administrere opdateringer:

| Gruppe | Beskrivelse |
| ------ | ------ |
| Test | Bruges til at validere ændringer af Microsoft-administreret skrivebordspolitik, opdateringer af operativsystem, funktionsopdateringer og andre ændringer, der er sendt til Azure AD-organisationen ("lejer"). Gruppen Test er: <br><ul><li>Bedst til test eller brugere, der kan give tidlig feedback.</li><li>Undtaget fra alle etablerede serviceaftaler og brugersupport.</li><li>Tilgængelig til validering af kompatibiliteten af programmer med ændringer i den nye politik eller det nye operativsystem.</li></ul> |
| Første | Indeholder tidlige softwareindlæsere og enheder, der kan være underlagt foreløbige opdateringer. <br><br> Enheder i denne gruppe kan opleve strømsvigt, hvis der er scenarier, som ikke blev dækket under test i testringen. |
| Hurtig | Prioriterer hastighed over stabiliteten. Gruppen Fast er: <br><ul><li>Nyttig til at registrere kvalitetsproblemer, før de tilbydes til gruppen Bred.</li> <li>Det næste lag af validering og er typisk mere stabilt end Grupperne Test og Første.</li></ul> |
| Bred | Denne gruppe er den sidste gruppe, der har adgang til funktions- og kvalitetsopdateringer. <br><br> Gruppen Bred indeholder de fleste brugere i Azure AD-organisationen og foretrækker derfor stabilitet i forhold til hastighed i installationen. Test af apps skal udføres med denne gruppe, da miljøet er det mest stabile. |

### <a name="moving-devices-between-update-groups"></a>Flytte enheder mellem opdateringsgrupper

Det kan være en ide, at nogle enheder skal modtage opdateringer sidst, og andre, som du gerne vil gå i gang med først. Hvis du vil flytte disse enheder til den relevante opdateringsgruppe, skal du [se Tildel enheder til en installationsgruppe](../working-with-managed-desktop/assign-deployment-group.md).

Du kan finde flere oplysninger om roller og ansvarsområder i disse installationsgrupper under [Microsoft-administrerede skrivebordsroller og -ansvarsområder](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Brug af microsoft-administrerede skrivebordsopdateringsgrupper

Der er dele af tjenesten, som du administrerer, f.eks. appinstallation, hvor det kan være nødvendigt at målrette mod alle administrerede enheder.

## <a name="update-deployment"></a>Opdateringsinstallation

Nedenfor beskrives det, hvordan opdateringsinstallation fungerer.

| Trin | Beskrivelse |
| ------ | ------ |
| Trin 1 | Microsoft Managed Desktop installerer en ny funktion eller kvalitetsopdatering i overensstemmelse med den tidsplan, der er angivet i følgende tabel.|
| Trin 2 | Under installationen overvåger Microsoft Managed Desktop for tegn på fejl eller afbrydelser baseret på diagnostiske data og brugersupportsystemet. Hvis der registreres nogen, afbryder vi straks installationen til alle aktuelle og fremtidige grupper.<br><br> Hvis der f.eks. bliver fundet et problem under installation af en kvalitetsopdatering til gruppen Første, vil opdatering af installationer til grupperne First, Fast og Broad blive sat på pause, indtil problemet er løst. <br><br> Du kan rapportere kompatibilitetsproblemer ved at arkivere en billet i administrationsportalen for Microsoft Managed Desktop. <br><br> Funktions- og kvalitetsopdateringer afbrydes midlertidigt enkeltvis. Pausen er som standard i kraft i 35 dage. Det kan dog reduceres eller forlænges, afhængigt af om problemet er mindsket. |
| Trin 3 | Når grupperne er blevet fjernet, genoptages udrulningen i overensstemmelse med tidsplanen i tabellen. |
| Trin 4| Brugerne har mulighed for at svare på meddelelser om genstart i en bestemt periode. Denne periode kaldes deadline, og den måles fra det tidspunkt, hvor opdateringen tilbydes til enheden. <br><br> I dette tidsrum genstartes enheden kun automatisk uden for aktive timer. Når denne periode udløber, er deadlinen nået, og enheden genstartes ved den næste tilgængelige mulighed, uanset aktive timer. <br><br> Deadline for kvalitetsopdateringer er tre dage. for funktionsopdateringer er det fem dage. |

> [!NOTE]
> Denne installationsproces gælder for både funktions- og kvalitetsopdateringer, men tidslinjen varierer for hver enkelt.

## <a name="deployment-settings"></a>Installationsindstillinger

Opdater installationsindstillinger nedenfor:

| Opdateringstype | Test | Første | Hurtig | Bred |
| ------ | ------ | ------ | ------ | ------ |
| Kvalitetsopdateringer til operativsystem | Nul dage | Nul dage | Nul dage | Syv dage |
| Funktionsopdateringer til operativsystem | Nul dage | 30 dage | 60 dage | 90 dage |
| Drivere/firmware | Følger tidsplanen for kvalitetsopdateringer. | Følger tidsplanen for kvalitetsopdateringer. | Følger tidsplanen for kvalitetsopdateringer. | Følger tidsplanen for kvalitetsopdateringer. |
| Antivirusdefinition | Opdateret med hver scanning. | Opdateret med hver scanning. | Opdateret med hver scanning. | Opdateret med hver scanning. |
| Microsoft 365 Apps til store virksomheder | [Få mere at vide](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Få mere at vide](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Få mere at vide](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Få mere at vide](../get-started/m365-apps.md#updates-to-microsoft-365-apps) |
| Microsoft Edge | [Få mere at vide](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Få mere at vide](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Få mere at vide](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Få mere at vide](../get-started/edge-browser-app.md#updates-to-microsoft-edge) |
| Microsoft Teams | [Få mere at vide](../get-started/teams.md#updates) | [Få mere at vide](../get-started/teams.md#updates) | [Få mere at vide](../get-started/teams.md#updates) | [Få mere at vide](../get-started/teams.md#updates) |

>[!NOTE]
>Disse udskydelsesperioder er designet til at sikre høj sikkerhed og ydelsesstandarder for alle brugere.<br><br> Baseret på data, der er indsamlet på tværs af alle Microsoft Managed Desktop-enheder og de varierende omfang og indvirkninger af opdateringer, forbeholder Microsoft Managed Desktop sig fleksibilitet til at ændre længden af ovenstående udskydelsesperioder for alle og alle installationsgrupper på ad hoc-basis.
>
>Microsoft Managed Desktop udfører en uafhængig vurdering af hver enkelt Windows funktionsudgivelse for at evaluere dens nødvendighed og anvendelighed til dens administrerede lejere. Microsoft Managed Desktop kan derfor muligvis eller ikke installere alle Windows funktionsopdateringer.

## <a name="windows-insider-program"></a>Windows Insider Program

Microsoft Managed Desktop understøtter ikke enheder, der er en del Windows Insider-programmet.

Programmet Windows Insider bruges til at validere foreløbige Windows software. Den er beregnet til enheder, der ikke er missionskritiske. Selvom det er et vigtigt Microsoft-tiltag, er det ikke beregnet til bred udrulning i produktionsmiljøer.

Alle enheder, der Windows med Insider-builds, kan blive sat ind i gruppen Test. Disse enheder vil være undtaget fra serviceaftaler på opdateringsniveau og brugersupport fra Microsoft Managed Desktop.

## <a name="bandwidth-management"></a>Båndbreddestyring

Vi bruger [Leveringsoptimering](/windows/deployment/update/waas-delivery-optimization) til alle opdateringer til operativsystem og driver. Leveringsoptimering minimerer downloadstørrelsen fra Windows Update ved at søge efter opdateringer fra peers inden for virksomhedens netværk.
