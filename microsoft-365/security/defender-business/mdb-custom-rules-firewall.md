---
title: Administrer brugerdefinerede regler for firewallpolitikker i Microsoft Defender til virksomheder
description: Brugerdefinerede regler indeholder undtagelser fra firewallpolitikker. Du kan bruge brugerdefinerede regler til at blokere eller tillade bestemte forbindelser i Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: ae409f1196b01b774d9e73d45d16868bff1c904b
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861702"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>Administrer dine brugerdefinerede regler for firewallpolitikker i Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 


Microsoft Defender til virksomheder indeholder firewallpolitikker, der hjælper med at beskytte dine enheder mod uønsket netværkstrafik. Du kan bruge brugerdefinerede regler til at definere undtagelser for firewallpolitikker. Du kan f.eks. bruge brugerdefinerede regler til at blokere eller tillade bestemte forbindelser.

Du kan få mere at vide om firewallpolitikker og -indstillinger [under Firewall i Microsoft Defender til virksomheder](mdb-firewall.md).

**I denne artikel beskrives det, hvordan du**:

- [Opret en brugerdefineret regel for en firewallpolitik](#create-a-custom-rule-for-a-firewall-policy)
- [Rediger en brugerdefineret regel for en firewallpolitik](#edit-a-custom-rule-for-a-firewall-policy)
- [Slet en brugerdefineret regel](#delete-a-custom-rule)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Opret en brugerdefineret regel for en firewallpolitik

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **konfigurationen EndpointsDevice** > , og gennemse listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemse indstillingerne i trinnet **Konfigurationsindstillinger** . Foretag de nødvendige ændringer af **domænenetværket**, **det offentlige netværk** og **det private netværk**.

5. Følg disse trin for at oprette en brugerdefineret regel: 

   1. Under **Brugerdefinerede regler** skal du vælge **+ Tilføj regel**. Du kan have op til 150 brugerdefinerede regler.
   2. I pop op-vinduet **Opret ny regel** skal du angive et navn og en beskrivelse af reglen.
   3. Vælg en profil. Dine muligheder omfatter **Domænenetværk**, **Offentligt netværk** eller **Privat netværk**.
   4. Vælg enten **IP-** eller **Programfilsti på** listen **Fjernadressetype**.
   5. Angiv en passende værdi i feltet **Værdi** . Afhængigt af hvad du valgte i trin 6d, kan du angive en IP-adresse, et IP-adresseinterval eller en programfilsti. (Se [Firewallindstillinger](mdb-firewall.md)).
   6. I pop op-vinduet **Opret ny regel** skal du vælge **Opret regel**. 

6. På skærmen **Konfigurationsindstillinger** skal du vælge **Næste**.

7. Gennemse de ændringer, der er foretaget af **firewallpolitikindstillingerne, på skærmen Gennemse din politik** . Foretag de nødvendige ændringer, og vælg derefter **Opret politik**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Rediger en brugerdefineret regel for en firewallpolitik

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **konfigurationen EndpointsDevice** > , og gennemse listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemse listen over **regler under Brugerdefinerede regler**.

5. Vælg en regel, og vælg derefter **Rediger**. Dens pop op-vindue åbnes.

6. Hvis du vil redigere din brugerdefinerede regel, skal du følge disse trin:

   1. Gennemse og rediger reglens navn og beskrivelse i pop op-vinduet **Rediger regel** .
   2. Gennemse og rediger eventuelt reglens profil. Dine muligheder omfatter **Domænenetværk**, **Offentligt netværk** eller **Privat netværk**.
   3. Vælg enten **IP-** eller **Programfilsti på** listen **Fjernadressetype**.
   4. Angiv en passende værdi i feltet **Værdi** . Afhængigt af hvad du valgte i trin 6c, kan du angive en IP-adresse, et IP-adresseinterval eller en programfilsti. (Se [Firewallindstillinger](mdb-firewall.md)).
   5. Angiv **Aktivér regel** til **Til** for at aktivere reglen. Du kan også deaktivere reglen ved at angive parameteren til **Fra**.
   6. Vælg **Opdater regel** i pop op-vinduet **Rediger regel**. 

7. På skærmen **Konfigurationsindstillinger** skal du vælge **Næste**.

8. Gennemse de ændringer, der er foretaget af **firewallpolitikindstillingerne, på skærmen Gennemse din politik** . Foretag de nødvendige ændringer, og vælg derefter **Opret politik**.

## <a name="delete-a-custom-rule"></a>Slet en brugerdefineret regel

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **konfigurationen EndpointsDevice** > , og gennemse listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemse listen over **regler under Brugerdefinerede regler**.

5. Vælg en regel, og vælg derefter **Slet**. Dens pop op-vindue åbnes.

6. Vælg **Slet** på bekræftelsesskærmen. 

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)