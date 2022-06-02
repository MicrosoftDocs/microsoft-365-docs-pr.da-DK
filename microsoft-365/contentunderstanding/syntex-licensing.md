---
title: Licenser til SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: high
description: Få mere at vide om licenser til SharePoint Syntex
ms.openlocfilehash: 7a7f310cb9c925fdb98a38ee12335abde91ea1db
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839324"
---
# <a name="licensing-for-sharepoint-syntex"></a>Licenser til SharePoint Syntex

Hvis du vil bruge SharePoint Syntex, skal din organisation have et abonnement på SharePoint Syntex, og hver SharePoint Syntex bruger skal have en licens. Hvis du annullerer dit SharePoint Syntex abonnement på en senere dato (eller prøveversionen udløber), kan brugerne ikke længere oprette, publicere eller køre modeller til dokumentforståelse eller formularbehandling. Derudover vil ordbankrapporter, SKOS-taksonomiimport og push af indholdstyper ikke længere være tilgængelige. Der slettes ingen modeller, indhold eller metadata, og webstedstilladelser ændres ikke.
 
> [!NOTE] 
> SharePoint Syntex er en licens til tilføjelsesprogrammet, og brugerne skal også have en licens til Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Opgaver, der kræver en licens
 
Følgende opgaver kræver en [SharePoint Syntex licens](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) til den bruger, der udfører dem:
 
- Anvendelse af en model til dokumentforståelse i et bibliotek. (Brugere uden licens kan få adgang til et indholdscenter og kan oprette modeller til dokumentforståelse der, men de kan ikke anvende dem på et dokumentbibliotek).
- Oprettelse af en formularbehandlingsmodel via indgangspunktet i et bibliotek
- Upload af indhold til et bibliotek, hvor der er anvendt en model til dokumentforståelse eller formularbehandling
- Kørsel af en model til dokumentforståelse efter behov
- Brug Premium-taksonomitjenester. (Premium taksonomitjenester omfatter import af SKOS-baserede ordsæt, push af virksomhedsindholdstyper til hubtilhørende websteder og ordbankrapporter).

Brugere uden licens kan få adgang til et indholdscenter og kan oprette modeller til dokumentforståelse der, men kan ikke anvende dem på et dokumentbibliotek.
 
## <a name="cost-of-training-and-running-models"></a>Omkostninger til oplæring og kørsel af modeller
 
Omkostningerne til oplæring og kørsel af modeller til dokumentforståelse er inkluderet i omkostningerne til en SharePoint Syntex licens. Formularbehandlingsmodeller bruger dog AI Builder-kapacitet til både oplæring og kørselsbehandling. Kapaciteten skal allokeres til det Power Apps miljø, hvor du skal bruge AI Builder.

For hver SharePoint Syntex licens tildeles du 3.500 AI Builder-kreditter pr. licens pr. måned, der er samlet på lejerniveau, med en maksimal tildeling på 1 million kreditter pr. måned. Denne allokering fornys hver måned for hver aktive SharePoint Syntex licens. Ubrugte kreditter overføres ikke fra måned til måned. 

Du kan anslå den AI Builder-kapacitet, der passer til dig, med [AI Builder-beregneren](https://powerapps.microsoft.com/ai-builder-calculator).

Hvis du planlægger at bruge et brugerdefineret Power Platform-miljø, skal du [tildele kredit til det pågældende miljø](/power-platform/admin/capacity-add-on).

Gå til [Power Platform Administration](https://admin.powerplatform.microsoft.com/resources/capacity) for at kontrollere dine kreditter og dit forbrug.
  
## <a name="additional-term-store-features"></a>Yderligere funktioner i ordbanken
 
Et abonnement på SharePoint Syntex indeholder følgende yderligere funktioner i ordbanken:
 
- Import af SKOS-baseret ordsæt
- Push af virksomhedsindholdstyper til et hubwebsted, som også føjer dem til de tilknyttede websteder og eventuelle nyoprettede lister eller biblioteker
- Ordbankrapporter, der giver indsigt i publicerede ordsæt og deres brug på tværs af din lejer


## <a name="see-also"></a>Se også

[Oversigt over licenser til Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[Ofte stillede spørgsmål om Power Apps og Power Automate licenser](/power-platform/admin/powerapps-flow-licensing-faq)
