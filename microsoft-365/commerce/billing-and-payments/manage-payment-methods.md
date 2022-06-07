---
title: Administrer betalingsmetoder
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- TopSMBIssues
- okr_SMB
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid: MET150
description: Køb virksomhedsprodukter eller -tjenester fra Microsoft ved hjælp af en eksisterende betalingsmetode, eller tilføj en ny i Microsoft 365 Administration.
ms.date: 06/01/2022
ms.openlocfilehash: a6f15318e1539ef1f6c2656197c222e068f04f87
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922991"
---
# <a name="manage-payment-methods"></a>Administrer betalingsmetoder

> [!IMPORTANT]
> Fra og med den 26. januar 2021 understøttes nye bankkonti ikke længere for kunder i Belgien, Frankrig, Italien, Luxembourg, Portugal, Spanien og USA. Hvis du er en eksisterende kunde i et af disse lande, kan du fortsætte med at betale for dit abonnement med en eksisterende bankkonto, der har et godt omdømme. Du kan dog ikke føje nye abonnementer til bankkontoen.

Når du køber virksomhedsprodukter eller -tjenester fra Microsoft, kan du bruge en eksisterende betalingsmetode eller tilføje en ny. Du kan bruge et kredit- eller debetkort eller en bankkonto til at betale for de ting, du køber.

Hvis din virksomhedskonto har en faktureringsprofil, og du er ejer af en faktureringsprofil eller bidragyder til faktureringsprofilen, kan du bruge den faktureringsprofil, der understøttes af et kreditkort eller en fakturabetaling, til at foretage køb eller betale regninger. Hvis du er leder for fakturering, kan du kun bruge en faktureringsprofil til at betale regninger. Du kan få mere at vide om faktureringsprofiler og -roller under [Administrer faktureringsprofiler](manage-billing-profiles.md).

Hvis din virksomhedskonto ikke har en faktureringsprofil, kan en global administrator eller faktureringsadministrator administrere og bruge en hvilken som helst bankkonto, der er føjet til virksomhedskontoen. Du kan dog kun administrere eller bruge kreditkort, som du tilføjer.

> [!NOTE]
> Muligheden for at betale med en bankkonto er ikke tilgængelig i visse lande eller områder.
>
> Du skal bruge en betalingsmetode, der er udstedt fra det samme land som din lejer.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="watch-update-your-payment-method"></a>Se: Opdater din betalingsmetode

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AVxy?autoplay=false]

Du kan nemt opdatere betalingsmetoden for dit abonnement på Microsoft 365 Business. Du kan ændre oplysninger, f.eks. det kreditkort, der bruges, navnet eller adressen.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator eller faktureringsadministrator for at udføre opgaverne i denne artikel. Få flere oplysninger under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="add-a-payment-method"></a>Tilføj en betalingsmetode

Tilføjelse af en betalingsmetode knytter ikke nogen abonnementer til den. Hvis du vil tildele et enkelt abonnement til betalingsmetoden, skal du se [Rediger en betalingsmetode for et enkelt abonnement](#change-a-payment-method-for-a-single-subscription). Hvis du vil erstatte alle abonnementer, der bruger en anden betalingsmetode, med den nye, skal du se [Erstat en betalingsmetode](#replace-a-payment-method).

1. I Administration skal du gå til siden **Fakturering** > **Fakturaer og betalinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Betalingsmetoder</a>.
2. Vælg **Tilføj en betalingsmetode**.
3. På siden **Betalingsmetoder** skal du vælge en betalingsmetode fra rullemenuen.
4. Angiv oplysningerne for det nye kort eller den nye bankkonto, og vælg derefter **Tilføj**.

## <a name="update-payment-method-details"></a>Opdater oplysninger om betalingsmetode

Du kan ændre navnet på kredit- eller debetkortet, faktureringsadressen eller udløbsdatoen for en eksisterende betalingsmetode. Du kan dog ikke ændre kortet eller kontonummeret. Hvis kontonummeret er ændret, kan du [erstatte det med en anden betalingsmetode](#replace-a-payment-method) og derefter [slette den gamle](#delete-a-payment-method).

1. I Administration skal du gå til siden **Fakturering** > **Fakturaer og betalinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Betalingsmetoder</a>.
2. Vælg rækken for den betalingsmetode, der skal opdateres. Vælg **Rediger** i højre rude.
3. Opdater oplysningerne om din betalingsmetode, herunder navnet på kredit- eller debetkortet, faktureringsadressen eller udløbsdatoen, og vælg derefter **Gem**.

## <a name="replace-a-payment-method"></a>Vælg en betalingsmetode

Når du erstatter en betalingsmetode, erstatter du den for alle abonnementer og faktureringsprofiler, der bruger den samme betalingsmetode. Erstatning af en betalingsmetode sletter ikke den eksisterende betalingsmetode. Den er stadig tilgængelig, så du kan vælge og bruge den til andre abonnementer og faktureringsprofiler.

Hvis du vil ændre betalingsmetoden for et enkelt abonnement, skal du se [Rediger en betalingsmetode for et enkelt abonnement](#change-a-payment-method-for-a-single-subscription).

1. I Administration skal du gå til siden **Fakturering** > **Fakturaer og betalinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Betalingsmetoder</a>.
2. Vælg den række af betalingsmetoden, der skal erstattes. I højre rude vises alle faktureringsprofiler og individuelle abonnementer, der bruger den valgte betalingsmetode.
3. I højre rude skal du vælge **Erstat betalingsmetode for alle elementer**.
4. Hvis du vil bruge en eksisterende betalingsmetode, skal du vælge en på rullelisten og derefter vælge **Erstat**.
    > [!NOTE]
    > Hvis du har abonnementer, der er knyttet til en faktureringsprofil, kan du kun bruge et kredit- eller debetkort til at betale for dem. Hvis du har bankkonti, der er angivet på siden **Betalingsmetoder**, kan de ikke vælges på rullelisten.
5. Hvis du vil tilføje en ny betalingsmetode, skal du vælge **Tilføj betalingsmetode**.
6. Angiv kontooplysningerne i ruden **Tilføj en betalingsmetode**, og vælg derefter **Gem**. Du skal bruge en betalingsmetode fra det samme land som din lejer.
7. Den nye betalingsmetode er allerede valgt på rullelisten. Vælg **Erstat**.

## <a name="change-a-payment-method-for-a-single-subscription"></a>Skift en betalingsmetode for et enkelt abonnement

Du kan ændre den betalingsmetode, der bruges til at betale for et enkelt abonnement.

1. I Administration skal du gå til siden **Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.
2. På fanen **Produkter** skal du finde det abonnement, du vil betale for, med den alternative betalingsmetode.
3. Vælg de tre prikker (flere handlinger), og vælg derefter **Erstat betalingsmetode**.
4. I ruden **Erstat betalingsmetode** skal du vælge en alternativ betalingsmetode på rullelisten eller vælge at tilføje en betalingsmetode.
5. Hvis du tilføjer en betalingsmetode, skal du angive kort- eller kontooplysningerne og derefter vælge **Gem**.
6. Kontrollér, at den valgte betalingsmetode er korrekt, og vælg derefter **Erstat**.

## <a name="delete-a-payment-method"></a>Slet en betalingsmetode

Du kan kun slette en betalingsmetode, der ikke er knyttet til et abonnement eller en faktureringsprofil. Dette gælder for alle abonnementer, uanset deres status.

### <a name="delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached"></a>Slet en betalingsmetode uden tilknyttede abonnementer eller faktureringsprofiler

Hvis en betalingsmetode ikke er knyttet til nogen abonnementer eller faktureringsprofiler, kan du slette den med det samme.

1. I Administration skal du gå til siden **Fakturering** > **Fakturaer og betalinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Betalingsmetoder</a>.
2. Find den betalingsmetode, du vil slette, vælg de tre prikker, og vælg derefter **Slet**.
3. Vælg **Slet** nederst i den højre rude.

### <a name="delete-a-payment-method-with-subscriptions-or-billing-profiles-attached"></a>Slet en betalingsmetode med tilknyttede abonnementer eller faktureringsprofiler

Hvis der er knyttet en betalingsmetode til abonnementer eller faktureringsprofiler, skal du først erstatte den med en eksisterende betalingsmetode eller tilføje en ny og derefter slette den gamle betalingsmetode.

1. I Administration skal du gå til siden **Fakturering** > **Fakturaer og betalinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Betalingsmetoder</a>.
2. Vælg rækken for den betalingsmetode, der skal slettes. I højre rude vises eksisterende abonnementer, der bruger den pågældende betalingsmetode.
3. Vælg **Slet** i den højre rude.
4. Hvis du vil bruge en eksisterende betalingsmetode, skal du vælge en på rullelisten, vælge **Næste** og derefter vælge **Slet**.
    > [!NOTE]
    > Hvis du har abonnementer, der er knyttet til en faktureringsprofil, kan du kun bruge et kreditkort til at betale for dem. Hvis du har bankkonti, der er angivet på siden **Betalingsmetoder**, kan de ikke vælges på rullelisten.
5. Hvis du vil tilføje en ny betalingsmetode, skal du vælge **Tilføj betalingsmetode**.
6. Vælg den type betalingsmetode, du vil tilføje, angiv kontooplysningerne, og vælg derefter **Gem**.
7. Den nye betalingsmetode er allerede valgt på rullelisten. Vælg **Næste**.
8. Vælg **Slet**.

## <a name="troubleshoot-payment-methods"></a>Fejlfinding af betalingsmetoder

| Problem | Trin til fejlfinding |
|:----------|:-----|
|**Jeg får en fejlmeddelelse, hvor der står "Browseren er i øjeblikket indstillet til at blokere cookies".** |Indstil din browser til at tillade cookies fra tredjeparter, og prøv igen. |
|**Mit kredit- eller debetkort blev afvist.** |Hvis du betaler med kredit- eller debetkort, og dit kort afvises, modtager du en mail, hvor der står, at Microsoft ikke kunne behandle betalingen. Dobbelttjek, at kortoplysningerne&mdash;kortnummer, udløbsdato, navn på kortet og adresse, herunder by, stat og postnummer,&mdash;vises nøjagtigt, som de gør på kortet og dit kontoudtog. Du kan opdatere dine kortoplysninger og straks sende betalingen ved hjælp af linket **Afregn saldo** i afsnittet **Fakturering** på siden med abonnementsoplysninger. Du kan få mere at vide under [Hvad nu, hvis jeg har en udestående saldo?](pay-for-your-subscription.md#what-if-i-have-an-outstanding-balance)  <br/><br/>  Hvis du fortsat får vist meddelelsen "afvist", skal du kontakte din bank. Det er muligt, at dit kort ikke er aktivt. Hvis du for nylig har modtaget kortet i mailen med en opdateret udløbsdato, skal du kontrollere, at det er aktiveret. Din bank kan også fortælle dig, om dit kort ikke er godkendt til online, internationale eller tilbagevendende transaktioner. |
|**Jeg vil opdatere et kort- eller bankkontonummer.** |Du kan ikke ændre kort- eller kontonummeret på en eksisterende betalingsmetode. Hvis dit kort- eller kontonummer er ændret, skal du [erstatte det med en anden betalingsmetode](#replace-a-payment-method), som flytter alle aktive abonnementer fra betalingsmetoden til den nye, og [derefter slette den gamle betalingsmetode](#delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached). |
|**Jeg kun har ét kort eller én bankkonto på min konto, og jeg vil fjerne det/den.** |Hvis du kun har én betalingsmetode, skal du [erstatte den med en ny betalingsmetode](#replace-a-payment-method), før du kan slette den. |
|**Jeg kan ikke tilføje mit kort eller min bankkonto.**  |Du skal bruge en betalingsmetode, der er udstedt fra det samme land som din lejer. Hvis du har problemer med at angive dine kort- eller bankkontooplysninger, kan du [kontakte support](../../admin/get-help-support.md). |

## <a name="related-content"></a>Relateret indhold

[Betal for dit virksomhedsabonnement](pay-for-your-subscription.md) (artikel)\
[Administrer faktureringsprofiler](manage-billing-profiles.md) (artikel)\
[Skift din faktureringshyppighed](change-payment-frequency.md) (artikel)
