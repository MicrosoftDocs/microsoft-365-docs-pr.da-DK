---
title: Kom i gang med administration af datalivscyklus
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
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Er du klar til at begynde at styre din organisations data, men er du ikke sikker på, hvor du skal starte? Læs nogle præskriptive retningslinjer for at komme i gang.
ms.openlocfilehash: c5b9e931e2ab822a4d888b775de9fb8fa2acb13b
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972359"
---
# <a name="get-started-with-data-lifecycle-management"></a>Kom i gang med administration af datalivscyklus

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Er du klar til at begynde at styre din organisations data ved at bevare det indhold, du skal beholde, og slette det indhold, du ikke har? Du kommer i gang ved at bruge følgende vejledning til Administration af Microsoft Purview-datalivscyklus (tidligere Microsoft Information Governance):

1. **Forstå, hvordan opbevaring og sletning fungerer** i Microsoft 365, og identificer derefter de arbejdsbelastninger, der skal bruge en opbevaringspolitik, og om du har brug for at oprette opbevaringsmærkater for undtagelser: [Få mere at vide om opbevaring](retention.md)
    
    > [!NOTE]
    > Hvis du har brug for at administrere elementer af høj værdi for forretningsrelaterede, juridiske eller lovmæssige krav til registrering: Brug opbevaringsmærkater med [datastyring](records-management.md) i stedet for administration af datalivscyklus.

2. **Opret opbevaringspolitikker** for de arbejdsbelastninger, du har identificeret, og angiv opbevaringsindstillinger og handlinger, der kræves af organisationens politikker eller brancheregler: [Opret opbevaringspolitikker](create-retention-policies.md)
    
    Hvis det er nødvendigt, [kan du oprette og anvende opbevaringsmærkater for dine undtagelser](create-retention-labels-information-governance.md).

3. **Aktivér arkivering af postkasser** for at give brugere ekstra lagerplads på postkasser: [Aktivér arkivpostkasser på Microsoft Purview-overholdelsesportalen](enable-archive-mailboxes.md)
    
    Hvis det er nødvendigt for at understøtte arkivpostkasser:
    
    - [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md) for postkasser, der har brug for mere end 100 GB lagerplads.
    
    - Brug [opbevaringskoder med en opbevaringspolitik fra administration af meddelelsesposter,](set-up-an-archive-and-deletion-policy-for-mailboxes.md) hvis du har brug for at tilpasse, hvordan mails automatisk flyttes fra en brugers primære postkasse til deres arkivpostkasse, eller hvis du har brug for at angive indstillinger for opbevaring og sletning for bestemte mapper i stedet for hele postkassen.

4. **Forstå og administrer inaktive postkasser** , der bevarer postkasseindhold, når medarbejdere forlader organisationen: [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md)

5. Hvis du har PST-filer, der indeholder data, du vil styre: **Importér PST-filer til onlinepostkasser** ved hjælp af netværksoverførsel eller -drevforsendelse: [Få mere at vide om import af din organisations PST-filer](importing-pst-files-to-office-365.md)

## <a name="subscription-and-licensing-requirements"></a>Abonnements- og licenskrav

En række forskellige abonnementer understøtter funktioner til administration af datalivscyklus.

Hvis du vil se indstillingerne for licensering af dine brugere, så de kan drage fordel af Microsoft Purview-funktioner, skal du se [Microsoft 365 licensvejledning for at få oplysninger om sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Du kan se de funktioner, der er angivet på denne side, i afsnittet [Administration af Microsoft Purview-datalivscyklus](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management) og relateret [PDF-download](https://go.microsoft.com/fwlink/?linkid=2139145) for at få licenskrav til funktioner.

## <a name="permissions"></a>Tilladelser

Se følgende afsnit for at få oplysninger om roller og rollegrupper til administration af Microsoft 365 opbevaring.

Hvis du vil have tilladelse til at administrere postkasser til arkivering, inaktive postkasser og import, kræver disse typisk Exchange tilladelser, f.eks. rollen Postmodtagere. Denne rolle tildeles som standard til rollegrupperne Modtageradministration og Organisationsadministration. Du kan finde de nøjagtige tilladelseskrav for hver administrationsopgave i den dokumentation, der følger med administratorvejledningen.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Tilladelser til opbevaringspolitikker og opbevaringsmærkater

Medlemmer af dit overholdelsesteam, der skal oprette og administrere opbevaringspolitikker og opbevaringsmærkater, skal have tilladelser til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>. Lejeradministratoren (global administrator) har som standard adgang til denne placering og kan give overholdelsesansvarlige og andre personer adgang uden at give dem alle tilladelserne for en lejeradministrator. Hvis du vil tildele tilladelser til denne begrænsede administration, anbefaler vi, at du føjer brugere til rollegruppen **Administrator af overholdelse** .

Hvis du vil bruge denne standardrolle, kan du oprette en ny rollegruppe og føje rollen **Opbevaringsstyring** til denne gruppe. Hvis du vil have en skrivebeskyttet rolle, skal du bruge **Visnings kun opbevaringsstyring**. 

Du kan finde oplysninger om, hvordan du føjer brugere til standardrollerne eller opretter dine egne rollegrupper, [under Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md).

Disse tilladelser kræves kun for at oprette, konfigurere og anvende opbevaringspolitikker og opbevaringsmærkater. Den person, der konfigurerer disse politikker og mærkater, kræver ikke adgang til indholdet.

## <a name="common-scenarios"></a>Almindelige scenarier

Brug følgende tabel til at hjælpe dig med at knytte dine forretningskrav til de mest almindelige scenarier for administration af datalivscyklus.

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Gem eller slet data effektivt for Microsoft 365-tjenester: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Microsoft 365-grupper <br />- Teams <br />- Yammer <br />- Skype for Business |[Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)|
|Giv brugerne ekstra postkasselager |[Aktivér arkivpostkasser på Microsoft Purview-overholdelsesportalen](enable-archive-mailboxes.md)|
|Bevar postkassedata, når medarbejdere forlader organisationen |[Opret og administrer inaktive postkasser](create-and-manage-inactive-mailboxes.md)|
|Upload postkassedata fra PST-filer |[Brug netværksupload til at importere PST-filer](use-network-upload-to-import-pst-files.md)|


Hvis du har et scenarie, der kræver dataadministration af individuelle elementer, kan du se de [almindelige scenarier for datastyring](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

Se følgende afsnit for at få oplysninger om slutbrugerdokumentation til understøttelse af Microsoft 365 opbevaring.

De funktioner til administration af datalivscyklus, der understøtter administration af postkasser (arkivering, inaktive postkasser og import), kræver normalt ikke dokumentation fra slutbrugeren.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Slutbrugerdokumentation til opbevaring og sletning

De fleste opbevaringspolitikker fungerer diskret i baggrunden uden brugerinteraktion og har derfor kun lidt dokumentation til brugerne. Opbevaringspolitikker for Teams informere brugerne, når deres meddelelser er blevet slettet, med et link til [Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Men hvis du supplerer opbevaringspolitikker med opbevaringsmærkater, har disse mærkater en tilstedeværelse af brugergrænsefladen i Microsoft 365 apps. Før du installerer disse mærkater på dit produktionsnetværk, skal du sørge for at angive oplysninger og instruktioner til slutbrugerne og din helpdesk. Hvis du vil hjælpe brugerne med at anvende opbevaringsmærkater i SharePoint og OneDrive, skal du se [Anvend opbevaringsmærkater på filer i SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Den mest effektive dokumentation til slutbrugere vil altid være tilpasset vejledning og instruktioner, du angiver for de navne og konfigurationer for opbevaringsmærkater, du vælger. Se følgende side og downloads, som du kan bruge til at hjælpe med at oplære dine brugere: [Slutbrugeruddannelse for opbevaringsmærkater](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

