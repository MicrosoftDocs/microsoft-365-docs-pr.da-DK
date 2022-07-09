---
title: Gennemse afhjælpningshandlinger efter automatiserede undersøgelser
description: Gennemse og godkend (eller afvis) afhjælpningshandlinger efter en automatisk undersøgelse.
keywords: autoir, automatiseret, undersøgelse, registrering, afhjælpning, handling, ventende, godkendt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.technology: mde
ms.openlocfilehash: 122b216a07bdd70ab5619903ba049b4fb507179e
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695610"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Gennemse afhjælpningshandlinger efter en automatiseret undersøgelse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Når der kører en [automatisk undersøgelse](automated-investigations.md) , genereres der en dom for hvert bevis, der undersøges. Dommene kan være *Ondsindede*, *Mistænkelige* eller *Ingen trusler fundet*.

Afhængigt af

- den type trussel,
- den resulterende dom, og
- hvordan organisationens [enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups) er konfigureret,

afhjælpningshandlinger kan forekomme automatisk eller kun efter godkendelse af organisationens sikkerhedsteam.

Her er nogle få eksempler:

- **Eksempel 1**: Fabrikams enhedsgrupper er angivet til **Fuld – afhjælper trusler automatisk** (den anbefalede indstilling). I dette tilfælde udføres afhjælpningshandlinger automatisk for artefakter, der anses for at være skadelige efter en automatiseret undersøgelse (se [Gennemse fuldførte handlinger](#review-completed-actions)).

- **Eksempel 2**: Contosos enheder er inkluderet i en enhedsgruppe, der er indstillet til **Semi – kræver godkendelse for enhver afhjælpning**. I dette tilfælde skal Contosos team for sikkerhedshandlinger gennemse og godkende alle afhjælpningshandlinger efter en automatisk undersøgelse (se [Gennemse ventende handlinger](#review-pending-actions)).

- **Eksempel 3**: Tailspin Toys har angivet deres enhedsgrupper til **Intet automatiseret svar** (anbefales ikke). I dette tilfælde sker der ikke automatiserede undersøgelser. Der udføres eller afventer ingen afhjælpningshandlinger, og der logføres ingen handlinger i [Løsningscenter](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) for deres enheder (se [Administrer enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

Uanset om det udføres automatisk eller efter godkendelse, kan en automatiseret undersøgelse resultere i en eller flere af afhjælpningshandlingerne:

- Sæt en fil i karantæne
- Fjern en registreringsdatabasenøgle
- Dræb en proces
- Stop en tjeneste
- Deaktiver en driver
- Fjern en planlagt opgave

## <a name="review-pending-actions"></a>Gennemse ventende handlinger

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Gennemse elementerne under fanen **Ventende** .

4. Vælg en handling for at åbne dens pop op-rude.

5. Gennemse oplysningerne i pop op-ruden, og udfør derefter et af følgende trin:

   - Vælg **siden Åbn undersøgelse** for at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en ventende handling.
   - Vælg **Afvis** for at forhindre, at der udføres en ventende handling.
   - Vælg **Gå på jagt** for at gå ind i [Avanceret jagt](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Gennemse fuldførte handlinger

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Gennemse elementerne under fanen **Oversigt** .

4. Vælg et element for at få vist flere oplysninger om afhjælpningshandlingen.

## <a name="undo-completed-actions"></a>Fortryd fuldførte handlinger

Hvis du har fastslået, at en enhed eller en fil ikke er en trussel, kan du fortryde afhjælpningshandlinger, der er foretaget, uanset om disse handlinger blev udført automatisk eller manuelt. I Handlingscenter under fanen **Oversigt** kan du fortryde en af følgende handlinger:

|Handlingskilde|Understøttede handlinger|
|---|---|
|<ul><li>Automatiseret undersøgelse</li><li>Manuelle svarhandlinger (se nedenstående note)</li><li>Microsoft Defender Antivirus</li></ul>|<ul><li>Deaktiver en driver</li><li>Isoler enhed</li><li>Sæt en fil i karantæne</li><li>Fjern en registreringsdatabasenøgle</li><li>Fjern en planlagt opgave</li><li>Begræns kørsel af kode</li><li>Stop en tjeneste</li></ul>|

> [!NOTE]
> [Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) og [Microsoft Defender til virksomheder](../defender-business/mdb-overview.md) kun indeholde følgende manuelle svarhandlinger:
>
> - Kør antivirusscanning
> - Isoler enhed
> - Stop og sæt en fil i karantæne
> - Tilføj en indikator for at blokere eller tillade en fil
>
> Du kan få mere at vide under [Sammenlign Microsoft Defender for Endpoint-planer](defender-endpoint-plan-1-2.md) og [Sammenlign sikkerhedsfunktioner i Microsoft 365-planer til små og mellemstore virksomheder](../defender-business/compare-mdb-m365-plans.md).

### <a name="to-undo-multiple-actions-at-one-time"></a>Sådan fortryder du flere handlinger på én gang

1. Gå til Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. Vælg de handlinger, du vil fortryde, under fanen **Oversigt** . Sørg for at vælge elementer, der har samme handlingstype. Der åbnes en pop op-rude.

3. Vælg **Fortryd** i pop op-ruden.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Sådan fjernes en fil fra karantæne på tværs af flere enheder

1. Gå til Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. Under fanen **Historik** skal du vælge et element med handlingstypen **Karantænefil**.

3. I pop op-vinduet skal du vælge **Anvend på X flere forekomster af denne fil** og derefter vælge **Fortryd**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Automatiseringsniveauer, automatiserede undersøgelsesresultater og resulterende handlinger

Automatiseringsniveauer påvirker, om visse afhjælpningshandlinger udføres automatisk eller kun efter godkendelse. Nogle gange har dit team af sikkerhedshandlinger flere trin at tage, afhængigt af resultaterne af en automatiseret undersøgelse. I følgende tabel opsummeres automatiseringsniveauer, resultater af automatiserede undersøgelser, og hvad der skal gøres i hvert enkelt tilfælde.

|Indstilling for enhedsgruppe|Automatiserede undersøgelsesresultater|Sådan gør du|
|---|---|---|
|**Fuld – afhjælp trusler automatisk**<br/>(anbefales)|En dom af *Ondsindet* er nået for et stykke af beviser. <p> Der udføres automatisk relevante afhjælpningshandlinger.|[Gennemse fuldførte handlinger](#review-completed-actions)|
|**Fuld – afhjælp trusler automatisk**|En mistænkelig *dom er nået* for et bevis. <p> Der udføres automatisk relevante afhjælpningshandlinger.|[Godkend (eller afvis) ventende handlinger](#review-pending-actions)|
|**Semi – kræver godkendelse til enhver afhjælpning**|En dom af enten *Ondsindet* eller *Mistænkelig* er nået for et stykke af beviser. <p> Afhjælpningshandlinger afventer godkendelse for at fortsætte.|[Godkend (eller afvis) ventende handlinger](#review-pending-actions)|
|**Semi – kræver godkendelse til afhjælpning af kernemapper**|En dom af *Ondsindet* er nået for et stykke af beviser. <p> Hvis artefaktet er en fil eller eksekverbar og er i en operativsystemmappe, f.eks. Windows-mappen eller mappen Programfiler, afventer afhjælpningshandlinger godkendelse. <p> Hvis artefaktet *ikke* findes i en operativsystemmappe, udføres afhjælpningshandlinger automatisk.|<ol><li>[Godkend (eller afvis) ventende handlinger](#review-pending-actions)</li><li>[Gennemse fuldførte handlinger](#review-completed-actions)</li></ol>|
|**Semi – kræver godkendelse til afhjælpning af kernemapper**|En mistænkelig *dom er nået* for et bevis. <p> Afhjælpningshandlinger afventer godkendelse.|[Godkend (eller afvis) ventende handlinger](#review-pending-actions).|
|**Semi – kræver godkendelse til afhjælpning af mapper, der ikke er midlertidige**|En dom af *Ondsindet* er nået for et stykke af beviser. <p> Hvis artefaktet er en fil eller eksekverbar, der ikke findes i en midlertidig mappe, f.eks. brugerens mappe til downloads eller temp, afventer afhjælpningshandlinger godkendelse. <p> Hvis artefaktet er en fil eller eksekverbar fil, der *er* i en midlertidig mappe, udføres afhjælpningshandlinger automatisk.|<ol><li>[Godkend (eller afvis) ventende handlinger](#review-pending-actions)</li><li>[Gennemse fuldførte handlinger](#review-completed-actions)</li></ol>|
|**Semi – kræver godkendelse til afhjælpning af mapper, der ikke er midlertidige**|En mistænkelig *dom er nået* for et bevis. <p> Afhjælpningshandlinger afventer godkendelse.|[Godkend (eller afvis) ventende handlinger](#review-pending-actions)|
|Et hvilket som helst af niveauerne **Fuld** eller **Halvautomatisering**|En dom af *Ingen trusler fundet* er nået for et stykke af beviser. <p> Der udføres ingen afhjælpningshandlinger, og ingen handlinger afventer godkendelse.|[Få vist detaljer om og resultater af automatiserede undersøgelser](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Intet automatiseret svar** (anbefales ikke)|Der køres ingen automatiserede undersøgelser, så der opnås ingen domme, og der udføres ingen afhjælpningshandlinger eller afventer godkendelse.|[Overvej at konfigurere eller ændre dine enhedsgrupper, så de bruger **fuld** eller **semiautomatisering**](/microsoft-365/security/defender-endpoint/machine-groups)|

Alle domme spores i [Action Center](auto-investigation-action-center.md#the-unified-action-center).

> [!NOTE]
> I [Defender for Business](../defender-business/mdb-overview.md) er automatiserede undersøgelses- og afhjælpningsfunktioner forudindstillet til at bruge **Fuld – afhjælp automatisk trusler**. Disse egenskaber anvendes som standard på alle enheder.

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om funktioner til live-svar](live-response.md)
- [Proaktiv jagt efter trusler med avanceret jagt](advanced-hunting-overview.md)
- [Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Se også

- [Oversigt over automatiserede undersøgelser](automated-investigations.md)
