---
title: Arbejde med vurderingsskabeloner i Microsoft Compliance Manager
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
description: Forstå, hvordan du bruger og administrerer skabeloner til oprettelse af vurderinger i Microsoft Compliance Manager. Opret og rediger skabeloner ved hjælp af en formateret Excel-fil.
ms.openlocfilehash: 0dc28eb3058e3b929da47d947b29c7ba7be41111
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758987"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Få mere at vide om vurderingsskabeloner i Overholdelsesstyring

**I denne artikel:** Forstå **, hvordan skabeloner fungerer****, og hvordan du administrerer dem** fra siden med vurderingsskabeloner. Få instruktioner til **oprettelse af** nye skabeloner, **udvidelse** og **ændring af** eksisterende skabeloner, **formatering af dine skabelondata med Excel** og eksport af **skabelonrapporter**.

> [!IMPORTANT]
> De vurderingsskabeloner, der er tilgængelige for din organisation, afhænger af din licensaftale. [Gennemse detaljerne](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="templates-overview"></a>Oversigt over skabeloner

En skabelon er en struktur af kontrolelementer til oprettelse af en vurdering i Overholdelsesstyring. Vores omfattende sæt af skabeloner kan hjælpe din organisation med at overholde nationale, regionale og branchespecifikke krav til indsamling og brug af data.

## <a name="template-versions-microsoft-and-universal"></a>Skabelonversioner: Microsoft og universal

Vi refererer til skabeloner med samme navn som deres underliggende certificering eller regulering, f.eks. EU's GDPR-skabelon og ISO/IEC 27701:2019-skabelonen.

Overholdelsesstyring kan bruges til at vurdere forskellige produkttyper. Alle skabeloner bortset fra grundlinjen findes i mindst én version, der gælder for et foruddefineret produkt, f.eks. Microsoft 365, og en universel version, der kan skræddersyes til at passe til andre produkter. Vurderinger fra universelle skabeloner er mere generelle, men tilbyder udvidet alsidighed, da de kan hjælpe dig med nemt at spore din organisations overholdelse af angivne standarder på tværs af flere produkter.

Bemærk, at kunder med GCC (US Government Community) Moderate, GCC High og DoD i øjeblikket ikke kan bruge universelle skabeloner.

## <a name="template-availability-and-licensing"></a>Skabelontilgængelighed og licensering

Der er to kategorier af skabeloner i Overholdelsesstyring: inkluderet og Premium.

1. **Inkluderede skabeloner** tildeles af din Compliance Manager-licens og dækker vigtige regler og krav. Du kan få mere at vide om, hvilke skabeloner der er tilgængelige under din licensaftale, under [Licensoplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Premium skabeloner** til at dække yderligere behov og scenarier kan opnås ved at købe skabelonlicenser.

Når du begynder at oprette vurderinger, sporer Overholdelsesstyring, hvor mange skabeloner der er aktive, så du kan overvåge dit forbrug. Du kan få mere at vide under [Aktive og inaktive skabeloner](compliance-manager-templates.md#active-and-inactive-templates).

Få vist den [komplette liste over skabeloner](compliance-manager-templates-list.md) , der er tilgængelige i Overholdelsesstyring.

### <a name="purchase-premium-template-licenses"></a>Køb Premium-skabelonlicenser

Skabelonlicenser kan hentes ved hjælp af en eller flere af disse metoder, afhængigt af din licensaftale for Overholdelsesstyring. Når dit køb er fuldført, bør skabelonerne blive tilgængelige i din lejer inden for 48 timer.

**Kommerciel og GCC moderat**

Kommercielle og GCC Moderate konti kan købe skabelonlicenser i Administration ([få mere at vide om abonnementer, licenser og fakturering](/microsoft-365/commerce/)). Vælg det antal licenser, du vil købe, og din betalingsplan.

Købslinks:

- [Kommercielle](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC moderat](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Du kan også erhverve licenser via din deltagelse i [Cloud Solution Provider-programmet](https://partner.microsoft.com/membership/cloud-solution-provider) eller [volumenlicens](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**GCC Konti med høj og DOD**

GCC Høj- og DOD-konti skal købe skabelonlicenser via [volumenlicenser](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Prøv Premium-skabeloner

Hvis du vil prøve Premium-skabeloner, før du foretager et køb, kan du også få prøveversioner af licenserne. Prøvelicenser er gode i op til 25 skabeloner i 90 dage. Når du har fået din prøvelicens, skal skabelonerne være tilgængelige i din lejer inden for 48 timer.

Hvis din organisation har en kommerciel licens til Overholdelsesstyring, kan du få mere at vide om, hvordan du starter din prøveversion på [Om den gratis prøveversion af Premium-vurderinger fra Microsoft Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

Hvis din organisation er under en GCC- eller DOD-licens, skal du vælge det relevante prøveversionslink til din organisation:

- [GCC moderat](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC Høj](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Aktive og inaktive skabeloner

Skabeloner viser en aktiveringsstatus som enten aktiv eller inaktiv:

- En skabelon anses for **at være aktiv** , når du har oprettet en vurdering ud fra skabelonen.
- En skabelon betragtes som **inaktiv** , hvis din organisation ikke bruger den til en vurdering.

Hvis du linker vurderinger til en købt Premium-skabelon, vil skabelonen være aktiv i et år. Dit køb fornys automatisk, medmindre du annullerer.

#### <a name="activated-templates-counter"></a>Tæller for aktiverede skabeloner

Siden med vurderingssider og vurderingsskabeloner har en **aktiveret tæller for skabeloner** øverst. Tælleren viser antallet af skabeloner, der er i brug ud af det antal, du er berettiget til at bruge i henhold til din licensaftale. Brug af skabeloner tælles på certificeringsniveau.

Hvis tælleren f.eks. viser 2/5, betyder det, at din organisation har aktiveret to skabeloner ud af de 5, der er tilgængelige til brug.

Hvis din tæller viser 5/2, angiver det, at din organisation overskrider sine grænser og skal købe 3 af de Premium-skabeloner, der er i brug.

Skabeloner til et foruddefineret produkt, f.eks. Microsoft 365, har fælles licenser til de universelle versioner af den samme skabelon. Det giver dig mulighed for at bruge den samme underliggende certificering på tværs af mere end ét produkt. Hvis du bruger en af eller begge versioner af den samme skabelon, tælles den kun med som én aktiveret skabelon.

Du kan finde flere oplysninger i [Licensvejledning til Overholdelsesstyring](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Få vist og administrer skabeloner

Siden med vurderingsskabeloner i Overholdelsesstyring viser en liste over skabeloner og vigtige oplysninger om dem. Listen indeholder skabeloner, der leveres af Overholdelsesstyring, samt alle skabeloner, din organisation har ændret eller oprettet. Du kan anvende filtre til at finde en skabelon, der er baseret på certificering, produktområde, land, branche, hvem der har oprettet den, og om skabelonen er aktiveret til oprettelse af vurdering.

Vælg en skabelon på rækken for at få vist detaljesiden. Denne side indeholder en beskrivelse af skabelonen og yderligere oplysninger om certificering, omfang og kontrolelementer. På denne side kan du vælge de relevante knapper for at oprette en vurdering, eksportere skabelondataene til Excel eller redigere skabelonen.

## <a name="create-an-assessment-template"></a>Opret en vurderingsskabelon

Hvis du vil oprette din egen nye skabelon til brugerdefinerede vurderinger i Overholdelsesstyring, skal du bruge et særligt formateret Excel regneark til at samle de nødvendige kontroldata. Når regnearket er fuldført, skal du importere det i Overholdelsesstyring. Du kan få mere at vide under [Opret en vurderingsskabelon](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Rediger en vurderingsskabelon

Når du arbejder med vurderinger i Overholdelsesstyring, kan det være en god idé at ændre en vurderingsskabelon, som du har oprettet. Processen ligner processen til oprettelse af skabelonen, da du uploader en formateret Excel fil med dine skabelondata. Hvis du vil vide mere om, hvordan du foretager ændringer, og hvordan du bevarer de data, du stadig vil bevare, skal du se [Rediger en vurderingsskabelon](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Udvid en vurderingsskabelon

Overholdelsesstyring giver dig mulighed for at føje dine egne kontrolelementer og forbedringshandlinger til en eksisterende skabelon. Denne proces kaldes udvidelse af en skabelon. Hvis du vil udvide en skabelon, skal du bruge særlige instruktioner til tilføjelse af skabelondata, afhængigt af om du udvider Microsoft-vurderingsskabeloner eller universelle vurderingsskabeloner. Du kan få mere at vide under [Udvid en vurderingsskabelon](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Formatér vurderingsskabelondata i Excel

Når du opretter, ændrer eller udvider vurderingsskabeloner i Overholdelsesstyring, skal du arbejde med Excel regneark, der bruger et bestemt format og skema. Disse specifikationer skal følges, for at filerne kan importeres korrekt. Du kan få mere at vide under [Formatér skabelondata for vurdering i Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Eksportér en skabelon

Du kan eksportere en Excel fil, der indeholder alle en skabelons data. Du skal eksportere en skabelon for at kunne redigere den, da det er den Excel fil, du redigerer og uploader i [ændringsprocessen](compliance-manager-templates-modify.md). Du kan også eksportere en skabelon til reference, hvis du vil bruge data fra den, mens du opretter en ny brugerdefineret skabelon.

Hvis du vil eksportere skabelonen, skal du gå til siden med skabelonoplysninger og vælge knappen **Eksportér til Excel**.

Bemærk, at når du eksporterer en skabelon, du har udvidet fra en overholdelsesstyringsskabelon, indeholder den eksporterede fil kun de attributter, du har føjet til skabelonen. Den eksporterede fil indeholder ikke de oprindelige skabelondata, der er leveret af Microsoft. Hvis du vil have en sådan rapport, skal du se instruktionerne til [eksport af en vurderingsrapport](compliance-manager-assessments.md#export-an-assessment-report).