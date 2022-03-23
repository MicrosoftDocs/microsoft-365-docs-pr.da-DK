---
title: Importere Advanced eDiscovery ere, der er Advanced eDiscovery sag
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Brug masseimportværktøjet til hurtigt at føje flere ydbrugere og deres tilknyttede datakilder til en sag Advanced eDiscovery.
ms.openlocfilehash: f02745f8eb9dff2ce54d128d967486b0dd9cbc7a
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590270"
---
# <a name="import-custodians-to-an-advanced-ediscovery-case"></a>Importere Advanced eDiscovery ere, der er Advanced eDiscovery sag

I Advanced eDiscovery, der involverer mange personer, der er øvrige, kan du importere flere  brugen af disse personer på én gang ved hjælp af en CSV-fil, der indeholder de oplysninger, der er nødvendige for at føje dem til en sag. Værktøjet til import-godkendere kan også validere CSV-filen, før importjobbet oprettes. Det betyder, at du kan løse eventuelle fejl i CSV-filen i stedet for at skulle vente, indtil importjobbet er fuldført, før du lærer, at der er fejl, der forhindrer en leder i at blive føjet til sagen.

## <a name="before-you-import-custodians"></a>Før du importerer 2010-2016-

- Du kan maksimalt importere 1.000 personer, der er  kolonner (rækker) pr. CSV-fil.

- Du kan tilknytte op til 500 datakilder for hver databehandler.  

- Du kan kun importere importere, der er en del af din organisations Azure Active Directory.

- Hver modtager skal have en entydig mailadresse.

- Hvis du vil importere en inaktiv postkasse som en assistent, eller hvis du vil knytte en inaktiv postkasse til en anden modtager, skal du tilføje et "." præfiks i mailadressen til den inaktive postkasse (f.eks. .sarad@contoso.onmmicrosoft.com).

## <a name="import-custodians"></a>Importér ydsere

1. Åbn dialogboksen Advanced eDiscovery store og små bogstaver, og vælg **fanen** Datakilder.

2. Klik på **Tilføj datakildeImportere** > **, der er årsagen til årsagen til årsagen**.

3. På siden **Hent skabelonguide** skal du klikke på **Download CSV-skabelonen for at** downloade en skabelon til skabelonen CSV-fil, der skal vises.

   ![Download en CSV-skabelon fra pop op-siden Import-2010-2016.](../media/ImportCustodians1.png)

4. Føj oplysninger om din sikkerhed til CSV-filen, og gem dem på din lokale computer. Du kan [finde detaljerede oplysninger om de påkrævede](#custodian-csv-file) egenskaber i CSV-filen i sektionen Til opbevaring af CSV-filer.

5. Når du har forberedt CSV-filen med oplysninger om, hvem der er din ven,  >  kan  du gå tilbage til fanen Datakilder og klikke på Tilføj **datakildeImportér beredskabere** igen.

6. På siden **Upload CSV-fil** skal du klikke på **Upload CSV-fil** og derefter overføre den CSV-fil, der indeholder oplysninger om videoen.

   Når du har overført CSV-filen, validerer guiden Importér CSV-filen. Hvis der findes valideringsfejl, viser guiden et fejlbanner med et link til visning af fejlene.

   ![Banner til valideringsfejl med link til flere oplysninger.](../media/ImportCustodians2.png)

   Fejloplysningerne identificerer rækken og kolonnen i den celle, der indeholder fejlen, og foreslår en afhjælpningshandling. Du er nødt til at løse eventuelle valideringsfejl og derefter genindlæse den rettede CSV-fil. CSV-filen skal valideres korrekt, før du kan oprette importjobbet.

7. Når CSV-filen er blevet valideret, skal du klikke på **Næste** og derefter klikke på **Importér for** at starte importjobbet.

Når du har startet importjobbet, Advanced eDiscovery du gøre følgende:

- Opretter et job **med navnet BulkAddCustodian** **under fanen** Jobs for sagen.

- Udfører Avanceret indeksering af alle datakilder for hver person, der er på arbejde.

- Placerer alle datakilder, der er påholdende, i venteposition (hvis **egenskaben Is OnHold** i CSV-filen er indstillet til SAND)

Når import- og importbehandlerjobbet er færdigt, føjes y-edskilder og deres tilknyttede **datakilder til** siden datakilder for sagen.

## <a name="custodian-csv-file"></a>Øvrige CSV-fil

Når du har downloadet skabelonen til hjælp til csv-førere, kan du tilføje y-pindpinde og deres datakilder i hver række. Sørg for ikke at ændre kolonnenavnene i kolonneoverskriften. Brug kolonnerne med arbejdsbelastningstypen og arbejdsbelastningen til at knytte andre datakilder til en kollega.

| Kolonnenavn|Beskrivelse|
|:------- |:------------------------------------------------------------|
|**Kontakt, der kan kontaktesMail**     |Den anden modtagers UPN-mailadresse. For eksempel sarad@contoso.onmicrosoft.com.           |
|**Exchange aktiveret** | VÆRDIEN SAND/FALSK, som skal medtages eller ikke medtages i postkassen for den, der er tilsvarer.      |
|**OneDrive aktiveret** | VÆRDIEN SAND/FALSK, der skal medtages eller ikke medtages i forældrenes OneDrive for Business konto. |
|**Is OnHold**        | VÆRDIEN SAND/FALSK for at angive, om dataene, der skal kontrolleres, skal være i venteposition. <sup>1</sup>     |
|**Arbejdsbelastning1-type**         |Strengværdi, der angiver typen af datakilde, der skal knyttes til assistenten. Mulige værdier omfatter: <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- <sup>TeamsMailbox2</sup><br/>- <sup>YammerMailbox2</sup>. De forrige værdier for disse typer af arbejdsbelastninger tager hensyn til store og små bogstaver. CSV-filen indeholder kolonner til tre typer af arbejdsbelastninger og deres tilsvarende arbejdsbelastningsplaceringer. Du kan tilføje samlet 500 typer af arbejdsbelastninger og placeringer.|
|**Arbejdsbelastning1-placering**     | Afhængigt af arbejdsmængdens type vil dette være placeringen af datakilden. Mailadressen til en postkasse til Exchange eller URL-adressen til et SharePoint websted. |
|||

> [!NOTE]
> <sup>1</sup> Hvis du sætter mere end 1.000 postkasser eller 100 websteder i venteposition i en sag, skalerer systemet automatisk eDiscovery-ventepositionen efter behov. Det betyder, at systemet automatisk føjer dataplaceringer til flere politikker for venteposition i stedet for at føje dem til en enkelt politik. Men grænsen på 10.000 politikker for venteposition for hver organisation gælder stadig. Du kan finde flere oplysninger om begrænsninger i [venteposition i Advanced eDiscovery](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> Når du medtager arbejdsbelastninger for TeamsMailbox og YammerMailbox i CSV-filen, tilføjes gruppewebstedet (TeamSite og YammerSite) automatisk som standard. Du behøver ikke at angive TeamsSite og YammerSite separat i CSV-filen.

Her er et eksempel på en CSV-fil med oplysninger om arkiveringsinformation:<br/><br/>

|Kontakt, der kan kontaktesMail      | Exchange aktiveret | OneDrive aktiveret | Is OnHold | Arbejdsbelastning1-type | Arbejdsbelastning1-placering             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | SAND             | SAND             | SAND      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | SAND             | SAND             | SAND      | |  |
|.johnj@contoso.onmicrosoft.com|SAND|SAND|SAND||
|sarad@contoso.onmicrosoft.com|SAND|SAND|SAND|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Som tidligere nævnt skal du tilføje et "." præfiks til UPN-adressen på en inaktiv postkasse for at importere en inaktiv postkasse som en medarbejdermedarbejder eller for at knytte en inaktiv postkasse til en anden inaktiv postkasse.
