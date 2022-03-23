---
title: Sådan konfigureres Skype for Business lokalt miljø til at bruge hybrid, moderne godkendelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Lær, hvordan du Skype for Business bruger en lokal installation til at bruge hybrid moderne godkendelse (HMA), hvilket giver dig mere sikker brugergodkendelse og autorisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd42aa6befdbb646217a9829dd59c0821fbd29d3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591618"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Sådan konfigureres Skype for Business lokalt miljø til at bruge hybrid, moderne godkendelse

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Moderne godkendelse, er en identitetsadministrationsmetode, der giver mere sikker brugergodkendelse og -autorisation, er tilgængelig for Skype for Business-server i det lokale miljø og Exchange-server lokalt og Skype for Business-hybrider.

> [!IMPORTANT]
> Vil du gerne vide mere om moderne godkendelse (MA), og hvorfor du måske foretrækker at bruge det i din virksomhed eller organisation? Se [dokumentet for](hybrid-modern-auth-overview.md) at få et overblik. Hvis du vil vide, Skype for Business topologier understøttes med MA, er det dokumenteret her!

**Før vi begynder**, bruger jeg disse udtryk:

- Moderne godkendelse (MA)

- Hybrid moderne godkendelse (HMA)

- Exchange lokal (EXCH)

- Exchange Online (EXO)

- Skype for Business lokalt (SFB)

- Skype for Business Online (SFBO)

Hvis grafikken i denne artikel desuden har et objekt, der er nedtonet eller nedtonet, betyder det, at det element, der  vises i grå, ikke er inkluderet i MA-specifik konfiguration.

## <a name="read-the-summary"></a>Læs oversigten

Denne oversigt opdeler processen i trin, der ellers kunne gå tabt under udførelsen, og er god til en overordnet tjekliste til at holde styr på, hvor du er i processen.

1. Først skal du sørge for, at du opfylder alle forudsætningerne.

1. Da mange forudsætninger er fælles for både Skype for Business og Exchange, kan du læse **oversigtsartikel** til din tjekliste, der er [klar til brug](hybrid-modern-auth-overview.md). Gør dette  *,*  før du starter nogle af trinnene i denne artikel.

1. Indsaml de HMA-specifikke oplysninger, du skal bruge i en fil, eller OneNote.

1. Slå moderne godkendelse til for EXO (hvis det ikke allerede er slået til).

1. Slå moderne godkendelse til for SFBO (hvis det ikke allerede er slået til).

1. Slå hybrid moderne godkendelse til for Exchange lokale miljø.

1. Slå hybrid moderne godkendelse til for Skype for Business lokale miljø.

Disse trin aktiverer MA for SFB, SFBO, EXCH og EXO – det vil sige alle de produkter, der kan deltage i en HMA-konfiguration af SFB og SFBO (herunder afhængigheder af EXCH/EXO). Med andre ord, hvis brugerne er hjemme i/har postkasser oprettet i en del af hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO eller EXCH + SFB), vil dit færdige produkt se således ud:

![En Mixed 6 Skype HMA-topologi til virksomheder har MA på alle fire mulige placeringer.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Som du kan se, er der fire forskellige steder at aktivere MA! For at få den bedste brugeroplevelse anbefaler vi, at du aktiverer MA på alle fire af disse placeringer. Hvis du ikke kan aktivere MA på alle disse placeringer, skal du justere trinnene, så du kun aktiverer MA på de placeringer, der er nødvendige for dit miljø.

Se emnet [Supportability for Skype for Business med MA](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) for understøttede topologier.

> [!IMPORTANT]
> Kontrollér, at du har opfyldt alle forudsætningerne, før du går i gang. Du kan finde disse oplysninger i Oversigt [over og forudsætninger for hybrid moderne godkendelse](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>Indsaml alle HMA-specifikke oplysninger, du skal bruge

Når du har kontrolleret, at du opfylder forudsætningerne [](hybrid-modern-auth-overview.md) for at bruge moderne godkendelse (se noten ovenfor), skal du oprette en fil, der indeholder de oplysninger, du skal bruge til at konfigurere HMA i de efterfølgende trin. Eksempler, der bruges i denne artikel:

- **SIP/SMTP-domæne**

  - F.eks. contoso.com (er medlem af organisationsnetværk med Office 365)

- **Lejer-id**

  - Det GUID, der repræsenterer Office 365 lejer (ved logon på contoso.onmicrosoft.com).

- **SFB 2015 CU5 Web Service URL-adresser**

Du skal bruge interne og eksterne webtjenestewebadresser for alle sfB 2015-puljer, der er installeret. For at hente disse skal du køre følgende fra Skype for Business Management Shell:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- F.eks. Internt: https://lyncwebint01.contoso.com

- F.eks. Ekstern: https://lyncwebext01.contoso.com

Hvis du bruger en Standard Edition, er den interne URL-adresse tom. I dette tilfælde skal du bruge pulje-fqdn til den interne URL-adresse.

## <a name="turn-on-modern-authentication-for-exo"></a>Slå moderne godkendelse til for EXO

Følg vejledningen her: Exchange Online[: Sådan aktiverer du din lejer til moderne godkendelse.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>Slå moderne godkendelse til for SFBO

Følg vejledningen her: Skype for Business [Online: Aktivér din lejer for moderne godkendelse](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Slå hybrid moderne godkendelse til for Exchange lokale miljø

Følg vejledningen her: [Sådan konfigureres Exchange Server lokale miljø til at bruge hybrid moderne godkendelse](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Slå hybrid moderne godkendelse til for Skype for Business lokale miljø

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Tilføj URL-adresser for lokale webtjeneste som SPN'er Azure Active Directory

Nu skal du køre kommandoer for at tilføje URL-adresserne (indsamlet tidligere) som tjenesteinspektører i SFBO.

> [!NOTE]
> Tjenestens hovednavne (SPN'er) identificerer webtjenester og knytter dem til en sikkerhedskontokonto (f.eks. et kontonavn eller en gruppe), så tjenesten kan handle på vegne af en godkendt bruger. Klienter, der godkender til en server, gør brug af oplysninger, der er indeholdt i SPN'er.

1. Opret først forbindelse til Azure Active Directory (Azure AD) med [denne vejledning](/powershell/azure/active-directory/overview).

2. Kør denne kommando i det lokale miljø for at få en liste over URL-adresser for SFB-webtjenesten.

   Bemærk, at AppPrincipalId begynder med `00000004`. Dette svarer til Skype for Business Online.

   Vær opmærksom på (og skærmbillede til senere sammenligning) outputtet af denne kommando, som indeholder en SE- og WS-URL-adresse, men som hovedsageligt består af SPN'er, der starter med `00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. Hvis de interne **eller** eksterne SFB URL-adresser fra det lokale miljø mangler (f.eks. https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) og vi er nødt til at føje disse specifikke poster til denne liste.

    Sørg for at erstatte  *nedenstående eksempel-URL-adresser* med dine faktiske URL-adresser i kommandoerne Tilføj!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. Kontrollér, at dine nye poster blev tilføjet ved at køre **kommandoen Get-MsolServicePrincipal** fra trin 2 igen og gennemgå outputtet. Sammenlign listen eller skærmbilledet fra før med den nye liste over SPN'er. Du kan også skærmbillede den nye liste til dine poster. Hvis det lykkedes for dig, får du vist de to nye URL-adresser på listen. I vores eksempel vil listen over SPN'er nu indeholde de specifikke URL-adresser https://lyncwebint01.contoso.com og https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>Oprette objektet for godkendelsesserveren

Kør følgende kommando i Skype for Business Management Shell.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Aktivér hybrid moderne godkendelse

Dette er det trin, der faktisk aktiverer MA. Alle de forrige trin kan køres i forvejen uden at ændre klientgodkendelsesflowet. Når du er klar til at ændre godkendelsesflowet, skal du køre denne kommando i Skype for Business Management Shell.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Bekræft

Når du aktiverer HMA, bruger en klients næste logon det nye godkendelsesflow. Bemærk, at kun aktivering af HMA ikke udløser en genautentiering for nogen klient. Klienterne reauthenticate baseret på levetiden for de godkendelsestokens og/eller certs, de har.

Hvis du vil teste, om HMA fungerer, efter du har aktiveret det, skal du logge af en SFB Windows-klient og sørge for at klikke på "Slet mine legitimationsoplysninger". Log på igen. Klienten bør nu bruge flowet Moderne godkendelse, og dit logon indeholder nu en **Office 365-prompt** om en "arbejds- eller skolekonto", som vises lige før klienten kontakter serveren og logger dig på.

Du skal også kontrollere "Konfigurationsoplysninger" for Skype for Business for et "OAuth-nøglecenter". Det gør du på klientcomputeren ved at holde Ctrl nede, samtidig med at du højreklikker på ikonet Skype for Business i Windows meddelelsesområdet. Klik **på Konfigurationsoplysninger** i den menu, der vises. I vinduet "Skype for Business Konfigurationsoplysninger", der vises på skrivebordet, skal du se efter følgende:

:::image type="content" alt-text="Konfigurationsoplysningerne for en Skype for Business klient, der bruger moderne godkendelse, viser en URL-adresse til Lync og EWS OAUTH Authority https://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Du skal også holde CTRL-tasten nede, samtidig med at du højreklikker på ikonet for Outlook-klienten (også i proceslinjen Windows-meddelelser), og klikke på "Forbindelsesstatus". Se efter klientens SMTP-adresse mod en AuthN-type 'Bearer\*', som repræsenterer den Bearer-token, der bruges i OAuth.

## <a name="related-articles"></a>Relaterede artikler

[Opret et link tilbage til den moderne godkendelsesoversigt](hybrid-modern-auth-overview.md).

Har du brug for at vide, hvordan du bruger moderne godkendelse til Skype for Business klienter? Vi har trin her: Oversigt over hybrid moderne godkendelse og forudsætninger for brug af det med lokale Skype for Business [og Exchange servere](./hybrid-modern-auth-overview.md).
