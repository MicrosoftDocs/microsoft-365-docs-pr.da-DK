---
title: Sådan konfigurerer du Skype for Business i det lokale miljø til at bruge hybrid moderne godkendelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Få mere at vide om, hvordan du konfigurerer Skype for Business i det lokale miljø til at bruge Hybrid Modern Authentication (HMA), som giver dig mere sikker brugergodkendelse og -godkendelse.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f5e48905416f84ed1a4c48f7e6f1a4b6477f73e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093476"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Sådan konfigurerer du Skype for Business i det lokale miljø til at bruge hybrid moderne godkendelse

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Moderne godkendelse, er en metode til identitetsstyring, der tilbyder mere sikker brugergodkendelse og -godkendelse, er tilgængelig for Skype for Business server i det lokale miljø og Exchange server i det lokale miljø og hybrider med opdelt domæne Skype for Business.

> [!IMPORTANT]
> Vil du vide mere om moderne godkendelse, og hvorfor du foretrækker at bruge den i din virksomhed eller organisation? Kontrollér [dette dokument](hybrid-modern-auth-overview.md) for at få en oversigt. Hvis du har brug for at vide, hvilke Skype for Business topologier understøttes med ma, er det dokumenteret her!

**Før vi begynder**, bruger jeg følgende begreber:

- Moderne godkendelse

- Hybrid moderne godkendelse (HMA)

- Exchange i det lokale miljø (EXCH)

- Exchange Online (EXO)

- Skype for Business lokalt (SFB)

- Skype for Business Online (SFBO)

Hvis et grafikelement i denne artikel har et objekt, der er nedtonet eller nedtonet, betyder det også, at det element, der vises med gråt **, ikke er** inkluderet i en MA-specifik konfiguration.

## <a name="read-the-summary"></a>Læs oversigten

I denne oversigt opdeles processen i trin, der ellers kan gå tabt under udførelsen, og det er godt for en overordnet tjekliste til at holde styr på, hvor du befinder dig i processen.

1. Først skal du sørge for at opfylde alle forudsætningerne.

1. Da mange **forudsætninger** er almindelige for både Skype for Business og Exchange, kan du [se oversigtsartiklen for tjeklisten](hybrid-modern-auth-overview.md). Gør dette  *, før*  du begynder på nogen af trinnene i denne artikel.

1. Indsaml de HMA-specifikke oplysninger, du skal bruge i en fil, eller OneNote.

1. Slå moderne godkendelse til for EXO (hvis den ikke allerede er slået til).

1. Slå moderne godkendelse til for SFBO (hvis den ikke allerede er slået til).

1. Slå hybrid moderne godkendelse til for Exchange i det lokale miljø.

1. Slå hybrid moderne godkendelse til for Skype for Business i det lokale miljø.

Disse trin aktiverer MA for SFB, SFBO, EXCH og EXO – dvs. alle de produkter, der kan deltage i en HMA-konfiguration af SFB og SFBO (herunder afhængigheder af EXCH/EXO). Med andre ord, hvis dine brugere er hjemme i/har postkasser oprettet i nogen del af Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, eller EXCH + SFB), vil dit færdige produkt se sådan ud:

![En HMA-topologi med blandet 6 Skype til virksomheder har MA aktiveret på alle fire mulige placeringer.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Som du kan se, er der fire forskellige steder at aktivere MA! For at få den bedste brugeroplevelse anbefaler vi, at du slår ma til på alle fire af disse placeringer. Hvis du ikke kan slå ma til på alle disse placeringer, skal du justere trinnene, så du kun aktiverer ma på de placeringer, der er nødvendige for dit miljø.

Se [emnet Supportability for Skype for Business med MA](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) for at få oplysninger om understøttede topologier.

> [!IMPORTANT]
> Dobbelttjek, at du har opfyldt alle forudsætningerne, før du begynder. Du kan finde disse oplysninger i [Oversigt over hybrid moderne godkendelse og forudsætninger](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>Indsaml alle HMA-specifikke oplysninger, du skal bruge

Når du har dobbelttjekket, at du opfylder [forudsætningerne](hybrid-modern-auth-overview.md) for at bruge moderne godkendelse (se noten ovenfor), skal du oprette en fil, der indeholder de oplysninger, du skal bruge til at konfigurere HMA i de efterfølgende trin. Eksempler, der bruges i denne artikel:

- **SIP-/SMTP-domæne**

  - Ex. contoso.com (er sammenkædet med Office 365)

- **Lejer-id**

  - Det GUID, der repræsenterer din Office 365 lejer (ved logon af contoso.onmicrosoft.com).

- **URL-adresser til SFB 2015 CU5-webtjeneste**

Du skal bruge URL-adresser til interne og eksterne webtjenester for alle udrullede SfB 2015-grupper. Du kan hente disse ved at køre følgende fra Skype for Business Management Shell:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. Interne: https://lyncwebint01.contoso.com

- Ex. Eksterne: https://lyncwebext01.contoso.com

Hvis du bruger en Standard Edition server, er den interne URL-adresse tom. I dette tilfælde skal du bruge puljefqdn til den interne URL-adresse.

## <a name="turn-on-modern-authentication-for-exo"></a>Slå moderne godkendelse til for EXO

Følg vejledningen her: [Exchange Online: Sådan aktiverer du din lejer til moderne godkendelse.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>Slå moderne godkendelse til for SFBO

Følg vejledningen her: [Skype for Business Online: Aktivér din lejer til moderne godkendelse](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Slå hybrid moderne godkendelse til for Exchange i det lokale miljø

Følg vejledningen her: [Sådan konfigurerer du Exchange Server i det lokale miljø til at bruge hybrid moderne godkendelse](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Slå hybrid moderne godkendelse til for Skype for Business i det lokale miljø

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Tilføj URL-adresser til webtjenesten i det lokale miljø som SPN'er i Azure Active Directory

Nu skal du køre kommandoer for at tilføje URL-adresserne (indsamlet tidligere) som tjenesteprincipaler i SFBO.

> [!NOTE]
> Tjenesteprincipalnavne identificerer webtjenester og knytter dem til en sikkerhedskonto (f.eks. et kontonavn eller en gruppe), så tjenesten kan handle på vegne af en godkendt bruger. Klienter, der godkender til en server, bruger oplysninger, der er indeholdt i SPN'er.

1. Først skal du oprette forbindelse til Azure Active Directory (Azure AD) med [disse instruktioner](/powershell/azure/active-directory/overview).

2. Kør denne kommando i det lokale miljø for at få vist en liste over URL-adresser til SFB-webtjenesten.

   Bemærk, at AppPrincipalId starter med `00000004`. Dette svarer til Skype for Business Online.

   Notér (og skærmbillede til senere sammenligning) outputtet fra denne kommando, som omfatter en URL-adresse til SE og WS, men hovedsageligt består af SPN'er, der starter med `00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. Hvis de interne **eller** eksterne SFB-URL-adresser fra det lokale miljø mangler (f.eks. https://lyncwebint01.contoso.com og https://lyncwebext01.contoso.com) vi skal føje disse specifikke poster til denne liste.

    Sørg for at erstatte nedenstående  *eksempel-URL-adresser* med dine faktiske URL-adresser i Tilføj kommandoer!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. Kontrollér, at dine nye poster blev tilføjet ved at køre kommandoen **Get-MsolServicePrincipal** fra trin 2 igen og gennemse outputtet. Sammenlign listen eller skærmbilledet fra før med den nye liste over SPN'er. Du kan også skærmbillede den nye liste for dine poster. Hvis du lykkedes, får du vist de to nye URL-adresser på listen. I eksemplet indeholder listen over SPN'er nu de specifikke URL-adresser https://lyncwebint01.contoso.com og https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>Opret godkendelsesserverobjektet EvoSTS

Kør følgende kommando i Skype for Business Management Shell.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Aktivér hybrid moderne godkendelse

Dette er det trin, der faktisk slår MA til. Alle de forrige trin kan køres på forhånd uden at ændre klientgodkendelsesflowet. Når du er klar til at ændre godkendelsesflowet, skal du køre denne kommando i Skype for Business Management Shell.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Kontrollere

Når du aktiverer HMA, bruger en klients næste logon det nye godkendelsesflow. Bemærk, at hvis du bare aktiverer HMA, udløses der ikke en godkendelse for nogen klient. Klienterne genauthenticerer baseret på levetiden af de godkendelsestokens og/eller certifikater, de har.

Hvis du vil teste, at HMA fungerer, når du har aktiveret den, skal du logge af en SFB-testklient Windows og sørge for at klikke på "slet mine legitimationsoplysninger". Log på igen. Klienten skal nu bruge det moderne godkendelsesflow, og dit logon omfatter nu en **Office 365** beder om en 'Arbejds- eller skolekonto', der vises, lige før klienten kontakter serveren og logger dig på.

Du bør også kontrollere 'Konfigurationsoplysninger' for Skype for Business-klienter for et 'OAuth Authority'. Hvis du vil gøre dette på klientcomputeren, skal du holde Ctrl nede, samtidig med at du højreklikker på ikonet Skype for Business på Windows meddelelsesbakke. Klik på **Konfigurationsoplysninger** i den menu, der vises. I vinduet 'Skype for Business konfigurationsoplysninger', der vises på skrivebordet, skal du se efter følgende:

:::image type="content" alt-text="Konfigurationsoplysningerne for en Skype for Business klient, der bruger moderne godkendelse, viser URL-adressen til Lync og EWS OAUTH-autoritet for https://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Du skal også holde CTRL-tasten nede, samtidig med at du højreklikker på ikonet for Outlook-klienten (også på Windows meddelelsesbakken) og klikke på "Forbindelsesstatus". Kig efter klientens SMTP-adresse i forhold til authN-typen 'Ihændehaver\*', som repræsenterer det ihændehavertoken, der bruges i OAuth.

## <a name="related-articles"></a>Relaterede artikler

[Opret et link tilbage til oversigten over moderne godkendelse](hybrid-modern-auth-overview.md).

Har du brug for at vide, hvordan du bruger moderne godkendelse til dine Skype for Business klienter? Vi har trin her: [Oversigt over hybrid moderne godkendelse og forudsætninger for at bruge den med lokale Skype for Business og Exchange servere](./hybrid-modern-auth-overview.md).
