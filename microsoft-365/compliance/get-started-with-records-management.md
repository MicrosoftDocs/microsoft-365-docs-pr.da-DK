---
title: Kom i gang med datastyring i Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Har du brug for en løsning til Microsoft 365 datastyring, der administrerer indhold med høj værdi for juridiske, forretningsmæssige eller lovmæssige forpligtelser, men ikke er sikker på, hvor du skal starte? Læs nogle praktiske vejledninger for at komme i gang.
ms.openlocfilehash: ba23aed20cbef05272bc33306df5fc1eebc6cb3f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63590621"
---
# <a name="get-started-with-records-management"></a>Introduktion til datastyring

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Er du klar til at begynde at administrere din organisations indhold af høj værdi for juridiske, forretningsmæssige eller lovmæssige forpligtelser ved hjælp af en datastyringsløsning Microsoft 365? Brug følgende vejledning for at komme i gang:

1. **Forstå,** hvordan opbevaring og sletning fungerer i Microsoft 365, og identificer, om du skal bruge opbevaringspolitikker som supplement til opbevaringsetiketter, der administrerer dokumenter og mails på elementniveau [: Få](retention.md) mere at vide om opbevaringspolitikker og opbevaringsetiketter
    
    Hvis det er nødvendigt, [kan du oprette opbevaringspolitikker](create-retention-policies.md) til styring af oprindelige planer for data på tværs Microsoft 365 arbejdsbelastninger.
    
2. **Forstå løsningen til datastyring,** og hvordan opbevaringsnavne kan bruges til at tillade eller blokere handlinger, når dokumenter og mails erklæres som poster: Få mere at vide [om datastyring](records-management.md)

3. **Opret din filplan for indstillinger og handlinger for** opbevaring og sletning, og hvornår elementer skal markeres som poster ved at importere en eksisterende plan, hvis du har en, eller oprette nye opbevaringsnavne [: Brug](file-plan-manager.md) filplan til at oprette og administrere opbevaringsnavne

4. **Publicere og anvende dine opbevaringsnavne**. Opbevaringsetiketter er dokumentkomponenter, der kan genbruges, som kan bruges i flere politikker og kan indarbejdes i brugerarbejdsprocesser:

    - [Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)
    - [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)

Uafhængigt af disse trin kan du bruge forbindelser til at importere og arkivere **tredjepartsdata** , der omfatter data fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde. Når disse data importeres til onlinepostkasser, understøtter det ikke kun datastyring fra Microsoft 365 Compliance, men også andre overholdelsesløsninger som f.eks. kommunikationsoverholdelse, insider-risikostyring og eDiscovery. Få mere at vide [under Få mere at vide om forbindelser til tredjepartsdata](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Abonnements- og licenskrav

En række forskellige abonnementer understøtter datastyring, og licenskravene for brugere afhænger af de funktioner, du bruger.

Hvis du vil se mulighederne for at licensere dine brugere til at drage fordel af Microsoft 365 overholdelsesfunktioner, skal du se [Microsoft 365 for sikkerheds- & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). For datastyring skal du se afsnittet [Datastyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) og relateret PDF-download for krav til licenser på funktionsniveau.

## <a name="permissions"></a>Tilladelser

Medlemmer af dit overholdelsesteam, der er ansvarlige for datastyring, skal have tilladelse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">til Microsoft 365 Overholdelsescenter</a>. Som standard har lejeradministratoren (global administrator) adgang til denne placering og kan give compliance officers og andre personer adgang uden at give dem alle tilladelser som lejeradministrator. Hvis du vil give tilladelser til denne begrænsede administration, anbefaler vi, at du føjer  brugere til rollegruppen datastyringsadministrator, som giver tilladelser til alle funktioner, der er relateret til datastyring, herunder [dispositionsgennemsyn og bekræftelse](disposition.md).

Hvis du har en skrivebeskyttet rolle, kan du oprette en ny rollegruppe og  føje poststyringsrollen skrivebeskyttet til denne gruppe.

Du kan finde en vejledning til at føje brugere til standardrollerne eller oprette dine egne [rollegrupper under Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md).

Disse tilladelser er kun nødvendige for at oprette, konfigurere og anvende opbevaringsetiketter, der erklære poster og administrere disposition. Den person, der konfigurerer disse etiketter, kræver ikke adgang til indholdet.

## <a name="common-scenarios"></a>Almindelige scenarier

Brug tabellen nedenfor som en hjælp til at kortlægge virksomhedens krav til de scenarier, der understøttes af datastyring.

> [!TIP]
> Skal du overholde en bestemt brancheforordningen? Kontrollér [lovmæssige krav til informationsstyring og datastyring](retention-regulatory-requirements.md) for at få en regelspecifik vejledning.

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Erklære en post |[Erklære poster ved hjælp af opbevaringsnavne](declare-records.md)|
|Opdatere en post |[Brug versionsversioner af poster til at opdatere poster, der er gemt i SharePoint eller OneDrive](record-versioning.md)|
|Lad administratorer og brugere anvende bevarelses- og sletningshandlinger for dokumenter og mails manuelt: <br />- SharePoint <br />- OneDrive <br />- Outlook og Outlook på internettet|[Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad webstedsadministratorer angive standardhandlinger for at bevare og slette alt indhold SharePoint et bibliotek, en mappe eller en dokumentsæt|[Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad brugere automatisk anvende bevarelses- og sletningshandlinger på mails ved hjælp Outlook regler|[Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad administratorer anvende bevarelses- og sletningshandlinger til en dokumentforståelsesmodel, så disse automatisk anvendes på identificerede dokumenter i SharePoint dokumentbibliotek|[Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)|
|Automatisk anvende bevarelses- og sletningshandlinger på dokumenter og mails |[Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)|
|Start opbevaringsperioden, når en hændelse forekommer, f.eks.:  <br />- Medarbejdere forlader organisationen <br />- Kontrakter udløber <br />- Slutningen af produktets levetid| [Start opbevaring, når en hændelse forekommer](event-driven-retention.md)|
|Begræns ændringer af politikker for at imødekomme lovmæssige krav eller beskytte administratorer mod administratorer| [Brug Preservation Lock til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md)
|Administrer livscyklussen for forskellige dokumenttyper i SharePoint| [Brug opbevaringsnavne til at administrere livscyklussen for dokumenter, der er gemt i SharePoint](auto-apply-retention-labels-scenario.md)|
|Sørg for, at nogen gennemser og godkender, før indhold slettes ved udløbet af dets opbevaringsperiode|[Dispositionsvurderinger](disposition.md#disposition-reviews) |
|Få dokumentation for disposition for indhold, der slettes permanent ved udløbet af dets opbevaringsperiode|[Disposition af poster](disposition.md#disposition-of-records) |
| Overvåge, hvordan og hvor indstillingerne for bevarelse og sletning anvendes på elementer | [Overvågning af opbevaringsnavne](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

Hvis du bruger opbevaringspolitikker til datastyring for oprindelige planer, fungerer de typisk diskret i baggrunden uden brugerinstruktiv. De skal derfor kun bruge lidt dokumentation til brugerne. Opbevaringspolitikker for Teams brugere, når deres meddelelser er blevet slettet, med et link til Teams [om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Til sammenligning har opbevaringsnavne en tilstedeværelse i brugergrænsefladen i Microsoft 365-apps, så sørg for at give vejledning til slutbrugere og din helpdesk, før disse etiketter installeres i produktionsnetværket. For at hjælpe brugerne med at anvende opbevaringsnavne i SharePoint og OneDrive samt oplysninger om at låse poster op til redigering, skal du se Anvend opbevaringsetiketter på filer [i SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Den mest effektive dokumentation til slutbrugeren vil dog blive tilpasset vejledning og vejledning, som du angiver for de opbevaringsetiketnavne og -konfigurationer, du vælger. Se følgende side og downloads, som du kan bruge til at hjælpe med at træne dine brugere: [Slutbrugerkurser i opbevaringsnavne](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
