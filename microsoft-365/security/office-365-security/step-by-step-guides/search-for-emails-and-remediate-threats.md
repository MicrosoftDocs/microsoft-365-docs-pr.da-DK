---
title: Søg efter mails, og afhjælp trusler ved hjælp af Threat Explorer i Microsoft 365 Defender
description: Trinnene til manuel afhjælpning i Threat Explorer i Microsoft 365 Defender, herunder hvordan du får den bedste ydeevne og de scenarier, der kræver afhjælpning.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 6bce250add79d4119f82730c05f3042f3e3dbafe
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842382"
---
# <a name="steps-to-use-manual-email-remediation-in-threat-explorer"></a>Trin til at bruge manuel mailafhjælpning i Threat Explorer

Mailafhjælpning er en allerede eksisterende funktion, der hjælper administratorer med at reagere på mails, der er trusler.

## <a name="what-youll-need"></a>Det skal du bruge
- Microsoft Defender for Office 365 plan 2
- Tilstrækkelige tilladelser (sørg for at tildele kontoen rollen [Søg og Fjern](https://sip.security.microsoft.com/securitypermissions) )

## <a name="create-and-track-the-remediation"></a>Opret og spor afhjælpningen

1. **Vælg en trussel, der skal afhjælpes** i [Threat Explorer](https://security.microsoft.com/threatexplorer) , og vælg knappen **Meddelelseshandlinger** , som giver dig mulighed for indstillinger som *Blød sletning* eller *Hård sletning*.
1. Sideruden åbnes og beder om oplysninger som f.eks. et navn på afhjælpningen, alvorsgraden og beskrivelsen. Når oplysningerne er gennemset, skal du trykke på **Send**.
1. Så snart administratoren godkender denne handling, får vedkommende vist godkendelses-id'et og et link til Microsoft 365 Defender Løsningscenter [her](https://security.microsoft.com/action-center/history). På denne side **kan handlinger spores**.

    1. **Administration handlingsbesked** – En systembesked vises i beskedkøen med navnet 'Administrativ handling sendt af en administrator'. Dette angiver, at en administrator har foretaget en afhjælpning af en enhed. Den indeholder oplysninger som f.eks. navnet på den administrator, der foretog handlingen, og linket til undersøgelsen og tid. Dette gør administratorer opmærksomme på hver vigtige handling, f.eks. afhjælpning, der udføres på enheder.
    1. **Administration handlingsundersøgelse** – Da analysen på enheder allerede blev udført af administratoren, og det var det, der førte til den udførte handling, udføres der ingen yderligere analyse af systemet. Den viser detaljer som relateret besked, enhed, der er valgt til afhjælpning, udført handling, afhjælpningsstatus, antal enheder og godkender af handlingen. Dette gør det muligt for administratorer at holde styr på undersøgelsen og handlinger, der udføres *manuelt* – en undersøgelse af en administratorhandling.
1. **Handlingslogge i Unified Action Center** – Oversigts- og handlingslogge for mailhandlinger, f.eks. blød sletning og flytning til mappen slettede elementer, er *alle tilgængelige i en centraliseret visning* under **fanen Oversigt for** Samlet **Handlingscenter** > . 
1. **Filtre i Unified Action Center** – Der er flere filtre, f.eks. afhjælpningsnavn, godkendelses-id, undersøgelses-id, status, handlingskilde og handlingstype. Disse er nyttige til at finde og spore mailhandlinger i Unified Action Center.

> [!IMPORTANT]
> Ydeevne For at opnå en bedre ydeevne skal afhjælpningen udføres i batches på *50.000 eller færre*. Begræns søgeresultatet ved hjælp af *den seneste leveringsplacering* , og udløs afhjælpning af mail, hvis mailen er i en mappe, der kan afhjælpes, f.eks. Indbakke, Uønsket, Slettet.

## <a name="scenarios-that-call-for-email-remediation"></a>Scenarier, der kræver afhjælpning via mail

Her er scenarier med afhjælpning af mail:

1. Som en del af en undersøgelse identificerer SecOps en trussel i en slutbrugers postkasse og ønsker at rydde de problemmail(r).
1. Når foreslåede mailhandlinger i AIR (Automated Investigation and Response) godkendes af SecOps, udløses afhjælpningshandlingen automatisk for den angivne mail eller mailklynge.

To manuelle mailafhjælpningsscenarier:

1. Hovedscenariet:
    1. Manuelle handlinger, der udføres på mails (f.eks. brug af Threat Explorer eller Avanceret jagt), er kun synlige i det ældre Defender for Office 365 Action Center (> gennemse > Action Center i Action Center – Microsoft 365 sikkerhed).  
1. Godkendelsesscenarie med to trin:
    1. Manuelle handlinger, der afventer godkendelse, ved hjælp af godkendelsesprocessen med to trin (1. Mailen blev føjet til afhjælpning af en analytiker, 2. Mailen blev gennemgået og godkendt af en anden analytiker).

I betragtning af de almindelige scenarier kan afhjælpning af mail udløses på tre forskellige måder.

1. **Forespørgselsbaseret afhjælpning**: Ved at vælge alle søgeresultaterne med en forespørgsel (der kan maksimalt sendes 200.000 mails).
1. **Håndplukket afhjælpning**: Vælg mails én for én ved at klikke på afkrydsningsfeltet (100 mails kan indsendes på én gang).
1. **Forespørgselsbaseret afhjælpning med udeladelser**: Vælg alle mails, og fjern derefter nogle få meddelelser manuelt (forespørgslen kan maksimalt indeholde 1.000 mails, og det maksimale antal undtagelser er 100).

## <a name="next-steps"></a>Næste trin
1. Gå til [Microsoft 365 Defender-portalen](https://security.microsoft.com), og log på.
1. Vælg **Løsningscenter** i navigationsruden.
1. Gå til fanen **Oversigt** , og klik på en ventende godkendelsesliste. Det åbner en siderude.  
1. Spor handlingsstatus i det samlede handlingscenter.

## <a name="more-information"></a>Flere oplysninger

[Få mere at vide om afhjælpning af mail](../../office-365-security/air-review-approve-pending-completed-actions.md)
