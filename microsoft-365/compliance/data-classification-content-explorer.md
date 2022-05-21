---
title: Kom i gang med Indholdsviser
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
description: Med Indholdsoversigt kan du få vist elementer, der er forsynet med mærkater i det oprindelige miljø.
ms.openlocfilehash: fdc67df9819054eedbe84ce647d77177039cd4a8
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623281"
---
# <a name="get-started-with-content-explorer"></a>Kom i gang med Indholdsviser

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Med Indholdsoversigt kan du oprindeligt få vist de elementer, der er opsummeret på oversigtssiden.

## <a name="prerequisites"></a>Forudsætninger

Du kan få mere at vide om licenskrav under [Information Protection: Analyse af dataklassificering: Oversigt over indhold & Aktivitetsoversigt](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer)

### <a name="permissions"></a>Tilladelser

Hvis du vil have adgang til fanen indholdsoversigt, skal en konto tildeles medlemskab i en af disse roller eller rollegrupper. 

**Microsoft 365 rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Administrator af overholdelsesdata

> [!IMPORTANT]
> Medlemskab af disse rollegrupper giver dig ikke mulighed for at få vist listen over elementer i Indholdsoversigt eller at få vist indholdet af elementerne i Indholdsoversigt.

> [!IMPORTANT]
> Det er kun globale administratorer, der kan administrere eller tildele tilladelser til andre brugere på overholdelsesportalen. Du kan få flere oplysninger [under Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md).
> 
### <a name="required-permissions-to-access-items-in-content-explorer"></a>Påkrævede tilladelser til at få adgang til elementer i Indholdsoversigt

Adgangen til Indholdsoversigt er meget begrænset, fordi du kan læse indholdet af scannede filer.

> [!IMPORTANT]
> Disse tilladelser tilsidesætter tilladelser, der er tildelt elementerne lokalt, hvilket gør det muligt at få vist indholdet. 

Der er to roller, der giver adgang til indholdsoversigten, og den tildeles ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft Purview-compliance-portal</a>:

- **Listefremviser til Indholdsoversigt**: Medlemskab i denne rollegruppe giver dig mulighed for at se hvert element og dets placering i listevisning. Rollen `data classification list viewer` er tildelt denne rollegruppe på forhånd.

- **Indholdsvisning i Indholdsoversigt**: Medlemskab af denne rollegruppe giver dig mulighed for at få vist indholdet af hvert element på listen. Rollen `data classification content viewer` er tildelt denne rollegruppe på forhånd.

Den konto, du bruger til at få adgang til Indholdsoversigt, skal være i en eller begge rollegrupper. Disse er uafhængige rollegrupper og er ikke akkumulerede. Hvis du f.eks. vil give en konto mulighed for kun at få vist elementerne og deres placeringer, skal du tildele listefremviserrettigheder til Indholdsoversigt. Hvis du vil have, at den samme konto også skal kunne få vist indholdet af elementerne på listen, skal du også tildele Indholdsoversigt rettigheder til indholdsfremviser.

Du kan også tildele en eller begge roller til en brugerdefineret rollegruppe for at skræddersy adgangen til indholdsoversigten.

En global administrator kan tildele den nødvendige listefremviser til Indholdsoversigt og medlemskab af rollegruppen Indholdsfremviser i Indholdsoversigt.

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection administrator
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide under [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

## <a name="content-explorer"></a>Indholdsoversigt

Indholdsoversigt viser et aktuelt snapshot af de elementer, der har en følsomhedsmærkat, en opbevaringsmærkat eller er klassificeret som en følsom oplysningstype i din organisation.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

En [DLP-politik](dlp-learn-about-dlp.md) kan hjælpe med at beskytte følsomme oplysninger, der defineres som en **type følsomme oplysninger**. Microsoft 365 indeholder [definitioner til mange almindelige følsomme oplysningstyper](sensitive-information-type-entity-definitions.md) fra mange forskellige områder, der er klar til brug. Det kan f.eks. være et kreditkortnummer, bankkontonumre, nationale id-numre og Windows live-id-tjenestenumre.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

En [følsomhedsmærkat](sensitivity-labels.md) er blot et mærke, der angiver værdien af elementet i din organisation. Den kan anvendes manuelt eller automatisk. Når etiketten er anvendt, integreres den i dokumentet og følger dokumentet overalt, hvor det går. En følsomhedsmærkat muliggør forskellige beskyttende funktionsmåder, f.eks. obligatorisk vandmærke eller kryptering.

Følsomhedsmærkater skal være aktiveret for filer, der er i SharePoint og OneDrive, for at de tilsvarende data vises på siden til dataklassificering. Du kan få flere oplysninger under [Aktivér følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Opbevaringsmærkater

En [opbevaringsmærkat](retention.md) giver dig mulighed for at definere, hvor længe et navngivet element bevares, og de trin, der skal udføres, før du sletter det. De anvendes manuelt eller automatisk via politikker. De kan spille en rolle for at hjælpe din organisation med at overholde de juridiske og lovmæssige krav.

### <a name="how-to-use-content-explorer"></a>Sådan bruger du Indholdsoversigt

1. Åbn **Microsoft Purview-compliance-portal**  >  **DataklassificeringIndholdoversigt** > .
2. Hvis du kender navnet på etiketten eller typen af følsomme oplysninger, kan du skrive det i filterfeltet.
3. Du kan også søge efter elementet ved at udvide mærkattypen og vælge etiketten på listen.
4. Vælg en placering under **Alle placeringer,** og analysér mappestrukturen ned til elementet.
5. Dobbeltklik for at åbne elementet oprindeligt i Indholdsoversigt.

### <a name="export"></a>eksportér
**Eksportkontrolelementet** opretter en .csv fil, der indeholder en liste over, hvad rudens fokus er.

![eksportkontrol af dataklassificering.](../media/data_classification_export_control.png)


> [!NOTE]
> Det kan tage op til *syv dage* , før optællinger opdateres i Indholdsoversigt.

### <a name="filter"></a>Filter

Når du foretager detailudledning på en placering, f.eks. en Exchange eller en Teams mappe eller et SharePoint eller OneDrive websted, **vises filterværktøjet**.

![søgeværktøjet indholdsoversigt.](../media/data_classification_search_tool.png)

Søgeværktøjets område er det, der vises i ruden **Alle placeringer,** og det, du kan søge efter, varierer afhængigt af den valgte placering. 

Når **Exchange** eller **Teams** er den valgte placering, kan du søge efter den fulde mailadresse for postkassen, f.eks`user@domainname.com`. .

Når enten **SharePoint** eller **OneDrive** er valgt, vises søgeværktøjet, når du foretager detailudledning til webstedsnavne, mapper og filer. 

Du kan søge på:

|Værdi|Eksempel  |
|---------|---------|
|fuldt webstedsnavn    |`https://contoso.onmicrosoft.com/sites/sitename`    |
|filnavn    |    `RES_Resume_1234.txt`     |
|tekst i starten af filnavnet| `RES`|
|tekst efter et understregningstegn ( _) i filnavnet|`Resume` Eller `1234`| 
|filtypenavn|`txt`|


## <a name="see-also"></a>Se også

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)
- [Objekt af typen følsomme oplysninger definitions.md](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)
