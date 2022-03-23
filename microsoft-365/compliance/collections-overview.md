---
title: Oversigt over samlinger i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Brug samlinger i Advanced eDiscovery til at søge efter og indsamle indhold, der er i forhold til din sag eller undersøgelse.
ms.openlocfilehash: 8ccefb69463a2c518b0e0882a94bba81139e97eb
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63593412"
---
# <a name="learn-about-collections-in-advanced-ediscovery"></a>Få mere at vide om samlinger i Advanced eDiscovery

Når organisationer står over for at skulle indsamle den kommunikation og det indhold, der kan være relevant for en undersøgelse eller en mulig procesførelse, står de over for en betydelig udfordring under de bedste omstændigheder. På den moderne arbejdsplads muliggør indholdets volumen, variation og hastighed innovation og fjernarbejde, og samtidig udvides kravene og processen til administration af samlinger til eDiscovery-undersøgelser.

Arbejdsprocessen for indsamling udgør betydelige tekniske udfordringer i forbindelse med at udtrække indhold fra oprindelige placeringer og kilder. Det er også et vigtigt punkt i vurdering og strategi for almindelige procesførelses- eller undersøgelsesscenarier. Når organisationer begynder at vurdere en undersøgelse, er de første spørgsmål, der blev stillet, hvem der var involveret? Når du har identificeret, hvem der var involveret, kan disse  fremfor alt hurtigt sættes i venteposition for at bevare relevant indhold. Det næste spørgsmål er, hvad der fandt sted? For at besvare dette andet grundlæggende spørgsmål om enhver undersøgelse skal lederne vende sig til dataene. For hurtigt at vurdere det mest relevante indhold til spørgsmålet om, hvad der fandt sted, begynder lederne at indskrænke spørgsmålets mål for at sikre, at indsamlingsresultaterne er omfattende uden at være for brede.

Samlinger i en Advanced eDiscovery hjælpe eDiscovery-ledere med hurtigt at søge efter indhold på tværs af mail, dokumenter og andet indhold Microsoft 365. Samlinger giver ledere et estimat af det indhold, der kan være relevant for sagen. Dette giver ledere mulighed for at foretage hurtige og velovervejede beslutninger om størrelsen og omfanget af indhold, der er relevant for en sag. eDiscovery-ledere kan oprette en samling for at søge efter postkassedatakilder (f.eks. postkasser og SharePoint-websteder) og ved at bruge bestemte søgekriterier (f.eks. nøgleord og datoområder) til hurtigt at definere omfanget af deres indsamling.

Når samlingen er defineret, kan eDiscovery-ledere gemme samlingen som en kladde og få estimater, herunder overslag for mængden af data, de indholdsplaceringer, der indeholder resultater, og antallet af hits for søgeforespørgselsbetingelse. Denne indsigt kan være med til at informere om, om samlingen skal revideres for at indsnævre eller udvide samlingens omfang, før du går videre til gennemsyns- og analysefaserne i eDiscovery-arbejdsprocessen.

Når lederen er tilfreds med samlingens omfang og den anslåede mængde indhold, der sandsynligvis svarer, kan chefen tilføje eller bekræfte indholdet i et gennemsynssæt. Når du binder en samling til et korrektursæt, har den pågældende leder også mulighed for at inkludere chatsamtaler, vedhæftede skybaserede filer og dokumentversioner. Indholdet i samlingen går også igennem et andet niveau af behandling under ingestion i korrektursættet. , og samlingen opdateres med den endelige samlingsoversigt. Når indhold er føjet til korrektursættet, kan eDiscovery-ledere fortsætte med at forespørge, gruppere og indskrænke indholdet for at hjælpe med minimering og gennemgang. Desuden opdateres samlingen med oplysninger og statistikker om det indhold, der er forpligtet til at gennemgå sættet. Dette giver en historisk reference om indholdet i samlingen.

Med udgivelsen af samlinger i en Advanced eDiscovery er fanen Søgninger blevet omdøbt til Samlinger i en Advanced eDiscovery sag  Microsoft 365 Overholdelsescenter. Trinnene til at definere samlingens omfang og størrelse følger den samme fremgangsmåde som søgning for at definere placeringer og betingelser. Gem som kladde, og få anslåede eksempelvisninger muliggør hurtig validering af det målrettede omfang af samlinger, før du gemmer en fuld søgning og en samling i gennemsynssættet. Det giver forbedret jobstyring og målrettede gentagelser for at minimere indhold under søge- og indsamlingsprocessen.

## <a name="collections-workflow"></a>Arbejdsprocessen Samlinger

Her er en grundlæggende arbejdsproces og beskrivelser Advanced eDiscovery hvert trin i processen for at komme i gang med at bruge samlinger i Advanced eDiscovery.

![Arbejdsprocessen for samlinger i Advanced eDiscovery.](../media/CollectionsWorkflow.png)

1. **Opret og kør en kladdesamling**. Det første trin er at oprette en kladde til indsamling og definere de datakilder, der ikke er registrerede og ikke-registrerede, til at søge. Du kan også søge efter andre datakilder, der ikke er blevet føjet til sagen. Når du har tilføjet datakilderne, skal du konfigurere søgeforespørgslen til at søge efter indhold, der er relevant for sagen, i datakilderne. Du kan nøgleord, egenskaber og betingelser for at opbygge søgeforespørgsler, der returnerer indhold, der sandsynligvis er mest relevant for sagen. Få mere at vide under [Opret en kladdesamling](create-draft-collection.md).

2. **Gennemgå skøn og statistik**. Når du har oprettet en kladdesamling og kørt den, er næste trin at få vist samlingsstatistik, som kan hjælpe dig med at bekræfte, om relevant indhold findes, og om der er flest hits på indholdsplaceringerne. Du kan også få vist et eksempel på en stikprøve af søgeresultaterne for yderligere at hjælpe dig med at afgøre, om indholdet er inden for omfanget af din undersøgelse. Få mere at vide under [Statistik og rapporter for kladdesamlinger](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).

3. **Revy og kør en kladdesamling igen**. Baseret på estimater og statistikker, der returneres af samlingen, kan du redigere kladdesamlingen ved at ændre de datakilder, der søges efter, og søgeforespørgslen for at udvide eller indsnævre samlingen. Du kan opdatere og køre kladdesamlingen igen, indtil du er sikker på, at samlingen indeholder det indhold, der er mest relevant for din sag.

4. **Bestil en kladdesamling til et korrektursæt**. Når du er tilfreds med, at samlingen returnerer den typeindhold, der er relevant for sagen, kan du bekræfte samlingen i korrektursættet. Når du har bekræftet en samling, har du mulighed for at føje samtaletråde, vedhæftede skybaserede filer og dokumentversioner til korrektursættet, som alle kan være relevante for sagen.

   Når du har bekræftet en samling, udtrækkes underordnede elementer som f.eks. mailsignaturer og billeder fra et overordnet element (f.eks. en mail, chatmeddelelse eller et dokument) og behandles derefter af Optical Character Recognition (OCR) for at udtrække tekst fra det underordnede element. Tekst, der udtrækkes fra underordnede elementer, føjes derefter til det overordnede element, så du kan se det i korrektursættet. Hvis du ikke føjer underordnede elementer til korrektursættet som en separat fil, hjælper Advanced eDiscovery med at begrænse antallet af elementer, der potentielt efterlignes i korrektursættet. Du kan finde flere oplysninger om, hvordan underordnede elementer håndteres, [under Indsamling af statistik og rapporter](collection-statistics-reports.md#collection-contents).

   Du kan få mere at vide [under Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md).

5. **Gennemgå oversigt over indsamlinger og statistik**. Når du har gemt en samling i et gennemsynssæt, bevares oplysninger om samlingen, f.eks. statistik om udtrukne elementer, dybtgående indeksering, søgeforespørgslen, der bruges til samlingen, og de indholdsplaceringer, som elementer blev indsamlet fra. Desuden kan bindende samlinger ikke redigeres eller køres igen. Du kan kun kopiere eller slette dem. Bevaring af samlinger giver en historisk oversigt over de indsamlede elementer, der blev føjet til et korrektursæt. Få mere at vide under [Statistik og rapporter for bindende samlinger](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).
