---
title: Føj flere brugere på samme tid til Microsoft 365 – Hjælp til administratorer
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
- admindeeplinkMAC
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
description: 'Lær, hvordan du føjer flere brugere Microsoft 365 for business fra en liste i et regneark eller en anden CSV-formateret fil. Se en video på YouTube, der forklarer, hvordan du føjer konti Microsoft 365. I slutningen af denne proces vil hver enkelt bruger med en konto have en Microsoft 365 postkasse. '
ms.openlocfilehash: d9152ba8dfef21faeaba6f981c23359eb114b653
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590380"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a>Føj flere brugere på samme tid til Microsoft 365 – Hjælp til administratorer

Hver person i dit team skal have en brugerkonto, før de kan logge på og få adgang til Microsoft 365, f.eks. mail og Office. Hvis der er mange personer, kan du tilføje deres konti på én gang fra et Excel-regneark eller en anden fil, der er gemt i CSV-format. [Er du i tvivl om, hvad csv-formatet er](add-several-users-at-the-same-time.md#not-sure-what-csv-format-is)?
  
> [!NOTE]
> Hvis du ikke bruger den nye Microsoft 365 Administration, kan du aktivere den ved at vælge til/fra-knappen Prøv  den nye Administration øverst på startsiden.

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a>Tilføj flere brugere i Microsoft 365 Administration

1. Log på Microsoft 365 med din arbejds- eller skolekonto.

2. Vælg Aktive **brugere i** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Administration**</a>.

3. Vælg **Tilføj flere brugere**.

4. I panelet **Importér flere brugere** kan du eventuelt hente en CSV-eksempelfil med eller uden udfyldt eksempeldata.

    Dit regneark skal have de **nøjagtigt samme kolonneoverskrifter** som eksemplet (Brugernavn, Fornavn, og så videre). Hvis du bruger skabelonen, skal du åbne den i et tekstredigeringsværktøj, f.eks. Notesblok, og overveje at lade alle dataene i række 1 være og kun angive data i række 2 og nedenfor.

    Dit regneark skal også indeholde værdier for brugernavnet (f.eks. bob@contoso.com) og et visningsnavn (f.eks. Bob Kelly) for hver bruger.

  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Angiv en filsti i feltet, eller vælg Gennemse **for at** gå til placeringen af CSV-filen, og vælg derefter **Bekræft**.
  
    Hvis der er problemer med filen, vises problemet i panelet. Du kan også downloade en logfil.

6. I dialogboksen **Angiv brugerindstillinger** kan du angive logonstatus og vælge den produktlicens, der skal tildeles til alle brugere.

7. I dialogboksen  Vis resultat kan du vælge at sende resultaterne til dig selv eller andre brugere (adgangskoder vises som almindelig tekst), og du kan se, hvor mange brugere der er oprettet, og om du skal købe flere licenser for at tildele til nogle af de nye brugere.

## <a name="next-steps"></a>Næste trin

- Nu, hvor disse personer har konti, skal de downloade og installere eller geninstallere [Microsoft 365 eller Office 2016 på en pc eller Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Hver person i dit team kan installere Microsoft 365 på op til 5 pc'er eller Mac-computere.

- Hver person kan også konfigurere [Office-apps](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) og mail på en mobilenhed på op til 5 tablets og 5 telefoner, f.eks. iPhones, iPads og Android-telefoner og -tablets. På den måde kan de redigere Office hvor som helst.

    Se [Konfigurer Microsoft 365 til virksomheder](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for en komplet liste over konfigurationstrinnene.

## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a>Flere oplysninger om, hvordan du føjer brugere til Microsoft 365

### <a name="not-sure-what-csv-format-is"></a>Er du i tvivl om, hvad csv-formatet er?

En CSV-fil er en fil med kommaseparerede værdier. Du kan oprette eller redigere en fil som denne i et teksteditor- eller regnearksprogram, f.eks. Excel.
  
Du kan hente [dette eksempelark](https://www.microsoft.com/download/details.aspx?id=45485) som et udgangspunkt. Husk, Microsoft 365 kræver kolonneoverskrifter i den første række, så erstat dem ikke med noget andet. 
  
Gem filen under et nyt navn, og angiv CSV-format.
  
![Et billede af, hvordan du gemmer en fil i Excel CSV-format.](../media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Når du gemmer filen, får du sandsynligvis en meddelelse om, at nogle funktioner i projektmappen går tabt, hvis du gemmer filen i CSV-format. Dette er i orden. Klik **på Ja** for at fortsætte.
  
![Et billede af prompten, du muligvis får fra en Excel spørger, om du virkelig ønsker at gemme filen som et CSV-format.](../media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Tips til formatering af dit regneark

- **Har jeg brug for de samme kolonneoverskrifter som i eksempelarket?** Ja. Eksempelarket indeholder kolonneoverskrifter i den første række. Disse overskrifter er påkrævede. For hver bruger, du vil føje til Microsoft 365, skal du oprette en række under overskriften. Hvis du tilføjer, ændrer eller sletter nogen af kolonneoverskrifterne, vil Microsoft 365 muligvis ikke kunne oprette brugere ud fra oplysningerne i filen.

- **Hvad gør jeg, hvis jeg ikke har alle de nødvendige oplysninger for hver bruger?** Brugernavn og visningsnavn er påkrævet, og du kan ikke tilføje en ny bruger uden disse oplysninger. Hvis du ikke har nogle af de andre oplysninger, f.eks. faxen, kan du bruge et mellemrum plus et komma til at angive, at feltet skal forblive tomt.

- **Hvor lille eller stort må regnearket være?** Regnearket skal have mindst to rækker. En til kolonneoverskrifterne (kolonnenavnet for brugerdataene) og en til brugeren. Du kan ikke have mere end 251 rækker. Hvis du vil importere mere end 250 brugere, kan du oprette mere end ét regneark.

- **Hvilke sprog kan jeg bruge?** Når du opretter regnearket, kan du angive kolonnenavnene for brugerdata på alle sprog og med alle tegn, men du må ikke ændre rækkefølgen af etiketterne, sådan som det er vist i eksemplet. Du kan derefter oprette poster i felterne på et hvilket som helst sprog eller med alle tegn og gemme filen i Unicode- eller UTF-8-format.

- **Hvad nu, hvis jeg tilføjer brugere fra forskellige lande eller områder?** Opret et separat regneark for hvert område. Du skal gennemgå guiden Tilføj flere brugere for hvert regneark og give en enkelt placering for alle brugere i den fil, du arbejder med.

- **Er der en grænse for det antal tegn, jeg kan bruge?** Følgende tabel viser kolonnenavnene for brugerdataene og den maksimale tegnlængde for hvert navn i eksempelarket.

|**Kolonnenavn for brugerdata**|**Maksimal tegnlængde**|
|:-----|:-----|
|Brugernavn (påkrævet)  <br/> |79, inklusive sn-tegnet (@), i formatet name@domain.\<extension\>. Brugerens alias må ikke overskride 50 tegn, og domænenavnet må ikke overskride 48 tegn.  <br/> |
|Fornavn  <br/> |64  <br/> |
|Efternavn  <br/> |64  <br/> |
|Vist navn (påkrævet)  <br/> |256  <br/> |
|Stilling  <br/> |64  <br/> |
|Afdeling  <br/> |64  <br/> |
|Office tal  <br/> |128  <br/> |
|Office Telefon  <br/> |64  <br/> |
|Mobildata Telefon  <br/> |64  <br/> |
|Fax  <br/> |64  <br/> |
|Adresse  <br/> |1023  <br/> |
|By  <br/> |128  <br/> |
|Stat eller provins  <br/> |128  <br/> |
|Postnummer  <br/> |40  <br/> |
|Land eller område  <br/> |128  <br/> |

### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a>Har du stadig problemer, når du føjer brugere Microsoft 365?

- **Kontrollér, at regnearket er formateret korrekt.** Kontrollér, at kolonneoverskrifterne matcher overskrifterne i eksempelfilen. Sørg for, at du følger reglerne for tegnlængde, og at hvert felt er adskilt af et komma.

- **Hvis du ikke kan se de nye brugere på Microsoft 365, skal du vente et par minutter.** Det kan tage et stykke tid, før ændringerne træder i tværs af alle tjenesterne Microsoft 365. 

## <a name="related-articles"></a>Relaterede artikler

[Tilføj brugere enkeltvis eller flere Microsoft 365](/office365/admin/add-users/add-users)