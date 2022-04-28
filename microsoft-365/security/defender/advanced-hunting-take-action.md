---
title: Udfør handlinger på avancerede resultater af jagtforespørgslen i Microsoft 365 Defender
description: Håndter hurtigt trusler og berørte aktiver i dine avancerede resultater af jagtforespørgsler
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, handle
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b7fbe659902bf89023e994f4e1304f25f3934db8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097587"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Udfør handlinger på avancerede resultater af jagtforespørgslen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Du kan hurtigt indeholde trusler eller løse kompromitterede aktiver, som du finder i [avanceret jagt](advanced-hunting-overview.md) ved hjælp af effektive og omfattende handlingsmuligheder. Med disse indstillinger kan du:

- Udfør forskellige handlinger på enheder
- Sæt filer i karantæne

## <a name="required-permissions"></a>Påkrævede tilladelser
Hvis du vil udføre handlinger på enheder via avanceret jagt, skal du have en rolle i Microsoft Defender for Endpoint med [tilladelser til at indsende afhjælpningshandlinger på enheder](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Hvis du ikke kan udføre handlinger, skal du kontakte en global administrator for at få følgende tilladelse:

*Aktive afhjælpningshandlinger > Threat and håndtering af sikkerhedsrisici – Afhjælpningshåndtering*

Hvis du vil handle på e-mails gennem avanceret jagt, har du brug for en rolle i Microsoft Defender for Office 365 til at [søge efter og fjerne e-mails](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="take-various-actions-on-devices"></a>Udfør forskellige handlinger på enheder
Du kan foretage følgende handlinger på enheder, der er identificeret af kolonnen `DeviceId` i dine forespørgselsresultater:

- Isolere berørte enheder for at indeholde en infektion eller forhindre angreb i at bevæge sig side om side
- Indsaml undersøgelsespakken for at få flere tekniske oplysninger
- Kør en antivirusscanning for at finde og fjerne trusler ved hjælp af de nyeste sikkerhedsintelligensopdateringer
- Start en automatiseret undersøgelse for at kontrollere og afhjælpe trusler på enheden og muligvis andre berørte enheder
- Begræns appkørsel til kun Microsoft-signerede eksekverbare filer, der forhindrer efterfølgende trusselsaktivitet via malware eller andre eksekverbare filer, der ikke er tillid til

Hvis du vil vide mere om, hvordan disse svarhandlinger udføres via Microsoft Defender for Endpoint, skal du [læse om svarhandlinger på enheder](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
### <a name="quarantine-files"></a>Sæt filer i karantæne
Du kan udrulle *karantænehandlingen* på filer, så de automatisk bliver sat i karantæne, når de registreres. Når du vælger denne handling, kan du vælge mellem følgende kolonner for at identificere, hvilke filer i dine forespørgselsresultater der skal sættes i karantæne:

- `SHA1`: I de mest avancerede jagttabeller refererer denne kolonne til SHA-1 for den fil, der blev påvirket af den registrerede handling. Hvis en fil f.eks. blev kopieret, ville den pågældende fil være den kopierede fil.
- `InitiatingProcessSHA1`: I de mest avancerede jagttabeller henviser denne kolonne til den fil, der er ansvarlig for at starte den registrerede handling. Hvis en underordnet proces f.eks. blev startet, ville denne initiatorfil være en del af den overordnede proces. 
- `SHA256`: Denne kolonne er SHA-256-ækvivalenten af den fil, der identificeres af kolonnen `SHA1` .
- `InitiatingProcessSHA256`: Denne kolonne er SHA-256-ækvivalenten af den fil, der identificeres af kolonnen `InitiatingProcessSHA1` .

Hvis du vil vide mere om, hvordan karantænehandlinger udføres, og hvordan filer kan gendannes, skal [du læse om svarhandlinger på filer](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>For at finde filer og sætte dem i karantæne skal forespørgselsresultaterne også indeholde `DeviceId` værdier som enheds-id'er.  

Hvis du vil udføre en af de beskrevne handlinger, skal du vælge en eller flere poster i dine forespørgselsresultater og derefter vælge **Udfør handlinger**. En guide fører dig gennem processen med at vælge og derefter indsende dine foretrukne handlinger.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="Indstillingen Udfør handlinger på portalen Microsoft 365 Defender" lightbox="../../media/take-action-multiple.png":::


## <a name="take-various-actions-on-emails"></a>Udfør forskellige handlinger i mails
Ud over enhedsfokuserede afhjælpningstrin kan du også udføre nogle handlinger på mails fra dine forespørgselsresultater. Vælg de poster, du vil udføre en handling for, vælg **Udfør handlinger**, og vælg derefter dit valg på følgende under **Vælg handlinger**:
- `Move to mailbox folder` – vælg denne for at flytte mailmeddelelserne til mappen Uønsket mail, Indbakke eller Slettet post

   :::image type="content" source="../../media/advanced-hunting-take-actions-email.png" alt-text="Indstillingen Udfør handlinger på portalen Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email.png":::

- `Delete email` - vælg denne indstilling for at flytte mails til mappen Slettet post (**blød sletning**) eller slette dem permanent (**hård sletning**)

   :::image type="content" source="../../media/advanced-hunting-take-actions-email-del.png" alt-text="Indstillingen Udfør handlinger på portalen Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email-del.png":::

Du kan også angive et afhjælpningsnavn og en kort beskrivelse af den handling, der udføres for nemt at spore den i handlingscenterets historik. Du kan også bruge godkendelses-id'et til at filtrere efter disse handlinger i Løsningscenter. Dette id er angivet i slutningen af guiden:

:::image type="content" source="../../media/choose-email-actions-entities.png" alt-text="guiden Udfør handlinger, der viser vælg handlinger for objekter" lightbox="../../media/choose-email-actions-entities.png":::

Disse mailhandlinger gælder også for [brugerdefinerede registreringer](custom-detections-overview.md) .


## <a name="review-actions-taken"></a>Gennemse udførte handlinger
Hver handling registreres individuelt i [Handlingscenter](m365d-action-center.md) under **Action** **centerHistory** >  ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). Gå til Løsningscenter for at kontrollere status for hver handling.
 
>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender for Endpoint. [Slå Microsoft 365 Defender](m365d-enable.md) til for at jagte trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser for jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i [Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Oversigt over Handlingscenter](m365d-action-center.md)
