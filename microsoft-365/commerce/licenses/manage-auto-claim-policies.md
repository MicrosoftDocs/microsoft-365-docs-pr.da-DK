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
description: Få mere at vide om, hvordan du opretter og administrerer politikker for automatisk krav, der automatisk tildeler licenser til brugere for visse apps.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: d6cb3d78de914e84e831947089aeadf277e72ddf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591734"
---
# <a name="manage-auto-claim-policies"></a>Administrer politikker for automatisk krav

En politik for automatisk krav giver brugere mulighed for automatisk at gøre krav på en licens til et produkt, første gang de logger på en app. Som administrator tildeler du typisk licenser til brugere enten manuelt eller ved hjælp af gruppebaseret licensering. Ved hjælp af politikker for automatisk krav kan du administrere de produkter, som brugere automatisk kan gøre krav på licenser for. Du kan også styre, hvilke produkter disse licenser kommer fra.

> [!IMPORTANT]
> Politikker for automatisk krav er i øjeblikket kun tilgængelige for Microsoft Teams. Der vil være flere produkter tilgængelige til senere brug.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global, bruger eller licensadministrator for at oprette og administrere politikker for automatisk krav. Få mere at vide under [Om Microsoft 365 administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Slå funktionen til automatisk kravpolitik til eller fra

Som standard er funktionen til automatisk kravpolitik slået fra. Før du kan bruge funktionen, skal du først aktivere den. Når du har aktiveret funktionen, kan du oprette en politik for automatisk krav.

### <a name="turn-on-auto-claim-policies"></a>Slå politikker for automatisk krav til

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg knappen Aktivér indstilling midt på **siden** .

### <a name="turn-off-auto-claim-policies"></a>Slå politikker for automatisk krav fra

Kun en global administrator kan deaktivere en politikindstilling for automatisk krav.

1. I Administration skal du gå til siden **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Org-indstillinger</a>.
2. Nederst i tabellen skal du vælge **Brugerejede apps og tjenester**.
3. I højre rude skal du fjerne markeringen i afkrydsningsfeltet **Lad brugere gøre brug af licenser automatisk, første gang de logger på**.

Hvis du allerede har en aktiv politik, men du ikke vil have flere brugere til at gøre krav på licenser, [skal du deaktivere politikken](#turn-a-policy-on-or-off). Når du deaktiverer en politik for automatisk krav, kan ingen flere brugere gøre krav på en licens fra det pågældende tidspunkt. Brugere, der allerede påstået en licens, mister ikke deres licens.

## <a name="create-an-auto-claim-policy"></a>Opret en politik for automatisk krav

Under <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">fanen Politik for automatisk krav</a> vises de politikker, du opretter. På denne fane kan du se: navnet på politikken, den app, der er knyttet til politikken, det produkt, der er tildelt politikken, antallet af tilgængelige licenser og politikkens status.

Når du opretter en politik for automatisk krav, kan du tilføje et sikkerhedskopiprodukt til den. Hvis det primære produkt ikke har flere licenser, bruges sikkerhedskopiproduktet til at tildele licenser til brugerne. Du kan tilføje op til fire sikkerhedskopiprodukter [og ændre den rækkefølge, de bruges i](#change-the-assigning-order-for-backup-products). Du kan få mere at vide [under Tilføj eller fjern sikkerhedskopierede produkter](#add-or-remove-backup-products).

> [!NOTE]
> I øjeblikket kan du kun oprette én politik for automatisk krav. Antallet af politikker, du kan oprette, øges i forhold til, at flere produkter kan bruge denne funktion.

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg **Tilføj en politik**.
3. På siden **Navngive denne politik for automatisk** krav skal du angive et navn til politikken og derefter vælge **Næste**.
4. På siden **Angiv en app til automatisk krav og produkt skal** du vælge en app og det abonnement, der skal tildeles licenser fra.
5. Hvis du vil tilføje et sikkerhedskopiprodukt, skal **du vælge Føj et sikkerhedskopiprodukt** til denne politik og derefter vælge produktet på listen.
6. Vælg **Næste**.
7. På siden **Vælg apps skal** du rydde eller markere felterne for de apps, der skal udelades eller medtages med licensen, og derefter skal du vælge **Næste**.
8. Hvis du har tilføjet et eller flere sikkerhedskopiprodukter, skal du gentage trin 7 for hvert produkt. Ellers skal du gå til trin 9.
9. På siden **Gennemse og afslut** skal du bekræfte de nye politikoplysninger, foretage de nødvendige ændringer og derefter vælge **Opret politik**.
10. Vælg **Luk**.

## <a name="turn-a-policy-on-or-off"></a>Slå en politik til eller fra

Når du deaktiverer en politik, kan flere brugere ikke gøre krav på licenser i henhold til denne politik. Ændringen påvirker ikke brugere, der allerede har påstået licenser i henhold til denne politik.

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. Markér eller fjern markeringen i **afkrydsningsfeltet under Slå denne** politik til eller fra i detaljeruden.
4. Vælg **Gem** for at lukke detaljeruden.

## <a name="edit-the-policy-friendly-name"></a>Rediger politikkens brugervenlige navn

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. I detaljeruden i sektionen **Politiknavn** skal du vælge **Rediger**.
4. Angiv et nyt politiknavn, og vælg derefter **Gem**.
5. Vælg **Gem** for at lukke detaljeruden.

## <a name="add-or-remove-backup-products"></a>Tilføj eller fjern sikkerhedskopierede produkter

Når du opretter en politik, føjer du et produkt til den. Licenser tildeles derefter automatisk til brugere fra den pågældende licenspulje. Du kan når som helst tilføje eller fjerne produkter for en politik for automatisk krav. Hvis du allerede har ét produkt, der er knyttet til politikken, betragtes alle de produkter, du tilføjer, som sikkerhedskopiprodukter. Når det tilgængelige antal licenser fra det første produkt er brugt, bruger politikken det næste sikkerhedskopiprodukt på listen til at tildele licenser fra. Du [kan ændre rækkefølgen af listen over produkter, som](#change-the-assigning-apps-and-services) du ønsker.

Når du fjerner et sikkerhedskopieringsprodukt, bruges det ikke længere til at tildele licenser. Brugere med en eksisterende licens har stadig denne licens, men ingen nye brugere kan modtage licenser for det pågældende produkt.

> [!NOTE]
> En politik for automatisk krav skal indeholde mindst ét produkt. Du kan ikke fjerne alle produkter fra en politik. Hvis du ikke vil tildele licenser fra en bestemt politik for automatisk krav længere, skal [du deaktivere politikken](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Tilføj et sikkerhedskopiprodukt

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. I detaljeruden nederst skal du vælge Føj **et sikkerhedskopiprodukt til denne politik**.
    > [!NOTE]
    > Hvis du ikke kan se dette link, skyldes det, at du kun har ét produkt knyttet til din konto.
4. I **ruden Tilføj et produkt** skal du bruge rullelisten til at vælge et produkt, der skal føjes til politikken, og derefter vælge **Tilføj**.
5. Vælg **Gem** for at lukke detaljeruden.

### <a name="remove-a-backup-product"></a>Fjern et sikkerhedskopiprodukt

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. I detaljeruden nederst skal du vælge **Fjern et produkt**.
4. I **ruden Fjern et produkt fra politikruden** skal du markere feltet for den politik, du vil fjerne, og derefter vælge **Gem**.
5. Luk detaljeruden.

## <a name="change-the-assigning-apps-and-services"></a>Ændre tildeling af apps og tjenester

Hvert produkt har en samling af apps og tjenester tilknyttet. For hvert produkt i din politik for automatisk krav kan du angive, hvilke apps og tjenester, der skal medtages, når en bruger automatisk tildeles en licens til det pågældende produkt.

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. I detaljeruden under **Apps og tjenester skal** du vælge **Rediger**.
4. Vælg et **enkelt produkt på** rullelisten **Produkt** i ruden Apps og tjenester, eller vælg **Alle produkter**.
5. Markér eller fjern markeringen i afkrydsningsfelterne for apps og tjenester, som brugere skal have eller ikke skal have adgang til.
6. Når du er færdig, skal du **vælge Gem** og derefter lukke detaljeruden.

## <a name="change-the-assigning-order-for-backup-products"></a>Ændre tildelingsordren for sikkerhedskopierede produkter

Hvis du har sikkerhedskopierede produkter, der er tildelt politikken, kan du ændre den rækkefølge, som de bruges til at tildele licenser i, når brugerne logger på appen.

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg den politik, du vil redigere.
3. I detaljeruden i sektionen **Produktlicenser** skal du markere feltet ud for det produkt, du vil flytte, og derefter vælge **Flyt op** **eller Flyt ned**.
4. Gentag trin 3 for hvert produkt, du vil ændre rækkefølgen for.
5. Når du er færdig med at omarranger produkterne, skal du vælge **Gem** for at lukke detaljeruden.

## <a name="view-an-auto-claim-policy-report"></a>Få vist en rapport om automatisk kravpolitik

1. I Administration skal du gå til siden **Faktureringslicenser** \> og derefter vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Politik for automatisk</a> krav.
2. Vælg **Vis rapport**. Siden **rapport over automatisk kravpolitik viser** alle licenser, der er tildelt fra hver politik inden for de seneste 90 dage. Siden viser som standard de seneste 90 dage.
3. Hvis du vil ændre den viste tidsperiode, skal **du vælge rullelisten Seneste 30** dage. Du kan få vist rapporter for de seneste 1, 7, 30 og 90 dage.

## <a name="next-steps"></a>Næste trin

Du kan med jævne mellemrum vende tilbage til **fanen politik for** automatisk krav for at få vist en liste over brugere, der har påstået licenser i henhold til de politikker, du har oprettet.

## <a name="related-content"></a>Relateret indhold

[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Køb eller fjern abonnementslicenser](buy-licenses.md) (artikel)\
[Forstå abonnementer og licenser](subscriptions-and-licenses.md) (artikel)
