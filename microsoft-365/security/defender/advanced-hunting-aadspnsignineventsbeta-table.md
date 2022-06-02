---
title: Tabellen AADSpnSignInEventsBeta i det avancerede jagtskema
description: Få mere at vide om oplysninger, der er knyttet til Azure Active Directory tjenesteprincipal og tabellen med administrerede identitetslogonhændelser.
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
ms.openlocfilehash: b1b9d6405abdddea42652cfd4c532df91eeb6b30
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842208"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**Gælder for:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Tabellen `AADSpnSignInEventsBeta` er i øjeblikket i betaversion og tilbydes på kort sigt, så du kan gå på jagt efter Azure Active Directory (AAD)-logonhændelser. Kunder skal have en Azure Active Directory Premium P2-licens for at indsamle og få vist aktiviteter for denne tabel. Microsoft flytter til sidst alle logonskemaoplysninger til tabellen `IdentityLogonEvents` .

Tabellen `AADSpnSignInEventsBeta` i det avancerede jagtskema indeholder oplysninger om Azure Active Directory tjenesteprincipal og administrerede identitetslogon. Du kan få mere at vide om de forskellige typer logon i [Azure Active Directory logonaktivitetsrapporter – prøveversion](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Kolonnenavn|Datatype|Beskrivelse|
|---|---|---|
|`Timestamp`|`datetime`|Dato og klokkeslæt for oprettelse af posten|
|`Application`|`string`|Program, der udførte den registrerede handling|
|`ApplicationId`|`string`|Entydigt id for programmet|
|`IsManagedIdentity`|`boolean`|Angiver, om logon blev startet af en administreret identitet|
|`ErrorCode`|`int`|Indeholder fejlkoden, hvis der opstår en logonfejl. Hvis du vil finde en beskrivelse af en bestemt fejlkode, skal du gå til <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Entydigt id for logonhændelsen|
|`ServicePrincipalName`|`string`|Navnet på den tjenesteprincipal, der startede logon|
|`ServicePrincipalId`|`string`|Entydigt id for den tjenesteprincipal, der startede logon|
|`ResourceDisplayName`|`string`|Vist navn på den ressource, der er åbnet|
|`ResourceId`|`string`|Entydigt id for den ressource, der er adgang til|
|`ResourceTenantId`|`string`|Entydigt id for lejeren for den ressource, der er adgang til|
|`IPAddress`|`string`|IP-adresse, der er tildelt slutpunktet og bruges under relateret netværkskommunikation|
|`Country`|`string`|Kode på to bogstaver, der angiver det land, hvor klientens IP-adresse er geolokaliseret|
|`State`|`string`|Angiv, hvor logon fandt sted, hvis det er muligt|
|`City`|`string`|By, hvor kontobrugeren er placeret|
|`Latitude`|`string`|Koordinaterne nord til syd for logonplaceringen|
|`Longitude`|`string`|Koordinaterne fra øst til vest for logonplaceringen|
|`RequestId`|`string`|Entydigt id for anmodningen|
|`ReportId`|`string`|Entydigt id for hændelsen|
||||

## <a name="related-articles"></a>Relaterede artikler

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Oversigt over avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Få mere at vide om forespørgselssproget](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Forstå skemaet](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
