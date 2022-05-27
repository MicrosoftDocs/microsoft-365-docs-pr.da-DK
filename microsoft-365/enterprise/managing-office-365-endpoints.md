---
title: Administrere Office 365-slutpunkter
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/18/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Få mere at vide om, hvordan du administrerer Office 365 slutpunkter, så de fungerer sammen med netværksarkitekturen i din virksomhed.
ms.openlocfilehash: c32b44365a8c926e398e4441b6b50905ea77147d
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753820"
---
# <a name="managing-office-365-endpoints"></a>Administrere Office 365-slutpunkter

De fleste virksomhedsorganisationer, der har flere kontorplaceringer og et WAN, der opretter forbindelse, skal konfigureres for Office 365 netværksforbindelse. Du kan optimere dit netværk ved at sende alle Office 365 netværksanmodninger, der er tillid til, direkte gennem firewallen og omgå al ekstra kontrol eller behandling på pakkeniveau. Dette reducerer ventetiden og kravene til perimeterkapaciteten. Identificering af Office 365 netværkstrafik er det første skridt til at sikre optimal ydeevne for dine brugere. Du kan få flere oplysninger [under principper for Office 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md).

Microsoft anbefaler, at du får adgang til Office 365 netværksslutpunkter og igangværende ændringer af dem ved hjælp af [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

Uanset hvordan du administrerer vigtig Office 365 netværkstrafik, kræver Office 365 internetforbindelse. Andre netværksslutpunkter, hvor der kræves forbindelse, er angivet under [Flere slutpunkter, der ikke er inkluderet i Office 365 IP-adresse og URL-webtjeneste](additional-office365-ip-addresses-and-urls.md).

Den måde, du bruger Office 365 netværksslutpunkter på, afhænger af virksomhedens netværksarkitektur. I denne artikel beskrives flere måder, som virksomhedsnetværksarkitekturer kan integreres med Office 365 IP-adresser og URL-adresser. Den nemmeste måde at vælge, hvilke netværksanmodninger du har tillid til, er at bruge SD-WAN-enheder, der understøtter automatiseret Office 365 konfiguration på hver af dine kontorplaceringer.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SD-WAN for lokal forgreningsudgang af vital Office 365 netværkstrafik

På hver placering på forgreningskontorerne kan du angive en SD-WAN-enhed, der er konfigureret til at dirigere trafik til Office 365 optimere kategori af slutpunkter eller optimer og tillad kategorier direkte til Microsofts netværk. Anden netværkstrafik, herunder datacentertrafik i det lokale miljø, generel trafik på websteder og trafik til Office 365 Standardkategorislutpunkter sendes til en anden placering, hvor du har en mere omfattende netværksperimeter.

Microsoft arbejder sammen med SD-WAN-udbydere om at aktivere automatiseret konfiguration. Du kan få flere oplysninger under [Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Brug en PAC-fil til direkte routing af vigtig Office 365 trafik

Brug PAC- eller WPAD-filer til at administrere netværksanmodninger, der er knyttet til Office 365, men som ikke har en IP-adresse. Typiske netværksanmodninger, der sendes via en proxy- eller perimeterenhed, øger ventetiden. Mens SSL Break og Inspect opretter den største ventetid, kan andre tjenester, f.eks. proxygodkendelse og omdømmeopslag, medføre dårlig ydeevne og en dårlig brugeroplevelse. Derudover skal disse perimeternetværksenheder have tilstrækkelig kapacitet til at behandle alle anmodninger om netværksforbindelse. Vi anbefaler, at du tilsidesætter dine proxy- eller kontrolenheder til direkte Office 365 netværksanmodninger.
  
[PowerShell Gallery Get-PacFile er et PowerShell-script](https://www.powershellgallery.com/packages/Get-PacFile), der læser de nyeste netværksslutpunkter fra Office 365 IP-adresse og URL-webtjeneste og opretter en eksempel-PAC-fil. Du kan ændre scriptet, så det kan integreres med din eksisterende PAC-filadministration.

> [!NOTE]
> Du kan finde flere oplysninger om overvejelser om sikkerhed og ydeevne i forbindelse med direkte forbindelse til Office 365 slutpunkter under [principper for Office 365 Network Connectivity](microsoft-365-network-connectivity-principles.md).

![Oprettelse af forbindelse til Office 365 via firewalls og proxyer.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figur 1 – Simpel netværksperimeter til virksomheder**

PAC-filen installeres i webbrowsere på punkt 1 i Figur 1. Når du bruger en PAC-fil til direkte udgående Office 365 netværkstrafik, skal du også tillade forbindelse til IP-adresserne bag disse URL-adresser på din firewall for netværksperimeter. Dette gøres ved at hente IP-adresserne for de samme Office 365 slutpunktskategorier som angivet i PAC-filen og oprette firewall-ACL'er baseret på disse adresser. Firewallen er punkt 3 i Figur 1.

Hvis du vælger kun at udføre direkte routing for kategorislutpunkterne Optimer, skal alle påkrævede Tillad kategorislutpunkter, som du sender til proxyserveren, vises på proxyserveren for at tilsidesætte yderligere behandling. SSL-afbrydelse og Inspektions- og Proxygodkendelse er f.eks. ikke kompatible med både slutpunkterne Optimer og Tillad kategori. Proxyserveren er punkt 2 i Figur 1.

Den almindelige konfiguration er at tillade uden at behandle al udgående trafik fra proxyserveren for destinations-IP-adresserne for Office 365 netværkstrafik, der rammer proxyserveren. Du kan finde oplysninger om problemer med SSL Break og Inspect under [Brug af netværksenheder eller løsninger fra tredjepart på Office 365 trafik](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Der er to typer PAC-filer, som Get-PacFile scriptet genererer.

| Type | Beskrivelse |
|:-----|:-----|
|**1** <br/> |Send Optimer slutpunktstrafik direkte og alt andet til proxyserveren. <br/> |
|**2** <br/> |Send Optimer og Tillad direkte trafik for slutpunkter og alt andet til proxyserveren. Denne type kan også bruges til at sende alle understøttede ExpressRoute for Office 365 trafik til ExpressRoute-netværkssegmenter og alt andet til proxyserveren. <br/> |

Her er et simpelt eksempel på kald af PowerShell-scriptet:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Der er mange parametre, du kan overføre til scriptet:

| Parameter | Beskrivelse |
|:-----|:-----|
|**ClientRequestId** <br/> |Dette er påkrævet, og er et GUID, der overføres til webtjenesten, som repræsenterer den klientcomputer, der foretager opkaldet. <br/> |
|**Eksempel** <br/> |Den Office 365 tjenesteforekomst, der som standard er Verdensomspændende. Dette overføres også til webtjenesten. <br/> |
|**Lejernavn** <br/> |Dit Office 365 lejernavn. Overføres til webtjenesten og bruges som en erstatningsparameter i nogle Office 365 URL-adresser. <br/> |
|**Type** <br/> |Den proxy-PAC-filtype, du vil generere. <br/> |

Her er et andet eksempel på at kalde PowerShell-scriptet med yderligere parametre:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxyserveren tilsidesætter behandlingen af Office 365 netværkstrafik

Hvis PAC-filer ikke bruges til direkte udgående trafik, vil du stadig omgå behandlingen af netværksperimeteren ved at konfigurere proxyserveren. Nogle proxyserverleverandører har aktiveret automatisk konfiguration af dette som beskrevet i [Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md).

Hvis du gør dette manuelt, skal du hente kategoridataene Optimer og Tillad slutpunkt fra Office 365 IP-adresse og URL-webtjeneste og konfigurere proxyserveren til at tilsidesætte behandlingen af disse. Det er vigtigt at undgå SSL Break- og Inspect- og Proxy Authentication for kategorislutpunkterne Optimer og Tillad.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Ændringsstyring for Office 365 IP-adresser og URL-adresser

Ud over at vælge en passende konfiguration for din netværksperimeter er det vigtigt, at du anvender en proces til administration af ændringer for Office 365 slutpunkter. Disse slutpunkter ændres regelmæssigt, og hvis du ikke administrerer ændringerne, kan du ende med at få brugere blokeret eller med dårlig ydeevne, når en ny IP-adresse eller URL-adresse er tilføjet.

Ændringer af Office 365 IP-adresser og URL-adresser udgives normalt nær den sidste dag i hver måned. Nogle gange udgives en ændring uden for denne tidsplan på grund af driftsmæssige, support- eller sikkerhedskrav.

Når der publiceres en ændring, der kræver, at du handler, fordi der er tilføjet en IP-adresse eller URL-adresse, bør du forvente at modtage 30 dages varsel fra det tidspunkt, hvor vi publicerer ændringen, indtil der er en Office 365 tjeneste på det pågældende slutpunkt. Dette afspejles som ikrafttrædelsesdatoen. Selvom vi tilstræber denne meddelelsesperiode, er det muligvis ikke altid muligt på grund af driftsmæssige, support- eller sikkerhedskrav. Ændringer, der ikke kræver øjeblikkelig handling for at opretholde forbindelsen, f.eks. fjernede IP-adresser eller URL-adresser eller mindre betydelige ændringer, omfatter ikke forhåndsmeddelelse. I disse tilfælde angives der ingen ikrafttrædelsesdato. Uanset hvilken meddelelse der er angivet, angiver vi den forventede aktive tjenestedato for hver ændring.

### <a name="change-notification-using-the-web-service"></a>Skift meddelelse ved hjælp af webtjenesten

Du kan bruge Office 365 IP-adresse og URL-webtjeneste til at få besked om ændringer. Vi anbefaler, at du kalder webmetoden **/version** én gang i timen for at kontrollere versionen af de slutpunkter, du bruger til at oprette forbindelse til Office 365. Hvis denne version ændres sammenlignet med den version, du har i brug, skal du hente de nyeste slutpunktsdata fra webmetoden **/endpoints** og eventuelt hente forskellene fra webmetoden **/changes** . Det er ikke nødvendigt at kalde **webmetoderne /endpoints** eller **/changes** , hvis der ikke har været nogen ændring af den version, du har fundet.

Du kan finde flere oplysninger [under Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Skift meddelelse ved hjælp af RSS-kilder

Den Office 365 IP-adresse og URL-webtjeneste leverer et RSS-feed, som du kan abonnere på i Outlook. Der er links til RSS-URL-adresserne på hver af de Office 365 tjenesteforekomstspecifikke sider for IP-adresserne og URL-adresserne. Du kan finde flere oplysninger [under Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Rediger gennemgangen af meddelelser og godkendelser ved hjælp af Power Automate

Vi er klar over, at du muligvis stadig har brug for manuel behandling af ændringer af netværksslutpunkter, der foretages hver måned. Du kan bruge Power Automate til at oprette et flow, der giver dig besked via mail og eventuelt kører en godkendelsesproces for ændringer, når Office 365 netværksslutpunkter har ændringer. Når gennemgangen er fuldført, kan du få flowet til automatisk at sende ændringerne til firewall- og proxyserveradministrationsteamet via mail.

Du kan finde oplysninger om et Power Automate eksempel og en skabelon under [Brug Power Automate til at modtage en mail for at få ændringer i Office 365 IP-adresser og URL-adresser](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Ofte stillede spørgsmål om Office 365 netværksslutpunkter

Se disse ofte stillede spørgsmål om Office 365 netværksforbindelse.
  
### <a name="how-do-i-submit-a-question"></a>Hvordan gør jeg sende et spørgsmål?

Klik på linket nederst for at angive, om artiklen var nyttig eller ej, og send eventuelle yderligere spørgsmål. Vi overvåger feedbacken og opdaterer spørgsmålene her med de oftest stillede.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Hvordan gør jeg bestemme min lejers placering?

 **Lejerens placering** bestemmes bedst ved hjælp af vores [datacenterkort](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Er jeg peering passende med Microsoft?

 **Peeringplaceringer** er beskrevet mere detaljeret i [peering med Microsoft](https://www.microsoft.com/peering).
  
Med over 2500 ISP-peering-relationer globalt og 70 punkters tilstedeværelse bør det være problemfrit at komme fra dit netværk til vores. Det kan ikke skade at bruge et par minutter på at sikre, at internetudbyderens peering-relation er den mest optimale. [Her er nogle eksempler på](/archive/blogs/onthewire/__guidance) gode og ikke så gode peering-afleveringer til vores netværk.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Jeg kan se netværksanmodninger til IP-adresser, der ikke er på den publicerede liste. Skal jeg give adgang til dem?

Vi angiver kun IP-adresser for de Office 365 servere, du skal distribuere direkte til. Dette er ikke en omfattende liste over alle de IP-adresser, du får vist netværksanmodninger for. Du får vist netværksanmodninger til Microsoft og tredjepartsejede, ikke-publicerede IP-adresser. Disse IP-adresser genereres eller administreres dynamisk på en måde, der forhindrer rettidig varsel, når de ændres. Hvis din firewall ikke kan tillade adgang baseret på FQDN'er for disse netværksanmodninger, skal du bruge en PAC- eller WPAD-fil til at administrere anmodningerne.
  
Se en IP-adresse, der er knyttet til Office 365, som du vil have flere oplysninger om?
  
1. Kontrollér, om IP-adressen er inkluderet i et større udgivet område ved hjælp af en CIDR-beregner, f.eks. disse for [IPv4](https://www.ipaddressguide.com/cidr) eller [IPv6](https://www.ipaddressguide.com/ipv6-cidr). 40.96.0.0/13 inkluderer f.eks. IP-adressen 40.103.0.1, selvom 40.96 ikke stemmer overens med 40.103.
2. Se, om en partner ejer IP-adressen med en [whois-forespørgsel](https://dnsquery.org/). Hvis microsoft ejes, kan det være en intern partner. Mange partnernetværksslutpunkter er angivet som hører til _standardkategorien_ , hvor IP-adresser ikke publiceres.
3. IP-adressen må ikke være en del af Office 365 eller en afhængighed. Office 365 publicering af netværksslutpunkter indeholder ikke alle Microsoft-netværksslutpunkter.
4. Kontrollér certifikatet. Med en browser kan du oprette forbindelse til IP-adressen ved hjælp  *af HTTPS://\<IP_ADDRESS\>* og kontrollere de domæner, der er angivet på certifikatet, for at forstå, hvilke domæner der er knyttet til IP-adressen. Hvis det er en Microsoft-ejet IP-adresse og ikke er på listen over Office 365 IP-adresser, er det sandsynligt, at IP-adressen er knyttet til en Microsoft-CDN, f.eks *. MSOCDN.NET* eller et andet Microsoft-domæne uden publicerede IP-oplysninger. Hvis du finder domænet på certifikatet er et, hvor vi hævder at angive IP-adressen, skal du fortælle os det.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Nogle Office 365 URL-adresser peger på CNAME-poster i stedet for A-poster i DNS. Hvad har jeg at gøre med CNAME-posterne?

Klientcomputere skal bruge en DNS A- eller AAAA-post, der indeholder en eller flere IP-adresser, for at oprette forbindelse til en cloudtjeneste. Nogle URL-adresser, der er inkluderet i Office 365 viser CNAME-poster i stedet for A- eller AAAA-poster. Disse CNAME-poster er mellemliggende, og der kan være flere i en kæde. De vil altid med tiden løse til en A- eller AAAA-post for en IP-adresse. Overvej f.eks. følgende serie DNS-poster, der i sidste ende fortolkes som IP-adressen _IP_1_:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Disse CNAME-omdirigeringer er en normal del af DNS og er gennemsigtige for klientcomputeren og gennemsigtige for proxyservere. De bruges til belastningsjustering, netværk til levering af indhold, høj tilgængelighed og afhjælpning af tjenestehændelser. Microsoft publicerer ikke de mellemliggende CNAME-poster, de kan ændres når som helst, og du skal ikke konfigurere dem som tilladt på din proxyserver.

En proxyserver validerer den oprindelige URL-adresse, som i ovenstående eksempel er serviceA.office.com, og denne URL-adresse medtages i Office 365 publicering. Proxyserveren anmoder om DNS-opløsning for den pågældende URL-adresse til en IP-adresse og modtager IP_1 igen. Den validerer ikke de mellemliggende CNAME-omdirigeringsposter.

Hard-coded konfigurationer eller brug af en allowlist baseret på indirekte Office 365 FQDN'er anbefales ikke, understøttes ikke af Microsoft og er kendt for at forårsage problemer med kundeforbindelsen. DNS-løsninger, der blokerer ved CNAME-omdirigering, eller som på anden måde fejlagtigt fortolker Office 365 DNS-poster, kan løses via DNS-videresendere med AKTIVERET DNS-rekursion eller ved hjælp af DNS-rodtip. Mange perimeterprodukter fra tredjepart integrerer oprindeligt det anbefalede Office 365 slutpunkt for at inkludere en allowlist i deres konfiguration ved hjælp af [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Hvorfor kan jeg se navne som nsatc.net eller akadns.net i Microsofts domænenavne?

Office 365 og andre Microsoft-tjenester bruge flere tredjepartstjenester som Akamai og MarkMonitor til at forbedre din Office 365 oplevelse. For fortsat at give dig den bedst mulige oplevelse kan vi ændre disse tjenester i fremtiden. Tredjepartsdomæner kan være vært for indhold, f.eks. en CDN, eller de kan hoste en tjeneste, f.eks. en geografisk trafikstyringstjeneste. Nogle af de tjenester, der aktuelt er i brug, omfatter:
  
[MarkMonitor](https://www.markmonitor.com/) er i brug, når du får vist anmodninger, der indeholder  *\*.nsatc.net*. Denne tjeneste yder beskyttelse mod domænenavne og overvågning for at beskytte mod skadelig adfærd.
  
[ExactTarget](https://www.marketingcloud.com/) bruges, når du får vist anmodninger til  *\*.exacttarget.com*. Denne tjeneste leverer administration af maillink og overvågning mod skadelig adfærd.
  
[Akamai](https://www.akamai.com/) er i brug, når du får vist anmodninger, der indeholder en af følgende FQDN'er. Denne tjeneste tilbyder geo-DNS og netværkstjenester til levering af indhold.
  
```console
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Jeg skal have den mindste forbindelse, der er mulig for Office 365

Da Office 365 er en pakke af tjenester, der er bygget til at fungere via internettet, er løfterne om pålidelighed og tilgængelighed baseret på, at mange standard internettjenester er tilgængelige. Standardinternettjenester som DNS, CRL og CDN'er skal f.eks. være tilgængelige for at bruge Office 365 ligesom de skal være tilgængelige for at bruge de fleste moderne internettjenester.

Office 365-pakken er opdelt i større serviceområder. Disse kan selektivt aktiveres til forbindelse, og der er et fælles område, som er en afhængighed for alle, og som altid er påkrævet.

| Tjenesteområde | Beskrivelse |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online og Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online og OneDrive for Business <br/> |
|**Skype for Business Online og Microsoft Teams** <br/> |Skype for Business og Microsoft Teams <br/> |
|**Fælles** <br/> |Office 365 Pro Plus, Office i en browser, Azure AD og andre almindelige netværksslutpunkter <br/> |

Ud over grundlæggende internettjenester er der tredjepartstjenester, der kun bruges til at integrere funktionalitet. Selvom disse er nødvendige til integration, er de markeret som valgfrie i artiklen om Office 365 slutpunkter, hvilket betyder, at kernefunktionaliteten i tjenesten fortsat fungerer, hvis slutpunktet ikke er tilgængeligt. Alle netværksslutpunkter, der er påkrævet, har den påkrævede attribut angivet til sand. Alle netværksslutpunkter, der er valgfrie, har den påkrævede attribut angivet til falsk, og noteattributten indeholder oplysninger om den manglende funktionalitet, du bør forvente, hvis forbindelsen blokeres.
  
Hvis du forsøger at bruge Office 365 og finder tredjepartstjenester, der ikke er tilgængelige, skal du sikre dig, at [alle FQDN'er, der er markeret som obligatoriske eller valgfrie i denne artikel, er tilladt via proxyen og firewallen](urls-and-ip-address-ranges.md).
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Hvordan gør jeg blokere adgangen til Microsofts forbrugertjenester?

Funktionen med lejerbegrænsninger understøtter nu blokering af brugen af alle Microsoft-forbrugerprogrammer (MSA-apps), f.eks. OneDrive, Hotmail og Xbox.com. Dette bruger en separat overskrift til login.live.com slutpunkt. Du kan få flere oplysninger under [Brug lejerbegrænsninger til at administrere adgang til SaaS-cloudprogrammer](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>

### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Min firewall kræver IP-adresser og kan ikke behandle URL-adresser. Hvordan gør jeg konfigurere den til Office 365?

Office 365 angiver ikke IP-adresser på alle nødvendige netværksslutpunkter. Nogle er kun angivet som URL-adresser og er kategoriseret som standard. URL-adresser i standardkategorien, der kræves, skal tillades via en proxyserver. Hvis du ikke har en proxyserver, kan du se, hvordan du har konfigureret webanmodninger for URL-adresser, som brugerne skriver i adresselinjen i en webbrowser. Brugeren angiver heller ikke en IP-adresse. De Office 365 standardkategori-URL-adresser, der ikke indeholder IP-adresser, skal konfigureres på samme måde.

## <a name="related-topics"></a>Relaterede emner

[Office 365 IP-adresse og URL-adressewebtjeneste](microsoft-365-ip-web-service.md)

[IP-intervaller for Microsoft Azure datacenter](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Offentlige IP fra Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Krav til netværksinfrastruktur for Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute og Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)
  
[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[principper for Office 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)
