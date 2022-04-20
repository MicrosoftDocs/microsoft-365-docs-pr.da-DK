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
description: Har du brug for en datastyringsløsning til Microsoft 365, der administrerer indhold af høj værdi for juridiske, forretningsmæssige eller lovmæssige forpligtelser, men er du ikke sikker på, hvor du skal starte? Læs nogle praktiske retningslinjer for at komme i gang.
ms.openlocfilehash: 02c16f9d1a9d42f59cf8bc27bdee38bcc2d10d73
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911384"
---
# <a name="get-started-with-records-management"></a>Kom i gang med datastyring

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Er du klar til at begynde at administrere din organisations indhold af høj værdi for juridiske, forretningsmæssige eller lovmæssige forpligtelser ved hjælp af en løsning til datastyring i Microsoft 365? Brug følgende vejledning til at komme i gang:

1. **Forstå, hvordan opbevaring og sletning fungerer** i Microsoft 365, og identificer, om du skal bruge opbevaringspolitikker til at supplere opbevaringsmærkater, der administrerer dokumenter og mails på elementniveau: [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)
    
    Hvis det er nødvendigt, [kan du oprette opbevaringspolitikker](create-retention-policies.md) for grundlæggende styring af data på tværs af Microsoft 365 arbejdsbelastninger.
    
2. **Forstå løsningen til datastyring** , og hvordan opbevaringsmærkater kan bruges til at tillade eller blokere handlinger, når dokumenter og mails erklæres som poster: [Få mere at vide om datastyring](records-management.md)

3. **Opret din filplan til indstillinger og handlinger for opbevaring og sletning, og når elementer skal markeres som poster** ved at importere en eksisterende plan, hvis du har en, eller opret nye opbevaringsmærkater: [Brug filplanen til at oprette og administrere opbevaringsmærkater](file-plan-manager.md)

4. **Publicer og anvend dine opbevaringsmærkater**. Opbevaringsmærkater kan genbruges som dokumentkomponenter, der kan bruges i flere politikker og kan inkorporeres i brugerarbejdsprocesser:

    - [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
    - [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)

Uafhængigt af disse trin **skal du bruge connectors til at importere og arkivere tredjepartsdata** , der omfatter data fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde. Når disse data importeres til onlinepostkasser, understøtter de ikke kun dataadministration fra Microsoft 365 Overholdelse, men også andre løsninger til overholdelse af angivne standarder, f.eks. overholdelse af angivne standarder for kommunikation, styring af insiderrisiko og eDiscovery. Du kan finde flere oplysninger under [Få mere at vide om forbindelser til tredjepartsdata](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Abonnements- og licenskrav

En række forskellige abonnementer understøtter datastyring, og licenskravene for brugere afhænger af de funktioner, du bruger.

Hvis du vil se mulighederne for at licensere dine brugere, så de kan drage fordel af Microsoft 365 overholdelsesfunktioner, skal du se [Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Hvis du vil have administration af poster, skal du se afsnittet [Datastyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) og relateret PDF-download for at få licenskrav på funktionsniveau.

## <a name="permissions"></a>Tilladelser

Medlemmer af dit overholdelsesteam, der er ansvarlige for datastyring, skal have tilladelser til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>. Lejeradministratoren (global administrator) har som standard adgang til denne placering og kan give overholdelsesansvarlige og andre personer adgang uden at give dem alle tilladelserne for en lejeradministrator. Hvis du vil give tilladelser til denne begrænsede administration, anbefaler vi, at du føjer brugere til rollegruppen **Administration af datastyring** , som giver tilladelser til alle funktioner, der er relateret til datastyring, herunder [dispositionsgennemsyn og bekræftelse](disposition.md).

For en skrivebeskyttet rolle kan du oprette en ny rollegruppe og føje rollen **Vis kun postadministration** til denne gruppe.

Du kan finde oplysninger om, hvordan du føjer brugere til standardrollerne eller opretter dine egne rollegrupper, [under Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md).

Disse tilladelser kræves kun for at oprette, konfigurere og anvende opbevaringsmærkater, der deklarerer poster og administrerer disposition. Den person, der konfigurerer disse mærkater, kræver ikke adgang til indholdet.

## <a name="common-scenarios"></a>Almindelige scenarier

Brug følgende tabel som en hjælp til at knytte dine forretningskrav til de scenarier, der understøttes af datastyring.

> [!TIP]
> Har du brug for at overholde en specifik branchelovgivning? Se [Lovmæssige krav til styring af oplysninger og datastyring](retention-regulatory-requirements.md) for at få en regelspecifik vejledning.

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Deklarer en post |[Erklær data ved hjælp af opbevaringsmærkater](declare-records.md)|
|Opdater en post |[Brug postversionsstyring til at opdatere poster, der er gemt i SharePoint eller OneDrive](record-versioning.md)|
|Lad administratorer og brugere anvende bevarelses- og slettehandlinger manuelt for dokumenter og mails: <br />- SharePoint <br />- OneDrive <br />- Outlook og Outlook på internettet|[Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad webstedsadministratorer angive standardhandlinger til bevarelse og sletning af alt indhold i et SharePoint bibliotek, en mappe eller et dokumentsæt|[Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad brugerne automatisk anvende bevarelses- og sletningshandlinger på mails ved hjælp af Outlook regler|[Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)|
|Lad administratorer anvende bevarelses- og sletningshandlinger på en model til dokumentforståelse, så disse automatisk anvendes på identificerede dokumenter i et SharePoint bibliotek|[Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)|
|Anvend automatisk bevarelses- og sletningshandlinger på dokumenter og mails |[Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)|
|Start opbevaringsperioden, når der opstår en hændelse, f.eks.:  <br />- Medarbejdere forlader organisationen <br />- Kontrakterne udløber <br />- Produktets levetid ophører| [Start opbevaring, når der opstår en hændelse](event-driven-retention.md)|
|Begræns ændringer af politikker for at hjælpe med at opfylde lovmæssige krav eller beskytte mod rogue-administratorer| [Brug Bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md)
|Administrer livscyklussen for forskellige dokumenttyper i SharePoint| [Brug opbevaringsmærkater til at administrere livscyklussen for dokumenter, der er gemt i SharePoint](auto-apply-retention-labels-scenario.md)|
|Sørg for, at nogen gennemser og godkender, før indholdet slettes i slutningen af opbevaringsperioden|[Dispositionsgennemgange](disposition.md#disposition-reviews) |
|Hav bevis for fordeling for indhold, der slettes permanent ved slutningen af opbevaringsperioden|[Fordeling af poster](disposition.md#disposition-of-records) |
| Overvåg, hvordan og hvor indstillinger for bevarelse og sletning anvendes på elementer | [Overvågning af opbevaringsmærkater](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

Hvis du bruger opbevaringspolitikker til styring af grundlæggende data, fungerer de typisk diskret i baggrunden uden brugerinteraktion. Derfor har de kun brug for lidt dokumentation til brugerne. Opbevaringspolitikker for Teams informere brugerne, når deres meddelelser er blevet slettet, med et link til [Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Til sammenligning har opbevaringsmærkater en brugergrænseflade tilstedeværelse i Microsoft 365 apps, så sørg for at give vejledning til slutbrugere og din helpdesk, før disse mærkater udrulles til dit produktionsnetværk. Hvis du vil hjælpe brugerne med at anvende opbevaringsmærkater i SharePoint og OneDrive og oplysninger om oplåsning af poster til redigering, skal du se [Anvend opbevaringsmærkater på filer i SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Den mest effektive dokumentation til slutbrugere vil dog være tilpasset vejledning og instruktioner, du angiver for de navne og konfigurationer for opbevaringsmærkater, du vælger. Se følgende side og downloads, som du kan bruge til at hjælpe med at oplære dine brugere: [Slutbrugeruddannelse for opbevaringsmærkater](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
