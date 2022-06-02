---
title: Metoder og -egenskaber for afhjælpningsaktivitet
description: API-svaret indeholder trussels-& håndtering af sikkerhedsrisici afhjælpningsaktiviteter, der er oprettet i din lejer. Du kan anmode om alle afhjælpningsaktiviteter, kun én afhjælpningsaktivitet eller oplysninger om eksponerede enheder for en valgt afhjælpningsopgave.
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
ms.openlocfilehash: 14f57d6590d580e0145abc2da788f184c88a721e
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840249"
---
# <a name="remediation-activity-methods-and-properties"></a>Metoder og -egenskaber for afhjælpningsaktivitet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

API-svaret indeholder [Threat & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md) afhjælpningsaktiviteter, der er oprettet i din lejer.

## <a name="methods"></a>Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
[Angiv alle afhjælpningsaktiviteter](get-remediation-all-activities.md)|Undersøgelsessamling|Returnerer oplysninger om alle afhjælpningsaktiviteter.
[Angiv eksponerede enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)|Undersøgelsesenhed|Returnerer oplysninger om eksponerede enheder for den angivne afhjælpningsaktivitet.
[Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)|Undersøgelsesenhed|Returnerer oplysninger om den angivne afhjælpningsaktivitet.

Få mere at vide om [afhjælpningsaktiviteter](tvm-remediation.md).

## <a name="properties"></a>Egenskaber

Egenskabs-id|Datatype|Beskrivelse
:---|:---|:---
Kategori|String|Kategori for afhjælpningsaktiviteten (software-/sikkerhedskonfiguration)
completerEmail|String|Hvis afhjælpningsaktiviteten blev udført manuelt af en person, indeholder denne kolonne deres mail
completerId|String|Hvis afhjælpningsaktiviteten blev udført manuelt af en person, indeholder denne kolonne sit objekt-id
completionMethod|String|En afhjælpningsaktivitet kan fuldføres "automatisk" (hvis alle enhederne er repareret) eller "manuelt" af en person, der vælger "Markér som fuldført".
oprettet til|Datetime|Det tidspunkt, hvor denne afhjælpningsaktivitet blev oprettet
Beskrivelse|String|Beskrivelse af denne afhjælpningsaktivitet
forfalder til|Datetime|Forfaldsdato, som forfatteren har angivet for denne afhjælpningsaktivitet
fixedDevices||Antallet af enheder, der er blevet rettet
ID|String|Id for denne afhjælpningsaktivitet
nameId|String|Relateret produktnavn
Prioritet|String|Prioritet, som opretteren har angivet for denne afhjælpningsaktivitet (Høj\Mellem\Lav)
Instruktion|String|Relateret produkt-id
produktivitetImpactRemediationType|String|Der kan kun anmodes om nogle få konfigurationsændringer for enheder, der ikke påvirker brugerne. Denne værdi angiver valget mellem "alle eksponerede enheder" eller "kun enheder uden brugerpåvirkning".
rbacGroupNames|String|Relaterede enhedsgruppenavne
anbefalet program|String|Anbefalet program til opgradering til
recommendedVendor|String|Anbefalet leverandør, der skal opgraderes til
recommendedVersion|String|Anbefalet version til opdatering/opgradering til
relatedComponent|String|Relateret komponent til denne afhjælpningsaktivitet (svarer til den relaterede komponent til en sikkerhedsanbefaling)
requesterEmail|String|Opretterens mailadresse
requesterId|String|Opretterobjekt-id
requesterNotes|String|De noter (fri tekst), som forfatteren har tilføjet til denne afhjælpningsaktivitet
Scid|String|SCID for den relaterede sikkerhedsanbefaling
Status|String|Status for afhjælpningsaktivitet (aktiv/fuldført)
statusLastModifiedOn|Datetime|Dato for opdatering af statusfeltet
targetDevices|Lang|Antal eksponerede enheder, som denne afhjælpning gælder for
Titel|String|Titlen på denne afhjælpningsaktivitet
Type|String|Afhjælpningstype
vendorId|String|Navn på relateret leverandør

## <a name="see-also"></a>Se også

- [Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)

- [Angiv alle afhjælpningsaktiviteter](get-remediation-all-activities.md)

- [Angiv eksponerede enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)

- [Risikobaseret trussel & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)

- [Sikkerhedsrisici i din organisation](tvm-weaknesses.md)
