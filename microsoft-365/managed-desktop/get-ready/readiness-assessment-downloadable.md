---
title: Kontrol af parathed til download
description: Kontrollerer enheds- og netværksindstillinger, herunder nødvendige slutpunkter
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 9e3ad0953cdbd6561f9a0145ccff5aefe24b8dfb
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63602977"
---
# <a name="downloadable-readiness-assessment-checker"></a>Kontrol af parathed til download

For at fungere godt sammen med Microsofts administrerede skrivebord skal enhederne opfylde visse krav til hardware og indstillinger. Hver enhed skal kunne oprette forbindelse til vigtige slutpunkter.

Download og kør værktøjet til vurdering af parathed for at hente en HTML-rapport, få vist resultater og foretage en handling. Du skal downloade værktøjet og støttefilerne. Kør den derefter manuelt på hver enhed, du vil tilmelde dig, i Microsoft Managed Desktop.

For hver kontrol rapporterer værktøjet et af tre mulige resultater:

| Resultat | Betydning |
| ----- | ----- |
| Klar | Der kræves ingen handling, før du har fuldført tilmeldingen. |
| Vejledning | Følg trinnene i værktøjet for at få den bedste oplevelse med registrering og for brugere. <br><br> Du *kan* fuldføre tilmeldingen, men du skal løse disse problemer, før du installerer din første enhed. |
| Ikke klar | **Din tilmelding mislykkes** , hvis du ikke løser disse problemer. <br><br> Følg trinnene i værktøjet for at løse dem. |

## <a name="obtain-the-checker"></a>Hent kontrol

Download .zip fil fra https://aka.ms/mmddratoolv0.

> [!NOTE]
> Den bruger, der kører værktøjet, skal have lokale administratorrettigheder på den enhed, hvor brugeren kører det.

**Sådan kører du værktøjet:**

1. Kopiér den .zip fil til hver enhed, du vil kontrollere.
2. Udtræk alle filer i den komprimerede download.
3. Kør **Microsoft.MMD.DeviceReadinessAssessmentTool.exe**.
4. Når prompten Brugeradgangskontrol vises, skal du vælge **Ja**. Værktøjet kører og åbner en rapport i din standardbrowser.

Du kan også downloade og udtrække .zip til en delt placering og få adgang **Microsoft.MMD.DeviceReadinessAssessmentTool.exe** fra hver enhed. Kør den derefter lokalt.

## <a name="checks"></a>Kontroller

Værktøjet, der kan downloades, kontrollerer disse enheder og netværksrelaterede elementer:

| Tjek | Beskrivelse |
| ----- | ----- |
| Hardware | Enheder skal opfylde specifikke hardwarekrav for at fungere med Microsoft Managed Desktop. Du kan finde flere oplysninger under [Krav til enheder](../service-description/device-list.md). <br><br> Hvis din enhed ikke kontrollerer noget, er den ikke kompatibel med Microsoft Managed Desktop. |
| Netværksslutpunkter | Enheder kan i høj grad nå flere [vigtige slutpunkter for at arbejde](network.md) med Microsoft Managed Desktop. <br><br> Hvis værktøjet rapporterer et **ikke klar-resultat** , skal du se den detaljerede rapport for at finde ud af, hvilke slutpunkter der ikke kunne oprettes forbindelse til. Juster derefter din firewall eller andre netværksindstillinger for at sikre, at disse slutpunkter kan nås. |

### <a name="other-settings"></a>Andre indstillinger

| Indstilling | Beskrivelse |
| ----- | ----- |
| Enterprise Wi-Fi profiler | Et **Advisory-resultat** betyder, at du bruger nogle af Wi-Fi, der skal have certifikater og profiler til at fungere korrekt. Få mere at vide under [Installér certifikater og Wi-Fi/VPN-profil](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile). |
| LAN-profiler | Et **rådgivningsresultat** betyder, at du har LAN'er, der skal have certifikater og profiler til at fungere korrekt. Få mere at vide under [Forbered certifikater og netværksprofiler til Microsoft Managed Desktop](certs-wifi-lan.md). |
| VPN-profiler | En **vejledning** betyder, at du bruger et virtuelt privat netværk (VPN). Opret en VPN-profil, der installerer certifikater, der er integreret Microsoft Intune. Få mere at vide under [Forbered certifikater og netværksprofiler til Microsoft Managed Desktop](certs-wifi-lan.md). |
| Tilknyttede drev | Et **rådgivningsresultat** betyder, at du har nogle tilknyttede drev, som ikke anbefales. Få mere at vide under [Forbered tilknyttede drev til Microsoft Managed Desktop](mapped-drives.md). |
| Udskriv køer | Et **rådgivningsresultat** betyder, at du har nogle udestående udskriftskøer, hvilket ikke anbefales. En løsning er at bruge skyudskrivning. Få mere at vide under [Forbered udskrivningsressourcer til Microsoft Managed Desktop](printing.md). |
| Proxyer | Et **rådgivningsresultat** betyder, at du har en proxyserver i brug. Du kan få mere at vide [under Netværkskonfiguration til Microsoft Managed Desktop](network.md). |
