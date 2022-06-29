---
title: Arbejde med enhedsgrupper i Microsoft 365 Business Premium
description: Få mere at vide om enhedsgrupper, og hvordan du anvender politikker med Intune i Microsoft 365 Business Premium, og øg beskyttelsen mod cyberangreb.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a8d132669319e26adea53498e7dcf78a82a3250d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489720"
---
# <a name="device-groups-and-categories-in-microsoft-365-business-premium"></a>Enhedsgrupper og -kategorier i Microsoft 365 Business Premium

Microsoft 365 Business Premium omfatter beskyttelse af slutpunkter via Microsoft Defender til virksomheder og Microsoft Intune. Politikker for enhedsbeskyttelse anvendes på enheder via visse samlinger, der kaldes enhedsgrupper. I Intune grupperes enheder i enhedskategorier som en anden måde at organisere dem på. 

Denne artikel indeholder følgende afsnit:  

- [Arbejde med enhedsgrupper](#working-with-device-groups)
- [Sådan opretter du en ny enhedsgruppe](#create-a-device-group-in-the-microsoft-365-defender-portal)
- [Sådan opretter du en ny enhedskategori i Intune](#create-a-device-category-in-intune)

## <a name="working-with-device-groups"></a>Arbejde med enhedsgrupper

En enhedsgruppe er en samling af enheder, der er grupperet på grund af visse angivne kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du ekskluderer dem.

Med Microsoft 365 Business Premium har du standardenhedsgrupper, som du kan bruge. Standardenhedsgrupperne omfatter alle de enheder, der er onboardet til Defender for Business. Du kan dog også oprette nye enhedsgrupper for at tildele politikker for enhedsbeskyttelse med bestemte indstillinger til bestemte enheder.

Alle enhedsgrupper, herunder dine standardenhedsgrupper og brugerdefinerede enhedsgrupper, som du definerer, gemmes i [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-device-group-in-the-microsoft-365-defender-portal"></a>Opret en enhedsgruppe på Microsoft 365 Defender-portalen

Du kan oprette en ny enhedsgruppe, mens du er i gang med at oprette eller redigere en politik for enhedsbeskyttelse.

1. Gå til [Microsoft 365 Defender-portalen](https://security.microsoft.com), og log på.

2. Vælg **Enhedskonfiguration** i navigationsruden.

3. Udfør en af følgende handlinger:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.

    2. Vælg **+ Tilføj** for at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, skal du se [Få vist eller rediger politikker i Microsoft Defender til virksomheder](m365bp-view-edit-create-mdb-policies.md).

4. Gennemse oplysningerne i trinnet **Generelle oplysninger** , rediger dem, hvis det er nødvendigt, og vælg derefter **Næste**.

5. Vælg **Opret ny gruppe**.

6. Angiv et navn og en beskrivelse til enhedsgruppen, og vælg derefter **Næste**.

7. Vælg de enheder, der skal medtages i gruppen, og vælg derefter **Opret gruppe**.

8. Gennemse listen over enhedsgrupper for politikken på trinnet **Enhedsgrupper** . Hvis det er nødvendigt, skal du fjerne en gruppe fra listen. Vælg derefter **Næste**.

9. Gennemse og rediger indstillingerne efter behov på siden **Konfigurationsindstillinger** , og vælg derefter **Næste**. Du kan finde flere oplysninger om disse indstillinger [under Forstå næste generations konfigurationsindstillinger i Microsoft Defender til virksomheder](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. Gennemse alle indstillingerne i trinnet **Gennemse din politik** , foretag de nødvendige ændringer, og vælg derefter **Opret politik** eller **Opdater politik**.

## <a name="create-a-device-category-in-intune"></a>Opret en enhedskategori i Intune

Opret enhedskategorier i Intune, som brugerne skal vælge imellem, når de tilmelder en enhed.

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).

2. Vælg **Enhedskategorier** >  > **Opret enhedskategori** for at tilføje en ny kategori.

3. Angiv et navn til den nye kategori og en valgfri beskrivelse i ruden **Opret enhedskategori** .

4. Når du er færdig, skal du vælge **Opret**. Du kan se den nye kategori på listen.

Brug enhedskategorinavnet, når du opretter sikkerhedsgrupperne i Azure Active Directory (Azure AD). Når brugerne tilmelder deres enheder, får de vist en liste over de kategorier, du har konfigureret i Intune. Når de har valgt en kategori og afsluttet tilmeldingen, føjes deres enhed til den Active Directory-sikkerhedsgruppe, der er knyttet til den.

## <a name="create-dynamic-device-groups-in-azure-active-directory"></a>Opret dynamiske enhedsgrupper i Azure Active Directory

Du kan også angive Azure Active Directory-portalen (Azure AD) fra[https://portal.azure.com](https://portal.azure.com) Microsoft 365 Administration. I Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com/)) skal du vælge **Alle administrationscentre** og derefter vælge **Azure Active Directory**.

I Azure AD-portalen kan du oprette dynamiske grupper baseret på enhedskategorien og enhedskategorinavnet. Brug regler for dynamisk gruppe til automatisk at tilføje og fjerne enheder. Hvis en enheds attributter ændres, kigger systemet på reglerne for den dynamiske gruppe for mappen for at se, om enheden opfylder regelkravene (tilføjes) eller ikke længere opfylder regelkravene (fjernes).

Du kan oprette en dynamisk gruppe for enten enheder eller brugere, men ikke for begge. Du kan heller ikke oprette en enhedsgruppe baseret på enhedsejernes attributter. Regler for enhedsmedlemskab kan kun referere til enhedstilskrivelser. 

## <a name="after-device-groups-are-created"></a>Når der er oprettet enhedsgrupper

Nu, hvor der er oprettet kategorier og enhedsgrupper, skal brugere af iOS- og Android-enheder tilmelde deres enheder, og når de gør det, skal de vælge en kategori på listen over kategorier, der er konfigureret. Windows-brugere kan bruge Firmaportal-webstedet eller Firmaportal-appen til at vælge en kategori.

1. Når du har tilmeldt enheden, skal du gå til [firmaportalen](https://portal.microsoft.com) og vælge **Mine enheder**.

2. Vælg den tilmeldte enhed på listen, og vælg derefter en kategori.

Når du har valgt en kategori, føjes enheden automatisk til den tilsvarende gruppe. Hvis en enhed allerede er tilmeldt, før du konfigurerer kategorier, får brugeren vist en meddelelse om enheden på Firmaportal websted. Dette giver brugeren besked om at vælge en kategori, næste gang vedkommende får adgang til appen Firmaportal på iOS/iPadOS eller Android.

> [!NOTE]
> - Du kan redigere en enhedskategori i Azure Portal, men du skal manuelt opdatere alle Azure AD sikkerhedsgrupper, der refererer til denne kategori.
> - Hvis du sletter en kategori, viser enheder, der er tildelt den, kategorinavnet **Ikke tildelt**.

## <a name="view-the-categories-of-devices-that-you-manage"></a>Få vist kategorierne for de enheder, du administrerer

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com), vælg **Enheder** > **Alle enheder**.

2. På listen over enheder skal du undersøge kolonnen **Enhedskategori** .

3. Hvis kolonnen Enhedskategori ikke vises, skal du vælge **Anvend kolonnekategori** >  > .

## <a name="change-the-category-of-a-device"></a>Skift kategorien for en enhed

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com), vælg **Enheder** > **Alle enheder**. 

2. Vælg den ønskede kategori på listen for at se dens egenskaber.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har fuldført dine primære missioner, kan du bruge tid på at konfigurere dine [svarteams](m365bp-security-incident-management.md) og [vedligeholde dit miljø](m365bp-maintain-environment.md).
