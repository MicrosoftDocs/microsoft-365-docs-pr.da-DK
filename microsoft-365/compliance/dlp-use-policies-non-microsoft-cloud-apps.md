---
title: Brug DLP-politikker til cloudapps, der ikke er fra Microsoft
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
description: Få mere at vide om, hvordan du bruger dlp-politikker til cloudapps, der ikke er fra Microsoft.
ms.openlocfilehash: a50849b53819a7c5872c3ec8cb279ffa8d14e27f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634397"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Brug politikker til forebyggelse af datatab til cloudapps, der ikke er fra Microsoft

Du kan bruge DLP-politikker til at Microsoft Defender for Cloud Apps til at overvåge, registrere og udføre handlinger, når følsomme elementer bruges og deles via cloudapps, der ikke er fra Microsoft.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Før du begynder at bruge DLP-politikker, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelsesprogrammer. Hvis du vil have adgang til og bruge denne funktionalitet, skal du have et af disse abonnementer eller tilføjelsesprogrammer:

- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft 365 E5 Sikkerhed

### <a name="permissions"></a>Tilladelser
Den bruger, der opretter DLP-politikken, skal være:

- Global administrator
- Overholdelsesadministrator: Tildel i Azure AD
- Administrator af overholdelsesdata: Tildel i Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Forbered dit Defender for Cloud Apps-miljø

Før du konfigurerer DLP-politikker, der er beregnet til at Microsoft Defender for Cloud Apps, skal du forberede dit Defender for Cloud Apps-miljø. Du kan finde instruktioner under [Hurtig start: Kom i gang med Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started).

### <a name="connect-a-non-microsoft-cloud-app"></a>Opret forbindelse til en cloudapp, der ikke er fra Microsoft

Hvis du vil bruge en DLP-politik, der er begrænset til en bestemt cloudapp, der ikke er Microsoft, skal appen være forbundet til Defender for Cloud Apps. Du kan få flere oplysninger under:

- [Tilslutningsboks](/defender-cloud-apps/connect-box)
- [Opret forbindelse til Dropbox](/defender-cloud-apps/connect-dropbox)
- [Opret forbindelse til Google Workspace](/defender-cloud-apps/connect-google-workspace)
- [Opret forbindelse til Salesforce](/defender-cloud-apps/connect-salesforce)
- [Opret forbindelse til Cisco Webex](/defender-cloud-apps/connect-webex)

Når du har oprettet forbindelse mellem dine cloudapps og Defender for Cloud Apps, kan du oprette DLP-politikker for dem.

## <a name="create-a-dlp-policy-scoped-to-a-non-microsoft-cloud-app"></a>Opret en DLP-politik, der er begrænset til en cloudapp, der ikke er fra Microsoft

Se [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md) for de procedurer, der skal bruges til at oprette en DLP-politik. Vær opmærksom på disse punkter, når du konfigurerer din politik.

- Vælg slå **Microsoft Defender for Cloud Apps** placering til.
- Hvis du vil vælge en bestemt app eller forekomst, skal du vælge **Vælg forekomst**. Hvis du ikke vælger en forekomst, vil politikken være begrænset til alle forbundne apps i din Microsoft Defender for Cloud Apps lejer.
- Du kan vælge mellem en række **handlinger,** der skal gennemtvinges på tredjepartsapps. Hvis du vil begrænse tredjepartsapps, skal du vælge **Begræns tredjepartsapps** og derefter vælge de specifikke handlinger.

![liste over handlinger, der skal gennemtvinges på forbundne cloudapps](../media/dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Når du opretter en DLP-politik, der er begrænset til Microsoft Defender for Cloud Apps, oprettes den samme politik automatisk i Microsoft Defender for Cloud Apps.

## <a name="see-also"></a>Se også

- [Opret test, og juster en DLP-politik](./create-test-tune-dlp-policy.md)
- [Kom i gang med DLP-standardpolitikken](./get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](./create-a-dlp-policy-from-a-template.md)
