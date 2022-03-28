---
title: Tilgængelighedstilstand i SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du bruger tilgængelighedsfunktioner, når du træner og arbejder med SharePoint Syntex.
ms.openlocfilehash: 09fd16259a44a2aa4d1b82dca49fffa76065690b
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63597452"
---
# <a name="accessibility-mode-in-sharepoint-syntex"></a>Tilgængelighedstilstand i SharePoint Syntex

I [SharePoint Syntex](index.md) kan brugerne slå Tilgængelighedstilstand til i alle faser af modelkursus (etiket, træn, test), når de arbejder med eksempeldokumenter. Brug af tilgængelighedstilstand kan hjælpe svagtseende brugere med at have nemmere tilgængelighed ved hjælp af tastaturet, når de navigerer og navn nemer elementer i dokumentvisningen.

Dette hjælper brugerne med at bruge deres tastaturer til at navigere gennem teksten i dokumentvisningen og til at høre indtaling af ikke blot de valgte værdier, men også handlinger (f.eks. mærkning eller fjernelse af mærkning fra markeret tekst) eller forudsagte etiketværdier, når du oplære modellen med yderligere eksempeldokumenter. 


![Tilgængelighedstilstand.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Krav

Hvis du vil høre lyden fra indtalingerne, skal du sørge for [](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) at aktivere Oplæser-appen i indstillingerne for Oplæser på Windows 10 systemet.

![Slå Oplæser til.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Mærkning for tastaturbrugere

For tastaturbrugere, der bruger tilgængelighedstilstand, kan du bruge følgende taster, hvis du mærker tekst i et eksempeldokument i fremviseren:

- Fane: Flytter dig fremad og markerer det næste ord.
- Tab+Skift: Flytter dig tilbage og markerer det forrige ord.
- Enter: Etiket eller fjerner et navn fra det markerede ord.
- Højre pil: Flytter dig fremad gennem individuelle tegn i et markeret ord.
- Venstre pil: Flytter dig tilbage gennem individuelle tegn i et markeret ord.

> [!NOTE]
> Hvis du mærker flere ord for en enkelt etiket, skal du markere hvert ord.


## <a name="narration"></a>Indtaling

For Brugere af Oplæser, der bruger tilgængelighedstilstand, skal du bruge den samme tastaturnavigation, der er beskrevet for tastaturbrugere, til at gennemgå eksempeldokumentet i fremviseren.

Når du navigerer gennem eksempeldokumenterne og værdierne for navnestrenge, giver Oplæser brugeren følgende lydprompter:

- Når du bruger tastaturet til at navigere gennem dokumentvisningen, viser Oplæser-lyd den valgte streng.
- I en markeret streng angiver lyd for Oplæser hvert tegn i strengen, når du markerer dem ved hjælp af venstre eller højre piletast.
- Hvis du vælger en streng, der er mærket, vil Oplæser angive værdien og derefter "mærket".  Hvis etiketværdien f.eks. er "Contoso", angives "Costoso mærket". 
- Hvis du under fanen Kursus vælger en streng i dokumentvisningen, som kun er blevet forudsagt, vil oplæserlyd angive værdien og derefter "forudsagt". Dette sker, når uddannelse forudsiger en værdi i filen, der ikke svarer til det, der er blevet navngivet af brugeren.
- Hvis du på fanen Kursus vælger en streng i dokumentvisningen, der er mærket og forudsagt, vil Oplæser-lyd angive værdien og derefter "mærket og forudsagt". Dette sker, når kurserne lykkes, og der findes et match mellem en forudsagt værdi og brugernavnet.

Når en streng er mærket, eller et navn er blevet fjernet i fremviseren, advarer Oplæser-lyd dig om at gemme ændringerne, før du afslutter.

## <a name="see-also"></a>Se også

[Opret en extractor](create-an-extractor.md)

[Opret en klassificering](create-a-classifier.md)










 


  
  



