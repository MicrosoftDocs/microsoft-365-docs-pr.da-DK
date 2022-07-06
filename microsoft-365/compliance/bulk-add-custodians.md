---
title: Importér tilsynsførende til en eDiscovery-sag (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Brug masseimportværktøjet til hurtigt at føje flere tilsynsførende og deres tilknyttede datakilder til en sag i Microsoft Purview eDiscovery (Premium).
ms.openlocfilehash: f50304711b12cbcf0b42f0cb185d29d085924108
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626859"
---
# <a name="import-custodians-to-an-ediscovery-premium-case"></a>Importér tilsynsførende til en eDiscovery-sag (Premium)

I forbindelse med Microsoft Purview eDiscovery (Premium)-sager, der involverer mange tilsynsførende, kan du importere flere tilsynsførende på én gang ved hjælp af en CSV-fil, der indeholder de oplysninger, der er nødvendige for at føje dem til en sag. Værktøjet til import af tilsynsførende validerer også CSV-filen, før importjobbet oprettes. Det betyder, at du kan rette eventuelle fejl i CSV-filen i stedet for at skulle vente, indtil importjobbet er fuldført, før du lærer, at der er fejl, der forhindrer en tilsynsførende i at blive føjet til sagen.

## <a name="before-you-import-custodians"></a>Før du importerer vogtere

- Du kan maksimalt importere 1.000 tilsynsførende (rækker) pr. CSV-fil. Bemærk, at import af 1.000 tilsynsførende på samme tid kan resultere i timeoutfejl, og nogle tilsynsførende kan mislykke importen. Du afhjælper dette ved at gentage importen, og de mislykkede tilsynsførende skal importeres. For at undgå timeout anbefaler vi, at du importerer 200 tilsynsførende ad gangen.

- Du kan tilknytte op til 500 datakilder for hver tilsynsførende.  

- Du kan kun importere tilsynsførende, der er en del af din organisations Azure Active Directory.

- Hver tilsynsførende skal have en entydig mailadresse.

- Hvis du vil importere en inaktiv postkasse som tilsynsførende eller knytte en inaktiv postkasse til en anden tilsynsførende, skal du føje præfikset "." til mailadressen på den inaktive postkasse (f.eks. .sarad@contoso.onmmicrosoft.com).

## <a name="import-custodians"></a>Importér tilsynsførende

1. Åbn sagen eDiscovery (Premium), og vælg fanen **Datakilder** .

2. Klik på **Tilføj****datakildeimportvarsmænd** > .

3. På siden **Hent skabelonguide** skal du klikke på **Download CSV-skabelonen** for at downloade en CSV-fil med en CSV-fil med frihedsberøvelsesskabelonen.

   ![Download en CSV-skabelon fra siden Import tilsynsførende.](../media/ImportCustodians1.png)

4. Føj oplysningerne om forældremyndigheden til CSV-filen, og gem dem på din lokale computer. Se afsnittet [Custodian CSV-fil](#custodian-csv-file) for at få detaljerede oplysninger om de påkrævede egenskaber i CSV-filen.

5. Når du har forberedt CSV-filen med oplysningerne om vogteren, skal du gå tilbage til fanen **Datakilder** og klikke på **Tilføj****datakildeimportvogtere** >  igen.

6. På siden med guiden **Upload CSV-fil** skal du klikke på **Overfør csv-fil** og derefter overføre den CSV-fil, der indeholder oplysningerne om vogteren.

   Når du har uploadet CSV-filen, validerer importguiden CSV-filen. Hvis der findes valideringsfejl, viser guiden et fejlbanner med et link til at få vist fejlene.

   ![Banner med valideringsfejl med link til flere oplysninger.](../media/ImportCustodians2.png)

   Fejloplysningerne identificerer rækken og kolonnen i den celle, der indeholder fejlen, og foreslår en afhjælpningshandling. Du skal rette eventuelle valideringsfejl og derefter genindlæse den faste CSV-fil. CSV-filen skal valideres, før du kan oprette jobbet til import af varetægtsfængslet.

7. Når CSV-filen er blevet valideret, skal du klikke på **Næste** og derefter klikke på **Importér** for at starte importjobbet.

Når du har startet importjobbet, gør eDiscovery (Premium) følgende ting:

- Opretter et job med navnet **BulkAddCustodian** under fanen **Jobs** i sagen.

- Udfører avanceret indeksering af alle datakilder for hver tilsynsførende.

- Placerer alle tilsynsførende datakilder i venteposition (hvis egenskaben **Is OnHold** i CSV-filen er angivet til TRUE)

Når jobbet som tilsynsførende for import er fuldført, føjes tilsynsførende og deres tilknyttede datakilder til siden **Datakilder** i sagen.

## <a name="custodian-csv-file"></a>Tilsynsførende CSV-fil

Når du har downloadet skabelonen CSV-tilsynsførende, kan du tilføje tilsynsførende og deres datakilder i hver række. Sørg for ikke at ændre kolonnenavnene i kolonneoverskriften. Brug kolonnerne for arbejdsbelastningstype og arbejdsbelastningsplacering til at knytte andre datakilder til en tilsynsførende.

| Kolonnenavn|Beskrivelse|
|:------- |:------------------------------------------------------------|
|**TilsynsførendekontaktMail**     |Forældremyndighedens UPN-mailadresse. F.eks. sarad@contoso.onmicrosoft.com.           |
|**Exchange er aktiveret** | TRUE/FALSE-værdi, der skal medtages eller ikke medtages i tilsynsførendes postkasse.      |
|**OneDrive er aktiveret** | TRUE/FALSE-værdi, der skal inkluderes eller ikke inkludere tilsynsførendes OneDrive for Business-konto. |
|**Er OnHold**        | TRUE/FALSE-værdi til at angive, om datakilderne for tilsynsførende skal placeres i venteposition. <sup>1</sup>     |
|**Arbejdsbelastning1-type**         |Strengværdi, der angiver den type datakilde, der skal knyttes til tilsynsførende. Mulige værdier omfatter: <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- TeamsMailbox<sup>2</sup><br/>- YammerMailbox<sup>2</sup>. Der skelnes mellem store og små bogstaver i de tidligere værdier for disse arbejdsbelastningstyper. CSV-filen indeholder kolonner til tre arbejdsbelastningstyper og deres tilsvarende arbejdsbelastningsplaceringer. Du kan tilføje i alt 500 arbejdsbelastningstyper og -placeringer.|
|**Placering af arbejdsbelastning1**     | Afhængigt af arbejdsbelastningstypen vil dette være placeringen af datakilden. Det kan f.eks. være mailadressen på en Exchange-postkasse eller URL-adressen til et SharePoint-websted. |
|||

> [!NOTE]
> <sup>1</sup> Hvis du sætter mere end 1.000 postkasser eller 100 websteder i venteposition i en sag, skalerer systemet automatisk eDiscovery-ventepositionen efter behov. Det betyder, at systemet automatisk føjer dataplaceringer til flere politikker for bevarelse i stedet for at føje dem til en enkelt politik. Grænsen på 10.000 politikker for sags bevarelse pr. organisation gælder dog stadig. Du kan finde flere oplysninger om begrænsninger for venteposition [under Grænser i eDiscovery (Premium)](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> Når du medtager arbejdsbelastninger for TeamsMailbox og YammerMailbox i CSV-filen, tilføjes gruppewebstedet (TeamSite og YammerSite) automatisk som standard. Du behøver ikke at angive TeamsSite og YammerSite separat i CSV-filen.

Her er et eksempel på en CSV-fil med oplysninger om tilsynsførende:<br/><br/>

|TilsynsførendekontaktMail      | Exchange er aktiveret | OneDrive er aktiveret | Er OnHold | Arbejdsbelastning1-type | Placering af arbejdsbelastning1             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | SANDT             | SANDT             | SANDT      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | SANDT             | SANDT             | SANDT      | |  |
|.johnj@contoso.onmicrosoft.com|SANDT|SANDT|SANDT||
|sarad@contoso.onmicrosoft.com|SANDT|SANDT|SANDT|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Som tidligere forklaret skal du føje præfikset "." til UPN-adressen for en inaktiv postkasse for at importere en inaktiv postkasse som tilsynsførende eller knytte en inaktiv postkasse til en anden tilsynsførende.
