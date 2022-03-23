---
title: Administrer licensanmodninger
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: micurn, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- MACBillingLicensesRequests
- AdminSurgePortfolio
search.appverid: MET150
description: Få mere at vide om, hvordan du gennemser og godkender eller afviser licensanmodninger fra brugere Microsoft 365 for business-abonnement.
ms.date: 06/07/2021
ms.openlocfilehash: 7932383afe109e707a5c35914e50c665d0bf1885
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590522"
---
# <a name="manage-license-requests"></a>Administrer licensanmodninger

> [!NOTE]
> Oplysningerne i denne artikel gælder kun for produkter, der er købt via selvbetjening. Du kan få mere at vide under [Ofte stillede spørgsmål om selvbetjeningskøb](../subscriptions/self-service-purchase-faq.yml).

Hvis du deaktiverer selvbetjeningskøb i organisationen, kan du bruge licensanmodninger til at administrere processen for licensanmodninger for dine brugere. Når en bruger forsøger at foretage et selvbetjeningskøb for et produkt, som du har blokeret, kan brugeren sende en anmodning om en licens til dig, administratoren. Når de anmoder om det, kan de tilføje navnene på andre brugere, som også skal bruge licenser til produktet.

> [!NOTE]
> Hvis du blokerer brugere fra at foretage selvbetjeningskøb, sender Microsoft dem ikke marketingmails. Hvis de bruger en prøveversion af et produkt, ser de heller ikke instruktioner om at købe det. Du kan få mere at [vide under Administrer selvbetjeningskøb (administrator)](../subscriptions/manage-self-service-purchases-admins.md).

For at se og administrere licensanmodninger bruger **administratoren fanen** Anmodninger på **siden** Licensering. Listen viser navnet på det produkt, der anmodes om, navnet på den person, der anmoder om en licens, den anmodede dato og anmodningens status. Administratorer kan filtrere listen for at få vist anmodninger, der afventer eller er fuldført. Anmodninger opbevares i 30 dage.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator for at udføre opgaverne i denne artikel. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Brug din egen anmodningsproces

Hvis din organisation har sin egen anmodningsproces, kan du bruge den i stedet. Du opretter en meddelelse, der vises for brugerne, når de anmoder om en licens.

> [!IMPORTANT]
> Hvis du bruger din egen anmodningsproces, vises der ingen anmodninger under **fanen** Anmodninger. Eksisterende anmodninger fra før du tilføjede meddelelsen fortsætter med at blive vist, indtil du godkender eller afviser dem.

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> >  og derefter vælge **fanen** Anmodninger.
2. Vælg **Brug din eksisterende anmodningsproces i stedet**.
3. Skriv den meddelelse, **brugerne skal se** , når de anmoder om en licens, i feltet Meddelelse i højre rude. Hvis du også vil medtage et link til organisationens politik eller anden dokumentation, skal du angive URL-adressen i **tekstfeltet Link** til dokumentation (valgfrit).
4. Vælg **Gem**.

Når du vender tilbage til **listen Anmodninger** , får du vist meddelelsen **Du bruger din egen licensanmodningsproces**. Hvis du vil foretage ændringer i den meddelelse, der sendes til brugere, skal du **vælge Brug den eksisterende anmodningsproces i stedet**.

## <a name="stop-using-your-own-request-process"></a>Stop med at bruge din egen anmodningsproces

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> >  og derefter vælge **fanen** Anmodninger.
2. Vælg **Brug din eksisterende anmodningsproces i stedet**.
3. Fjern markeringen i afkrydsningsfeltet **Brug organisationens anmodningsproces i højre** rude.
4. Vælg **Gem**.

## <a name="approve-or-deny-a-license-request"></a>Godkend eller afvisning af en licensanmodning

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> >  og derefter vælge **fanen** Anmodninger.
2. Markér den række, der indeholder den anmodning, du vil gennemse. Ruden til højre viser oplysninger om, hvilke brugere der ønsker licenser til produktet.
3. Hvis du vil afvise hele anmodningen, **skal du vælge** Godkend ikke, og i dialogboksen **skal du vælge Godkend ikke**.
4. Hvis du vil afvise nogle brugere til anmodningen, men godkende andre, skal du vælge X ud for navnet på de brugere, du vil fjerne. Deres navne flyttes under **Tildel ikke til disse brugere**.
5. Hvis du har mere end ét produkt, skal **du vælge det** produkt, du vil bruge til at tildele licenser til, under Vælg et produkt.
6. Hvis du vil nægte brugere adgang til bestemte apps og tjenester, skal du udvide Slå **apps** og tjenester til eller fra og derefter fjerne markeringen i afkrydsningsfelterne ud for dem, du vil udelade.
7. Skriv en valgfri meddelelse i tekstfeltet nederst i ruden.
8. Når du er færdig, skal du vælge **Godkend**. Ruden til højre viser oplysningerne om anmodningen.
9. Luk højre rude.
    Brugerne modtager en mail, hvor der står, at deres anmodning er blevet godkendt eller afvist.

## <a name="related-content"></a>Relateret indhold

[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Flyt brugere til et andet abonnement](../subscriptions/move-users-different-subscription.md) (artikel)\
[Køb eller fjern abonnementslicenser](buy-licenses.md) (artikel)
