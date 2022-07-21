---
title: Kom i gang med Aktivitetsoversigt
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Med Aktivitetsoversigt kan du se og filtrere på de handlinger, som brugerne foretager på dit navngivne indhold.
ms.openlocfilehash: c33ff2653eef6813caf9b9281903b7248af12359
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917996"
---
# <a name="get-started-with-activity-explorer"></a>Kom i gang med aktivitetsviser

Oversigt [over dataklassificering](data-classification-overview.md) og faner i [Indholdsoversigt giver](data-classification-content-explorer.md) dig indblik i, hvilket indhold der er blevet fundet og mærket, og hvor indholdet er. Aktivitetsoversigt runder denne pakke af funktioner ud ved at give dig mulighed for at overvåge, hvad der sker med dit navngivne indhold. Aktivitetsoversigt giver en oversigt over aktiviteter på dit mærkede indhold. Aktivitetsoplysningerne indsamles fra Microsoft 365 Unified Audit Logs, transformeres og gøres tilgængelige i brugergrænsefladen i Aktivitetsoversigt. Aktivitetsoversigt rapporterer om data for op til 30 dage.

![pladsholderskærmbillede oversigt over aktivitetsoversigt.](../media/data-classification-activity-explorer-1.png)

Der er over 30 forskellige filtre tilgængelige til brug. Nogle er:

- Datointerval
- Aktivitetstype
- Placering
- Bruger
- Følsomhedsmærkat
- Opbevaringsmærkat
- Filsti
- DLP-politik



## <a name="prerequisites"></a>Forudsætninger

Alle konti, der tilgår og bruger dataklassificering, skal have en licens tildelt fra et af disse abonnementer:

- Microsoft 365 (E5)
- Office 365 (E5)
- Tilføjelsesprogrammet Avanceret overholdelse (E5)
- Tilføjelsesprogrammet Advanced Threat Intelligence (E5)
- Microsoft 365 E5/A5 Info Protection & Styring
- overholdelse af Microsoft 365 E5/A5

### <a name="permissions"></a>Tilladelser

En konto skal udtrykkeligt tildeles medlemskab i en af disse rollegrupper eller tildeles rollen eksplicit.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper i prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide om under [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365-rollegrupper**

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Administrator af overholdelsesdata

**Microsoft 365-roller**

- Overholdelsesadministrator
- Sikkerhedsadministrator
- Sikkerhedslæser

## <a name="activity-types"></a>Aktivitetstyper

Aktivitetsoversigt indsamler aktivitetsoplysninger fra overvågningslogge på flere kilder til aktiviteter. Du kan finde flere detaljerede oplysninger om, hvilken mærkataktivitet der gør den til [Aktivitetsoversigt, under Mærkathændelser, der er tilgængelige i Aktivitetsoversigt](data-classification-activity-explorer-available-events.md).

**Aktiviteter med følsomhedsmærkater** og **aktiviteter til opbevaringsmærkning** fra oprindelige Office-programmer, Azure Information Protection (AIP) samlet mærkatklient og -scanner, SharePoint Online, Exchange Online (kun følsomhedsmærkater) og OneDrive. Nogle eksempler er:

- Anvendt navn
- Navnet er ændret (opgraderet, nedgraderet eller fjernet)
- Simulering af automatisk navngivning
- Fillæsning

**AIP-scanner- og AIP-klienter (Azure Information Protection)**

- Beskyttelse anvendt
- Beskyttelsen er ændret
- Beskyttelse fjernet
- Registrerede filer

Aktivitetsoversigt indsamler også **DLP-politikforekomster** fra Exchange Online, SharePoint Online, OneDrive, Teams Chat og kanal (prøveversion), SharePoint-mapper og -biblioteker i det lokale miljø og filshares i det lokale miljø og Windows 10 enheder via **DLP (Forebyggelse af datatab i Slutpunkt).** Nogle eksempler på hændelser fra Windows 10 enheder er fil:

- Sletninger
- Kreationer
- Kopieret til Udklipsholder
- Ændret
- Læse
- Udskrives
- Omdøbt
- Kopieret til netværksshare
- Tilgået af ikke-tilladt app 

Hvis du forstår, hvilke handlinger der udføres med dit følsomme mærkatindhold, kan du se, om de kontrolelementer, du har på plads, f.eks. [Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md) politikker, er effektive eller ej. Hvis det ikke er muligt, eller hvis du opdager noget uventet, f.eks. et stort antal elementer, der er mærket `highly confidential` og nedgraderes `general`, kan du administrere dine forskellige politikker og udføre nye handlinger for at begrænse den uønskede funktionsmåde.

> [!NOTE]
> Aktivitetsoversigt overvåger i øjeblikket ikke opbevaringsaktiviteter for Exchange Online.

## <a name="see-also"></a>Se også

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)
- [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md)
- [Om klassificering af data](data-classification-overview.md)
