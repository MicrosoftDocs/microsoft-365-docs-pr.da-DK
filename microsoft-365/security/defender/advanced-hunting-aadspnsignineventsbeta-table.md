---
title: Tabellen AADSpnSignInEventsBeta i det avancerede jagtskema
description: Få mere at vide om oplysninger, Azure Active Directory er tjenestens hovedstol og tabel med administrerede identitetshændelser.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, AlertInfo, alert, enheder, bevis, fil, IP-adresse, enhed, computer, bruger, konto, identitet, AAD
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 77cf2d7b74dfc4ccea88661642579f5244e14089
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63591189"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**Gælder for:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Tabellen `AADSpnSignInEventsBeta` er i øjeblikket i betaversionen og tilbydes på kort sigt, så du kan lede efter Azure Active Directory (AAD)-logonhændelser. Kunder skal have en Azure Active Directory Premium P2-licens for at kunne indsamle og få vist aktiviteter for denne tabel. Microsoft vil med tiden flytte alle logonskemaoplysninger til `IdentityLogonEvents` tabellen.

Tabellen `AADSpnSignInEventsBeta` i det avancerede søgeskema indeholder oplysninger om Azure Active Directory og administrerede identitetstegn. Du kan få mere at vide om de forskellige typer logon Azure Active Directory [rapporter om logonaktivitet – forhåndsvisning](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Kolonnenavn|Datatype|Beskrivelse|
|---|---|---|
|`Timestamp`|`datetime`|Dato og klokkeslæt for, hvornår posten blev oprettet|
|`Application`|`string`|Program, der udførte den optagede handling|
|`ApplicationId`|`string`|Entydigt id for programmet|
|`IsManagedIdentity`|`boolean`|Angiver, om logon blev startet af en administreret identitet|
|`ErrorCode`|`int`|Indeholder fejlkoden, hvis der opstår en logonfejl. Hvis du vil finde en beskrivelse af en bestemt fejlkode, skal du gå til <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Entydigt id for logonhændelsen|
|`ServicePrincipalName`|`string`|Navnet på den tjenesteinspektør, der startede logon|
|`ServicePrincipalId`|`string`|Entydigt id for den tjenesteinspektør, der startede logon|
|`ResourceDisplayName`|`string`|Vist navn på den ressource, der blev åbnet|
|`ResourceId`|`string`|Entydigt id for den ressource, der blev åbnet|
|`ResourceTenantId`|`string`|Entydigt id for lejeren for den ressource, der blev åbnet|
|`IPAddress`|`string`|IP-adresse, der er tildelt slutpunktet og brugt under relateret netværkskommunikation|
|`Country`|`string`|Kode på to bogstaver, der angiver det land, hvor klientens IP-adresse er geolokeret|
|`State`|`string`|Den stat, hvor logon indtraf, hvis det er muligt|
|`City`|`string`|By, hvor kontobrugeren er placeret|
|`Latitude`|`string`|Koordinaterne nord for syd for logonplaceringen|
|`Longitude`|`string`|Koordinaterne øst mod vest for logonplaceringen|
|`RequestId`|`string`|Entydigt id for anmodningen|
|`ReportId`|`string`|Entydigt id for hændelsen|
||||

## <a name="related-articles"></a>Relaterede artikler

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Avanceret jagtoversigt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Lær forespørgselssproget](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Forstå skemaet](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
