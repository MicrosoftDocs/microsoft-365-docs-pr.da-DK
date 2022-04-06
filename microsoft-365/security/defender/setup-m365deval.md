---
title: Konfigurer dit Microsoft 365 Defender prøvelaboratorium eller et pilotmiljø
description: Få adgang Microsoft 365 Defender portal, og konfigurer derefter dit Microsoft 365 Defender prøveversionslaboratorium
keywords: Microsoft 365 Defender installation af prøveversion, Microsoft 365 Defender pilotinstallation, kan du prøve Microsoft 365 Defender Microsoft 365 Defender konfiguration af evalueringslaboratorium
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
ms.openlocfilehash: 5d516a7062d8c6f617cee2a260f27ee896689f2c
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667334"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Konfigurer din Microsoft 365 Defender prøveversion i et laboratoriemiljø 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender 

I dette emne får du hjælp til at konfigurere et dedikeret laboratoriemiljø. Du kan finde oplysninger om, hvordan du konfigurerer en prøveversion i produktion, i den nye vejledning [til evaluering og pilot Microsoft 365 Defender](eval-overview.md). 

## <a name="create-an-office-365-e5-trial-tenant"></a>Opret en Office 365 E5 prøveversionslejer
>[!NOTE]
>Hvis du allerede har et eksisterende Office 365- eller Azure Active Directory-abonnement, kan du springe Office 365 E5 lejeroprettelsestrin over.

1. Gå til [Office 365 E5 produktportal,](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) og vælg **Gratis prøveversion**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Siden med Office 365 E5 gratis prøveversion" lightbox="../../media/mtp-eval-9.png":::
  
2. Fuldfør registreringen af prøveversionen ved at angive din mailadresse (personlig eller firma). Klik på **Konfigurer konto**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Siden til konfiguration af Office 365 E5 prøveversion" lightbox="../../media/mtp-eval-10.png":::

3. Udfyld dit fornavn, efternavn, firmatelefonnummer, firmanavn, firmastørrelse og land eller område.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Siden til konfiguration af Office 365 E5 prøveregistrering, hvor du bliver bedt om oplysninger om navn, telefon og firma" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Det land eller område, du angiver her, bestemmer det datacenterområde, som din Office 365 hostes for.
  
4. Vælg dine kontrolindstillinger: via en sms eller et opkald. Klik på **Send bekræftelseskode**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Siden til konfiguration af Office 365 E5 prøveregistrering, hvor du bliver bedt om bekræftelsespræference" lightbox="../../media/mtp-eval-12.png":::

5. Angiv det brugerdefinerede domænenavn for din lejer, og klik derefter på **Næste**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Siden til konfiguration af Office 365 E5 prøveversion, hvor du kan konfigurere dit brugerdefinerede domænenavn" lightbox="../../media/mtp-eval-13.png":::
 
6. Konfigurer den første identitet, som skal være global administrator for lejeren. Udfyld **Navn** og **Adgangskode**. Klik på **Tilmeld dig**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Siden til konfiguration af Office 365 E5 prøveregistrering, hvor du kan angive din virksomhedsidentitet" lightbox="../../media/mtp-eval-14.png":::

7. Klik på **Gå til installationsprogrammet** for at fuldføre klargøringen af Office 365 E5 prøveversion af lejeren.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="Siden til konfiguration af Office 365 E5 prøveversion, hvor du bliver bedt om at klikke på Knappen Gå til installation" lightbox="../../media/mtp-eval-15.png":::

8. Forbind dit virksomhedsdomæne til den Office 365 lejer. [Valgfri] Vælg **Forbind et domæne, du allerede ejer**, og skriv dit domænenavn. Klik på **Næste**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Siden Office 365 E5 konfiguration, hvor du skal tilpasse dit logon og din mail" lightbox="../../media/mtp-eval-16.png":::
 
9. Tilføj en TXT- eller MX-post for at validere ejerskabet af domænet. Når du har føjet TXT- eller MX-posten til dit domæne, skal du vælge **Bekræft**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Siden Office 365 E5 konfiguration, hvor du skal tilføje en TXT af MX-post for at bekræfte dit domæne" lightbox="../../media/mtp-eval-17.png":::
 
10. [Valgfri] Opret flere brugerkonti til din lejer. Du kan springe dette trin over ved at klikke på **Næste**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Siden Office 365 E5 konfiguration, hvor du kan tilføje flere brugere" lightbox="../../media/mtp-eval-18.png":::
 
11. [Valgfri] Download Office apps. Klik på **Næste** for at springe dette trin over. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Den Office 365 E5 side, hvor du kan installere dine Office apps" lightbox="../../media/mtp-eval-19.png":::

12. [Valgfri] Overfør mailmeddelelser. Igen kan du springe dette trin over.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Den Office 365 E5, hvor du kan angive, om du vil overføre mails eller ej" lightbox="../../media/mtp-eval-20.png":::
 
13. Vælg onlinetjenester. Vælg **Exchange**, og klik på **Næste**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Det Office 365 E5, hvor du kan vælge dine onlinetjenester" lightbox="../../media/mtp-eval-21.png":::

14. Føj poster af typen MX, CNAME og TXT til dit domæne. Når du er færdig, skal du vælge **Bekræft**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="Office 365 E5 her kan du tilføje dine DNS-poster" lightbox="../../media/mtp-eval-22.png":::
 
15. Tillykke, du har fuldført klargøringen af din Office 365 lejer.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Bekræftelsessiden for fuldførelse af Office 365 E5 konfiguration" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Aktivér Microsoft 365 prøveabonnement

>[!NOTE]
>Når du tilmelder dig en prøveversion, får du 25 brugerlicenser, du kan bruge i en måned. Se [Prøv eller køb et Microsoft 365-abonnement](../../commerce/try-or-buy-microsoft-365.md) for at få flere oplysninger.

1. Klik [på Fakturering fra Microsoft 365 Administration Center](https://admin.microsoft.com/), og  naviger derefter til **Køb tjenester**.

2. Vælg **Microsoft 365 E5**, og klik på **Start gratis prøveversion**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion" lightbox="../../media/mtp-eval-24.png":::

3. Vælg dine kontrolindstillinger: via en sms eller et opkald. Når du har besluttet dig, skal du angive telefonnummeret, vælge **Tekst mig** eller **Ring til mig** afhængigt af dit valg.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion, hvor du bliver bedt om kontaktoplysninger for at sende kode for at bevise, at du ikke er en robot" lightbox="../../media/mtp-eval-25.png":::
 
4. Angiv bekræftelseskoden, og klik på **Start din gratis prøveversion**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion, hvor du kan udfylde bekræftelseskoden, som systemet har sendt for at bevise, at du ikke er en robot" lightbox="../../media/mtp-eval-26.png":::

5. Klik på **Prøv nu** for at bekræfte din Microsoft 365 E5 prøveversion.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="Siden Microsoft 365 E5 Start gratis prøveversion, hvor du skal bruge knappen Prøv nu for at starte" lightbox="../../media/mtp-eval-27.png":::
 
6. Gå til **Microsoft 365 Administration** **CenterUsersActive-brugere** >  > . Vælg din brugerkonto, vælg **Administrer produktlicenser**, og byt derefter licensen fra Office 365 E5 til **Microsoft 365 E5**. Klik på **Gem**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan vælge den Microsoft 365 E5 licens" lightbox="../../media/mtp-eval-28.png":::
 
7. Vælg den globale administratorkonto igen, og klik derefter på **Administrer brugernavn**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan vælge Konto og Administrer brugernavn" lightbox="../../media/mtp-eval-29.png":::

8. [Valgfri] Skift domænet fra *onmicrosoft.com* til dit eget domæne – afhængigt af hvad du valgte i de forrige trin. Klik på **Gem ændringer**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Siden Microsoft 365 Administration Center, hvor du kan ændre dine domæneindstillinger" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Næste trin
|[Fase 3: Konfigurer & onboard](config-m365d-eval.md) | Konfigurer hver Microsoft 365 Defender søjle for dit Microsoft 365 Defender prøvelaboratorium eller pilotmiljø, og onboarder dine slutpunkter.
|:-------|:-----|
