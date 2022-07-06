---
title: Arbejd sammen med en partner om at arkivere tredjepartsdata
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du konfigurerer en brugerdefineret connector til import af tredjepartsdata fra datakilder som Salesforce Chatter, Yahoo Messenger eller Yammer.
ms.openlocfilehash: 7b66c16da344a0254ecbc704311c6de5fe92c232
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637811"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Arbejd sammen med en partner om at arkivere tredjepartsdata

Du kan arbejde sammen med en Microsoft-partner om at importere og arkivere data fra en tredjepartsdatakilde til Microsoft 365. En partner kan give dig en brugerdefineret connector, der er konfigureret til at udtrække elementer fra tredjepartsdatakilden (regelmæssigt) og derefter importere disse elementer. Partnerconnectoren konverterer indholdet af et element fra datakilden til et mailformat og gemmer derefter elementerne i postkasser. Når data fra tredjepart er importeret, kan du anvende Microsoft Purview-funktioner som Litigation Hold, eDiscovery, In-Place Arkivering, Overvågning og Microsoft 365-opbevaringspolitikker på disse data.

> [!IMPORTANT]
> Løsningen [til overholdelse af angivne standarder for kommunikation](communication-compliance.md) i Microsoft 365 kan ikke anvendes på de tredjepartsdata, der importeres af partnerconnectors, som er nævnt i denne artikel.

Her er en oversigt over processen og de trin, der er nødvendige for at arbejde sammen med en Microsoft-partner om at importere tredjepartsdata.

[Trin 1: Find en tredjepartsdatapartner](#step-1-find-a-third-party-data-partner)

[Trin 2: Opret og konfigurer en datapostkasse fra tredjepart](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[Trin 3: Konfigurer brugerpostkasser til tredjepartsdata](#step-3-configure-user-mailboxes-for-third-party-data)

[Trin 4: Giv din partner oplysninger](#step-4-provide-your-partner-with-information)

[Trin 5: Registrer dataconnectoren fra tredjepart i Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Sådan fungerer dataimportprocessen fra tredjepart

Følgende illustration og beskrivelse beskriver, hvordan dataimportprocessen fra tredjepart fungerer, når du arbejder med en partner.

![Sådan fungerer dataimportprocessen fra tredjepart.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Kunden arbejder sammen med sin valgte partner om at konfigurere en connector, der udtrækker elementer fra tredjepartsdatakilden og derefter importerer disse elementer til Microsoft 365.

2. Partnerconnectoren opretter forbindelse til datakilder fra tredjepart via en API fra tredjepart (planlagt eller som konfigureret) og udtrækker elementer fra datakilden. Partnerconnectoren konverterer indholdet af et element til et mailformat. Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af skemaet i meddelelsesformat.

3. Partnerconnectoren opretter forbindelse til Azure-tjenesten i Microsoft 365 ved hjælp af Exchange Web Service (EWS) via et velkendt slutpunkt.

4. Elementer importeres til en bestemt brugers postkasse eller til en datapostkasse fra tredjepart, der "fanger alle". Om et element importeres til en bestemt brugerpostkasse eller til en datapostkasse fra tredjepart, er baseret på følgende kriterier:

   1. **Elementer med et bruger-id, der svarer til en brugerkonto:** Hvis partnerconnectoren kan knytte bruger-id'et for elementet i datakilden fra tredjepart til et bestemt bruger-id i Microsoft 365, kopieres elementet til mappen **Renser** i brugerens mappe Gendanbare elementer. Brugerne kan ikke få adgang til elementer i mappen Renser. Du kan dog bruge eDiscovery-værktøjer til at søge efter elementer i mappen Ryd op.

   1. **Elementer, der ikke har et bruger-id, der svarer til en brugerkonto:** Hvis partnerconnectoren ikke kan knytte bruger-id'et for et element til et bestemt bruger-id, kopieres elementet til mappen **Indbakke** i datapostkassen fra tredjepart. Import af elementer til indbakken gør det muligt for dig eller en person i din organisation at logge på tredjepartspostkassen for at få vist og administrere disse elementer og se, om der skal foretages ændringer i partnerconnectorkonfigurationen.

## <a name="step-1-find-a-third-party-data-partner"></a>Trin 1: Find en tredjepartsdatapartner

En vigtig komponent til arkivering af tredjepartsdata i Microsoft 365 er at finde og arbejde sammen med en Microsoft-partner, der er specialiseret i hentning af data fra en datakilde fra tredjepart og import af dem til Microsoft 365. Når dataene er importeret, kan de arkiveres og bevares sammen med din organisations andre Microsoft-data, f.eks. mail fra Exchange og dokumenter fra SharePoint og OneDrive for Business. En partner opretter en connector, der udtrækker data fra din organisations tredjepartsdatakilder (f.eks. BlackBerry, Facebook, Google+, Thomson Reuters, Twitter og YouTube), og overfører disse data til en Microsoft 365-API, der importerer elementer til Exchange-postkasser som mailmeddelelser.

I følgende afsnit vises de Microsoft-partnere (og de datakilder fra tredjepart, de understøtter), der deltager i programmet til arkivering af tredjepartsdata i Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[ArkivSocial](#archivesocial)

[Veritas](#veritas)

[Åbn tekst](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[17a-4 LLC](https://www.17a-4.com) understøtter følgende tredjepartsdatakilder:

- Blackberry

- Bloomberg-datastrømme

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- MessageLabs Data Streams

- Åbn tekst

- Oracle/ATG 'click-to-call' Live Hjælp

- PivotER IMTRADER

- Microsoft SharePoint

- MindAlign

- Sitrion One (nyhedstager)

- Skype for Business (Lync/OCS)

- Skype for Business Online (Lync Online)

- SQL-databaser

- Squawker

- Thomson Reuters Eikon Messenger

### <a name="archivesocial"></a>ArkivSocial

[ArchiveSocial](https://www.archivesocial.com) understøtter følgende datakilder fra tredjepart:

- Facebook

- Flickr

- Instagram

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Veritas](https://www.globanet.com) understøtter følgende datakilder fra tredjepart:

- AOL med pivotklient

- BlackBerry-opkaldslogge (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN-kode (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Chat

- Bloomberg Mail

- Boksen

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

- ICE Chat/YellowJacket

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive for Business

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Pivot

- Salesforce-snak

- Skype for Business Online

- Skype for Business, version 2007 R2 – 2016 (i det lokale miljø)

- Slack - virksomhedsgitter

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Thomson Reuters Dealings 3000 / FX Trading

- Twitter

- UBS-chat

- YouTube

### <a name="opentext"></a>Åbn tekst

[OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) understøtter følgende datakilder fra tredjepart:

- Akser krypteret

- Udveksling af akser

- Akser lokalt arkiv

- Øksepladsholder

- Akser signeret

- Bloomberg

- Thomson Reuters

### <a name="smarsh"></a>Smarsh

[Smarsh](https://www.smarsh.com) understøtter følgende datakilder fra tredjepart:

- MÅL

- American Idol

- Æblejuice

- AOL med Pivot-klient

- Ares

- Basarstemme

- Bæreandel

- Bit-skydstrøm

- BlackBerry-opkaldslogge (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN-kode (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Mail

- CellTrust

- Chatimport

- Logføring og politik for chat i realtid

- Snak

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (v8.6.3, v8.6.4, v8.6.5)

- Import af samarbejde

- Logføring af samarbejde i realtid

- Direkte forbindelse

- Facebook

- FactSet

- Fasttrack

- Gnutella

- Google+

- Gå tilMitPC

- Hopster

- HubConnex

- IBM-forbindelser (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Kommuniker 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowJacket

- Import af chat

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

- Delt chatbesked til Microsoft 365

- Pinterest

- Pivot

- QQ

- Skype for Business 2015

- Blødere

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Tor

- TTT

- Twitter

- Winmx

- Winny

- Yahoo

- Yammer

- YouTube

### <a name="verba"></a>Verba

[Verba](https://www.verba.com) understøtter følgende datakilder fra tredjepart:

- Avaya Aura Video

- Avaya Aura Voice

- Avtec Radio

- Bosch/Telex Radio

- BroadSoft-video

- BroadSoft-stemme

- Centile stemme

- Cisco Jabber IM

- Cisco UC Video

- Cisco UC-stemme

- Cisco UCCX/UCCE Video

- Cisco UCCX/UCCE Voice

- ESChat-radio

- Geoman-kontaktekspert

- IP Trade Voice

- Luware LUCS Kontaktcenter

- Microsoft UC (Unified Communications)

- Mitel MiContact Center for Lync (prairieFyre)

- Video om Oracle/Acme Packet Session Border Controller

- Oracle/Acme Packet Session Border Controller Voice

- Singtel Mobile Voice

- SIPREC-video

-  SIPREC-stemme

- Skype for Business/Lync-chat

- Skype for Business/Lync-video

- Skype for Business/Lync-stemme

- Speakerbus-stemme

- Standard SIP/H.323 Video

- Standard SIP/H.323 Voice

- Truphone-stemme

- TwistedPair Radio

- Windows-skrivebordscomputerskærm

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>Trin 2: Opret og konfigurer en datapostkasse fra tredjepart i Microsoft 365

Her er trinnene til oprettelse og konfiguration af en tredjepartsdatapostkasse til import af data til Microsoft 365. Som tidligere forklaret, importeres elementer til denne postkasse, hvis partnerconnectoren ikke kan knytte bruger-id'et for elementet til en brugerkonto.

### <a name="complete-these-tasks-in-the-microsoft-365-admin-center"></a>Udfør disse opgaver i Microsoft 365 Administration

1. Opret en brugerkonto, og tildel den en Exchange Online Plan 2-licens. Se [Føj brugere til Microsoft 365](../admin/add-users/add-users.md). Der kræves en Plan 2-licens for at placere postkassen i litigation-venteposition eller aktivere en arkivpostkasse, der har en lagerkvote på op til 1,5 TB.

2. Føj brugerkontoen for tredjepartsdatapostkassen til administratorrollen **Exchange** i Microsoft 365. se [Tildel administratorroller i Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > Skriv legitimationsoplysningerne for denne brugerkonto ned. Du skal give dem til din partner, som beskrevet i trin 4.

### <a name="complete-these-tasks-in-the-exchange-admin-center"></a>Udfør disse opgaver i Exchange Administration

1. Skjul datapostkassen fra tredjepart fra adressekartoteket og andre adresselister i din organisation. se [Administrer brugerpostkasser](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Du kan også køre følgende [Exchange Online PowerShell-kommando](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Tildel **FullAccess-tilladelsen** til tredjepartsdatapostkassen, så administratorer eller overholdelsesansvarlige kan åbne datapostkassen fra tredjepart i Outlook Desktop-klienten. se [Administrer tilladelser for modtagere](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Aktivér følgende funktioner, der er relateret til overholdelse af angivne standarder, for tredjepartsdatapostkassen:

    - Aktivér arkivpostkassen. se [Aktivér arkivpostkasser](enable-archive-mailboxes.md) og [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md). Det giver dig mulighed for at frigøre lagerplads i den primære postkasse ved at konfigurere en arkivpolitik, der flytter dataelementer fra tredjepart til arkivpostkassen. Dette giver dig op til 1,5 TB lagerplads til tredjepartsdata.

    - Placer datapostkassen fra tredjepart i procesventeposition. Du kan også anvende en Microsoft 365-opbevaringspolitik i Security and Compliance Center. Hvis denne postkasse sættes i venteposition, bevares tredjepartsdataelementer (på ubestemt tid eller i en bestemt varighed) og forhindrer, at de fjernes fra postkassen. Se et af følgende emner:

      - [Placer en postkasse i venteposition for procesførelse](./create-a-litigation-hold.md)

      - [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)

    - Aktivér logføring af overvågning af postkasse for ejer-, stedfortræder- og administratoradgang til tredjepartsdatapostkassen. se [Aktivér overvågning af postkasse](enable-mailbox-auditing.md). Dette giver dig mulighed for at overvåge alle aktiviteter, der udføres af alle brugere, der har adgang til tredjepartsdatapostkassen.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>Trin 3: Konfigurer brugerpostkasser til tredjepartsdata

Det næste trin er at konfigurere brugerpostkasser til at understøtte tredjepartsdata. Udfør disse opgaver ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> eller ved hjælp af de tilsvarende cmdlet'er.

1. Aktivér arkivpostkassen for hver bruger. se [Aktivér arkivpostkasser](enable-archive-mailboxes.md) og [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).

2. Placer brugerpostkasser i retslig venteposition, eller anvend en Microsoft 365-opbevaringspolitik. se et af følgende emner:

    - [Placer en postkasse i venteposition for procesførelse](./create-a-litigation-hold.md)

    - [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md)

    Når du placerer postkasser i venteposition, kan du som tidligere nævnt angive en varighed for, hvor længe elementer fra datakilden fra tredjepart skal opbevares, eller du kan vælge at opbevare elementer på ubestemt tid.

## <a name="step-4-provide-your-partner-with-information"></a>Trin 4: Giv din partner oplysninger

Det sidste trin er at give din partner følgende oplysninger, så de kan konfigurere connectoren til at oprette forbindelse til din organisation for at importere data til brugerpostkasser og til datapostkassen fra tredjepart.

- Det slutpunkt, der bruges til at oprette forbindelse til Azure-tjenesten i Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- Logonlegitimationsoplysninger (Bruger-id og adgangskode til Microsoft 365) for den datapostkasse fra tredjepart, du oprettede i trin 2. Disse legitimationsoplysninger er påkrævet, så partnerconnectoren kan få adgang til og importere elementer til brugerpostkasser og til tredjepartsdatapostkassen.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>Trin 5: Registrer dataconnectoren fra tredjepart i Azure Active Directory

Fra og med den 30. september 2018 begynder Azure-tjenesten i Microsoft 365 at bruge moderne godkendelse i Exchange Online til at godkende tredjepartsdataconnectors, der forsøger at oprette forbindelse til din organisation for at importere data. Årsagen til denne ændring er, at moderne godkendelse giver mere sikkerhed end den aktuelle metode, som var baseret på en liste over tilladte forbindelser for tredjepartsconnectorer, der bruger det tidligere beskrevne slutpunkt til at oprette forbindelse til Azure-tjenesten.

Hvis en dataconnector fra tredjepart skal kunne oprette forbindelse til Microsoft 365 ved hjælp af den nye moderne godkendelsesmetode, skal en administrator i din organisation give samtykke til at registrere connectoren som et tjenesteprogram, der er tillid til, i Azure Active Directory. Dette gøres ved at acceptere en anmodning om tilladelse for at give connectoren adgang til din organisations data i Azure Active Directory. Når du har accepteret denne anmodning, tilføjes dataconnectoren fra tredjepart som et virksomhedsprogram til Azure Active Directory og repræsenteres som en tjenesteprincipal. Du kan få flere oplysninger om samtykkeprocessen under [Lejer Administration Samtykke](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Her er trinnene til at få adgang til og acceptere anmodningen om at registrere connectoren:

1. Gå til [denne side](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) , og log på med legitimationsoplysningerne for en global administrator.

   Følgende dialogboks vises. Du kan udvide bilsættene for at gennemse de tilladelser, der tildeles til connectoren.

   ![Dialogboksen med anmodning om tilladelser vises.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. Klik på **Acceptér**.

Når du har accepteret anmodningen, vises [Azure Portal](https://portal.azure.com). Hvis du vil have vist listen over programmer for din organisation, skal du klikke på **Azure Active Directory** > **Enterprise-programmer**. Dataconnectoren fra tredjepart til Microsoft 365 er angivet på bladet **Virksomhedsprogrammer** .

> [!IMPORTANT]
> Efter den 30. september 2018 importeres tredjepartsdata ikke længere i postkasser i din organisation, hvis du ikke registrerer en dataconnector fra tredjepart i Azure Active Directory. Bemærk, at eksisterende dataconnectors fra tredjepart (dem, der er oprettet før den 30. september 2018) også skal registreres i Azure Active Directory ved at følge proceduren i trin 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Tilbagekalder samtykke til en dataconnector fra tredjepart

Når din organisation har givet samtykke til anmodningen om tilladelse til at registrere en dataconnector fra tredjepart i Azure Active Directory, kan din organisation tilbagekalde dette samtykke når som helst. Hvis du tilbagekalder samtykket for en connector, betyder det dog, at data fra tredjepartsdatakilden ikke længere importeres til Microsoft 365.

Hvis du vil tilbagekalde samtykket for en dataconnector fra tredjepart, kan du slette programmet (ved at slette den tilsvarende tjenesteprincipal) fra Azure Active Directory ved hjælp af bladet **Virksomhedsprogrammer** i Azure Portal eller ved hjælp af [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) i Microsoft 365 PowerShell. Du kan også bruge cmdlet'en [Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) i Azure Active Directory PowerShell.

## <a name="more-information"></a>Flere oplysninger

- Som tidligere forklaret importeres elementer fra datakilder fra tredjepart til Exchange-postkasser som mailmeddelelser. Partnerconnectoren importerer elementet ved hjælp af et skema, der kræves af Microsoft 365 API. I følgende tabel beskrives meddelelsesegenskaberne for et element fra en datakilde fra en tredjepart, når det er importeret til en Exchange-postkasse som en mail. Tabellen angiver også, om meddelelsesegenskaben er obligatorisk. Obligatoriske egenskaber skal udfyldes. Hvis et element mangler en obligatorisk egenskab, importeres det ikke til Microsoft 365. Importprocessen returnerer en fejlmeddelelse, der forklarer, hvorfor et element ikke blev importeret, og hvilken egenskab der mangler.

  |Meddelelsesegenskab|Obligatorisk?|Beskrivelse|Eksempelværdi|
  |---|---|---|---|
  |**FRA**|Ja|Den bruger, der oprindeligt oprettede eller sendte elementet i datakilden fra tredjepart. Partnerconnectoren forsøger at knytte bruger-id'et fra kildeelementet (f.eks. et Twitter-håndtag) til en brugerkonto for alle deltagere (brugere i felterne FRA og TIL). Der importeres en kopi af meddelelsen til hver enkelt deltagers postkasse. Hvis ingen af deltagerne fra elementet kan knyttes til en brugerkonto, importeres elementet til arkiveringspostkassen fra tredjepart i Microsoft 365.  <br/> <br/> Den deltager, der er identificeret som afsender af elementet, skal have en aktiv postkasse i organisationen, som elementet importeres til. Hvis afsenderen ikke har en aktiv postkasse, returneres følgende fejl:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`|`bob@contoso.com`|
  |**TIL**|Ja|Den bruger, der har modtaget et element, hvis det er relevant for et element i datakilden.|`bob@contoso.com`|
  |**EMNE**|Nej|Emnet fra kildeelementet.|`"Mega deals with Contoso coming your way! #ContosoHolidayDeals"`|
  |**DATO**|Ja|Den dato, hvor elementet oprindeligt blev oprettet eller bogført i kundens datakilde. Det kan f.eks. være den dato, hvor en Twitter-meddelelse blev tweetet.|`01 NOV 2015`|
  |**KROPPEN**|Nej|Indholdet af meddelelsen eller indlægget. For nogle datakilder kan indholdet af denne egenskab være det samme som indholdet for egenskaben **SUBJECT** . Under importprocessen forsøger partnerconnectoren at bevare den fulde pålidelighed fra indholdskilden som muligt. Hvis det er muligt, medtages filer, grafik eller andet indhold fra kildeelementets brødtekst i denne egenskab. Ellers medtages indhold fra kildeelementet i egenskaben **ATTACHMENT** . Indholdet af denne egenskab afhænger af partnerconnectoren og af kildeplatformens funktionalitet.|`Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015`|
  |**VEDHÆFTET FIL**|Nej|Hvis et element i datakilden (f.eks. et tweet på Twitter eller en chatsamtale) har en vedhæftet fil eller medtag billeder, forsøger partnerforbindelsen først at inkludere vedhæftede filer i egenskaben **BODY** . Hvis det ikke er muligt, føjes den til egenskaben ** VEDHÆFTET FIL **. Andre eksempler på vedhæftede filer omfatter Synes godt om i Facebook, metadata fra indholdskilden og svar på en meddelelse eller et indlæg.|`image.gif`|
  |**MEDDELELSESKLASSE**|Ja|Dette er en egenskab med flere værdier, som oprettes og udfyldes af partnerconnectoren. Formatet for denne egenskab er  `IPM.NOTE.Source.Event`. (Denne egenskab skal begynde med  `IPM.NOTE`. Dette format svarer til formatet for meddelelsesklassen  `IPM.NOTE.X` . Denne egenskab indeholder følgende oplysninger:  <br/><br/>`Source`: Angiver datakilden fra tredjepart. for eksempel Twitter, Facebook eller BlackBerry.  <br/> <br/>  `Event`: Angiver den type aktivitet, der blev udført i den tredjepartsdatakilde, der producerede elementerne. f.eks. et tweet på Twitter eller et opslag på Facebook. Hændelser er specifikke for datakilden.  <br/> <br/>  Et formål med denne egenskab er at filtrere bestemte elementer baseret på den datakilde, hvor et element stammer fra, eller baseret på typen af hændelse. I en eDiscovery-søgning kan du f.eks. oprette en søgeforespørgsel for at finde alle de tweets, der blev postet af en bestemt bruger.|`IPM.NOTE.Twitter.Tweet`|

- Når elementer importeres til postkasser i Microsoft 365, returneres der et entydigt id til kalderen som en del af HTTP-svaret. Dette id, der kaldes  `x-IngestionCorrelationID`, kan bruges til efterfølgende fejlfindingsformål af partnere til sporing af elementer fra ende til anden. Det anbefales, at partnere registrerer disse oplysninger og logfører dem i overensstemmelse hermed i slutningen. Her er et eksempel på et HTTP-svar, der viser dette id:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Du kan bruge værktøjet Indholdssøgning i Security and Compliance Center til at søge efter elementer, der er importeret til postkasser fra en datakilde fra en tredjepart. Hvis du vil søge specifikt efter disse importerede elementer, kan du bruge følgende par med meddelelsesegenskabsværdier i nøgleordsfeltet til en indholdssøgning.

  - **`kind:externaldata`**: Brug dette egenskabsværdipar til at søge i alle datatyper fra tredjepart. Hvis du f.eks. vil søge efter elementer, der er importeret fra en tredjepartsdatakilde og indeholdt ordet "contoso" i egenskaben Subject for det importerede element, skal du bruge nøgleordsforespørgslen  `kind:externaldata AND subject:contoso`.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: Brug dette egenskabsværdipar til kun at søge efter en bestemt type tredjepartsdata. Hvis du f.eks. kun vil søge efter Facebook-data, der indeholder ordet "contoso" i egenskaben Emne, skal du bruge nøgleordsforespørgslen  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`.

  Hvis du vil have vist en komplet liste over værdier, der skal bruges til datatyper fra tredjepart for  `itemclass` egenskaben, skal du se [Brug indholdssøgning til at søge efter tredjepartsdata, der blev importeret til Microsoft 365](use-content-search-to-search-third-party-data-that-was-imported.md).

   Du kan finde flere oplysninger om brug af indholdssøgning og oprettelse af nøgleordssøgningsforespørgsler i:

  - [Indholdssøgning](content-search.md)

  - [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)
