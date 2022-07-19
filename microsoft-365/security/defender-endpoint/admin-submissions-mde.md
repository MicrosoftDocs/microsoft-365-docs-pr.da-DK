---
title: Send filer i Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du bruger funktionen Samlede indsendelser i Microsoft 365 Defender til at sende mistænkelige mails, URL-adresser, vedhæftede filer i mails og filer til Microsoft til scanning.
keywords: antivirus, spam, phish, fil, besked, Microsoft Defender for Endpoint, falsk positiv, falsk negativ, blokeret fil, blokeret URL-adresse, indsendelse, indsende, rapport
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.date: 06/15/2021
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
manager: dansimp
localization_priority: Normal
audience: ITPro
ms.topic: how-to
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: FPFN
ms.openlocfilehash: 0d445050ea667d54b8a73eb2f040c8114e1dfcfb
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858907"
---
# <a name="submit-files-in-microsoft-defender-for-endpoint"></a>Send filer i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146806)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-usewdatp-abovefoldlink).

I Microsoft Defender for Endpoint kan administratorer bruge funktionen Samlede indsendelser til at sende filer og filhashes til Microsoft til gennemsyn. Den samlede indsendelsesoplevelse er en one-stop-shop til indsendelse af mails, URL-adresser, vedhæftede filer i mails og filer i én og nem indsendelsesoplevelse. Administratorer kan bruge Microsoft 365 Defender-portalen eller siden med Microsoft Defender for Endpoint besked til at sende mistænkelige filer.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Den nye samlede indsendelsesoplevelse er kun tilgængelig i abonnementer, der omfatter Microsoft 365 Defender, Microsoft Defender for Endpoint Plan 2 eller Microsoft Defender for Office Plan 2.

- Hvis du vil sende filer til Microsoft, skal du være medlem af en af følgende rollegrupper:

  - **Organisationsadministration**, **Sikkerhedsadministrator** eller **Sikkerhedslæser** på [portalen Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-security-center.md).

- Du kan få flere oplysninger om, hvordan du sender spam, phish, URL-adresser og vedhæftede filer i mails til Microsoft, under [Rapportér meddelelser og filer til Microsoft](../office-365-security/report-junk-email-messages-to-microsoft.md).

## <a name="report-items-to-microsoft-from-the-portal"></a>Rapportér elementer til Microsoft fra portalen

Hvis du har en fil, som du har mistanke om kan være malware eller er ved at blive registreret forkert (falsk positiv), kan du sende den til Microsoft til analyse ved hjælp af Microsoft 365 Defender-portalen på https://security.microsoft.com/.

### <a name="submit-a-file-or-file-hash"></a>Send en fil eller en filhash

1. Åbn Microsoft 365 Defender på <https://security.microsoft.com/>, klik på **Handlinger & afsendelser**, klik på **Afsendelser**, gå til fanen **Filer**, og vælg derefter **Tilføj ny indsendelse**.

    > [!div class="mx-imgBorder"]
    > ![Tilføj ny indsendelse](../../media/unified-admin-submission-new.png)

2. Brug pop op-vinduet **Send elementer til Microsoft til gennemsyn** , der ser ud til at sende **hashværdien Fil** eller **Fil**.

3. I feltet **Vælg indsendelsestype** skal du vælge **Fil** eller **Filhash** på rullelisten.

4. Klik på **Gennemse filer**, når du sender en fil. Find og vælg filen i den dialogboks, der åbnes, og klik derefter på **Åbn**. Bemærk, at for indsendelser af **filhash** skal du enten kopiere eller skrive filhash.

5. I afsnittet **Denne fil skal være kategoriseret som** skal du vælge enten **Malware** (falsk negativ) eller **Uønsket software** eller **Ren** (falsk positiv).

6. **Vælg derefter prioriteten**. Bemærk, at for **indsendelser af filhash** er **Low – masseindsendelse af filer eller filhashindsendelse** det eneste valg og vælges automatisk.

    > [!div class="mx-imgBorder"]
    > ![Send elementer til Microsoft til gennemsyn](../../media/unified-admin-submission-file.png)

7. Klik på **Send**.

   Hvis du vil have vist oplysningerne om din indsendelse, skal du vælge din indsendelse på listen **Navn på indsendelser** for at åbne pop op-vinduet **Resultatoplysninger** .

## <a name="report-items-to-microsoft-from-the-alerts-page"></a>Rapportér elementer til Microsoft fra siden Beskeder

Du kan også sende en fil- eller filhash direkte fra listen over beskeder på siden **Beskeder** .

1. Åbn Microsoft 365 Defender på <https://security.microsoft.com/>, klik på **Hændelser & beskeder**, og klik derefter på **Beskeder** for at få vist listen over beskeder.

2. Vælg den besked, du vil rapportere. Bemærk, at du sender en fil, der er indlejret i beskeden.

3. Klik på ellipsen ud for **Administrer besked** for at se flere indstillinger. Vælg **Send elementer til Microsoft til gennemsyn**.

    > [!div class="mx-imgBorder"]
    > ![Send elementer fra beskedkøen](../../media/unified-admin-submission-alerts-queue.png)

4. Vælg indsendelsestypen i det næste pop op-vindue, der åbnes.

    > [!div class="mx-imgBorder"]
    > ![Udfyld de påkrævede felter](../../media/unified-admin-submission-alert-queue-flyout.png)

    Hvis du vælger **Fil** som indsendelsestype, skal du uploade filen, kategorisere din indsendelse og vælge prioriteten.

    Hvis du vælger **Filhash** som indsendelsestype, skal du vælge de filhashværdier, der er tilgængelige på rullelisten. Du kan vælge flere filhashes.

5. Klik på **Send**.

## <a name="related-information"></a>Relaterede oplysninger

- [Microsoft Defender for Endpoint i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md)
- [Adresse falske positiver/negativer](defender-endpoint-false-positives-negatives.md)
- [Få vist og organiser beskedkøen i Microsoft Defender for Endpoint](alerts-queue.md)
