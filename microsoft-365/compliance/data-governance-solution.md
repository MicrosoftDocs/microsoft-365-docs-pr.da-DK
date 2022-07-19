---
title: Udrul en datastyringsløsning
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365solution-overview
- m365solution-mig
- m365initiative-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Præskriptive vejledning til installation af Microsoft Purview, så din organisation kan styre dine data i forhold til overholdelse af angivne standarder eller lovmæssige krav.
ms.openlocfilehash: fbfc208a860b8f062b424912207718ece2055b3b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66858924"
---
# <a name="deploy-a-data-governance-solution-with-microsoft-purview"></a>Udrul en løsning til datastyring med Microsoft Purview

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug **Administration af Microsoft Purview-datalivscyklus** (tidligere Microsoft Information Governance) og **Microsoft Purview-datastyring** til at styre dine Microsoft 365-data til overholdelse af angivne standarder eller lovmæssige krav.

![Oversigt over trin til installation af en løsning til datastyring med Microsoft Purview](../media/data-governance-solution-overview.png)

I forbindelse med datastyring, der tilknytter og administrerer data på tværs af dit dataområde, herunder multicloud og SaaS (software-as-a-service), skal du bruge [Microsoft Purview Data Map, Microsoft Purview Data Catalog og Microsoft Purview Data Estate Insights](/azure/purview/overview).

Hvis du vil have en databeskyttelsesløsning, skal [du se Installér en løsning til beskyttelse af oplysninger med Microsoft Purview](information-protection-solution.md).

## <a name="licensing"></a>Licensering

Du kan få mere at vide om dine licenskrav og -muligheder i følgende afsnit i [dokumentationen til Microsoft 365-licenser](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Administration af Microsoft Purview-datalivscyklus](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [Microsoft Purview-datastyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

Eventuelle yderligere licenskrav inkluderes i dokumentationens instruktioner. Licenser, der er specifikke for administration af postkasser, kan f.eks. kræve licenser fra Exchange Online.

## <a name="keep-what-you-need-and-delete-what-you-dont"></a>Behold det, du har brug for, og slet det, du ikke har brug for

![Trin til løsning til administration af datalivscyklus](../media/data-lifecycle-management-solution.png)

Brug **Administration af Microsoft Purview-datalivscyklus** (tidligere Microsoft Information Governance) til at beholde det, du har brug for, og slette det, du ikke har brug for.

|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1| Forstå, hvordan opbevaring og sletning fungerer for Microsoft 365-tjenester. <br /><br /> Når du har forstået, hvordan du kan bruge opbevaringspolitikker og opbevaringsmærkater, skal du identificere dine arbejdsbelastninger, der har brug for en opbevaringspolitik, og om du har brug for at oprette opbevaringsmærkater for undtagelser. | [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)|
|2| Opret opbevaringspolitikker og om nødvendigt opbevaringsmærkater for undtagelser. <br /><br /> De mest anvendte opbevaringspolitikker er for Exchange, SharePoint, Teams, Microsoft 365-grupper og Yammer. Du kan konfigurere undtagelser for dokumenter og mails. | [Opret opbevaringspolitik](create-retention-policies.md) <p> [Opret og anvend opbevaringsmærkater for dine undtagelser](create-retention-labels-information-governance.md)|
|3| Administrer postkasser. <br /><br /> Aktivér postkasser til arkivering og automatisk udvidelse af arkivering, overvej, om du skal tilpasse, når mails flyttes til arkivpostkassen, og gøre postkasser inaktive, når brugere forlader organisationen.| [Aktivér arkivpostkasse](enable-archive-mailboxes.md) <p> [Aktivér automatisk udvidelse af arkiv](enable-autoexpanding-archiving.md) <p> [Opret og administrer inaktive postkasser](create-and-manage-inactive-mailboxes.md)|
|4| Importér PST-filer til onlinepostkasser.  <br /><br /> Hvis du har PST-filer, der indeholder data, du vil styre, kan du importere dem ved hjælp af netværksupload eller drevforsendelse.| [Brug netværksoverførsel til at importere din organisations PST-filer](use-network-upload-to-import-pst-files.md) <p> [Brug drevforsendelse til at importere din organisations PST-filer](use-drive-shipping-to-import-pst-files-to-office-365.md)|

Hvis du vil vide mere om funktionerne fra denne løsning, skal [du se Få mere at vide om administration af datalivscyklus](information-governance.md).

## <a name="manage-high-value-items"></a>Administrer elementer med høj værdi

![Trin til løsning til datastyring](../media/records-management-solution.png)

Brug **Microsoft Purview-datastyring** til at administrere organisationens vigtige elementer i forbindelse med forretningsrelaterede, juridiske eller lovmæssige krav til registrering.

|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1| Forstå løsningen til datastyring. <br /><br /> Brug opbevaringsmærkater med mere fleksible konfigurationsindstillinger, og deklarer elementer som poster, når det er nødvendigt. | [Få mere at vide om datastyring](records-management.md)|
|2| Brug filplanen til at administrere dine opbevaringsplaner. <br /><br /> Med filplanen kan du oprette opbevaringsmærkater interaktivt eller importere samlet og eksportere til analyse. Etiketter, du opretter med filplanen, understøtter yderligere administrative oplysninger, der kan hjælpe dig med at identificere og spore forretningsmæssige eller lovmæssige krav. | [Brug filplanen til at oprette og administrere opbevaringsmærkater](file-plan-manager.md)|
|3| Anvend dine opbevaringsmærkater. <br /><br /> Dine opbevaringsmærkater kan publiceres og anvendes manuelt eller automatisk i apps eller automatisk anvendes på baggrund af følsomme oplysninger, nøgleord eller søgbare egenskaber, klassificeringer, der kan oplæres, eller vedhæftede filer i skyen. |[Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md) <p> [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)|
|4| Administrer permanent sletning af data. <br /><br /> Du kan kræve en manuel gennemgang af indholdet, før det slettes permanent, og du kan dokumentere, at dataene er blevet dispositionsbehandlet. |[Administrer indholdsdisposition](disposition.md)|

> [!TIP]
> Se listen over [almindelige scenarier](get-started-with-records-management.md#common-scenarios) for yderligere konfigurationer, der understøttes af datastyring.

Hvis du vil vide mere om funktionerne fra denne løsning, skal [du se Få mere at vide om datastyring](records-management.md).

## <a name="training-resources"></a>Oplæringsressourcer

Læringsmoduler til konsulenter og administratorer:

- [Introduktion til beskyttelse af oplysninger og administration af datalivscyklus i Microsoft Purview](/learn/modules/m365-compliance-information-governance)
- [Administrer datalivscyklussen i Microsoft Purview](/learn/modules/m365-compliance-information-govern-information/)
- [Administrer poster i Microsoft Purview](/learn/modules/m365-compliance-information-manage-records/)

Du kan finde dokumentation, der understøtter brugere, når disse løsninger udrulles, i dokumentationen til slutbrugere i afsnittet om [administration af datalivscyklus](get-started-with-information-governance.md#end-user-documentation) og [datastyring](get-started-with-records-management.md#end-user-documentation).