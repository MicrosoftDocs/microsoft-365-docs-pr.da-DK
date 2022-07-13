---
title: Politikker for identitets- og enhedsadgang til B2B-adgang for gæster og eksterne brugere – Microsoft 365 for enterprise-| Microsoft Docs
description: Beskriver den anbefalede betinget adgang og relaterede politikker til beskyttelse af adgang for gæster og eksterne brugere.
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
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: c6784f73b431826063d94794606b373662446324
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750138"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Politikker for adgang til gæsteadgang og B2B-ekstern brugeradgang

I denne artikel beskrives justering af de anbefalede Nul tillid politikker for identitets- og enhedsadgang, så gæster og eksterne brugere, der har en Azure Active Directory-konto (Azure AD) Business-to-Business (B2B), får adgang. Denne vejledning bygger på de [fælles politikker for identitets- og enhedsadgang](identity-access-policies.md).

Disse anbefalinger er designet til at gælde for **startniveauet** for beskyttelse. Men du kan også justere anbefalingerne baseret på dine specifikke behov for **virksomhedssikkerhed** og **specialiseret sikkerhedsbeskyttelse** .

Angivelse af en sti til B2B-konti, der skal godkendes med din Azure AD lejer, giver ikke disse konti adgang til hele dit miljø. B2B-brugere og deres konti har adgang til tjenester og ressourcer, f.eks. filer, der deles med dem af politikken Betinget adgang.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Opdatering af de almindelige politikker for at tillade og beskytte gæster og adgang til eksterne brugere

I dette diagram vises, hvilke politikker der skal tilføjes eller opdateres blandt de fælles politikker for identitets- og enhedsadgang for B2B-gæste- og ekstern brugeradgang.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="Oversigten over politikopdateringer til beskyttelse af gæsteadgang" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

I følgende tabel vises de politikker, du enten skal bruge for at oprette og opdatere. De fælles politikker linker til de tilknyttede konfigurationsinstruktioner i artiklen [Fælles politikker for identitets- og enhedsadgang](identity-access-policies.md) .

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv altid MFA for gæster og eksterne brugere](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Opret denne nye politik, og konfigurer: <ul><li>For **tildelinger > brugere og grupper > Medtag** skal du vælge **Vælg brugere og grupper** og derefter vælge **Alle gæste- og eksterne brugere**.</li><li>I forbindelse **med tildelinger > betingelser > Logon** skal du undlade at markere alle indstillinger for altid at gennemtvinge multifaktorgodkendelse.</li></ul>|
||[Kræv MFA, når logonrisikoen er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Rediger denne politik for at udelukke gæster og eksterne brugere.|

Hvis du vil medtage eller udelade gæster og eksterne brugere i politikker for betinget adgang, skal du markere **Alle gæste- og eksterne brugere** for **tildelinger > brugere og grupper > Medtag** eller **Udelad**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="Kontrolelementerne for udelader gæster og eksterne brugere" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>Flere oplysninger

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Adgang for gæster og eksterne brugere med Microsoft Teams

Microsoft Teams definerer følgende brugere:

- **Gæsteadgang** bruger en Azure AD B2B-konto, der kan tilføjes som medlem af et team og har adgang til teamets kommunikation og ressourcer.

- **Ekstern adgang** er for en ekstern bruger, der ikke har en B2B-konto. Ekstern brugeradgang omfatter invitationer, opkald, chats og møder, men omfatter ikke teammedlemskab og adgang til teamets ressourcer.

Du kan få flere oplysninger i [sammenligningen mellem gæster og adgang til eksterne brugere for teams](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

Du kan finde flere oplysninger om sikring af politikker for identitets- og enhedsadgang for Teams i [Politikanbefalinger til sikring af Teams-chats, -grupper og -filer](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Kræv altid MFA for gæstebrugere og eksterne brugere

Denne politik beder gæster om at tilmelde sig MFA i din lejer, uanset om de er registreret til MFA i deres lokale lejer. Når du tilgår ressourcer i din lejer, skal gæster og eksterne brugere bruge MFA til hver anmodning.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Udeladelse af gæster og eksterne brugere fra risikobaseret MFA

Organisationer kan gennemtvinge risikobaserede politikker for B2B-brugere ved hjælp af Azure AD Identity Protection, men der er begrænsninger i implementeringen af Azure AD Identitetsbeskyttelse for B2B-samarbejdsbrugere i en ressourcemappe på grund af deres eksisterende identitet i deres hjemmemappe. På grund af disse begrænsninger anbefaler Microsoft, at du udelukker gæster fra risikobaserede MFA-politikker og kræver, at disse brugere altid bruger MFA.

Du kan få flere oplysninger under [Begrænsninger for identitetsbeskyttelse for B2B-samarbejdsbrugere](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Udelader gæster og eksterne brugere fra enhedshåndtering

Kun én organisation kan administrere en enhed. Hvis du ikke udelukker gæster og eksterne brugere fra politikker, der kræver enhedsoverholdelse, blokerer disse politikker disse brugere.

## <a name="next-step"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Politikkerne for Microsoft 365-cloudapps og -Microsoft Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurer politikker for betinget adgang for:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender for Cloud Apps](mcas-saas-access-policies.md)
 
