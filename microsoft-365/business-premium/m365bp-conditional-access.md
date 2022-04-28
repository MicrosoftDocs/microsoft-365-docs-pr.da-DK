---
title: Sikkerhedsstandarder og betinget adgang
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan sikkerhedsstandarder kan hjælpe med at beskytte din organisation mod identitetsrelaterede angreb ved at angive forudkonfigurerede sikkerhedsindstillinger for Microsoft 365 Business Premium.
ms.openlocfilehash: af9b19dcf33f1b79d4057662cf759ace27aec38f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095262"
---
# <a name="security-defaults-and-multi-factor-authentication"></a>Sikkerhedsstandarder og multifaktorgodkendelse

Microsoft 365 Business Premium er udviklet til at beskytte virksomhedens brugerkonti med forudkonfigurerede sikkerhedsindstillinger. Disse indstillinger omfatter aktivering af multifaktorgodkendelse (MFA) for alle dine administratorer og brugerkonti. For de fleste organisationer tilbyder sikkerhedsstandarder et godt niveau af logonsikkerhed.

Du kan få flere oplysninger om sikkerhedsstandarder og de politikker, de [gennemtvinger, under Hvad er sikkerhedsstandarder?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Denne artikel indeholder oplysninger om:

- [Sikkerhedsstandarder](#security-defaults) (egnet til de fleste virksomheder)
- [Betinget adgang](#conditional-access) (til virksomheder med strengere sikkerhedskrav)

> [!NOTE]
> Hvis du har brugt politikker for betinget adgang, skal du slå dem fra, før du bruger sikkerhedsstandarder. Du kan enten bruge sikkerhedsstandarder eller politikker for betinget adgang, men du kan ikke bruge begge på samme tid.

## <a name="security-defaults"></a>Sikkerhedsstandarder

Sikkerhedsstandarder er udviklet til at hjælpe med at beskytte virksomhedens brugerkonti fra starten. Når indstillingen er slået til, indeholder sikkerhedsstandarder sikre standardindstillinger, der hjælper med at beskytte din virksomhed ved at:

- Kræver, at alle brugere og administratorer tilmelder sig MFA ved hjælp af Microsoft Authenticator-appen.
- Udfordrende brugere med MFA, primært når de vises på en ny enhed eller app, men oftere i forbindelse med kritiske roller og opgaver.
- Deaktivering af godkendelse fra ældre godkendelsesklienter, der ikke kan udføre MFA.
- Beskyttelse af administratorer ved at kræve ekstra godkendelse, hver gang de logger på.

MFA er et vigtigt første skridt til at beskytte din virksomhed, og sikkerhedsstandarder gør det nemt at implementere MFA. Hvis dit abonnement blev oprettet den 22. oktober 2019, kan sikkerhedsstandarder være blevet aktiveret automatisk for dig, og du&mdash; bør kontrollere dine indstillinger for at bekræfte det.

> [!TIP]
> Du kan få flere oplysninger om sikkerhedsstandarder og de politikker, de [gennemtvinger, under Hvad er sikkerhedsstandarder?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

### <a name="to-enable-security-defaults-or-confirm-theyre-already-enabled"></a>Sådan aktiverer du sikkerhedsstandarder (eller bekræfter, at de allerede er aktiveret)

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> med sikkerhedsadministrator, administrator af betinget adgang eller globale administratorlegitimationsoplysninger.

2. Vælg **Vis alle** i ruden til venstre, og vælg derefter **Azure Active Directory** under **Administrationscentre**.

3. Vælg **Azure Active Directory** i venstre rude i **Azure Active Directory Administration**.

4. Vælg **Egenskaber** i menuen til venstre i dashboardet i sektionen **Administrer**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Skærmbillede af Azure Active Directory Administration, der viser placeringen af menupunktet Egenskaber.":::

5. Nederst på siden **Egenskaber** skal du vælge **Administrer sikkerhedsstandarder**.

6. I ruden til højre kan du se indstillingen **Aktivér standarder for sikkerhed** . Hvis **Ja** er valgt, er sikkerhedsstandarder allerede aktiveret, og der kræves ingen yderligere handling. Hvis sikkerhedsstandarder ikke er aktiveret i øjeblikket, skal du vælge **Ja** for at aktivere dem og derefter vælge **Gem**.

## <a name="conditional-access"></a>Betinget adgang

> [!NOTE]
> Hvis du har brugt sikkerhedsstandarder, skal du slå dem fra, før du bruger Betinget adgang. Du kan enten bruge sikkerhedsstandarder eller politikker for betinget adgang, men du kan ikke bruge begge på samme tid.

Hvis din virksomhed eller virksomhed har komplekse sikkerhedskrav, eller hvis du har brug for mere detaljeret kontrol over dine sikkerhedspolitikker, bør du overveje at bruge Betinget adgang i stedet for sikkerhedsstandarder for at opnå en lignende eller højere sikkerhedsholdning.

Betinget adgang giver dig mulighed for at oprette og definere politikker, der reagerer på logonhændelser og anmode om yderligere handlinger, før en bruger får adgang til et program eller en tjeneste. Politikker for betinget adgang kan være detaljerede og specifikke, så brugerne kan være produktive, uanset hvor og hvornår de vil, men også beskytte din organisation.

Sikkerhedsstandarder er tilgængelige for alle kunder, mens Betinget adgang kræver en af følgende planer:

- Azure Active Directory Premium P1 eller P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 eller E5
- Enterprise Mobility & Security E3 eller E5

Hvis du vil bruge Betinget adgang til at konfigurere politikker, skal du se følgende trinvise vejledninger:

- [Kræv MFA for administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Kræv MFA til Azure-administration](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Kræv Azure AD MFA-registrering](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) – kræver Azure AD Identity Protection, som er en del af Azure Active Directory Premium P2

Du kan få mere at vide om Betinget adgang under [Hvad er betinget adgang?](/azure/active-directory/conditional-access/overview) Du kan få flere oplysninger om oprettelse af politikker for betinget adgang under [Opret en politik for betinget adgang](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Hvis du har en plan eller licens, der giver betinget adgang, men endnu ikke har oprettet nogen politikker for betinget adgang, er du velkommen til at bruge sikkerhedsstandarder. Du skal dog deaktivere sikkerhedsstandarder, før du kan bruge politikker for betinget adgang.

## <a name="next-objective"></a>Næste mål

Konfigurer måder at [beskytte mod malware og andre trusler](m365bp-increase-protection.md) på.

