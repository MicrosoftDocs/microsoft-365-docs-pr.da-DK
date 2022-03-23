---
title: Netværk, der kan levere indhold
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/15/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Brug disse oplysninger til at få mere at vide om, Office 365 bruger Content Delivery Networks (CDN'er) til at forbedre ydeevnen.
ms.openlocfilehash: 1aecd8b23502ed8626979d258f7d26a90b4d3d51
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590558"
---
# <a name="content-delivery-networks-cdns"></a>Content Delivery Networks (CDN'er)

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

CDN'er hjælper Office 365 hurtig og pålidelig for slutbrugere. Skytjenester som f.eks. Office 365 CDN'er bruger CDN'er til at cache statiske aktiver tættere på browserne og beder dem om at sætte fart på overførslerne og reducere opfattede slutbrugernes ventetid. Oplysningerne i dette emne hjælper dig med at få mere at vide om Content Delivery Networks (CDN'er), og hvordan de bruges af Office 365.

## <a name="what-exactly-is-a-cdn"></a>Hvad er en CDN?

En CDN er et geografisk distribueret netværk bestående af proxy- og filservere i datacentre, der er forbundet via high-speed-basisnetværk. CDN'er bruges til at reducere ventetid og indlæsningstider for et bestemt sæt filer og objekter på et websted eller en tjeneste. En CDN kan have mange tusindvis af slutpunkter for optimal service af indgående anmodninger fra enhver placering.

CDNere bruges ofte til at levere hurtigere downloads af generisk indhold til et websted eller en tjeneste såsom Javascript-filer, ikoner og billeder, og kan også give privat adgang til brugerindhold som filer i SharePoint Online-dokumentbiblioteker, streaming media-filer og brugerdefineret kode.

CDN'er bruges af de fleste skybaserede virksomhedstjenester. Skytjenester som f.eks. Office 365 har millioner af kunder, der henter en blanding af beskyttet indhold (f.eks. mails) og generisk indhold (f.eks. ikoner) på én gang. Det er mere effektivt at placere billeder, som alle bruger, f.eks. ikoner, så tæt på brugerens computer som muligt. Det er ikke praktisk for alle skytjenester at opbygge CDN-datacentre, der lagrer dette generisk indhold i alle områder i hovedstaden eller endda i alle større internethubs over hele verden, så nogle af disse CDN'er deles.

## <a name="how-do-cdns-make-services-work-faster"></a>Hvordan får CDN'er tjenester til at fungere hurtigere?

Overførsel af almindelige objekter som f.eks. webstedsbilleder og ikoner igen og igen kan opbygge netværksbåndbredde, som kan bruges bedre til at hente vigtigt personligt indhold, f.eks. mails eller dokumenter. Da Office 365 en arkitektur, der omfatter CDN'er, kan ikoner, scripts og andet generisk indhold downloades fra servere tættere på klientcomputere, hvilket gør overførslerne hurtigere. Det betyder hurtigere adgang til dit personlige indhold, som er sikkert gemt i Office 365 datacentre.

CDN'er hjælper dig med at forbedre ydeevnen for skytjenesten på flere måder:

- CDN'er forskyder en del af netværket og filoverførselsbelastningen væk fra skytjenesten, hvilket frilagerer skytjenesteressourcer til servering af brugerindhold og andre tjenester ved at reducere behovet for at betjene anmodninger om statiske aktiver.
- CDN'er er designet til at give adgang til filer med lav latenstid ved at implementere højtydende netværk og filservere og ved at udnytte opdaterede netværksprotokoller som [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) med meget effektiv komprimering og anmode om multipleksing.
- CDN bruger mange globalt distribuerede slutpunkter til at gøre indhold tilgængeligt så tæt som muligt for brugerne.

## <a name="the-office-365-cdn"></a>Den Office 365 CDN

Den indbyggede Office 365 Content Delivery Network (CDN) giver Office 365-administratorer mulighed for at give bedre ydeevne for deres organisations SharePoint Online-sider ved at cache statiske aktiver tættere på browsere, der anmoder om dem, hvilket hjælper dig med at sætte fart på overførslerne og reducere ventetiden. Netværksserveren Office 365 CDN [HTTP/2-protokollen til](https://en.wikipedia.org/wiki/HTTP/2) forbedret komprimering og downloadhastigheder.

> [!NOTE]
> Lejerne Office 365 CDN kun tilgængelige for lejere i **produktionsskyen** (hele verden). Lejere i den amerikanske stat, Kina og Tysklands skyer understøtter i øjeblikket ikke Office 365 CDN.

The Office 365 CDN består af flere CDN'er, der giver dig mulighed for at hoste statiske aktiver på flere placeringer eller _oprindelser og betjene_ dem fra globale højhastighedsnetværk. Afhængigt af den type indhold, du vil hoste i Office 365 CDN, kan du tilføje offentlige oprindelser, **private** oprindelser eller begge dele.

![Office 365 CDN konceptuelt diagram.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN begrebsmæssigt diagram")

Indhold i **offentlige** oprindelser inden for Office 365 CDN er anonymt tilgængeligt og kan tilgås af alle, der har URL-adresser til tilknyttede aktiver. Da adgang til indhold i offentlige oprindelser er anonymt, bør du kun bruge det til at cachelagre ikke-følsomt generisk indhold som f.eks. Javascript-filer, scripts, ikoner og billeder. Den Office 365 CDN bruges som standard til at downloade generiske ressourceaktiver som Office 365 klientprogrammer fra en offentlig oprindelse.

**Private** oprindelser i Office 365 CDN giver privat adgang til brugerindhold som f.eks. SharePoint Online-dokumentbiblioteker, websteder og beskyttede billeder. Adgang til indhold i private oprindelser er sikret med dynamisk genererede tokens, så de kan kun åbnes af brugere med tilladelser til det oprindelige dokumentbibliotek eller den oprindelige lagerplacering. Private oprindelser i Office 365 CDN kan kun bruges til SharePoint Online-indhold, og du kan kun få adgang til aktiver via omdirigering fra din SharePoint Online-lejer.

Tjenesten Office 365 CDN inkluderet som en del af dit SharePoint Online-abonnement.

Du kan finde flere oplysninger om, hvordan du bruger Office 365 CDN, under Brug Office 365 til levering af [indhold med SharePoint Online](use-microsoft-365-cdn-with-spo.md).

Hvis du vil se en række korte videoer, der giver grundlæggende oplysninger og HOWTO-oplysninger om brug Office 365 CDN, skal du gå til [SharePoint på YouTube-kanalen Udviklermønstre og -fremgangsmåder](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Andre Microsoft-CDN'er

Selvom det ikke er en del af Office 365 CDN, kan du bruge disse CDN'er i din Office 365-lejer til at få adgang til SharePoint-udviklingsbiblioteker, brugerdefineret kode og andre formål, der falder uden for Office 365 CDN.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>Fra og med Q3 2020 begynder SharePoint Online cachelagring af videoer på internettet Azure CDN at understøtte forbedret afspilning og pålidelighed af video. Populære videoer streames fra det CDN slutpunkt, der er tættest på brugeren. Disse data forbliver inden for Microsoft 365 overholdelsesgrænse. Dette er en gratis tjeneste for alle lejere, og det kræver ikke nogen kundehandling at konfigurere.

Du kan bruge **Azure CDN** til at installere din egen CDN-forekomst til at hoste brugerdefinerede webdele, biblioteker og andre ressourceaktiver, hvilket giver dig mulighed for at anvende hurtigtaster på din CDN-lagerplads og give større kontrol over din CDN-konfiguration. Brug af Azure CDN er ikke gratis, og det kræver et Azure-abonnement.

Du kan finde flere oplysninger om, hvordan du konfigurerer Azure CDN forekomst, under [Hurtig start: Integrer en Azure Storage-konto Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

Se et eksempel på, hvordan Azure CDN kan bruges til at hoste SharePoint-webdele, under Installér din [SharePoint-webdel på klientsiden for at Azure CDN](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Du kan finde oplysninger Azure CDN PowerShell-modulet [i Administrer Azure CDN med PowerShell](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsofts **Ajax CDN** er en skrivebeskyttet CDN, der tilbyder mange populære biblioteker til udvikling, herunder jQuery (og alle dens andre biblioteker), ASP.NET Ajax, Bootstrap, Knockout.js og andre.
  
Hvis du vil medtage disse scripts i projektet, skal du blot erstatte eventuelle referencer til disse offentligt tilgængelige biblioteker med referencer til CDN-adressen i stedet for at medtage den i selve projektet. Brug f.eks. følgende kode til at oprette et link til jQuery:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Du kan finde flere oplysninger om, hvordan du bruger Microsoft Ajax CDN, under [Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Hvordan Office 365 indhold fra en CDN?

Uanset hvad CDN konfigurerer for din Office 365, er den grundlæggende datahentningsproces den samme.

1. Din klient (en browser eller Office) anmoder om data fra Office 365.

2. Office 365 enten returnerer dataene direkte til din klient eller, hvis dataene er en del af et sæt indhold, der er hostet af CDN, omdirigerer din klient til CDN URL-adressen.

    a. Hvis dataene allerede er cachelagret i en  offentlig oprindelse, henter din klient dataene direkte fra det nærmeste CDN til din klient.

    b. Hvis dataene allerede er cachelagret i en _privat_ oprindelse, kontrollerer CDN-tjenesten tilladelserne Office 365 din Office 365 for oprindelsen. Hvis du har tilladelser, genererer SharePoint Online dynamisk en brugerdefineret URL, der består af stien til aktivet i CDN og to adgangstokens, og returnerer den brugerdefinerede URL-adresse til din klient. Din klient downloader derefter dataene direkte fra det nærmeste CDN til din klient ved hjælp af den brugerdefinerede URL-adresse.

3. Hvis dataene ikke er cachelagret på CDN, anmoder CDN-noden om dataene fra Office 365 og cachelagrer derefter dataene i et stykke tid, efter at din klient har hentet dataene.

Datacenteret CDN det nærmeste datacenter til brugerens browser og ved hjælp af omdirigering downloade de ønskede data derfra. CDN er hurtig og kan spare brugere en masse downloadtid.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Hvordan skal jeg konfigurere mit netværk, så CDN'er fungerer bedst med Office 365?

Minimering af ventetid mellem klienter på dit netværk og CDN slutpunkter er den vigtigste overvejelse for at sikre optimal ydeevne. Du kan bruge de bedste fremgangsmåder, der er [](managing-office-365-endpoints.md) beskrevet i Administration af Office 365-slutpunkter, til at sikre, at din netværkskonfiguration tillader klientbrowsere at få adgang til CDN direkte i stedet for at dirigere CDN-trafik gennem centrale proxyer for at undgå at introducere unødvendig ventetid.

Du kan også læse [Office 365 Network Connectivity Principles for](./microsoft-365-network-connectivity-principles.md) at forstå begreberne bag optimering Office 365 netværkets ydeevne.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Er der en liste over alle de CDN'er, Office 365 bruger?

CDN'er, der bruges af Office 365, kan altid ændres, og i mange tilfælde er der flere CDN-partnere konfigureret i tilfælde af, at en sådan ikke er tilgængelig. De primære CDN'er, der bruges Office 365, er:

|CDN  |Firma  |Anvendelse  |Link  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Generiske aktiver i offentlige oprindelser SharePoint brugerindhold i private oprindelser         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Brugerdefinerede kode- SharePoint Framework løsninger         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (skrivebeskyttet)     |Microsoft         |Almindelige biblioteker for Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js osv.         |[Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Hvilken ydeevne opnår en CDN?

Der er mange faktorer involveret i at måle specifikke forskelle i ydeevnen mellem data, der downloades direkte fra Office 365, og data, der downloades fra en bestemt CDN, f.eks. din placering i forhold til din lejer og det nærmeste CDN-slutpunkt, antallet af aktiver på en side, der betjenes af CDN, og midlertidige ændringer i netværksventetid og båndbredde. En simpel A/B-test kan dog hjælpe med at vise forskellen i downloadtid for en bestemt fil.

De følgende skærmbilleder illustrerer forskellen i downloadhastighed mellem den oprindelige filplacering i Office 365 og den samme fil, der er hostet på [Microsoft Ajax-Content Delivery Network](/aspnet/ajax/cdn/overview). Disse skærmbilleder er fra **fanen Netværk** i Internet Explorer 11-udviklerværktøjerne. Disse skærmbilleder viser ventetiden på det populære bibliotek jQuery. Tryk på **F12** i Internet Explorer for at få dette skærmbillede frem, og vælg  fanen Netværk, som er symboliseret med et Wi-Fi ikon.
  
![Skærmbillede af F12-netværk.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Dette skærmbillede viser det bibliotek, der er overført til mastersidegalleriet på SharePoint Online-webstedet. Den tid, det har taget at overføre biblioteket, er 1,51 sekunder.
  
![Skærmbillede af indlæsningstiden 1,51.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Det andet skærmbillede viser den samme fil leveret af Microsofts CDN. Ventetiden denne gang er omkring 496 millisekunder. Dette er en stor forbedring og viser, at et helt sekund er skyggelagt fra den samlede tid, det er tid til at hente objektet.
  
![Skærmbillede af indlæsningstider i 469 ms.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Er mine data sikre?

Vi beskytter de data, der driver din virksomhed, godt. Data, der er gemt i Office 365 CDN, krypteres både under overførsel og in rest, og adgang til data i Office 365 SharePoint CDN er sikret ved Office 365 brugertilladelser og tokengodkendelse. Anmodninger om data i Office 365 SharePoint CDN skal henvises (omdirigeres) fra din Office 365-lejer, eller der genereres ikke et godkendelsestoken.

For at sikre at dine data forbliver sikre, anbefaler vi, at du aldrig gemmer brugerindhold eller andre følsomme data i et offentligt CDN. Da adgang til data i en offentlig CDN er anonym, bør offentlige CDN'er kun bruges til at hoste generisk indhold som f.eks. webscriptfiler, ikoner, billeder og andre ikke-følsomme aktiver.

> [!NOTE]
> Tredjepartsudbydere af CDN kan have standarder for beskyttelse af personlige oplysninger og overholdelse af regler og standarder, der afviger fra de forpligtelser, der er beskrevet i Office 365 Sikkerhedscenter. Data, der er cachelagret via CDN-tjenesten, overholder muligvis ikke Microsofts vilkår for behandling af data, og de kan være uden for Office 365 Sikkerhedscenters overholdelsesgrænser.

Hvis du vil have uddybende oplysninger om beskyttelse af personlige oplysninger og databeskyttelse for Office 365 CDN, skal du gå til følgende:  

- Få mere at vide Office 365 om beskyttelse af personlige oplysninger og databeskyttelse i [Microsoft Center for sikkerhed og beskyttelse af personlige oplysninger i Microsoft Center for sikkerhed og sikkerhed](https://www.microsoft.com/trustcenter)
- Få mere at vide om Akamais beskyttelse af personlige oplysninger og databeskyttelse i [Akamai Privacy Trust Center](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- Få mere at vide om beskyttelse af personlige oplysninger og databeskyttelse i [Azure Trust Center](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Hvordan kan jeg sikre mit netværk med alle disse tredjepartstjenester?

Ved at udnytte et omfattende sæt partnertjenester kan Office 365 skalere og opfylde krav til tilgængelighed samt forbedre brugeroplevelsen, når du bruger Office 365. De tredjepartstjenester, Office 365 udnytter, omfatter begge lister over tilbagekaldte certifikater, f.eks. crl.microsoft.com eller sa.symcb.com og CDN'er, f.eks. r3.res.outlook.com. Hver CDN FQDN, der genereres Office 365, er et brugerdefineret FQDN til Office 365. Hvis du bliver sendt til et FQDN på anmodning af Office 365 kan du være sikker på, at CDN-udbyderen kontrollerer FQDN og det underliggende indhold på den pågældende placering.
  
For kunder, der vil adskille anmodninger, der er beregnet for et Microsoft- eller Office 365-datacenter, fra anmodninger, der er beregnet for en tredjepart, har vi skrevet en vejledning til administration [af Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Er der en liste over alle de FQDN'er, der udnytter CDN'er?

Listen over FQDN'er, og hvordan de udnytter CDN'er, ændres over tid. Se vores publicerede Office 365 [URL-adresser og siden med IP-adresseintervaller](./urls-and-ip-address-ranges.md) for at blive opdateret med de seneste FQDN'er, der udnytter CDN'er.

Du kan også bruge DEN [Office 365-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md) til at anmode om de aktuelle Office 365 URL-adresser og IP-adresseintervaller formateret som CSV eller JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kan jeg bruge mit eget CDN og cachelagre indhold på mit lokale netværk?

Vi leder konstant efter nye måder at understøtte vores kunders behov på og undersøger i øjeblikket brugen af cachelagring af proxyløsninger og andre lokale CDN løsninger.

Selvom det ikke er en del af Office 365 CDN, kan du også bruge **Azure CDN** til at hoste brugerdefinerede webdele, biblioteker og andre ressourceaktiver, hvilket giver dig mulighed for at anvende hurtigtaster på dit CDN-lager og have større kontrol over din CDN-konfiguration. Brug af Azure CDN er ikke gratis, og det kræver et Azure-abonnement. Du kan finde flere oplysninger om, hvordan du konfigurerer Azure CDN forekomst, under [Hurtig start: Integrer en Azure Storage-konto Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Jeg bruger Azure ExpressRoute til Office 365, ændrer det noget?

[Azure ExpressRoute til Office 365](azure-expressroute.md) giver en dedikeret forbindelse til Office 365 infrastruktur, der er adskilt fra det offentlige internet. Det betyder, at klienter stadig skal oprette forbindelse via ikke-ExpressRoute-forbindelser for at oprette forbindelse til CDN'er og anden Microsoft-infrastruktur, der ikke udtrykkeligt er medtaget på listen over tjenester, der understøttes af ExpressRoute. Du kan finde flere oplysninger om, hvordan du distribuerer bestemt trafik, f.eks. anmodninger, der er beregnet [til CDN'er, Office 365 administration af netværkstrafik](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Kan jeg bruge CDN'SharePoint lokal server?

Brug af CDNere giver kun mening i en SharePoint Online-kontekst og skal undgås med SharePoint Server. Dette skyldes, at alle fordelene i forbindelse med geografisk placering ikke gælder, hvis serveren er placeret lokalt eller geografisk tæt på. Hvis der er en netværksforbindelse til de servere, hvor det hostes, kan webstedet bruges uden en internetforbindelse og kan derfor ikke hente de CDN filer. Ellers skal du bruge en CDN, hvis der er en tilgængelig og stabil for det bibliotek og de filer, du skal bruge til dit websted.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Se også

[Office 365 principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md)

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)

[Administrere Office 365 slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](./urls-and-ip-address-ranges.md)

[Brug Office 365 til levering af indhold med SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)

[Finjustere ydeevnen Office 365 finjustere ydeevnen](tune-microsoft-365-performance.md)
