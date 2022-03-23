---
title: Arbejde sammen med en partner om at arkivere tredjepartsdata
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du konfigurerer en brugerdefineret forbindelse til at importere tredjepartsdata fra datakilder som f.eks. Salesforce Chatter, Yahoo Messenger eller Yammer.
ms.openlocfilehash: 53c6cae76327c7a8fb8ca89de464ad8a63e75d6a
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63588728"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Arbejde sammen med en partner om at arkivere tredjepartsdata

Du kan arbejde sammen med en Microsoft-partner om at importere og arkivere data fra en tredjepartsdatakilde for at Microsoft 365. En partner kan give dig en brugerdefineret forbindelse, der er konfigureret til at udtrække elementer fra tredjepartsdatakilden (med jævne mellemrum) og derefter importere disse elementer. Partnerforbindelse konverterer indholdet af et element fra datakilden til et mailformat og gemmer derefter elementerne i postkasserne. Når tredjepartsdata er importeret, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, In-Place Archiving, Auditing og Microsoft 365 opbevaringspolitikker til disse data.

> [!IMPORTANT]
> Løsningen [kommunikationsoverholdelse](communication-compliance.md) i Microsoft 365 kan ikke anvendes på de tredjepartsdata, der importeres af partnerforbindelser, der er nævnt i denne artikel.

Her er en oversigt over processen og de nødvendige trin til at arbejde sammen med en Microsoft-partner om at importere tredjepartsdata.

[Trin 1: Find en tredjepartsdatapartner](#step-1-find-a-third-party-data-partner)

[Trin 2: Opret og konfigurer en tredjepartsdatapostkasse](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[Trin 3: Konfigurer brugerpostkasser til tredjepartsdata](#step-3-configure-user-mailboxes-for-third-party-data)

[Trin 4: Giv din partner oplysninger](#step-4-provide-your-partner-with-information)

[Trin 5: Registrer tredjepartsdataforbindelse i Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Sådan fungerer importprocessen for data fra tredjepart

Følgende illustration og beskrivelse forklarer, hvordan dataimportprocessen fra tredjepart fungerer, når du arbejder med en partner.

![Sådan fungerer importprocessen for data fra tredjepart.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Kunden arbejder sammen med sin valgte partner om at konfigurere en forbindelse, der udtrækker elementer fra tredjepartsdatakilden og derefter importerer disse elementer til Microsoft 365.

2. Partnerforbindelse opretter forbindelse til tredjepartsdatakilder via en tredjeparts-API (på planlagt eller som konfigureret basis) og udtrækker elementer fra datakilden. Partnerforbindelse konverterer indholdet af et element til et mailformat. Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af skemaet for meddelelsesformatet.

3. Partnerforbindelse opretter forbindelse til Azure-tjenesten i Microsoft 365 ved hjælp Exchange webtjeneste (EWS) via et velkendt slutpunkt.

4. Elementer importeres til en bestemt brugers postkasse eller til en "catch-all"-postkasse fra en tredjepart. Om et element importeres til en bestemt brugerpostkasse eller til tredjepartsdatapostkassen, er baseret på følgende kriterier:

   1. **Elementer, der har et bruger-id, der svarer til en brugerkonto:** Hvis partnerforbindelse kan knytte bruger-id'et for elementet i tredjepartsdatakilden til et bestemt bruger-id i Microsoft 365, kopieres elementet til mappen Fjernet i mappen med  genoprettelige elementer. Brugere kan ikke få adgang til elementer i mappen Fjernet. Du kan dog bruge eDiscovery-værktøjer til at søge efter elementer i mappen Fjernet.

   1. **Elementer, der ikke har et bruger-id, der svarer til en brugerkonto:** Hvis partnerforbindelse ikke kan knytte bruger-id'et for et element til et bestemt bruger-id, kopieres elementet til mappen Indbakke  i tredjepartsdatapostkassen. Ved at importere elementer til indbakken kan du eller en anden i organisationen logge på tredjepartspostkassen for at få vist og administrere disse elementer og se, om der skal foretages justeringer i konfigurationen af partnerforbindelser.

## <a name="step-1-find-a-third-party-data-partner"></a>Trin 1: Find en tredjepartsdatapartner

En vigtig komponent til arkivering af tredjepartsdata i Microsoft 365 er at finde og arbejde med en Microsoft-partner, der er specialiserede i at indsamle data fra en tredjepartsdatakilde og importere dem til Microsoft 365. Når dataene er importeret, kan de arkiveres og bevares sammen med din organisations andre Microsoft-data, f.eks. mails fra Exchange og dokumenter fra SharePoint og OneDrive for Business. En partner opretter en forbindelse, der udtrækker data fra organisationens tredjeparts datakilder (f.eks. BlackBerry, Facebook, Google+, Thierarkison Reuters, Twitter og YouTube) og videregiver disse data til en Microsoft 365 API, der importerer elementer til Exchange-postkasser som mails.

De følgende afsnit viser de Microsoft-partnere (og de tredjepartsdatakilder, de understøtter), som deltager i programmet til arkivering af tredjepartsdata i Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[Archive Zip](#archivesocial)

[Veritas](#veritas)

[OpenText](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[17a-4 LLC](https://www.17a-4.com) understøtter følgende tredjepartsdatakilder:

- BlackBerry

- Bloombergs data Strømme

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- MessageLabs-data Strømme

- OpenText

- Oracle/ATG "Klik og ring" Livehjælp

- Pivot IMTRADER

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype for Business (Lync/OCS)

- Skype for Business Online (Lync Online)

- SQL databaser

- Squawker

- Tutoson Reuters Eikon Messenger

### <a name="archivesocial"></a>Archive Zip

[ArchiveArkiv](https://www.archivesocial.com) understøtter følgende tredjepartsdatakilder:

- Facebook

- Flickr

- Eller Ellers

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Veritas](https://www.globanet.com) understøtter følgende tredjepartsdatakilder:

- AOL med Pivot-klient

- BlackBerry-opkaldslogfiler (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry-pinkode (v5, v10, v12)

- BlackBerry-sms(v5, v10, v12)

- Bloomberg-chat

- Bloomberg Mail

- Box

- CipherCloud til Salesforce Chatter

- Cisco IM &amp; Presence Server (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- Brugerdefinerede tekstfiler

- Brugerdefinerede XML-filer

- Facebook (sider)

- Faktasæt

- FXConnect

- ICE-chat/YellowFileet

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive for Business

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Pivot

- Salesforce Chatter

- Skype for Business Online

- Skype for Business, version 2007 R2 - 2016 (lokalt)

- Slæk i virksomhedsgitter

- Ikke-for-store

- Tutoson Reuters Eikon

- Tutoson Reuters Messenger

- Tutoson Reuters Dealings 3000 / FX Trading

- Twitter

- UBS-chat

- YouTube

### <a name="opentext"></a>OpenText

[OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) understøtter følgende tredjepartsdatakilder:

- Akser krypteret

- Akser Exchange

- Det lokale axs-arkiv

- Axs-pladsholder

- Akser signeret

- Bloomberg

- Tutoson Reuters

### <a name="smarsh"></a>Smarsh

[Smarsh](https://www.smarsh.com) understøtter følgende tredjepartsdatakilder:

- AIM

- American American – 2010

- Apple Juice

- AOL med Pivot-klient

- Ares

- Bazaar Voice

- Bear Share

- Bit-strøm

- BlackBerry-opkaldslogfiler (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry-pinkode (v5, v10, v12)

- BlackBerry-sms(v5, v10, v12)

- Bloomberg Mail

- CellTrust

- Chatimport

- Logføring og politik for chat i realtid

- Chatter

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (v8.6.3, v8.6.4, v8.6.5)

- Import af samarbejde

- Logføring af samarbejde i realtid

- Direkte Forbind

- Facebook

- FactSet

- FastTrack

- Gnutella

- Google+

- GoToMyPC

- Hopster

- HubConnex

- IBM Connections (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowFileet

- Chatimport

- Logføring og politik for chat i realtid

- Indii Messenger

- Øjeblikkelig Bloomberg

- IRC

- Jive

- Jive 6 Logføring i realtid (v6, v7)

- Jive-import

- JXTA

- LinkedIn

- Microsoft Lync (2010, 2013)

- MFTP

- Microsoft Lync 2013 Voice

- Microsoft SharePoint (2010, 2013)

- Microsoft Office SharePoint Online

- Microsoft UC (Unified Communications)

- MindAlign

- Mobile Guard

- MSN

- Mit område

- NEONetwork

- Microsoft 365 Lync Dedicated

- Microsoft 365 Delt chat

- Pinterest

- Pivot

- QQ

- Skype for Business 2015

- SoftEther

- Ikke-for-store

- Tutoson Reuters Eikon

- Tutoson Reuters Messenger

- Tor

- TTT

- Twitter

- WinMX

- Winny

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[Verba](https://www.verba.com) understøtter følgende tredjepartsdatakilder:

- Avaya Aura Video

- Avaya Aura Voice

- Avtec Radio

- Proxy/Telex Radio

- BroadSoft-video

- BroadSoft Voice

- Centile Voice

- Cisco Jabber-chat

- Cisco UC-video

- Cisco UC Voice

- Cisco UCCX/UCCE Video

- Cisco UCCX/UCCE Voice

- ESChat-radio

- Geoman Contact Expert

- IP Trade Voice

- LuwareCASS Contact Center

- Microsoft UC (Unified Communications)

- Mitel MiContact Center for Lync (PrairieFyre)

- Video om Oracle/Acme-pakkesessionsgrænsecontroller

- Oracle /Acme Packet Session Border Controller Voice

- Singtel Mobile Voice

- SIPREC-video

-  SIPREC Voice

- Skype for Business/Lync-chat

- Skype for Business/Lync Video

- Skype for Business/Lync Voice

- Speakerbus Voice

- Standardvideo om SIP/H.323

- Standard SIP/H.323 Voice

- Telefonsvarer

- TwistedPair-radio

- Windows på din stationære computer

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>Trin 2: Opret og konfigurer en tredjepartsdatapostkasse i Microsoft 365

Her er trinnene til at oprette og konfigurere en tredjepartsdatapostkasse til import af data Microsoft 365. Som beskrevet tidligere importeres elementer til denne postkasse, hvis partnerforbindelse ikke kan knytte bruger-id'et for elementet til en brugerkonto.

 **Fuldfør disse opgaver i Microsoft 365 Administration**

1. Opret en brugerkonto, og tildel den Exchange Online Plan 2-licens. Se [Føje brugere Microsoft 365](../admin/add-users/add-users.md). En Plan 2-licens er påkrævet for at placere postkassen i retslig venteposition eller aktivere en arkivpostkasse, der har en lagerkvote på op til 1,5 TB.

2. Føj brugerkontoen for tredjepartsdatapostkassen til **Exchange administratorrolle** i Microsoft 365. Se Tildel [administratorroller Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > Skriv legitimationsoplysningerne for denne brugerkonto ned. Du skal levere dem til din partner, sådan som det er beskrevet i trin 4.

 **Fuldfør disse opgaver Exchange Administration**

1. Skjul tredjepartsdatapostkassen fra adressekartoteket og andre adresselister i organisationen. se [Administrere brugerpostkasser](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Alternativt kan du køre følgende PowerShell-kommando:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Tildele **FullAccess-tilladelse** til tredjepartsdatapostkassen, så administratorer eller overholdelsesmedarbejdere kan åbne tredjepartsdatapostkassen i Outlook-skrivebordsklienten. Se Administrer tilladelser [for modtagere](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Aktivér følgende kompatibilitetsrelaterede funktioner for tredjepartsdatapostkassen:

    - Aktivere arkivpostkassen. Se [Aktivér arkivpostkasser](enable-archive-mailboxes.md) [og Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md). Dette giver dig mulighed for at frigøre lagerplads i den primære postkasse ved at konfigurere en arkiveringspolitik, der flytter dataelementer fra tredjeparter til arkivpostkassen. Dette giver dig op til 1,5 TB lagerplads til tredjepartsdata.

    - Placer tredjepartsdatapostkassen i Retslig venteposition. Du kan også anvende Microsoft 365 opbevaringspolitik i Security and Compliance Center. Hvis du sætter denne postkasse i venteposition, bevares tredjepartsdataelementer (på ubestemt tid eller i en bestemt periode) og forhindrer dem i at blive slettet fra postkassen. Se et af følgende emner:

      - [Placer en postkasse i retslig venteposition](./create-a-litigation-hold.md)

      - [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md)

    - Aktivér logføring af postkassekontrol for ejer-, stedfortræder- og administratoradgang til tredjepartsdatapostkassen. se [Aktivér postkasserevision](enable-mailbox-auditing.md). Dette giver dig mulighed for at overvåge alle aktiviteter, der udføres af enhver bruger, der har adgang til tredjepartsdatapostkassen.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>Trin 3: Konfigurer brugerpostkasser til tredjepartsdata

Næste trin er at konfigurere brugerpostkasser til at understøtte tredjepartsdata. Udfør disse opgaver ved hjælp <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration eller</a> ved hjælp af de tilsvarende Windows PowerShell cmdlet'er.

1. Aktivér arkivpostkassen for hver bruger. Se [Aktivér arkivpostkasser](enable-archive-mailboxes.md) [og Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md).

2. Placer brugerpostkasser i retslig tilbageholdelse, eller anvend Microsoft 365 opbevaringspolitik. Se et af følgende emner:

    - [Placer en postkasse i retslig venteposition](./create-a-litigation-hold.md)

    - [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md)

    Som det er blevet nævnt tidligere, kan du, når du sætter postkasser i venteposition, angive en varighed for, hvor lang tid elementer skal opbevares fra tredjepartsdatakilden, eller du kan vælge at sætte elementer i venteposition på ubestemt tid.

## <a name="step-4-provide-your-partner-with-information"></a>Trin 4: Giv din partner oplysninger

Det sidste trin er at give din partner følgende oplysninger, så de kan konfigurere forbindelsen til at oprette forbindelse til din organisation for at importere data til brugerpostkasser og til tredjepartsdatapostkassen.

- Slutpunktet, der bruges til at oprette forbindelse til Azure-tjenesten Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- Logonlegitimationsoplysninger (Microsoft 365 bruger-id og adgangskode) for den tredjepartsdatapostkasse, du oprettede i trin 2. Disse legitimationsoplysninger er påkrævede, så partnerforbindelse kan få adgang til og importere elementer til brugerpostkasser og til tredjepartsdatapostkassen.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>Trin 5: Registrer tredjepartsdataforbindelse i Azure Active Directory

Fra d. 30. september 2018 begynder Azure-tjenesten i Microsoft 365 at bruge moderne godkendelse i Exchange Online til at godkende tredjepartsdataforbindelser, der forsøger at oprette forbindelse til din organisation for at importere data. Årsagen til denne ændring er, at moderne godkendelse giver mere sikkerhed end den aktuelle metode, som var baseret på en tilladelsesliste for forbindelser fra tredjeparter, der bruger det tidligere beskrevne slutpunkt til at oprette forbindelse til Azure-tjenesten.

Hvis du vil aktivere en tredjepartsdataforbindelse til at oprette forbindelse til Microsoft 365 ved hjælp af den nye moderne godkendelsesmetode, skal en administrator i organisationen acceptere at registrere forbindelsen som et tjenesteprogram, der er tillid til, i Azure Active Directory. Dette gøres ved at acceptere en anmodning om tilladelse til at give forbindelsen adgang til din organisations data i Azure Active Directory. Når du har accepteret denne anmodning, tilføjes tredjepartsdataforbindelse som et virksomhedsprogram til Azure Active Directory og repræsenteres som tjenesteinspektør. Du kan finde flere oplysninger om samtykkeprocessen under  [Samtykke for lejeradministrator](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Her er trinnene til at få adgang til og acceptere anmodningen om at registrere forbindelsen:

1. Gå til [denne side](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) , og log på med legitimationsoplysningerne fra en global administrator.

   Følgende dialogboks vises. Du kan udvide indrykningen for at se de tilladelser, der bliver tildelt forbindelsen.

   ![Dialogboksen for anmodning om tilladelser vises.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. Klik **på Acceptér**.

Når du har accepteret anmodningen, [vises Azure-portalen](https://portal.azure.com) . Hvis du vil have vist listen over programmer for organisationen, skal du **klikke Azure Active Directory** >  **Enterprise-programmer**. Dataforbindelse Microsoft 365 tredjepartsdataforbindelse er angivet på **Enterprise-program bladet**.

> [!IMPORTANT]
> Efter d. 30. september 2018 importeres tredjepartsdata ikke længere til postkasser i organisationen, hvis du ikke registrerer en tredjepartsdataforbindelse i Azure Active Directory. Bemærk, at eksisterende tredjepartsdataforbindelser (dem, der er oprettet før d. 30. september 2018) også skal registreres i Azure Active Directory ved at følge fremgangsmåden i trin 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Tilbagekalde samtykke for en tredjepartsdataforbindelse

Når din organisation har accepteret anmodningen om tilladelse til at registrere en tredjepartsdataforbindelse i Azure Active Directory, kan din organisation til enhver tid tilbagekalde dette samtykke. Tilbagekaldelse af samtykket for en forbindelse betyder dog, at data fra tredjepartsdatakilden ikke længere importeres Microsoft 365.

Hvis du vil tilbagekalde samtykket for en tredjepartsdataforbindelse, kan du slette programmet (ved at slette den tilsvarende tjenesteprincipal) fra Azure Active Directory ved hjælp af **Enterprise-program** bladet i Azure-portalen eller ved at bruge [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) i Microsoft 365 PowerShell. Du kan også bruge [Remove-AzureADServicePrincipal-cmdlet'en](/powershell/module/azuread/remove-azureadserviceprincipal) i Azure Active Directory PowerShell.

## <a name="more-information"></a>Flere oplysninger

- Som beskrevet tidligere importeres elementer fra tredjeparts datakilder til Exchange postkasser som mails. Partnerforbindelse importerer elementet ved hjælp af et skema, der kræves af Microsoft 365 API. I følgende tabel beskrives meddelelsesegenskaberne for et element fra en tredjepartsdatakilde, når det er importeret til en Exchange-postkasse som en mailmeddelelse. Tabellen angiver også, om meddelelsesegenskaben er obligatorisk. Obligatoriske egenskaber skal udfyldes. Hvis et element mangler en obligatorisk egenskab, importeres det ikke til Microsoft 365. Importprocessen returnerer en fejlmeddelelse, der forklarer, hvorfor et element ikke blev importeret, og hvilken egenskab der mangler.<br/><br/>

    |**Meddelelsesegenskab**|**Obligatorisk?**|**Beskrivelse**|**Eksempelværdi**|
    |:-----|:-----|:-----|:-----|
    |**FROM** <br/> |Ja  <br/> |Den bruger, der oprindeligt oprettede eller sendte elementet i tredjepartsdatakilden. Partnerforbindelse forsøger at knytte bruger-id'et fra kildeelementet (f.eks. et Twitter-håndtag) til en brugerkonto for alle deltagere (brugere i felterne FRA og TIL). Der importeres en kopi af meddelelsen til hver deltagers postkasse. Hvis ingen af deltagerne fra elementet kan knyttes til en brugerkonto, importeres elementet til tredjepartsarkivpostkassen i Microsoft 365.  <br/> <br/> Den deltager, der er identificeret som afsenderen af elementet, skal have en aktiv postkasse i organisationen, som elementet importeres til. Hvis afsenderen ikke har en aktiv postkasse, returneres følgende fejl:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**TO** <br/> |Ja  <br/> |Den bruger, der har modtaget et element, hvis det er relevant for et element i datakilden.  <br/> | `bob@contoso.com` <br/> |
    |**SUBJECT** <br/> |Nej  <br/> |Emnet fra kildeelementet.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**DATO** <br/> |Ja  <br/> |Den dato, hvor elementet oprindeligt blev oprettet eller slået op i kundens datakilde. Det kunne f.eks. være den dato, hvor en Twitter-besked blev tweetet.  <br/> | `01 NOV 2015` <br/> |
    |**BRØDTEKST** <br/> |Nej  <br/> |Indholdet af meddelelsen eller indlægget. For nogle datakilder kan indholdet af denne egenskab være det samme som indholdet af egenskaben **SUBJECT** . Under importen forsøger partnerforbindelse at bevare fuld gengivelse fra indholdskilden som muligt. Hvis det er muligt, er filer, grafik eller andet indhold fra brødteksten i kildeelementet inkluderet i denne egenskab. Ellers er indhold fra kildeelementet inkluderet i egenskaben **VEDHÆFTET** FIL. Indholdet af denne egenskab afhænger af partnerforbindelse og af egenskaberne for kildeplatformen.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**VEDHÆFTET FIL** <br/> |Nej  <br/> |Hvis et element i datakilden (f.eks. et tweet på Twitter eller en chatsamtale) har en vedhæftet fil eller medtager billeder, vil partneren, der opretter forbindelse, først forsøge at medtage vedhæftede filer i egenskaben **BRØDTEKST.** Hvis det ikke er muligt, føjes den til egenskaben ** VEDHÆFTET FIL **. Andre eksempler på vedhæftede filer omfatter Synes godt om-synes godt om i Facebook, metadata fra indholdskilden og svar på en meddelelse eller et indlæg.  <br/> | `image.gif` <br/> |
    |**MEDDELELSESKLASSE** <br/> |Ja  <br/> | Dette er en egenskab med flere værdier, som oprettes og udfyldes af en partnerforbindelse. Formatet for denne egenskab er  `IPM.NOTE.Source.Event`. (Denne egenskab skal starte med  `IPM.NOTE`. Dette format svarer til formatet for meddelelsesklassen  `IPM.NOTE.X` ). Denne egenskab indeholder følgende oplysninger:  <br/><br/>`Source`: Angiver tredjepartsdatakilden; Twitter, Facebook eller BlackBerry.  <br/> <br/>  `Event`: Angiver typen af aktivitet, der blev udført i den tredjepartsdatakilde, der fremstillede elementerne; eksempelvis et tweet på Twitter eller et indlæg på Facebook. Hændelser er specifikke for datakilden.  <br/> <br/>  Et formål med denne egenskab er at filtrere bestemte elementer baseret på datakilden, hvor et element stammer fra, eller baseret på typen af hændelse. I en eDiscovery-søgning kan du f.eks. oprette en søgeforespørgsel for at finde alle de tweets, der blev skrevet af en bestemt bruger.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- Når elementer importeres til postkasser i Microsoft 365, returneres entydig identifier til den, der ringer op, som en del af HTTP-svaret. Denne identifikator  `x-IngestionCorrelationID`, kaldet , kan bruges til efterfølgende fejlfindingsformål af partnere til en ende-til-ende-sporing af elementer. Det anbefales, at partnere registrerer disse oplysninger og logger dem derefter ved deres afslutning. Her er et eksempel på et HTTP-svar, der viser denne identifikator:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Du kan bruge værktøjet Indholdssøgning i Sikkerheds- og overholdelsescenter til at søge efter elementer, der er blevet importeret til postkasser fra en tredjepartsdatakilde. Hvis du vil søge specifikt efter disse importerede elementer, kan du bruge følgende par med egenskabsværdier for meddelelser i nøgleordsfeltet for en indholdssøgning.

  - **`kind:externaldata`**: Brug dette par med egenskabsværdier til at søge i alle tredjepartsdatatyper. Hvis du f.eks. vil søge efter elementer, der er importeret fra en datakilde fra en tredjepart og indeholdt ordet "contoso" i egenskaben Emne for det importerede element, skal du bruge nøgleordsforespørgslen  `kind:externaldata AND subject:contoso`.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: Brug dette par med egenskabsværdier til kun at søge efter en bestemt type tredjepartsdata. Hvis du f.eks. kun vil søge efter Facebook-data, der indeholder ordet "contoso" i egenskaben Emne, skal du bruge nøgleordsforespørgslen  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`.

  Du kan finde en komplet liste over værdier, der skal bruges til tredjepartsdatatyper for `itemclass` egenskaben, under Brug indholdssøgning til at søge efter [tredjepartsdata](use-content-search-to-search-third-party-data-that-was-imported.md), der blev importeret til Microsoft 365.

   Du kan finde flere oplysninger om brug af indholdssøgning og oprettelse af søgeforespørgsler om nøgleord i:

  - [Indholdssøgning](content-search.md)

  - [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)