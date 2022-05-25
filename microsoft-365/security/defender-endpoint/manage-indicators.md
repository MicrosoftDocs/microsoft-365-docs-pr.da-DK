---
title: Opret indikatorer
ms.reviewer: ''
description: Opret indikatorer for en filhash, IP-adresse, URL-adresser eller domæner, der definerer registrering, forebyggelse og udeladelse af enheder.
keywords: administrer, tilladt, blokeret, bloker, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1e68e1e49dd855356840eb732c6050178ae1c147
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669710"
---
# <a name="create-indicators"></a>Opret indikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Indikator for kompromismatchning (IoCs) er en vigtig funktion i alle løsning til beskyttelse af slutpunkter. Denne funktion giver SecOps mulighed for at angive en liste over indikatorer for registrering og blokering (forebyggelse og svar).

Opret indikatorer, der definerer registrering, forebyggelse og udeladelse af enheder. Du kan definere den handling, der skal udføres, samt varigheden af, hvornår handlingen skal anvendes, samt omfanget af den enhedsgruppe, den skal anvendes på.

Kilder, der understøttes i øjeblikket, er cloudregistreringsprogrammet for Defender for Endpoint, det automatiserede undersøgelses- og afhjælpningsprogram og programmet til forebyggelse af slutpunkter (Microsoft Defender Antivirus).

## <a name="cloud-detection-engine"></a>Cloudregistreringsprogram

Programmet til skyregistrering i Defender for Endpoint scanner jævnligt indsamlede data og forsøger at matche de indikatorer, du angiver. Når der er et match, udføres der en handling i henhold til de indstillinger, du har angivet for IoC.

## <a name="endpoint-prevention-engine"></a>Slutpunktsforebyggelsesprogram

Den samme liste over indikatorer æres af forebyggelsesagenten. Det betyder, at hvis Microsoft Defender AV er den primære AV-konfigureret, behandles de tilsvarende indikatorer i henhold til indstillingerne. Hvis handlingen f.eks. er "Besked og Bloker", forhindrer Microsoft Defender AV filudførelser (bloker og afhjælpning), og der udløses en tilsvarende besked. På den anden side, hvis handlingen er angivet til "Tillad", registrerer eller blokerer Microsoft Defender AV ikke filen fra at blive kørt.

## <a name="automated-investigation-and-remediation-engine"></a>Automatiseret undersøgelses- og afhjælpningsprogram

Den automatiserede undersøgelse og afhjælpning fungerer på samme måde. Hvis en indikator er angivet til "Tillad", ignorerer automatiseret undersøgelse og afhjælpning en "dårlig" dom for den. Hvis den er angivet til "Block", vil automatiseret undersøgelse og afhjælpning behandle den som "dårlig".

Indstillingen EnableFileHashComputation beregner filhash for certifikat- og fil-IoC under filscanninger. Det understøtter IoC-håndhævelse af hash, og certifikater tilhører programmer, der er tillid til. Den aktiveres og deaktiveres samtidig med indstillingen tillad eller bloker fil. EnableFileHashComputation aktiveres manuelt via Gruppepolitik og er deaktiveret som standard.

Når du opretter en ny indikator (IoC), er en eller flere af følgende handlinger tilgængelige:

- Allow – IoC kan køre på dine enheder.
- Overvågning – en besked udløses, når IoC kører.
- Advar – IoC beder om en advarsel om, at brugeren kan omgå 
- Bloker udførelse – IoC må ikke køre.
- Bloker og afhjælp – IoC må ikke køre, og der vil blive anvendt en afhjælpningshandling på IoC.

>[!NOTE]
> Hvis du bruger Advar-tilstand, bliver brugerne bedt om at angive en advarsel, hvis de åbner en risikable app. Prompten blokerer dem ikke fra at bruge appen, men du kan angive en brugerdefineret meddelelse og links til en virksomhedsside, der beskriver den relevante brug af appen. Brugerne kan stadig tilsidesætte advarslen og fortsætte med at bruge appen, hvis de har brug for det. Du kan finde flere oplysninger under [Styr de apps, der registreres af Microsoft Defender for Endpoint](/cloud-app-security/mde-govern).

Du kan oprette en indikator for:

- [Filer](indicator-file.md)
- [IP-adresser, URL-adresser/domæner](indicator-ip-domain.md)
- [Certifikater](indicator-certificates.md)

I nedenstående tabel kan du se præcis, hvilke handlinger der er tilgængelige pr. indikatortype (IoC):

| IoC-type | Tilgængelige handlinger |
|:---|:---|
| [Filer](indicator-file.md) | Tillad <br> Revision <br> Bloker og afhjælp |
| [IP-adresser](indicator-ip-domain.md) | Tillad <br> Revision <br> Bloker udførelse <br> Advare |
| [URL-adresser og domæner](indicator-ip-domain.md) | Tillad <br> Revision <br> Bloker udførelse<br> Advare |
| [Certifikater](indicator-certificates.md) | Tillad <br> Bloker og afhjælp |

Funktionaliteten af allerede eksisterende IoCs ændres ikke. Indikatorerne blev dog omdøbt, så de stemmer overens med de aktuelle understøttede svarhandlinger:

- Svarhandlingen "kun besked" blev omdøbt til "overvågning" med indstillingen Generér besked aktiveret.
- Svaret "besked og blok" blev omdøbt til "bloker og afhjælp" med den valgfri indstilling for generér besked.

IoC API-skemaet og trussels-id'erne på forhånd på jagt er blevet opdateret for at tilpasse sig omdøbningen af IoC-svarhandlinger. Ændringerne i API-skemaet gælder for alle IoC-typer.

> [!Note]
> Der er en grænse på 15.000 indikatorer pr. lejer. Fil- og certifikatindikatorer blokerer ikke [de udeladelser, der er defineret for Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Indikatorer understøttes ikke i Microsoft Defender Antivirus, når de er i passiv tilstand.
>
> Formatet for import af nye indikatorer (IoCs) er ændret i henhold til de nye opdaterede indstillinger for handlinger og beskeder. Vi anbefaler, at du downloader det nye CSV-format, der findes nederst i importpanelet.

## <a name="related-topics"></a>Relaterede emner

- [Opret kontekstafhængig IoC](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Brug API'en til Microsoft Defender for Endpoint indikatorer](ti-indicator.md)
- [Brug partnerintegrerede løsninger](partner-applications.md)
