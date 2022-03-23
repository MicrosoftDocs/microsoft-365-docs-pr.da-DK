---
title: Få mere at vide om dataklassificering
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Dataklassificeringsdashboardet giver dig overblik over, hvor mange følsomme data der er blevet fundet og klassificeret i din organisation.
ms.openlocfilehash: ac51e20b786b2e21d3bb83bd7900e56fb8fac513
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587755"
---
# <a name="learn-about-data-classification"></a>Få mere at vide om dataklassificering

Som Microsoft 365 administrator eller overholdelsesadministrator kan du evaluere og derefter mærke indhold i organisationen for at styre, hvor det går hen, beskytte det, uanset hvor det er, og for at sikre, at det bevares og slettes i overensstemmelse med dine organisationers behov. Det gør du via anvendelse af [følsomhedsmærkater](sensitivity-labels.md), [opbevaringsmærkater](retention.md#retention-labels) og klassificering af følsomme oplysninger. Der er forskellige måder at finde, evaluere og mærke på, men det endelige resultat er, at du kan have et stort antal dokumenter og mails, der er tagget og klassificeret med en eller begge af disse etiketter. Når du har anvendt dine opbevaringsmærkater og følsomhedsmærkater, kan du se, hvordan etiketterne bruges på tværs af din lejer, og hvad der bliver gjort med disse elementer. Siden med dataklassificering giver indblik i indholdets brødtekst, især:

- antallet af elementer, der er klassificeret som en følsom oplysningstype, og hvad disse klassificeringer er
- de øverste anvendte følsomhedsmærkater i Microsoft 365 og Azure Information Protection
- de øverste anvendte opbevaringsnavne
- en oversigt over aktiviteter, som brugerne tager på dit følsomme indhold
- placeringerne af dine følsomme og bevarede data

Du administrerer også disse funktioner på siden dataklassificering:

- [trainable classifiers](classifier-learn-about.md)
- [typer af følsomme oplysninger](sensitive-information-type-learn-about.md)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [indholdsstifinder](data-classification-content-explorer.md)
- [aktivitetsstifinder](data-classification-activity-explorer.md)

Du kan finde dataklassificering <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">i Microsoft 365 Overholdelsescenter</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **ClassificationData** >  >  **Classification**.

Få en video-rundvisning i vores dataklassificeringsfunktioner.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

Dataklassificering scanner dit følsomme indhold og mærket indhold, før du opretter nogen politikker. Dette kaldes styring **af nulændringer**. Dette giver dig mulighed for at se den påvirkning, som alle opbevarings- og følsomhedsmærkater har i dit miljø og giver dig mulighed for at begynde at vurdere dine behov for beskyttelses- og styringspolitik.

## <a name="prerequisites"></a>Forudsætninger

### <a name="permissions"></a>Tilladelser

 For at få adgang til dataklassificeringssiden skal en konto være tildelt medlemskab i en af disse roller eller rollegrupper.

**Microsoft 365 rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder

> [!NOTE]
> Som bedste fremgangsmåde skal du altid bruge rollen med mindst rettigheder til at give adgang til Microsoft 365 dataklassificering.

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at vide om [dem i Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

## <a name="sensitive-information-types-used-most-in-your-content"></a>Typer af følsomme oplysninger, der bruges mest i dit indhold

Microsoft 365 leveres med mange definitioner af følsomme oplysningstyper, f.eks. et element, der indeholder et CPR-nummer eller et kreditkortnummer. Du kan finde flere oplysninger om typer af følsomme oplysninger [under Enhedsdefinitioner for typer af følsomme oplysninger](sensitive-information-type-entity-definitions.md).

Visitkortet med typen af følsomme oplysninger viser de vigtigste typer af følsomme oplysninger, der er fundet og mærket på tværs af organisationen.

![vigtigste typer af følsomme oplysninger.](../media/data-classification-sens-info-types-card.png)

Hvis du vil finde ud af, hvor mange elementer der er i en hvilken som helst kategori, skal du holde markøren over linjen for kategorien.

![mest følsomme oplysningstyper med pegefølsomme detaljer.](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Hvis kortet viser meddelelsen "Ingen data fundet med følsomme oplysninger", betyder det, at der ikke er nogen elementer i organisationen, der er blevet klassificeret som en type af følsomme oplysninger, eller ingen elementer, der er blevet gennemsøgt. Se følgende for at komme i gang med navne:
>- [Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md)
>- [Introduktion til datastyring](get-started-with-records-management.md)
>- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>Top-følsomhedsetiketter anvendt på indhold

Når du anvender et følsomhedsmærkat på et element enten via Microsoft 365 eller Azure Information Protection (AIP), sker der to ting:

- Et mærke, der angiver værdien af elementet til din organisation, integreres i dokumentet og følger det overalt.
- Tilstedeværelsen af mærket aktiverer forskellige beskyttende funktionsmåder, f.eks obligatorisk vandmærke eller kryptering. Med slutpunktsbeskyttelse aktiveret kan du endda forhindre et element i at forlade din organisations kontrol.

Du kan finde flere oplysninger om følsomhedsmærkater under: [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)

Følsomhedsmærkater skal være aktiveret for filer, der er i SharePoint og OneDrive, for at de tilsvarende data vises på dataklassificeringssiden. Få mere at vide under [Aktivér følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Følsomhedsmærkatkortet viser antallet af elementer (mail eller dokument) efter følsomhedsniveau.

![Opdeling af indhold efter pladsholder til klassificering af følsomhedsmærkat.](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Hvis du ikke har oprettet eller publiceret nogen følsomhedsmærkater eller intet indhold har haft en følsomhedsmærkat anvendt, vil dette kort vise meddelelsen "Der blev ikke registreret nogen følsomhedsmærkater". For at komme i gang med følsomhedsmærkater, skal du se:
>- [Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md) eller for AIP [Konfigurer Azure-beskyttelsespolitikken for oplysninger](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>Topopbevaringsetiketter anvendt på indhold

Opbevaringsmærkater bruges til at administrere opbevaring og disposition af indhold i organisationen. Når de anvendes, kan de bruges til at styre, hvor længe et element opbevares før sletningen, om det skal gennemses før sletningen, hvornår opbevaringsperioden udløber, og om det skal markeres som en post. Få mere at vide under [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

Det øverste anvendte opbevaringsetiketkort viser dig, hvor mange elementer der har en given opbevaringsetiket.

![øverste anvendte opbevaringsetiketter, pladsholderskærmbillede.](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Hvis dette kort viser meddelelsen "Der blev ikke registreret nogen opbevaringsnavne", betyder det, at du ikke har oprettet eller publiceret nogen opbevaringsmærkater, eller at der ikke er anvendt en opbevaringsetiket. Se følgende for at komme i gang med opbevaringsnavne:
>- [Introduktion til informationsstyring](get-started-with-information-governance.md)

## <a name="top-activities-detected"></a>De mest populære aktiviteter registreret

Dette kort giver en hurtig oversigt over de mest almindelige handlinger, som brugerne tager på følsomhedset elementer. Du kan [bruge](data-classification-activity-explorer.md) Aktivitetsstifinder til at analysere de forskellige aktiviteter, Microsoft 365 registrerer på mærket indhold og indhold, der er placeret på Windows 10 slutpunkter.

> [!NOTE]
> Hvis dette kort viser meddelelsen "Der blev ikke registreret nogen aktivitet", betyder det, at der ikke har været nogen aktivitet på filerne, eller at bruger- og administratorrevision ikke er slået til. Hvis du vil aktivere overvågningslogfilerne, skal du se:
>- [Søg i overvågningsloggen i sikkerheds- & overholdelsescenter](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Følsomhed og opbevaringsetiket data efter placering

Dataklassificeringsrapportering handler om at gøre det mere synligt i antallet af elementer, der har hvilken mærkat samt deres placering. Disse kort giver dig besked om, hvor mange etiketter elementerne er i Exchange, SharePoint og OneDrive osv.

> [!NOTE]
> Hvis dette kort viser meddelelsen "Der blev ikke fundet nogen placeringer, betyder det, at du ikke har oprettet eller publiceret nogen følsomhedsmærkater, eller at der ikke er anvendt et indholdsnavn. For at komme i gang med følsomhedsmærkater, skal du se:
>- [Følsomhedsmærkater](sensitivity-labels.md)

## <a name="public-preview-release-notes"></a>Offentlige produktbemærkninger til forhåndsvisning 

> [!NOTE]
> **Exchange: Der vises** et lille værktøjstip, når du går ned i Exchange postkasser. Dette er for at gøre opmærksom på, at det samlede antal, der vises for følsomme oplysningstype, følsomhedsetiket og opbevaringsetiket muligvis ikke svarer nøjagtigt til det antal elementer, du finder i postkassen. Dette skyldes, at detaljeudrulning i mappen henter den direkte visning af indhold, der er klassificeret, mens det aggregerede antal beregnes. Oplysninger, som brugeren bør bemærke, selvom skimming

> [!NOTE]
> **Gengivelse af krypterede dokumenter**: SharePoint, Exchange og OneDrive filer, der er krypteret, gengives ikke i indholdsstifinder. Dette er et følsomt problem, der kræver en balance mellem behovet for at se filindhold i indholdsstifinder og behovet for at holde indholdet krypteret. Med de tilladelser, der er givet af **Indholdsoversigtslistevisning** og indholdsoversigtens rollegrupper, får du vist en listevisning af filerne, filmetadataene og et link, du kan bruge til at få adgang til indholdet via webklienten. Oplysninger, som brugeren bør bemærke, selvom skimming

> [!NOTE]
> **Understøttede tegn i navne på opbevaringsnavne i SharePoint** søgning: SharePoint-søgning understøtter `-`ikke navne på opbevaringsnavne med `_` eller i dem. F.eks. `Label-MIP` `Label_MIP` og understøttes ikke. SharePoint-søgning understøtter disse tegn i følsomhedsmærkatnavne og navne på følsomme oplysningstyper.

> [!NOTE]
> **OneDrive forbliver i forhåndsvisning**: Tak for din værdifulde feedback på OneDrive integration under vores preview-program. Når vi arbejder med det specifikke, kan du løbe ind i inkonsistente data/flows. Vi fortsætter med at fremvise OneDrive i forhåndsvisning, indtil alle rettelser er på plads. Vi sætter pris på din fortsatte støtte.

## <a name="see-also"></a>Se også

- [Vis etiketaktivitet](data-classification-activity-explorer.md)
- [Få vist mærket indhold](data-classification-content-explorer.md)
- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md)
- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md)
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om klassekammerater, der kan trænes (forhåndsvisning)](classifier-learn-about.md)

Du kan få mere at vide om, hvordan du bruger dataklassificering til at overholde bestemmelser om beskyttelse af data ved at se Udrul beskyttelse af data for bestemmelser om beskyttelse af personlige oplysninger [Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).
