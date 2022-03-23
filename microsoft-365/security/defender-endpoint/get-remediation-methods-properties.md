---
title: Afhjælpning af aktivitetsmetoder og -egenskaber
description: API-svaret indeholder trussels & håndtering af sikkerhedsrisici afhjælpningsaktiviteter, der er oprettet i din lejer. Du kan anmode om alle afhjælpningsaktiviteterne, kun én afhjælpningsaktivitet eller oplysninger om eksponerede enheder til en valgt afhjælpningsopgave.
keywords: apis, afhjælpning, afhjælpnings-API, hent, afhjælpningsopgaver, afhjælpningsmetoder, afhjælpningsegenskaber,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 124a44f6a04e4e4e77d80ac91ed4da169e2a4aae
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63593849"
---
# <a name="remediation-activity-methods-and-properties"></a>Afhjælpning af aktivitetsmetoder og -egenskaber

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

API-svaret indeholder [trussels & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md) afhjælpningsaktiviteter, der er blevet oprettet i din lejer.

## <a name="methods"></a>Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
[Vis alle afhjælpningsaktiviteter](get-remediation-all-activities.md)|Undersøgelsessamling|Returnerer oplysninger om alle afhjælpningsaktiviteter.
[Vis blotsatte enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)|Undersøgelsesenhed|Returnerer oplysninger om eksponerede enheder for den angivne afhjælpningsaktivitet.
[Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)|Undersøgelsesenhed|Returnerer oplysninger om den angivne afhjælpningsaktivitet.

Få mere at vide [om afhjælpningsaktiviteter](tvm-remediation.md).

## <a name="properties"></a>Egenskaber

Egenskabs-id|Datatype|Beskrivelse
:---|:---|:---
Kategori|String|Kategori af afhjælpningsaktiviteten (Software/sikkerhedskonfiguration)
completerEmail|String|Hvis afhjælpningsaktiviteten blev fuldført manuelt af en person, indeholder denne kolonne deres mail
completerId|String|Hvis afhjælpningsaktiviteten blev fuldført manuelt af en person, indeholder denne kolonne deres objekt-id
completionMethod|String|En afhjælpningsaktivitet kan udføres "automatisk" (hvis alle enhederne er rettet) eller "manuelt" af en person, der vælger "markér som fuldført".
createdOn|DateTime|Tidspunktet for denne afhjælpningsaktivitet blev oprettet
Beskrivelse|String|Beskrivelse af denne afhjælpningsaktivitet
dueOn|DateTime|Forfaldsdato, som opretteren har angivet for denne afhjælpningsaktivitet
fixedDevices||Antallet af enheder, der er blevet rettet
Id|String|Id for denne afhjælpningsaktivitet
nameId|String|Relateret produktnavn
Prioritet|String|Prioritet, som forfatteren har angivet for denne afhjælpningsaktivitet (Høj\Mellem\Lav)
productId|String|Relateret produkt-id
productivityImpactRemediationType|String|Der kan kun anmodes om nogle få konfigurationsændringer for enheder, der ikke påvirker brugere. Denne værdi angiver valget mellem "alle eksponerede enheder" eller "kun enheder uden brugerpåvirkning".
rbacGroupNames|String|Relaterede enhedsgruppenavne
recommendedProgram|String|Anbefalet program at opgradere til
anbefaletVenlighed|String|Anbefalet leverandør at opgradere til
recommendedVersion|String|Anbefalet version at opdatere/opgradere til
relatedComponent|String|Relateret komponent i denne afhjælpningsaktivitet (svarende til den relaterede komponent for en sikkerhedsanbefaling)
requesterEmail|String|Opretter-mailadresse
requesterId|String|Creator-objekt-id
anmoderNoter|String|De noter (gratis tekst), som forfatteren har tilføjet til denne afhjælpningsaktivitet
Scid|String|SCID for den relaterede sikkerhedsanbefaling
Status|String|Aktivitetsstatus for afhjælpning (aktiv/fuldført)
statusLastModifiedOn|DateTime|Dato for opdatering af statusfeltet
targetDevices|Lang|Antal blotlagte enheder, som denne afhjælpning gælder for
Titel|String|Titlen på denne afhjælpningsaktivitet
Type|String|Afhjælpningstype
vendorId|String|Relateret leverandørnavn

## <a name="see-also"></a>Se også

- [Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)

- [Vis alle afhjælpningsaktiviteter](get-remediation-all-activities.md)

- [Vis blotsatte enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)

- [Sårbarheder i din organisation](tvm-weaknesses.md)
