---
title: Rapportering af værtsfirewall i Microsoft Defender for Endpoint
description: Host og få vist firewallrapportering på Microsoft 365 Defender portal.
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
ms.openlocfilehash: 0dcb03a5398b38e05c3c7c867306444b17b8c720
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490226"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Rapportering af værtsfirewall i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Hvis du er global administrator eller sikkerhedsadministrator, kan du nu hoste firewallrapportering på [Microsoft 365 Defender-portalen](https://security.microsoft.com). Denne funktion giver dig mulighed for at få vist firewallrapportering Windows 10, Windows 11, Windows Server 2019 og Windows Server 2022 fra en central placering.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du skal køre Windows 10 eller Windows 11 eller Windows Server 2019 eller Windows Server 2022.
- Hvis du vil føje enheder til Microsoft Defender for Endpoint-tjenesten, skal du se [her](onboard-configure.md).
- Hvis <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal begynde at modtage dataene, skal du aktivere **Overvågningshændelser** for Windows Defender Firewall med avanceret sikkerhed:
  - [Slip pakke til overvågning af filtreringsplatform](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Overvåg forbindelse til filtreringsplatform](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Aktivér disse hændelser ved hjælp af Gruppepolitik Object Editor, Lokal sikkerhedspolitik eller kommandoerne auditpol.exe. Du kan få flere oplysninger [her](/windows/win32/fwp/auditing-and-logging).
  - De to PowerShell-kommandoer er:
    - `auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable`
    - `auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable`

```powershell
param (
    [switch]$remediate
)
try {

    $categories = "Filtering Platform Packet Drop,Filtering Platform Connection"
    $current = auditpol /get /subcategory:"$($categories)" /r | ConvertFrom-Csv    
    if ($current."Inclusion Setting" -ne "failure") {
        if ($remediate.IsPresent) {
            Write-Host "Remediating. No Auditing Enabled. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})"
            $output = auditpol /set /subcategory:"$($categories)" /failure:enable
            if($output -eq "The command was successfully executed.") {
                Write-Host "$($output)"
                exit 0
            }
            else {
                Write-Host "$($output)"
                exit 1
            }
        }
        else {
            Write-Host "Remediation Needed. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})."
            exit 1
        }
    }

}
catch {
    throw $_
} 
```

## <a name="the-process"></a>Processen

> [!NOTE]
> Sørg for at følge vejledningen i afsnittet ovenfor, og konfigurer dine enheder korrekt til tidlig deltagelse i prøveversionen.

- Når hændelserne er aktiveret, begynder Microsoft 365 Defender at overvåge dataene, hvilket omfatter: 
   - Ekstern IP
   - Ekstern port
   - Lokal port
   - Lokal IP
   - Computernavn
   - Behandl på tværs af indgående og udgående forbindelser
- Administratorer kan nu se [Windows-værtsfirewallaktivitet her](https://security.microsoft.com/firewall).
   - Yderligere rapportering kan lettes ved at downloade [scriptet til brugerdefineret rapportering](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) for at overvåge de Windows Defender Firewall aktiviteter ved hjælp af Power BI.
   - Det kan tage op til 12 timer, før dataene afspejles.

## <a name="supported-scenarios"></a>Understøttede scenarier

Følgende scenarier understøttes under Ring0 Preview:

- [Firewallrapportering](#firewall-reporting)
- [Fra "Computere med blokeret forbindelse" til enhed](#from-computers-with-a-blocked-connection-to-device)
- [Analysér ind på avanceret jagt (opdatering af prøveversion)](#drill-into-advanced-hunting-preview-refresh)

### <a name="firewall-reporting"></a>Firewallrapportering

Her er nogle eksempler på firewallrapportsiderne. Her kan du finde en oversigt over indgående, udgående og programaktivitet. Du kan få adgang til denne side direkte ved at gå til <https://security.microsoft.com/firewall>.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="Rapporteringssiden for værtsfirewallen" lightbox="\images\host-firewall-reporting-page.png":::

Du kan også få adgang til disse rapporter ved at gå til sektionen **Rapporter** > **for sikkerhedsrapportenheder** >  nederst på kortet **Firewall blokerede indgående forbindelser**.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>Fra "Computere med blokeret forbindelse" til enhed

Kort understøtter interaktive objekter. Du kan analysere en enheds aktivitet ved at klikke på enhedsnavnet, hvilket starter Microsoft 365 Defender-portalen på en ny fane og fører dig direkte til fanen **Enhedstidslinje**.

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="Computere med en blokeret forbindelsesside" lightbox="\images\firewall-reporting-blocked-connection.png":::

Du kan nu vælge fanen **Tidslinje** , som giver dig en liste over hændelser, der er knyttet til den pågældende enhed.

Når du har klikket på knappen **Filtre** i øverste højre hjørne af visningsruden, skal du vælge den ønskede type hændelse. I dette tilfælde skal du vælge **Firewallhændelser** , hvorefter ruden filtreres til Firewall-hændelser.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="Knappen Filtre" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Analysér ind på avanceret jagt (opdatering af prøveversion)

Firewallrapporter understøtter detailudledning fra kortet direkte til **Avanceret jagt** ved at klikke på knappen **Åbn avanceret jagt** . Forespørgslen er udfyldt på forhånd.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="Knappen Åbn avanceret jagt" lightbox="\images\firewall-reporting-advanced-hunting.png":::

Forespørgslen kan nu udføres, og alle relaterede firewallhændelser fra de sidste 30 dage kan udforskes.

Hvis du vil have mere rapportering eller brugerdefinerede ændringer, kan forespørgslen eksporteres til Power BI til yderligere analyse. Brugerdefineret rapportering kan lettes ved at downloade [scriptet til brugerdefineret rapportering](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) for at overvåge de Windows Defender Firewall aktiviteter ved hjælp af Power BI.
