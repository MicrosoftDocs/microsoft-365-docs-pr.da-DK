---
title: Konfigurere Microsoft Defender Antivirus meddelelser
description: Få mere at vide om, hvordan du konfigurerer og tilpasser både standardmeddelelser Microsoft Defender Antivirus andre meddelelser på slutpunkter.
keywords: meddelelser, defender, antivirus, slutpunkt, administration, administrator
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 287e49a92032e725153065ef3d996e2b5c14baf9
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63606507"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Konfigurere Microsoft Defender Antivirus meddelelser, der vises på slutpunkter

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I Windows 10 og Windows 11 er programmeddelelser om registrering og afhjælpning af malware mere robuste, ensartede og kortfattede. Microsoft Defender Antivirus meddelelser på slutpunkter, når scanningerne er fuldført, og trusler registreres. Meddelelser følger både planlagte og manuelt udløste scanninger. Disse meddelelser vises også i **Meddelelsescenter**, og en oversigt over scanninger og trusselsregistreringer vises med jævne mellemrum.

Hvis du er en del af organisationens sikkerhedsteam, kan du konfigurere, hvordan meddelelser vises på slutpunkter, f.eks. meddelelser, der beder om en genstart af systemet, eller som indikerer, at en trussel er blevet registreret og afhjulpet.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Konfigurere antivirusmeddelelser ved Gruppepolitik appen Windows Sikkerhed computeren

Du kan konfigurere visningen af yderligere meddelelser, f.eks. de seneste oversigter over trusselsregistrering, [i appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md) og med Gruppepolitik.

> [!NOTE]
> I Windows 10 version 1607 kaldes funktionen **Udvidede** meddelelser og blev konfigureret under **Windows Indstillinger** \> **Opdatering & sikkerhedsindstillinger** \> **Windows Defender**. I Gruppepolitik for alle versioner af Windows 10 og Windows 11, kaldes meddelelsesfunktionen **Forbedrede meddelelser**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Brug Gruppepolitik til at deaktivere yderligere meddelelser

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

4. Vælg **Administrative skabeloner**.

5. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** >  **Rapportering**.

6. Dobbeltklik på **Deaktiver udvidede meddelelser**, og angiv indstillingen til **Aktiveret**. Vælg derefter **OK**. Dette forhindrer, at der vises yderligere meddelelser.

> [!IMPORTANT]
> Deaktivering af yderligere meddelelser deaktiverer ikke vigtige meddelelser, f.eks. trusselsregistrering og afhjælpningsadvarsler.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Brug appen Windows Sikkerhed til at deaktivere yderligere meddelelser

1. Åbn appen Windows Sikkerhed ved at klikke på skjoldet på proceslinjen eller søge i menuen Start for **Sikkerhed**.

2. Vælg **flisen & virusbeskyttelse** (eller skjoldikonet på den venstre menulinje), og vælg derefter **indstillinger for & af trusselsbeskyttelse**

3. Rul til sektionen **Meddelelser** , og vælg **Skift indstillinger for meddelelser**.

4. Skub knappen til Fra **eller Til** **for at** deaktivere eller aktivere yderligere meddelelser.

> [!IMPORTANT]
> Deaktivering af yderligere meddelelser deaktiverer ikke vigtige meddelelser, f.eks. trusselsregistrering og afhjælpningsadvarsler.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Konfigurer standardmeddelelser på slutpunkter ved hjælp af Gruppepolitik

Du kan bruge Gruppepolitik til at:

- Vis yderligere, brugerdefineret tekst på slutpunkter, når brugeren skal udføre en handling
- Skjul alle meddelelser på slutpunkter
- Skjul genstartsmeddelelser på slutpunkter

Det kan være nyttigt at skjule meddelelser i situationer, hvor du ikke kan skjule hele Microsoft Defender Antivirus brugergrænsefladen. Se [Forebyd, at brugere kan se eller arbejde Microsoft Defender Antivirus brugergrænsefladen](prevent-end-user-interaction-microsoft-defender-antivirus.md), hvis du vil have mere at vide. Når du skjuler meddelelser, sker det kun på slutpunkter, som politikken er installeret på. Meddelelser, der er relateret til handlinger, der skal foretages (f.eks. en genstart), vises [stadig på Microsoft Endpoint Manager Endpoint Protection dashboard og rapporter for overvågning](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Hvis du vil føje brugerdefinerede kontaktoplysninger til slutpunktsmeddelelser, skal [du se Windows Sikkerhed appen til organisationen](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Brug Gruppepolitik til at skjule meddelelser

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. På fanen **Gruppepolitik skal du** gå til **Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus klientgrænseflade**\>. 

5. Dobbeltklik på Suppress **all notifications and** set the option to **Enabled**. 

6. Vælg **OK**. Dette forhindrer, at der vises yderligere meddelelser.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Brug Gruppepolitik til at skjule genstartsmeddelelser

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus klientgrænseflade**\>.

5. Dobbeltklik på **Undertrykker genstartsmeddelelser,** og angiv indstillingen til **Aktiveret**. 

5. Vælg **OK**. Dette forhindrer, at der vises yderligere meddelelser.

