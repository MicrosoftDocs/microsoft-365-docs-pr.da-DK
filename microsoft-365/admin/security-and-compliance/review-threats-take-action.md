---
title: Gennemgå registrerede trusler, og udfør handlinger
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Få mere at vide om, hvordan du gennemser og administrerer trusler, der er registreret af Microsoft Defender Antivirus på dine Windows 10 enheder.
ms.openlocfilehash: 2d75149f8bcb4ea13e1e474acbb1dedfccb4ec50
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469464"
---
# <a name="review-threats-detected-by-microsoft-defender-antivirus-and-take-action"></a>Gennemse trusler, der er registreret af Microsoft Defender Antivirus, og udfør handlinger

Så snart der registreres en skadelig fil eller software, blokerer Microsoft Defender Antivirus den og forhindrer den i at køre. Og med skybaseret beskyttelse slået til, føjes nyligt registrerede trusler til antivirus- og antimalwareprogrammet, så dine andre enheder og brugere også er beskyttet.

Microsoft Defender Antivirus registrerer og beskytter mod følgende typer trusler:

- Virus, malware og webbaserede trusler på enheder
- Phishingforsøg
- Forsøg på datatyveri

Som it-ekspert/administrator kan du få vist oplysninger om trusselsregistreringer på tværs [af Windows 10 enheder, der er tilmeldt Intune](/mem/intune/enrollment/device-enrollment) i Microsoft 365 Administration. Du får vist oversigtsoplysninger, f.eks.:

- Hvor mange enheder har brug for antivirusbeskyttelse
- Hvor mange enheder, der ikke overholder sikkerhedspolitikker
- Hvor mange trusler der i øjeblikket er aktive, afhjælpes eller løses

Du har flere muligheder for at få vist specifikke oplysninger om trusselsregistreringer og -enheder:

- Siden **Aktive enheder** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Se [Administrer trusselsregistreringer på siden Aktive enheder](#manage-threat-detections-on-the-active-devices-page) i denne artikel.
- Siden **Aktive trusler** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Se [Administrer trusselsregistreringer på siden Aktive trusler](#manage-threat-detections-on-the-active-threats-page) i denne artikel.
- Siden **Antivirus** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Se [Administrer trusselsregistreringer i Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) i denne artikel.

Du kan få mere at vide under [Trusler registreret af Microsoft Defender Antivirus](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Administrer trusselsregistreringer på siden **Aktive enheder**

Følgende procedure gælder for kunder, der har Microsoft 365 Business Premium.

1. Gå til Microsoft 365 Administration på , og log på<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Vælg **EnhederAktive** >  enheder på navigationssiden. Du får vist en liste over aktive enheder og oplysninger, f.eks. beskyttelsesstatus, beskyttelsestilstand for antivirus (AV) og antallet af registrerede aktive trusler.

3. Vælg en enhed for at få vist flere oplysninger om den pågældende enhed og tilgængelige handlinger. Der åbnes et pop op-vindue med anbefalinger og tilgængelige handlinger, f.eks **. Opdateringspolitik**, **Opdater antivirus**, **Kør hurtig scanning**, **Kør fuld scanning** med mere.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Administrer trusselsregistreringer på siden **Aktive trusler**

Følgende procedure gælder for kunder, der har Microsoft 365 Business Premium. [Windows 10 enheder skal sikres](../setup/secure-win-10-pcs.md) og [være tilmeldt Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> Siden **Microsoft Defender Antivirus** kort og **aktive trusler** udrulles i faser, så du har muligvis ikke umiddelbar adgang til dem.

1. Gå til Microsoft 365 Administration på , og log på<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Vælg **Få vist aktive trusler** på kortet **Microsoft Defender Antivirus**. (Du kan også vælge **Tilstand** >  i navigationsruden **Trusler & antivirus**).

3. På siden **Aktive trusler** skal du vælge en registreret trussel for at få mere at vide om den. Der åbnes et pop op-vindue med oplysninger om denne trussel, herunder hvilke enheder der påvirkes.

4. På pop op-vinduet skal du vælge en enhed for at få vist tilgængelige handlinger, f.eks **Opdateringspolitik**, **Opdater antivirus**, **Kør hurtig scanning** og meget mere.

## <a name="actions-you-can-take"></a>Handlinger, du kan foretage

Når du får vist detaljer om bestemte trusler eller enheder, får du vist anbefalinger og en eller flere handlinger, du kan foretage. I følgende tabel beskrives de handlinger, du kan se.<br><br>

| Handling | Beskrivelse |
|--|--|
| Konfigurer beskyttelse | Dine politikker for trusselsbeskyttelse skal konfigureres. Vælg linket for at gå til siden til konfiguration af politikken.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Opdater politik | Dine beskyttelsespolitikker for antivirus og realtid skal opdateres eller konfigureres. Vælg linket for at gå til siden til konfiguration af politik.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Kør hurtig scanning | Starter en hurtig antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, f.eks. registreringsdatabasenøgler og kendte Windows startmapper. |
| Kør fuld scanning | Starter en komplet antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Opdater antivirus | Kræver, at enheden henter [opdateringer til sikkerhedsintelligens](https://go.microsoft.com/fwlink/?linkid=2149926) til beskyttelse mod antivirus og antimalware. |
| Genstart enhed | Gennemtvinger, at en Windows 10 enhed genstartes inden for fem minutter.<br><br>**VIGTIGT:** Ejeren eller brugeren af enheden får ikke automatisk besked om genstarten og kan miste arbejde, der ikke er gemt. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Administrer trusselsregistreringer i Microsoft Endpoint Manager

Du kan bruge Microsoft Endpoint Manager til at administrere trusselsregistreringer. Windows 10 enheder skal [være tilmeldt Intune](/mem/intune/enrollment/windows-enrollment-methods) (en del af Microsoft Endpoint Manager).

1. Gå til Microsoft Endpoint Manager Administration på , og log på<a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a>.

2. Vælg **Slutpunktssikkerhed** i navigationsruden.

3. Under **Administrer** skal du vælge **Antivirus**. Du får vist flere faner, f.eks **. Oversigt**, **Windows 10 usunde slutpunkter** og **Windows 10 registreret malware**.

4. Gennemse oplysningerne under de tilgængelige faner, og foretag derefter de nødvendige handlinger.

Antag f.eks., at enheder er angivet på fanen **Windows 10 registreret malware**. Når du vælger en enhed, har du visse handlinger tilgængelige, f.eks **. Genstart**, **Hurtig scanning**, **Fuld scanning**, **Synkroniser** eller **Opdater signaturer**. Vælg en handling for den pågældende enhed.

I følgende tabel beskrives de handlinger, du kan se i Microsoft Endpoint Manager.<br><br>

| Handling | Beskrivelse |
|--|--|
| Genstarte | Gennemtvinger, at en Windows 10 enhed genstartes inden for fem minutter.<br><br>**VIGTIGT:** Ejeren eller brugeren af enheden får ikke automatisk besked om genstarten og kan miste arbejde, der ikke er gemt. |
| Hurtig scanning | Starter en hurtig antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, f.eks. registreringsdatabasenøgler og kendte Windows startmapper. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Fuld scanning | Starter en komplet antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Sync | Kræver, at en enhed tjekker ind med Intune (en del af Microsoft Endpoint Manager). Når enheden tjekker ind, modtager enheden eventuelle ventende handlinger eller politikker, der er tildelt enheden. |
| Opdater signaturer | Kræver, at enheden henter [opdateringer til sikkerhedsintelligens](https://go.microsoft.com/fwlink/?linkid=2149926) til beskyttelse mod antivirus og antimalware. |

> [!TIP]
> Du kan få flere oplysninger under [Fjernhandlinger for enheder](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Sådan indsender du en fil til malwareanalyse

Hvis du har en fil, som du mener blev savnet eller fejlagtigt klassificeret som malware, kan du sende denne fil til Microsoft til analyse af malware. Brugere og it-administratorer kan sende en fil til analyse. Besøg [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til forretningsplaner](../../admin/security-and-compliance/secure-your-business-data.md)

[Oversigt over Microsoft Defender til virksomheder](../../security/defender-business/mdb-overview.md) (Defender for Business udrulles til Microsoft 365 Business Premium kunder fra 1. marts 2022)