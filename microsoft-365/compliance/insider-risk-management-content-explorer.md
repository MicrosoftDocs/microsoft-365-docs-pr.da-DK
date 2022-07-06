---
title: Indholdsoversigt for styring af insiderrisiko
description: Få mere at vide om styring af insiderrisikoIndholdsoversigt i Microsoft Purview
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
ms.openlocfilehash: c193325608feef3bc8114b50af9d5e5832eb9d66
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642541"
---
# <a name="insider-risk-management-content-explorer"></a>Indholdsoversigt for styring af insiderrisiko

**Indholdsoversigten** til styring af insiderrisiko giver brugere, der er tildelt rollen *Insider Risk Management Investigators*, mulighed for at undersøge konteksten og detaljerne for det indhold, der er knyttet til aktivitet i beskeder. Sagsdata i Indholdsoversigt opdateres dagligt for at inkludere ny aktivitet. For alle beskeder, der bekræftes til en sag, arkiveres kopier af data og meddelelsesfiler som et snapshot i tid af elementerne, samtidig med at de oprindelige filer og meddelelser bevares i lagerkilderne. Hvis det er nødvendigt, kan sagsdatafiler eksporteres som en PDF-fil (Portable Document File) eller i det oprindelige filformat.

I nye tilfælde tager det normalt ca. en time, før indhold udfyldes i Indholdsoversigt. I forbindelse med sager med store mængder indhold kan det tage længere tid at oprette et snapshot. Hvis indhold stadig indlæses i Indholdsoversigt, får du vist en statusindikator, der viser fuldførelsesprocenten.

I nogle tilfælde er data, der er knyttet til en sag, muligvis ikke tilgængelige som et snapshot til gennemsyn i Indholdsoversigt. Denne situation kan opstå, når sagsdata er blevet slettet eller flyttet, eller når der opstår en midlertidig fejl under behandling af sagsdata. Hvis denne situation opstår, skal du vælge **Vis filer** på advarselslinjen for at få vist filnavne, filsti og årsag til fejlen for hver fil. Disse oplysninger kan om nødvendigt eksporteres til en fil med .csv (kommaseparerede værdier).

Hvis indholdet indeholder Tilladelser til Information Rights Management, vedligeholdes disse tilladelser for det kopierede indhold, og brugere, der har fået tildelt rollen *Undersøgere af insiderrisikostyring* , skal bruge disse tilladelser og rettigheder, hvis de har brug for at åbne og få vist filerne. Hver fil og meddelelse tildeles automatisk et entydigt fil-id i insiderrisikostyringscasen til administrationsmæssige formål. Dokumenter, der er knyttet til enhedens indikatoraktiviteter, er ikke inkluderet i Indholdsoversigt.

> [!NOTE]
> Indholdsoversigt indeholder brugeraktiviteter, der er relateret til Microsoft 365-tjenestefiler, f.eks. brugeraktivitet på SharePoint, Exchange, Microsoft Teams og OneDrive for Business.

## <a name="column-options"></a>Kolonneindstillinger

For at gøre det nemmere for risikoanalytikere og efterforskere at gennemse hentede data og meddelelser og gennemse konteksten i sagen er flere filtrerings- og sorteringsværktøjer inkluderet i Indholdsoversigt. I forbindelse med grundlæggende sortering understøtter kolonnerne **Dato** og **Filklasse** sortering ved hjælp af kolonnetitlerne i ruden med indholdskøen. Andre køkolonner er tilgængelige, som kan føjes til visningen for at levere forskellige pivots på filerne og meddelelserne.

Hvis du vil tilføje eller fjerne kolonneoverskrifter for indholdskøen, skal du bruge kontrolelementet **Rediger kolonner** og vælge mellem følgende kolonneindstillinger. Disse kolonner knyttes til de almindelige betingelser, mail og dokumentegenskaber, der understøttes i Indholdsoversigt og er angivet senere i denne artikel.

| **Indstillingen Kolonne** | **Beskrivelse** |
|:------------------|:----------------|
| **Forfatter** | Forfatterfeltet fra Office-dokumenter, som bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og sender mails med det til en anden, der derefter uploader det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter. |
| **Bcc** | Brugere i feltet Bcc-meddelelse er tilgængelige for mails. |
| **Cc** | Brugere i feltet Cc-meddelelse er tilgængelige for mails. |
| **Sammensat sti** | Sti, der kan læses af mennesker, og som beskriver elementets kilde. |
| **Samtale-id** | Samtale-id fra meddelelsen. |
| **Samtaleindeks** | Samtaleindeks fra meddelelsen. |
| **Oprettelsestidspunkt** | Det tidspunkt, hvor filen eller mailen blev oprettet. |
| **Dato (UTC)** | For mail den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter den dato, hvor et dokument sidst blev ændret. Datoen er i UTC (Coordinated Universal Time).|
| **Dominerende tema** | Dominerende tema som beregnet til analyse. |
| **Id for mailsæt** | Gruppe-id for alle meddelelser i det samme mailsæt. |
| **Familie-id** | Familie-id grupperer alle elementer. i forbindelse med mail indeholder denne kolonne meddelelsen og alle vedhæftede filer. for dokumenter indeholder denne kolonne dokumentet og alle integrerede elementer. |
| **Filklasse** | For indhold fra SharePoint og OneDrive: **Dokument**; for indhold fra Exchange: **Mail** eller **Vedhæftet fil**. |
| **Fil-id** | Dokument-id'et er entydigt i sagen. |
| **Ikonet Filtype** | Filtypenavnet for en fil. f.eks. docx, one, pptx eller xlsx. Dette felt er den samme egenskab som webstedsegenskaben FileExtension. |
| **ID** | GUID-id'et for filen. |
| **Uforanderligt id** | Uforanderligt id som gemt i Office 365. |
| **Inkluderende type** | Inkluderende type beregnet for analyse: **0** – ikke inkluderende; **1** - inklusive; **2** - inklusive minus; **3** – inklusive kopi. |
| **Senest ændret** | Den dato, hvor et dokument sidst blev ændret. |
| **Markeret som repræsentant** | Ét dokument fra hvert sæt nøjagtige dubletter markeres som repræsentanter. |
| **Meddelelsestype** | Den type mail, der skal søges efter. Mulige værdier: kontakter, dokumenter, mail, eksterne data, faxer, chat, journaler, møder, Microsoft Teams (returnerer elementer fra chats, møder og opkald i Microsoft Teams), noter, indlæg, RSS-feeds, opgaver, voicemail |
| **Deltagere** | Liste over alle deltagere i en meddelelse. f.eks. Afsender, Til, Cc, Bcc. |
| **Pivot-id** | Id'et for en pivot. |
| **Modtaget** | Den dato, hvor en mail blev modtaget af en modtager. Dette felt er den samme egenskab som egenskaben Modtaget mail. |
| **Modtagere** | Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc. |
| **Repræsentativt id** | Numerisk id for hvert sæt nøjagtige dubletter. |
| **Afsender** | Afsenderen af en mail. |
| **Afsender/forfatter** | Den person, der sendte en meddelelse i forbindelse med en mail. For dokumenter: den person, der er nævnt i forfatterfeltet, fra Office-dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. To eller flere værdier er logisk forbundet af operatoren OR. |
| **Følsomme infotyper** | De følsomme oplysningstyper, der er identificeret i indhold. |
| **Følsomhedsmærkater** | De følsomhedsmærkater, der er anvendt på indholdet. |
| **Sendt** | Den dato, hvor en mail blev sendt af afsenderen. Dette felt er den samme egenskab som egenskaben Sendt mail. |
| **Størrelse** | Størrelsen på elementet (i byte) for både mail og dokumenter. |
| **Emne** | Teksten i emnelinjen i en mail. |
| **Emne/titel** | I forbindelse med mail er teksten i emnelinjen i en meddelelse. Titlen på dokumentet for dokumenter. Som tidligere forklaret er egenskaben Title metadata angivet i Microsoft Office-dokumenter. Du kan skrive navnet på mere end ét emne/én titel adskilt af kommaer. To eller flere værdier er logisk forbundet af operatoren OR. |
| **Liste over temaer** | Listen Temaer beregnet til analyse. |
| **Titel** | Dokumentets titel. Egenskaben Title er metadata, der er angivet i Office-dokumenter. Den er forskellig fra dokumentets filnavn. |
| **Til** | Modtageren af en mail i feltet Til. |

## <a name="filtering"></a>Filtrering

Du kan bruge et eller flere filtre til at indsnævre omfanget af en søgning og returnere et mere raffineret sæt resultater. Hvis du vil angive et filter, skal du vælge **Filtre** øverst i indholdskøen. Mange filtre indeholder yderligere filtreringsindstillinger, der hjælper med at indsnævre de resultater, der returneres af filteret. *Datofilteret* indeholder f.eks. kontrolelementer til konfiguration af en *startdato* og *en slutdato* for filteret **Dato**. Vælg et eller flere filterelementer i følgende kategorier:

### <a name="common-filters"></a>Fælles filtre

| **Filter** | **Beskrivelse** |
|:---------------------|:----------------|
| **Dato (UTC)** | For mail den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter den dato, hvor et dokument sidst blev ændret. |
| **Afsender/forfatter** | Den person, der sendte en meddelelse i forbindelse med en mail. For dokumenter den person, der er nævnt i feltet *Forfatter* fra Office-dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. |
| **Kilde** | Dokumentets placering i din organisation. Det kan f.eks. være en bestemt sharePoint-webstedsplacering. |
| **Emne/titel** | I forbindelse med mail er teksten i emnelinjen i en meddelelse. Titlen på dokumentet for dokumenter. Egenskaben Title i dokumenter er metadata, der er angivet i Microsoft Office-dokumenter. Du kan skrive navnet på mere end ét emne/én titel adskilt af kommaer. To eller flere værdier er logisk forbundet af operatoren OR. |

### <a name="email-filters"></a>Mailfiltre

| **Filter** | **Beskrivelse** |
|:---------------------|:----------------|
| **Bcc** | Feltet Bcc i en mail. |
| **Cc** | Feltet Cc i en mail. |
| **Har vedhæftet fil** | Angiver, om en meddelelse har en vedhæftet fil. Værdier er angivet som **true** eller **false**. |
| **Er vedhæftet fil** | Hvis dokumentet er en vedhæftet fil, er værdien angivet som **Ja**. |
| **Er et integreret dokument** | Hvis dokumentet er integreret i mailen, er værdien angivet som **Ja**. |
| **Er indbygget vedhæftet fil** | Hvis dokumentet er en indbygget vedhæftet fil i mailen, er værdien angivet som **Ja**. |
| **Deltagere** | Alle personfelterne i en mail. Disse felter er Fra, Til, Cc og Bcc. |
| **Modtaget** | Den dato, hvor en mail blev modtaget af en modtager. |
| **Modtagerdomæner** | Liste over alle domæner for modtagere af en meddelelse. |
| **Modtagere** | Modtagerne af mailen. |
| **Afsender** | Afsenderfelt (fra) for meddelelsestyper.  Formatet er **DisplayName \<SmtpAddress>**. |
| **Afsenderdomæne** | Afsenderens domæne. |
| **Til** | Feltet Til i en mail. |
| **Entydig i mailsæt** | Falsk, hvis der er en dublet af den vedhæftede fil i mailsættet. |

## <a name="document-filters"></a>Dokumentfiltre

| **Filtre** | **Beskrivelse** |
|:---------------------|:----------------|
| **Overholdelsesmærkater** | Overholdelsesmærkater anvendt i Office 365. |
| **Oprettelsestidspunkt (UTC)** | Den dato og det klokkeslæt, hvor filen eller mailen blev oprettet. Datoen og klokkeslættet er i UTC (Coordinated Universal Time). |
| **Dato for seneste ændring (UTC)** | Den dato, hvor et dokument sidst blev ændret. Datoen og klokkeslættet er i UTC (Coordinated Universal Time). |
| **Filtypenavn** | Filtypen for filen. |
| **Hændelser for brugeraktivitet** | Aktivitet for elementer, der er relateret til en bestemt brugeraktivitet i en sag.  Når du f.eks. vælger et link til "Udforsk indhold" for en aktivitet på siden **Brugeraktivitet** for en sag, bruges dette filter til at vise elementer, der er relateret til den pågældende aktivitet. |
| **Arbejdsprodukt** | Arbejdsprodukttypen for dokumentet. Det kan f.eks. være anmærkninger eller mærker i dokumentet. |
