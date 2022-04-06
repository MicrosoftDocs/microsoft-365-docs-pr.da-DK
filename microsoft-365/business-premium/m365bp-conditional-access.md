---
title: Slå sikkerhedsstandardindstillinger til for Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan sikkerhedsstandardindstillingerne kan hjælpe med at beskytte din organisation mod identitetsrelaterede angreb ved at give forudkonfigurerede sikkerhedsindstillinger til Microsoft 365 Business Premium.
ms.openlocfilehash: dfd0d3edff541d828b70d383641aaf66c93826b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705135"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Slå sikkerhedsstandardindstillinger til for Microsoft 365 Business Premium

Sikkerhedsstandardindstillingerne hjælper med at beskytte din organisation mod identitetsrelaterede angreb ved at give forudkonfigurerede sikkerhedsindstillinger, som Microsoft administrerer på vegne af din organisation. Disse indstillinger omfatter aktivering af Multi-Factor Authentication (MFA) for alle administratorer og brugerkonti. For de fleste organisationer tilbyder sikkerhedsstandards et godt niveau af ekstra logonsikkerhed.

Du kan finde flere oplysninger om sikkerhedsstandard og de politikker, de gennemtvinger, [under Hvad er sikkerhedsstandard?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Hvis dit abonnement blev oprettet den 22. oktober 2019, er sikkerhedsstandardindstillingerne muligvis blevet aktiveret automatisk for dig&mdash;, og du bør kontrollere dine indstillinger for at bekræfte.

Sådan aktiverer du sikkerhedsstandardindstillinger i Azure Active Directory (Azure AD) eller for at kontrollere, om de allerede er aktiveret:

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration med</a> sikkerhedsadministrator, betinget adgangsadministrator eller globale legitimationsoplysninger.

2. I venstre rude skal du **vælge Vis alle,** og derefter **skal du under Administration** vælge **Azure Active Directory**.

3. I venstre rude i **Azure Active Directory Administration skal du** vælge **Azure Active Directory**.

4. I menuen til venstre for dashboardet i sektionen **Administrer** skal du vælge **Egenskaber**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Skærmbillede af Azure Active Directory, der viser placeringen af menuelementet Egenskaber.":::

5. Nederst på siden Egenskaber **skal du** vælge Administrer **standardindstillinger for sikkerhed**.

6. I højre rude får du vist indstillingen **Aktivér standardindstillinger for** sikkerhed. Hvis **Ja** er valgt, er sikkerhedsstandardindstillingerne allerede aktiveret, og der kræves ingen yderligere handling. Hvis standardindstillingerne ikke er aktiveret i øjeblikket, skal du **vælge Ja** for at aktivere dem og derefter vælge **Gem**.

> [!NOTE]
> Hvis du har brugt Betingede adgangspolitikker, skal du deaktivere dem, før du bruger sikkerhedsstandardindstillinger.
>
> Du kan bruge enten sikkerhedsstandard eller Politikker for betinget adgang, men du kan ikke bruge begge på samme tid.

## <a name="consider-using-conditional-access"></a>Overvej at bruge Betinget adgang

Hvis din organisation har komplekse sikkerhedskrav, eller du har brug for mere detaljeret kontrol over dine sikkerhedspolitikker, bør du overveje at bruge Betinget adgang i stedet for sikkerhedsstandard for at opnå en lignende eller højere sikkerhedsudseendelse. 

Med Betinget adgang kan du oprette og definere politikker, der reagerer på logonhændelser og anmoder om yderligere handlinger, før en bruger får tildelt adgang til et program eller en tjeneste. Betingede access-politikker kan være specifikke og specifikke, så brugerne kan være produktive, uanset hvor og hvornår, men samtidig beskytte din organisation.

Sikkerhedsstandarden er tilgængelig for alle kunder, mens Betinget adgang kræver en licens til en af følgende planer:

- Azure Active Directory Premium P1 eller P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 eller E5
- Enterprise Mobility & Security E3 eller E5

Hvis du vil bruge Betinget adgang til at konfigurere politikker, der svarer til dem, der er aktiveret som sikkerhedsindstillinger, kan du se følgende trinvise vejledninger:

- [Kræv MFA til administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Kræv MFA til Azure-administration](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Kræv registrering af Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) – Kræver Azure AD Identity Protection, som er en del Azure Active Directory Premium P2

Du kan få mere at vide om Betinget adgang [under Hvad er Betinget adgang?](/azure/active-directory/conditional-access/overview) Du kan finde flere oplysninger om oprettelse af betingede access-politikker [under Oprette en politik for betinget adgang](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Hvis du har en plan eller licens, der indeholder Betinget adgang, men endnu ikke har oprettet nogen politikker for Betinget adgang, er du velkommen til at bruge sikkerhedsstandarden. Du skal dog deaktivere sikkerhedsstandardindstillingerne, før du kan bruge politikkerne for Betinget adgang.
