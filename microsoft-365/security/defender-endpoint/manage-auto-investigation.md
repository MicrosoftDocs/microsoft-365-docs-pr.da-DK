---
title: Gennemse afhjælpningshandlinger efter automatiserede undersøgelser
description: Gennemse og godkend (eller afvis) afhjælpningshandlinger efter en automatisk undersøgelse.
keywords: autoir, automatiseret, undersøgelse, registrering, afhjælpning, handling, afventende, godkendt
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
ms.date: 01/29/2021
ms.technology: mde
ms.openlocfilehash: 952e5a057f893cfc11b928e40e2038255a93601c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591203"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Gennemse afhjælpningshandlinger efter en automatisk undersøgelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Når en [automatiseret undersøgelse](automated-investigations.md) køres, genereres der en vurdering for hvert stykke bevis, der undersøges. Det kan være *ondsindede*, *mistænkelige* eller *ingen trusler, der kan findes*.

Afhængigt af

- typen af trussel,
- den resulterende konklusion, og
- hvordan din organisations [enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups) konfigureres,

afhjælpningshandlinger kan forekomme automatisk eller kun efter godkendelse fra organisationens sikkerhedsteam.

Her er et par eksempler:

- **Eksempel 1**: Fabrikams enhedsgrupper er indstillet til **Fuld – afhjulpet trusler automatisk** (den anbefalede indstilling). I dette tilfælde udføres afhjælpningshandlinger automatisk for artefakter, der anses for skadelige efter en automatisk undersøgelse (se Gennemse [fuldførte handlinger](#review-completed-actions)).

- **Eksempel 2**: Contosos enheder er inkluderet i en gruppe af enheder, der er indstillet til **Semi – kræver godkendelse til enhver afhjælpning**. I dette tilfælde skal Contosos sikkerhedsteam gennemse og godkende alle afhjælpningshandlinger efter en automatisk undersøgelse (se Gennemse [afventende handlinger](#review-pending-actions)).

- **Eksempel 3**: Tailspin Toys har deres enhedsgrupper indstillet **til Intet automatiseret svar** (anbefales ikke). I dette tilfælde forekommer automatiserede undersøgelser ikke. Der bliver ikke taget eller afventer nogen afhjælpningshandlinger, og der logføres ingen handlinger i Handlingscenter [for deres](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) enheder (se [Administrer enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

Uanset om det tages automatisk eller ved godkendelse, kan en automatisk undersøgelse resultere i en eller flere af afhjælpningshandlingerne:

- Sætte en fil i karantæne
- Fjern en registreringsdatabasenøgle
- Dræb en proces
- Stop en tjeneste
- Deaktiver en driver
- Fjerne en planlagt opgave

## <a name="review-pending-actions"></a>Gennemse afventende handlinger

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på.
2. Vælg Handlingscenter i **navigationsruden**.
3. Gennemse elementerne under **fanen Afventer** .
4. Vælg en handling for at åbne pop op-ruden.
5. Gennemse oplysningerne i pop op-ruden, og gør derefter et af følgende:
   - Vælg **siden Åbn undersøgelse for** at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en afventende handling.
   - Vælg **Afvis** for at forhindre, at der tages en afventende handling.
   - Vælg **Gå på jagt** for at gå til [Avanceret jagt](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Gennemse fuldførte handlinger

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på.
2. Vælg Handlingscenter i **navigationsruden**.
3. Gennemse elementerne under **fanen** Oversigt.
4. Vælg et element for at få vist flere oplysninger om afhjælpningshandlingen.

## <a name="undo-completed-actions"></a>Fortryde fuldførte handlinger

Hvis du har besluttet, at en enhed eller en fil ikke er en trussel, kan du fortryde afhjælpningshandlinger, der blev foretaget, uanset om disse handlinger blev foretaget automatisk eller manuelt. I handlingscenter under fanen **Oversigt** kan du fortryde en af følgende handlinger:

<br>

****

|Handlingskilde|Understøttede handlinger|
|---|---|
|<ul><li>Automatiseret undersøgelse</li><li>Microsoft Defender Antivirus</li><li>Manuelle svarhandlinger</li></ul>|<ul><li>Isoler enhed</li><li>Begræns udførelse af kode</li><li>Sætte en fil i karantæne</li><li>Fjern en registreringsdatabasenøgle</li><li>Stop en tjeneste</li><li>Deaktiver en driver</li><li>Fjerne en planlagt opgave</li></ul>|
|

### <a name="to-undo-multiple-actions-at-one-time"></a>For at fortryde flere handlinger på én gang

1. Gå til handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.
2. Vælg **de handlinger** , du vil fortryde, under fanen Oversigt. Sørg for at markere elementer, der har samme handlingstype. Der åbnes en pop op-rude.
3. Vælg Fortryd i pop **op-ruden**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Sådan fjernes en fil fra karantæne på tværs af flere enheder

1. Gå til handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.
2. På fanen **Oversigt skal** du vælge et element, der har filen Handlingstype **Karantæne**.
3. I pop op-ruden skal du **vælge Anvend på X flere forekomster af denne fil** og derefter vælge **Fortryd**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Automatiseringsniveauer, resultater af automatiseret undersøgelse og resulterende handlinger

Automatiseringsniveauer påvirker, om visse afhjælpningshandlinger skal løses automatisk eller kun efter godkendelse. Nogle gange har dit sikkerhedsteam flere trin at udføre, afhængigt af resultaterne af en automatisk undersøgelse. Følgende tabel opsummerer automatiseringsniveauer, resultater af automatiserede undersøgelser, og hvad du skal gøre i hvert enkelt tilfælde.

<br>

****

|Indstilling for gruppe af enheder|Resultater af automatiseret undersøgelse|Hvad kan du gøre?|
|---|---|---|
|**Fuld – afhjælpe trusler automatisk** (den anbefalede indstilling)|En konklusion af *Ondsindet* er nået for et stykke bevis. <p> Relevante afhjælpningshandlinger løses automatisk.|[Gennemse fuldførte handlinger](#review-completed-actions)|
|**Fuld – afhjulpet trusler automatisk**|En vurdering af *Mistænkelig* er nået for et stykke bevis. <p> Afhjælpningshandlinger afventer godkendelse for at fortsætte.|[Godkend (eller afvis) afventende handlinger](#review-pending-actions)|
|**Semi – kræver godkendelse for enhver afhjælpning**|En vurdering af enten *Ondsindet* *eller Mistænkelig* er nået for et stykke bevis. <p> Afhjælpningshandlinger afventer godkendelse for at fortsætte.|[Godkend (eller afvis) afventende handlinger](#review-pending-actions)|
|**Semi – kræver godkendelse til afhjælpning af centrale mapper**|En konklusion af *Ondsindet* er nået for et stykke bevis. <p> Hvis artefaktet er en fil eller eksekverbar og er i et operativsystembibliotek, f.eks. mappen Windows eller mappen Programfiler, afventer afhjælpningshandlingerne godkendelse. <p> Hvis *artefakterne ikke* er i et operativsystembibliotek, løses afhjælpningshandlinger automatisk.|<ol><li>[Godkend (eller afvis) afventende handlinger](#review-pending-actions)</li><li>[Gennemse fuldførte handlinger](#review-completed-actions)</li></ol>|
|**Semi – kræver godkendelse til afhjælpning af centrale mapper**|En vurdering af *Mistænkelig* er nået for et stykke bevis. <p> Afhjælpningshandlinger afventer godkendelse.|[Godkend (eller afvis) afventende handlinger](#review-pending-actions).|
|**Semi – kræver godkendelse til ikke-midlertidige mapper afhjælpning**|En konklusion af *Ondsindet* er nået for et stykke bevis. <p> Hvis artefakterne er en fil eller eksekverbar fil, der ikke er i en midlertidig mappe, f.eks. brugerens downloadmappe eller midlertidige mappe, afventer afhjælpningshandlinger godkendelse. <p> Hvis artefaktet er en fil eller eksekverbar fil, der findes i en midlertidig mappe, udføres afhjælpningshandlinger automatisk.|<ol><li>[Godkend (eller afvis) afventende handlinger](#review-pending-actions)</li><li>[Gennemse fuldførte handlinger](#review-completed-actions)</li></ol>|
|**Semi – kræver godkendelse til ikke-midlertidige mapper afhjælpning**|En vurdering af *Mistænkelig* er nået for et stykke bevis. <p> Afhjælpningshandlinger afventer godkendelse.|[Godkend (eller afvis) afventende handlinger](#review-pending-actions)|
|Et hvilket som helst **af fuld-** eller **halv automatiseringsniveauerne**|En konklusion af *Ingen trusler er* nået for et stykke bevis. <p> Der er ikke foretaget nogen afhjælpningshandlinger, og der afventer ingen handlinger.|[Få vist detaljer og resultater af automatiserede undersøgelser](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Intet automatiseret svar** (anbefales ikke)|Der kører ingen automatiserede undersøgelser, så der opnås ingen konklusion, og der bliver ikke taget nogen afhjælpningshandlinger, eller der afventer godkendelse.|[Overvej at konfigurere eller ændre dine enhedsgrupper for at bruge **fuld eller** **halv automatisering**](/microsoft-365/security/defender-endpoint/machine-groups)|
|

I Microsoft Defender til slutpunkt registreres alle slutninger i [Handlingscenter](auto-investigation-action-center.md#new-a-unified-action-center).

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om live svarfunktioner](live-response.md)
- [Proaktivt lede efter trusler med avanceret jagt](advanced-hunting-overview.md)
- [Adressere falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Se også

- [Oversigt over automatiserede undersøgelser](automated-investigations.md)
