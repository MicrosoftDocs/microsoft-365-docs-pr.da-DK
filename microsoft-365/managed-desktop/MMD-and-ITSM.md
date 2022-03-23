---
title: Microsoft-administreret skrivebord og ITIL
description: Korrelerer ITIL-faser med Microsoft Managed Desktop-oplysninger og artikler
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, ITISM
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b9984e308b6681512297e484817f95206283385e
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/13/2022
ms.locfileid: "63587679"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Microsoft-administreret skrivebord og ITIL

Mange organisationer finder det værdifuldt at strukturere deres it-tjenester i stil med en formaliseret IT-tjenestemodel (ITSM), f.eks [. ITIL](https://www.axelos.com/best-practice-solutions/itil). 

Microsoft Managed Desktop gør det muligt for din organisation at overholde mange vigtige aspekter af sådanne formaliserede ITSM-modeller. Hvis du bruger ITIL som eksempel, kan du i denne artikel få vist forbindelserne mellem almindelige ITIL-faser og -processer og tilsvarende Microsoft Managed Desktop-funktioner, hvor det er relevant. Disse oplysninger gælder kun for Microsoft Managed Desktop-delen af din organisation.

Du kan finde mere omfattende oplysninger om ITIL og dens faser og proces i [dokumentationen](https://www.axelos.com/best-practice-solutions/itil).


## <a name="service-design"></a>Servicedesign

Denne tabel relaterer vigtige ITIL-faser og -processer til Microsoft Managed Desktop-funktioner med links til vores dokumentation for at få flere oplysninger:



|ITIL-proces |Beskrivelse  |Dokumentation |
|---------|---------|---------|
|Administration på tjenesteniveau     | Svartider defineres for anmodninger og hændelser for administratorer.  |  [Administratorsupport til Microsoft-administreret skrivebord](working-with-managed-desktop/admin-support.md)  |
|Administration af tjenestekataloger     | Tjenestebeskrivelse, der beskriver komponenterne i tjenesten, bevares i forhold til tjenestens tilstand, som er tilgængelig for alle aktuelle og interesserede kunder.<br><br>Forudsætninger, der er beskrevet for at forstå, hvad der er nødvendigt for at kunne anvende tjenesten.  | - [Tjenestebeskrivelse for Microsoft-administreret skrivebord](service-description/index.md)<br><br>- [Bliv klar til tilmelding i Microsoft Managed Desktop](get-ready/index.md)  |
|Administration af informationssikkerhed     | Sikkerhedsoplysninger, herunder informationssikkerhed for tjenesten.<br><br> Sikkerhedsrelaterede politikker og andre oplysninger om, hvordan enheder konfigureres.   | - [Sikkerhed i Microsoft-administreret skrivebord](service-description/security.md)<br><br>- [Enhedskonfiguration](service-description/device-policies.md)  |
|Administration af tilgængelighed     |  Microsoft Managed Desktop afbalancerer ansvaret med din organisation for at sikre, at tjenesten er tilgængelig.<br><br>Administratorer og brugere har ruter til respektive support, hvis der er problemer med tjenesten eller tilgængeligheden. | - [Microsoft-administreret skrivebordshandlinger og -overvågning](service-description/operations-and-monitoring.md)<br><br>- [Administratorsupport til Microsoft-administreret skrivebord](working-with-managed-desktop/admin-support.md)<br>- [Få hjælp til brugere](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Tjenesteovergang


|ITIL-proces |Beskrivelse  |Dokumentation |
|---------|---------|---------|
|Administration af ændringer     | Defineret ansvarsbalance, procesoversigt og typer relateret til tilgængelig ændringsstyring.  | [Microsoft-administreret skrivebordshandlinger og -overvågning](service-description/operations-and-monitoring.md#change-management) |
|Administration af udgivelse og installation     |  Microsoft Managed Desktop administrerer opdateringer til enheder, der er tilmeldt tjenesten.  | [Sådan håndteres opdateringer i Microsoft Managed Desktop](service-description/updates.md)        |
|Administration af tjenesteaktiver og konfiguration     | Oplysninger om din organisations Microsoft Managed Desktop-installation er tilgængelige på it-administrationsportalen.  | [Administratorsupport til Microsoft-administreret skrivebord](working-with-managed-desktop/admin-support.md) |
|Vidensstyring     | Oplysningerne på Microsoft Managed Desktop-tjenesten holdes opdateret på dette websted.   | [Ændringsoversigt for microsoft-administreret skrivebordsdokumentation](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Tjenestehandling


|ITIL-proces |Beskrivelse  |Dokumentation  |
|---------|---------|---------|
|Administration af begivenheder     |  Oplysninger om overvågning af enheder er angivet.<br><br>Standardoperativsystemer til Tjenesten Microsoft Managed Desktop er detaljerede. |  - [Sikkerhed i Microsoft-administreret skrivebord](service-description/security.md)<br>- [Microsoft-administreret skrivebordshandlinger og -overvågning](service-description/operations-and-monitoring.md)       |
|Hændelsesstyring  | Microsoft Managed Desktop vil undersøge og reagere på hændelser pr. defineret alvorsgradsdefinitioner.  |  [Supportanmodningsdefinitioner for alvorsgrad](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Administration af anmodning     |  Process for anmodninger om oplysninger og ændringsanmodninger relateret til Microsoft Managed Desktop-tjenesten er defineret.         |[Administratorsupport til Microsoft-administreret skrivebord](working-with-managed-desktop/admin-support.md)         |
|Problemstyring     | Eventuelle problemer med tjenesten skal dirigeres til dit lokale kontoteam på nuværende tidspunkt. | Dokumentation under udvikling |
|Adgangsstyring     | Komponenter og ansvarsområder for access-administration for kunden for at sikre, at funktionaliteten er detaljeret.  | [Administration af identitet og adgang](service-description/security.md#identity-and-access-management)        |
