---
title: Vurder virkningen af ændringer af sikkerhedskonfigurationen med Stifinder
description: Eksempler på og gennemgang af brugen af Stifinder til at fastslå virkningen af en ændring af sikkerhedskontrol (konfiguration) i Microsoft Defender for Office 365
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: b710fe78c141cd1f2c0b4461ded6e3f485276616
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859011"
---
# <a name="assess-the-impact-of-security-configuration-changes-with-explorer"></a>Vurder virkningen af ændringer af sikkerhedskonfigurationen med Stifinder

Før du foretager ændringer af din sikkerhedskonfiguration, f.eks. politikker eller transportregler, er det vigtigt at forstå virkningen af ændringerne, så du kan planlægge og sikre *minimal* afbrydelse for din organisation.

Denne trinvise vejledning fører dig gennem vurdering af en ændring og eksport af de berørte mails til vurdering. Proceduren kan anvendes på mange forskellige ændringer ved at ændre de kriterier (filtre), du bruger i Stifinder.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 2 (inkluderet som en del af E5).
- Tilstrækkelige tilladelser (Minimumkrav til sikkerhedslæser for at vurdere via Threat Explorer).
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="assess-changing-normal-confidence-phish-delivery-location-to-quarantine-from-the-junk-email-folder"></a>Vurder ændring af den normale placering til levering af tillid til karantæne (fra mappen Uønsket mail)

1. **Log på** sikkerhedsportalen, og naviger til Stifinder (under *Mail & Samarbejde* i venstre navigationsrude) <https://security.microsoft.com/threatexplorer>.
1. Vælg **Phish** under den øverste fanevalg (*Alle mails* er standardvisningen).
1. Tryk på **filterknappen** (som standard *Afsender*), og vælg **Phish-konfidensniveau**.
1. Vælg **niveauet Phish-konfidens** for **Normal**.
1. Tilføj et ekstra **filter** for **den oprindelige leveringsplacering** , der er angivet som **mappen Uønsket mail**.
1. Tryk på **Opdater**. Explorer er nu filtreret til at vise alle de mails, der registreres som *phish med høj genkendelsessikkerhed* , og som leveres til mappen Uønsket mail på grund af indstillingerne i politikken for anti-spam.
1. Hvis du vil pivotere de data, der vises i diagrammet, kan du gøre det ved hjælp **af dataudsnittet øverst til venstre i diagrammet (som standard *handlingen Levering*)** og vælge nyttige data som f.eks **. Afsenders IP** eller **Afsenderdomæne** for at spotte tendenser og de mest berørte afsendere.
1. Under diagramafsnittet, hvor de berørte mails vises, skal du vælge **Eksportér mailliste**, som genererer en CSV til offlineanalyse. **Dette er en liste over de mails, der vil blive sat i karantæne, hvis phish-handlingen blev ændret til Karantæne (anbefalet ændring for både standardindstillinger og strenge forudindstillinger)**.

## <a name="assess-removing-a-sender--domain-override-removal"></a>Vurder fjernelse af afsender/domænetilsidesættelse

1. **Log på** sikkerhedsportalen, og naviger til **Stifinder** (under Mail & Samarbejde i venstre navigationsrude) <https://security.microsoft.com/threatexplorer>.
1. Vælg **Alle mails** , hvis de ikke allerede er valgt.
1. Tryk på **filterknappen** (som standard *Sender*), og tilføj enten et domænefilter for afsender eller afsender, og tilføj derefter den post, hvor du vil vurdere virkningen af fjernelsen.
1. Udvid datointervallet til det maksimale & tryk på **Opdater** . Du kan nu se mails, der er angivet, hvis afsenderen/afsendelsesdomænet stadig er aktivt i din organisation. Hvis *du ikke* har brug for at finjustere filteret, eller alternativt modtager du ikke længere mail fra det pågældende domæne/den pågældende afsender og kan fjerne posten sikkert.
1. Hvis der vises en post, betyder det, at posten stadig er en aktiv afsender. Pivoter dataene i diagrammet ved hjælp af dataudsnit (som standard angivet til *Leveringshandling*) til **registreringsteknologi**.
1. Diagrammet skal opdateres, og hvis der nu ikke vises nogen data, betyder det, at vi ikke har registreret nogen trusler mod nogen af de mails, der tidligere blev vist, hvilket angiver, at en tilsidesættelse ikke er nødvendig, da der ikke er nogen registrering, der skal tilsidesættes.
1. Hvis der vises data, når dataene er opdelt i udsnit efter **registreringsteknologi**, betyder det, at fjernelsen af tilsidesættelsen *vil* have indflydelse på denne afsender/domæne, fordi beskyttelsesstakken udfører en handling.
1. Du bør undersøge mailen yderligere for at vurdere, om den virkelig er ondsindet, og om posten kan fjernes, eller om den er falsk *positiv* og bør afhjælpes, så den ikke længere fejlagtigt registreres som en trussel (godkendelse er den største årsag til falske positiver).

### <a name="further-reading"></a>Yderligere læsning

Overvej at bruge sikre forudindstillinger [for at sikre, at du altid har de optimale sikkerhedskontroller med forudindstillede sikkerhedspolitikker](/microsoft-365/security/office-365-security/step-by-step-guides/ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies)

Du kan også administrere problemer med godkendelse af mail med spoof [intelligence-indsigt i Spoof intelligence](/microsoft-365/security/office-365-security/learn-about-spoof-intelligence)

Få mere at vide om [mailgodkendelse via mailgodkendelse i Exchange Online Protection](/microsoft-365/security/office-365-security/email-validation-and-authentication)
