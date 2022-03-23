---
title: Microsoft Information Governance i Microsoft 365
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
description: Implementer Microsoft Information Governance-funktioner for at styre dine data i forbindelse med overholdelse eller lovmæssige krav.
ms.openlocfilehash: b99d073817dc0ef899f448fb6a21619b08806759
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63588751"
---
# <a name="microsoft-information-governance-in-microsoft-365"></a>Microsoft Information Governance i Microsoft 365

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug Microsofts funktioner til informationsstyring (nogle gange forkortet til MIG) til at styre dine data til overholdelse af regler eller lovkrav.

Fra et [licensperspektiv kan](#licensing-requirements) der være betydelige overlap mellem informationsstyring, datastyring og dataforbindelser. Alle tre områder understøtter opbevaring og sletning af data Microsoft 365. Forbindelser bruges af andre løsninger til overholdelse end informationsstyring og datastyring. 

Brug følgende grafik som en hjælp til at identificere de vigtigste konfigurerbare komponenter til disse tre forskellige løsninger, som hver har deres egen node i overholdelsescenteret:

![Hovedkomponenter til administration af Microsoft Information Goevernance.](../media/information-governance-components.png)

Vil du beskytte dine data? Se [Microsoft Information Protection i Microsoft 365](information-protection.md).

## <a name="information-governance"></a>Styring af oplysninger

Sådan beholder du det, du har brug for, og sletter det, du ikke har brug for:
 
|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|:--------------------|:-----------------------------|
|[Opbevaringspolitikker for Microsoft 365 arbejdsbelastninger med opbevaringsetiketter for undtagelser](retention.md) | Bevare eller slette indhold med politikstyring for mail, dokumenter, Teams og Yammer meddelelser | [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md) <br /><br /> [Oprette opbevaringsnavne for undtagelser til dine opbevaringspolitikker](create-retention-labels-information-governance.md)|
|[Arkivpostkasser](archive-mailboxes.md)| Giver brugerne yderligere lagerplads til postkasse | [Aktivere arkivpostkasser](enable-archive-mailboxes.md) |
|[Inaktive postkasser](inactive-mailboxes-in-office-365.md)| Behold postkasseindhold, når medarbejdere forlader organisationen, så dette indhold forbliver tilgængeligt for administratorer, compliance officers og dataledere | [Oprette og administrere inaktive postkasser](create-and-manage-inactive-mailboxes.md)|
|[Importér tjeneste til PST-filer](importing-pst-files-to-office-365.md)| Masseimport af PST-filer til Exchange Online postkasser for at bevare og søge i mails efter overholdelse eller lovmæssige krav | [Brug netværksupload til at importere din organisations PST-filer Microsoft 365](use-network-upload-to-import-pst-files.md)|

## <a name="records-management"></a>Datastyring

Administration af livscyklus for elementer af høj værdi for juridiske, forretningsmæssige eller lovgivningsmæssige forpligtelser:

|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|---------------------|:----------------------------|
|[Datastyring](records-management.md)| En enkelt løsning til mail og dokumenter, der indeholder fleksible tidsplaner og krav til opbevaring og sletning, så dit indholds fulde livscyklus understøttes med dataerklæring og disposition, når det er nødvendigt |[Introduktion til datastyring](get-started-with-records-management.md) |

## <a name="connectors-for-third-party-data"></a>Forbindelser til tredjepartsdata

Udvid dine overholdelsesværktøjer til importerede og arkiverede tredjepartsdata fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde:

|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|:--------------------|:-----------------------------|
|[Dataforbindelser](archiving-third-party-data.md)| Importere, arkivere og anvende overholdelsesløsninger til tredjepartsdata fra sociale medieplatforme, chatplatforme og dokumentsamarbejdsplatforme| [Tredjepartsforbindelser](archiving-third-party-data.md#third-party-data-connectors)|

## <a name="licensing-requirements"></a>Licenskrav

Licenskrav til Microsoft Information Governance afhænger af de scenarier og funktioner, du bruger, i stedet for at angive licenskrav for hver funktionalitet, der er angivet på denne side. Hvis du vil have mere at vide om dine licenskrav og -indstillinger, skal du se de [følgende afsnit Microsoft 365 dokumentationen over licenser](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Information Governance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) 
- [Datastyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) 
- [Dataforbindelser](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-connectors)

Eventuelle yderligere licenskrav medtages i dokumentationsvejledningen. Licenser, der er specifikke for administration af postkasser, kan f.eks. kræve licenser Exchange Online.

