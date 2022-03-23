---
title: Opret indikatorer
ms.reviewer: ''
description: Opret indikatorer for en filhash, IP-adresse, URL-adresser eller domæner, der definerer registrering, forebyggelse og udelukkelse af enheder.
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
ms.openlocfilehash: 00685ee4540949028b8bb438dd8a4965e2e9a5e7
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63592871"
---
# <a name="create-indicators"></a>Opret indikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Indikator for forlig (IoCs) -match er en afgørende funktion i alle løsninger til slutpunktsbeskyttelse. Denne funktion giver SecOps mulighed for at angive en liste over indikatorer til registrering og til blokering (forebyggelse og svar).

Opret indikatorer, der definerer registrering, forhindring og udelukkelse af enheder. Du kan definere den handling, der skal tages, samt varigheden for, hvornår handlingen skal anvendes, samt omfanget af den enhedsgruppe, den skal anvendes på.

Understøttede kilder er i øjeblikket det program, der bruges til registrering af skyen for Defender til Slutpunkt, det automatiske undersøgelses- og afhjælpningsprogram og det program til forebyggelse af slutpunkter (Microsoft Defender Antivirus).

## <a name="cloud-detection-engine"></a>Skyregistreringsprogram

Det skybaserede registreringsprogram for Defender til Slutpunkt scanner regelmæssigt data og forsøger at matche de indikatorer, du har angivet. Når der findes et match, sker der en handling i overensstemmelse med de indstillinger, du har angivet for IoC.

## <a name="endpoint-prevention-engine"></a>Program til forebyggelse af slutpunkter

Den samme liste over indikatorer imødekommes af den forebyggelsesagent. Betydning, hvis Microsoft Defender AV er den primære AV konfigureret, bliver de matchede indikatorer behandlet i henhold til indstillingerne. Hvis handlingen f.eks. er "Advarsel og bloker", vil Microsoft Defender AV forhindre filudførelser (blokere og afhjælpe), og en tilsvarende besked hæves. Hvis handlingen derimod er indstillet til "Tillad", vil Microsoft Defender AV ikke registrere eller blokere filen fra at blive kørt.

## <a name="automated-investigation-and-remediation-engine"></a>Automatiseret undersøgelse og afhjælpningsprogram

Den automatiske undersøgelse og afhjælpning fungerer på samme måde. Hvis en indikator er indstillet til "Tillad", ignorerer automatiseret undersøgelse og afhjælpning en "dårlig" konklusion for den. Hvis den er indstillet til "Bloker", behandler Automatiseret undersøgelse og afhjælpning den som "dårlig".

Indstillingen EnableFileHashComputation beregner filhash for cert og fil IoC under filscanninger. Det understøtter IoC-håndhævelse af hash'er og certs, som tilhører programmer, der er tillid til. Den aktiveres og deaktiveres samtidigt med indstillingen Tillad eller bloker fil. EnableFileHashComputation aktiveres manuelt via Gruppepolitik og er som standard deaktiveret.

Når du opretter en ny indikator (IoC), kan du udføre en eller flere af følgende handlinger:

- Tillad – IoC får tilladelse til at køre på dine enheder.
- Overvågning – der udløses en besked, når IoC kører.
- Advar – IoC viser en advarsel om, at brugeren kan tilsidesætte 
- Bloker eksekvering – IoC får ikke tilladelse til at køre.
- Bloker og afhjulpet – IoC får ikke tilladelse til at køre, og en afhjælpningshandling anvendes på IoC.

>[!NOTE]
> Hvis du bruger tilstanden Advar, får brugerne en advarsel, hvis de åbner en risikabel app. Prompten blokerer dem ikke fra at bruge appen, men du kan angive en brugerdefineret meddelelse og links til en virksomhedsside, der beskriver den relevante brug af appen. Brugere kan stadig springe advarslen over og fortsætte med at bruge appen, hvis de har brug for det. Få mere at vide under [Styre apps, der findes af Microsoft Defender til slutpunkt](/cloud-app-security/mde-govern).

Du kan oprette en indikator for:

- [Filer](indicator-file.md)
- [IP-adresser, URL-adresser/domæner](indicator-ip-domain.md)
- [Certifikater](indicator-certificates.md)

Tabellen nedenfor viser præcis, hvilke handlinger der er tilgængelige pr. indikatortype (IoC):

| IoC-type | Tilgængelige handlinger |
|:---|:---|
| [Filer](indicator-file.md) | Tillad <br> Overvågning <br> Bloker og afhjulpet |
| [IP-adresser](indicator-ip-domain.md) | Tillad <br> Overvågning <br> Bloker eksekvering <br> Advar |
| [URL-adresser og domæner](indicator-ip-domain.md) | Tillad <br> Overvågning <br> Bloker eksekvering<br> Advar |
| [Certifikater](indicator-certificates.md) | Tillad <br> Bloker og afhjulpet |

Funktionaliteten i eksisterende IoCs ændres ikke. Indikatorerne blev dog omdøbt til at svare til de aktuelle understøttede svarhandlinger:

- Svarhandlingen "Kun påmindelse" blev omdøbt til "overvågning", hvor indstillingen Opret besked er aktiveret.
- Svaret "påmindelse og blokering" blev omdøbt til "blokere og afhjælpe" med den valgfrie indstilling for genereringsbeskeder.

IoC API-skemaet og trussels-id'erne ved forhåndssøgning er blevet opdateret til at være i overensstemmelse med omdøbning af IoC-svarhandlingerne. Api-skemaændringerne gælder for alle IoC-typer.

> [!Note]
> Der er en grænse på 15.000 indikatorer pr. lejer. Fil- og certifikatindikatorer blokerer ikke [udeladelse, der er defineret for Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Indikatorer understøttes ikke i Microsoft Defender Antivirus, når den er i passiv tilstand.
>
> Formatet for import af nye indikatorer (IoCs) er ændret i henhold til de nye opdaterede indstillinger for handlinger og beskeder. Vi anbefaler, at du downloader det nye CSV-format, der kan findes nederst i importpanelet.

## <a name="related-topics"></a>Relaterede emner

- [Opret kontekstafhængig IoC](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Brug API'en Microsoft Defender til slutpunktsindikatorer](ti-indicator.md)
- [Brug partnerintegrerede løsninger](partner-applications.md)
