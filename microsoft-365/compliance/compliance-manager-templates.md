---
title: Arbejde med bedømmelsesskabeloner i Microsoft Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du bruger og administrerer skabeloner til opbygning af bedømmelser i Microsoft Compliance Manager. Opret og rediger skabeloner ved hjælp af en formateret Excel fil.
ms.openlocfilehash: 6885008e58c1e1289723a6d8c1ee4e04d16740b0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591070"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Få mere at vide om bedømmelsesskabeloner i Overholdelsesstyring

**I denne artikel:** Forstå **, hvordan skabeloner fungerer,** **og hvordan du administrerer dem fra** siden med bedømmelsesskabeloner. Få vejledning i **at** oprette **nye skabeloner,** udvide  og ændre eksisterende skabeloner, formatere dine **skabelondata Excel** og eksportere **skabelonrapporter**.

> [!IMPORTANT]
> De bedømmelsesskabeloner, der er tilgængelige for din organisation, afhænger af din licensaftale. [Gennemgå oplysningerne](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="templates-overview"></a>Oversigt over skabeloner

En skabelon er en ramme af kontrolelementer til oprettelse af en vurdering i Overholdelsesstyring. Vores omfattende sæt skabeloner kan hjælpe din organisation med at overholde nationale, regionale og branchespecifikke krav vedrørende indsamling og brug af data.

## <a name="template-versions-microsoft-and-universal"></a>Skabelonversioner: Microsoft og universal

Vi refererer til skabeloner med samme navn som deres underliggende certificering eller forordning, f.eks. EU GDPR-skabelonen og ISO/IEC 27701:2019-skabelonen.

Compliance Manger kan bruges til at vurdere forskellige produkttyper. Alle skabeloner, der adskiller sig fra den oprindelige plan, findes i mindst én version, der gælder for et foruddefineret produkt, f.eks. Microsoft 365, og en universel version, der kan tilpasses til andre produkter. Bedømmelser fra universelle skabeloner er mere generelle, men tilbyder udvidet fleksibilitet, da de kan hjælpe dig med nemt at spore din organisations overholdelse på tværs af flere produkter.

Bemærk, at kunder i det amerikanske government community (GCC) Moderate, GCC High og Department of Defense (DoD) i øjeblikket ikke kan bruge universelle skabeloner.

## <a name="template-availability-and-licensing"></a>Tilgængelighed og licensering af skabeloner

Der er to kategorier af skabeloner i Overholdelsesstyring: inkluderet og premium.

1. **Inkluderede skabeloner** tildeles af din Compliance Manager-licens og dækker vigtige regler og krav. Du kan få mere at vide om, hvilke skabeloner der er tilgængelige i henhold til din licensaftale, [under Licensoplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Premium skabeloner,** der dækker yderligere behov, og scenarier kan fås ved at købe skabelonlicenser.

Når du begynder at oprette bedømmelser, sporer Overholdelsesstyring, hvor mange skabeloner der er aktive, så du kan overvåge din brug. Du kan få mere at vide under [Aktive og inaktive skabeloner](compliance-manager-templates.md#active-and-inactive-templates).

Få vist den [komplette liste over skabeloner, der](compliance-manager-templates-list.md) er tilgængelige i Overholdelsesstyring.

### <a name="purchase-premium-template-licenses"></a>Køb Premium-skabelonlicenser

Skabelonlicenser kan fås ved hjælp af en eller flere af disse metoder, afhængigt af din Overholdelsesstyring-licensaftale. Når dit køb er afsluttet, skulle skabelonerne være tilgængelige i din lejer inden for 48 timer.

**Kommerciel og GCC moderat**

Kommercielle og GCC Moderate konti kan købe skabelonlicenser i Administration (få [mere at vide om abonnementer, licenser og fakturering](/microsoft-365/commerce/)). Vælg antallet af licenser, du vil købe, og din betalingsplan.

Købslinks:

- [Kommerciel](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC moderat](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Du kan også købe licenser via din deltagelse i [Cloud Solution Provider-programmet eller](https://partner.microsoft.com/membership/cloud-solution-provider) [volumenlicens](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**GCC High- og DOD-konti**

GCC High- og DOD-konti skal købe skabelonlicenser via [volumenlicens](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Prøv førsteklasses skabeloner

Hvis du vil prøve førsteklasses skabeloner, før du foretager et køb, kan du også købe prøveversioner af licenserne. Prøvelicenser er gode i op til 25 skabeloner i 90 dage. Når du har fået din prøvelicens, bør skabelonerne være tilgængelige i din lejer inden for 48 timer.

Hvis din organisation har en kommerciel licens til Overholdelsesstyring, kan du se, hvordan du starter din prøveversion på Om den gratis prøveversion [af Microsoft Compliance Manager Premium-bedømmelser](compliance-easy-trials-compliance-manager-assessments.md).

Hvis din organisation er under en GCC en DOD-licens, skal du vælge det relevante prøvelink til din organisation:

- [GCC moderat](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC høj](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Aktive og inaktive skabeloner

Skabeloner viser en aktiveringsstatus som enten aktiv eller inaktiv:

- En skabelon betragtes som aktiv **,** når du opretter en vurdering ud fra den pågældende skabelon.
- En skabelon anses for **at være** inaktiv, hvis din organisation ikke bruger den til en vurdering.

Hvis du sammenkæder eventuelle bedømmelser med en købt Premium-skabelon, vil den pågældende skabelon være aktiv i et år. Dit køb fornys automatisk, medmindre du annullerer.

#### <a name="activated-templates-counter"></a>Tæller for aktiverede skabeloner

Din side med bedømmelses- og bedømmelsesskabeloner **har en aktiveret skabelontæller** nær toppen. Tælleren viser antallet af skabeloner, der er i brug, ud af det antal, du er berettiget til at bruge i henhold til din licensaftale. Brug af skabeloner tælles på certificeringsniveau.

Hvis din tæller f.eks. viser 2/5, betyder det, at din organisation har aktiveret to skabeloner ud af de 5, der er tilgængelige til brug.

Hvis din tæller viser 5/2, betyder det, at din organisation overskrider sine grænser og skal købe 3 af de førsteklasses skabeloner, der er i brug.

Skabeloner til et foruddefineret produkt, f.eks. Microsoft 365, har fælles licensering med de universelle versioner af den samme skabelon. Dette giver dig mulighed for at bruge den samme underliggende certificering på tværs af mere end ét produkt. Brug af en eller begge versioner af den samme skabelon tæller kun som én aktiveret skabelon.

Du kan få mere at vide under [Vejledning til licenser til Overholdelsesstyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Få vist og administrer skabeloner

Siden med bedømmelsesskabeloner i Overholdelsesstyring viser en liste over skabeloner og vigtige oplysninger om dem. Listen indeholder skabeloner fra Overholdelsesstyring samt alle skabeloner, din organisation har ændret eller oprettet. Du kan anvende filtre til at finde en skabelon, der er baseret på certificering, produktomfang, land, branche, hvem der har oprettet den, og om skabelonen er aktiveret til oprettelse af bedømmelsesvurdering.

Vælg en skabelon fra dens række for at få vist dens detaljeside. Denne side indeholder en beskrivelse af skabelonen og yderligere oplysninger om certificering, omfang og detaljer om kontrolelementer. Fra denne side kan du vælge de relevante knapper til at oprette en bedømmelsesvurdering, eksportere skabelondataene Excel eller redigere skabelonen.

## <a name="create-an-assessment-template"></a>Opret en bedømmelsesskabelon

Hvis du vil oprette din egen nye skabelon til brugerdefinerede bedømmelser i Overholdelsesstyring, skal du bruge et specialformateret Excel-regneark til at samle de nødvendige kontroldata. Når du er færdig med regnearket, skal du importere det i Overholdelsesstyring. Du kan få mere at vide [under Opret en bedømmelsesskabelon](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Rediger en bedømmelsesskabelon

Når du arbejder med bedømmelser i Overholdelsesstyring, kan det være en ide at ændre en bedømmelsesskabelon, du har oprettet. Processen svarer til processen til oprettelse af skabeloner, hvor du overfører en formateret fil Excel dine skabelondata. Du kan få mere at vide om, hvordan du foretager ændringer, og hvordan du bevarer de data, du stadig vil bevare, i [Rediger en bedømmelsesskabelon](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Udvide en bedømmelsesskabelon

Overholdelsesstyring giver mulighed for at tilføje dine egne kontrolelementer og forbedringshandlinger til en eksisterende skabelon. Denne proces kaldes at udvide en skabelon. Hvis du vil udvide en skabelon, skal du bruge særlige instruktioner til at føje til skabelondata, afhængigt af om du udvider Microsoft-bedømmelsesskabeloner eller universelle bedømmelsesskabeloner. Du kan få mere at vide under [Udvid en bedømmelsesskabelon](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Formatér data fra bedømmelsesskabelonen i Excel

Når du opretter, redigerer eller udvider bedømmelsesskabeloner i Overholdelsesstyring, arbejder du med Excel, der bruger et bestemt format og skema. Disse specifikationer skal følges, for at filerne kan importeres korrekt. Du kan få mere at vide [i Formatér data til bedømmelsesskabeloner Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Eksportér en skabelon

Du kan eksportere Excel fil, der indeholder alle en skabelons data. Du skal eksportere en skabelon for at redigere den, da dette vil være den Excel fil, du redigerer og uploader i [ændringsprocessen](compliance-manager-templates-modify.md). Du kan også eksportere en skabelon til reference, hvis du vil bruge data fra den, mens du konstruerer en ny brugerdefineret skabelon.

Hvis du vil eksportere skabelonen, skal du gå til siden med skabelonoplysninger og vælge **knappen Excel** Eksportér til.

Bemærk, at når du eksporterer en skabelon, du har udvidet fra en Overholdelsesstyring-skabelon, indeholder den eksporterede fil kun de attributter, du har føjet til skabelonen. Den eksporterede fil medtager ikke de oprindelige skabelondata, der leveres af Microsoft. Se instruktionerne til at eksportere en bedømmelsesrapport for [at få en sådan rapport](compliance-manager-assessments.md#export-an-assessment-report).