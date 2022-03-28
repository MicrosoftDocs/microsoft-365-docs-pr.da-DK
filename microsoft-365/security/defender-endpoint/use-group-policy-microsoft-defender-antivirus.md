---
title: Konfigurere Microsoft Defender Antivirus med Gruppepolitik
description: Lær at bruge en Gruppepolitik til at konfigurere og Microsoft Defender Antivirus på dine slutpunkter i Microsoft Defender til slutpunkt.
keywords: gruppepolitik, gruppepolitikobjekt, konfiguration, indstillinger
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/04/2022
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 3659f0f532b14babd256f3310c4e7da8dde67e3c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63597889"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan bruge [Gruppepolitik](/windows/win32/srvnodes/group-policy) til at konfigurere og Microsoft Defender Antivirus på dine slutpunkter.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Konfigurere Microsoft Defender Antivirus ved hjælp af Gruppepolitik

Generelt kan du bruge følgende fremgangsmåde til at konfigurere eller ændre Microsoft Defender Antivirus gruppepolitikindstillinger:

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Management Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik-objekt (GPO), du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows flere** \> **Microsoft Defender Antivirus**.

5. Udvid den sektion (kaldet Placering  i tabellen i dette emne), der indeholder den indstilling, du vil konfigurere, dobbeltklikke på indstillingen for at åbne den og foretage konfigurationsændringer.

6. [Installér det opdaterede gruppepolitikobjekt, som du normalt gør](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>Gruppepolitik indstillinger og ressourcer

I følgende tabel vises ofte anvendte Gruppepolitik, der er tilgængelige i Windows 10.

> [!TIP]
> Download oversigtsarket Gruppepolitik, som viser politikindstillingerne for computer- og brugerkonfigurationer, der er inkluderet i de administrative skabelonfiler, der leveres sammen med til Windows. Du kan konfigurere henvis til regnearket, når du redigerer Gruppepolitik objekter. <br/><br/> Her er de seneste versioner:
> - [Gruppepolitik Indstillinger til regneark til Windows 10 maj 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Gruppepolitik Indstillinger oversigtsark til Windows 11. oktober 2021 Opdatering (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Placering|Indstilling|Artikel|
|---|---|---|
|Klientgrænseflade|Aktivér brugergrænsefladen uden hoved|[Forhindre brugere i at se eller arbejde med Microsoft Defender Antivirus brugergrænsefladen](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Vis yderligere tekst til klienter, når de skal udføre en handling|[Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Skjule alle meddelelser|[Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Undertrykker genstartsmeddelelser|[Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)|
|Udeladelser|Udeladelse af udvidelse|[Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Sti-udeladelse|[Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Procesudetagelser|[Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Slå automatisk udeladelse fra|[Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|KORT|Konfigurere funktionen "Blok ved første syn"|[Aktivér blok ved første synsviden](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|KORT|Deltag i Microsoft MAPS|[Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)|
|KORT|Send fileksempler, når yderligere analyse er påkrævet|[Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)|
|KORT|Konfigurere tilsidesættelse af lokale indstillinger for rapportering til Microsoft MAPS|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Konfigurere udvidet skykontrol|[Konfigurere tidsperioden for skyblokering](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Vælg skybeskyttelsesniveau|[Angiv beskyttelsesniveauet, der leveres i skyen](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|Netværksinspektionssystem|Angive yderligere definitionssæt til inspektion af netværkstrafik| Ikke brugt (frarådet) |
|Netværksinspektionssystem|Slå tilbagetrækning af definition til| Ikke brugt (frarådet)|
|Netværksinspektionssystem|Slå protokolgenkendelse til| Ikke brugt (frarådet)|
|Karantæne|Konfigurere tilsidesættelse af lokale indstillinger for fjernelse af elementer fra mappen Karantæne|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Karantæne|Konfigurere fjernelse af elementer fra karantænemappen|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af fil- og programaktivitet på computeren|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af indgående og udgående filaktivitet|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for at aktivere overvågning af funktionsmåder|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokale indstillinger for at aktivere beskyttelse i realtid|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Definer den maksimale størrelse på downloadede filer og vedhæftede filer, der skal scannes|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Overvåg fil- og programaktivitet på din computer|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Scan alle downloadede filer og vedhæftede filer|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå beskyttelse i realtid fra|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Aktiver overvågning af funktionsmåder|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå processcanning til, når beskyttelse i realtid er aktiveret|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå rå meddelelser om lydstyrke til|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurere overvågning af indgående og udgående fil- og programaktivitet|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Afhjælpning|Konfigurere tilsidesættelse af lokale indstillinger for tidspunktet på dagen til at køre en planlagt fuld scanning for at fuldføre afhjælpningen|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Afhjælpning|Angiv ugedagen for at køre en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurere planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Afhjælpning|Angiv tidspunktet på dagen, der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurere planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Rapportering|Slå udvidede meddelelser fra|[Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)
|Rod|Slå Microsoft Defender Antivirus|Bruges ikke. Hvis du bruger eller planlægger at bruge et antivirusprodukt, der ikke er fra Microsoft, [skal du Microsoft Defender Antivirus med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md).|
|Rod|Definer adresser, der skal tilsidesættes af proxyserveren|[Konfigurere indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Definer proxy autoconfig (.pac) for at oprette forbindelse til netværket|[Konfigurere indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Definer proxyserver til at oprette forbindelse til netværket|[Konfigurere indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Konfigurere den lokale administratorfletningsfunktionsmåde for lister|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Rod|Tillad, at antimalwaretjenesten starter med normal prioritet|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Tillad, at antimalwaretjenesten altid kører|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Slå rutinemæssig afhjælpning fra|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Randomisere planlagte opgavetider|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Tillad brugere at afbryde scanningen midlertidigt|[Forhindre brugere i at se eller arbejde med Microsoft Defender Antivirus (](prevent-end-user-interaction-microsoft-defender-antivirus.md)understøttes ikke på Windows 10)|
|Scan|Se efter de nyeste definitioner af virus og spyware, før du kører en planlagt scanning|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Scan|Definer det antal dage, hvorefter en indbrudsscanning er gennemtvunget|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Scan|Slå fuld scanning til|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Scan|Slå Hurtig scanning til|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Scan|Konfigurere tilsidesættelse af lokale indstillinger for den maksimale procentdel af CPU-anvendelsen|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlægning af scanningdag|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlagt hurtig scanning|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlagt scanningstid|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Scan|Konfigurere tilsidesættelse af lokale indstillinger for den scanningstype, der skal bruges til en planlagt scanning|[Forebyd eller tillad brugere at redigere politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Scan|Opret et systemgendannelsespunkt|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Scan|Slå fjernelse af elementer fra mappen med scanningsoversigten til|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Scan|Slå heuristics til|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Scan|Aktivere scanning af e-mails|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Slå scanning af genparse point til|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Kør fuld scanning på tilknyttede netværksdrev|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Scan arkivfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Scan netværksfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Scanne eksekverbare eksekverbare værdier|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Scan | Scan scripts | [Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Se også [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Scan|Scan flytbare drev|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Angiv den maksimale dybde for scanningsarkivfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Angiv den maksimale procentdel af CPU-udnyttelse under en scanning|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Angiv den maksimale størrelse på arkivfiler, der skal scannes|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Scan|Angiv ugedagen for at køre en planlagt scanning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Angiv det interval, der skal køre hurtige scanninger pr. dag|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Angiv den scanningstype, der skal bruges til en planlagt scanning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Angiv tidspunktet for en daglig hurtig scanning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Angiv det klokkeslæt på dagen, der skal køres en planlagt scanning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Scan|Starte den planlagte scanning, når computeren er tændt, men ikke i brug|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Tillad sikkerhedsintelligensopdateringer fra Microsoft Update|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Tillad sikkerhedsintelligensopdateringer, når der køres på batteristrøm|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Tillad meddelelser om at deaktivere definitionsbaserede rapporter i Microsoft MAPS|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Tillad sikkerhedsintelligensopdateringer i realtid, der er baseret på rapporter til Microsoft MAPS|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Se efter de nyeste definitioner af virus og spyware ved opstart|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Definer filshares til hentning af sikkerhedsintelligensopdateringer|[Administrere Microsoft Defender Antivirus sikkerheds- og sikkerhedsintelligensopdateringer](manage-protection-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Definer det antal dage, hvorefter der kræves en opdatering med en sikkerhedsintelligens|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Definere antallet af dage, før spywaredefinitioner betragtes som forældede|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Definer, hvor mange dage før virusdefinitioner betragtes som forældede|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Definere rækkefølgen af kilder til hentning af sikkerhedsintelligensopdateringer|[Administrere Microsoft Defender Antivirus sikkerheds- og sikkerhedsintelligensopdateringer](manage-protection-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Start sikkerhedsintelligensopdatering ved start|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Angiv ugedagen for at søge efter sikkerhedsintelligensopdateringer|[Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Angiv intervallet, der skal kontrolleres for sikkerhedsintelligensopdateringer|[Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Angive tiden, der skal søges efter sikkerhedsintelligensopdateringer|[Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Sikkerhedsintelligensopdateringer|Aktiver scanning efter Sikkerhedsintelligens-opdatering|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Trusler|Angive niveauer for besked om trusler, hvor standardhandlingen ikke skal tages, når den registreres|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Trusler|Angive trusler, som standardhandlingen ikke skal anvendes på, når den registreres|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|


## <a name="see-also"></a>Se også

- [Referenceemner til administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
