---
title: Politikker for identitets- og enhedsadgang til at tillade gæste- og ekstern bruger B2B-adgang Microsoft 365 til | Microsoft Docs
description: Beskriver den anbefalede Betingede adgang og relaterede politikker til beskyttelse af gæsters og eksterne brugeres adgang.
ms.prod: m365-security
ms.topic: article
ms.author: dansimp
author: dansimp
audience: Admin
manager: Laurawi
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 28b389292ed733318e5796a1be3ed9c11d2df462
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466603"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Politikker for at tillade gæsteadgang og B2B-ekstern brugeradgang

I denne artikel beskrives det, hvordan du justerer de anbefalede politikker for Nul tillid-identitet og enhedsadgang for at tillade adgang for gæster og eksterne brugere, der har en Azure Active Directory-konto (Azure AD) Business-to-Business (B2B). Denne vejledning er baseret på de almindelige [politikker for identitet og enhedsadgang](identity-access-policies.md).

Disse anbefalinger er designet til at gælde **for udgangspunktet** for beskyttelse. Men du kan også justere anbefalingerne ud fra dine specifikke behov for **virksomhedssikkerhed og** **særlig sikkerhedsbeskyttelse** .

Hvis du har oprettet en sti til B2B-konti, der skal godkendes med din Azure AD-lejer, får disse konti ikke adgang til hele miljøet. B2B-brugere og deres konti har adgang til tjenester og ressourcer, f.eks. filer, der deles med dem af politikken Betinget adgang.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Opdatering af de fælles politikker for at tillade og beskytte gæster og ekstern brugeradgang

Dette diagram viser, hvilke politikker der skal tilføjes eller opdateres mellem de almindelige politikker for identitets- og enhedsadgang for B2B-gæster og ekstern brugeradgang.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="Oversigten over politikopdateringer til beskyttelse af gæsteadgang" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

I følgende tabel vises de politikker, du enten skal oprette og opdatere. De fælles politikker linker til de tilknyttede konfigurationsinstruktioner i [artiklen Fælles identitets- og enhedsadgangspolitikker](identity-access-policies.md) .

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA altid for gæster og eksterne brugere](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Opret denne nye politik, og konfigurer: <ul><li>Til **opgaver > brugere og grupper > Inkluder** skal du vælge **Vælg** brugere og grupper og derefter **vælge Alle gæster og eksterne brugere**.</li><li>For **Opgaver > Betingelser >** logon skal du lade alle indstillinger være umarkeret, hvis du altid vil gennemtvinge Multi-Factor Authentication (MFA).</li></ul>|
||[Kræv MFA, når logonrisici er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Rediger denne politik for at udelukke gæster og eksterne brugere.|

Hvis du vil medtage eller udelade gæster og eksterne brugere i politikker for betinget adgang, skal du for Opgaver > Brugere og grupper **> Medtag** eller **Udelad** markere Alle gæster **og eksterne brugere**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="Kontrolelementerne til at udelukke gæster og eksterne brugere" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>Flere oplysninger

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Gæster og ekstern brugeradgang med Microsoft Teams

Microsoft Teams definerer følgende brugere:

- **Gæsteadgang** bruger en Azure AD B2B-konto, der kan tilføjes som medlem af et team og har adgang til kommunikation og ressourcer for teamet.

- **Ekstern adgang** er for en ekstern bruger, der ikke har en B2B-konto. Adgang for eksterne brugere omfatter invitationer, opkald, chats og møder, men omfatter ikke teammedlemskab og adgang til teamets ressourcer.

Du kan finde flere oplysninger i [sammenligningen mellem gæster og ekstern brugeradgang for teams](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

Du kan finde flere oplysninger om beskyttelse af identitet og politikker for enhedsadgang for Teams i Politikanbefalinger [til sikring Teams chatsamtaler, grupper og filer](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Kræv MFA altid for gæster og eksterne brugere

Denne politik beder gæster om at tilmelde sig MFA i din lejer, uanset om de er registreret til MFA i deres hjemmelejer. Når du tilgår ressourcer i din lejer, skal gæster og eksterne brugere bruge MFA for hver anmodning.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Ekskluder gæster og eksterne brugere fra risikobaseret MFA

Selvom organisationer kan håndhæve risikobaserede politikker for B2B-brugere, der bruger Azure AD Identity Protection, er der begrænsninger i implementeringen af Azure AD Identity Protection til brugere af B2B-samarbejde i en ressourcemappe på grund af deres identitet, der findes i deres hjemmemappe. På grund af disse begrænsninger anbefaler Microsoft, at du udelader gæster fra risikobaserede MFA-politikker og kræver, at disse brugere altid bruger MFA.

Du kan finde flere oplysninger under [Begrænsninger for identitetsbeskyttelse for brugere af B2B-samarbejde](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Ekskluder gæster og eksterne brugere fra enhedsstyring

Kun én organisation kan administrere en enhed. Hvis du ikke udelukker gæster og eksterne brugere fra politikker, der kræver overholdelse af enhed, blokerer disse brugere for disse politikker.

## <a name="next-step"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Politikkerne for Microsoft 365 apps og Microsoft Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurere Betingede adgangspolitikker for:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender for Cloud Apps](mcas-saas-access-policies.md)
 
