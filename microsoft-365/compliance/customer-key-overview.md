---
title: Tjenestekryptering med Microsoft Purview-kundenøgle
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: I denne artikel får du mere at vide om, hvordan tjenestekryptering fungerer sammen med Microsoft Purview kundenøgle.
ms.openlocfilehash: 3a0533b94cb70c9fc46d6246e99d3f9fdb5eb6e6
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415079"
---
# <a name="service-encryption-with-microsoft-purview-customer-key"></a>Tjenestekryptering med Microsoft Purview-kundenøgle

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 leverer grundlæggende kryptering på diskenhedsniveau, der er aktiveret via BitLocker og Distributed Key Manager (DKM). Microsoft 365 tilbyder et ekstra krypteringslag for dit indhold. Dette indhold indeholder data fra Exchange Online, Skype for Business, SharePoint Online, OneDrive for Business og Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Sådan arbejder tjenestekryptering, BitLocker og kundenøgle sammen

Dine data krypteres altid inaktive i Microsoft 365-tjenesten med BitLocker og DKM. Du kan få flere oplysninger under [Sådan sikrer Exchange Online dine mailhemmeligheder](exchange-online-secures-email-secrets.md). Kundenøglen giver ekstra beskyttelse mod visning af data af uautoriserede systemer eller medarbejdere og supplerer BitLocker-diskkryptering i Microsoft-datacentre. Kryptering af tjenesten er ikke beregnet til at forhindre Microsoft-medarbejdere i at få adgang til dine data. I stedet hjælper Kundenøgle dig med at overholde lovmæssige eller overholdelsesforpligtelser til styring af rodnøgler. Du giver udtrykkeligt Microsoft 365 tjenester tilladelse til at bruge dine krypteringsnøgler til at levere ekstra cloudtjenester, f.eks. eDiscovery, antimalware, anti-spam, søgeindeksering osv.

Kundenøglen er baseret på tjenestekryptering og giver dig mulighed for at angive og styre krypteringsnøgler. Microsoft 365 bruger derefter disse nøgler til at kryptere inaktive data som beskrevet i [VILKÅR for onlinetjenester](https://www.microsoft.com/licensing/product-licensing/products.aspx). Kundenøglen hjælper dig med at opfylde overholdelsesforpligtelserne, fordi du styrer de krypteringsnøgler, som Microsoft 365 bruger til at kryptere og dekryptere data.
  
Customer Key forbedrer din organisations mulighed for at opfylde kravene til overholdelse af angivne standarder, der angiver vigtige aftaler med cloududbyderen. Med Kundenøgle kan du angive og styre rodkrypteringsnøglerne til dine inaktive Microsoft 365 data på programniveau. Det betyder, at du har kontrol over organisationens nøgler.

## <a name="customer-key-with-hybrid-deployments"></a>Kundenøgle med hybridinstallationer

Kundenøglen krypterer kun inaktive data i cloudmiljøet. Kundenøglen fungerer ikke for at beskytte dine postkasser og filer i det lokale miljø. Du kan kryptere dine data i det lokale miljø ved hjælp af en anden metode, f.eks. BitLocker.

## <a name="about-data-encryption-policies"></a>Om politikker for datakryptering

En politik for datakryptering definerer krypteringshierarkiet. Dette hierarki bruges af tjenesten til at kryptere data ved hjælp af hver af de nøgler, du administrerer, og den tilgængelighedsnøgle, der er beskyttet af Microsoft. Du opretter DEP'er ved hjælp af PowerShell-cmdlet'er og tildeler derefter disse DEP'er for at kryptere programdata. Der er tre typer dep'er, der understøttes af kundenøglen. Hver politiktype bruger forskellige cmdlet'er og giver dækning for en anden type data. De DEP'er, du kan definere, omfatter:

**Forhindring af datatab for flere Microsoft 365 arbejdsbelastninger** Disse DEP'er krypterer data på tværs af flere M365-arbejdsbelastninger for alle brugere i lejeren. Disse arbejdsbelastninger omfatter:

- Teams chatbeskeder (1:1 chats, gruppechats, mødechats og kanalsamtaler)
- Teams mediemeddelelser (billeder, kodestykker, videomeddelelser, lydmeddelelser, wikibilleder)
- Teams opkalds- og mødeoptagelser, der er gemt i Teams lager
- Teams chatbeskeder
- Teams chatforslag fra Cortana
- Teams statusmeddelelser
- Bruger- og signaloplysninger for Exchange Online
- Exchange Online postkasser, der ikke allerede er krypteret af dep'er til postkasser
- Samlet lager for overvågningslog
- Microsoft Purview Information Protection:

  - Præcise datamatchdata (EDM), herunder datafilskemaer, regelpakker og salte, der bruges til at hash-hashe de følsomme data. For EDM og Microsoft Teams krypterer DEP med flere arbejdsbelastninger nye data fra det tidspunkt, du tildeler forhindring af datatab til lejeren. For Exchange Online krypterer Kundenøgle alle eksisterende og nye data.

  - Konfiguration af mærkater for følsomhedsmærkater

DEP'er med flere arbejdsbelastninger krypterer ikke følgende typer data. I stedet bruger Microsoft 365 andre krypteringstyper til at beskytte disse data.

- SharePoint og OneDrive for Business data.
- Microsoft Teams filer og nogle Teams opkalds- og mødeoptagelser, der er gemt i OneDrive for Business og SharePoint Online, krypteres ved hjælp af programmet til SharePoint Online.
- Andre Microsoft 365 arbejdsbelastninger, f.eks. Yammer og Planner, der i øjeblikket ikke understøttes af Kundenøgle.
- Teams livebegivenhedsdata.

Du kan oprette flere dep'er pr. lejer, men du kan kun tildele én dep ad gangen. Når du tildeler forhindring af datatab, starter kryptering automatisk, men det tager noget tid at fuldføre, afhængigt af størrelsen på din lejer.

**DEP'er til Exchange Online postkasser** PostkasseDEP'er giver mere præcis kontrol over individuelle postkasser i Exchange Online. Brug postkasseDEP'er til at kryptere data, der er gemt i EXO-postkasser af forskellige typer, f.eks. UserMailbox, MailUser, Group, PublicFolder og Delte postkasser. Du kan have op til 50 aktive dep'er pr. lejer og tildele disse dep'er til individuelle postkasser. Du kan tildele én dep til flere postkasser.

Dine postkasser krypteres som standard ved hjælp af Microsoft-administrerede nøgler. Når du tildeler en kundenøgle til en postkasse:

- Hvis postkassen krypteres ved hjælp af en forhindring af datakørsel med flere arbejdsbelastninger, genwrapser tjenesten postkassen ved hjælp af den nye postkasse-programmet, så længe en bruger eller en systemhandling får adgang til postkassedataene.

- Hvis postkassen allerede er krypteret ved hjælp af Microsoft-administrerede nøgler, genwrapser tjenesten postkassen ved hjælp af den nye postkasse-programmet, så længe en bruger eller en systemhandling får adgang til postkassedataene.

- Hvis postkassen endnu ikke er krypteret ved hjælp af standardkryptering, markerer tjenesten postkassen til flytning. Krypteringen sker, når flytningen er fuldført. Flytning af postkasser styres på baggrund af de prioriteter, der er angivet for alle Microsoft 365. Du kan få flere oplysninger under [Flyt anmodninger i Microsoft 365-tjenesten](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Hvis postkasserne ikke krypteres inden for det angivne tidspunkt, skal du kontakte Microsoft.

Senere kan du enten opdatere programmet til dataopdatering eller tildele en anden dep til postkassen som beskrevet i [Administrer kundenøgle for Office 365](customer-key-manage.md). Hver postkasse skal have de relevante licenser for at få tildelt en deaktiveringspostkasse. Du kan få flere oplysninger om licenser under [Før du konfigurerer kundenøgle](customer-key-set-up.md#before-you-set-up-customer-key).

DEP'er kan tildeles til en delt postkasse, en offentlig mappepostkasse og Microsoft 365 gruppepostkasse for lejere, der opfylder licenskravet for brugerpostkasser. Du behøver ikke separate licenser til ikke-brugerspecifikke postkasser for at tildele kundenøgle-forhindring af dataadgang.

For kundenøgle-DEP'er, som du tildeler til individuelle postkasser, kan du anmode Microsoft om at fjerne bestemte DEP'er, når du forlader tjenesten. Du kan få oplysninger om processen til datarensning og tilbagekaldelse af nøgler under [Tilbagekald dine nøgler, og start processen for datarensningsstien](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Når du tilbagekalder adgangen til dine nøgler som en del af at forlade tjenesten, slettes tilgængelighedsnøglen, hvilket resulterer i kryptografisk sletning af dine data. Kryptografisk sletning afhjælper risikoen for dataremanens, hvilket er vigtigt for at opfylde både sikkerheds- og overholdelsesforpligtelserne.

**Dep for SharePoint Online og OneDrive for Business** Denne dep bruges til at kryptere indhold, der er gemt i SPO og OneDrive for Business, herunder Microsoft Teams filer, der er gemt i SPO. Hvis du bruger multi-geo-funktionen, kan du oprette én DEP pr. geo for din organisation. Hvis du ikke bruger multi-geo-funktionen, kan du kun oprette én dep pr. lejer. Se detaljerne i [Konfigurer kundenøgle](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Krypteringsciffer, der bruges af kundenøglen

Kundenøglen bruger forskellige krypteringsciffer til at kryptere nøgler som vist i følgende tal.

Det nøglehierarki, der bruges til DEP'er, der krypterer data for flere Microsoft 365 arbejdsbelastninger, svarer til det hierarki, der bruges til DEP'er for individuelle Exchange Online postkasser. Den eneste forskel er, at postkassenøglen erstattes med den tilsvarende Microsoft 365 arbejdsbelastningsnøgle.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Krypteringsciffer, der bruges til at kryptere nøgler til Exchange Online og Skype for Business

![Krypteringsciffer til Exchange Online kundenøgle.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Krypteringsciffer, der bruges til at kryptere nøgler til SharePoint Online-, OneDrive for Business- og Teams-filer

![Krypteringsciffer til SharePoint onlinekundenøgle.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Kundelockbox](customer-lockbox-requests.md)

- [Tjenestekryptering](office-365-service-encryption.md)
