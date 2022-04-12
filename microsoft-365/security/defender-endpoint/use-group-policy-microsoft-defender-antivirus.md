---
title: Konfigurer Microsoft Defender Antivirus med Gruppepolitik
description: Få mere at vide om, hvordan du bruger en Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus på dine slutpunkter i Microsoft Defender for Endpoint.
keywords: gruppepolitik, gruppepolitik, gruppepolitik, konfiguration, indstillinger
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
ms.openlocfilehash: e8cda6f387814ed6ec613db8cb53ff030243a92b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789406"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan bruge [Gruppepolitik](/windows/win32/srvnodes/group-policy) til at konfigurere og administrere Microsoft Defender Antivirus på dine slutpunkter.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Konfigurer Microsoft Defender Antivirus ved hjælp af Gruppepolitik

Generelt kan du bruge følgende fremgangsmåde til at konfigurere eller ændre Microsoft Defender Antivirus gruppepolitikindstillinger:

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus**.

5. Udvid det afsnit (kaldet **Placering** i tabellen i dette emne), der indeholder den indstilling, du vil konfigurere, dobbeltklik på indstillingen for at åbne den, og foretag konfigurationsændringer.

6. [Udrul det opdaterede gruppepolitikobjekt, som du normalt gør](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>Gruppepolitik indstillinger og ressourcer

I følgende tabel vises de almindeligt anvendte Gruppepolitik indstillinger, der er tilgængelige i Windows 10.

> [!TIP]
> Download Gruppepolitik Reference-regneark, som viser politikindstillingerne for computer- og brugerkonfigurationer, der er inkluderet i de administrative skabelonfiler, der leveres med til Windows. Du kan konfigurere referer til regnearket, når du redigerer Gruppepolitik Objekter. <br/><br/> Her er de nyeste versioner:
> - [Gruppepolitik Indstillinger referenceregneark til Windows 10 maj 2020-opdatering (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Gruppepolitik Indstillinger referenceregneark til Windows 11 oktober 2021-opdatering (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Placering|Indstilling|Artikel|
|---|---|---|
|Klientgrænseflade|Aktivér hovedløs brugergrænsefladetilstand|[Undgå, at brugerne får vist eller interagerer med den Microsoft Defender Antivirus brugergrænseflade](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Vis yderligere tekst til klienter, når de har brug for at udføre en handling|[Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Skjul alle meddelelser|[Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)|
|Klientgrænseflade|Undertrykker meddelelser om genstart|[Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)|
|Udeladelser|Udeladelser for filtypenavne|[Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Stiudeladelser|[Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Behandl udeladelser|[Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|Udeladelser|Deaktiver automatisk udeladelse|[Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)|
|KORT|Konfigurer funktionen 'Blok ved første øjekast'|[Aktivér blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|KORT|Deltag i Microsoft MAPS|[Aktivér skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)|
|KORT|Send fileksempler, når der kræves yderligere analyse|[Aktivér skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)|
|KORT|Konfigurer tilsidesættelse af lokale indstillinger for rapportering til Microsoft MAPS|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Konfigurer udvidet cloudkontrol|[Konfigurer timeoutperioden for skyblokering](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Vælg skybeskyttelsesniveau|[Angiv det skybaserede beskyttelsesniveau](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|Netværksinspektionssystem|Angiv yderligere definitionssæt til inspektion af netværkstrafik| Bruges ikke (frarådes) |
|Netværksinspektionssystem|Slå definition af pensionering til| Bruges ikke (frarådes)|
|Netværksinspektionssystem|Slå protokolgenkendelse til| Bruges ikke (frarådes)|
|Karantæne|Konfigurer tilsidesættelse af lokale indstillinger for fjernelse af elementer fra karantænemappen|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Karantæne|Konfigurer fjernelse af elementer fra karantænemappen|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for overvågning af fil- og programaktivitet på computeren|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for overvågning for indgående og udgående filaktivitet|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for aktivering af overvågning af funktionsmåde|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for at aktivere beskyttelse i realtid|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Definer den maksimale størrelse af downloadede filer og vedhæftede filer, der skal scannes|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Overvåg fil- og programaktivitet på computeren|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Scan alle downloadede filer og vedhæftede filer|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå beskyttelse i realtid fra|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå overvågning af funktionsmåde til|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå processcanning til, når beskyttelse i realtid er aktiveret|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Slå rå meddelelser om skrivning af diskenhed til|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Beskyttelse i realtid|Konfigurer overvågning for indgående og udgående fil- og programaktivitet|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Oprydning|Konfigurer tilsidesættelse af lokal indstilling for tidspunktet på dagen for at køre en planlagt fuld scanning for at fuldføre afhjælpningen|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Oprydning|Angiv den ugedag, hvor der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurer planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Oprydning|Angiv det tidspunkt på dagen, hvor der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurer planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Rapportering|Deaktiver forbedrede meddelelser|[Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)
|Rod|Deaktiver Microsoft Defender Antivirus|Bruges ikke. Hvis du bruger eller planlægger at bruge et antivirusprogram, der ikke er fra Microsoft, skal du se [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md).|
|Rod|Definer adresser, der skal tilsidesætte proxyserveren|[Konfigurer indstillingerne for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Definer automatisk konfiguration af proxy (.pac) til oprettelse af forbindelse til netværket|[Konfigurer indstillingerne for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Definer proxyserver til oprettelse af forbindelse til netværket|[Konfigurer indstillingerne for enhedsproxy og internetforbindelse](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Rod|Konfigurer funktionsmåden for fletning af lokale administratorer for lister|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Rod|Tillad, at antimalwaretjenesten starter med normal prioritet|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Tillad, at antimalwaretjenesten fortsat kører altid|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Deaktiver rutinemæssig afhjælpning|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Rod|Randomiser planlagte opgavetider|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Tillad, at brugere standser scanning midlertidigt|[Undgå, at brugerne får vist eller interagerer med Microsoft Defender Antivirus brugergrænseflade](prevent-end-user-interaction-microsoft-defender-antivirus.md) (understøttes ikke på Windows 10)|
|Skan|Søg efter de nyeste virus- og spywaredefinitioner, før du kører en planlagt scanning|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Skan|Definer det antal dage, hvorefter en opsummeringsscanning gennemtvinges|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skan|Slå fuld scanning til|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skan|Slå hurtig scanning til|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skan|Konfigurer tilsidesættelse af lokal indstilling for maksimal procentdel af CPU-udnyttelse|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skan|Konfigurer tilsidesættelse af lokal indstilling for planlægning af scanningsdag|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skan|Konfigurer tilsidesættelse af lokal indstilling for planlagt hurtigsøgningstid|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skan|Konfigurer tilsidesættelse af lokal indstilling for planlagt scanningstid|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skan|Konfigurer tilsidesættelse af lokal indstilling for den scanningstype, der skal bruges til en planlagt scanning|[Forhindre eller tillade brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skan|Opret et systemgendannelsespunkt|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Skan|Slå fjernelse af elementer til fra mappen med scanningsoversigten|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Skan|Slå heuristik til|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Skan|Slå mailscanning til|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Slå scanning af genfortolkningspunkt til|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Kør fuld scanning på tilknyttede netværksdrev|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Scan arkivfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Scan netværksfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Scan pakkede eksekverbare filer|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Skan | Scan scripts | [Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Se også [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Skan|Scan flytbare drev|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Angiv den maksimale dybde til scanning af arkivfiler|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Angiv den maksimale procentdel af CPU-udnyttelse under en scanning|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Angiv den maksimale størrelse på de arkivfiler, der skal scannes|[Konfigurer scanningsindstillinger i Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skan|Angiv den ugedag, hvor en planlagt scanning skal køres|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Angiv intervallet for hurtig scanning pr. dag|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Angiv den scanningstype, der skal bruges til en planlagt scanning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Angiv tidspunktet for en daglig hurtigsøgning|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Angiv det tidspunkt på dagen, hvor en planlagt scanning skal køres|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skan|Start kun den planlagte scanning, når computeren er tændt, men ikke i brug|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Tillad opdateringer af sikkerhedsintelligens fra Microsoft Update|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Tillad opdateringer af sikkerhedsintelligens, når der køres på batteri|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Tillad, at meddelelser deaktiverer definitionsbaserede rapporter i Microsoft MAPS|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Tillad opdateringer af sikkerhedsintelligens i realtid baseret på rapporter til Microsoft MAPS|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Kontrollér, om der er de nyeste virus- og spywaredefinitioner ved start|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Definer filshares til download af sikkerhedsintelligensopdateringer|[Administrer Microsoft Defender Antivirus opdateringer til beskyttelse og sikkerhedsintelligens](manage-protection-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Definer det antal dage, hvorefter der kræves en opdatering til sikkerhedsintelligens|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Definer antallet af dage, før spywaredefinitioner anses for at være forældede|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Definer antallet af dage, før virusdefinitioner anses for at være forældede|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Definer rækkefølgen af kilder til download af sikkerhedsintelligensopdateringer|[Administrer Microsoft Defender Antivirus opdateringer til beskyttelse og sikkerhedsintelligens](manage-protection-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Start sikkerhedsintelligensopdatering ved start|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Angiv den ugedag, hvor der skal søges efter sikkerhedsopdateringer|[Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Angiv det interval, der skal kontrolleres for sikkerhedsintelligensopdateringer|[Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Angiv det tidspunkt, hvor det skal kontrolleres, om der er opdateringer til security intelligence|[Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Opdateringer til sikkerhedsintelligens|Slå scanning til efter sikkerhedsintelligensopdatering|[Konfigurer planlagte scanninger for Microsoft Defender Antivirus](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Trusler|Angiv niveauer for trusselsbeskeder, hvor standardhandlingen ikke skal udføres, når den registreres|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|
|Trusler|Angiv trusler, som standardhandlingen ikke skal udføres på, når den registreres|[Konfigurer afhjælpning for Microsoft Defender Antivirus scanninger](configure-remediation-microsoft-defender-antivirus.md)|

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Referenceemner om administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
