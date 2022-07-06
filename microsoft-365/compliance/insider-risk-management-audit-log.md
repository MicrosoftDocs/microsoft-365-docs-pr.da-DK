---
title: Overvågningslog for styring af insiderrisiko
description: Få mere at vide om overvågningsloggen til styring af insiderrisiko i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
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
ms.openlocfilehash: 544c31205469bcb810bd3f05d9f686d650df6269
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638185"
---
# <a name="insider-risk-management-audit-log"></a>Overvågningslog for styring af insiderrisiko

Overvågningsloggen for styring af insiderrisiko giver dig mulighed for at holde dig informeret om de handlinger, der blev udført på insiderrisikostyringsfunktioner. Denne log giver mulighed for uafhængig gennemgang af de handlinger, som brugere, der er tildelt en eller flere insiderrisikostyringsrollegrupper, har udført. Overvågningsloggen for styring af insiderrisiko er automatisk aktiveret i din organisation og kan ikke deaktiveres.

![Overvågningslog for styring af insiderrisiko.](../media/insider-risk-audit-log.png)

Overvågningsloggen opdateres automatisk og straks, når overvågede aktiviteter finder sted, og loggen bevarer oplysninger om aktiviteten i 180 dage (ca. seks måneder). Efter 180 dage slettes dataene for aktiviteten permanent fra loggen.

Områder, der er omfattet af aktivitetsovervågning, omfatter:

- Politikker
- Tilfælde
- Beskeder
- Indstillinger
- Brugere
- Bemærk skabeloner

Hvis du vil have vist og eksportere data fra overvågningsloggen, skal brugerne tildeles rollegrupperne *Insider Risk Management* eller *Insider Risk Management Auditør* . Hvis du vil vide mere om rollegrupper for styring af insiderrisiko, skal [du se Introduktion til styring af insiderrisiko trin 1: Aktivering af tilladelser](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Overvågningsloggen til styring af insiderrisiko er ikke knyttet til Microsoft 365-overvågningsloggen, de er uafhængige overvågningssystemer og registrerer oplysninger om separate aktiviteter. Deaktivering af Microsoft 365-overvågning påvirker ikke aktivitetsovervågning i styring af insiderrisiko.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Vis aktivitet i overvågningsloggen for insiderrisiko

Hvis du vil have vist funktionsaktivitet, der overvåges for styring af insiderrisiko, skal du navigere til og vælge linket **Insider-risikoovervågningslog** i øverste højre område på en hvilken som helst fane med styring af insiderrisiko. Som standard får du vist følgende oplysninger for insiderrisikostyringsaktiviteter:

- **Aktivitet:** En beskrivelse af den aktivitet, en bruger har foretaget i løsningen til styring af insiderrisiko.
- **Kategori:** Det område eller element, hvor aktiviteten blev udført. Du kan f.eks. se *Politikker* som kategorien, når aktiviteter til ændring af politik blev udført.
- **Aktivitet udført af:** Brugernavnet på den bruger, der udførte aktiviteten.
- **Dato:** Den dato og det klokkeslæt, hvor aktiviteten blev udført. Dato og klokkeslæt er den lokale dato og det lokale klokkeslæt for din organisation.

Du kan finde flere oplysninger om en logført aktivitet ved at vælge aktiviteten for at få vist ruden med aktivitetsoplysninger. Denne rude indeholder flere oplysninger om aktiviteten.

## <a name="columns-and-filtering"></a>Kolonner og filtrering

For at gøre det nemmere for revisorer at gennemse logført aktivitet understøttes filtrering i **overvågningsloggen over insiderrisiko**. I forbindelse med grundlæggende filtrering er køkolonner tilgængelige, som kan føjes til visningen for at levere forskellige pivots om filer og meddelelser. Du kan filtrere aktiviteter efter **den kategori, det datointerval** og den **aktivitet, der udføres af** felter.

Hvis du vil tilføje eller fjerne kolonneoverskrifter for aktivitetskøen, skal du bruge kontrolelementet **Tilpas kolonner** og vælge blandt kolonneindstillingerne. Disse kolonner knyttes til almindelige betingelser, der understøttes i **overvågningsloggen over insiderrisici** , og vises senere i denne artikel.

## <a name="audit-log-export"></a>Eksport af overvågningslog

Brugere, der er tildelt rollegrupperne *Insider Risk Management* eller *Insider Risk Management,* kan eksportere alle aktiviteter i overvågningsloggen til en fil med .csv (kommaseparerede værdier) ved at vælge **Eksportér** på siden **Insider risk audit log** . Afhængigt af aktiviteten er nogle felter for en aktivitet muligvis ikke relevante for aktiviteten, og disse felter vises som tomme i den eksporterede fil.

Filen indeholder aktivitetsoplysninger for følgende felter:

- **Aktivitet udført af:** Brugernavnet på den bruger, der ændrer en elementværdi. De brugere, der er angivet her, blev tildelt en eller flere af følgende [rollerollegrupper for styring af insiderrisiko](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management): *Insider Risk Management*, *Administratorer af Insider Risk Management*, *Insider Risk Management Analysts*, *Insider Risk Management Investigators*. Hver rollegruppe har forskellige tilladelsesniveauer til administration af insiderrisikofunktioner.
- **Aktivitet:** Den aktivitet, der udføres på et element. Værdier vises *, slettes, tilføjes, redigeres politik, sag, bruger, besked* og *indstillinger.*
- **Tilføjet**: Objekter, der blev tilføjet under aktiviteten, f.eks. brugere, filtyper eller domæner.
- **Beskedmængde**: Niveauet af beskedmængde, der er defineret under indstillinger for styring af insiderrisiko.
- **Beløb**: De aktuelt valgte brugerdefinerede indikatorbeløb for en politik.
- **Aktiv-id**: Aktiv-id'et for det prioriterede fysiske aktiv, som aktiviteten blev udført på.
- **Kategori:** Kategorien for det element, der er ændret. Værdier er *skabelonerne Politikker, Sager, Brugere, Beskeder, Indstillinger* og *Meddelelse.*
- **Dato:** Dato og klokkeslæt, der er angivet i din organisations lokale dato og klokkeslæt.
- **Beskrivelse**: Brugerens beskrivelse af det objekt, der reageres på (f.eks. en politik eller en prioriteret brugergruppe).
- **DLP-politik**: Politikken for Microsoft Purview Forebyggelse af datatab (DLP) er valgt til at udløse medtagelse i en politik for styring af insiderrisiko.
- **Indikator**: Indikatoren i indstillingerne for insiderrisiko, som aktiviteten blev udført på (f.eks. tilføjelse eller fjernelse af en indikator).
- **Meddelelsesskabelon**: Den meddelelsesskabelon, som aktiviteten blev udført på.
- **Antal dage**: Vinduet til aktivering af politikken, der er defineret i indstillingerne for insiderrisiko.
- **Antal filer**: Grænsen for filmængde, der er defineret under indstillinger for styring af insiderrisiko.
- **Politikskabelon**: Den politikskabelon, som indikatorerne har handlet på, tilhører.
- **Forrige beløb**: De tidligere valgte brugerdefinerede indikatorbeløb for en politik.
- **Prioritetsbrugergruppe**: Den prioritetsbrugergruppe, som aktiviteten blev udført på.
- **Fjernet**: Objekter, der blev fjernet under aktiviteten, f.eks. brugere, filtyper eller domæner.
- **Afsender**: Afsenderfeltet i den meddelelsesskabelon, som aktiviteten blev udført på.
- **Destinationspolitik**: Den politik, som aktiviteten blev udført på (f.eks. tilføjelse af en bruger til eller fjernelse af en bruger fra).
- **Brødtekst i skabelonmeddelelse**: Meddelelsesteksten i den meddelelsesskabelon, som aktiviteten blev udført på.
- **Skabelonemne**: Emnefeltet i den meddelelsesskabelon, som aktiviteten blev udført på.
- **Bruger:** Bruger, som aktiviteten blev udført på.
