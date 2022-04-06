---
title: Kom i gang med informationsstyring i Microsoft 365
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
description: Er du klar til at begynde at styre din organisations data, men er du ikke sikker på, hvor du skal starte? Læs nogle præskrivive vejledninger for at komme i gang.
ms.openlocfilehash: 5b30dc870389c06bd006a056127439f1ec18ac65
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63607443"
---
# <a name="get-started-with-information-governance"></a>Introduktion til informationsstyring

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Er du klar til at begynde at styre din organisations data ved at bevare det indhold, du vil beholde, og slette det indhold, du ikke har? Brug følgende vejledning for at komme i gang:

1. **Forstå, hvordan** opbevaring og sletning fungerer i Microsoft 365, og identificer derefter de arbejdsbelastninger, der skal bruge en opbevaringspolitik, og om du har brug for at oprette opbevaringsnavne for undtagelser: Få mere at vide om [opbevaring](retention.md)
    
    > [!NOTE]
    > Hvis du har brug for livscyklusstyring af elementer af høj værdi til forretningsmæssige, juridiske eller lovgivningsmæssige krav til registrering: Brug opbevaringsetiketter med datastyring [i stedet](records-management.md) for informationsstyring.

2. **Opret opbevaringspolitikker** for de arbejdsbelastninger, du har identificeret, og angiv opbevaringsindstillinger og handlinger, der kræves af organisationens politikker eller branchebestemmelser: [Opret opbevaringspolitikker](create-retention-policies.md)
    
    Hvis det er nødvendigt, [kan du oprette og anvende opbevaringsetiketter for dine undtagelser](create-retention-labels-information-governance.md).

3. **Aktivér postkassearkivering** for at give brugere yderligere lagerplads til postkassen: [Aktivér arkivpostkasser i overholdelsescenter](enable-archive-mailboxes.md)
    
    Hvis det er nødvendigt for at understøtte arkivpostkasser:
    
    - [Aktivér automatisk udvidende arkivering for](enable-autoexpanding-archiving.md) postkasser, hvor der skal være mere end 100 GB lagerplads.
    
    - Brug opbevaringsmærker med en opbevaringspolitik fra [MRM (messaging records management](set-up-an-archive-and-deletion-policy-for-mailboxes.md) ), hvis du har brug for at tilpasse, hvordan mails automatisk flyttes fra en brugers primære postkasse til deres arkivpostkasse, eller hvis du har brug for at angive indstillinger for opbevaring og sletning for bestemte mapper i stedet for hele postkassen.

4. **Forstå og administrer inaktive postkasser,** der bevarer postkasseindhold, når medarbejdere forlader organisationen: Få mere at vide [om inaktive postkasser](inactive-mailboxes-in-office-365.md)

5. Hvis du har PST-filer, der indeholder data, du vil styre: **Importér PST-filer til onlinepostkasser** ved hjælp af netværksupload eller drevforsendelse: Få mere at vide om at importere din organisations [PST-filer](importing-pst-files-to-office-365.md)

Uafhængigt af disse trin kan du bruge forbindelser til at importere og arkivere **tredjepartsdata** , der omfatter data fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde. Når disse data importeres til onlinepostkasser, understøtter de ikke kun informationsstyring fra Microsoft 365 Compliance, men også andre overholdelsesløsninger som f.eks. kommunikationsoverholdelse, insider-risikostyring og eDiscovery. Få mere at vide [under Få mere at vide om forbindelser til tredjepartsdata](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Abonnements- og licenskrav

En række forskellige abonnementer understøtter styring af oplysninger.

Hvis du vil se mulighederne for at licensere dine brugere til at drage fordel af Microsoft 365 overholdelsesfunktioner, skal du se [Microsoft 365 for sikkerheds- & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). For at se de funktioner, der er angivet på denne side, skal du se afsnittet [Information Governance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) og relateret [PDF-download](https://go.microsoft.com/fwlink/?linkid=2139145) for at få licenskrav på funktionsniveau.

## <a name="permissions"></a>Tilladelser

Se det følgende afsnit for at få oplysninger om roller og rollegrupper til at administrere Microsoft 365 opbevaring.

Hvis du vil have tilladelse til at administrere postkasser til arkivering, inaktive postkasser og til at importere, kræver disse typisk Exchange, f.eks. rollen Postmodtagere. Som standard er denne rolle tildelt rollegrupperne Modtageradministration og Organisationsadministration. For de nøjagtige tilladelseskrav til hver administrationsopgave skal du se den dokumentation, der følger med administratorvejledningen.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Tilladelser til opbevaringspolitikker og opbevaringsnavne

Medlemmer af dit overholdelsesteam, der opretter og administrerer opbevaringspolitikker og opbevaringsmærkater, skal have tilladelse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">til Microsoft 365 Overholdelsescenter</a>. Som standard har lejeradministratoren (global administrator) adgang til denne placering og kan give compliance officers og andre personer adgang uden at give dem alle tilladelser som lejeradministrator. Hvis du vil give tilladelser til denne begrænsede administration, anbefaler vi, at du føjer brugere til **rollegruppen overholdelsesadministrator** .

Alternativt kan du bruge denne standardrolle til at oprette en ny rollegruppe og føje **opbevaringsstyringsrollen** til denne gruppe. For at få en skrivebeskyttet rolle skal du **bruge Skrivebeskyttet opbevaringsstyring**. 

Du kan finde en vejledning til at føje brugere til standardrollerne eller oprette dine egne [rollegrupper under Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md).

Disse tilladelser er kun nødvendige for at oprette, konfigurere og anvende opbevaringspolitikker og opbevaringsnavne. Den person, der konfigurerer disse politikker og etiketter, kræver ikke adgang til indholdet.

## <a name="common-scenarios"></a>Almindelige scenarier

Brug tabellen nedenfor som en hjælp til at kortlægge virksomhedens krav til de mest almindelige scenarier for informationsstyring.

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Opbehold eller slet effektivt data til Microsoft 365 tjenester: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Microsoft 365 grupper <br />- Teams <br />- Yammer <br />- Skype for Business |[Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)|
|Giv brugere yderligere lagerplads til postkasser |[Aktivér arkivpostkasser i overholdelsescenter](enable-archive-mailboxes.md)|
|Bevare postkassedata, når medarbejdere forlader organisationen |[Oprette og administrere inaktive postkasser](create-and-manage-inactive-mailboxes.md)|
|Upload postkassedata fra PST-filer |[Brug netværksupload til at importere PST-filer](use-network-upload-to-import-pst-files.md)|


Hvis du har et scenarie, der kræver administration af livscyklus for individuelle elementer, kan [du se de almindelige scenarier for datastyring](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

Se det følgende afsnit for at få oplysninger om slutbrugerdokumentation, der understøtter Microsoft 365 opbevaring.

De funktioner til informationsstyring, der understøtter administration af postkasser (arkivering, inaktive postkasser og import), kræver typisk ikke slutbrugerdokumentation.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Slutbrugerdokumentation til opbevaring og sletning

De fleste opbevaringspolitikker fungerer diskret i baggrunden uden brugerinteraktion, og der er derfor brug for meget lidt dokumentation til brugerne. Opbevaringspolitikker for Teams brugere, når deres meddelelser er blevet slettet, med et link til Teams [om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Men hvis du supplerer opbevaringspolitikker med opbevaringsetiketter, har disse etiketter en brugergrænsefladetilstedeværelse Microsoft 365 apps. Før du installerer disse etiketter i produktionsnetværket, skal du sørge for at angive oplysninger og instruktioner til slutbrugerne og din helpdesk. For at hjælpe brugerne med at anvende opbevaringsmærkater SharePoint og OneDrive, skal du se Anvend opbevaringsnavne på [filer SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Den mest effektive dokumentation til slutbrugeren vil altid blive tilpasset vejledning og vejledning, som du angiver for de opbevaringsetiketnavne og -konfigurationer, du vælger. Se følgende side og downloads, som du kan bruge til at hjælpe med at træne dine brugere: [Slutbrugerkurser i opbevaringsnavne](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

