---
title: Content Delivery Networks
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Brug disse oplysninger til at få mere at vide om, hvordan Office 365 bruger CDN'er (Content Delivery Networks) til at forbedre ydeevnen.
ms.openlocfilehash: b2809a524088b3cb53e415d3d83d1f8a02b27dc1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092729"
---
# <a name="content-delivery-networks-cdns"></a>Netværk til levering af indhold (CDN'er)

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

CDN'er hjælper med at holde Office 365 hurtigt og pålideligt for slutbrugerne. Cloudtjenester som Office 365 bruge CDN'er til at cachelagre statiske aktiver tættere på de browsere, der anmoder dem om at fremskynde downloads og reducere den opfattede ventetid for slutbrugeren. Oplysningerne i dette emne hjælper dig med at få mere at vide om CDN'er (Content Delivery Networks), og hvordan de bruges af Office 365.

## <a name="what-exactly-is-a-cdn"></a>Hvad er en CDN?

Et CDN er et geografisk distribueret netværk, der består af proxy- og filservere i datacentre, der er forbundet med højhastigheds backbone-netværk. CDN'er bruges til at reducere ventetiden og indlæsningstiden for et bestemt sæt filer og objekter på et websted eller en tjeneste. En CDN kan have mange tusinde slutpunkter til optimal servicering af indgående anmodninger fra enhver placering.

CDN'er bruges ofte til at levere hurtigere downloads af generisk indhold til et websted eller en tjeneste, f.eks. Javascript-filer, ikoner og billeder, og kan også give privat adgang til brugerindhold, f.eks. filer i SharePoint Online-dokumentbiblioteker, streamingmediefiler og brugerdefineret kode.

CDN'er bruges af de fleste cloudtjenester i virksomheder. Cloudtjenester som Office 365 få millioner af kunder til at downloade en blanding af beskyttet indhold (f.eks. mails) og generisk indhold (f.eks. ikoner) på én gang. Det er mere effektivt at placere billeder, som alle bruger, f.eks. ikoner, så tæt på brugerens computer som muligt. Det er ikke praktisk for alle cloudtjenester at bygge CDN datacentre, der gemmer dette generiske indhold i alle storbyområder eller endda i alle større internethubber rundt om i verden, så nogle af disse CDN'er deles.

## <a name="how-do-cdns-make-services-work-faster"></a>Hvordan får CDN'er tjenester til at fungere hurtigere?

Download af almindelige objekter som f.eks. webstedsbilleder og ikoner igen og igen kan optage netværksbåndbredde, der bedre kan bruges til at downloade vigtigt personligt indhold, f.eks. mail eller dokumenter. Da Office 365 bruger en arkitektur, der indeholder CDN'er, kan ikonerne, scripts og andet generisk indhold downloades fra servere, der er tættere på klientcomputerne, hvilket gør downloads hurtigere. Det betyder hurtigere adgang til dit personlige indhold, som er sikkert gemt i Office 365 datacentre.

CDN'er hjælper med at forbedre ydeevnen i cloudtjenesten på flere måder:

- CDN'er flytter en del af netværks- og fildownloadbyrden væk fra cloudtjenesten og frigør cloudtjenesteressourcer til visning af brugerindhold og andre tjenester ved at reducere behovet for at håndtere anmodninger om statiske aktiver.
- CDN'er er udviklet til at give filadgang med lav ventetid ved at implementere netværk og filservere med høj ydeevne og ved at udnytte opdaterede netværksprotokoller, f.eks [. HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) , med høj effektiv komprimering og anmodning om multipleksning.
- CDN netværk bruger mange globalt distribuerede slutpunkter til at gøre indhold tilgængeligt så tæt som muligt på brugerne.

## <a name="the-office-365-cdn"></a>Office 365 CDN

Den indbyggede Office 365 Content Delivery Network (CDN) gør det muligt for Office 365 administratorer at levere bedre ydeevne for deres organisations SharePoint Online-sider ved at cachelagring af statiske aktiver tættere på de browsere, der anmoder om dem, hvilket hjælper med at fremskynde downloads og reducere ventetiden. Office 365 CDN bruger [HTTP/2-protokollen](https://en.wikipedia.org/wiki/HTTP/2) til forbedrede komprimerings- og downloadhastigheder.

> [!NOTE]
> Den Office 365 CDN er kun tilgængelig for lejere i **produktionsskyen** (verden over). Lejere i cloudmiljøet US Government, Kina og Tyskland understøtter i øjeblikket ikke Office 365 CDN.

Den Office 365 CDN består af flere CDN'er, der giver dig mulighed for at hoste statiske aktiver på flere placeringer eller _oprindelser_ og betjene dem fra globale netværk med høj hastighed. Afhængigt af den type indhold, du vil hoste i Office 365 CDN, kan du tilføje **offentlige** oprindelser, **private** oprindelser eller begge dele.

![Office 365 CDN konceptuelt diagram.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN konceptuelt diagram")

Indhold i **offentlige** oprindelser i Office 365 CDN er tilgængeligt anonymt og kan tilgås af alle, der har URL-adresser til hostede aktiver. Da adgang til indhold med offentlig oprindelse er anonym, bør du kun bruge dem til at cachelagre ikke-følsomt generisk indhold, f.eks. Javascript-filer, scripts, ikoner og billeder. Den Office 365 CDN bruges som standard til at downloade generiske ressourceaktiver, f.eks. Office 365 klientprogrammer fra en offentlig oprindelse.

**Private** oprindelser i Office 365 CDN give privat adgang til brugerindhold, f.eks. SharePoint Online-dokumentbiblioteker, websteder og beskyttede billeder. Adgang til indhold i private oprindelser sikres med dynamisk genererede tokens, så de kun kan tilgås af brugere med tilladelser til det oprindelige dokumentbibliotek eller den oprindelige lagerplacering. Private oprindelser i Office 365 CDN kan kun bruges til SharePoint onlineindhold, og du kan kun få adgang til aktiver via omdirigering fra din SharePoint Online-lejer.

Office 365 CDN-tjenesten er inkluderet som en del af dit SharePoint Online-abonnement.

Du kan få flere oplysninger om, hvordan du bruger Office 365 CDN, under [Brug netværket til levering af Office 365 indhold sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md).

Hvis du vil se en række korte videoer, der indeholder konceptuelle og HOWTO-oplysninger om brug af Office 365 CDN, skal du besøge [YouTube-kanalen SharePoint Udviklermønstre og -fremgangsmåder](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Andre Microsoft CDN'er

Selvom du ikke er en del af Office 365 CDN, kan du bruge disse CDN'er i din Office 365 lejer til at få adgang til SharePoint udviklingsbiblioteker, brugerdefineret kode og andre formål, der falder uden for Office 365 CDN.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>Fra og med 3. kvartal 2020 begynder SharePoint Online at cachelagring af videoer på Azure CDN for at understøtte forbedret videoafspilning og pålidelighed. Populære videoer streames fra det CDN slutpunkt, der er tættest på brugeren. Disse data forbliver inden for Microsoft Purview-grænsen. Dette er en gratis tjeneste for alle lejere, og det kræver ikke nogen kundehandling at konfigurere.

Du kan bruge **Azure CDN** til at udrulle din egen CDN forekomst til hosting af brugerdefinerede webdele, biblioteker og andre ressourceaktiver, hvilket giver dig mulighed for at anvende adgangsnøgler på dit CDN lager og udøve større kontrol over din CDN konfiguration. Brug af Azure CDN er ikke gratis og kræver et Azure-abonnement.

Du kan få flere oplysninger om, hvordan du konfigurerer en Azure CDN instans, i [Hurtig start: Integrer en Azure Storage-konto med Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

Du kan se et eksempel på, hvordan Azure CDN kan bruges til at hoste SharePoint webdele, under [Installér din SharePoint webdel på klientsiden for at Azure CDN](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Du kan få oplysninger om Azure CDN PowerShell-modulet under [Administrer Azure CDN med PowerShell](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsofts **Ajax CDN** er en skrivebeskyttet CDN, der tilbyder mange populære udviklingsbiblioteker, herunder jQuery (og alle sine andre biblioteker), ASP.NET Ajax, Bootstrap, Knockout.js, og andre.
  
Hvis du vil medtage disse scripts i projektet, skal du blot erstatte referencer til disse offentligt tilgængelige biblioteker med referencer til den CDN adresse i stedet for at medtage dem i selve projektet. Brug f.eks. følgende kode til at linke til jQuery:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Du kan få flere oplysninger om, hvordan du bruger Microsoft Ajax-CDN, [under Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Hvordan bruger Office 365 indhold fra en CDN?

Uanset hvad CDN du konfigurerer for din Office 365 lejer, er den grundlæggende datahentningsproces den samme.

1. Din klient (en browser eller et Office klientprogram) anmoder om data fra Office 365.

2. Office 365 returnerer enten dataene direkte til klienten, eller hvis dataene er en del af et indholdssæt, der hostes af CDN, omdirigerer klienten til den CDN URL-adresse.

    a. Hvis dataene allerede er cachelagret i en _offentlig_ oprindelse, downloader din klient dataene direkte fra den nærmeste CDN placering til klienten.

    b. Hvis dataene allerede er cachelagret i en _privat_ oprindelse, kontrollerer CDN-tjenesten din Office 365 brugerkontos tilladelser til oprindelsen. Hvis du har tilladelser, genererer SharePoint Online dynamisk en brugerdefineret URL-adresse, der består af stien til aktivet i CDN og to adgangstokens, og returnerer den brugerdefinerede URL-adresse til klienten. Din klient downloader derefter dataene direkte fra den nærmeste CDN placering til klienten ved hjælp af den brugerdefinerede URL-adresse.

3. Hvis dataene ikke cachelagres på CDN, anmoder den CDN node om dataene fra Office 365 og cachelagrer derefter dataene i en periode, efter at klienten har downloadet dataene.

Den CDN finder ud af det nærmeste datacenter til brugerens browser og downloader de ønskede data derfra ved hjælp af omdirigering. CDN omdirigering er hurtig og kan spare brugerne en masse downloadtid.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Hvordan skal jeg konfigurere mit netværk, så CDN'er fungerer bedst sammen med Office 365?

Minimering af ventetid mellem klienter på dit netværk og CDN slutpunkter er den vigtigste overvejelse for at sikre optimal ydeevne. Du kan bruge de bedste fremgangsmåder, der er beskrevet i [Administration af Office 365 slutpunkter](managing-office-365-endpoints.md), til at sikre, at netværkskonfigurationen tillader klientbrowsere at få direkte adgang til CDN i stedet for at dirigere CDN trafik gennem centrale proxyer for at undgå unødvendig ventetid.

Du kan også læse [Office 365 principper for netværksforbindelsen](./microsoft-365-network-connectivity-principles.md) for at forstå begreberne bag optimering af Office 365 netværksydeevne.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Er der en liste over alle de CDN'er, som Office 365 bruger?

De CDN'er, der bruges af Office 365 kan altid ændres, og i mange tilfælde er der flere CDN partnere, der er konfigureret i tilfælde af, at en ikke er tilgængelig. De primære CDN'er, der bruges af Office 365, er:

|CDN  |Virksomhed  |Brug  |Link  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Generiske aktiver i offentlige oprindelser, SharePoint brugerindhold i privat oprindelse         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Brugerdefineret kode, SharePoint Framework løsninger         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (skrivebeskyttet)     |Microsoft         |Fælles biblioteker for Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js osv.         |[Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Hvilke ydeevnegevinster giver en CDN?

Der er mange faktorer involveret i måling af specifikke forskelle i ydeevnen mellem data, der downloades direkte fra Office 365, og data, der downloades fra en bestemt CDN, f.eks. din placering i forhold til din lejer og det nærmeste CDN slutpunkt, antallet af aktiver på en side, der betjenes af CDN, og midlertidige ændringer i netværksventetid og båndbredde. En simpel A/B-test kan dog hjælpe med at vise forskellen i downloadtiden for en bestemt fil.

Følgende skærmbilleder illustrerer forskellen i downloadhastigheden mellem den oprindelige filplacering i Office 365 og den samme fil, der hostes på [Microsoft Ajax-Content Delivery Network](/aspnet/ajax/cdn/overview). Disse skærmbilleder er fra fanen **Netværk** i Udviklerværktøjer i Internet Explorer 11. Disse skærmbilleder viser ventetiden på det populære bibliotek jQuery. Hvis du vil have vist denne skærm, skal du trykke på **F12** i Internet Explorer og vælge fanen **Netværk** , der er symboliseret med et Wi-Fi-ikon.
  
![Skærmbillede af F12 Network.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Dette skærmbillede viser det bibliotek, der er uploadet til mastersidegalleriet på selve SharePoint Online-webstedet. Den tid, det tog at overføre biblioteket, er 1,51 sekunder.
  
![Skærmbillede af indlæsningstid 1,51s.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Det andet skærmbillede viser den samme fil, der er leveret af Microsofts CDN. Denne gang er ventetiden ca. 496 millisekunder. Dette er en stor forbedring og viser, at et helt sekund er barberet ud den samlede tid til at downloade objektet.
  
![Skærmbillede af indlæsningstider på 469 ms.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Er mine data sikre?

Vi sørger for at beskytte de data, der kører din virksomhed. Data, der er gemt i Office 365 CDN, krypteres både under overførsel og inaktive data, og adgang til data i Office 365 SharePoint CDN sikres af Office 365 brugertilladelser og tokenautorisation. Anmodninger om data i Office 365 SharePoint CDN skal henvises til (omdirigeres) fra din Office 365 lejer, ellers genereres der ikke et godkendelsestoken.

For at sikre at dine data forbliver sikre, anbefaler vi, at du aldrig gemmer brugerindhold eller andre følsomme data i en offentlig CDN. Da adgang til data i en offentlig CDN er anonym, bør offentlige CDN'er kun bruges til at hoste generisk indhold, f.eks. webscriptfiler, ikoner, billeder og andre ikke-følsomme aktiver.

> [!NOTE]
> Tredjepartsudbydere af CDN kan have standarder for beskyttelse af personlige oplysninger og overholdelse af angivne standarder, der adskiller sig fra de forpligtelser, der er beskrevet af Office 365 Center for sikkerhed og rettighedsadministration. Data, der cachelagres via CDN-tjenesten, er muligvis ikke i overensstemmelse med Vilkårene for Microsoft-databehandling (DPT) og kan være uden for grænserne for overholdelse af Office 365 Center for sikkerhed og rettighedsadministration.

Du kan finde detaljerede oplysninger om beskyttelse af personlige oplysninger og databeskyttelse for Office 365 CDN udbydere ved at besøge følgende:  

- Få mere at vide om Office 365 beskyttelse af personlige oplysninger og databeskyttelse i [Microsoft Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter)
- Få mere at vide om Akamais beskyttelse af personlige oplysninger og databeskyttelse på [Akamai Center for beskyttelse af personlige oplysninger](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- Få mere at vide om beskyttelse af personlige oplysninger og databeskyttelse i [Azure Trust Center](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Hvordan kan jeg sikre mit netværk med alle disse tredjepartstjenester?

Brug af et omfattende sæt partnertjenester gør det muligt for Office 365 at skalere og opfylde tilgængelighedskravene samt forbedre brugeroplevelsen, når du bruger Office 365. Tredjepartstjenesterne Office 365 udnytter, omfatter både lister over tilbagekaldte certifikater, f.eks. crl.microsoft.com eller sa.symcb.com, og CDN'er, f.eks. r3.res.outlook.com. Hvert CDN FQDN, der genereres af Office 365, er et brugerdefineret FQDN til Office 365. Hvis du sendes til et FQDN på anmodning af Office 365 kan du være sikker på, at den CDN udbyder styrer FQDN og det underliggende indhold på den pågældende placering.
  
For kunder, der ønsker at adskille anmodninger, der er beregnet til et Microsoft- eller Office 365-datacenter, fra anmodninger, der er beregnet til en tredjepart, har vi udarbejdet en vejledning i [administration af Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Er der en liste over alle de FQDN'er, der udnytter CDN'er?

Listen over FQDN'er, og hvordan de udnytter CDN'er ændres over tid. Se vores publicerede [Office 365 URL-adresser og siden MED IP-adresseområder](./urls-and-ip-address-ranges.md) for at få opdaterede oplysninger om de seneste FQDN'er, der udnytter CDN'er.

Du kan også bruge [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md) til at anmode om de aktuelle Office 365 URL-adresser og IP-adresseområder, der er formateret som CSV eller JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kan jeg bruge mine egne CDN og cachelagre indhold på mit lokale netværk?

Vi er hele tiden på udkig efter nye måder at understøtte vores kunders behov på, og vi undersøger i øjeblikket brugen af cachelagringsproxyløsninger og andre lokale CDN løsninger.

Selvom det ikke er en del af Office 365 CDN, kan du også bruge **Azure CDN** til at hoste brugerdefinerede webdele, biblioteker og andre ressourceaktiver, hvilket giver dig mulighed for at anvende adgangsnøgler til dit CDN lager og udøve større kontrol over din CDN konfiguration. Brug af Azure CDN er ikke gratis og kræver et Azure-abonnement. Du kan få flere oplysninger om, hvordan du konfigurerer en Azure CDN instans, i [Hurtig start: Integrer en Azure Storage-konto med Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Jeg bruger Azure ExpressRoute til Office 365. Ændrer det noget?

[Azure ExpressRoute til Office 365](azure-expressroute.md) giver en dedikeret forbindelse til Office 365 infrastruktur, der er adskilt fra det offentlige internet. Det betyder, at klienterne stadig skal oprette forbindelse via forbindelser, der ikke er ExpressRoute, for at oprette forbindelse til CDN'er og anden Microsoft-infrastruktur, som ikke udtrykkeligt er inkluderet på listen over tjenester, der understøttes af ExpressRoute. Du kan finde flere oplysninger om, hvordan du distribuerer specifik trafik, f.eks. anmodninger, der er beregnet til CDN'er, [i Office 365 administration af netværkstrafik](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Kan jeg bruge CDN'er med SharePoint Server i det lokale miljø?

Brug af CDN'er giver kun mening i en SharePoint Online-kontekst og bør undgås med SharePoint Server. Det skyldes, at alle fordelene omkring geografisk placering ikke er sande, hvis serveren er placeret i det lokale miljø eller geografisk tæt på alligevel. Hvis der er netværksforbindelse til de servere, hvor det er hostet, kan webstedet desuden bruges uden en internetforbindelse og kan derfor ikke hente de CDN filer. Ellers skal du bruge en CDN hvis der er en tilgængelig og stabil til det bibliotek og filer, du har brug for til dit websted.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Se også

[principper for Office 365 netværksforbindelser](./microsoft-365-network-connectivity-principles.md)

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](./urls-and-ip-address-ranges.md)

[Brug netværket til levering af Office 365 indhold sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)
