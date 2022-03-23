---
title: Brug politikker til forebyggelse af datatab til ikke-Microsoft-skyapps
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du bruger dlp-politikker til ikke-Microsoft-skyapps.
ms.openlocfilehash: b374f9b85d41b6dd6a5281e17347dffd414361da
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63591482"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Brug politikker til forebyggelse af datatab til ikke-Microsoft-skyapps

Politikker til forebyggelse af datatab (DLP) til ikke-Microsoft-skyapps er en del af Microsoft 365 DLP-pakken af funktioner. Ved hjælp af disse funktioner kan du opdage og beskytte følsomme elementer på tværs af Microsoft 365-tjenester. Du kan finde flere oplysninger om alle Microsoft DLP-tilbud i [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

Du kan bruge DLP-politikker til ikke-Microsoft-skyapps til at overvåge og registrere, når følsomme elementer bruges og deles via ikke-Microsoft-skyapps. Hvis du bruger disse politikker, får du den synlighed og kontrol, du skal bruge for at sikre, at de bruges og beskyttes korrekt, og det er med til at forhindre risikabelt adfærd, der kan kompromittere dem.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Før du begynder at bruge DLP-politikker til ikke-Microsoft-skyapps, skal du bekræfte [dit Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelsesprogrammer. For at få adgang til og bruge denne funktionalitet skal du have et af disse abonnementer eller tilføjelser:

- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft 365 E5 Sikkerhed

### <a name="permissions"></a>Tilladelser
Den bruger, der opretter DLP-politikken, skal være:

- Global administrator
- Overholdelsesadministrator: tildel i Azure AD
- Dataadministrator for overholdelse af regler og standarder: tildel i Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Klargør dit Defender til cloudapps-miljø

DLP-politikker til ikke-Microsoft-skyapps bruger Defender til cloudapps DLP-funktioner. Hvis du vil bruge det, skal du forberede dit Defender for Cloud Apps-miljø. Du kan finde instruktioner [i Angiv øjeblikkelig synlighed, beskyttelse og styringshandlinger for dine apps](/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps).

### <a name="connect-a-non-microsoft-cloud-app"></a>Forbind en skyapp, der ikke er Microsoft

Hvis du vil bruge DLP-politikken til en bestemt ikke-Microsoft-skyapp, skal appen have forbindelse til Defender til skyapps. Du kan finde flere oplysninger i:

- [Forbind Box](/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [Forbind Dropbox](/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [Forbind G-Arbejdsområde](/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [Forbind Salesforce](/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [Forbind Cisco Webex](/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

Når du forbinder dine skyapps til Defender for Cloud Apps, kan du oprette Microsoft 365 DLP-politikker for dem.

> [!NOTE]
> Det er også muligt at bruge Microsoft Defender til skyapps til at oprette DLP-politikker til Microsoft-skyapps. Det anbefales dog at bruge Microsofts Microsoft 365 til at oprette og administrere DLP-politikker til Microsoft-skyapps.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>Opret en DLP-politik til en ikke-Microsoft-skyapp

Når du vælger en placering til DLP-politikken, skal du aktivere placeringen **af Microsoft Defender for Cloud Apps** .

- Vælg Vælg forekomst for at vælge en bestemt app **eller forekomst**.
- Hvis du ikke vælger en forekomst, bruger politikken alle forbundne apps i lejeren Microsoft Defender til skyapps.

   ![Placeringer, hvor politikken skal anvendes.](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Box-US og Box-General.](../media/2-dlp-non-microsoft-cloud-app-box.png)

Du kan vælge forskellige handlinger for hver understøttet ikke-Microsoft-skyapp. For hver app er der forskellige mulige handlinger (afhænger af den skybaserede app-API).

![Opret regel.](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

Når du opretter en regel i DLP-politikken, kan du vælge en handling for ikke-Microsoft-skyapps. Hvis du vil begrænse tredjepartsapps, skal du **vælge Begræns tredjepartsapps**.

![Begræns tredjepartsapps.](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> DLP-politikker, der anvendes på ikke-Microsoft-apps, bruger Microsoft Defender til skyapps. Når DLP-politikken for en ikke-Microsoft-app oprettes, oprettes den samme politik automatisk i Microsoft Defender til skyapps.

Du kan finde oplysninger om oprettelse og konfiguration af DLP-politikker i [Opret test og finjuster en DLP-politik](./create-test-tune-dlp-policy.md).

## <a name="see-also"></a>Se også

- [Opret test og finjuster en DLP-politik](./create-test-tune-dlp-policy.md)
- [Introduktion til DLP-standardpolitikken](./get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](./create-a-dlp-policy-from-a-template.md)
