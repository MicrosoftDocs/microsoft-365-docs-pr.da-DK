---
title: Opret DNS-poster for Microsoft ved Windows-baseret DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Windows-baseret DNS til Microsoft.
ms.openlocfilehash: 0349366e1cb3af23de1161a69b9b37305cc1237a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588099"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Opret DNS-poster for Microsoft ved Windows-baseret DNS

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
   
Hvis du hoster dine egne DNS-poster ved hjælp af Windows-baseret DNS, skal du følge trinnene i denne artikel for at konfigurere dine poster for mail, Skype for Business Online osv.
  
For at komme i gang skal du [finde dine DNS-poster Windows-baseret DNS](#find-your-dns-records-in-windows-based-dns), så du kan opdatere dem. Hvis du planlægger at synkronisere dit lokale Active Directory med Microsoft, skal du se Mailadresse, der ikke kan sendes, som en UPN i dit lokale [Active Directory](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory).
  
Problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, se [Fejlfinding efter ændring af dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Find dine DNS-poster Windows-baseret DNS
<a name="BKMK_find_your_dns_1"> </a> Gå til den side, der indeholder DNS-posterne for dit domæne. Hvis du arbejder i en Windows Server 2008, skal du gå til **StartRun** > . Hvis du arbejder i en Windows Server 2012, skal du trykke på Windows og **r**. Skriv **dnsmgmnt.msc**, og vælg derefter **OK**. I DNS Manager skal du **udvide\<DNS server name\>\> Forward Lookup Zones**. Vælg dit domæne. Du er nu klar til at oprette DNS-posterne.
   
## <a name="add-mx-record"></a>Tilføje MX-post
<a name="BKMK_add_MX"> </a>

Tilføj en MX-post, så mail til dit domæne kommer til Microsoft.
- Den MX-post, du skal tilføje, indeholder en værdi  (værdien Peger på adresse), der ser sådan ud: \<MX token\>.mail.protection.outlook.com, \<MX token\> hvor er en værdi som MSxxxxxxx. 
- Fra rækken MX i sektionen Exchange Online siden Tilføj DNS-poster i Microsoft skal du kopiere den værdi, der er angivet under Peger på adresse. Du skal bruge denne værdi i den post, du opretter i denne opgave. 
- På DNS Manager-siden for domænet skal du gå til **ActionMail** >  **Exchanger (MX)**. For at finde denne side for domænet skal [du se Finde dine DNS-poster Windows-baseret DNS](#find-your-dns-records-in-windows-based-dns).  
- I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående: 
    - Værtsnavn: 
    - @Address: Indsæt værdien Peger på adresse, som du lige har kopieret fra Microsoft, her.  
    - Pref: 
- Vælg **Gem ændringer**.
- Fjern eventuelle forældede MX-poster. Hvis du har gamle MX-poster for dette domæne, som dirigerer mail til et andet sted, skal du markere afkrydsningsfeltet ud for hver gammel post og derefter vælge **DeleteOK** > . 
   
## <a name="add-cname-records"></a>Tilføj CNAME-poster
<a name="BKMK_add_CNAME"> </a>

Tilføj de CNAME-poster, der kræves til Microsoft. Hvis yderligere CNAME-poster er angivet i Microsoft, kan du tilføje dem ved at følge de samme generelle trin, der er vist her.
  
> [!IMPORTANT]
> Hvis du har administration af mobilenheder (MDM) til Microsoft, skal du oprette to ekstra CNAME-poster. Følg den fremgangsmåde, du anvendte til de fire andre CNAME-poster, men brug værdierne fra følgende tabel. Hvis du ikke har MDM, kan du springe dette trin over. 

- På DNS Manager-siden for domænet skal du gå til **ActionCNAME** >  **(CNAME)**.
- I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    - Værtsnavn: autodiscover
    - Skriv: 
    - CNAMEAddress: autodiscover.outlook.com
- Vælg **OK**.

Tilføj CNAME-posten for SIP. 
- På DNS Manager-siden for domænet skal du gå til **Action** \> **CNAME (CNAME)**. 
- I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    - Værtsnavn: sip
    - Type: CNAME
    - Adresse: sipdir.online.lync.com
- Vælg **OK**.

Tilføj Skype for Business Online Autodiscover CNAME-post.  
- På DNS Manager-siden for domænet skal du gå til **Action** \> **CNAME (CNAME)**. I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    - Værtsnavn: lyncdiscover
    - Type: CNAME
    - Adresse: webdir.online.lync.com
- Vælg **OK**.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Tilføj to CNAME-poster til administration af mobilenheder (MDM) til Microsoft

> [!IMPORTANT]
> Hvis du har administration af mobilenheder (MDM) til Microsoft, skal du oprette to ekstra CNAME-poster. Følg den fremgangsmåde, du anvendte til de fire andre CNAME-poster, men brug værdierne fra følgende tabel. >(Hvis du ikke har MDM, kan du springe dette trin over). 
  

Tilføj CNAME-posten for MDM Enterpriseregistration.  
- På DNS Manager-siden for domænet skal du gå til **Action** \> **CNAME (CNAME)**. 
- I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
- Værtsnavn: enterpriseregistration
- Type: CNAME
- Adresse: enterpriseregistration.windows.net
- Vælg **OK**. 

Tilføj CNAME-posten for MDM Enterpriseenrollment. 
-  På DNS Manager-siden for domænet skal du gå til **Action** \> **CNAME (CNAME)**. 
-  I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    - Værtsnavn: enterpriseenrollment
    - Type: CNAME
    - Adresse: enterpriseenrollment-s.manage.microsoft.com
- Vælg **OK**.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. 
  
Tilføj SPF TXT-posten for dit domæne for at forhindre mailspam.
  
- Du har måske allerede andre strenge i TXT-værdien for denne post (f.eks. strenge til marketingmails), hvilket er fint. Lad disse strenge være, og tilføj denne, og anførselstegn omkring hver streng for at adskille dem. 
- På DNS Manager-siden for dit domæne skal du gå til **Action** \> **Text (TXT)**. 
-  Sørg for **, at felterne** i dialogboksen Ny ressourcepost er indstillet med nøjagtigt de samme værdier som nedenstående. 
 > [!IMPORTANT]
> I nogle versioner af Windows DNS Manager kan domænet være konfigureret således, at det overordnede domæne som standard er det overordnede domæne, når du opretter en txt-post. I denne situation skal du, når du tilføjer en TXT-post, angive værtsnavnet til tomt (ingen værdi) i stedet for at indstille den til @ eller domænenavnet. 

-  Værtstype: @
-  Posttype: TXT
-  Adresse: v=spf1 include:spf.protection.outlook.com -all 
         
-  Vælg **OK**.
   
## <a name="add-srv-records"></a>Tilføje SRV-poster
<a name="BKMK_add_SRV"> </a>

Tilføj de to SRV-poster, der kræves til Microsoft.

Tilføj SIP SRV-posten for Skype for Business Online-webmøder.  <br/> 
-  På DNS Manager-siden for dit domæne skal du gå til **Action** \> **Other New Records**. 
-   I vinduet **Ressourceposttype** skal du vælge **Tjenesteplacering (SRV)** og derefter vælge **Opret post**. 
-   I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    -  Tjeneste: _sip
    -  Protokol: _tls
    -  Prioritet: 100
    -  Vægt: 1
    -  Port: 443
    -  Target (Hostname): sipdir.online.lync.com
-  Vælg **OK**. 


Tilføj SIP SRV-posten for Skype for Business Online-sammenslutning.  
-  På DNS Manager-siden for dit domæne skal du gå til **Action** \> **Other New Records**.  
-  I vinduet **Ressourceposttype** skal du vælge **Tjenesteplacering (SRV)** og derefter vælge **Opret post**. 
-   I dialogboksen **Ny ressourcepost** skal du sikre dig, at felterne er indstillet med nøjagtigt de samme værdier som nedenstående:  
    -  Tjeneste: _sipfederationtls
    -  Protokol: _tcp
    -  Prioritet: 100
    -  Vægt: 1
    -  Port: 5061
    -  Target (Hostname): sipfed.online.lync.com
-  Vælg **OK**. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Tilføj en post for at bekræfte, at du ejer domænet, hvis du ikke allerede har gjort det
<a name="BKMK_verify"> </a>

Før du tilføjer DNS-posterne for at konfigurere din Microsoft-tjenester, skal Microsoft bekræfte, at du ejer det domæne, du tilføjer. For at gøre dette skal du tilføje en post ved at følge nedenstående trin.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. 
  

1. Indsamle oplysninger fra Microsoft.  <br/> 
2. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>. 
3. Vælg **Start installationen** på siden Domæner **i kolonnen** Handlinger for det domæne, du er ved at **bekræfte**. 
4. På siden **Føj et domæne til Microsoft** skal du vælge **Start trin 1**. 
5. På siden **Bekræft, at** du ejer dit domæne skal du  vælge Generelle instruktioner på rullelisten Se instruktioner for at udføre **dette trin med**. 
6. Kopiér værdien for Destination eller adressepunkter fra tabellen. Du skal bruge den i næste trin. Vi anbefaler, at du kopierer og indsætter denne værdi, så alle mellemrum forbliver korrekte.

Tilføj en TXT-post. 
-  På DNS Manager-siden for dit domæne skal du gå til **Action** \> **Text (TXT)**. 
-   I dialogboksen **Ny ressourcepost** skal du vælge **Rediger**.  
-  I området **Custom Host Names** i dialogboksen **New Resource Record** skal du sørge for, at felterne er indstillet til nøjagtigt følgende værdier. 

> [!IMPORTANT] 
> I nogle versioner af Windows DNS Manager kan domænet være konfigureret således, at det overordnede domæne som standard er det overordnede domæne, når du opretter en txt-post. I denne situation skal du, når du tilføjer en TXT-post, angive værtsnavnet til tomt (ingen værdi) i stedet for at indstille den til @ eller domænenavnet. 

- Værtsnavn: @
- Type: TXT
- Adresse: Indsæt værdien Destination eller peger på adresse, som du lige har kopieret fra Microsoft, her.  
- Vælg **OKDone** > .

Bekræfte dit domæne i Microsoft.  
> [!IMPORTANT]
> Vent ca. 15 minutter, før du gør dette, så den post, du lige har oprettet, kan opdateres på tværs af internettet.       

- Gå tilbage til Microsoft, og følg trinnene nedenfor for at anmode om en bekræftelseskontrol. Denne kontrol søger efter den TXT-post, du tilføjede i forrige trin. Når den finder den korrekte TXT-post, bekræftes domænet.  
1. I Administration skal du gå til **siden Konfiguration** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">af</a> domæner.
2. På siden **Domæner i** kolonnen Handling for **det** domæne, du er ved at bekræfte, skal du vælge **Start installationen**. 
3. På siden **Bekræft, at** du ejer dit domæne skal du vælge **Udført,** bekræft nu og derefter vælge **Udfør i bekræftelsesdialogboksen**. 
   
> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Mailadresse, der ikke kan sendes, og som bruges som UPN i dit active directory, som ikke kan sendes
<a name="BKMK_ADNote"> </a>

Hvis du planlægger at synkronisere dit lokale Active Directory med Microsoft, skal du sikre dig, at ACTIVE Directory-brugerens hovednavn (UPN) er et gyldigt domænesuffiks og ikke et ikke-understøttet domænesuffiks som f.eks. @contoso.local. Hvis du vil ændre dit UPN-suffiks, skal du se Sådan forberedes et domæne, der ikke kan kan rous [, til katalogsynkronisering](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md).
  
> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="related-content"></a>Relateret indhold

[Overfør et domæne fra Micrsoft 365 til en anden vært](../get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host.md) (artikel)\
[Pilot Microsoft 365 fra mit eget domæne](../misc/pilot-microsoft-365-from-my-custom-domain.md) (artikel)\
[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)