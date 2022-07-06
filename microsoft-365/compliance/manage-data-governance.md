---
title: Administration af Microsoft Purview-datalivscyklus & Microsoft Purview-datastyring
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
recommendations: false
description: Implementer funktioner fra Administration af Microsoft Purview-datalivscyklus & Microsoft Purview-datastyring for at styre dine data i forhold til overholdelse af angivne standarder eller lovmæssige krav.
ms.openlocfilehash: 7578aad4bdbb44bf0937a58343fc05462449688f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635979"
---
# <a name="govern-your-data-with-microsoft-purview"></a>Styr dine data med Microsoft Purview

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug funktionerne fra **Administration af Microsoft Purview-datalivscyklus** (tidligere Microsoft Information Governance) og **Microsoft Purview-datastyring** til at styre dine data for overholdelse af angivne standarder eller lovmæssige krav.

> [!TIP]
> Ønsker du at kortlægge og administrere dine data på tværs af hele dit dataområde, herunder multi-cloud og SaaS (software-as-a-service)? Brug [Microsoft Purview Data Map, Microsoft Purview Data Catalog og Microsoft Purview Data Estate Insights](/azure/purview/overview).

Fra et [licensperspektiv](#licensing-requirements) kan der være betydelig overlapning mellem administration af datalivscyklusser og datastyring. Begge løsninger understøtter opbevaring og sletning af data til Microsoft 365-apps og -tjenester.

Brug følgende grafik som en hjælp til at identificere de hovedkomponenter, der kan konfigureres, for disse løsninger, som hver især har deres eget konfigurationsområde i Microsoft Purview-compliance-portal:

![Hovedkomponenter, der skal konfigureres og bruges til at styre dine data med Microsoft Purview.](../media/govern-your-data.png)

I følgende afsnit beskrives de primære funktioner for hver løsning med links, der kan bruges til at forstå mere. Men hvis du leder efter en guidet installation, skal du se [Installér en løsning til datastyring med Microsoft Purview](data-governance-solution.md).

Leder du efter supplerende funktioner til beskyttelse af dine data? Se [Beskyt dine data med Microsoft Purview](information-protection.md).

## <a name="microsoft-purview-data-lifecycle-management"></a>Administration af Microsoft Purview-datalivscyklus

Sådan beholder du det, du har brug for, og sletter det, du ikke har brug for:
 
|Kapacitet|Hvilke problemer løser det?|
|:------|:------------|:----------------|
|[Opbevaringspolitikker for Microsoft 365-arbejdsbelastninger med opbevaringsmærkater for undtagelser](retention.md) | Giver dig mulighed for at bevare eller slette indhold med politikstyring for mail, dokumenter, Teams og Yammer-meddelelser. |
|[Inaktive postkasser](inactive-mailboxes-in-office-365.md)| Giver dig mulighed for at bevare postkasseindhold, når medarbejdere forlader organisationen, så dette indhold forbliver tilgængeligt for administratorer, overholdelsesansvarlige og dataadministratorer. |
|[Arkivpostkasser](archive-mailboxes.md)| Giver brugerne yderligere lagerplads på postkassen.|
|[Importér tjeneste for PST-filer](importing-pst-files-to-office-365.md)| Understøtter masseimport af PST-filer til Exchange Online postkasser for at bevare og søge i mails efter overholdelse af angivne standarder eller lovmæssige krav. |

Vil du vide mere? Se [Få mere at vide om administration af datalivscyklus](data-lifecycle-management.md).

Er du klar til at begynde at bruge nogle af eller alle disse funktioner? Se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).


## <a name="microsoft-purview-records-management"></a>Microsoft Purview-datastyring

Administrer elementer af høj værdi for forretnings-, juridiske eller lovmæssige krav til registrering:

|Kapacitet|Hvilke problemer løser det?|
|:---------|:---------------------------|
|[Filplan](file-plan-manager.md)| Gør det muligt at oprette opbevaringsmærkater interaktivt eller importere samlet og eksportere til analyse. Mærkater understøtter yderligere administrative oplysninger (valgfrit) for at hjælpe dig med at identificere og spore forretningsmæssige eller lovmæssige krav. |
|[Opbevaringsmærkater for individuelle elementer, opbevaringspolitikker, hvis det er nødvendigt for oprindelig opbevaring](retention.md)| Mærkater understøtter fleksible opbevarings- og sletningsplaner, der kan anvendes manuelt eller automatisk, med definition af poster, når det er nødvendigt. |
|[Gennemgang af fordeling og bevis for fordeling](disposition.md)| Manuel gennemgang af indhold, før det slettes permanent, med bevis for fordeling af poster.|

Vil du vide mere? Se [Få mere at vide om datastyring](records-management.md).

Er du klar til at begynde at bruge nogle af eller alle disse funktioner? Se [Kom i gang med datastyring](get-started-with-records-management.md).


## <a name="licensing-requirements"></a>Licenskrav

Du kan få mere at vide om dine licenskrav og -muligheder i følgende afsnit i [dokumentationen til Microsoft 365-licenser](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Administration af Microsoft Purview-datalivscyklus](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [Microsoft Purview-datastyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

Eventuelle yderligere licenskrav inkluderes i dokumentationens instruktioner. Licenser, der er specifikke for administration af postkasser, kan f.eks. kræve licenser fra Exchange Online.