---
title: Administrer licensanmodninger
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
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
description: Få mere at vide om, hvordan du gennemser og godkender eller afviser licensanmodninger fra brugere for dit abonnement på Microsoft 365 til virksomheder.
ms.date: 04/22/2022
ms.openlocfilehash: dfe8410ce894e19489664396866917e4c5bb3dd4
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044241"
---
# <a name="manage-license-requests"></a>Administrer licensanmodninger

> [!NOTE]
> Oplysningerne i denne artikel gælder kun for købte produkter, der er købt via selvbetjening. Du kan få mere at vide under [Ofte stillede spørgsmål om køb via selvbetjening](../subscriptions/self-service-purchase-faq.yml).

Hvis du deaktiverer køb via selvbetjening i din organisation, kan du bruge licensanmodninger til at administrere licensanmodningsprocessen for dine brugere. Når en bruger forsøger at foretage et køb via selvbetjening for et produkt, du har blokeret, kan vedkommende sende en anmodning om en licens til dig, administratoren. Når de foretager en anmodning, kan de tilføje navnene på andre brugere, der også har brug for licenser til produktet.

> [!NOTE]
> Hvis du blokerer brugere fra at foretage køb via selvbetjening, sender Microsoft dem ikke marketingmails. Hvis de bruger en prøveversion af et produkt, får de heller ikke vist prompter om at købe det. Du kan få mere at vide under [Administrer køb via selvbetjening (administrator).](../subscriptions/manage-self-service-purchases-admins.md)

Hvis administratoren vil se og administrere licensanmodninger, skal du bruge fanen **Anmodninger** på siden **Licensering** . Listen viser navnet på det produkt, der anmodes om, navnet på den person, der anmoder om en licens, den anmodede dato og status for anmodningen. Administratorer kan filtrere listen for at få vist anmodninger, der afventer eller er fuldført. Anmodninger opbevares i 30 dage.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator for at kunne udføre opgaverne i denne artikel. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Brug din egen anmodningsproces

Hvis din organisation har sin egen anmodningsproces, kan du bruge den i stedet. Du opretter en meddelelse, der vises for brugerne, når de anmoder om en licens.

> [!IMPORTANT]
> Hvis du bruger din egen anmodningsproces, vises der ingen anmodninger under fanen **Anmodninger** . Eksisterende anmodninger fra før du har tilføjet din meddelelse, vises fortsat, indtil du godkender eller afviser dem.

1. Gå til siden **Faktureringslicenser** >  i Administration, og vælg derefter fanen **Anmodninger**.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Vælg **Brug i stedet din eksisterende anmodningsproces**.
3. Skriv den meddelelse, brugerne skal se, når de anmoder om en licens, i feltet **Meddelelse** i ruden til højre. Hvis du også vil medtage et link til din organisations politik eller anden dokumentation, skal du angive URL-adressen i tekstfeltet **Link til dokumentation (valgfrit).**
4. Vælg **Gem**.

Når du vender tilbage til listen **Over anmodninger** , får du vist meddelelsen **Du bruger din egen licensanmodningsproces**. Hvis du vil foretage ændringer i den meddelelse, der sendes til brugere, skal du vælge **Brug din eksisterende anmodningsproces i stedet.**

## <a name="stop-using-your-own-request-process"></a>Stop med at bruge din egen anmodningsproces

1. Gå til siden **Faktureringslicenser** >  i Administration, og vælg derefter fanen **Anmodninger**.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Vælg **Brug i stedet din eksisterende anmodningsproces**.
3. Fjern markeringen i afkrydsningsfeltet **Brug min organisations anmodningsproces** i ruden til højre.
4. Vælg **Gem**.

## <a name="approve-or-deny-a-license-request"></a>Godkend eller afvis en licensanmodning

1. Gå til siden **Faktureringslicenser** >  i Administration, og vælg derefter fanen **Anmodninger**.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Markér den række, der indeholder den anmodning, du vil gennemse. I ruden til højre kan du se oplysninger om, hvilke brugere der vil have licenser til produktet.
3. Hvis du vil afvise hele anmodningen, skal du vælge **Godkend ikke** og vælge **Godkend ikke** i dialogboksen.
4. Hvis du vil afvise nogle brugere for anmodningen, men godkende andre, skal du vælge X efter navnet på de brugere, du vil fjerne. Deres navne flyttes under **Tildel ikke til disse brugere**.
5. Hvis du har mere end ét produkt, skal du under **Vælg et produkt** vælge det, du vil bruge til at tildele licenser til.
6. Hvis du vil nægte brugere adgang til visse apps og tjenester, skal du udvide **Slå apps og tjenester til eller fra** og derefter fjerne markeringen i afkrydsningsfelterne for dem, du vil udelade.
7. Skriv en valgfri meddelelse i tekstfeltet nederst i ruden.
8. Når du er færdig, skal du vælge **Godkend**. Oplysningerne om anmodningen vises i ruden til højre.
9. Luk ruden til højre.
    Brugerne modtager en mail, hvor der står, at deres anmodning blev godkendt eller afvist.

## <a name="related-content"></a>Relateret indhold

[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Flyt brugere til et andet abonnement](../subscriptions/move-users-different-subscription.md) (artikel)\
[Køb eller fjern abonnementslicenser](buy-licenses.md) (artikel)\
[Ofte stillede spørgsmål om køb via selvbetjening](../subscriptions/self-service-purchase-faq.yml)
