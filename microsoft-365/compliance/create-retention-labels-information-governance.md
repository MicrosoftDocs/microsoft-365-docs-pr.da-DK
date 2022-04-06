---
title: Oprette opbevaringsnavne for undtagelser til dine opbevaringspolitikker
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Vejledning til at oprette opbevaringsmærkater for undtagelser til opbevaringspolitikker for styring af oplysninger, så du kan bevare det, du har brug for, og slette det, du ikke har brug for.
ms.openlocfilehash: 699df2a62204115c60271a5d5aa70613db48c7d5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63607441"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Oprette opbevaringsnavne for undtagelser til dine opbevaringspolitikker

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Som en del af din strategi for styringsoplysninger til at bevare det, du har brug for, og slette det, du ikke har, kan det være nødvendigt at oprette et par opbevaringsnavne for elementer, der har brug for undtagelser til dine opbevaringspolitikker. 

Mens opbevaringspolitikker automatisk gælder for alle elementer på objektbeholderniveau (f.eks. SharePoint-websteder, brugerpostkasser osv.), gælder opbevaringsetiketter for individuelle elementer, f.eks. et SharePoint-dokument eller en mail.

Sørg for, at du [](retention.md#the-principles-of-retention-or-what-takes-precedence) forstår principperne for opbevaring, før du bruger opbevaringsetiketter til at supplere en opbevaringspolitik for bestemte SharePoint, OneDrive eller Exchange elementer. Typisk skal du bruge opbevaringsetiketter til at bevare bestemte elementer, som er længere end en anvendt opbevaringspolitik, men de kan også bruges til at tilsidesætte automatisk sletning i slutningen af opbevaringsperioden eller anvende en anden sletningsperiode.

Som et typisk eksempel: Størstedelen af indholdet på dine SharePoint-websteder skal bevares i tre år, hvilket er dækket af en opbevaringspolitik. Men du har nogle kontraktdokumenter, der skal bevares i syv år. Disse undtagelser kan adresseres med opbevaringsetiketter. Når du har tildelt opbevaringspolitikken til alle SharePoint, skal du anvende opbevaringsetiketterne på kontraktdokumenterne. Alle SharePoint elementer bevares i tre år, og kun kontraktdokumenterne bevares i syv år.

Du kan finde flere eksempler på, hvordan opbevaringsnavne kan bruges som undtagelser til opbevaringspolitikker, under [Kombinere opbevaringspolitikker og opbevaringsetiketter](retention.md#combining-retention-policies-and-retention-labels).

Opbevaringsnavne understøtter også flere funktioner end opbevaringspolitikker. Få mere at vide under [Sammenlign funktioner for opbevaringspolitikker og opbevaringsmærkater](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Brug følgende oplysninger som en hjælp til at oprette opbevaringsetiketter som et supplement til opbevaringspolitikker som en del af din strategi for informationsstyring.

> [!NOTE]
> Opret opbevaringsnavne fra  løsningen Datastyring i stedet  for Styring af oplysninger, hvis du har brug for at bruge opbevaringsmærkater til livscyklusstyring af elementer af høj værdi til forretningsmæssige, juridiske eller lovgivningsmæssige krav til registrering. Du vil f.eks. bruge hændelsesbaseret opbevarings- eller dispositionsvurdering. Du kan finde en vejledning [under Brug filplan til at oprette og administrere opbevaringsnavne](file-plan-manager.md).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator i organisationen har fuld tilladelse til at oprette og redigere opbevaringsnavne og deres politikker. Hvis du ikke logger på som global administrator, skal du se [Tilladelser til opbevaringspolitikker og opbevaringsnavne](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-information-governance"></a>Sådan opretter du opbevaringsnavne til informationsstyring

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com/) du gå til: **SolutionsInformation** >  **governanceLabels** >  > + **Create a label**
    
    Kan du ikke straks se løsningen **til styring af** oplysninger? Vælg først **Vis alle**. 

2. Følg instruktionerne for at oprette en opbevaringsetiket. Vær forsigtig med det navn, du vælger, da dette ikke kan ændres, når etiketten er gemt.
    
    Du kan finde flere oplysninger om opbevaringsindstillingerne [under Indstillinger opbevaring og sletning af indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

3. Når du har oprettet navnet, og du får vist mulighederne for at publicere navnet, skal du anvende den automatisk eller blot gemme navnet: Vælg Gem blot etiketten **indtil** videre, og vælg derefter **Udført**.

4. Gentag disse trin for at oprette flere opbevaringsnavne, du har brug for til forskellige opbevaringsindstillinger.

Hvis du vil redigere en eksisterende etiket, skal du markere den og  derefter vælge indstillingen Rediger etiket for at starte konfigurationen af Rediger opbevaringsetiket, som gør det muligt at ændre etiketbeskrivelserne og alle berettigede indstillinger.

De fleste indstillinger kan ikke ændres, efter etiketten er oprettet og gemt, hvilket omfatter:
- Opbevaringsnavnet og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når en opbevaringsperiode er baseret på, hvornår elementerne blev mærket.

## <a name="next-steps"></a>Næste trin

Nu har du oprettet opbevaringsmærkater, de er klar til at blive føjet til elementer ved at publicere etiketterne eller automatisk anvende dem:
- [Udgive opbevaringsmærkater og anvende dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)