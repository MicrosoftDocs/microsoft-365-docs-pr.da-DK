---
title: Undtagelser til serviceplanen
description: Sådan anmoder du om undtagelser til standardserviceplanen
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 8069a899b9992a0e8b941b6ac53cd2f230a6174a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63587947"
---
# <a name="exceptions-to-the-service-plan"></a>Undtagelser til serviceplanen

Microsoft Managed Desktop indeholder en liste over enheder, [standardindstillinger](device-policies.md) for enheder, programkrav og visse konfigurerbare indstillinger – alt sammen designet til at give en sikker, produktiv og behagelig oplevelse for brugerne.[](../working-with-managed-desktop/config-setting-overview.md)

Det er bedst altid at bevare tjenesten, som den leveres. Vi er dog klar over, at nogle detaljer i tjenesten muligvis ikke helt passer til organisationens behov. Hvis du føler, at du har brug for at ændre tjenesten på en eller anden måde, er det vigtigt, at du følger følgende processer for at anmode om disse ændringer.

## <a name="types-of-exceptions"></a>Typer af undtagelser

En undtagelse er enhver tilføjelse eller ændring af Microsoft Managed Desktop Base-konfigurationen. Eksempler kan være alt fra konfiguration af USB-porte til implementering af en ny enhedsdriver. Vi grupperer forskellige undtagelser på følgende måde:

| Undtagelsestyper | Beskrivelse |
| ----- | ----- |
| Produktivitetssoftware | Forgrundssoftware, som brugere skal bruge, begrænset af [programkravene](mmd-app-requirements.md). |
| Sikkerhedsagenter & VPN | Software, der bruges til at sikre, overvåge eller ændre enhedens eller netværkets funktionsmåde. |
| Overvågning af digital oplevelse | Software, der bruges til at spore data på en brugers enhed til at rapportere til IT. |
| Hardware- eller softwaredrivere | Enhedsdrivere, der er begrænset af [programkravene](mmd-app-requirements.md). |
| Politikker | Windows 10 eller Microsoft 365 Apps for enterprise på en administreret enhed. |
| Enheder | Enheder, der ikke er på listen over [Microsoft-administrerede enheder på computeren](device-list.md). |
| Andet | Alt, der ikke er dækket af de andre områder. |

## <a name="request-an-exception"></a>Anmod om en undtagelse

Send anmodninger via portalen Microsoft Managed Desktop Admin ved at oprette en ændringsanmodning. Sørg for at medtage disse oplysninger:

| Oplysninger om ændring af anmodning | Beskrivelse |
| ----- | ----- |
| Undtagelsestype | Hvilken type undtagelse er det? (se den [forrige tabel](#types-of-exceptions)) |
| Krav | Hvad er det specifikke forretningskrav for undtagelsen? |
| Forslag | Hvilken løsning anmoder din virksomhed om? |
| Tidslinje | Hvor lang tid vil du have denne undtagelse til at vare? |

## <a name="how-we-assess-an-exception-request"></a>Hvordan vi vurderer en anmodning om undtagelse

Når vi gennemser anmodninger om undtagelser, vurderer vi disse faktorer i denne rækkefølge:

1. Nogle programmer og politikker, som Microsoft Managed Desktop installerer på alle enheder, kan ikke negotiable. Din anmodning må ikke påvirke disse programmer og politikker. Du kan finde flere oplysninger under [Enhedskonfiguration](device-policies.md).
2. Begrænset produktivitetssoftware, der kræves af en bruger for at udføre deres arbejde, vil sandsynligvis blive godkendt.
3. Hvis vi kan opfylde dit krav ved hjælp af Microsoft-teknologi, vil vi sandsynligvis godkende din anmodning om en undtagelsesperiode på tre til 12 måneder. Overførselsperioden afhænger af projektets omfang.
4. Hvis vi ikke opfylder dit krav ved hjælp af Microsoft-teknologi, vil vi sandsynligvis godkende din anmodning, medmindre den overtræder en af [de vigtigste betingelser](#key-conditions).  

Disse principper sikrer, at Microsoft Managed Desktop altid kan opfylde dine behov, mens du registrerer afvigelser fra vores standardskabelon.

## <a name="key-conditions"></a>Vigtige betingelser

Vi gennemser undtagelser for at sikre, at de ikke overtræder nogen af disse betingelser:

- En undtagelse må ikke påvirke systemets sikkerhed negativt.
- Vedligeholdelse af undtagelsen må ikke medføre betydelige omkostninger for hverken Microsoft Managed Desktop-handlinger eller support.
- En undtagelse må ikke påvirke systemets stabilitet, f.eks. ved at medføre, at kernetilstanden går ned eller hænger.
- Ændringen må ikke begrænse os i at køre tjenesten eller i konflikt med centrale Microsoft Managed Desktop-teknologier.
- Undtagelsen kan ikke omfatte tilpasning af brugeroplevelsen, f.eks. ændring af menuen Start eller proceslinjen.

Disse betingelser kan blive ændret i fremtiden. Hvis vi foretager sådanne ændringer, giver vi dig 30 dages varsel, før disse betingelser træder i kraft.  Hvis Microsoft Managed Desktop leverer en alternativ måde at opfylde en godkendt undtagelse, giver Microsoft Managed Desktop kunden besked, hvis Microsoft Managed Desktop ændrer den måde, den understøtter undtagelsen på.

## <a name="revoking-approval-for-an-exception"></a>Tilbagekalde godkendelse af en undtagelse

Når en ønsket undtagelse er blevet godkendt og installeret, er det muligt, at vi kan opdage problemer, der overtræder de vigtigste betingelser, som ikke blev fremgår tydeligt, da vi godkendte ændringen i første omgang. I denne situation kan det være, at vi er nødt til at tilbagekalde godkendelsen af undtagelsen.

Hvis vi er nødt til at tilbagekalde godkendelsen for undtagelsen, giver vi dig besked ved hjælp af administrationsportalen til Microsoft Managed Desktop. Fra den første gang vi giver dig besked, har du 90 dage til at fjerne undtagelsen, før enhederne med undtagelse ikke længere er bundet af Microsoft Managed Desktop-serviceaftaler.

Vi sender dig flere meddelelser i henhold til en streng tidslinje. En alvorlig hændelse eller trussel kan dog kræve, at vi ændrer tidslinjen for vores beslutninger om en undtagelse. Vi fjerner ikke *en undtagelse* uden dit samtykke. Enheder med tilbagekaldte undtagelser vil dog ikke længere være bundet af vores serviceaftale. Følgende tabel er tidslinjen for de meddelelser, vi sender dig:

| Meddelelsestype | Beskrivelse |
| ----- | ----- |
| Første meddelelse | Vi giver dig følgende oplysninger i den første meddelelse: <ul><li>Oplysninger om, hvorfor vi tilbagekalder den.</li><li>De handlinger, vi anbefaler, at du gør.</li><li>Deadline for disse handlinger.</li><Li>Trin, du skal følge, hvis du vil gøre beslutningen mere indbydende.</li></ul> <br>Denne meddelelse vises 90 dage forud, før undtagelsen skal fjernes fra alle enheder. |
| Anden meddelelse (30 dage senere) | Vi giver endnu en meddelelse, herunder de samme oplysninger, som blev angivet i den første meddelelse. |
| Tredje varsel (60 dage efter den første meddelelse) | Vi giver en tredje meddelelse, herunder de samme oplysninger i den første meddelelse. |
| Sidste meddelelse (en uge før deadline på 90 dage) | Vi giver en fjerde meddelelse, herunder de samme oplysninger i den første meddelelse. |
| 90 dage efter første varsel| Microsoft Managed Desktop-serviceaftaler gælder ikke længere for enheder, der har den tilbagekaldte undtagelse. Du kan til enhver tid stille spørgsmål ved beslutningen og give yderligere oplysninger til overvejelse, herunder opgradering, konfigurationsændringer eller ændring af software. |
