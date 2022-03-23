---
title: Administrere Office 365 slutpunkter
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, Office 365 administrere slutpunkter, så de fungerer sammen med din virksomheds organisations netværksarkitektur.
ms.openlocfilehash: 5d5e51b789ef0336a2e7aaa6a923ca2957ea6edf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591566"
---
# <a name="managing-office-365-endpoints"></a>Administrere Office 365 slutpunkter

De fleste virksomhedsorganisationer, der har flere kontorplaceringer, og en WAN-forbindelse skal konfigureres Office 365 netværksforbindelsen. Du kan optimere dit netværk ved at sende alle pålidelige Office 365 via din firewall og tilsidesætte al yderligere inspektion på pakkeniveau eller behandling. Dette reducerer ventetiden og dine krav til afskærmet kapacitet. At identificere Office 365 netværkstrafik er det første trin i at give optimal ydeevne for dine brugere. Du kan finde flere oplysninger [Office 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md).

Microsoft anbefaler, at du får adgang til Office 365-netværksslutpunkter og løbende ændringer af dem ved hjælp [af Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

Uanset hvordan du administrerer vigtige Office 365 netværkstrafik, kræver Office 365 forbindelse til internettet. Andre netværksslutpunkter, hvor der kræves forbindelse, er angivet på Flere slutpunkter, der [ikke er inkluderet i Office 365 IP-adresse og URL-webtjeneste](additional-office365-ip-addresses-and-urls.md).

Hvordan du bruger Office 365 netværksslutpunkter afhænger af virksomhedens organisations netværksarkitektur. I denne artikel beskrives flere måder, som virksomhedsnetværksarkitektur kan integreres med Office 365 IP-adresser og URL-adresser. Den nemmeste måde at vælge, hvilke netværksanmodninger du skal have tillid til, er at bruge SD-WAN-enheder, der understøtter automatiseret Office 365-konfiguration på hver af dine kontorplaceringer.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SD-WAN til lokalt afdelings udgangspunkt for vigtigt Office 365 netværkstrafik

På hver afdelingsplacering kan du angive en SD-WAN-enhed, der er konfigureret til at dirigere trafik til Office 365 Optimer kategori af slutpunkter eller kategorierne Optimer og Tillad direkte til Microsofts netværk. Andre netværkstrafik, herunder trafik i det lokale datacenter, generel trafik fra websteder på internettet og trafik til Office 365 Standardkategorislutpunkter sendes til en anden placering, hvor du har en mere omfattende netværksperimeter.

Microsoft arbejder med SD-WAN-udbydere for at aktivere automatiseret konfiguration. Du kan finde flere oplysninger [under Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Brug en PAC-fil til direkte routing af vigtige Office 365 trafik

Brug PAC- eller WPAD-filer til at administrere netværksanmodninger, der er knyttet Office 365 men ikke har en IP-adresse. Typiske netværksanmodninger, der sendes via en proxy- eller perimeterenhed, øger ventetiden. Mens SSL-pause og Undersøg opretter den største ventetid, kan andre tjenester som f.eks. proxygodkendelse og opslag af omdømme medføre dårlig ydeevne og en dårlig brugeroplevelse. Desuden skal disse perimeternetværksenheder have tilstrækkelig kapacitet til at behandle alle anmodninger om netværksforbindelse. Vi anbefaler, at du tilsidesætter dine proxy- eller inspektionsenheder til direkte Office 365 netværksanmodninger.
  
[PowerShell Gallery Get-PacFile er et PowerShell-script](https://www.powershellgallery.com/packages/Get-PacFile), der læser de nyeste netværksslutpunkter fra Office 365-ip-adressen og URL-webtjenesten og opretter en PAC-eksempelfil. Du kan redigere scriptet, så det integreres med din eksisterende PAC-filstyring.

![Oprette forbindelse til Office 365 gennem firewalls og proxyer.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figur 1 – Enkel perimeter for virksomhedsnetværk**

PAC-filen installeres i webbrowsere på punkt 1 i Figur 1. Når du bruger en PAC-fil til direkte udgangspunkt for vigtigt Office 365-netværkstrafik, skal du også tillade forbindelse til IP-adresserne bag disse URL-adresser på din netværksperimeterfirewall. Dette gøres ved at hente IP-adresserne for de samme Office 365-slutpunktskategorier som angivet i PAC-filen og oprette firewall-ACL'er baseret på disse adresser. Firewallen er punkt 3 i Figur 1.

Hvis du vælger kun at udføre direkte routing for slutpunkterne i kategorien Optimer, skal alle nødvendige Tillad kategorislutpunkter, som du sender til proxyserveren, angives på proxyserveren for at tilsidesætte yderligere behandling. SSL-pause og Undersøg og Proxygodkendelse er f.eks. ikke kompatible med slutpunkterne i kategorien Optimer og Tillad. Proxyserveren er punkt 2 i Figur 1.

Den almindelige konfiguration er at tillade uden at behandle al udgående trafik fra proxyserveren for destinationens IP-adresser for Office 365 netværkstrafik, der når proxyserveren. Du kan finde oplysninger om problemer med SSL Break og Undersøg i Brug af [tredjepartsnetværksenheder eller løsninger på Office 365 trafik](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Der findes to typer PAC-filer, som Get-PacFile scriptet genererer.

| Type | Beskrivelse |
|:-----|:-----|
|**1** <br/> |Send Optimer slutpunktstrafik direkte og alt andet til proxyserveren. <br/> |
|**2** <br/> |Send Optimer og Tillad slutpunktstrafik direkte og alt andet til proxyserveren. Denne type kan også bruges til at sende al understøttet ExpressRoute til Office 365 til ExpressRoute-netværkssegmenter og alt andet til proxyserveren. <br/> |

Her er et enkelt eksempel på, hvordan du kalder PowerShell-scriptet:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Der er mange parametre, du kan overføre til scriptet:

| Parameter | Beskrivelse |
|:-----|:-----|
|**ClientRequestId** <br/> |Dette er påkrævet og er en GUID, der overføres til den webtjeneste, der repræsenterer den klientmaskine, der foretager opkaldet. <br/> |
|**Forekomst** <br/> |Den Office 365 tjenesteforekomst, der som standard er Worldwide. Dette overføres også til webtjenesten. <br/> |
|**TenantName** <br/> |Dit Office 365 lejernavn. Videregives til webtjenesten og bruges som en parameter, der kan erstattes, i Office 365 URL-adresser. <br/> |
|**Type** <br/> |Den type proxy PAC-fil, der skal genereres. <br/> |

Her er et andet eksempel på, hvordan du kalder PowerShell-scriptet med yderligere parametre:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxyserver tilsidesætter behandling Office 365 netværkstrafik

Hvis PAC-filer ikke bruges til direkte udgående trafik, vil du stadig ignorere behandling på din netværksperimeter ved at konfigurere din proxyserver. Nogle proxyserverleverandører har aktiveret automatiseret konfiguration af dette som beskrevet [i Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md).

Hvis du gør dette manuelt, skal du hente kategoridata fra kategorien Optimer og Tillad slutpunkt fra Office 365-ip-adressen og URL-webtjenesten og konfigurere din proxyserver til at tilsidesætte behandlingen af disse. Det er vigtigt at undgå SSL-pause og Undersøg og proxygodkendelse for slutpunkterne Optimer og Tillad.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Administration af ændringer i Office 365 IP-adresser og URL-adresser

Ud over at vælge passende konfiguration for din netværksperimeter er det vigtigt, at du indfører en proces til styring af ændringer for Office 365 slutpunkter. Disse slutpunkter ændres regelmæssigt, og hvis du ikke administrerer ændringerne, kan du ende med, at brugere er blokeret eller får en dårlig ydeevne, når der er tilføjet en ny IP-adresse eller URL-adresse.

Ændringer af IP Office 365 adresser og URL-adresser publiceres normalt i nærheden af den sidste dag i hver måned. Nogle gange publiceres en ændring uden for tidsplanen pga. drifts-, support- eller sikkerhedskrav.

Når en ændring er blevet offentliggjort, der kræver, at du skal handle, fordi en IP-adresse eller URL-adresse er blevet tilføjet, kan du forvente at modtage 30 dages varsel fra det tidspunkt, vi udgiver ændringen, indtil der er en Office 365-tjeneste på dette slutpunkt. Dette afspejles som Ikrafttrædelsesdato. Selvom vi bestræber os på at bruge denne meddelelsesperiode, er det muligvis ikke altid muligt på grund af drifts-, support- eller sikkerhedskrav. Ændringer, der ikke kræver øjeblikkelig handling for at opretholde forbindelsen, f.eks. fjernede IP-adresser eller URL-adresser eller mindre væsentlige ændringer, inkluderer ikke forhåndsmeddelelse. I disse tilfælde angives ingen ikrafttrædelsesdato. Uanset hvilken meddelelse der er angivet, viser vi den forventede dato for aktiv tjeneste for hver ændring.

### <a name="change-notification-using-the-web-service"></a>Ændringsmeddelelse ved hjælp af webtjenesten

Du kan bruge IP Office 365-adressen og URL-webtjenesten til at få besked om ændringer. Vi anbefaler, at du ringer til webmetoden **/version** én gang i timen for at kontrollere versionen af de slutpunkter, du bruger til at oprette forbindelse til Office 365. Hvis denne version ændres i forhold til den version, du har i brug, så skal du hente de nyeste slutpunktsdata fra webmetoden **/slutpunkter** og eventuelt få forskellene fra **webmetoden /changes** . Det er ikke nødvendigt at ringe til **webmetoderne /slutpunkter** **eller /changes** , hvis der ikke er sket nogen ændringer i den version, du har fundet.

Du kan finde flere oplysninger [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Ændre meddelelse ved hjælp af RSS-feeds

Den Office 365 IP-adresse og URL-webtjeneste indeholder et RSS-feed, du kan abonnere på Outlook. Der er links til RSS-URL-adresserne på hver af de Office 365-tjenesteforekomstspecifikke sider for IP-adresserne og URL-adresserne. Du kan finde flere oplysninger [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Rediger gennemgang af meddelelser og godkendelse v Power Automate

Vi forstår, at du muligvis stadig skal bruge manuel behandling for ændringer af netværksslutpunktet, der kommer igennem hver måned. Du kan bruge Power Automate til at oprette et flow, der giver dig besked via mail, og du kan eventuelt køre en godkendelsesproces for ændringer, Office 365 netværksslutpunkter har ændringer. Når gennemgangen er fuldført, kan du få flowet til automatisk at sende ændringerne til din firewall og dit proxyserveradministrationsteam.

Du kan finde oplysninger Power Automate et eksempel og en skabelon i Brug Power Automate til at modtage en mail om ændringer i [Office 365 IP-adresser og URL-adresser](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 ofte stillede spørgsmål om netværksslutpunkter

Se disse ofte stillede spørgsmål om Office 365 netværksforbindelsen.
  
### <a name="how-do-i-submit-a-question"></a>Hvordan stiller jeg et spørgsmål?

Klik på linket nederst for at angive, om artiklen var nyttig eller ej, og send eventuelle yderligere spørgsmål. Vi overvåger feedbacken og opdaterer spørgsmålene her med de oftest stillede.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Hvordan kan jeg bestemme placeringen af min lejer?

 **Lejerplacering bestemmes** bedst ved hjælp af vores [datacenterkort](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Peerer jeg korrekt med Microsoft?

 **Peeringplaceringer** er beskrevet mere detaljeret i [peering med Microsoft](https://www.microsoft.com/peering).
  
Med mere end 2500 INTERNETUDBYDER-peeringrelationer på verdensplan og 70 punkter for tilstedeværelse bør det være problemfrit at komme fra dit netværk til vores. Det kan ikke skade at bruge et par minutter på at sikre, at din [internetudbyders](/archive/blogs/onthewire/__guidance) peeringrelation er den mest optimale. Her er et par eksempler på gode og ikke så gode peering-hand-offs til vores netværk.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Jeg kan se netværksanmodninger til IP-adresser, der ikke er på den offentliggjorte liste. Skal jeg give adgang til dem?

Vi angiver kun IP-adresser for de Office 365 servere, du skal dirigere direkte til. Dette er ikke en omfattende liste over alle IP-adresser, du vil få vist netværksanmodninger til. Du får vist netværksanmodninger til Microsoft og tredjepartsejede, ikke-publicerede IP-adresser. Disse IP-adresser genereres dynamisk eller administreres på en måde, der forhindrer rettidigt varsel om, at de ændres. Hvis din firewall ikke kan tillade adgang baseret på FQDN'er for disse netværksanmodninger, kan du bruge en PAC- eller WPAD-fil til at administrere anmodningerne.
  
Se en IP, der er knyttet Office 365, som du vil have mere at vide om?
  
1. Kontrollér, om IP-adressen er medtaget i et større publiceret område ved hjælp af en CIDR-lommeregner, f.eks. til [IPv4](https://www.ipaddressguide.com/cidr) [eller IPv6](https://www.ipaddressguide.com/ipv6-cidr). Eksempelvis inkluderer 40.96.0.0/13 IP-adressen 40.103.0.1 på trods af 40.96, der ikke matcher 40.103.
2. Se, om en partner ejer IP-adressen med en [whois-forespørgsel](https://dnsquery.org/). Hvis det ejes af Microsoft, kan det være en intern partner. Mange partnernetværksslutpunkter er angivet som tilhører _standardkategorien_ , hvor IP-adresser ikke publiceres.
3. IP-adressen er muligvis ikke en del Office 365 eller en afhængighed. Office 365 netværksslutpunktpublicering omfatter ikke alle Microsoft-netværksslutpunkter.
4. Kontrollér certifikatet. Med en browser skal du oprette forbindelse til IP-adressen ved hjælp af  *HTTPS://\<IP_ADDRESS\>* og kontrollere de domæner, der er angivet på certifikatet, for at forstå, hvilke domæner der er knyttet til IP-adressen. Hvis det er en IP-adresse, der ejes af Microsoft, og den ikke er på listen over IP-adresser i Office 365, er det sandsynligt, at IP-adressen er knyttet til en Microsoft CDN som *f.eks. MSOCDN.NET* eller et andet Microsoft-domæne uden offentliggjorte IP-oplysninger. Hvis du finder ud af, at domænet på certifikatet er et, hvor vi hævder at vise IP-adressen, skal du kontakte os.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Nogle Office 365 url-adresser peger på CNAME-poster i stedet for A-poster i DNS'en. Hvad har jeg at gøre med CNAME-posterne?

Klientcomputere skal bruge en DNS A- eller AAAA-post, der indeholder en eller flere IP-adresser for at oprette forbindelse til en skytjeneste. Nogle URL-adresser, der Office 365 CNAME-poster i stedet for A- eller AAAA-poster. Disse CNAME-poster er mellemled, og der kan være flere i en kæde. De vil altid med tiden blive løst til en A eller AAAA-post for en IP-adresse. Overvej f.eks. følgende serie af DNS-poster, som i sidste ende løses til _IP-IP_1_:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Disse CNAME-omdirigeringer er en normal del af DNS'en og er gennemsigtige for klientcomputeren og gennemsigtige for proxyservere. De bruges til justering af belastning, netværk, der lever op til indhold, høj tilgængelighed og afhjælpning af tjenestehændelser. Microsoft publicerer ikke de mellemliggende CNAME-poster, de kan ændres når som helst, og du bør ikke skulle konfigurere dem som tilladt på din proxyserver.

En proxyserver validerer den oprindelige URL-adresse, som i eksemplet ovenfor er serviceA.office.com, og denne URL-adresse medtages i Office 365 publicering. Proxyserveren anmoder om DNS-løsning for den pågældende URL-adresse til en IP-adresse og vil modtage IP_1. Den validerer ikke mellemliggende CNAME-omdirigeringsposter.

Hard-coded configurations or using an allowlist based on indirect Office 365 FQDN'er are not recommended, not supported by Microsoft, and are known to cause customer connectivity issues. DNS-løsninger, der blokerer for CNAME-omdirigering, eller som på anden måde fejlagtigt løser Office 365 DNS-poster, kan løses via DNS-videresendere med DNS-rekursion aktiveret eller ved hjælp af DNS-rodtip. Mange tredjepartsnetværksperimeterprodukter integrerer oprindeligt anbefalede Office 365-slutpunkt for at medtage en tilladelsesliste i deres konfiguration ved hjælp af [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Hvorfor kan jeg se navne som f.nsatc.net eller akadns.net i Microsoft-domænenavnene?

Office 365 og Microsoft-tjenester bruger flere tredjepartstjenester som Akamai og MarkMonitor til at forbedre din Office 365 oplevelse. Vi kan ændre disse tjenester i fremtiden for at fortsætte med at give dig den bedst mulige oplevelse. Tredjepartsdomæner kan hoste indhold, f.eks. en CDN, eller de kan hoste en tjeneste, f.eks. en geografisk trafikstyringstjeneste. Nogle af de tjenester, der aktuelt bruges, omfatter:
  
[MarkMonitor bruges](https://www.markmonitor.com/) , når du ser anmodninger, der omfatter  *\*.nsatc.net*. Denne tjeneste giver beskyttelse og overvågning af domænenavne for at beskytte dig mod skadelig opførsel.
  
[ExactTarget bruges](https://www.marketingcloud.com/) , når du ser anmodninger om  *\*.exacttarget.com*. Denne tjeneste giver administration og overvågning af links i mails mod skadelig opførsel.
  
[Akamai er](https://www.akamai.com/) i brug, når du ser anmodninger, der indeholder en af følgende FQDN'er. Denne tjeneste tilbyder geo-DNS og netværkstjenester til levering af indhold.
  
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
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Jeg skal have den mindst mulige forbindelse for Office 365

Da Office 365 er en pakke med tjenester, der er bygget til at fungere via internettet, er løftet om pålidelighed og tilgængelighed baseret på tilgængeligheden af mange almindelige internettjenester. Standardinternettjenester som DNS, CRL og CDN'er skal f.eks. være tilgængelige for at bruge Office 365 på samme måde, som de skal være tilgængelige for at bruge de fleste moderne internettjenester.

Pakken Office 365 opdelt i større tjenesteområder. Disse kan være selektivt aktiveret for forbindelser, og der er et Fælles område, som er en afhængighed for alle og altid er påkrævet.

| Tjenesteområde | Beskrivelse |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online og Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online og OneDrive for Business <br/> |
|**Skype for Business Online og Microsoft Teams** <br/> |Skype for Business og Microsoft Teams <br/> |
|**Almindeligt** <br/> |Office 365 Pro Plus, Office i en browser, Azure AD og andre almindelige netværksslutpunkter <br/> |

Ud over grundlæggende internettjenester er der tredjepartstjenester, der kun bruges til at integrere funktionalitet. Selvom disse er nødvendige til integration, er de markeret som valgfrie i artiklen om Office 365-slutpunkter, hvilket betyder, at kernefunktionaliteten i tjenesten fortsat fungerer, hvis slutpunktet ikke er tilgængeligt. Et hvilket som helst netværksslutpunkt, der er påkrævet, får den påkrævede attribut angivet til sand. Et netværksslutpunkt, der er valgfrit, har den påkrævede attribut angivet til falsk, og attributten Noter angiver de manglende funktioner, du kan forvente, hvis forbindelsen blokeres.
  
Hvis du forsøger at bruge Office 365 og finder tredjepartstjenester ikke er tilgængelige, skal du sikre dig, at alle [FQDN'er](urls-and-ip-address-ranges.md), der er markeret som påkrævede eller valgfrie i denne artikel, er tilladt gennem proxy og firewall.
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Hvordan blokerer jeg adgangen til Microsofts forbrugertjenester?

Funktionen for lejerbegrænsninger understøtter nu blokering af brugen af alle Microsoft-forbrugerprogrammer (MSA-apps), f.eks. OneDrive, Hotmail og Xbox.com. Dette anvender et separat sidehoved login.live.com slutpunktet. Få mere at vide under [Brug lejerbegrænsninger til at administrere adgang til SaaS-skyprogrammer](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Min firewall kræver IP-adresser og kan ikke behandle URL-adresser. Hvordan konfigurerer jeg den til Office 365?

Office 365 ikke IP-adresser for alle nødvendige netværksslutpunkter. Nogle leveres kun som URL-adresser og kategoriseres som standard. URL-adresser i standardkategorien, der er påkrævede, skal være tilladt via en proxyserver. Hvis du ikke har en proxyserver, kan du se, hvordan du har konfigureret webanmodninger for URL-adresser, som brugerne skriver i adresselinjen i en webbrowser. brugeren heller ikke har en IP-adresse. Webadresserne Office 365 standardkategorien, der ikke indeholder IP-adresser, skal konfigureres på samme måde.

## <a name="related-topics"></a>Relaterede emner

[Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md)

[Microsoft Azure IP-intervaller i datacenteret](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Krav til netværksinfrastruktur til Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute og Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)
  
[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Office 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)
