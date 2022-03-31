---
title: Konfigurere indstillinger for delt postkasse
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Opret en delt postkasse, og konfigurer nogle indstillinger for dens brugere, f.eks. videresendelse af mail og autosvar.
ms.openlocfilehash: 201291adddf588bde955cbba7e2c0075e5ca7c88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63599759"
---
# <a name="configure-shared-mailbox-settings"></a>Konfigurere indstillinger for delt postkasse

Når du har [oprettet en delt postkasse](create-a-shared-mailbox.md), skal du konfigurere nogle indstillinger for postkassebrugerne, f.eks. videresendelse af mail og autosvar. Senere kan det være en ide at ændre andre indstillinger, f.eks. postkassenavn, medlemmer eller medlemstilladelser. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Skift navn eller mailalias for en delt postkasse, eller rediger den primære mailadresse

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger** ud for **Navn, Mail, Mailaliasser**.

3. Angiv et nyt navn, eller tilføj et andet alias. Hvis du vil ændre den primære mailadresse, skal din postkasse have mere end ét mailalias.

4. Vælg **Gem**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Videresende mails, der sendes til en delt postkasse

Du behøver ikke at tildele en licens til den delte postkasse for at videresende mails, der sendes til den. Du kan videresende meddelelserne til en gyldig mailadresse eller distributionsliste.

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger ved videresendelse af mail**\>.
    
3. Sæt til/ **fra-knappen på Til**, og angiv én mailadresse, som meddelelserne skal videresendes til. Det kan være en hvilken som helst gyldig mailadresse. Hvis du vil videresende til flere adresser, skal du oprette en [distributionsgruppe](/office365/admin/setup/create-distribution-lists) til adresserne og derefter skrive navnet på gruppen i dette felt.
    
4. Vælg **Gem**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Send autosvar fra en delt postkasse

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Autosvar** \> **Rediger**.
    
3. Sæt til/fra knappen **på Til**, og vælg, om du vil sende svar til personer i organisationen eller uden for organisationen.

4. Skriv det svar, du vil sende til personer i din organisation. Du kan ikke tilføje billeder, kun tekst.

5. Hvis du også vil *sende* et svar til personer uden for organisationen, skal du markere afkrydsningsfeltet, hvem du vil have svaret til, og skrive teksten. Det er ikke muligt kun at sende til personer uden for organisationen, men ikke til personer inden for organisationen.

6. Vælg **Gem**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Tillad, at alle kan se den sendte mail (svarene)

Som standard gemmes meddelelser, der sendes fra den delte postkasse, ikke i mappen Sendt post i den delte postkasse. I stedet gemmes de i mappen Sendt post for den person, der har sendt meddelelsen.

Hvis du vil tillade, at alle kan se den sendte mail, skal du redigere indstillingerne for den delte postkasse i Administration og vælge **Rediger sendt** \> **post**.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Vælg de apps, som en delt postkasse kan bruge til at få adgang til Microsoft-mail

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger mailapps**\>.

3. Slå indstillingen Til for **alle** de apps, som medlemmer skal kunne bruge til at få adgang til den delte postkasse. Indstil til/ **fra-knappen til** Fra for apps, du ikke vil have, de skal bruge. 

4. Vælg **Gem**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Sæt en delt postkasse i retslig venteposition

Du kan få mere at vide om retslig venteposition under [Opret en retslig venteposition](../../compliance/create-a-litigation-hold.md).

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Retslig venteposition** \> **Rediger**.

3. Sæt til/fra-knappen til **Til**. 

4. Du kan også angive en varighed, noten om ventepositionen og en URL-adresse med flere oplysninger.  

5. Vælg **Gem**.


## <a name="add-or-remove-members"></a>Tilføj eller fjern medlemmer

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger** \> **medlemmer**.

3. Gør et af følgende:
   - Hvis du vil tilføje medlemmer, **skal du vælge** Tilføj medlemmer, søge efter eller vælge et medlem at tilføje og derefter vælge **Gem**.
   - Hvis du vil fjerne medlemmer, skal du bruge feltet Søg til at søge efter medlemmet, hvis det er nødvendigt, vælge **X** ud for medlemmets navn og derefter vælge **Gem**. 

4. Vælg **Gem** igen.

## <a name="add-or-remove-permissions-of-members"></a>Tilføje eller fjerne tilladelser for medlemmer

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg **derefter Medlemmer** \> **Tilpas tilladelser**.

3. Vælg **Rediger** ud for den tilladelse, du vil ændre for et medlem. 

4. Gør et af følgende:
   - Hvis du vil give tilladelse til et ekstra medlem, skal du vælge Tilføj tilladelser, søge efter eller vælge et medlem, der skal **tilføjes**, og derefter vælge **Gem**.
   - Hvis du vil fjerne tilladelsen fra et medlem, skal du bruge feltet Søg til at søge efter medlemmet, hvis det er nødvendigt, vælge **X** ud for medlemmets navn og derefter vælge **Gem**. 

4. Vælg **Gem** igen.

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Vise eller skjule en delt postkasse på den globale adresseliste

Hvis du vælger ikke at vise den delte postkasse på den globale adresseliste, vises postkassen ikke på organisationens adresseliste, men den vil stadig modtage mails, der sendes til den. 

1. I Administration skal du gå til **siden Delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser for</a> grupper.

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Vis i global adresseliste** \> **Rediger**.

3. Sæt til/fra-knappen **til Til**  eller **Fra**. 

4. Vælg **Gem**.

> [!NOTE]
> Hvis du skjuler en delt postkasse fra adresselisten, kan nye medlemmer af den delte postkasse ikke føje den skjulte postkasse til deres Outlook-profil, før den delte postkasse igen vises på adresselisten. 

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løse problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)