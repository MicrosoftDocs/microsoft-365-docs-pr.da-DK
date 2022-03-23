---
title: Tjenestekryptering med kundenøgle
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
description: I denne artikel kan du få mere at vide om, hvordan tjenestekryptering fungerer sammen med kundenøgle Microsoft 365.
ms.openlocfilehash: 14760bfcb26fa1bf45c54661cbb6fc189bad7d93
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63588987"
---
# <a name="service-encryption-with-customer-key"></a>Tjenestekryptering med kundenøgle

Microsoft 365 leverer grundlinje, kryptering på volumenniveau aktiveret via BitLocker og Distributed Key Manager (DKM). Microsoft 365 et ekstra lag kryptering til dit indhold. Dette indhold omfatter data fra Exchange Online, Skype for Business, SharePoint Online, OneDrive for Business og Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Sådan fungerer tjenestekryptering, BitLocker og Kundenøgle sammen

Dine data krypteres altid ved rester i Microsoft 365 med BitLocker og DKM. Du kan få mere at [vide Exchange Online hvordan du sikrer dine mailhemmeligheder](exchange-online-secures-email-secrets.md). Kundenøgle giver ekstra beskyttelse mod visning af data fra uautoriserede systemer eller medarbejdere og supplerer BitLocker-diskkryptering i Microsofts datacentre. Tjenestekryptering er ikke beregnet til at forhindre Microsoft-medarbejdere i at få adgang til dine data. I stedet kan kundenøgle hjælpe dig med at opfylde lovmæssige eller overholdelsesforpligtelser til kontrol af rodnøgler. Du autoriserer udtrykkeligt Microsoft 365-tjenester til at bruge dine krypteringsnøgler til at levere værditilførte skytjenester som f.eks. eDiscovery, antimalware, antispam, søgeindeksering osv.

Kundenøgle er bygget på tjenestekryptering og gør det muligt at levere og kontrollere krypteringsnøgler. Microsoft 365 derefter disse nøgler til at kryptere dine in rest-data, sådan som det er beskrevet i vilkårene [for onlinetjenester (OST)](https://www.microsoft.com/licensing/product-licensing/products.aspx). Kundenøgle hjælper dig med at opfylde overholdelsesforpligtelserne, fordi du styrer de krypteringsnøgler, som Microsoft 365 bruger til at kryptere og dekryptere data.
  
Kundenøgle forbedrer din organisations mulighed for at opfylde de krav i forbindelse med overholdelse af regler og standarder, der angiver vigtige bestemmelser med serviceudbyder. Med kundenøgle kan du angive og kontrollere rodkrypteringsnøglerne til dine Microsoft 365 data in rest på programniveau. Som resultat deraf kan du have kontrol over organisationens nøgler.

## <a name="customer-key-with-hybrid-deployments"></a>Kundenøgle med hybridinstallationer

Kundenøgle krypterer kun in rest-data i skyen. Kundenøgle beskytter ikke postkasser og filer i det lokale miljø. Du kan kryptere dine lokale data ved hjælp af en anden metode, f.eks BitLocker.

## <a name="about-data-encryption-policies"></a>Om politikker for datakryptering

En politik for datakryptering definerer krypteringshierarkiet. Dette hierarki bruges af tjenesten til at kryptere data ved hjælp af hver af de nøgler, du administrerer, og den tilgængelighedsnøgle, der er beskyttet af Microsoft. Du opretter IP'er ved hjælp af PowerShell-cmdlet'er og tildeler derefter disse DEP'er for at kryptere programdata. Der findes tre typer indholdstyper, der understøttes af Microsoft 365 Customer Key, hvor hver politiktype bruger forskellige cmdlet'er og leverer dækning af forskellige datatyper. De IP'er, du kan definere, omfatter:

**DEP for flere Microsoft 365 arbejdsbelastninger** Disse DEP'er krypterer data på tværs af flere M365-arbejdsbelastninger for alle brugere i lejeren. Disse arbejdsbelastninger omfatter:

- Teams chatmeddelelser (1:1 chats, gruppechats, mødechats og kanalsamtaler)
- Teams mediemeddelelser (billeder, kodestykker, videomeddelelser, lydbeskeder, wiki-billeder)
- Teams opkalds- og mødeoptagelser, der er gemt Teams lager
- Teams chatmeddelelser
- Teams forslag til chat ved at Cortana
- Teams statusmeddelelser
- Bruger- og signaloplysninger til Exchange Online
- Exchange Online postkasser, der ikke allerede er krypteret med postkasse-DEP'er
- Microsoft Information Protection:

  - Nøjagtige data matchdata (EDM) , herunder datafilskemaer, regelpakker og salte, der bruges til at hashtagme de følsomme data. For EDM og Microsoft Teams krypterer MULTI-workload DEP nye data fra det tidspunkt, du tildeler DEP til lejeren. For Exchange Online krypterer Kundenøgle alle eksisterende og nye data.

  - Etiketkonfiguration for følsomhedsmærkater

MULTI-workload DEP'er krypterer ikke følgende datatyper. I stedet Microsoft 365 bruge andre typer kryptering til at beskytte disse data.

- SharePoint og OneDrive for Business data.
- Microsoft Teams filer og nogle Teams opkalds- og mødeoptagelser, der er gemt i OneDrive for Business og SharePoint Online, krypteres ved hjælp af SharePoint Online DEP.
- Andre Microsoft 365 arbejdsbelastninger som f.eks. Yammer Planner, der i øjeblikket ikke understøttes af Kundenøgle.
- Teams med livebegivenhed.

Du kan oprette flere DEP'er pr. lejer, men kun tildele én dep ad gangen. Når du tildeler DEP, starter krypteringen automatisk, men tager lidt tid at fuldføre, afhængigt af størrelsen på din lejer.

**DEP'er til Exchange Online postkasser** PostkasseDEP'er giver mere præcis kontrol over individuelle postkasser i Exchange Online. Brug postkasse-IP'er til at kryptere data, der er gemt i EXO-postkasser af forskellige typer, f.eks. UserMailbox, MailUser, Group, PublicFolder og Delte postkasser. Du kan have op til 50 aktive IP'er pr. lejer og tildele disse DEP'er til individuelle postkasser. Du kan tildele én DEP til flere postkasser.

Som standard bliver dine postkasser krypteret ved hjælp af Microsoft-administrerede nøgler. Når du tildeler en kundenøgle dep til en postkasse:

- Hvis postkassen er krypteret med en DEP med flere arbejdsbelastninger, omskriver tjenesten postkassen ved hjælp af den nye postkasse DEP, så længe en bruger eller en systemhandling får adgang til postkassedataene.

- Hvis postkassen allerede er krypteret ved hjælp af Microsoft-administrerede nøgler, omskriver tjenesten postkassen ved hjælp af den nye postkasse DEP, så længe en bruger eller en systemhandling får adgang til postkassedataene.

- Hvis postkassen endnu ikke er krypteret med standardkryptering, markerer tjenesten postkassen for en flytning. Krypteringen finder sted, når flytningen er fuldført. Postkassebevægelser er underlagt prioriteter, der er angivet for alle Microsoft 365. Du kan finde flere oplysninger [under Flytningsanmodninger i Microsoft 365 tjeneste](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Hvis postkasserne ikke er krypteret inden for den angivne tid, skal du kontakte Microsoft.

Senere kan du enten opdatere dep'en eller tildele en anden dep til postkassen som beskrevet i Administrer kundenøgle [for Office 365](customer-key-manage.md). Hver postkasse skal have relevante licenser for at kunne tildeles en dep. Du kan finde flere oplysninger om licenser [under Før du konfigurerer en kundenøgle](customer-key-set-up.md#before-you-set-up-customer-key).

IP'er kan tildeles til en delt postkasse, offentlig mappepostkasse og Microsoft 365 gruppepostkasse for lejere, der opfylder licenskravene for brugerpostkasser. Du behøver ikke separate licenser til ikke-brugerspecifikke postkasser for at tildele kundenøgle-DEP.

For de kundenøgle-DEP'er, du tildeler de enkelte postkasser, kan du anmode Microsoft om at fjerne bestemte DEP'er, når du forlader tjenesten. Du kan finde oplysninger om data tømningsprocessen og tilbagekaldte nøgler i Tilbagekald dine nøgler [, og start processen med at fjerne data](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Når du tilbagekalder adgangen til dine nøgler som en del af at forlade tjenesten, slettes tilgængelighedsnøglen, hvilket resulterer i krypteret sletning af dine data. Krypteret sletning mindsker risikoen for dataremanencer, hvilket er vigtigt for at overholde både sikkerhed og overholdelsesforpligtelser.

**DEP til SharePoint Online og OneDrive for Business** Denne dep bruges til at kryptere indhold, der er gemt i SPO og OneDrive for Business, herunder Microsoft Teams-filer, der er gemt i SPO. Hvis du bruger multi-geo-funktionen, kan du oprette én DEP pr. geo for organisationen. Hvis du ikke bruger funktionen multi-geo, kan du kun oprette én dep pr. lejer. Se oplysningerne i [Konfigurer kundenøgle](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Krypteringskryptering, der bruges af kundenøgle

Kundenøgle bruger forskellige krypteringskrypteringskrypteringsnøgler til at kryptere nøgler som vist på følgende figurer.

Nøglehierarkiet, der bruges til deP'er, der krypterer data for flere Microsoft 365 arbejdsbelastninger, svarer til det hierarki, der bruges til DEP'er til individuelle Exchange Online postkasser. Den eneste forskel er, at postkassenøglen erstattes med den tilsvarende Microsoft 365 arbejdsbelastningsnøgle.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Krypteringskryptering, der bruges til at kryptere nøgler for Exchange Online og Skype for Business

![Krypteringskryptering til Exchange Online kundenøgle.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Krypteringskryptering, der bruges til at kryptere nøgler SharePoint Online-, OneDrive for Business- og Teams-filer

![Krypteringskryptering til SharePoint Online-kundenøgle.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Kunde-lockbox](customer-lockbox-requests.md)

- [Tjenestekryptering](office-365-service-encryption.md)
