---
title: Værtsfirewallrapportering i Microsoft Defender til slutpunkt
description: Vær vært, og få vist firewallrapportering Microsoft 365 Defender portal.
keywords: windows defender, firewall
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: b5aaad7363b42e18a0ca21e4d56d118218cec1a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63606579"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Værtsfirewallrapportering i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Hvis du er administrator, kan du nu hoste firewallrapportering til [Microsoft 365 Defender-portalen](https://security.microsoft.com). Denne funktion gør det muligt at få vist Windows 10-, Windows 11-, Windows Server 2019- og Windows Server 2022-firewallrapportering fra en centraliseret placering.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du skal køre Windows 10 eller Windows 11 eller Windows Server 2019 eller Windows Server 2022.
- Hvis du vil onboarde enheder til Microsoft Defender for Endpoint-tjenesten, skal du se [her](onboard-configure.md).
- Hvis <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal begynde at modtage dataene, skal du aktivere **overvågningshændelser** for Windows Defender Firewall med Avanceret sikkerhed:
  - [Overvågningsfiltreringsplatformens pakkedråbe](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Overvågningsfiltreringsplatformforbindelse](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Aktivér disse hændelser ved Gruppepolitik objekteditor, lokal sikkerhedspolitik eller auditpol.exe-kommandoer. Du kan finde flere oplysninger [her](/windows/win32/fwp/auditing-and-logging).
  - De to PowerShell-kommandoer er:
    - **auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable**
    - **auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable**

## <a name="the-process"></a>Processen

> [!NOTE]
> Sørg for at følge vejledningen fra ovenstående afsnit og korrekt konfigurere dine enheder til den tidlige forhåndsvisningsdeltagelse.

- Når du har aktiveret hændelserne, Microsoft 365 Defender du begynde at overvåge dataene.
  - Fjern-IP, Fjernport, Lokal port, Lokal IP, Computernavn, Proces på tværs af indgående og udgående forbindelser.
- Administratorer kan nu se Windows værtsfirewallaktivitet [her](https://security.microsoft.com/firewall).
  - Yderligere rapportering kan muliggøres ved at downloade [scriptet Brugerdefineret rapportering](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) for at overvåge Windows Defender Firewall-aktiviteter ved hjælp Power BI.
  - Det kan tage op til 12 timer, før dataene afspejles.

## <a name="supported-scenarios"></a>Understøttede scenarier

Følgende scenarier understøttes under forhåndsvisning af Ring0.

### <a name="firewall-reporting"></a>Firewallrapportering

Her er et par eksempler på firewall-rapportsiderne. Her finder du en oversigt over indgående, udgående og programaktivitet. Du kan få adgang til denne side direkte ved at gå til <https://security.microsoft.com/firewall>.

> [!div class="mx-imgBorder"]
> ![Rapporteringsside for værtsfirewall.](\images\host-firewall-reporting-page.png)

Disse rapporter kan også åbnes ved at gå til **ReportsSecurity** >  **ReportDevices** >  (sektion), der er placeret nederst på kortet **Firewall blokerede indgående** forbindelser.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>Fra "Computere med blokeret forbindelse" til enhed

Kort understøtter interaktive objekter. Du kan analysere aktiviteten for en enhed ved at klikke på enhedsnavnet, som åbner Microsoft 365 Defender-portalen på en ny fane og fører dig direkte til fanen Tidslinje **for enhed.**

> [!div class="mx-imgBorder"]
> ![Computere med blokeret forbindelse.](\images\firewall-reporting-blocked-connection.png)

Du kan nu vælge fanen **Tidslinje** , som giver dig en liste over hændelser, der er knyttet til den pågældende enhed.

Når du har **klikket på** knappen Filtre i øverste højre hjørne af visningsruden, skal du vælge den ønskede begivenhedstype. I dette tilfælde skal du **vælge Firewall-hændelser** , og ruden filtreres til Firewall-hændelser.

> [!div class="mx-imgBorder"]
> ![Knappen Filtre.](\images\firewall-reporting-filters-button.png)

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Analyser ind i avanceret jagt (forhåndsvisning af opdatering)

Firewallrapporter understøtter at der kan analyseres fra kortet direkte **ind i Avanceret** jagt ved at klikke **på knappen Åbn avanceret jagt** . Forespørgslen udfyldes på forhånd.

> [!div class="mx-imgBorder"]
> ![Åbn avanceret jagtknap.](\images\firewall-reporting-advanced-hunting.png)

Forespørgslen kan nu udføres, og alle relaterede Firewall-hændelser fra de seneste 30 dage kan udforskes.

Til yderligere rapportering eller brugerdefinerede ændringer kan forespørgslen eksporteres til Power BI til yderligere analyse. Brugerdefineret rapportering kan muliggøres ved at downloade [scriptet Brugerdefineret rapportering](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) for at overvåge Windows Defender Firewall-aktiviteter ved hjælp Power BI.
