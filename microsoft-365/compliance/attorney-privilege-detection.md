---
title: Konfigurer registrering af advokat-klientrettigheder i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Brug attorney-client privilege detection-modellen til at bruge den maskinlæringsbaserede registrering af privilegeret indhold, når du gennemser indhold i Advanced eDiscovery sag.
ms.openlocfilehash: 5e8a9e1ef0cf8cd8375cd6ce9a0b4d210840e838
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589516"
---
# <a name="set-up-attorney-client-privilege-detection-in-advanced-ediscovery"></a>Konfigurer registrering af advokat-klientrettigheder i Advanced eDiscovery

Et større og dyrere aspekt af gennemsynsfasen af en eDiscovery-proces er at gennemse dokumenter for privilegeret indhold. Advanced eDiscovery giver maskinlæringsbaseret registrering af privilegeret indhold for at gøre denne proces mere effektiv. Denne funktion kaldes registrering *af advokatklientrettigheder*.

## <a name="how-does-it-work"></a>Hvordan fungerer det?

Når registrering af advokat-klient-rettigheder er aktiveret, behandles alle dokumenter i et gennemsynssæt af registreringsmodellen for advokatklientrettigheder, når du analyserer [dataene](analyzing-data-in-review-set.md) i gennemsynssættet. Modellen søger efter to ting:

- Særligt indhold – Modellen bruger maskinlæring til at afgøre sandsynligheden for, at dokumentet indeholder indhold af juridisk karakter.

- Participants – As part of setting up attorney-client privilege detection, you have to submit a list of attorneys for your organization. Modellen sammenligner derefter deltagerne i dokumentet med listen over advokater for at afgøre, om et dokument har mindst én advokatdeltager.

Modellen frembringer følgende tre egenskaber for hvert dokument:

- **AttorneyClientPrivilegeScore:** Sandsynligheden for, at dokumentet er juridisk. værdierne for scoren er mellem **0** og **1**.

- **HasAttorney:** This property is set to **true** if one of the document participants is listed in the attorney list; Ellers er værdien **falsk**. Værdien er også angivet til **falsk** , hvis din organisation ikke har uploadet en advokatliste.

- **IsPrivilege:** This property is set to **true** if the value for **AttorneyClientPrivilegeScore is above** the threshold *or* if the document has an attorney participant; Ellers er værdien indstillet til **falsk**.

Disse egenskaber (og deres tilsvarende værdier) føjes til filens metadata i et korrektursæt, som vist på følgende skærmbillede:

![Attorney-client privilege properties shown in file metadata.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Disse tre egenskaber kan også søges i et korrektursæt. Få mere at vide under [Forespørg dataene i et gennemsynssæt](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Konfigurere registreringsmodellen for attorney-client-rettigheder

For at aktivere registreringsmodellen for attorney-client privilege, skal din organisation aktivere den og derefter uploade en liste over advokater.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Trin 1: Slå registrering af advokat-klient-rettigheder til

En person, der er eDiscovery-administrator i din organisation (medlem af undergruppen eDiscovery-administrator i rollegruppen eDiscovery Manager), skal gøre modellen tilgængelig i dine Advanced eDiscovery-sager.

1. I Microsoft 365 Overholdelsescenter skal du gå til [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **Advanced eDiscovery indstillinger**.

   ![Vælg Advanced eDiscovery indstillinger](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen **Analytics** og derefter slå indstillingen til registrering af **advokat-klientrettigheder** til til.

   ![Klik på til/fra-knap for at aktivere registrering af Attorney-client-rettigheder](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Klik **på Gem** for at gemme ændringen.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Trin 2: Upload en liste over advokaterne (valgfrit)

To take full advantage of the attorney-client privilege detection model and use the Results of the **Has Attorney** or **Potentially Privileged** detection that was previously described, we recommend that you upload a list of email addresses for the malwares and legal personnel who work for your organization.

To upload an attorney list for use by the attorney-client privilege detection model:

1. Opret en .csv fil (uden en kolonneoverskrift), og tilføj mailadressen for hver relevante person på en separat linje. Gem denne fil på din lokale computer.

2. På siden Advanced eDiscovery **Indstillinger** skal du vælge **fanen** Analyse.

   The **Attorney-client privilege** page is displayed, and the **Attorney-client privilege detection toggle** is turned on.

   ![Pop op-side med advokat-klientrettigheder](..\media\AeDUploadAttorneyList1.png)

3. Vælg **Vælg fil,** og find og vælg derefter den .csv fil, du oprettede i trin 1.

4. Vælg **Gem** for at uploade listen over advokater.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Bruge registreringsmodellen for attorney-client-rettigheder

Følg trinnene i dette afsnit for at bruge registrering af advokat-klient-rettigheder til dokumenter i et gennemsynssæt.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Trin 1: Opret en i-mærkegruppe med model til registrering af klientrettigheder

En af de primære måder at se resultaterne af registrering af advokat-klient-rettigheder i gennemsynsprocessen er ved hjælp af en i-mærkegruppe. En i-mærkegruppe angiver resultaterne af registrering af advokat-klient-rettigheder og viser resultaterne i linje ud for mærkerne i en i-mærkegruppe. Dette giver dig mulighed for hurtigt at identificere potentielt privilegerede dokumenter under dokumentgennemsyn. Desuden kan du også bruge mærkerne i i-mærkegruppen til at mærke dokumenter som privilegerede eller ikke-privilegerede. Du kan finde flere oplysninger om [i-mærker i Konfigurere i-mærker Advanced eDiscovery](smart-tags.md).

1. I det korrektursæt, der indeholder de dokumenter, du analyserede i trin 1, skal du vælge **Administrer korrektursæt** og derefter vælge **Administrer mærker**.

2. Under **Mærker** skal du vælge rulle ned ud for **Tilføj gruppe og** derefter vælge **Tilføj i-mærkegruppe**.

   ![Vælg "Tilføj i-mærkegruppe".](../media/AeDCreateSmartTag.png)

3. På siden **Vælg en model til dit i-mærke** skal du vælge **Vælg ud** for **Attorney-client privilege**.

   En kodegruppe med **navnet Attorney-client privilege** is displayed. Den indeholder to underordnede mærker kaldet **Positiv** og **Negativ**, hvilket svarer til de mulige resultater, der produceres af modellen.

   ![Attorney-client privilege i tag group.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Omdøb mærkegruppen og mærkerne efter behov til din gennemgang. Du kan f.eks. omdøbe **Positiv til** **Privilegeret** og **Negativ til** **Ikke privilegeret**.

### <a name="step-2-analyze-a-review-set"></a>Trin 2: Analysér et korrektursæt

Når du analyserer dokumenterne i et gennemsynssæt, kører registreringsmodellen med advokatklientrettigheder også, og de tilsvarende egenskaber (beskrevet i Hvordan virker det [?](#how-does-it-work)) føjes til hvert dokument i korrektursættet. Du kan finde flere oplysninger om analyse af data i et gennemsynssæt i [Analysér data i et Advanced eDiscovery](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Trin 3: Brug i-mærkegruppen til gennemgang af privilegeret indhold

Når du har analyseret korrektursættet og konfigureret i-mærker, er næste trin at gennemse dokumenterne. Hvis modellen har fastlagt, at dokumentet potentielt er privilegeret, vil det tilsvarende i-mærke  i panelet Mærkning angive følgende resultater, der er produceret af registrering af advokat-klient-rettigheder:

- Hvis dokumentet har indhold, der kan være lovligt, vises etiketten Juridisk indhold  ud for det tilsvarende i-mærke (som i dette tilfælde er **standardmærket Positiv**).

- If the document has a participant who is found in your organization's attorney list, the label **Attorney** is displayed next to the corresponding i tag (which in this case is also the default **Positive** tag).

- If the document has content that may be legal in nature *and* has a participant found in the attorney list, both the **Legal content**  and **Attorney** labels are displayed. 

If the model determines that a document doesn't contain content that is legal in nature or doesn't contain a participant from the attorney list, then neither label is displayed in the tagging panel.

Følgende skærmbilleder viser f.eks. to dokumenter. The first one contains content that is legal in nature and has a participant found in the list of attorneys. Den anden indeholder ingen af etiketterne og viser derfor ikke nogen etiketter.

![Dokument med mærkater med advokatindhold og juridisk indhold.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Dokument uden etiketter.](../media/AeDTaggingPanelNegative.png)

Når du har gennemset et dokument for at se, om det indeholder privilegeret indhold, kan du mærke dokumentet med det relevante mærke.
