---
title: Konfigurere IRM (Information Rights Management) SharePoint Administration
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: Lær at bruge SharePoint Online IRM via Microsoft Azure Active Directory RMS (Rights Management Services) til at beskytte SharePoint lister og dokumentbiblioteker.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 8c0f60ad1a571ba13ba83e3e92c1b5aca6535bb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588939"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Konfigurere IRM (Information Rights Management) SharePoint Administration

I SharePoint Online anvendes IRM-beskyttelse på filer på liste- og biblioteksniveau. Før din organisation kan bruge IRM-beskyttelse, skal du først konfigurere Rights Management. IRM er afhængig af Tjenesten Azure Rights Management fra Azure Information Protection til at kryptere og tildele begrænsninger for brug. Nogle Microsoft 365 omfatter Azure Rights Management, men ikke alle. Du kan få mere at vide [ved at læse Office programmer og tjenester understøtter Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Aktivere IRM-tjenesten SharePoint Administration

Før din organisation kan IRM-beskytte SharePoint lister og biblioteker, skal du først aktivere Rights Management-tjenesten for organisationen. Du kan få mere at vide [under Aktivering af Azure Rights Management](/information-protection/deploy-use/activate-service). Du skal bruge en arbejds- eller skolekonto, der har globale administratorrettigheder, for at aktivere Rights Management-tjenesten. Ellers kan du ikke bruge IRM-funktioner sammen med SharePoint Online.
  
Når du aktiverer Rights Management-tjenesten, skal du logge på SharePoint Administration for at aktivere IRM.
  
1. Log på som global administrator eller SharePoint administrator.
    
2. Vælg ikonet for appstarteren ![Ikonet for appstarteren i Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) øverst til venstre, og vælg **Administrator for** at åbne Microsoft 365 Administration. Hvis du ikke kan se feltet Administrator, har du ikke administratortilladelser i din organisation. 
    
3. I venstre rude skal du **vælge SharePoint** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Administration.</a>
    
4. I venstre rude skal du **vælge Indstillinger** og derefter vælge **klassisk indstillingsside**.
    
5. I sektionen **IRM (Information Rights Management)** skal du vælge Brug den **IRM-tjeneste**, der er angivet i konfigurationen, og derefter vælge Opdater **IRM Indstillinger**. Når du opdaterer IRM-indstillinger, kan personer i organisationen begynde at bruge IRM i deres SharePoint lister og dokumentbiblioteker. Det kan dog tage op til en time at få vist indstillingerne i Bibliotek Indstillinger Liste Indstillinger.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>IRM-aktiverede SharePoint dokumentbiblioteker og -lister
<a name="__toc220831191"> </a>

Når du har opdateret IRM-indstillinger, kan webstedsejere IRM-beskytte deres SharePoint lister og dokumentbiblioteker. Få mere at vide under [Brug af IDE (Information Rights Management) på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Når webstedsejere aktiverer IRM for en liste eller et bibliotek, kan de beskytte alle understøttede filtyper på den pågældende liste eller det pågældende bibliotek. Når IRM er aktiveret for et bibliotek, anvendes rettighedsstyring på alle filerne i det pågældende bibliotek. Når du aktiverer IRM for en liste, gælder rettighedsstyring kun for filer, der er knyttet til listeelementer, ikke de faktiske listeelementer.
  
Når personer henter filer på en IRM-aktiveret liste eller i et IRM-aktiveret bibliotek, krypteres filerne, så kun autoriserede personer kan se dem. Hver rettighedsstyret fil indeholder også en udstedelseslicens, der pålægger de personer, der får vist filen, begrænsninger. Typiske begrænsninger omfatter at gøre en fil skrivebeskyttet, deaktivere kopieringen af tekst, forhindre brugere i at gemme en lokal kopi og forhindre folk i at udskrive filen. Klientprogrammer, der kan læse IRM-understøttede filtyper, bruger udstedelseslicensen i den rettighedsstyret fil til at håndhæve disse begrænsninger. Sådan bevarer en rettighedsstyret fil beskyttelsen, selv efter den er downloadet. Hvis du vil aktivere IRM på en liste eller et bibliotek, skal du [se Anvend IRM (Information Rights Management) på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Du kan ikke oprette eller redigere dokumenter i et IRM-aktiveret bibliotek ved Office i en browser. I stedet kan én person ad gangen downloade og redigere IRM-krypterede filer. Brug indtjekning og udtjekning til at administrere  *samtidig redigering eller*  redigering på tværs af flere brugere. 
  
Når du henter en PDF-fil fra et IRM-beskyttet bibliotek, opretter Microsoft 365 en beskyttet PDF-fil. Filens filtypenavn ændres ikke, men filen er beskyttet. For at få vist denne fil skal du bruge Azure Information Protection Viewer, den fulde Azure Information Protection-klient eller et andet program, der understøtter visning af beskyttede PDF-filer. 
  
SharePoint Online understøtter kryptering af følgende filtyper:
  
- PDF
    
- 97-2003-filformaterne til følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- De Office Open XML-formater til følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- XPS-formatet (XML Paper Specification)
 
> [!NOTE]
> IRM-beskyttelse kan ikke anvendes på beskyttede dokumenter (f.eks. digitalt signerede PDF-filer), da SharePoint skal åbne dokumentet ved overførsel. 

## <a name="next-steps"></a>Næste trin
<a name="__toc220831191"> </a>

Når du har aktiveret IRM til SharePoint Online, kan du begynde at anvende rettighedsstyring på lister og biblioteker. Du kan finde flere oplysninger [i Anvend IDE (Information Rights Management) på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Den nye OneDrive-synkronisering-klient til Windows understøtter nu synkronisering af IRM-beskyttede SharePoint-dokumentbiblioteker og OneDrive-placeringer (så længe IRM-indstillingen for biblioteket ikke er indstillet til at udløbe adgangsrettigheder til dokumenter). Du kan finde flere oplysninger eller for at komme i gang med at installere den nye [synkroniseringsklient under Installere den OneDrive-synkronisering-klient til Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)