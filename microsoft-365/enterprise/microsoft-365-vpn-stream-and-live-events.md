---
title: Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer
ms.openlocfilehash: eb2e57b844f06bc3b1e005aa1095794b176bba94
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705255"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Du kan få et overblik over, hvordan du bruger VPN-opdelte forbindelser til at optimere Microsoft 365 forbindelse for eksterne brugere, under [Oversigt: VPN-opdelt Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Hvis du vil have detaljeret vejledning til implementering af VPN-opdeling, skal du [se Implementering af VPN-opdeling for at Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdeling af VPN i Almindelige [scenarier for vpnopdelning af Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde en vejledning til sikring Teams medietrafik i VPN-opdelte netværksmiljøer under Sikring [Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md).
>- Du kan finde oplysninger om optimering Microsoft 365 globale lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for Brugere i Kina](microsoft-365-networking-china.md).

Microsoft 365 Live Events-trafik (dette omfatter deltagere til Teams-fremstillede livebegivenheder og dem, der produceres med en ekstern koder via Teams, Stream eller Yammer), og Stream-trafik efter behov kategoriseres i øjeblikket som Standard versus Optimer i [URL/IP-listen for](urls-and-ip-address-ranges.md) tjenesten.  Disse slutpunkter kategoriseres som Standard **,** fordi de er hostet på CDN'er, der også kan bruges af andre tjenester. Kunder foretrækker generelt at proxyere denne type trafik og anvende eventuelle sikkerhedselementer, der normalt udføres på slutpunkter som disse.

Mange kunder har bedt om URL-/IP-data, der skal bruges til at forbinde deres brugere til Stream/Live Events direkte fra deres lokale internetforbindelse, i stedet for at dirigere trafik med høj volumen og ventetid via VPN-infrastrukturen. Dette er typisk ikke muligt uden både dedikerede navneområder og nøjagtige IP-oplysninger for slutpunkterne, som ikke er angivet for Microsoft 365 slutpunkter kategoriseret som **Standard**.

Brug følgende trin til at aktivere direkte forbindelse for Stream/Live Events-tjenesten fra klienter, der bruger et gennemtvunget VPN. Denne løsning er beregnet til at give kunderne mulighed for at undgå routing af Live Events-trafik via VPN, mens der er høj netværkstrafik på grund af arbejdsscenarier fra hjemmet. Hvis det er muligt, anbefales det at få adgang til tjenesten via en undersøger proxy.

>[!NOTE]
>Ved hjælp af denne løsning kan der være tjenesteelementer, der ikke løser de angivne IP-adresser og dermed krydser VPN, men den store mængde trafik som f.eks. streamingdata bør. Der kan være andre elementer uden for omfanget af Live Events/Stream, som bliver taget af denne aflastning, men disse bør være begrænset, da de skal opfylde både FQDN _og_ IP-matchet, før de går direkte.

>[!IMPORTANT]
>Kunder rådes til at afveje risikoen ved at sende mere trafik, der tilsidesætter VPN'et over ydeevnens forstærkning for Live-begivenheder.

Hvis du vil implementere den gennemtvungne Teams for Livebegivenheder og Stream, skal følgende trin anvendes:

## <a name="1-configure-external-dns-resolution"></a>1. Konfigurer ekstern DNS-opløsning

Klienter skal have ekstern, rekursiv DNS-opløsning for at være tilgængelig, så følgende værtsnavne kan løses til IP-adresser.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** bruges til Stream-begivenheder ([Konfigurer kodere til livestreaming i Microsoft Stream – Microsoft Stream | Microsoft-dokumenter](/stream/live-encoder-setup)).

**\*.media.azure.net** **\*og .bmc.cdn.office.net** bruges til Teams-fremstillede Live-begivenheder (Hurtig start-begivenheder, RTMP-In understøttede begivenheder [Roadmap-id 84960]), der er planlagt fra Teams-klienten.

 Nogle af disse slutpunkter deles med andre elementer uden for Stream/Live Events. Det anbefales ikke, at du kun bruger disse FQDN'er til at konfigurere VPN-offload, selvom det er teknisk muligt i din VPN-løsning (f.eks. hvis det virker på FQDN i stedet for IP).

FQDN'er er ikke påkrævet i VPN-konfigurationen. De er kun til brug i PAC-filer sammen med IP'erne for at sende den relevante trafik direkte.

## <a name="2-implement-pac-file-changes-where-required"></a>2. Implementer PAC-filændringer (hvor det er nødvendigt)

For organisationer, der bruger en PAC-fil til at dirigere trafik gennem en proxy, mens du er på VPN, opnås dette normalt ved hjælp af FQDN'er. Men med Stream/Live Events indeholder de værtsnavne, der er angivet, **\*** jokertegn som f.eks. .azureedge.net, som også omfatter andre elementer, hvor det ikke er muligt at angive fulde IP-lister. Hvis anmodningen sendes direkte baseret på DNS-jokertegn alene, blokeres trafik til disse slutpunkter, da der ikke er nogen rute via den direkte sti til den i trin [3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) senere i denne artikel.

For at løse dette kan vi angive følgende IP-adresser og bruge dem sammen med værtsnavnene i en PAC-eksempelfil som beskrevet [i trin 1](#1-configure-external-dns-resolution). PAC-filen kontrollerer, om URL-adressen svarer til dem, der bruges til Stream/Live-begivenheder, og hvis den gør, kontrollerer den også, om den IP, der returneres fra et DNS-opslag, svarer til dem, der er angivet for tjenesten. Hvis _begge_ matcher, dirigeres trafikken direkte. Hvis et af de to elementer (FQDN/IP) ikke stemmer overens, sendes trafikken til proxyen. Som resultat sikrer konfigurationen, at alt, hvad der løses til en IP uden for omfanget af både IP og definerede navneområder, vil krydse proxyen via VPN som normalt.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Indsamling af de aktuelle CDN slutpunkter

Live Events bruger flere CDN til at streame til kunder for at levere den bedst mulige dækning, kvalitet og fleksibilitet. I øjeblikket bruges Azure CDN fra Microsoft og fra Verizon. Over tid kan dette ændres på grund af situationer som f.eks. regional tilgængelighed. Denne artikel er en kilde, der giver dig mulighed for at holde dig opdateret om IP-områder.

For Azure CDN fra Microsoft kan du hente listen fra [Download Azure IP Ranges and Service Tags – Public Cloud fra Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=56519) – du skal søge specifikt efter tjenestemærket *AzureFrontdoor.Frontend* i JSON; *addressPrefixes* viser undernet i IPv4/IPv6. Med tiden kan IP'erne ændre sig, men listen over tjenestemærkater opdateres altid, før de bruges.

Hvis Azure CDN fra Verizon (Edgecast), [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) kan du finde en komplet liste ved hjælp af (klik på **Prøv det )** – du skal søge specifikt efter sektionen **Premium\_ Verizon**. Bemærk, at denne API viser alle Edgecast-IP'er (oprindelse og Anycast). Der er i øjeblikket ikke en mekanisme, som API'en kan bruge til at skelne mellem oprindelse og Anycast.

For at implementere dette i en PAC-fil kan du bruge følgende eksempel, som sender Microsoft 365 Optimer trafik direkte (hvilket anbefales bedste fremgangsmåde) via FQDN og den kritiske Stream/Live Events-trafik direkte via en kombination af FQDN og den returnerede IP-adresse. Pladsholdernavnet _Contoso_ skal redigeres til navnet på din specifikke lejer, hvor _contoso_ er fra contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>Eksempel på PAC-fil

Her er et eksempel på, hvordan PAC-filerne genereres:

1. Gem scriptet nedenfor på din lokale harddisk som _Get-TLEPacFile.ps1_.
1. Gå til [Verizon-webadressen,](/rest/api/cdn/edge-nodes/list#code-try-0) og download den resulterende JSON (kopiér den ind i en fil som cdnedgenodes.json)
1. Sæt filen i den samme mappe som scriptet.
1. I et PowerShell-vindue skal du køre følgende kommando. Udskift lejernavnet til noget andet, hvis du ønsker SPO-URL-adresserne. Dette er Type 2, så **Optimer** **og Tillad** (Type 1 er kun Optimer).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Filen TLE.pac indeholder alle navneområder og IP'er (IPv4/IPv6).

##### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Scriptet fortolker automatisk Azure-listen baseret på [download-URL-adressen](https://www.microsoft.com/download/details.aspx?id=56519) og nøgler fra **AzureFrontDoor.Frontend**, så der er ingen grund til at hente den manuelt.

Igen anbefales det ikke at udføre VPN-aflastning kun ved hjælp af FQDN'er; brug af **både** FQDN'er og IP-adresserne i funktionen hjælper med at begrænse brugen af denne aflæsning til et begrænset sæt slutpunkter, herunder Live Events/Stream. Den måde, funktionen er struktureret på, medfører, at der udføres et DNS-opslag for det FQDN, der svarer direkte til dem, der er angivet af klienten, dvs. DNS-opløsningen for de resterende navneområder er uændret.

Hvis du vil begrænse risikoen for at aflaste slutpunkter, der ikke er relateret til Live Events and Stream, **\*** kan du fjerne .azureedge.net-domænet fra konfigurationen, som er det sted, hvor de fleste af denne risiko ligger, da dette er et delt domæne, der bruges til alle Azure CDN-kunder. Bagsiden af dette er, at enhver begivenhed, der bruger en ekstern kodningsenhed, ikke optimeres, men begivenheder, der produceres/organiseres i Teams bliver.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Konfigurer routing på VPN for at aktivere direkte udgangspunkt

Det sidste trin er at tilføje en direkte rute for de Live Event IP'er, der er beskrevet under Indsamling af de aktuelle lister **over CDN-slutpunkter** i VPN-konfigurationen for at sikre, at trafikken ikke sendes via den tvungne strøm ind i VPN. Detaljerede oplysninger om, hvordan du gør dette for Microsoft 365 Optimer slutpunkter, kan findes i afsnittet [Implementer](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) VPN-opdelingsopdelning i Implementering af [VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md). Processen er præcis den samme for stream-/livehændelses-IP'er, der er angivet i dette dokument.

Bemærk, at det kun er IP'er (ikke FQDN'er), der indsamler de aktuelle [lister over CDN-slutpunkter](#gathering-the-current-lists-of-cdn-endpoints), der skal bruges til VPN-konfiguration.

## <a name="faq"></a>Ofte stillede spørgsmål

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Vil dette sende al min trafik til tjenesten direkte?

Nej, dette sender den latenstidsfølsomme streamingtrafik til en direkte Live Event eller Stream-video, al anden trafik fortsætter med at bruge VPN-vpnet, hvis de ikke løser sig til de IP'er, der er publiceret.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Skal jeg bruge IPv6-adresserne?

Nej, forbindelsen kan kun være IPv4, hvis det er nødvendigt.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Hvorfor publiceres disse IP'er ikke i Microsoft 365 URL-adresse/IP-tjeneste?

Microsoft har strenge kontroller vedrørende formatet og typen af oplysninger, der er i tjenesten, for at sikre, at kunderne kan bruge oplysningerne pålideligt til at implementere sikker og optimal routing baseret på slutpunktskategorien.

Kategorien **Standardslutpunkt** indeholder ingen IP-oplysninger af mange årsager (Standardslutpunkter kan være uden for Microsofts kontrol, kan ændres for ofte eller kan være i blokke, der deles med andre elementer). Derfor er Standardslutpunkter designet til at blive sendt via FQDN til en undersøgende proxy, f.eks. normal webtrafik.

I dette tilfælde er de ovenstående slutpunkter CDN'er, der kan bruges af andre elementer, der ikke er Microsoft-kontrollerede end Live Events eller Stream, og dermed betyder afsendelse af trafik direkte også alt andet, der løser sig til disse IP'er, sendes også direkte fra klienten. På grund af den aktuelle globale krises unikke karakter og vores kunders kortvarige behov har Microsoft leveret oplysningerne ovenfor, så kunderne kan bruge dem, som de ønsker.

Microsoft arbejder på at omkonfigurere slutpunkterne for Live Events, så de fremover bliver inkluderet i kategorierne Tillad/optimer slutpunkt.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Skal jeg kun tillade adgang til disse IP'er?

Nej, adgang til alle de **påkrævede** markerede slutpunkter i [URL-/IP-tjenesten](urls-and-ip-address-ranges.md) er afgørende for, at tjenesten kan fungere. Desuden kræves et valgfrit slutpunkt, der er markeret for Stream (id 41-45).

### <a name="what-scenarios-will-this-advice-cover"></a>Hvilke scenarier dækker dette råd?

1. Livebegivenheder, der er produceret i Teams app
2. Visning af stream hostet indhold
3. Eksterne enheds (encoder) fremstillede hændelser

### <a name="does-this-advice-cover-presenter-traffic"></a>Dækker dette råd trafik for præsentationsværter?

Det gælder ikke, ovenstående råd gælder kun for dem, der forbruger tjenesten. Når du præsenterer inde fra Teams, kan du se præsentationsværtens trafikflow til afsnittet Optimer markerede UDP-slutpunkter i URL/IP-tjenesterække 11 med detaljeret vejledning om VPN-aflastning, der er beskrevet i afsnittet [Om](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) opdelte VPN-netværksopdetaling i Implementering af [VPN opdelt Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Risikerer denne konfiguration anden trafik end Live Events &amp; Stream, der sendes direkte?

Ja, på grund af delte FQDN'er, der bruges til nogle elementer i tjenesten, kan du ikke undgå dette. Denne trafik sendes normalt via virksomhedens proxy, som kan anvende inspektion. I et VPN-opdelt scenario, hvor der bruges både FQDN'er og IP'er, begrænses risikoen til et minimum, men den vil stadig eksistere. Kunder kan fjerne **domænet .azureedge.net fra konfigurationen af offloaden og reducere risikoen til et minimum, men dette fjerner afbelastningen af Stream-understøttede livebegivenheder (Teams-planlagte, eksterne kodningshændelser, Yammer hændelser, der er produceret i Teams, Yammer-planlagte eksterne koderbegivenheder og Stream planlagte begivenheder eller visning efter behov fra Stream).\*** Hændelser, der planlægges og Teams i et møde, påvirkes ikke.

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdeling af Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier for opdeling af VPN-Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sikring Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md)

[Microsoft 365 optimering af ydeevnen for Kinas brugere](microsoft-365-networking-china.md)

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier for fjernarbejde (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: brug Windows 10 VPN-profiler til at tillade automatiske til-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
