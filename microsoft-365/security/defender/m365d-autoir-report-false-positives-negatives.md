---
title: Adressere falske positive eller falske negativer i Microsoft 365 Defender
description: Blev noget overset eller fejlagtigt registreret af AIR i Microsoft 365 Defender? Få mere at vide om, hvordan du sender falske positive eller falske negativer til analyse hos Microsoft.
keywords: automatiseret, undersøgelse, advarsel, afhjælpning, falsk positiv, falsk negativ
search.appverid: met150
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 67246d7f7876457e6553818b469987a2b5a59eb0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592600"
---
# <a name="address-false-positives-or-false-negatives-in-microsoft-365-defender"></a>Adressere falske positive eller falske negativer i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Falske positive eller negativer kan indimellem forekomme med enhver trusselsbeskyttelsesløsning. Hvis [automatiseret undersøgelse og svarmuligheder](m365d-autoir.md) i Microsoft 365 Defender mistet eller fejlagtigt registreret noget, er der trin, som dit sikkerhedsteam kan udføre:

- [Rapportér en falsk positiv/negativ til Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [Juster dine beskeder](#adjust-an-alert-to-prevent-false-positives-from-recurring) (hvis det er nødvendigt)
- [Fortryd afhjælpningshandlinger, der er foretaget på enheder](#undo-a-remediation-action-that-was-taken-on-a-device)

I de følgende afsnit beskrives, hvordan du udfører disse opgaver.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Rapportér en falsk positiv/negativ til Microsoft til analyse

|Element overses eller registreres forkert |Tjeneste  |Hvad kan du gøre?  |
|---------|---------|---------|
|- Mail <br/>- Vedhæftet fil i en mail <br/>- URL-adresse i en mail<br/>- URL-adresse i Office fil      |[Microsoft Defender til Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)        |[Send mistænkeligt spam, phish, URL-adresser og filer til Microsoft til scanning](../office-365-security/admin-submission.md)         |
|Fil eller app på en enhed    |[Microsoft Defender til Slutpunkt](/windows/security/threat-protection)         |[Send en fil til Microsoft til malwareanalyse](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Justere en besked for at forhindre falske positive i at blive gentaget

|Scenarie |Tjeneste |Hvad kan du gøre? |
|--------|--------|--------|
|- En meddelelse udløses af lovlig anvendelse <br/>- En besked er unøjagtig    |[Microsoft Defender til skyapps](/cloud-app-security)<br/> eller <br/>[Azure-trusselsbeskyttelse](/azure/security/fundamentals/threat-detection)         |[Administrer beskeder i Defender for Cloud Apps-portalen](/cloud-app-security/managing-alerts)         |
|En fil, IP-adresse, URL-adresse eller domæne behandles som malware på en enhed, selvom den er sikker|[Microsoft Defender til Slutpunkt](/windows/security/threat-protection) |[Oprette en brugerdefineret indikator med en "Tillad"-handling](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Fortryde en afhjælpningshandling, der blev foretaget på en enhed

Hvis en afhjælpningshandling er blevet foretaget på en enhed (f.eks. en enhed eller en mail), og den pågældende enhed faktisk ikke er en trussel, kan dit sikkerhedsteam fortryde afhjælpningshandlingen i [Handlingscenter](m365d-action-center.md).

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på. 
2. Vælg Handlingscenter i **navigationsruden**. 
3. Vælg en **handling** , du vil fortryde, under fanen Oversigt. Pop op-ruden åbnes.
4. Vælg Fortryd i pop **op-ruden**.

> [!TIP]
> Se [Fortryde fuldførte handlinger](m365d-autoir-actions.md#undo-completed-actions).

## <a name="see-also"></a>Se også

- [Få vist detaljer og resultater af en automatisk undersøgelse](m365d-autoir-results.md)
- [Proaktivt på jagt efter trusler med avanceret jagt på Microsoft 365 Defender](advanced-hunting-overview.md)
