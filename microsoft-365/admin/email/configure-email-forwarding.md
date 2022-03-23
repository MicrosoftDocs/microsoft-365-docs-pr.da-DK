---
title: Konfigurere videresendelse af mail
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: Videresendelse af mail gør det muligt at videresende mails, der er sendt Microsoft 365 en brugerpostkasse, til en anden postkasse i eller uden for organisationen.
ms.openlocfilehash: 5522d9202732ca54d1a395a83e99ae2442b68eb9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63589963"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>Konfigurere videresendelse af mail i Microsoft 365

Som administrator for en organisation kan du komme ud for firmakrav om at konfigurere videresendelse af mail for en brugers postkasse. Med videresendelse af mail kan du videresende mails, der sendes til en brugers postkasse, til en anden brugers postkasse i eller uden for organisationen.

> [!IMPORTANT]
> Du kan bruge politikker for udgående spamfilter til at styre automatisk videresendelse til eksterne modtagere. Du kan få mere at vide [under Kontrollere automatisk videresendelse af eksterne mails Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="configure-email-forwarding"></a>Konfigurere videresendelse af mail

Før du konfigurerer videresendelse af mail, skal du være opmærksom på følgende:

- Tillad automatisk videresendte meddelelser at blive sendt til personer på fjerndomænet. Se [Administrer eksterne domæner for at få](/exchange/mail-flow-best-practices/remote-domains/manage-remote-domains) mere at vide.

- Når du har konfigureret videresendelse af mail, **vil kun** nye mails, der  *sendes til fra*  postkassen blive videresendt.

- Videresendelse af mail kræver,  *at kontoen*  fra har en licens. Hvis du konfigurerer videresendelse af mail, fordi brugeren har forladt din organisation, er en anden mulighed at konvertere [brugerens postkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md). På den måde kan flere personer få adgang til den. En delt postkasse må dog ikke overstige 50 GB.

Du skal være Exchange administrator eller global administrator i Microsoft 365 at udføre disse trin. Du kan finde flere oplysninger i emnet [Om administratorroller](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere **[for](https://go.microsoft.com/fwlink/p/?linkid=834822)** brugere.

2. Vælg navnet på den bruger, hvis mail du vil videresende, og åbn derefter siden med egenskaber.

3. På fanen **Mail** skal du vælge Administrer **videresendelse af mail**.

4. På siden til videresendelse af mail skal du vælge Videresende alle **mails, der** sendes til denne postkasse, angive videresendelsesadressen og vælge, om du vil bevare en kopi af videresendte mails. Hvis du ikke kan se denne indstilling, skal du kontrollere, at brugerkontoen er tildelt en licens. Vælg **Gem ændringer**.

    **Hvis du vil videresende til flere mailadresser**, kan du bede brugeren om at konfigurere en regel i Outlook at videresende til adresserne. 
    
    1.  Åbn **outlook-regler** > >**for** > Vælg **Administrer regler & vigtige beskeder**  
    1. Vælg **Ny regel Vælg** > **Anvend regel på meddelelse, jeg modtager placeret** nederst på listen, og klik derefter på **Næste**.
    1. Klik **på Ja** , når du bliver spurgt Denne regel anvendes på alle meddelelser, du modtager. 
    1. På den næste liste skal du vælge handlingerne **omdirigere den til personer eller offentlig gruppe og** **standse behandlingen af flere regler**
    1. Klik på det understregede **udtryk personer eller den offentlige** gruppe i den nederste del af vinduet.
    1. Skriv den **mailadresse, du** vil videresende mails til, i feltet Til, og klik derefter på **OK**.
    1. Vælg **Udfør**
    

     Du kan også oprette en [distributionsgruppe i Administration](../setup/create-distribution-lists.md)[, tilføje](add-user-or-contact-to-distribution-list.md) adresserne til den og derefter konfigurere videresendelse til at pege på distributionsgruppen ved hjælp af instruktionerne i denne artikel.

5. Slet ikke kontoen for den bruger, hvis mail du videresender, eller fjern ikke brugerens licens!  Hvis du gør det, stopper videresendelse af mail.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere **[for](https://go.microsoft.com/fwlink/p/?linkid=850628)** brugere.

2. Vælg navnet på den bruger, hvis mail du vil videresende, for at åbne siden med egenskaber.

3. **Udvid indstillinger for** Mail, og vælg **derefter Rediger i** sektionen Videresendelse af **mail**.

4. På siden til videresendelse af mail skal du indstille til/fra-knappen til **Til, angive** videresendelsesadressen og vælge, om du vil beholde en kopi af videresendte mails. Hvis du ikke kan se denne indstilling, skal du kontrollere, at brugerkontoen er tildelt en licens. Vælg **Gem**.

   **Hvis du vil videresende til flere mailadresser**, kan du bede brugeren om at konfigurere en regel i Outlook at videresende til adresserne. Du kan få mere at vide [under Brug regler til automatisk videresendelse af meddelelser](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746).

   Du kan også oprette en [distributionsgruppe i Administration](../setup/create-distribution-lists.md)[, tilføje](add-user-or-contact-to-distribution-list.md) adresserne til den og derefter konfigurere videresendelse til at pege på distributionsgruppen ved hjælp af instruktionerne i denne artikel.

5. Slet ikke kontoen for den bruger, hvis mail du videresender, eller fjern ikke brugerens licens! Hvis du gør det, stopper videresendelse af mail.

::: moniker-end

## <a name="related-content"></a>Relateret indhold 

[Opret en delt postkasse](../email/create-a-shared-mailbox.md) (artikel)\
[Send mail fra en anden adresse](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artikel)\
[Rediger et brugernavn og en mailadresse](../add-users/change-a-user-name-and-email-address.md) (artikel)\
[Styr automatisk videresendelse af eksterne mails Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding) (artikel)


