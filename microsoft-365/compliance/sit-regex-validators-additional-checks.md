---
title: Følsomme oplysningstype REGEX-validatorer og yderligere kontroller
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du bruger REGEX-validatorer og yderligere kontroller i dine eksisterende oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 615d4757be16b3171005105aea8148536e6f3015
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63607468"
---
# <a name="sensitive-information-type-regex-validators-and-additional-check"></a>Følsomme oplysningstype REGEX-validatorer og yderligere kontrol

> [!IMPORTANT]
> Microsofts kundeservicemedarbejdere & ikke hjælpe med at oprette brugerdefinerede klassificeringer eller regulære udtryksmønstre. Supportteknikere kan yde begrænset support til funktionen, f.eks. give eksempler på regulære udtryksmønstre til testformål eller hjælpe med at foretage fejlfinding af et eksisterende regulært udtryksmønster, der ikke udløser som forventet, men kan ikke give forsikringer om, at en tilpasset udvikling af indholdssammenholdelse opfylder dine krav eller forpligtelser.

## <a name="sensitive-information-type-regular-expression-validators"></a>Validatorer for regulære udtryk af typen Følsomme oplysninger

### <a name="checksum-validator"></a>Kontrolsums validator

Hvis du vil køre et kontrolsum på et ciffer i et regulært udtryk, kan du bruge *kontrolsum validatoren*. Lad os f.eks. sige, at du skal oprette et SIT for et ottecifret licensnummer, hvor det sidste ciffer er et kontrolsumcifre, der valideres ved hjælp af en mod 9-beregning. Du har konfigureret kontrolsumalgoritmen sådan her:

```console
Sum = digit 1 * Weight 1 + digit 2 * weight 2 + digit 3 * weight 3 + digit 4 * weight 4 + digit 5 * weight 5 + digit 6 * weight 6 + digit 7 * weight 7 + digit 8 * weight 8
Mod value = Sum % 9
If Mod value == digit 8
    Account number is valid
If Mod value != digit 8
    Account number is invalid
```

1. Definer det primære element med dette regulære udtryk:

   ```console
   \d{8}
   ```

2. Tilføj derefter kontrolsums validatoren.

3. Adder de tykkelsesværdier, der er adskilt med kommaer, checkcifrets position og værdien Mod. Du kan finde flere oplysninger om Modulo-handlingen [under Modulo-handling](https://en.wikipedia.org/wiki/Modulo_operation).

   > [!NOTE]
   > Hvis kontrolcifret ikke er en del af kontrolsumberegningen, skal du bruge 0 som tykkelse for kontrolcifret. I ovenstående tilfælde er tykkelse 8 f.eks. lig med 0, hvis kontrolcifret ikke skal bruges til at beregne kontrolcifret.

   :::image type="content" alt-text="skærmbillede af konfigureret kontrolsums validator." source="../media/checksum-validator.png" lightbox="../media/checksum-validator.png":::

### <a name="date-validator"></a>Dato validator

Hvis en datoværdi, der er integreret i regulære udtryk, er en del af et nyt mønster, du opretter, kan du bruge dato *validatoren* til at teste, om den opfylder dine kriterier. Hvis du f.eks. vil oprette et SIT for et nicifret medarbejder-id. De første seks cifre er ansættelsesdatoen i formatet DDMMYY, og de sidste tre er tilfældigt oprettede tal. Sådan valideres det, at de første seks cifre er i det korrekte format.

1. Definer det primære element med dette regulære udtryk:

   ```console
   \d{9}
   ```

2. Tilføj derefter dato validatoren.

3. Vælg datoformatet og startforskydningen. Da datostrengen er de første seks cifre, er forskydningen `0`.

   :::image type="content" alt-text="skærmbillede af konfigureret dato validator." source="../media/date-validator.png" lightbox="../media/date-validator.png":::

### <a name="functional-processors-as-validators"></a>Funktionelle processorer som validatorer

Du kan bruge funktionsprocessorer til nogle af de mest almindeligt brugte SIT'er som validatorer. Dette giver dig mulighed for at definere dit eget regulære udtryk, samtidig med at de passerer de ekstra kontroller, der kræves af SIT. Eksempelvis sikrer Func_India_Aadhar, at det brugerdefinerede regulære udtryk, der er defineret af dig,  videregiver den valideringslogik, der kræves for indisk Aadhar-kort. Du kan finde flere oplysninger om DLP-funktioner, der kan bruges som validatorer, [under Funktioner af typen Følsomme oplysninger](sit-functions.md). 

### <a name="luhn-check-validator"></a>Luhn-kontrol validator

Du kan bruge Luhn-validatoren, hvis du har en brugerdefineret type af følsomme oplysninger, der indeholder et regulært udtryk, der skal videregive [Luhn-algoritmen](https://en.wikipedia.org/wiki/Luhn_algorithm).

## <a name="sensitive-information-type-additional-checks"></a>Følsomme oplysninger type yderligere kontroller

Her er definitionerne og nogle eksempler på de tilgængelige yderligere kontroller.

**Udelade bestemte match**: Denne kontrol gør det muligt at definere nøgleord, der kan udelades, når du registrerer match for det mønster, du redigerer. Du kan f.eks. udelade testkreditnumre som "4111111111111111", så de ikke matcher som et gyldigt nummer.

**Starter eller starter ikke med tegn: Med** denne kontrol kan du definere de tegn, som de matchede elementer må eller ikke må starte med. Hvis mønsteret f.eks. kun vil registrere kreditkortnumre, der starter med 41, 42 eller 43, skal du vælge **Starter** med og føje 41, 42 og 43 til listen adskilt med komma. 

**Slutter eller slutter ikke med tegn**: Denne kontrol gør det muligt at definere de tegn, som de matchede elementer må eller ikke må slutte med. Hvis dit medarbejder-id f.eks. ikke kan slutte med 0 eller 1, skal  du vælge Slutter ikke med og føje 0 og 1 til listen adskilt med kommaer.

**Udelade dublerede** tegn: Med denne kontrol kan du ignorere forekomster, hvor alle cifrene er ens. Hvis det sekscifrede medarbejder-id ikke kan have alle cifrene til det samme, kan du f.eks. vælge Udelad dublerede tegn for at udelade 111111, 222222, 333333, 444444, 555555, 666666, 777777, 888888, 999999 og 000000 på listen over gyldige match for medarbejder-id'et.

**Medtag eller udelad præfikser**: Denne kontrol gør det muligt at definere nøgleord, der skal eller ikke skal findes umiddelbart før den matchende enhed. Afhængigt af din markering bliver enheder matchet eller ikke matchet, hvis de indledes med de præfikser, du medtager her. Hvis du f.eks **. Udelader** **præfikset GUID:**, betragtes enhver enhed, der indledes af **GUID:** ikke som et match.

**Medtage eller udelade suffikser** Denne kontrol gør det muligt at definere de nøgleord, der skal eller ikke skal findes umiddelbart efter den matchende enhed. Afhængigt af dit valg bliver enheder matchet eller ikke matchet, hvis de efterfølges af de suffikser, du medtager her. Hvis du f.eks **. Udelader** suffikset **:GUID**, bliver al tekst, der efterfølges af **:GUID** , ikke matchet.
