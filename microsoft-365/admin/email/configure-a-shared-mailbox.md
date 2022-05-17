---
title: Konfigurer indstillinger for delt postkasse
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
description: Opret en delt postkasse, og konfigurer nogle indstillinger for brugerne, f.eks videresendelse af mail og autosvar.
ms.openlocfilehash: b3de51a8407c8f9786d6a1677137f2a564744ac0
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437145"
---
# <a name="configure-microsoft-365-shared-mailbox-settings"></a>Konfigurer Microsoft 365 delte postkasseindstillinger

Når du har [oprettet en delt postkasse](create-a-shared-mailbox.md), skal du konfigurere nogle indstillinger for brugerne af postkassen, f.eks. videresendelse af mail og autosvar. Senere kan det være en god idé at ændre andre indstillinger, f.eks. postkassens navn, medlemmer eller medlemstilladelser. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Rediger navnet eller mailaliasset for en delt postkasse, eller rediger den primære mailadresse

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger** ud for **Navn, Mail og Mailaliasser**.

3. Angiv et nyt navn, eller tilføj et andet alias. Hvis du vil ændre den primære mailadresse, skal postkassen have mere end ét mailalias.

4. Vælg **Gem**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Videresend mails, der sendes til en delt postkasse

Du behøver ikke at tildele en licens til den delte postkasse for at videresende mails, der er sendt til den. Du kan videresende meddelelserne til en hvilken som helst gyldig mailadresse eller distributionsliste.

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Videresendelse af** \> mail **Rediger**.
    
3. Angiv til/fra-knappen til **Til**, og angiv én mailadresse, meddelelserne skal videresendes til. Det kan være en hvilken som helst gyldig mailadresse. Hvis du vil videresende til flere adresser, skal du [oprette en distributionsgruppe](/office365/admin/setup/create-distribution-lists) for adresserne og derefter angive navnet på gruppen i dette felt.
    
4. Vælg **Gem**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Send autosvar fra en delt postkasse

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Autosvar** \> **Rediger**.
    
3. Angiv til/fra-knappen til **Til**, og vælg, om du vil sende svaret til personer i din organisation eller uden for din organisation.

4. Angiv det svar, du vil sende til personer i din organisation. Du kan ikke tilføje billeder, kun tekst.

5. Hvis du *også* vil sende et svar til personer uden for din organisation, skal du markere afkrydsningsfeltet, hvem du vil have svaret fra, og skrive teksten. Du kan ikke kun sende til personer uden for din organisation, men ikke til personer i din organisation.

6. Vælg **Gem**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Tillad alle at se den sendte mail (svarene)

Meddelelser, der sendes fra den delte postkasse, gemmes som standard ikke i mappen Sendt post i den delte postkasse. De gemmes i stedet i mappen Sendt post for den person, der sendte meddelelsen.

Hvis du vil give alle mulighed for at se Sendt mail, skal du redigere indstillingerne for den delte postkasse i Administration og vælge **Rediger sendte elementer**\>.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Vælg de apps, som en delt postkasse kan bruge til at få adgang til Microsoft-mail

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Rediger mailapps**\>.

3. Angiv til/fra-knappen til **Til** for alle de apps, som medlemmerne skal kunne bruge til at få adgang til den delte postkasse. Indstil til/ **fra-knappen til Fra** for alle de apps, du ikke vil have, de skal bruge. 

4. Vælg **Gem**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Sæt en delt postkasse i strid med procesførelse

Hvis du vil vide mere om venteposition for tvister, skal du se [Opret en procesførelsesventeposition](../../compliance/create-a-litigation-hold.md).

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Procesvist venteposition** \> **Rediger**.

3. Indstil til/fra-knappen til **Til**. 

4. Du kan også angive en varighed, en note om ventepositionen og en URL-adresse med flere oplysninger.  

5. Vælg **Gem**.


## <a name="add-or-remove-members"></a>Tilføj eller fjern medlemmer

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Medlemmer** \> **Rediger**.

3. Gør et af følgende:
   - Hvis du vil tilføje medlemmer, skal du vælge **Tilføj medlemmer**, søge efter eller vælge et medlem, der skal tilføjes, og derefter vælge **Gem**.
   - Hvis du vil fjerne medlemmer, skal du bruge søgefeltet til at søge efter medlemmet, hvis det er nødvendigt, vælge **X** ud for medlemmets navn og derefter vælge **Gem**. 

4. Vælg **Gem** igen.

## <a name="add-or-remove-permissions-of-members"></a>Tilføj eller fjern medlemmers tilladelser

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Medlemmer** \> **Tilpas tilladelser**.

3. Vælg **Rediger** ud for den tilladelse, du vil ændre for et medlem. 

4. Gør et af følgende:
   - Hvis du vil give denne tilladelse til et ekstra medlem, skal du vælge **Tilføj tilladelser**, søge efter eller vælge et medlem, der skal tilføjes, og derefter vælge **Gem**.
   - Hvis du vil fjerne tilladelsen fra et medlem, skal du bruge søgefeltet til at søge efter medlemmet, hvis det er nødvendigt, vælge **X** ud for medlemmets navn og derefter vælge **Gem**. 

4. Vælg **Gem** igen.

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Vis eller skjul en delt postkasse på den globale adresseliste

Hvis du vælger ikke at vise den delte postkasse på den globale adresseliste, vises postkassen ikke på organisationens adresseliste, men den modtager stadig mail, der er sendt til den. 

1. I Administration skal du gå til siden **Grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a> .

2. Vælg den delte postkasse, du vil redigere, og vælg derefter **Vis på den globale adresseliste** \> **Rediger**.

3. Indstil til/fra-knappen til **Til**  eller **Fra**. 

4. Vælg **Gem**.

> [!NOTE]
> Hvis du skjuler en delt postkasse fra adresselisten, bliver det umuligt for nye medlemmer af den delte postkasse at føje den skjulte postkasse til deres Outlook profil, før den delte postkasse igen vises på adresselisten. 

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løs problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)