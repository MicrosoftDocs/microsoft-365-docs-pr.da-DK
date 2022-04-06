---
title: Konfigurer dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø
description: Access Microsoft 365 Defender portal, og konfigurer derefter dit Microsoft 365 Defender prøvelaboratormiljø
keywords: Microsoft 365 Defender prøveversionskonfiguration Microsoft 365 Defender prøvekonfigurationen, prøve Microsoft 365 Defender Microsoft 365 Defender konfiguration af evalueringslaboratorium
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 681d9798c6f16f5829bdb4e5272abc3eac719a59
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500975"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Konfigurer din Microsoft 365 Defender i et labmiljø 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender 

Dette emne guider dig til at konfigurere et dedikeret laboratoriemiljø. Du kan finde oplysninger om konfiguration af en prøveversion i produktion i den nye [vejledning Evaluer Microsoft 365 Defender](eval-overview.md) pilotversionen. 

## <a name="create-an-office-365-e5-trial-tenant"></a>Opret en Office 365 E5 prøveversionslejer
>[!NOTE]
>Hvis du allerede har et eksisterende Office 365 eller Azure Active Directory abonnement, kan du springe de Office 365 E5 med prøveversionens lejeroprettelsestrin over.

1. Gå til Office 365 E5 [, og](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) vælg **Gratis prøveversion**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Siden Office 365 E5 gratis prøveversion" lightbox="../../media/mtp-eval-9.png":::
  
2. Fuldfør registrering af prøveversionen ved at angive din mailadresse (personlig eller virksomhed). Klik **på Konfigurer konto**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Siden Office 365 E5 konfiguration af prøveabonnement" lightbox="../../media/mtp-eval-10.png":::

3. Udfyld dit fornavn, efternavn, virksomhedens telefonnummer, firmanavn, virksomhedens størrelse og land eller område.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Siden Office 365 E5 konfiguration af prøveversion, der beder om navn, telefon og firmaoplysninger" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Det land eller område, du angiver her, bestemmer, hvilket datacenterområde Office 365 skal hostes.
  
4. Vælg din bekræftelsesindstilling: via en sms eller et opkald. Klik **på Send bekræftelseskode**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Siden Office 365 E5 konfiguration af prøveversionen, hvor du bliver bedt om at bekræfte" lightbox="../../media/mtp-eval-12.png":::

5. Angiv det brugerdefinerede domænenavn for din lejer, og klik derefter på **Næste**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Siden Office 365 E5 konfiguration af prøveversionen, hvor du kan konfigurere dit brugerdefinerede domænenavn" lightbox="../../media/mtp-eval-13.png":::
 
6. Konfigurer den første identitet, som skal være global administrator for lejeren. Udfyld **Navn og** **Adgangskode**. Klik **på Tilmeld dig**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Siden Office 365 E5 registrering af prøveversion, hvor du kan angive din virksomhedsidentitet" lightbox="../../media/mtp-eval-14.png":::

7. Klik **på Gå til konfiguration** for at fuldføre Office 365 E5 prøveversionens lejer klargøring.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="Siden Office 365 E5 konfiguration af prøveregistrering, hvor du bliver bedt om at klikke på knappen Gå til konfiguration" lightbox="../../media/mtp-eval-15.png":::

8. Forbind virksomhedens domæne til Office 365 lejer. [Valgfrit] Vælg **Forbind domæne, du allerede ejer**, og skriv dit domænenavn. Klik på **Næste**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Siden Office 365 E5 konfiguration, hvor du skal tilpasse dit logon og din mail" lightbox="../../media/mtp-eval-16.png":::
 
9. Tilføj en TXT- eller MX-post for at bekræfte ejerskabet af domænet. Når du har føjet TXT- eller MX-posten til dit domæne, skal du vælge **Bekræft**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Siden Office 365 E5 konfiguration, hvor du skal tilføje en TXT af MX-post for at bekræfte dit domæne" lightbox="../../media/mtp-eval-17.png":::
 
10. [Valgfrit] Opret flere brugerkonti til din lejer. Du kan springe dette trin over ved at klikke på **Næste**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Siden Office 365 E5 konfiguration, hvor du kan tilføje flere brugere" lightbox="../../media/mtp-eval-18.png":::
 
11. [Valgfrit] Download Office apps. Klik **på Næste** for at springe dette trin over. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Den Office 365 E5 side, hvor du kan installere dine Office apps" lightbox="../../media/mtp-eval-19.png":::

12. [Valgfrit] Overfør mails. Du kan også springe dette trin over.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Den Office 365 E5 hvor du kan angive, om du vil overføre mails eller ej" lightbox="../../media/mtp-eval-20.png":::
 
13. Vælg onlinetjenester. Vælg **Exchange,** og klik på **Næste**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Det Office 365 E5, hvor du kan vælge din onlinetjenester" lightbox="../../media/mtp-eval-21.png":::

14. Føj MX-, CNAME- og TXT-poster til dit domæne. Vælg Bekræft, når du **er færdig**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="Den Office 365 E5 her, kan du tilføje dine DNS-poster" lightbox="../../media/mtp-eval-22.png":::
 
15. Tillykke, du har færdiggjort klargøring af din Office 365 lejer.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Bekræftelsessiden Office 365 E5 fuldførelse af konfiguration" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Aktivér Microsoft 365 prøveabonnement

>[!NOTE]
>Når du tilmelder dig en prøveversion, får du 25 brugerlicenser til brug i en måned. Se [Prøv eller køb et Microsoft 365 for at få](../../commerce/try-or-buy-microsoft-365.md) flere oplysninger.

1. Fra [Microsoft 365 Administration skal du](https://admin.microsoft.com/) klikke på **Fakturering** og derefter gå til **Køb tjenester**.

2. Vælg **Microsoft 365 E5,** og klik **på Start gratis prøveversion**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion" lightbox="../../media/mtp-eval-24.png":::

3. Vælg din bekræftelsesindstilling: via en sms eller et opkald. Når du har besluttet dig, skal du angive telefonnummeret og vælge **Sms mig** eller **Ring til mig** afhængigt af dit valg.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Siden Microsoft 365 E5 start gratis prøveversion, der beder om kontaktoplysninger til at sende kode for at bevise, at du ikke er en robot" lightbox="../../media/mtp-eval-25.png":::
 
4. Angiv bekræftelseskoden, og klik **på Start din gratis prøveversion**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion, hvor du kan udfylde bekræftelseskoden, som systemet har sendt for at bevise, at du ikke er en robot" lightbox="../../media/mtp-eval-26.png":::

5. Klik **på Prøv nu** for at bekræfte Microsoft 365 E5 prøveversionen.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion, hvor du skal se knappen Prøv nu for at starte" lightbox="../../media/mtp-eval-27.png":::
 
6. Gå til **Microsoft 365 Administration** **CenterUsersActive-brugere** >  > . Vælg din brugerkonto, vælg **Administrer produktlicenser**, og byt derefter licensen fra Office 365 E5 til **Microsoft 365 E5**. Klik på **Gem**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan vælge Microsoft 365 E5 licens" lightbox="../../media/mtp-eval-28.png":::
 
7. Vælg den globale administratorkonto igen, og klik derefter **på Administrer brugernavn**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan vælge Konto og Administrer brugernavn" lightbox="../../media/mtp-eval-29.png":::

8. [Valgfrit] Skift domænet fra *onmicrosoft.com* dit eget domæne – afhængigt af hvad du valgte i de forrige trin. Klik på **Gem ændringer**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan ændre din domæneindstilling" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Næste trin
|[Fase 3: Konfigurer & onboard](config-m365d-eval.md) | Konfigurer hver Microsoft 365 Defender søjle til dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø, og onboard dine slutpunkter.
|:-------|:-----|
