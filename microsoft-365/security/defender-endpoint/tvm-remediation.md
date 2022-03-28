---
title: Afhjælpe sårbarheder med Håndtering af trusler og sikkerhedsrisici
description: Afhjulpet sikkerhedseksperter, der opdages via sikkerhedsanbefalinger, og opret undtagelser, hvis det er nødvendigt, Håndtering af trusler og sikkerhedsrisici.
keywords: Microsoft Defender for Endpoint tvm remediation, Microsoft Defender for Endpoint tvm, Håndtering af trusler og sikkerhedsrisici, threat & håndtering af sikkerhedsrisici, threat & håndtering af sikkerhedsrisici  afhjælpning, tvm remediation intune, tvm remediation sccm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4f00e28e4dfa1c7806167c789a869be70c6fb78
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597854"
---
# <a name="remediate-vulnerabilities-with-threat-and-vulnerability-management"></a>Afhjælpe sårbarheder med Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="request-remediation"></a>Anmod om afhjælpning

Den Håndtering af trusler og sikkerhedsrisici funktion i Microsoft Defender til slutpunkt, bygger bro mellem Sikkerhed og it-administratorer via arbejdsprocessen for afhjælpningsanmodning. Sikkerhedsadministratorer som dig kan anmode it-administratoren om at afhjælpe en sikkerhedsrisiko fra siderne **med sikkerhedsanbefaling** til Intune.

### <a name="enable-microsoft-intune-connection"></a>Aktivere Microsoft Intune forbindelse

Hvis du vil bruge denne funktion, skal Microsoft Intune oprette forbindelse. I portalen Microsoft 365 Defender skal du gå til **Indstillinger Avancerede** \>  \> **funktioner.** Rul ned, og se **efter Microsoft Intune forbindelse**. Til/fra-knappen er som standard slået fra. Slå din **Microsoft Intune forbindelse** **Til.**

**Bemærk**! Hvis du har aktiveret Intune-forbindelsen, får du mulighed for at oprette en Intune-sikkerhedsopgave, når du opretter en afhjælpningsanmodning. Denne indstilling vises ikke, hvis der ikke er angivet en forbindelse.

Se [Brug Intune til at afhjælpe sårbarheder, der er identificeret af Microsoft Defender til Slutpunkt, hvis du](/intune/atp-manage-vulnerabilities) vil have mere at vide.

### <a name="remediation-request-steps"></a>Trin til afhjælpningsanmodning

1. Gå til navigationsmenuen **til administration af trusler** og sikkerhedsrisiko i Microsoft 365 Defender, og vælg Anbefalinger **anbefalinger om** [**sikkerhed**](tvm-security-recommendation.md).

2. Vælg en sikkerhedsanbefaling, du vil anmode om afhjælpning for, og vælg derefter **Afhjælpningsindstillinger**.

3. Udfyld formularen, herunder det, du anmoder om afhjælpning af, relevante enhedsgrupper, prioritet, forfaldsdato og valgfrie noter.
    1. Hvis du vælger afhjælpningsindstillingen "Handling påkrævet", vil det ikke være muligt at vælge en forfaldsdato, da der ikke er nogen specifik handling.

4. Vælg **Send anmodning**. Når du indsender en afhjælpningsanmodning, oprettes et afhjælpningsaktivitetselement i Håndtering af trusler og sikkerhedsrisici, som kan bruges til at overvåge afhjælpnings status for denne anbefaling. Dette vil ikke udløse en afhjælpning eller anvende ændringer på enheder.

5. Giv din it-administrator besked om den nye anmodning, og få vedkommende til at logge på Intune for at godkende eller afvise anmodningen og starte en pakkeinstallation.

6. Gå til siden [**Afhjælpning for**](tvm-remediation.md) at få vist status for din afhjælpningsanmodning.

Hvis du vil se, hvordan billeten vises i Intune, skal du se Brug Intune til at afhjælpe sårbarheder, der er identificeret af [Microsoft Defender til Slutpunkt](/intune/atp-manage-vulnerabilities) , hvis du vil have mere at vide.

> [!NOTE]
> Hvis din anmodning indebærer afhjælpning af mere end 10.000 enheder, kan vi kun sende 10.000 enheder til afhjælpning til Intune.

Når din organisations cybersikkerhedseksperter identificeres og knyttes til konkrete [sikkerhedsanbefalinger](tvm-security-recommendation.md), kan du begynde at oprette sikkerhedsopgaver. Du kan oprette opgaver gennem integrationen med Microsoft Intune hvor afhjælpningsbilletter oprettes.

Sænk din organisations eksponering for sårbarheder, og øg din sikkerhedskonfiguration ved at rette sikkerhedsanbefalinger.

## <a name="view-your-remediation-activities"></a>Få vist dine afhjælpningsaktiviteter

Når du sender en anmodning om afhjælpning fra siden med sikkerhedsanbefalinger, startes en afhjælpningsaktivitet. Der oprettes en sikkerhedsopgave, som kan registreres på siden Håndtering af trusler og sikkerhedsrisici **afhjælpning**, og der oprettes en afhjælpningsbillet Microsoft Intune.

Hvis du vælger afhjælpningsindstillingen "Handling påkrævet", vil der ikke være nogen statuslinje, status for billet eller forfaldsdato, da der ikke er nogen handling, vi kan overvåge.

Når du er på siden Afhjælpning, skal du vælge den afhjælpningsaktivitet, du vil have vist. Du kan følge afhjælpningstrinnene, spore status, få vist den relaterede anbefaling, eksportere til CSV eller markere den som fuldført.

:::image type="content" source="../../media/remediation-flyouteolswnew.png" lightbox="../../media/remediation-flyouteolswnew.png" alt-text="Eksempel på siden Afhjælpning med en valgt afhjælpningsaktivitet, og den pågældende aktivitets pop op med beskrivelsen, it-tjenesten og administrationsværktøjer samt afhjælpning af enheder":::

> [!NOTE]
> Der er en 180-dages opbevaringsperiode for fuldført afhjælpningsaktiviteter. For at få siden Afhjælpning til at fungere optimalt fjernes afhjælpningsaktiviteten 6 måneder efter fuldførelsen.

### <a name="completed-by-column"></a>Fuldført efter kolonne

Hold styr på, hvem der lukkede afhjælpningsaktiviteten med kolonnen "Fuldført af" på siden Afhjælpning.

- **Mailadresse:** Mailen for den person, der har fuldført opgaven manuelt
- **Systembekræftelse**: Opgaven blev automatisk fuldført (alle enheder er blevet løst)
- **I/T**: Oplysningerne er ikke tilgængelige, fordi vi ikke ved, hvordan denne ældre opgave blev fuldført

:::image type="content" alt-text="Oprettes af og udfyldes af kolonner med to rækker. Én række for fuldført af har eksempel på en mail, og den anden række siger systembekræftelse." source="images/tvm-completed-by.png":::

### <a name="top-remediation-activities-in-the-dashboard"></a>Vigtigste afhjælpningsaktiviteter i dashboardet

Få **vist de vigtigste afhjælpningsaktiviteter** i [dashboardet for **trussels- og sikkerhedsrisikoadministration**](tvm-dashboard-insights.md). Vælg en af posterne for at gå til **siden** Afhjælpning. Du kan markere afhjælpningsaktiviteten som fuldført, når it-administratorteamet har løst opgaven.

![Eksempel på kortet Til øverste afhjælpningsaktiviteter med en tabel, der viser de vigtigste aktiviteter, der blev genereret fra sikkerhedsanbefalinger.](images/tvm-remediation-activities-card.png)

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)