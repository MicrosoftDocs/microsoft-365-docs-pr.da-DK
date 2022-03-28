---
title: AADSignInEventsBeta-tabel i det avancerede jagtskema
description: Få mere Azure Active Directory om tabellen med logonhændelser i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, fil, IP-adresse, enhed, maskine, bruger, konto, identitet, AAD
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dad3ea9fe4297d93864032130e3f6d6b5f6e4e82
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63597540"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Tabellen `AADSignInEventsBeta` er i øjeblikket i betaversionen og tilbydes på kort sigt, så du kan lede efter Azure Active Directory (AAD)-logonhændelser. Kunder skal have en Azure Active Directory Premium P2-licens for at kunne indsamle og få vist aktiviteter for denne tabel. Alle oplysninger om logonskemaet vil med tiden gå til `IdentityLogonEvents` tabellen.

Tabellen `AADSignInEventsBeta` i det avancerede søgeskema indeholder oplysninger Azure Active Directory og interaktive og ikke-interaktive logons. Få mere at vide om logon Azure Active Directory [rapporter om logonaktivitet – forhåndsvisning](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen. Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i den avancerede [jagtreference](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Kolonnenavn|Datatype|Beskrivelse|
|---|---|---|
|`Timestamp`|`datetime`|Dato og klokkeslæt for, hvornår posten blev oprettet|
|`Application`|`string`|Program, der udførte den optagede handling|
|`ApplicationId`|`string`|Entydigt id for programmet|
|`LogonType`|`string`|Logonsessionstype, interaktiv, fjern interaktiv (RDP), netværk, batch og tjeneste|
|`ErrorCode`|`int`|Indeholder fejlkoden, hvis der opstår en logonfejl. Hvis du vil finde en beskrivelse af en bestemt fejlkode, skal du gå til <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Entydigt id for logonhændelsen|
|`SessionId`|`string`|Entydigt nummer, der er tildelt en bruger af et websteds server under besøget eller sessionen|
|`AccountDisplayName`|`string`|Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet eller fornavn, en initial for mellemnavn og et efternavn eller efternavn.|
|`AccountObjectId`|`string`|Entydigt id for kontoen i Azure AD|
|`AccountUpn`|`string`|Brugerens hovednavn (UPN) for kontoen|
|`IsExternalUser`|`int`|Angiver, om den bruger, der er logget på, er ekstern. Mulige værdier: -1 (ikke angivet), 0 (ikke ekstern), 1 (ekstern).|
|`IsGuestUser`|`boolean`|Angiver, om den bruger, der er logget på, er en gæst i lejeren|
|`AlternateSignInName`|`string`|Brugerens hovednavn i det lokale miljø (UPN) for den bruger, der logger på Azure AD|
|`LastPasswordChangeTimestamp`|`datetime`|Dato og klokkeslæt for, hvornår den bruger, der er logget på, senest har ændret sin adgangskode|
|`ResourceDisplayName`|`string`|Vist navn på den ressource, der blev åbnet|
|`ResourceId`|`string`|Entydigt id for den ressource, der blev åbnet|
|`ResourceTenantId`|`string`|Entydigt id for lejeren for den ressource, der blev åbnet|
|`DeviceName`|`string`|Fuldt kvalificeret domænenavn på computeren|
|`AadDeviceId`|`string`|Entydigt id for enheden i Azure AD|
|`OSPlatform`|`string`|Platform for operativsystemet, der kører på computeren. Angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7.|
|`DeviceTrustType`|`string`|Angiver tillidstypen for den enhed, der er logget på. Kun for administrerede enhedsscenarier. Mulige værdier er Workplace, AzureAd og ServerAd.|
|`IsManaged`|`int`|Angiver, om den enhed, der startede logon' er en administreret enhed (1) eller ikke en administreret enhed (0)|
|`IsCompliant`|`int`|Angiver, om den enhed, der startede logon' er kompatibel (1) eller ikke-kompatibel (0)|
|`AuthenticationProcessingDetails`|`string`|Oplysninger om godkendelsesprocessoren|
|`AuthenticationRequirement`|`string`|Den type godkendelse, der kræves til logon. Mulige værdier: multiFactorAuthentication (MFA var påkrævet) og enkeltFaktorauthentication (ingen MFA var påkrævet).|
|`TokenIssuerType`|`int`|Angiver, om tokenudstederen er Azure Active Directory (0) eller Active Directory Federation Services (1)|
|`RiskLevelAggregated`|`int`|Aggregeret risikoniveau under logon. Mulige værdier: 0 (aggregeret risikoniveau er ikke angivet), 1 (ingen), 10 (lav), 50 (mellem) eller 100 (høj).|
|`RiskDetails`|`int`|Oplysninger om den risikabelde tilstand for den bruger, der er logget på|
|`RiskState`|`int`|Angiver risikabel brugertilstand. Mulige værdier: 0 (ingen), 1 (bekræftet sikker), 2 (afhjælpet), 3 (afvist), 4 (på risiko) eller 5 (bekræftet kompromitteret).|
|`UserAgent`|`string`|Oplysninger om brugeragenter fra webbrowseren eller et andet klientprogram|
|`ClientAppUsed`|`string`|Angiver den anvendte klientapp|
|`Browser`|`string`|Oplysninger om versionen af den browser, der bruges til at logge på|
|`ConditionalAccessPolicies`|`string`|Oplysninger om politikkerne for betinget adgang anvendt på logonhændelsen|
|`ConditionalAccessStatus`|`int`|Status for politikkerne for betinget adgang anvendt på logon. Mulige værdier er 0 (politikker anvendt), 1 (forsøg på at anvende politikker mislykkedes) eller 2 (politikker anvendes ikke).|
|`IPAddress`|`string`|IP-adresse, der er tildelt slutpunktet og brugt under relateret netværkskommunikation|
|`Country`|`string`|Kode på to bogstaver, der angiver det land, hvor klientens IP-adresse er geolokeret|
|`State`|`string`|Den stat, hvor logon indtraf, hvis det er muligt|
|`City`|`string`|By, hvor kontobrugeren er placeret|
|`Latitude`|`string`|Koordinaterne nord for syd for logonplaceringen|
|`Longitude`|`string`|Koordinaterne øst mod vest for logonplaceringen|
|`NetworkLocationDetails`|`string`|Oplysninger om netværksplacering for godkendelsesprocessoren for logonhændelsen|
|`RequestId`|`string`|Entydigt id for anmodningen|
|`ReportId`|`string`|Entydigt id for hændelsen|

## <a name="related-articles"></a>Relaterede artikler

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [Avanceret jagtoversigt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Lær forespørgselssproget](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Forstå skemaet](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
