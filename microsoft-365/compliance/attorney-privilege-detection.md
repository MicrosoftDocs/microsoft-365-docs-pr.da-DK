---
title: Konfigurer registrering af rettigheder for advokater og klienter i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug modellen til registrering af rettigheder for advokatklienten til at bruge den maskinel indlæringsbaserede registrering af privilegeret indhold, når du gennemgår indhold i en Microsoft Purview eDiscovery (Premium)-sag.
ms.openlocfilehash: 9f81ff216ecf0045aec69191b3a61916b6ea3081
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624625"
---
# <a name="set-up-attorney-client-privilege-detection-in-ediscovery-premium"></a>Konfigurer registrering af rettigheder for advokater og klienter i eDiscovery (Premium)

Et vigtigt og dyrt aspekt af gennemsynsfasen af en eDiscovery-proces er gennemsyn af dokumenter for privilegeret indhold. Microsoft Purview eDiscovery (Premium) leverer maskinel indlæringsbaseret registrering af privilegeret indhold for at gøre denne proces mere effektiv. Denne funktion kaldes *registrering af rettigheder for advokater og klienter*.

## <a name="how-does-it-work"></a>Hvordan fungerer det?

Når registrering af rettigheder for advokater og klienter er aktiveret, behandles alle dokumenter i et anmeldelsessæt af modellen til registrering af rettigheder for advokat/klient, når du [analyserer dataene](analyzing-data-in-review-set.md) i korrektursættet. Modellen søger efter to ting:

- Privilegeret indhold – modellen bruger maskinel indlæring til at bestemme sandsynligheden for, at dokumentet indeholder indhold, der er lovligt.

- Deltagere – som en del af oprettelsen advokat-klient rettighedsregistrering, skal du indsende en liste over advokater til din organisation. Modellen sammenligner derefter deltagerne i dokumentet med advokatlisten for at afgøre, om et dokument har mindst én advokatdeltager.

Modellen opretter følgende tre egenskaber for hvert dokument:

- **AttorneyClientPrivilegeScore:** Sandsynligheden for, at dokumentet er juridisk. værdierne for scoren er mellem **0** og **1**.

- **HasAttorney:** Denne ejendom er angivet til **sand** , hvis en af dokumentdeltagerne er angivet på advokatlisten. Ellers er værdien **false**. Værdien er også angivet til **falsk** , hvis din organisation ikke har uploadet en advokatliste.

- **IsPrivilege:** Denne ejendom er angivet til **sand** , hvis værdien for **AttorneyClientPrivilegeScore** er over tærsklen, *eller* hvis dokumentet har en advokatdeltager; Ellers er værdien indstillet til **falsk**.

Disse egenskaber (og deres tilsvarende værdier) føjes til dokumenternes filmetadata i et korrektursæt som vist på følgende skærmbillede:

![Egenskaber for rettigheder for advokater og klienter, der vises i filmetadata.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Der kan også søges i disse tre egenskaber i et korrektursæt. Du kan få flere oplysninger under [Forespørg om dataene i et korrektursæt](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Konfigurer modellen til registrering af rettigheder for advokater og klienter

Hvis du vil aktivere modellen til registrering af rettighedsregistrering for advokatklienter, skal din organisation aktivere den og derefter uploade en advokatliste.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Trin 1: Slå registrering af rettighedsregistrering for advokater og klienter til

En person, der er eDiscovery-administrator i din organisation (medlem af undergruppen eDiscovery-administrator i rollegruppen eDiscovery Manager), skal gøre modellen tilgængelig i dine eDiscovery-tilfælde (Premium).

1. I Microsoft Purview-compliance-portal skal du gå til [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **indstillinger for eDiscovery (Premium).**

   ![Vælg indstillinger for eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen **Analytics** og derefter slå **rettighedsregistreringen for advokat/klient** til til.

   ![Klik på Til/fra for at slå rettighedsregistrering for advokat/klient til](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Klik på **Gem** for at gemme ændringen.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Trin 2: Upload en liste over advokater (valgfrit)

For at drage fuld fordel af modellen til registrering af rettighedsregistrering for advokatklienter og bruge resultaterne af den tidligere beskrevne **har advokat** eller **potentielt privilegerede** registrering, anbefaler vi, at du uploader en liste over mailadresser til de advokater og juridisk personale, der arbejder for din organisation.

Sådan uploader du en advokatliste til brug for modellen til registrering af rettigheder for advokatklienten:

1. Opret en .csv fil (uden en overskriftsrække), og tilføj mailadressen for hver relevant person på en separat linje. Gem filen på den lokale computer.

2. På siden **Indstillinger for** eDiscovery (Premium) skal du vælge fanen **Analytics** .

   Siden **Med rettigheder for advokat/klient** vises, og til/ **fra-knappen for rettighedsregistrering for advokat/klient** er slået til.

   ![Side med rettigheds-/rettigheds-adgang for advokater](..\media\AeDUploadAttorneyList1.png)

3. Vælg **Vælg fil** , og find og vælg derefter den .csv fil, du oprettede i trin 1.

4. Vælg **Gem** for at uploade advokatlisten.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Brug modellen til registrering af rettigheder for advokater og klienter

Følg trinnene i dette afsnit for at bruge rettighedsregistrering for advokater og klienter til dokumenter i et anmeldelsessæt.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Trin 1: Opret en i-mærke-gruppe med model til registrering af rettigheder for advokatklienter

En af de primære måder at se resultaterne af rettighedsregistrering for advokat/klient i din anmeldelsesproces er ved hjælp af en gruppe med i-mærker. En i-mærke-gruppe angiver resultaterne af rettighedsregistreringen for advokat/klient og viser resultaterne på linje ud for mærkerne i en i-mærke-gruppe. Det giver dig mulighed for hurtigt at identificere potentielt privilegerede dokumenter under dokumentgennemsyn. Du kan også bruge mærkerne i i-mærke-gruppen til at mærke dokumenter som privilegerede eller ikke-privilegerede. Du kan finde flere oplysninger om i-mærker [under Konfigurer i-mærker i eDiscovery (Premium)](smart-tags.md).

1. I det korrektursæt, der indeholder de dokumenter, du analyserede i trin 1, skal du vælge **Administrer korrektursæt** og derefter vælge **Administrer mærker**.

2. Under **Mærker** skal du vælge rullepilen ud for **Tilføj gruppe** og derefter vælge **Tilføj i-mærke-gruppe**.

   ![Vælg "Tilføj i-mærke-gruppe".](../media/AeDCreateSmartTag.png)

3. På siden **Vælg en model til dit i-mærke** skal du vælge **Vælg** ud for **Rettigheden Advokat/klient**.

   Der vises en kodegruppe med navnet **Advokat/klient-rettighed** . Den indeholder to underordnede mærker med navnet **Positiv** og **Negativ**, som svarer til de mulige resultater, der produceres af modellen.

   ![Advokat-klient privilegium i-mærke-gruppe.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Omdøb kodegruppen og mærkerne, så de passer til din anmeldelse. Du kan f.eks. omdøbe **Positiv** til **Privilegeret** og **Negativ** til **Ikke privilegeret**.

### <a name="step-2-analyze-a-review-set"></a>Trin 2: Analysér et korrektursæt

Når du analyserer dokumenterne i et korrektursæt, køres modellen til registrering af rettigheder for advokatklienten også, og de tilsvarende egenskaber (beskrevet i [Hvordan fungerer det?](#how-does-it-work)) føjes til alle dokumenter i korrektursættet. Du kan finde flere oplysninger om analyse af data i korrektursæt [under Analysér data i et korrektursæt i eDiscovery (Premium)](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Trin 3: Brug i-mærke-gruppen til gennemgang af privilegeret indhold

Når du har analyseret korrektursættet og konfigureret i-mærker, er det næste trin at gennemse dokumenterne. Hvis modellen har bestemt, at dokumentet muligvis er privilegeret, angiver det tilsvarende i-mærke i **panelet Tagging** følgende resultater, der er produceret af rettighedsregistreringen for advokat/klient:

- Hvis dokumentet indeholder indhold, der kan være juridisk, vises det **juridiske indhold** ud for det tilsvarende i-mærke (som i dette tilfælde er standard-positivkoden).

- Hvis dokumentet har en deltager, der findes på organisationens advokatliste, vises etiketten **Attorney** ud for det tilsvarende i-mærke (som i dette tilfælde også er standardmærket **Positiv** ).

- Hvis dokumentet har indhold, der kan være juridisk *og* har en deltager fundet på advokatlisten, vises både **juridisk indhold**  og **advokatmærkater** . 

Hvis modellen bestemmer, at et dokument ikke indeholder indhold, der er juridisk eller ikke indeholder en deltager fra advokatlisten, vises ingen af mærkaterne i taggingpanelet.

Følgende skærmbilleder viser f.eks. to dokumenter. Den første indeholder indhold, der er lovligt og har en deltager fundet på listen over advokater. Den anden indeholder ingen af delene og viser derfor ingen navne.

![Dokument med indholdsmærkater fra advokater og juridiske personer.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Dokument uden navne.](../media/AeDTaggingPanelNegative.png)

Når du har gennemset et dokument for at se, om det indeholder privilegeret indhold, kan du mærke dokumentet med den relevante kode.
