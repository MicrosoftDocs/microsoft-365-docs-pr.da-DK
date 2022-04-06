---
title: Fejlfinding af onboardingproblemer og fejlmeddelelser
description: Fejlfinding af onboardingproblemer og fejlmeddelelser, mens du fuldfører konfigurationen Microsoft Defender for Endpoint.
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
ms.openlocfilehash: cfbd91743ed2e61809d9e2b6f0243b5c327bdae4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467549"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Fejlfinding af problemer med abonnements- og portaladgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Denne side indeholder detaljerede trin til fejlfinding af problemer, der kan opstå, når du konfigurerer Microsoft Defender for Endpoint tjeneste.

Hvis du modtager en fejlmeddelelse, giver Microsoft 365 Defender en detaljeret forklaring på, hvad problemet er, og relevante links vil blive leveret.

## <a name="no-subscriptions-found"></a>Der blev ikke fundet nogen abonnementer

Hvis der vises en meddelelse om, at der  ikke blev fundet nogen abonnementer, Microsoft 365 Defender meddelelsen "Ingen abonnementer fundet", betyder det, at den Azure Active Directory (Azure AD), der bruges til at logge brugeren på portalen, ikke har en Microsoft Defender for Endpoint-licens.

Mulige årsager:

- Windows E5- og Office E5-licenserne er separate licenser.
- Licensen blev købt, men ikke klargjort til denne Azure AD-forekomst.
  - Det kan være et problem med klargøring af licenser.
  - Det kan være, at du utilsigtet har klargjort licensen til en anden Microsoft Azure AD end den, der bruges til godkendelse i tjenesten.

I begge tilfælde skal du kontakte Microsoft Support hos [Generelt Microsoft Defender for Endpoint Support eller](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) [Support med volumenlicens](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="Siden Ingen abonnementer fundet" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>Dit abonnement er udløbet

Hvis du får vist Microsoft 365 Defender, når du **får meddelelsen Dit abonnement er udløbet**, er dit onlinetjenesteabonnement udløbet. Microsoft Defender for Endpoint-abonnement har, ligesom alle andre onlinetjenesteabonnementer, en udløbsdato.

Du kan til enhver tid vælge at forny eller udvide licensen. Når du åbner portalen efter udløbsdatoen, vises  meddelelsen Dit abonnement er udløbet med muligheden for at downloade pakken med enhedens offboarding, hvis du vælger ikke at forny licensen.

> [!NOTE]
> Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="Abonnementet udløb meddelelse" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>Du er ikke autoriseret til at få adgang til portalen

Hvis du modtager en Du er ikke autoriseret til at få adgang til **portalen, skal** du være opmærksom på, at Microsoft Defender for Endpoint er en sikkerhedsovervågning, undersøgelse af hændelser og svarprodukt, og adgang til det begrænses og kontrolleres som sådan af brugeren.
Du kan finde flere oplysninger [**under Tildel brugeradgang til portalen**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="Adgang er ikke tilladt meddelelse" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Data er i øjeblikket ikke tilgængelige i visse afsnit af portalen

Hvis portaldashboardet og andre afsnit viser en fejlmeddelelse som f.eks. "Data er ikke tilgængelige i øjeblikket":

:::image type="content" source="images/atp-data-not-available.png" alt-text="Dataene meddelelse" lightbox="images/atp-data-not-available.png":::

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
