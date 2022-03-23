---
title: Insider-indholdsstifinder til risikostyring
description: Få mere at vide om indholdsoversigt for insider-risikostyring i Microsoft 365
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
ms.openlocfilehash: d60726b7fbf68ecbeb8af2d40c4c18e2bb9aaa7c
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/13/2021
ms.locfileid: "63587552"
---
# <a name="insider-risk-management-content-explorer"></a>Insider-indholdsstifinder til risikostyring

Indholdsstifinder for **insider-risikostyring** gør det muligt for brugere, der er tildelt *rollen Insider Risk Management,* at undersøge konteksten og oplysningerne om indhold, der er knyttet til aktivitet i beskeder. Casedata i Indholdsstifinder opdateres dagligt for at medtage ny aktivitet. For alle vigtige beskeder, der bekræftes i en sag, arkiveres kopier af data og meddelelsesfiler som et øjebliksbillede af elementerne, mens du bevarer de oprindelige filer og meddelelser i lagringskilderne. Hvis det er nødvendigt, kan casedatafiler eksporteres som en PDF-fil (Portable Document File) eller i det oprindelige filformat.

I nye tilfælde tager det normalt omkring en time, før indhold udfyldes i Indholdsstifinder. I tilfælde med store mængder indhold kan det tage længere tid at oprette et øjebliksbillede. Hvis indhold stadig indlæses i Indholdsstifinder, vises en statusindikator, der viser fuldførelsesprocenten.

I nogle tilfælde er data, der er knyttet til en sag, muligvis ikke tilgængelige som et øjebliksbillede til gennemsyn i Indholdsstifinder. Denne situation kan opstå, når sagsdata er blevet slettet eller flyttet, eller når der opstår en midlertidig fejl under behandling af sagsdata. Hvis denne situation opstår **, skal du** vælge Vis filer på advarselslinjen for at få vist filnavne, filsti og årsag til fejlen for hver fil. Hvis det er nødvendigt, kan disse oplysninger eksporteres til .csv (kommaseparerede værdier).

Hvis indholdet omfatter Information Rights Management-tilladelser, bevares disse tilladelser for det kopierede indhold, og brugere, der er tildelt rollen *Insider Risk Management-* administration, skal have disse tilladelser og rettigheder, hvis de skal åbne og få vist filerne. Hver fil og meddelelse tildeles automatisk et entydigt fil-id i insider-risikostyringssagen til administrationsformål. Dokumenter, der er knyttet til enhedsindikatoraktiviteter, medtages ikke i Indholdsstifinder.

> [!NOTE]
> Indholdsstifinder omfatter brugeraktiviteter, Microsoft 365 i forbindelse med tjenestefiler, f.eks. brugeraktivitet SharePoint, Exchange, Microsoft Teams og OneDrive for Business.

## <a name="column-options"></a>Indstillinger for kolonne

For at gøre det nemmere for risikoanalytikere og risikoanalytikere at gennemse hentede data og meddelelser og gennemgå konteksten for sagen er der inkluderet flere filtrerings- og sorteringsværktøjer i Indholdsstifinder. Til grundlæggende sortering understøtter kolonnerne **Dato og** Fil sortering ved hjælp af kolonnetitlerne i ruden med indholdskøen. Andre køkolonner kan føjes til visningen for at give forskellige pivoter om filer og meddelelser.

Hvis du vil tilføje eller fjerne kolonneoverskrifter for indholdskøen, **skal du bruge** kontrolelementet Rediger kolonner og vælge mellem følgende kolonneindstillinger. Disse kolonner er kort over de almindelige betingelser for mail og dokumentegenskab, der understøttes i Indholdsstifinder, og som vises senere i denne artikel.

| **Kolonneindstilling** | **Beskrivelse** |
|:------------------|:----------------|
| **Forfatter** | Forfatterfeltet fra Office dokumenter, der bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og mailer det til en anden, som derefter overfører det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter. |
| **Bcc** | Brugerne i meddelelsesfeltet Bcc er tilgængelige for mails. |
| **Cc** | Brugerne i feltet Cc-meddelelse er tilgængelige for mails. |
| **Sammensat sti** | Læsbar vej, der beskriver elementets kilde. |
| **Samtale-id** | Samtale-id i meddelelsen. |
| **Samtaleindeks** | Samtaleindeks fra meddelelsen. |
| **Tidspunkt for oprettelse** | Det tidspunkt, hvor filen eller mailen blev oprettet. |
| **Dato (UTC)** | For mails er den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter er den dato, hvor et dokument sidst blev ændret. Dato findes i UTC (Coordinated Universal Time).|
| **Det dominerende tema** | Det dominerende tema som beregnet for analyser. |
| **Id for mailsæt** | Gruppe-id for alle meddelelser i samme mailsæt. |
| **Familie-id** | Familie-id grupperer alle elementer sammen. I forbindelse med mail indeholder denne kolonne meddelelsen og alle vedhæftede filer. For dokumenter omfatter denne kolonne dokumentet og eventuelle integrerede elementer. |
| **Filklasse** | For indhold fra SharePoint og OneDrive: **Dokument**; for indhold fra **Exchange: Mail** eller Vedhæftet **fil**. |
| **Fil-id** | Dokumentidentifikator er entydig i sagen. |
| **Ikon for filtype** | Filtypenavnet for en fil. eksempelvis docx, en, pptx eller xlsx. Dette felt er den samme egenskab som egenskaben FileExtension-websted. |
| **Id** | GUID-id'et for filen. |
| **Uforanderligt id** | Uforanderligt id som gemt i Office 365. |
| **Inkluderende type** | Inkluderende type beregnet til analyse: **0** – ikke inklusive; **1** – inklusive; **2** – inklusive minus; **3** – inkluderende kopi. |
| **Senest ændret** | Den dato, hvor et dokument sidst blev ændret. |
| **Markeret som repræsentant** | Ét dokument fra hvert sæt af nøjagtige dubletter markeres som repræsentanter. |
| **Meddelelses type** | Typen af mail, der skal søges efter. Mulige værdier: kontakter, dokumenter, mail, eksterne data, faxer, im, journaler, møder, Microsoft Teams (returnerer elementer fra chats, møder og opkald i Microsoft Teams), noter, indlæg, RSS-feeds, opgaver, voicemail |
| **Deltagere** | Liste over alle deltagere i en meddelelse; Afsender, Til, Cc, Bcc. |
| **Pivot-id** | Id'et for en pivot. |
| **Modtaget** | Den dato, hvor en mail blev modtaget af en modtager. Dette felt er den samme egenskab som egenskaben Modtaget mail. |
| **Modtagere** | Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc. |
| **Repræsentativt id** | Numerisk id for hvert sæt af nøjagtige dubletter. |
| **Afsender** | Afsenderen af en mail. |
| **Afsender/forfatter** | Til mail er den person, der har sendt en meddelelse. For dokumenter har den person, der er citeret i forfatterfeltet, Office dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. To eller flere værdier forbindes logisk af operatoren ELLER. |
| **Typer af følsomme oplysninger** | Typerne af følsomme oplysninger, der er identificeret i indhold. |
| **Følsomhedsmærkater** | Følsomhedsetiketterne anvendt på indholdet. |
| **Sendt** | Den dato, hvor afsenderen sendte en mail. Dette felt er den samme egenskab som egenskaben Sendt mail. |
| **Størrelse** | For både mail og dokumenter, elementets størrelse (i byte). |
| **Emne** | Teksten i emnelinjen i en mail. |
| **Emne/titel** | Hvad mail er teksten i emnelinjen i en meddelelse. For dokumenter, titlen på dokumentet. Som beskrevet tidligere er titelegenskaben metadata angivet i Microsoft Office dokumenter. Du kan skrive navnet på mere end ét emne/titel adskilt af kommaer. To eller flere værdier forbindes logisk af operatoren ELLER. |
| **Listen Temaer** | Listen Temaer beregnes for analyser. |
| **Titel** | Titlen på dokumentet. Titelegenskaben er metadata, der er angivet i Office dokumenter. Det er forskelligt fra filnavnet på dokumentet. |
| **Hvis du vil** | Modtageren af en mail i feltet Til. |

## <a name="filtering"></a>Filtrering

Du kan bruge et eller flere filtre til at begrænse omfanget af en søgning og returnere et mere elegant sæt resultater. Hvis du vil angive et filter, **skal du** vælge Filtre øverst i indholdskøen. Mange filtre indeholder yderligere filtreringsindstillinger for at indsnævre de resultater, der returneres af filteret. Datofilteret indeholder *f.eks* . kontrolelementer til at *konfigurere en* Startdato *og Slutdato* for **filteret** Dato. Vælg et eller flere filterelementer fra følgende kategorier:

### <a name="common-filters"></a>Almindelige filtre

| **Filter** | **Beskrivelse** |
|:---------------------|:----------------|
| **Dato (UTC)** | For mails er den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter er den dato, hvor et dokument sidst blev ændret. |
| **Afsender/forfatter** | Til mail er den person, der har sendt en meddelelse. For dokumenter har den person, der er citeret *i feltet* Forfatter fra Office dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. |
| **Kilde** | Placeringen af dokumentet i din organisation. Eksempelvis en bestemt placering SharePoint webstedet. |
| **Emne/titel** | Hvad mail er teksten i emnelinjen i en meddelelse. For dokumenter, titlen på dokumentet. Titelegenskaben i dokumenter er metadata, der er angivet Microsoft Office dokumenter. Du kan skrive navnet på mere end ét emne/titel adskilt af kommaer. To eller flere værdier forbindes logisk af operatoren ELLER. |

### <a name="email-filters"></a>Mailfiltre

| **Filter** | **Beskrivelse** |
|:---------------------|:----------------|
| **Bcc** | Feltet Bcc i en mail. |
| **Cc** | Feltet Cc i en mail. |
| **Har vedhæftet fil** | Angiver, om en meddelelse har en vedhæftet fil. Værdier er angivet som **sande** eller **falske**. |
| **Er vedhæftet fil i en mail** | Hvis dokumentet er en vedhæftet fil, vises værdien som **Ja**. |
| **Er integreret dokument** | Hvis dokumentet er integreret i mailen, er værdien angivet som **Ja**. |
| **Er indbygget vedhæftet fil** | Hvis dokumentet er en indbygget vedhæftet fil i mailen, er værdien angivet som **Ja**. |
| **Deltagere** | Alle personer-felterne i en mail. Disse felter er Fra, Til, Cc og Bcc. |
| **Modtaget** | Den dato, hvor en mail blev modtaget af en modtager. |
| **Modtagerdomæner** | Liste over alle domæner for modtagere af en meddelelse. |
| **Modtagere** | Modtagerne af mailen. |
| **Afsender** | Feltet Afsender (Fra) for meddelelsestyper.  Formatet er **DisplayName \<SmtpAddress>**. |
| **Afsenderdomæne** | Afsenderens domæne. |
| **Hvis du vil** | Feltet Til i en mail. |
| **Entydigt i mailsæt** | Falsk, hvis der er en kopi af den vedhæftede fil i mailsættet. |

## <a name="document-filters"></a>Dokumentfiltre

| **Filtre** | **Beskrivelse** |
|:---------------------|:----------------|
| **Mærkater til overholdelse af regler og** | Overensstemmelsesetiketter anvendes Office 365. |
| **Oprettet klokkeslæt (UTC)** | Dato og klokkeslæt for oprettelse af filen eller mailen. Dato og klokkeslæt er i UTC (Coordinated Universal Time). |
| **Dato for seneste ændring (UTC)** | Den dato, hvor et dokument sidst blev ændret. Dato og klokkeslæt er i UTC (Coordinated Universal Time). |
| **Filtypenavn** | Filtypenavnet for filen. |
| **Brugeraktivitetshændelser** | Aktivitet for elementer, der er relateret til specifik brugeraktivitet i en sag.  Når du f.eks. vælger et link til "Udforsk indhold" for en aktivitet på  siden Brugeraktivitet for en sag, bruges dette filter til at vise elementer, der er relateret til den pågældende aktivitet. |
| **Arbejdsprodukt** | Arbejdsprodukttypen for dokumentet. Eksempelvis anmærkninger eller mærker i dokumentet. |
