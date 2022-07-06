---
title: Opret opbevaringsmærkater for undtagelser
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
description: Instruktioner til oprettelse af opbevaringsmærkater for undtagelser fra opbevaringspolitikker for administration af datalivscyklus, så du kan bevare det, du har brug for, og slette det, du ikke har brug for.
ms.openlocfilehash: 0951ce1fea2f9324c19ec0bf17451d458b4914d1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632569"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Opret opbevaringsmærkater for undtagelser fra dine opbevaringspolitikker

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Som en del af din strategi for datastyring for at bevare det, du har brug for, og slette det, du ikke har brug for, skal du muligvis oprette et par opbevaringsmærkater for elementer, der har brug for undtagelser fra dine opbevaringspolitikker.

Opbevaringspolitikker gælder automatisk for alle elementer på objektbeholderniveau (f.eks. SharePoint-websteder, brugerpostkasser osv.), og opbevaringsmærkater gælder for individuelle elementer, f.eks. et SharePoint-dokument eller en mail.

Sørg for at forstå [principperne for opbevaring,](retention.md#the-principles-of-retention-or-what-takes-precedence) før du bruger opbevaringsmærkater til at supplere en opbevaringspolitik for bestemte SharePoint-, OneDrive- eller Exchange-elementer. Du bruger typisk opbevaringsmærkater til at bevare bestemte elementer, der er længere end en anvendt opbevaringspolitik, men de kan også bruges til at tilsidesætte automatisk sletning ved slutningen af opbevaringsperioden eller anvende en anden periode for sletning.

Som et typisk eksempel: Størstedelen af indholdet på dine SharePoint-websteder skal bevares i tre år, hvilket er omfattet af en opbevaringspolitik. Men du har nogle kontraktdokumenter, der skal opbevares i syv år. Disse undtagelser kan håndteres med opbevaringsmærkater. Når du har tildelt opbevaringspolitikken til alle SharePoint-websteder, skal du anvende opbevaringsbeskrivelserne på kontraktdokumenterne. Alle SharePoint-elementer opbevares i tre år, og kun kontraktdokumenterne opbevares i syv år.

Du kan få flere eksempler på, hvordan opbevaringsmærkater kan bruges som undtagelser til opbevaringspolitikker, under [Kombiner opbevaringspolitikker og opbevaringsmærkater](retention.md#combining-retention-policies-and-retention-labels).

Opbevaringsmærkater understøtter også flere funktioner end opbevaringspolitikker. Du kan få flere oplysninger under [Sammenlign funktioner for opbevaringspolitikker og opbevaringsmærkater](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Brug følgende oplysninger til at hjælpe dig med at oprette opbevaringsmærkater for at supplere opbevaringspolitikker som en del af din strategi for administration af datalivscyklusser.

> [!NOTE]
> Opret opbevaringsmærkater fra **dataadministrationsløsningen** i stedet for **datalivscyklusstyring** , hvis du har brug for at bruge opbevaringsmærkater til at administrere elementer af høj værdi for forretnings-, juridiske eller lovmæssige krav til registrering. Du vil f.eks. bruge hændelsesbaseret opbevarings- eller dispositionsgennemgang. Du kan finde instruktioner under [Brug filplan til at oprette og administrere opbevaringsmærkater](file-plan-manager.md).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator for din organisation har fuld tilladelse til at oprette og redigere opbevaringsmærkater og deres politikker. Hvis du ikke logger på som global administrator, skal du se [Tilladelser til opbevaringspolitikker og opbevaringsmærkater](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-data-lifecycle-management"></a>Sådan opretter du opbevaringsmærkater til administration af datalivscyklus

1. I [Microsoft Purview-compliance-portal skal du](https://compliance.microsoft.com/) navigere til: Fanen **Labels** til **administration af** >  **løsningers** >  datalivscyklus > + **Opret en mærkat**
    
    Kan du ikke se løsningen til **administration af datalivscyklus** med det samme? Vælg først **Vis alle**. 

2. Følg prompterne for at oprette opbevaringsmærkaten. Vær forsigtig med, hvilket navn du vælger, da dette ikke kan ændres, når etiketten er gemt.
    
    Du kan få flere oplysninger om opbevaringsindstillingerne under [Indstillinger for opbevaring og sletning af indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

3. Når du har oprettet etiketten, og du kan se indstillingerne for publicering af etiketten, skal du anvende etiketten automatisk eller blot gemme etiketten: Vælg **Gem blot etiketten nu**, og vælg derefter **Udført**.

4. Gentag disse trin for at oprette flere opbevaringsmærkater, som du skal bruge til forskellige opbevaringsindstillinger.

Hvis du vil redigere en eksisterende etiket, skal du vælge den og derefter vælge indstillingen **Rediger mærkat** for at starte konfigurationen Rediger opbevaringsmærkat, der giver dig mulighed for at ændre mærkatbeskrivelserne og eventuelle berettigede indstillinger.

De fleste indstillinger kan ikke ændres, når etiketten er oprettet og gemt, herunder:
- Navnet på opbevaringsmærkaten og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når opbevaringsperioden er baseret på, hvornår elementer blev mærket.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har oprettet opbevaringsmærkater, er de klar til at blive føjet til elementer ved at publicere mærkaterne eller automatisk anvende dem:
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)
