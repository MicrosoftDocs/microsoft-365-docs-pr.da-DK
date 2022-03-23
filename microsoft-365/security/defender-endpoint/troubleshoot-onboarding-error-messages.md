---
title: Fejlfinding af onboardingproblemer og fejlmeddelelser
description: Fejlfinding af onboardingproblemer og fejlmeddelelse under konfiguration af Microsoft Defender til slutpunkt.
keywords: fejlfinding, fejlfinding, Azure Active Directory, onboarding, fejlmeddelelse, fejlmeddelelser, Microsoft Defender til slutpunkt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: cbf2049841f2987eb71e9c716de133872c1e6a81
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2022
ms.locfileid: "63592896"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Fejlfinding af problemer med abonnements- og portaladgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Denne side indeholder detaljerede trin til fejlfinding af problemer, der kan opstå, når du konfigurerer din Microsoft Defender til slutpunktstjeneste.

Hvis du modtager en fejlmeddelelse, giver Microsoft 365 Defender en detaljeret forklaring på, hvad problemet er, og relevante links vil blive leveret.

## <a name="no-subscriptions-found"></a>Der blev ikke fundet nogen abonnementer

Hvis du får vist meddelelsen Ingen abonnementer Microsoft 365 Defender mens du  åbner Azure Active Directory, betyder det, at den Azure Active Directory (Azure AD), der bruges til at logge brugeren på portalen, ikke har en Microsoft Defender for Endpoint-licens.

Mulige årsager:

- Windows E5- og Office E5-licenserne er separate licenser.
- Licensen blev købt, men ikke klargjort til denne Azure AD-forekomst.
  - Det kan være et problem med klargøring af licenser.
  - Det kan være, at du utilsigtet har klargjort licensen til en anden Microsoft Azure AD end den, der bruges til godkendelse i tjenesten.

I begge tilfælde skal du kontakte Microsoft Support hos [General Microsoft Defender for Endpoint Support](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) eller [Understøttelse af volumenlicens](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

![Billede af ingen abonnementer fundet.](images/atp-no-subscriptions-found.png)

## <a name="your-subscription-has-expired"></a>Dit abonnement er udløbet

Hvis du får vist Microsoft 365 Defender, når du **får meddelelsen Dit abonnement er udløbet**, er dit onlinetjenesteabonnement udløbet. Som alle andre onlinetjenesteabonnementer har Microsoft Defender for Endpoint en udløbsdato.

Du kan til enhver tid vælge at forny eller udvide licensen. Når du åbner portalen efter udløbsdatoen, vises  meddelelsen Dit abonnement er udløbet med muligheden for at downloade pakken med enhedens offboarding, hvis du vælger ikke at forny licensen.

> [!NOTE]
> Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

![Billede af abonnementet er udløbet.](images/atp-subscription-expired.png)

## <a name="you-are-not-authorized-to-access-the-portal"></a>Du er ikke autoriseret til at få adgang til portalen

Hvis du modtager en Du er ikke autoriseret til at få adgang til **portalen, skal** du være opmærksom på, at Microsoft Defender til slutpunkt er en sikkerhedsovervågning, undersøgelse af hændelser og svarprodukt, og at adgang til det som sådan begrænses og kontrolleres af brugeren.
Du kan finde flere oplysninger [**under Tildel brugeradgang til portalen**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

![Billede af en portal, der ikke er autoriseret til at få adgang til.](images/atp-not-authorized-to-access-portal.png)

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Data er i øjeblikket ikke tilgængelige i visse afsnit af portalen

Hvis portaldashboardet og andre afsnit viser en fejlmeddelelse som f.eks. "Data er ikke tilgængelige i øjeblikket":

![Billede af data er i øjeblikket ikke tilgængeligt.](images/atp-data-not-available.png)

Du skal tillade og alle `security.windows.com` underdomæner under det i din webbrowser. F.eks. `*.security.windows.com`.

## <a name="portal-communication-issues"></a>Kommunikationsproblemer i portalen

Hvis du støder på problemer med at få adgang til portalen, manglende data eller begrænset adgang til dele af portalen, skal du kontrollere, at følgende URL-adresser er tilladte og åbne for kommunikation.

- `*.blob.core.windows.net`
- `crl.microsoft.com`
- `https://*.microsoftonline-p.com`
- `https://*.security.microsoft.com`
- `https://automatediracs-eus-prd.security.microsoft.com`
- `https://login.microsoftonline.com`
- `https://login.windows.net`
- `https://onboardingpackagescusprd.blob.core.windows.net`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://security.microsoft.com`
- `https://static2.sharepointonline.com`
