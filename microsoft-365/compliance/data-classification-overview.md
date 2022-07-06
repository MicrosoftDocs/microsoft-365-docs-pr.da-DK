---
title: Om klassificering af data
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
description: Dashboardet til dataklassificering giver dig indsigt i, hvor mange følsomme data der er blevet fundet og klassificeret i din organisation.
ms.openlocfilehash: e84205a0357e87f28a77f5186265cf421add1483
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640758"
---
# <a name="learn-about-data-classification"></a>Om klassificering af data

Som Microsoft 365-administrator eller overholdelsesadministrator kan du evaluere og derefter mærke indhold i din organisation for at styre, hvor det går hen, beskytte det, uanset hvor det er, og for at sikre, at det bevares og slettes i henhold til din organisations behov. Det gør du ved hjælp af [følsomhedsmærkater](sensitivity-labels.md), [opbevaringsmærkater](retention.md#retention-labels) og klassificering af følsomme oplysninger. Der er forskellige måder at gøre registrering, evaluering og mærkning, men det endelige resultat er, at du kan have meget stort antal dokumenter og e-mails, der er mærket og klassificeret med en eller begge disse mærkater. Når du har anvendt dine opbevaringsmærkater og følsomhedsmærkater, skal du se, hvordan mærkaterne bruges på tværs af din lejer, og hvad der udføres med disse elementer. Dataklassificeringssiden giver indblik i indholdets brødtekst, især:

- antallet af elementer, der er klassificeret som følsomme oplysninger, og hvilke klassificeringer der er
- de mest anvendte følsomhedsmærkater i både Microsoft 365 og Azure Information Protection
- de øverste anvendte opbevaringsmærkater
- en oversigt over aktiviteter, som brugerne påtager sig dit følsomme indhold
- placeringerne af dine følsomme og bevarede data

Du kan også administrere disse funktioner på siden til dataklassificering:

- [klassificeringer, der kan oplæres](classifier-learn-about.md)
- [følsomme oplysningstyper](sensitive-information-type-learn-about.md)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [indholdsoversigt](data-classification-content-explorer.md)
- [aktivitetsoversigt](data-classification-activity-explorer.md)

Du kan finde dataklassificering i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>**portalklassificeringsdataklassificering** >  > .

Få en videorundvisning af vores dataklassificeringsfunktioner.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

Dataklassificering scanner dit følsomme indhold og mærket indhold, før du opretter nogen politikker. Dette kaldes **nul ændringsstyring**. Dette giver dig mulighed for at se den indvirkning, som alle opbevarings- og følsomhedsmærkater har i dit miljø, og giver dig mulighed for at begynde at vurdere dine behov for beskyttelse og styringspolitik.

## <a name="prerequisites"></a>Forudsætninger

### <a name="permissions"></a>Tilladelser

 Hvis du vil have adgang til siden til dataklassificering, skal en konto tildeles medlemskab i en af disse roller eller rollegrupper.

**Microsoft 365-rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Administrator af overholdelsesdata

> [!NOTE]
> Som bedste praksis skal du altid bruge rollen med færrest rettigheder til at give adgang til Microsoft 365-dataklassificering.

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

## <a name="sensitive-information-types-used-most-in-your-content"></a>Følsomme oplysningstyper, der bruges mest i dit indhold

Microsoft 365 indeholder mange definitioner af følsomme oplysningstyper, f.eks. et element, der indeholder et CPR-nummer eller et kreditkortnummer. Du kan få flere oplysninger om typer af følsomme oplysninger under [Objektdefinitioner for følsomme oplysninger.](sensitive-information-type-entity-definitions.md)

Kortet med følsomme oplysninger viser de mest følsomme oplysningstyper, der er fundet og mærket på tværs af organisationen.

![mest følsomme oplysningstyper.](../media/data-classification-sens-info-types-card.png)

Hvis du vil finde ud af, hvor mange elementer der er i en given klassificeringskategori, skal du holde markøren over linjen for kategorien.

![mest følsomme oplysningstyper, der holder over detaljen.](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Hvis meddelelsen "Der blev ikke fundet nogen data med følsomme oplysninger" på kortet, betyder det, at der ikke er nogen elementer i din organisation, der er klassificeret som værende af typen følsomme oplysninger, eller at der ikke er blevet gennemsøgt nogen elementer. Hvis du vil i gang med mærkater, skal du se:
>- [Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md)
>- [Kom i gang med datastyring](get-started-with-records-management.md)
>- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>De vigtigste følsomhedsmærkater, der anvendes på indhold

Når du anvender en følsomhedsmærkat på et element enten via Microsoft 365 eller Azure Information Protection (AIP), sker der to ting:

- Et mærke, der angiver værdien af elementet i din organisation, er integreret i dokumentet og følger det overalt.
- Tilstedeværelsen af mærket muliggør forskellige beskyttende funktionsmåder, f.eks. obligatorisk vandmærke eller kryptering. Når slutpunktbeskyttelse er aktiveret, kan du endda forhindre, at et element forlader din organisations kontrol.

Du kan finde flere oplysninger om følsomhedsmærkater under: [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)

Følsomhedsmærkater skal være aktiveret for filer, der er i SharePoint og OneDrive, for at de tilsvarende data vises på siden til dataklassificering. Du kan finde flere oplysninger under [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Kortet med følsomhedsmærkaten viser antallet af elementer (mail eller dokument) efter følsomhedsniveau.

![skærmbillede af opdeling af indhold efter pladsholder for klassificering af følsomhedsmærkat.](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Hvis du ikke har oprettet eller publiceret nogen følsomhedsmærkater, eller der ikke er anvendt noget indhold, hvor der er anvendt en følsomhedsmærkat, vises meddelelsen "Der blev ikke registreret nogen følsomhedsmærkater" på dette kort. Hvis du vil i gang med følsomhedsmærkater, skal du se:
>- [Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md) eller til AIP [Konfigurer beskyttelsespolitikken for Azure-oplysninger](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>Topopbevaringsmærkater anvendt på indhold

Opbevaringsmærkater bruges til at administrere opbevaring og fordeling af indhold i din organisation. Når de anvendes, kan de bruges til at styre, hvor længe et element gemmes før sletning, om det skal gennemses før sletning, hvornår opbevaringsperioden udløber, og om det skal markeres som en post. Du kan finde flere oplysninger under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

Kortet med de anvendte opbevaringsmærkater øverst viser, hvor mange elementer der har en bestemt opbevaringsmærkat.

![skærmbillede af pladsholder for top anvendte opbevaringsmærkater.](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Hvis meddelelsen "Der blev ikke registreret nogen opbevaringsmærkater" på dette kort, betyder det, at du ikke har oprettet eller publiceret nogen opbevaringsmærkater, eller at der ikke er anvendt et opbevaringsmærkat. Hvis du vil i gang med opbevaringsmærkater, skal du se:
>- [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md)

## <a name="top-activities-detected"></a>De vigtigste aktiviteter, der er registreret

Dette kort indeholder en hurtig oversigt over de mest almindelige handlinger, som brugerne foretager på de elementer, der er forsynet med følsomhedsmærkater. Du kan bruge [Aktivitetsoversigt](data-classification-activity-explorer.md) til at foretage detailudledning på de forskellige aktiviteter, som Microsoft 365 sporer på navngivet indhold og indhold, der er placeret på Windows 10 slutpunkter.

> [!NOTE]
> Hvis meddelelsen "Ingen aktivitet registreret" vises på dette kort, betyder det, at der ikke har været nogen aktivitet på filerne, eller at overvågning af brugere og administratorer ikke er slået til. Hvis du vil slå overvågningslogge til , skal du se:
>- [Søg i overvågningsloggen i Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Følsomhed og opbevaringsmærkater efter placering

Punktet for rapportering af dataklassificering er at give indblik i antallet af elementer, der har hvilken mærkat samt deres placering. Disse kort giver dig besked om, hvor mange mærkede elementer der er i Exchange, SharePoint og OneDrive osv.

> [!NOTE]
> Hvis dette kort viser meddelelsen "Der blev ikke registreret nogen placeringer, betyder det, at du ikke har oprettet eller publiceret nogen følsomhedsmærkater, eller at der ikke er anvendt noget indhold på en opbevaringsmærkat. Hvis du vil i gang med følsomhedsmærkater, skal du se:
>- [Følsomhedsmærkater](sensitivity-labels.md)

## <a name="public-preview-release-notes"></a>Produktbemærkninger til offentlig prøveversion 

> [!NOTE]
> **Antal Exchange-postkasser**: Du vil bemærke, at der vises et lille værktøjstip, når du foretager detailudledning i Exchange-postkasser. Dette er for at fremhæve, at det samlede antal, der vises for følsomme oplysninger, følsomhedsmærkat og opbevaringsmærkat, muligvis ikke stemmer nøjagtigt overens med det antal elementer, du finder i postkassen. Dette skyldes, at detailudledning i mappen henter livevisningen af indhold, som klassificeres, mens det samlede antal beregnes. Oplysninger, som brugeren bør bemærke, selvom de skimming

> [!NOTE]
> **Gengivelse af krypterede dokumenter**: SharePoint-, Exchange- og OneDrive-filer, der er krypteret, gengives ikke i Indholdsoversigt. Dette er et følsomt problem, der kræver en balance mellem behovet for at se filindholdet i Indholdsoversigt og behovet for at holde indholdet krypteret. Med de tilladelser, der er tildelt af **Listefremviser for indholdsoversigt** og rollegrupper i **Indholdsoversigt** , får du vist en listevisning af filerne, filmetadata og et link, du kan bruge til at få adgang til indholdet via webklienten. Oplysninger, som brugeren bør bemærke, selvom de skimming

> [!NOTE]
> **Understøttede tegn i navne på opbevaringsnavne i SharePoint-søgning**: SharePoint-søgning understøtter ikke navne på opbevaringsmærkater med `-`eller `_` i dem. Og understøttes f.eks `Label-MIP` `Label_MIP` . ikke. SharePoint-søgning understøtter disse tegn i navne på følsomhedsmærkater og navne på følsomme oplysninger.

> [!NOTE]
> **OneDrive er stadig en prøveversion**: Tak for din værdifulde feedback om OneDrive-integration under vores prøveversionsprogram. Når vi gennemgår de specifikke oplysninger, kan du støde på uoverensstemmende data/flow. Vi viser fortsat OneDrive som prøveversion, indtil alle rettelser er på plads. Vi sætter pris på din fortsatte support.

## <a name="see-also"></a>Se også

- [Vis etiketaktivitet](data-classification-activity-explorer.md)
- [Vis navngivet indhold](data-classification-content-explorer.md)
- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)
- [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md)
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om klassificeringer, der kan oplæres (prøveversion)](classifier-learn-about.md)

Hvis du vil vide mere om, hvordan du bruger dataklassificering til at overholde reglerne for beskyttelse af personlige oplysninger, skal du se [Udrul regler om beskyttelse af personlige oplysninger med Microsoft 365](../solutions/information-protection-deploy.md)  (aka.ms/m365dataprivacy).
