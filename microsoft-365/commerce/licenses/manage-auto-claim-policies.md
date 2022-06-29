---
title: Administrer politikker for automatisk krav
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: yinggiy, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
description: Få mere at vide om, hvordan du opretter og administrerer politikker for automatisk krav, der automatisk tildeler licenser til brugere til bestemte apps.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: 76f2742dc97f880c8044def269e3e9517ea4605c
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493780"
---
# <a name="manage-microsoft-teams-auto-claim-policies"></a>Administrer politikker for automatisk krav til Microsoft Teams

En politik for automatisk krav giver brugerne mulighed for automatisk at gøre krav på en licens til et produkt, første gang de logger på en app. Som administrator tildeler du typisk licenser til brugere enten manuelt eller ved hjælp af gruppebaserede licenser. Ved hjælp af politikker for automatisk krav kan du administrere de produkter, som brugerne automatisk kan gøre krav på licenser for. Du kan også styre, hvilke produkter disse licenser kommer fra.

> [!IMPORTANT]
> Politikker for automatisk krav er i øjeblikket kun tilgængelige for Microsoft Teams. Flere produkter vil være tilgængelige til brug i fremtiden.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator, bruger eller licensadministrator for at oprette og administrere politikker for automatisk krav. Du kan få flere oplysninger under [Om administratorroller i Microsoft 365](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Slå politikfunktionen for automatisk krav til eller fra

Politikfunktionen for automatisk krav er som standard slået fra. Før du kan bruge funktionen, skal du først aktivere den. Når du har slået funktionen til, kan du oprette en politik for automatisk krav.

### <a name="turn-on-auto-claim-policies"></a>Slå politikker for automatisk krav til

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg knappen **Slå indstilling** til midt på siden.

### <a name="turn-off-auto-claim-policies"></a>Deaktiver politikker for automatisk krav

Det er kun en global administrator, der kan deaktivere en politikindstilling for automatisk krav.

1. I Administration skal du gå til siden **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Organisationsindstillinger</a> .
2. Nederst i tabellen skal du vælge **Brugerejet apps og tjenester**.
3. I ruden til højre skal du fjerne markeringen i afkrydsningsfeltet **Lad brugerne automatisk gøre krav på licenser, første gang de logger på**.

Hvis du allerede har en aktiv politik, men ikke ønsker, at flere brugere skal gøre krav på licenser, skal [du deaktivere politikken](#turn-a-policy-on-or-off). Når du slår en politik for automatisk krav fra, kan ikke flere brugere gøre krav på en licens fra det pågældende tidspunkt. Brugere, der allerede har gjort krav på en licens, mister ikke deres licens.

## <a name="create-an-auto-claim-policy"></a>Opret en politik for automatisk krav

Under fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a> vises de politikker, du opretter. Under denne fane kan du se: navnet på politikken, den app, der er knyttet til politikken, det produkt, der er tildelt politikken, antallet af tilgængelige licenser og status for politikken.

Når du opretter en politik for automatisk krav, kan du føje et sikkerhedskopiprodukt til den. Hvis det primære produkt ikke har flere licenser, bruges sikkerhedskopiproduktet til at tildele licenser til brugere. Du kan tilføje op til fire sikkerhedskopiprodukter og [ændre den rækkefølge, de bruges i](#change-the-assigning-order-for-backup-products). Du kan få mere at vide under [Tilføj eller fjern sikkerhedskopieringsprodukter](#add-or-remove-backup-products).

> [!NOTE]
> I øjeblikket kan du kun oprette én politik for automatisk krav. Det antal politikker, du kan oprette, øges, efterhånden som flere produkter kan bruge denne funktion.

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg **Tilføj en politik**.
3. Angiv et navn til politikken på siden **Navngiv denne politik for automatisk krav** , og vælg derefter **Næste**.
4. På siden **Angiv en app og et produkt til automatisk krav** skal du vælge en app og det abonnement, du vil tildele licenser fra.
5. Hvis du vil tilføje et sikkerhedskopieringsprodukt, skal du vælge **Føj et sikkerhedskopiprodukt til denne politik** og derefter vælge produktet på listen.
6. Vælg **Næste**.
7. På siden **Vælg apps** skal du rydde eller markere felterne for de apps, der skal udelades eller inkluderes i licensen, og derefter vælge **Næste**.
8. Hvis du har tilføjet et eller flere sikkerhedskopieringsprodukter, skal du gentage trin 7 for hvert produkt. Ellers skal du gå til trin 9.
9. Kontrollér de nye politikoplysninger på siden **Gennemse og afslut** , foretag eventuelle ændringer, og vælg derefter **Opret politik**.
10. Vælg **Luk**.

## <a name="turn-a-policy-on-or-off"></a>Slå en politik til eller fra

Når du slår en politik fra, kan ikke flere brugere gøre krav på licenser under den pågældende politik. Ændringen påvirker ikke brugere, der allerede har gjort krav på licenser i henhold til denne politik.

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. Markér eller fjern markeringen i afkrydsningsfeltet under **Slå denne politik til eller fra** i detaljeruden.
4. Vælg **Gem** for at lukke detaljeruden.

## <a name="edit-the-policy-friendly-name"></a>Rediger det fulde navn for politikken

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. Vælg **Rediger** i sektionen **Politiknavn** i detaljeruden.
4. Angiv et nyt politiknavn, og vælg derefter **Gem**.
5. Vælg **Gem** for at lukke detaljeruden.

## <a name="add-or-remove-backup-products"></a>Tilføj eller fjern sikkerhedskopieringsprodukter

Når du opretter en politik, føjer du et produkt til den. Licenser tildeles derefter automatisk til brugere fra den pågældende pulje af licenser. Du kan når som helst tilføje eller fjerne produkter til en politik for automatisk krav. Hvis du allerede har et produkt, der er knyttet til politikken, anses de produkter, du tilføjer, som sikkerhedskopiprodukter. Når det tilgængelige antal licenser fra det første produkt er brugt op, bruger politikken det næste sikkerhedskopieringsprodukt på listen til at tildele licenser fra. Du [kan omarrangere listen over produkter](#change-the-assigning-apps-and-services) , som du vil.

Når du fjerner et sikkerhedskopieringsprodukt, bruges det ikke længere til at tildele licenser. Brugere med en eksisterende licens har stadig denne licens, men ingen nye brugere kan modtage licenser til det pågældende produkt.

> [!NOTE]
> En politik for automatisk krav skal indeholde mindst ét produkt. Du kan ikke fjerne alle produkter fra en politik. Hvis du ikke længere vil tildele licenser fra en bestemt politik for automatisk krav, skal [du slå politikken fra](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Tilføj et sikkerhedskopieringsprodukt

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. Vælg **Føj et sikkerhedskopiprodukt til denne politik** nederst i detaljeruden.
    > [!NOTE]
    > Hvis du ikke kan se dette link, skyldes det, at du kun har ét produkt knyttet til din konto.
4. I ruden **Tilføj et produkt** skal du bruge rullelisten til at vælge et produkt, der skal føjes til politikken, og derefter vælge **Tilføj**.
5. Vælg **Gem** for at lukke detaljeruden.

### <a name="remove-a-backup-product"></a>Fjern et sikkerhedskopieringsprodukt

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. Vælg **Fjern et produkt** nederst i detaljeruden.
4. I ruden **Fjern et produkt fra politik** skal du markere afkrydsningsfeltet for den politik, du vil fjerne, og derefter vælge **Gem**.
5. Luk detaljeruden.

## <a name="change-the-assigning-apps-and-services"></a>Skift tildeling af apps og tjenester

Hvert produkt har en samling af apps og tjenester tilknyttet. For hvert produkt i politikken for automatisk krav kan du angive, hvilke apps og tjenester der skal inkluderes, når en bruger automatisk tildeles en licens til det pågældende produkt.

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. Vælg **Rediger** under **Apps og tjenester** i detaljeruden.
4. Vælg et enkelt produkt på rullelisten **Produkt** i ruden **Apps og tjenester**, eller vælg **Alle produkter**.
5. Markér eller fjern markeringen i afkrydsningsfeltet for de apps og tjenester, som brugerne skal have eller ikke skal have adgang til.
6. Når du er færdig, skal du vælge **Gem** og derefter lukke detaljeruden.

## <a name="change-the-assigning-order-for-backup-products"></a>Skift tildelingsrækkefølgen for sikkerhedskopiprodukter

Hvis du har fået tildelt sikkerhedskopiprodukter til politikken, kan du ændre den rækkefølge, de bruges i til at tildele licenser, når brugerne logger på appen.

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg den politik, du vil redigere.
3. I detaljeruden skal du i afsnittet **Produktlicenser** markere afkrydsningsfeltet ud for det produkt, du vil flytte, og derefter vælge **Flyt op** eller **Flyt ned**.
4. Gentag trin 3 for hvert produkt, du vil omarrangere.
5. Når du er færdig med at omarrangere produkterne, skal du vælge **Gem** for at lukke detaljeruden.

## <a name="view-an-auto-claim-policy-report"></a>Få vist en politikrapport for automatisk krav

1. I Administration skal du gå til siden **Faktureringslicenser**  \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk krav</a>.
2. Vælg **Vis rapport**. Rapportsiden **Automatisk kravpolitik** viser alle licenser, der er tildelt fra hver politik inden for de seneste 90 dage. Siden viser som standard de seneste 90 dage.
3. Hvis du vil ændre den viste tidsperiode, skal du vælge rullelisten **De seneste 30 dage** . Du kan få vist rapporter for de seneste 1, 7, 30 og 90 dage.

## <a name="next-steps"></a>Næste trin

Du kan jævnligt vende tilbage til fanen **Automatisk kravpolitik** for at få vist en liste over brugere, der har gjort krav på licenser under de politikker, du har oprettet.

## <a name="related-content"></a>Relateret indhold

[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Køb eller fjern abonnementslicenser](buy-licenses.md) (artikel)\
[Forstå abonnementer og licenser](subscriptions-and-licenses.md) (artikel)
