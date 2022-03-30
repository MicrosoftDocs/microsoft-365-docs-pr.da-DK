---
title: Introduktion til indholdsstifinder
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Indholdsstifinder giver dig mulighed for indbygget at få vist elementer, der er mærket.
ms.openlocfilehash: f402df53c19da78435e22717577b351fc302d0f4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679956"
---
# <a name="get-started-with-content-explorer"></a>Introduktion til indholdsstifinder

Med dataklassificeringsindholdsstifinder kan du indbygget se de elementer, der er opsummeret på oversigtssiden.

![skærmbillede med skjult indholdsstifinder.](../media/data-classification-content-explorer-1.png)

## <a name="prerequisites"></a>Forudsætninger

For licenskrav skal du se [Information Protection: Dataklassificeringsanalyse: Over indhold & Aktivitetsoversigt](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer)

### <a name="permissions"></a>Tilladelser

For at få adgang til fanen indholdsstifinder skal en konto være tildelt medlemskab i en af disse roller eller rollegrupper. 

**Microsoft 365 rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder

> [!IMPORTANT]
> Medlemskab af disse rollegrupper giver dig ikke mulighed for at få vist listen over elementer i indholdsstifinder eller at få vist indholdet af elementerne i indholdsstifinder.

> [!IMPORTANT]
> Kun globale administratorer kan administrere eller tildele tilladelser til andre brugere i Overholdelsescenter. Få mere at vide under [Giv brugere adgang til Security & Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
> 
### <a name="required-permissions-to-access-items-in-content-explorer"></a>Påkrævede tilladelser til at få adgang til elementer i indholdsstifinder

Adgang til indholdsstifinder er meget begrænset, fordi det giver dig mulighed for at læse indholdet af scannede filer.

> [!IMPORTANT]
> Disse tilladelser supercedetilladelser, der er tildelt lokalt til elementerne, hvilket giver mulighed for visning af indholdet. 

Der er to roller, der giver adgang til indholdsstifinder, og som tildeles via <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft 365 Overholdelsescenter</a>:

- **Listevisning i Indholdsstifinder**: Medlemskab af denne rollegruppe giver dig mulighed for at se hvert element og dets placering i listevisning. Rollen `data classification list viewer` er på forhånd tildelt denne rollegruppe.

- **Indholdsvisning af indhold i** Indholdsstifinder: Medlemskab af denne rollegruppe giver dig mulighed for at få vist indholdet af hvert element på listen. Rollen `data classification content viewer` er på forhånd tildelt denne rollegruppe.

Den konto, du bruger til at få adgang til indholdsstifinder, skal være i en eller begge af rollegrupperne. Disse er uafhængige rollegrupper og er ikke kumulative. Hvis du f.eks. vil give en konto mulighed for kun at få vist elementerne og deres placeringer, skal du tildele Listevisningsrettigheder til Indholdsstifinder. Hvis du vil have, at den samme konto også skal kunne se indholdet af elementerne på listen, skal du også tildele Indholdsvisning rettigheder til Indholdsvisning.

Du kan også tildele en eller begge roller til en brugerdefineret rollegruppe for at skræddersy adgang til indholdsstifinder.

En global administrator kan tildele den nødvendige indholdsoversigtsvisning og medlemskab af indholdsvisningsgruppen Indholdsoversigt.

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at [vide under Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

## <a name="content-explorer"></a>Indholdsstifinder

Indholdsstifinder viser et aktuelt øjebliksbillede af elementer med et følsomhedsmærkat, en opbevaringsmærkat eller er blevet klassificeret som en følsom oplysningstype i organisationen.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

En [DLP-politik](dlp-learn-about-dlp.md) kan hjælpe med at beskytte følsomme oplysninger, der er defineret som **en følsom oplysningstype**. Microsoft 365 indeholder [definitioner på mange almindelige typer af følsomme oplysninger på](sensitive-information-type-entity-definitions.md) tværs af mange forskellige områder, der er klar til brug. Eksempelvis et kreditkortnummer, bankkontonumre, nationale id-numre og Windows Live ID-servicenumre.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

Et [følsomhedsmærkat](sensitivity-labels.md) er blot et mærke, der angiver elementets værdi for din organisation. Den kan anvendes manuelt eller automatisk. Når det er anvendt, integreres det i dokumentet og følger det overalt. En følsomhedsmærkat aktiverer forskellige beskyttende funktionsmåder, f.eks obligatorisk vandmærke eller kryptering.

Følsomhedsmærkater skal være aktiveret for filer, der er i SharePoint og OneDrive, for at de tilsvarende data vises på dataklassificeringssiden. Få mere at vide under [Aktivér følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Opbevaringsnavne

Med [en opbevaringsetiket](retention.md) kan du definere, hvor lang tid et mærket element opbevares, og hvilke trin der skal tages, før du sletter det. De anvendes manuelt eller automatisk via politikker. De kan spille en rolle i at hjælpe din organisation med at overholde juridiske og lovmæssige krav.

### <a name="how-to-use-content-explorer"></a>Sådan bruger du indholdsstifinder

1. Åbn **Microsoft 365 Overholdelsescenter**  >  **Data** **classificationContent** >  Explorer.
2. Hvis du kender navnet på navnet eller typen af følsomme oplysninger, kan du skrive det i filterfeltet.
3. Alternativt kan du søge efter elementet ved at udvide etikettypen og vælge navnet på listen.
4. Vælg en placering under **Alle placeringer,** og bor ned i mappestrukturen til elementet.
5. Dobbeltklik for at åbne elementet indbygget i indholdsstifinder.

### <a name="export"></a>eksportér
**Eksportkontrolelementet** opretter en .csv, der indeholder en liste over det, der vises i **ruden Alle** placeringer.

![Dataklassificering af eksportkontrolelement.](../media/data_classification_export_control.png)


> [!NOTE]
> Det kan tage op til *syv dage,* før optællinger opdateres i indholdsstifinder.

### <a name="search"></a>Søg

Når du analyserer ned i en placering, f.eks. en Exchange- eller Teams-mappe eller et SharePoint-OneDrive-websted, **vises søgeværktøjet**.

![søgeværktøj til indholdsstifinder.](../media/data_classification_search_tool.png)

Søgeværktøjets omfang er det, der vises i ruden Alle placeringer, og det, du kan søge efter, varierer afhængigt af den valgte placering. 

Når **Exchange** eller **Teams** er den valgte placering, kan du søge på postkassens fulde mailadresse, f.eks`user@domainname.com`. .

Når enten **SharePoint** eller **OneDrive** placering, vises søgeværktøjet, når du analyserer ned til webstedsnavne, mapper og filer. 

Du kan søge på:

|værdi|eksempel  |
|---------|---------|
|fulde navn på websted    |`https://contoso.onmicrosoft.com/sites/sitename`    |
|filnavn    |    `RES_Resume_1234.txt`     |
|tekst i begyndelsen af filnavnet| `RES`|
|tekst efter et understregningstegn ( _ ) i filnavn|`Resume` eller `1234`| 
|filtypenavn|`txt`|


## <a name="see-also"></a>Se også

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md)
- [Enhed med følsomme definitions.md](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
