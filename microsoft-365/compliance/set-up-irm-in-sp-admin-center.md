---
title: Konfigurer IRM (Information Rights Management) i SharePoint Administration
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
description: Få mere at vide om, hvordan du bruger SharePoint Online IRM via RMS (Microsoft Azure Active Directory Rights Management Services) til at beskytte SharePoint lister og dokumentbiblioteker.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 71881e5317153288f955c44d3c52cbf80a3f8def
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042994"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Konfigurer IRM (Information Rights Management) i SharePoint Administration

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I SharePoint Online anvendes IRM-beskyttelse på filer på liste- og biblioteksniveau. Før din organisation kan bruge IRM-beskyttelse, skal du først konfigurere Rights Management. IRM er afhængig af Azure Rights Management-tjenesten fra Azure Information Protection til at kryptere og tildele forbrugsbegrænsninger. Nogle Microsoft 365 planer omfatter Azure Rights Management, men ikke alle. Du kan få mere at vide ved at læse [Sådan understøtter Office programmer og tjenester Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Slå IRM-tjenesten til ved hjælp af SharePoint Administration

Før din organisation kan IRM-beskytte SharePoint lister og biblioteker, skal du først aktivere Rights Management-tjenesten for din organisation. Du kan få mere at vide om, hvordan du [kan se Aktivering af Azure Rights Management](/information-protection/deploy-use/activate-service). Du skal bruge en arbejds- eller skolekonto, der har globale administratorrettigheder, for at aktivere Rights Management-tjenesten. Ellers kan du ikke bruge IRM-funktioner med SharePoint Online.
  
Når du har aktiveret Rights Management-tjenesten, skal du logge på SharePoint Administration for at aktivere IRM.
  
1. Log på som global administrator eller SharePoint administrator.
    
2. Vælg appstarterikonet ![ikonet appstarter i Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) øverst til venstre, og vælg **Administrator** for at åbne Microsoft 365 Administration. Hvis du ikke kan se feltet Administrator, har du ikke administratorrettigheder i din organisation. 
    
3. I venstre rude skal du vælge **Administration SharePoint** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Administration</a>.
    
4. Vælg **Indstillinger** i ruden til venstre, og vælg derefter **siden med klassiske indstillinger**.
    
5. I afsnittet **Oplysninger Rights Management (IRM)** skal du vælge **Brug den IRM-tjeneste, der er angivet i konfigurationen**, og derefter vælge **Opdater IRM-Indstillinger**. Når du har opdateret IRM-indstillingerne, kan personer i din organisation begynde at bruge IRM på deres SharePoint lister og dokumentbiblioteker. Det kan dog tage op til en time, før indstillingerne vises i Bibliotek Indstillinger og Liste Indstillinger.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>IRM-aktivér SharePoint dokumentbiblioteker og -lister
<a name="__toc220831191"> </a>

Når IRM-indstillingerne er opdateret, kan webstedsejerne IRM-beskytte deres SharePoint lister og dokumentbiblioteker. Du kan finde flere oplysninger under [Anvend oplysninger Rights Management på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Når webstedsejere aktiverer IRM for en liste eller et bibliotek, kan de beskytte alle understøttede filtyper på listen eller biblioteket. Når IRM er aktiveret for et bibliotek, gælder rights management for alle filerne i det pågældende bibliotek. Når du aktiverer IRM for en liste, gælder Rights Management kun for filer, der er knyttet til listeelementer, og ikke de faktiske listeelementer.
  
Når folk downloader filer på en IRM-aktiveret liste eller et IRM-bibliotek, krypteres filerne, så det kun er godkendte personer, der kan se dem. Hver rettighedsadministreret fil indeholder også en udstedelseslicens, der pålægger begrænsninger for de personer, der får vist filen. Typiske begrænsninger omfatter at gøre en fil skrivebeskyttet, deaktivere kopiering af tekst, forhindre personer i at gemme en lokal kopi og forhindre andre i at udskrive filen. Klientprogrammer, der kan læse IRM-understøttede filtyper, bruger udstedelseslicensen i den rettighedsadministrerede fil til at gennemtvinge disse begrænsninger. Sådan bevarer en rettighedsadministreret fil sin beskyttelse, selv efter at den er downloadet. Hvis du vil aktivere IRM på en liste eller et bibliotek, [skal du se Anvend oplysninger Rights Management på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Du kan ikke oprette eller redigere dokumenter i et IRM-aktiveret bibliotek ved hjælp af Office i en browser. I stedet kan én person ad gangen downloade og redigere IRM-krypterede filer. Brug ind- og udtjekning til at administrere  *samtidig redigering* eller oprettelse på tværs af flere brugere. 
  
Når du downloader en PDF-fil fra et IRM-beskyttet bibliotek, opretter Microsoft 365 en beskyttet PDF-fil. Filens filtypenavn ændres ikke, men filen er beskyttet. Hvis du vil have vist denne fil, skal du bruge Azure Information Protection-fremviseren, hele Azure Information Protection-klienten eller et andet program, der understøtter visning af beskyttede PDF-filer.
  
SharePoint Online understøtter kryptering af følgende filtyper:
  
- PDF
    
- Filformaterne 97-2003 til følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- Office Open XML-formaterne for følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- XPS-formatet (XML Paper Specification)
 
> [!NOTE]
> IRM-beskyttelse kan ikke anvendes på beskyttede dokumenter (f.eks. digitalt signerede PDF-filer), da SharePoint skal åbne dokumentet ved upload. 

## <a name="next-steps"></a>Næste trin
<a name="__toc220831191"> </a>

Når du har aktiveret IRM til SharePoint Online, kan du begynde at anvende rettighedsstyring på lister og biblioteker. Du kan finde flere oplysninger under [Anvend oplysninger Rights Management på en liste eller et bibliotek](apply-irm-to-a-list-or-library.md).
  
Den nye OneDrive-synkronisering klient til Windows understøtter nu synkronisering af IRM-beskyttede SharePoint dokumentbiblioteker og OneDrive placeringer (så længe IRM-indstillingen for biblioteket ikke er angivet til at udløbe dokumentadgangsrettigheder). Du kan få flere oplysninger eller komme i gang med at installere den nye synkroniseringsklient under [Installér den nye OneDrive-synkronisering klient til Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)
