---
title: Insider-overvågningslog til risikostyring
description: Få mere at vide om insider-overvågningsloggen for risikostyring i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 2bf453e8856f69e9ddb8c7c7a9264267ef77b4f0
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63597463"
---
# <a name="insider-risk-management-audit-log"></a>Insider-overvågningslog til risikostyring

Insider-overvågningsloggen for risikostyring giver dig mulighed for at holde dig opdateret om de handlinger, der er foretaget på insider-risikostyringsfunktioner. Denne logfil giver mulighed for uafhængig gennemgang af de handlinger, der er foretaget af brugere, som er tildelt en eller flere Insider Risk Management-rollegrupper. Insider-overvågningsloggen for risikostyring er automatisk aktiveret i din organisation og kan ikke deaktiveres.

![Insider-overvågningslog for risikostyring.](../media/insider-risk-audit-log.png)

Overvågningsloggen opdateres automatisk og opdateres straks, når der foretages overvågede aktiviteter, og logfilen bevarer oplysninger om aktiviteten i 180 dage (ca. seks måneder). Efter 180 dage slettes dataene for aktiviteten permanent fra logfilen.

Områder i aktivitetsovervågning omfatter:

- Politikker
- Sager
- Beskeder
- Indstillinger
- Brugere
- Meddelelsesskabeloner

For at få vist og eksportere data fra overvågningsloggen skal brugere være tildelt rollegrupperne *Insider Risk Management* eller *Insider Risk Management-revisorer* . Du kan få mere at vide om insider-rollegrupper i Introduktion til [Insider-risikostyring Trin 1: Aktivering af tilladelser](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Insider-overvågningsloggen for risikostyring er ikke knyttet til den Microsoft 365 overvågningslog, de er uafhængige overvågningssystemer og registrerer oplysninger om separate aktiviteter. Deaktivering Microsoft 365 overvågning påvirker ikke aktivitetsrevision inden for insider-risikostyring.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Vis aktivitet i overvågningsloggen for insider-risiko

Hvis du vil have vist funktionsaktiviteter, som overvåges for insider-risikostyring,  skal du gå til og vælge linket Insider-risikorevisionslog i det øverste højre område på fanen insider-risikostyring. Som standard får du vist følgende oplysninger for Insider-risikostyringsaktiviteter:

- **Aktivitet:** En beskrivelse af de aktiviteter, en bruger tager inden for insider-risikostyringsløsningen.
- **Kategori:** Det område eller element, hvor aktiviteten blev udført. Du får f.eks. vist *Politikker* som kategorien, når der blev udført ændringer af politikken.
- **Aktivitet, der er udført af:** Brugernavnet på den bruger, der udførte aktiviteten.
- **Dato:** Den dato og det klokkeslæt, hvor aktiviteten blev udført. Dato og klokkeslæt er organisationens lokale dato og klokkeslæt.

Hvis du vil have mere at vide om en logført aktivitet, skal du vælge aktiviteten for at få vist ruden med aktivitetsoplysninger. Denne rude indeholder yderligere oplysninger om aktiviteten.

## <a name="columns-and-filtering"></a>Kolonner og filtrering

For at gøre det nemmere for revisorer at gennemse logført aktivitet understøttes filtrering i **Insider-risikorevisionsloggen**. Til grundlæggende filtrering kan køkolonner føjes til visningen for at give forskellige pivoter om filer og meddelelser. Du kan filtrere aktiviteter efter felterne **Kategori, Datointerval og** **Aktivitet udført efter** .

Hvis du vil tilføje eller fjerne kolonneoverskrifter for aktivitetskøen, skal du bruge **kontrolelementet** Tilpas kolonner og vælge mellem kolonneindstillingerne. Disse kolonner knyttes til almindelige betingelser, der understøttes **i Insider-risikorevisionsloggen** , og de vises senere i denne artikel.

## <a name="audit-log-export"></a>Eksport af overvågningslogfil

Brugere, der er tildelt rollegrupperne *Insider Risk Management* eller *Insider Risk Management-revisorer*, kan eksportere alle aktiviteter i overvågningsloggen til en .csv-fil (kommaseparerede værdier) ved at  vælge Eksportér på siden **Insider-risikorevisionslog**. Afhængigt af aktiviteten er nogle felter for en aktivitet muligvis ikke relevante for aktiviteten, og disse felter vises som tomme i den eksporterede fil.

Filen indeholder aktivitetsoplysninger for følgende felter:

- **Aktivitet, der er udført af:** Brugernavnet på den bruger, der ændrer en elementværdi. De brugere, der er angivet her, er blevet tildelt en eller flere af følgende rollegrupper inden for [insider-risikostyring](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management): *Insider Risk Management*, *Insider Risk Management-administratorer*, *Insider-analytikere* for risikostyring, *insider-risikohåndteringsanalyser*. Hver rollegruppe har forskellige tilladelsesniveauer til administration af insider-risikofunktioner.
- **Aktivitet:** Den aktivitet, der er taget på et element. Værdier vises *, slettes, tilføjes, redigeret politik, sag, bruger, besked* *og Indstillinger.*
- **Tilføjet**: Objekter, der blev tilføjet under aktiviteten, f.eks. brugere, filtyper eller domæner.
- **Lydstyrke for** beskeder: Niveauet for mængden af beskeder, der er defineret i indstillingerne for insider-risikostyring.
- **Beløb**: De aktuelt valgte brugerdefinerede indikatorbeløb for en politik.
- **Aktiv-id**: Aktiv-id'et for det prioritets fysiske aktiv, som aktiviteten blev udført på.
- **Kategori:** Kategorien for elementet er ændret. Værdier er politikker *, sager, brugere, beskeder, Indstillinger og meddelelser**.*
- **Dato:** Dato og klokkeslæt, der er angivet i organisationens lokale dato og klokkeslæt.
- **Beskrivelse**: Brugerens input til beskrivelse af det objekt, der reageres på (f.eks. en politik eller en prioriteret brugergruppe).
- **DLP-politik: DLP-politikken** (forebyggelse af datatab) valgt til at udløse inklusion i en politik for insider-risikostyring.
- **Indikator**: Indikatoren i indstillingerne for Insider-risiko, som aktiviteten blev udført på (f.eks. tilføjelse eller fjernelse af en indikator).
- **Meddelelsesskabelon**: Den meddelelsesskabelon, som aktiviteten blev udført på.
- **Antal dage**: Aktiveringsvinduet for politikker er defineret i indstillingerne for insider-risiko.
- **Antal filer**: Den filmængdegrænse, der er defineret i indstillingerne for insider-risikostyring.
- **Politikskabelon**: Den politikskabelon, som indikatorerne handler på tilhører.
- **Forrige beløb**: Det tidligere valgte beløb for brugerdefinerede indikatorbeløb for en politik.
- **Prioritetsbrugergruppe**: Den prioritetsbrugergruppe, aktiviteten blev udført på.
- **Fjernet**: Objekter, der blev fjernet under aktiviteten, f.eks. brugere, filtyper eller domæner.
- **Afsender**: Afsenderfeltet i meddelelsesskabelonen, som aktiviteten blev udført på.
- **Målpolitik**: Den politik, aktiviteten blev udført på (f.eks. tilføjelse af en bruger til eller fjernelse af en bruger fra).
- **Skabelonens brødtekst**: Meddelelsesteksten i meddelelsesskabelonen, som aktiviteten blev udført på.
- **Skabelonens** emne: Emnefeltet i meddelelsesskabelonen, som aktiviteten blev udført på.
- **Bruger:** Brugeren, som aktiviteten blev udført på.
