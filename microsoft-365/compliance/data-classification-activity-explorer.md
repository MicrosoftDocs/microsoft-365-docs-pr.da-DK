---
title: Introduktion til Aktivitetsstifinder
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Med Aktivitetsstifinder kan du se og filtrere de handlinger, som brugerne laver på dit navnerede indhold.
ms.openlocfilehash: 93cd3910a79b136d95ba46fa79940d379340cf75
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63587756"
---
# <a name="get-started-with-activity-explorer"></a>Introduktion til Aktivitetsstifinder

[Dataklassificeringsoversigten](data-classification-overview.md) og fanerne med indholdsstifinder giver dig overblik over, hvilket indhold der er blevet fundet og mærket, og hvor indholdet er.[](data-classification-content-explorer.md) Aktivitetsstifinder afrunder denne funktionspakke ved at give dig mulighed for at overvåge, hvad der bliver gjort med dit mærkede indhold. Aktivitetsstifinder giver en historisk visning af aktiviteter på dit mærkede indhold. Aktivitetsoplysningerne indsamles fra Microsoft 365 samlede overvågningslogfiler, transformeres og gøres tilgængelige i brugergrænsefladen i Aktivitetsoversigt. Aktivitetsstifinder rapporterer om data for op til 30 dage.

![Pladsholder skærmbillede oversigt aktivitetsstifinder.](../media/data-classification-activity-explorer-1.png)

Der er mere end 30 forskellige filtre tilgængelige til brug, nogle er:

- Datointerval
- Aktivitetstype
- Placering
- Bruger
- Følsomhedsmærkat
- Opbevaringsmærkat
- Filsti
- DLP-politik



## <a name="prerequisites"></a>Forudsætninger

Alle konti, der tilgås og bruger dataklassificering, skal have en licens tildelt fra et af disse abonnementer:

- Microsoft 365 (E5)
- Office 365 (E5)
- Tilføjelsesprogrammet Avanceret overholdelse af regler og standarder (E5)
- Avanceret tilføjelsesprogrammet Threat Intelligence (E5)
- Microsoft 365 E5/A5 Info Protection & styring
- Microsoft 365 E5/A5-overholdelse

### <a name="permissions"></a>Tilladelser

En konto skal eksplicit være tildelt medlemskab i en af disse rollegrupper eller udtrykkeligt tildeles rollen.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at vide om [dette under Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365 rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder

**Microsoft 365 roller**

- Overholdelsesadministrator
- Sikkerhedsadministrator
- Sikkerhedslæser

## <a name="activity-types"></a>Aktivitetstyper

Aktivitetsstifinder indsamler aktivitetsoplysninger fra overvågningslogfilerne på flere aktivitetskilder. Hvis du vil have mere detaljerede oplysninger om, hvilken etiketaktivitet, der gør den til Aktivitetsstifinder, skal du se [Mærkathændelser, der er tilgængelige i Aktivitetsoversigt](data-classification-activity-explorer-available-events.md).

**Følsomhedsmærkataktiviteter** og opbevaringsetiketaktiviteter fra Office oprindelige programmer, tilføjelsesprogrammet Azure Information Protection, SharePoint Online, Exchange Online (kun følsomhedsmærkater) og OneDrive. Her er nogle eksempler:

- Anvendt etiket
- Navnet er ændret (opgraderet, nedgraderet eller fjernet)
- Automatisk simulering
- Filen er læst

**Azure Information Protection-scanner og AIP-klienter**

- Beskyttelse anvendt
- Beskyttelse er ændret
- Beskyttelse er fjernet
- Fundne filer

Aktivitetsstifinder indsamler også **DLP-politikken**, der svarer til begivenheder fra Exchange Online, SharePoint Online, OneDrive, Teams-chat og -kanal (forhåndsvisning), lokale SharePoint-mapper og -biblioteker samt lokale filshares og Windows 10-enheder via **Forebyggelse af datatab på slutpunkter (DLP)**. Nogle eksempler på hændelser fra Windows 10 enheder er filer:

- Sletninger
- Oprettelser
- Kopieret til Udklipsholder
- Ændret
- Læs
- Udskrevet
- Omdøbt
- Kopieret til netværksshare
- App, der ikke er tilladt, tilgås 

Når du forstår, hvilke handlinger der foretages med dit følsomme, etikette indhold, kan du se, om de kontrolelementer, du har [](dlp-learn-about-dlp.md) på plads, f.eks. politikker til forebyggelse af datatab, er effektive eller ej. Hvis ikke, eller hvis du opdager noget uventet, `highly confidential` `general`f.eks. et stort antal elementer, der er mærket og nedgraderet , kan du administrere dine forskellige politikker og udføre nye handlinger for at begrænse den uønskede funktionsmåde.

> [!NOTE]
> Aktivitetsstifinder overvåger i øjeblikket ikke opbevaringsaktiviteter for Exchange Online.

## <a name="see-also"></a>Se også

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md)
- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md)
- [Få mere at vide om dataklassificering](data-classification-overview.md)
