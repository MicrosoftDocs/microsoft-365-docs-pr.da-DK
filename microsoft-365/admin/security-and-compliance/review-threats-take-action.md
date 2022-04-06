---
title: Gennemse registrerede trusler, og reaktion
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
description: Få mere at vide om, hvordan du gennemser og administrerer trusler, der registreres af Microsoft Defender Antivirus på Windows 10 enheder.
ms.openlocfilehash: e0e0613ad7805b8c4bde221aa2192c788fb75106
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606678"
---
# <a name="review-detected-threats-and-take-action"></a>Gennemse registrerede trusler, og reaktion

Så snart der registreres en skadelig fil eller software, Microsoft Defender Antivirus den og forhindrer den i at køre. Og med cloud-leveret beskyttelse slået til føjes nyligt registrerede trusler til antivirus- og antimalwareprogrammet, så dine andre enheder og brugere også er beskyttet.

Microsoft Defender Antivirus registrerer og beskytter mod følgende slags trusler:

- Virus, malware og webbaserede trusler på enheder
- Forsøg på phishing
- Datatyveriforsøg

Som it-fagperson/administrator kan du få vist oplysninger om trusselsregistreringer på tværs Windows 10 enheder, der er tilmeldt [Intune](/mem/intune/enrollment/device-enrollment) i Microsoft 365 Administration. Du får vist oversigtsoplysninger, f.eks.:

- Hvor mange enheder, der skal beskyttes mod antivirus
- Hvor mange enheder, der ikke overholder sikkerhedspolitikkerne
- Hvor mange trusler, der i øjeblikket er aktive, afhjælpes eller løses

Du har flere muligheder for at få vist specifikke oplysninger om trusselsregistreringer og enheder:

- Siden **Aktive** enheder i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Se [Administrer trusselsregistreringer på siden Aktive enheder](#manage-threat-detections-on-the-active-devices-page) i denne artikel.
- Siden **Aktive trusler** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Se [Administrer trusselsregistreringer på siden Aktive trusler](#manage-threat-detections-on-the-active-threats-page) i denne artikel.
- Siden **Antivirus** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Se [Administrer trusselsregistreringer Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) denne artikel.

Du kan få mere at vide [under Trusler, der er registreret af Microsoft Defender Antivirus](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Administrer trusselsregistreringer på **siden Aktive** enheder

Følgende procedure gælder for kunder, der har Microsoft 365 Business Premium.

1. Gå til Microsoft 365 Administration, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> og log på.

2. På navigationssiden skal du vælge **EnhederAktivér** >  enheder. Du får vist en liste over aktive enheder og detaljer, f.eks. beskyttelsesstatus, antivirustilstand (AV)-beskyttelsestilstand og antallet af registrerede aktive trusler.

3. Vælg en enhed for at få vist flere oplysninger om enheden og tilgængelige handlinger. Der åbnes et pop op-vindue med anbefalinger og tilgængelige handlinger, f.eks Opdateringspolitik **, Opdater** **antivirus****, Kør** hurtig scanning, **Kør fuld scanning** og meget mere.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Administrer trusselsregistreringer på **siden Aktive** trusler

Følgende procedure gælder for kunder, der har Microsoft 365 Business Premium. [Windows 10 enheder skal være sikret](../setup/secure-win-10-pcs.md) [og tilmeldt Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> Siden **Microsoft Defender Antivirus** aktive **trusler rulles** ud i faser, så du har muligvis ikke øjeblikkelig adgang til dem.

1. Gå til Microsoft 365 Administration, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> og log på.

2. På kortet **Microsoft Defender Antivirus** skal du **vælge Vis aktive trusler**. (Du kan også vælge Tilstand i **navigationsruden** >  **Trusler & antivirus**.)

3. På siden **Aktive trusler skal du** vælge en registreret trussel for at få mere at vide om den. Der åbnes en pop op-vindue med oplysninger om denne trussel, herunder hvilke enheder der er påvirket.

4. Vælg en enhed i pop op-pop-menuen for at få vist tilgængelige handlinger, f.eks Opdateringspolitik **, Opdater** **antivirus**, Kør **hurtig scanning** og meget mere.

## <a name="actions-you-can-take"></a>Handlinger, du kan udføre

Når du får vist detaljer om specifikke trusler eller enheder, får du vist anbefalinger og en eller flere handlinger, du kan udføre. I følgende tabel beskrives de handlinger, du kan få vist.<br><br>

| Handling | Beskrivelse |
|--|--|
| Konfigurer beskyttelse | Dine politikker for trusselsbeskyttelse skal konfigureres. Vælg linket for at gå til siden konfiguration af politik.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med slutpunktssikkerhedspolitikker i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Opdateringspolitik | Beskyttelsespolitikkerne for dit antivirusprogram og i realtid skal opdateres eller konfigureres. Vælg linket for at gå til siden til konfiguration af politik.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med slutpunktssikkerhedspolitikker i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Kør Hurtig scanning | Starter en hurtig antivirusscanning på enheden, fokuserer på almindelige steder, hvor malware kan være registreret, f.eks registreringsdatabasenøgler og kendte Windows startmapper. |
| Kør fuld scanning | Starter en komplet antivirusscanning på enheden, fokuserer på fælles steder, hvor der kan registreres malware, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Opdater antivirus | Kræver, at enheden henter [sikkerhedsintelligensopdateringer](https://go.microsoft.com/fwlink/?linkid=2149926) til antivirus- og antimalwarebeskyttelse. |
| Genstart enhed | Tvinger en Windows 10 til at genstarte inden for fem minutter.<br><br>**VIGTIGT:** Ejeren af enheden eller brugeren får ikke automatisk besked om genstart og kan miste ikke-gemt arbejde. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Administrer trusselsregistreringer i Microsoft Endpoint Manager

Du kan bruge Microsoft Endpoint Manager til at administrere trusselsregistreringer. Windows 10 enheder skal være [tilmeldt Intune (en](/mem/intune/enrollment/windows-enrollment-methods) del af Microsoft Endpoint Manager).

1. Gå til Microsoft Endpoint Manager Administration, <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> og log på.

2. Vælg Slutpunktssikkerhed i **navigationsruden**.

3. Under **Administrer** skal du vælge **Antivirus**. Du får vist flere faner, f.eks Oversigt **, Windows 10 usunde slutpunkter** og **Windows 10 registreret malware**.

4. Gennemse oplysningerne på de tilgængelige faner, og gør derefter de nødvendige handlinger.

Antag f.eks., at enheder er angivet **på Windows 10 registreret malware**. Når du vælger en enhed, er visse handlinger tilgængelige, f.eks **Genstart, Hurtig** **scanning,** **Fuld** **scanning, Synkronisering** eller **Opdater signaturer**. Vælg en handling for den pågældende enhed.

I følgende tabel beskrives de handlinger, du kan se i Microsoft Endpoint Manager.<br><br>

| Handling | Beskrivelse |
|--|--|
| Genstart | Tvinger en Windows 10 til at genstarte inden for fem minutter.<br><br>**VIGTIGT:** Ejeren af enheden eller brugeren får ikke automatisk besked om genstart og kan miste ikke-gemt arbejde. |
| Hurtig scanning | Starter en hurtig antivirusscanning på enheden, fokuserer på almindelige steder, hvor malware kan være registreret, f.eks registreringsdatabasenøgler og kendte Windows startmapper. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Fuld scanning | Starter en komplet antivirusscanning på enheden, fokuserer på fælles steder, hvor der kan registreres malware, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synkroniser | Kræver, at du har en enhed til at tjekke ind med Intune (en del Microsoft Endpoint Manager). Når enheden tjekker ind, modtager enheden alle ventende handlinger eller politikker, der er tildelt enheden. |
| Opdater signaturer | Kræver, at enheden henter [sikkerhedsintelligensopdateringer](https://go.microsoft.com/fwlink/?linkid=2149926) til antivirus- og antimalwarebeskyttelse. |

> [!TIP]
> Du kan få mere at vide [under Fjernhandlinger for enheder](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Sådan sender du en fil til malwareanalyse

Hvis du har en fil, du mener er gået glip af eller fejlagtigt klassificeret som malware, kan du sende denne fil til Microsoft til malwareanalyse. Brugere og it-administratorer kan sende en fil til analyse. Gå til [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](secure-your-business-data.md)

[Oversigt over Microsoft Defender for Business](../../security/defender-business/mdb-overview.md) (Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022)