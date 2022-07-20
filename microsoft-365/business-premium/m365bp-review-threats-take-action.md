---
title: Gennemse registrerede trusler på enheder, og udfør handlinger
f1.keywords: NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.date: 07/19/2022
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Få mere at vide om, hvordan du gennemser og administrerer trusler, der er registreret af Microsoft Defender Antivirus, på dine Windows-enheder.
ms.openlocfilehash: e389eea971c2d9763816f7b1184cf98b3f41113a
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893563"
---
# <a name="review-detected-threats"></a>Gennemse registrerede trusler

Så snart der registreres en skadelig fil eller software, blokerer Microsoft Defender den og forhindrer den i at køre. Og med skybaseret beskyttelse slået til, føjes nyligt registrerede trusler til antivirus- og antimalwareprogrammet, så dine andre enheder og brugere også er beskyttet.

Microsoft Defender Antivirus registrerer og beskytter mod følgende typer trusler:

- Virus, malware og webbaserede trusler på enheder
- Phishingforsøg
- Forsøg på datatyveri

Som it-ekspert/administrator kan du få vist oplysninger om trusselsregistreringer på tværs af [Windows-enheder, der er tilmeldt Intune](/mem/intune/enrollment/device-enrollment) i Microsoft 365 Administration. Du får vist oversigtsoplysninger, f.eks.:

- Hvor mange enheder har brug for antivirusbeskyttelse
- Hvor mange enheder der ikke overholder sikkerhedspolitikker
- Hvor mange trusler der i øjeblikket er aktive, afhjælpes eller løses

## <a name="actions-you-can-take"></a>Handlinger, du kan foretage

Når du får vist detaljer om bestemte trusler eller enheder, får du vist anbefalinger og en eller flere handlinger, du kan foretage. I følgende tabel beskrives de handlinger, du kan se.<br><br>

| Handling | Beskrivelse |
|--|--|
| Konfigurer beskyttelse | Dine politikker for trusselsbeskyttelse skal konfigureres. Vælg linket for at gå til siden til konfiguration af politikken.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Opdater politik | Dine beskyttelsespolitikker for antivirus og realtid skal opdateres eller konfigureres. Vælg linket for at gå til siden til konfiguration af politik.<br><br>Har du brug for hjælp? Se [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Kør hurtig scanning | Starter en hurtig antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, f.eks. registreringsdatabasenøgler og kendte Windows-startmapper. |
| Kør fuld scanning | Starter en komplet antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Opdater antivirus | Kræver, at enheden henter [opdateringer til sikkerhedsintelligens](https://go.microsoft.com/fwlink/?linkid=2149926) til beskyttelse mod antivirus og antimalware. |
| Genstart enhed | Gennemtvinger, at en Windows-enhed genstartes inden for fem minutter.<br><br>**VIGTIGT:** Enhedsejeren eller -brugeren får ikke automatisk besked om genstarten og kan miste arbejde, der ikke er gemt. |

## <a name="view-and-manage-threat-detections-in-the-microsoft-365-defender-portal"></a>Få vist og administrer trusselsregistreringer på Microsoft 365 Defender-portalen

1. Gå til ([Microsoft 365 Defender-portalen](https://security.microsoft.com)), og log på.

1. Vælg **Threat Analytics** i navigationsruden for at se alle de aktuelle trusler. De er kategoriseret efter alvorsgrad og type af trusler.

1. Klik på en trussel for at se flere detaljer om truslen.

1. I tabellen kan du filtrere beskederne i henhold til en række kriterier.

## <a name="manage-threat-detections-in-microsoft-intune"></a>Administrer trusselsregistreringer i Microsoft InTune

Du kan også bruge Microsoft Endpoint Manager til at administrere trusselsregistreringer. Først skal alle enheder, uanset om det er Windows, iOS eller Android, [være tilmeldt Intune](/mem/intune/enrollment/windows-enrollment-methods) (en del af Microsoft Endpoint Manager).

1. Gå til Microsoft Endpoint Manager Administration på , og log på<a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a>.

2. Vælg **Slutpunktssikkerhed** i navigationsruden.

3. Under **Administrer** skal du vælge **Antivirus**. Du får vist faner for **Oversigt**, **Usunde slutpunkter** og **Aktiv malware**.

4. Gennemse oplysningerne under de tilgængelige faner, og foretag derefter de nødvendige handlinger.

Lad os f.eks. antage, at enheder er angivet under fanen **Aktiv malware** . Når du vælger en enhed, har du visse handlinger tilgængelige, f.eks **. Genstart**, **Hurtig scanning**, **Fuld scanning**, **Synkroniser** eller **Opdater signaturer**. Vælg en handling for den pågældende enhed.

I følgende tabel beskrives de handlinger, du kan se i Microsoft Endpoint Manager.<br><br>

| Handling | Beskrivelse |
|--|--|
| Genstarte | Gennemtvinger, at en Windows-enhed genstartes inden for fem minutter.<br><br>**VIGTIGT:** Enhedsejeren eller -brugeren får ikke automatisk besked om genstarten og kan miste arbejde, der ikke er gemt. |
| Hurtig scanning | Starter en hurtig antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, f.eks. registreringsdatabasenøgler og kendte Windows-startmapper. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Fuld scanning | Starter en komplet antivirusscanning på enheden med fokus på almindelige placeringer, hvor malware kan registreres, og herunder alle filer og mapper på enheden. Resultaterne sendes til [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Sync | Kræver, at en enhed tjekker ind med Intune (en del af Microsoft Endpoint Manager). Når enheden tjekker ind, modtager enheden eventuelle ventende handlinger eller politikker, der er tildelt enheden. |
| Opdater signaturer | Kræver, at enheden henter [opdateringer til sikkerhedsintelligens](https://go.microsoft.com/fwlink/?linkid=2149926) til beskyttelse mod antivirus og antimalware. |

> [!TIP]
> Du kan få flere oplysninger under [Fjernhandlinger for enheder](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Sådan indsender du en fil til malwareanalyse

Hvis du har en fil, som du mener blev savnet eller fejlagtigt klassificeret som malware, kan du sende denne fil til Microsoft til analyse af malware. Brugere og it-administratorer kan sende en fil til analyse. Besøg [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)

[Oversigt over Microsoft Defender til virksomheder](../security/defender-business/mdb-overview.md) (Defender for Business udrulles til Microsoft 365 Business Premium kunder fra 1. marts 2022)
