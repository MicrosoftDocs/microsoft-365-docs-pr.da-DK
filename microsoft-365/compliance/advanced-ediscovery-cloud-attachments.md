---
title: Indsaml vedhæftede skybaserede filer Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Brug samlinger i Advanced eDiscovery til at indsamle vedhæftede skybaserede filer til gennemgang i en undersøgelse eller sag.
ms.openlocfilehash: bdf30fea0e168d4b36175296f524ade13539970b
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/22/2021
ms.locfileid: "63593008"
---
# <a name="collect-cloud-attachments-in-advanced-ediscovery-preview"></a>Indsaml vedhæftede filer fra skyen Advanced eDiscovery (eksempel)

Vedhæftede skybaserede filer er links til dokumenter, der typisk er gemt på SharePoint-websted OneDrive. Så i stedet for at vedhæfte en faktisk kopi af et dokument i en mail eller en Teams-chatsamtale, har du mulighed for at dele et link til filen. Vedhæftede skybaserede filer er en effektiv måde at dele dokumenter på og samarbejde med andre personer i organisationen. Men vedhæftede filer fra skyen er en udfordring under eDiscovery-arbejdsprocessen, fordi det kun er linket til vedhæftede filer i skyen og ikke selve indholdet i det delte dokument, der returneres i en eDiscovery-søgning. For at håndtere denne udfordring giver Advanced eDiscovery to løsninger til indsamling af vedhæftede filer i skyen:  

- Indsamling af den live version af et dokument, der er sammenkædet med i en vedhæftet skybaseret fil.

- Indsamling af versionen af dokumentet på det tidspunkt, hvor det blev delt, i en vedhæftet skybaseret fil.

## <a name="collecting-cloud-attachments"></a>Indsamling af vedhæftede filer i skyen

Når du opretter en kladdesamling, og søgeresultaterne indeholder elementer, der indeholder vedhæftede filer fra skyen, har du mulighed for at indsamle destinationen for den vedhæftede skybaserede fil, når du forpligter kladdesamlingen til et gennemsynssæt. Når du vælger denne indstilling, føjer Advanced eDiscovery de dokumenter, der er kædet til, i den vedhæftede skyen til korrektursættet. Dette giver dig mulighed for at gennemse destinationsdokumenterne og afgøre, om dokumentet er relevant for din sag eller undersøgelse.

Følgende skærmbillede viser muligheden for at medtage mål for vedhæftede filer i skyen, når du har bekræftet en samling i et gennemsynssæt.

![Muligheden for at medtage vedhæftede skybaserede filer, når du vedhæfter en samling i et korrektursæt](../media/CollectCloudAttachments1.png)

> [!NOTE]
>- Hvis du bruger det nye [caseformat](advanced-ediscovery-new-case-format.md) i Advanced eDiscovery, er indstillingen for at medtage vedhæftede skybaserede filer i korrektursættet valgt som standard og kan ikke fravælges.<br/>
>- Du har også mulighed for at medtage alle versioner (ud over den version, der blev delt) af vedhæftede skybaserede filer i korrektursættet.  
Hvis du vil have vejledning i at bekræfte en samling på et korrektursæt, skal [du se Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md).

## <a name="collecting-the-version-shared-in-a-cloud-attachment"></a>Indsamling af den version, der deles i en vedhæftet skybaseret fil

Arbejdsprocessen Advanced eDiscovery til indsamling af vedhæftede filer fra skyen omfatter kun tilføjelse af den nyeste version af en vedhæftet skyen til et korrektursæt. Det betyder, at den version, der indsamles og føjes til et korrektursæt, kan være en anden end den version, der oprindeligt blev delt i den vedhæftede skyversion. Det er derfor muligt, at det indhold, der var til stede i den vedhæftede sky på det tidspunkt, hvor det blev delt, er blevet fjernet og ikke findes i den aktuelle version, der er føjet til korrektursættet.

Organisationer har nu mulighed for at bruge Microsoft 365 opbevaringsnavne for at bevare versionen af et dokument på det tidspunkt, hvor det blev delt som en vedhæftet skybaseret fil. For at gøre dette kan din organisation oprette en opbevaringsmærkat, vælge indstillingen anvend navnet på vedhæftede skybaserede filer og derefter automatisk anvende navnet på dokumenter, der er gemt i SharePoint og OneDrive. Når du har konfigureret denne konfiguration, oprettes der en kopi af et dokument på det tidspunkt, hvor filen deles. Hvis dokumentet ændres og deles igen som en vedhæftet skybaseret fil, bevares den ændrede version også. Hvis filen redigeres og deles igen, bevares en ny kopi af filen som en ny version.

Bevaring af de delte versioner af vedhæftede filer i skyen kan hjælpe organisationen med at bevare og indsamle potentielt relevant indhold til den specifikke version af dokumentet, der blev delt, i stedet for den aktuelle liveversion. Når du implementerer denne opbevaringsløsning, indsamles både den aktuelle liveversion af en vedhæftet skyversion og den version, der blev delt i den vedhæftede skybaserede version, og de føjes til et gennemsynssæt.

Du kan finde en vejledning til konfiguration af en opbevaringsetiket og automatisk anvendelse af den på vedhæftede filer i skyen under [Anvend automatisk etiketter på vedhæftede filer i skyen](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments).

Følgende skærmbillede viser et vedhæftet dokument i skyen med navnet *XYZ Research.docx*, der blev føjet til et korrektursæt. Dokumentet blev delt som en vedhæftet skybaseret fil i Teams chatsamtale. Korrektursættet indeholder også den version, der oprindeligt blev delt i den vedhæftede sky. Bemærk, at navnet på denne version af den vedhæftede skybaserede fil genereres af systemet, og forfatteren identificeres **som SharePoint**.

![Versionen af en vedhæftet skybaseret fil, der blev delt, vises i et korrektursæt](../media/CollectCloudAttachments2.png)

Desuden har den aktuelle liveversion og den version, der blev delt, samme **FamilyId-egenskabsværdi**, hvilket er det samme som **FamilyId** for det overordnede objekt (f.eks. en mail eller en Teams-chatsamtale). Dette gør det muligt at gruppere vedhæftede filer i skyen med det element, som de blev delt i.

Når du har implementeret opbevaringsmærkaten og automatisk anvender etiketten på SharePoint-dokumenter, kan du stadig vælge at indsamle vedhæftede skybaserede filer, når du vedhæfter en kladde til et korrektursæt. Når vedhæftede filer fra skyen indsamles, føjes både den aktuelle liveversion og den version, der oprindeligt blev delt, til gennemsynssættet.
