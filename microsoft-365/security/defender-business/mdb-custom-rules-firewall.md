---
title: Administrer brugerdefinerede regler for firewallpolitikker i Microsoft Defender for Business
description: Brugerdefinerede regler giver undtagelser til firewallpolitikker. Du kan bruge brugerdefinerede regler til at blokere eller tillade bestemte forbindelser i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 161ce8a20500bdea7d2ccd2dd9cc8a387345de1c
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594700"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>Administrer dine brugerdefinerede regler for firewallpolitikker i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 


Microsoft Defender for Business omfatter firewallpolitikker, der beskytter dine enheder mod uønsket netværkstrafik. Du kan bruge brugerdefinerede regler til at definere undtagelser for politikker for din firewall. Det vil sige, at du kan bruge brugerdefinerede regler til at blokere eller tillade bestemte forbindelser.

Hvis du vil have mere at vide om politikker og indstillinger for firewall, [skal du se Firewall i Microsoft Defender for Business](mdb-firewall.md).

**I denne artikel beskrives det, hvordan** du:

- [Oprette en brugerdefineret regel for en firewallpolitik](#create-a-custom-rule-for-a-firewall-policy)
- [Rediger en brugerdefineret regel for en firewallpolitik](#edit-a-custom-rule-for-a-firewall-policy)
- [Slette en brugerdefineret regel](#delete-a-custom-rule)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Oprette en brugerdefineret regel for en firewallpolitik

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Konfiguration af** **SlutpunkterEnhed** > , og gennemgå listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemgå **indstillingerne på** trinnet Konfigurationsindstillinger. Foretag eventuelle nødvendige ændringer **i Domænenetværk**, **Offentligt netværk** og **Privat netværk**.

5. Hvis du vil oprette en brugerdefineret regel, skal du følge disse trin: 

   1. Under **Brugerdefinerede regler** skal du **vælge + Tilføj regel**. Du kan have op til 150 brugerdefinerede regler.
   2. På pop **op-siden Opret** ny regel skal du angive et navn og en beskrivelse af reglen.
   3. Vælg en profil. (Dine muligheder omfatter **Domænenetværk**, **Offentligt** netværk eller **Privat** netværk).
   4. Vælg enten **IP- eller Programfilsti** på  listen **Fjernadressetype**.
   5. Angiv **en** passende værdi i feltet Værdi. Afhængigt af hvad du valgte i trin 6d, kan du angive en IP-adresse, et IP-adresseområde eller en programfilsti. (Se [Firewall-indstillinger](mdb-firewall.md)).
   6. I pop **op-dialogboksen Opret** ny regel skal du **vælge Opret regel**. 

6. Vælg Næste **på skærmbilledet** **Konfigurationsindstillinger**.

7. På **skærmbilledet Gennemse din politik** skal du gennemse de ændringer, der er foretaget af politikindstillinger for firewall. Foretag eventuelle nødvendige ændringer, og vælg **derefter Opret politik**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Rediger en brugerdefineret regel for en firewallpolitik

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Konfiguration af** **SlutpunkterEnhed** > , og gennemgå listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemgå **listen over** regler under Brugerdefinerede regler.

5. Vælg en regel, og vælg derefter **Rediger**. Pop op-vindue åbnes.

6. Hvis du vil redigere den brugerdefinerede regel, skal du følge disse trin:

   1. I pop **op-menuen** Rediger regel skal du gennemse og redigere reglens navn og beskrivelse.
   2. Gennemse reglens profil, hvis det er nødvendigt. (Dine muligheder omfatter **Domænenetværk**, **Offentligt** netværk eller **Privat** netværk).
   3. Vælg enten **IP- eller Programfilsti** på  listen **Fjernadressetype**.
   4. Angiv **en** passende værdi i feltet Værdi. Afhængigt af hvad du valgte i trin 6c, kan du angive en IP-adresse, et IP-adresseområde eller en programfilsti. (Se [Firewall-indstillinger](mdb-firewall.md)).
   5. Angiv **Aktivér regel** **til Til** for at gøre reglen aktiv. Hvis du vil deaktivere reglen, skal du indstille indstillingen til **Fra**.
   6. I pop **op-menuen** Rediger regel skal du **vælge Opdater regel**. 

7. Vælg Næste **på skærmbilledet** **Konfigurationsindstillinger**.

8. På **skærmbilledet Gennemse din politik** skal du gennemse de ændringer, der er foretaget af politikindstillinger for firewall. Foretag eventuelle nødvendige ændringer, og vælg **derefter Opret politik**.

## <a name="delete-a-custom-rule"></a>Slette en brugerdefineret regel

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Konfiguration af** **SlutpunkterEnhed** > , og gennemgå listen over politikker.

3. I afsnittet **Firewall** skal du vælge en eksisterende politik eller tilføje en ny politik.

4. Gennemgå **listen over** regler under Brugerdefinerede regler.

5. Vælg en regel, og vælg derefter **Slet**. Pop op-vindue åbnes.

6. Vælg Slet på **bekræftelsesskærmbilledet**. 

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)