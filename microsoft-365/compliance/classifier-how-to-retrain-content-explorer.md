---
title: Sådan omskoling af en klassificering i indholdsstifinder
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du giver feedback til en god klassificering i Indholdsstifinder.
ms.openlocfilehash: bbc724b94997a4668115314df0c627dcfa5ddc77
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589811"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Sådan omskoling af en klassificering i indholdsstifinder

En Microsoft 365 klassekammerat er et værktøj, du kan træne til at genkende forskellige typer indhold ved at give den eksempler, du kan kigge på. Når du er blevet trænet, kan du bruge den til at identificere elementer til anvendelse Office følsomhedsmærkater, politikker for overholdelse af kommunikation og opbevaringsetiketpolitikker.

I denne artikel kan du se, hvordan du kan forbedre ydeevnen for brugerdefinerede klassificeringer, der kan trænes, ved at give dem yderligere feedback.

Hvis du vil have mere at vide om de forskellige typer klassificeringer, skal du [se Få mere at vide om trænbare klassificeringer](classifier-learn-about.md).

Se denne video for at få en hurtig oversigt over justerings- og omskodningsprocessen. Du skal stadig læse denne hele artikel for at få flere oplysninger.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Pre-trained classifiers cannot betrained.

## <a name="permissions"></a>Tilladelser

Sådan får du adgang til klassificeringer i Microsoft 365 Compliance Center:

- Overholdelsesadministratorrollen eller dataadministratoren for overholdelse af regler og standarder er påkrævet for at kunne oplære en klassificering

Du skal bruge konti med disse tilladelser for at bruge klassificeringer i disse scenarier:

- Scenarie for opbevaringsetiketpolitik: Roller for administration af poster og opbevaringsstyring 

## <a name="overall-workflow"></a>Samlet arbejdsproces

> [!IMPORTANT]
> Du giver feedback i Indholdsstifinder for automatisk at anvende opbevaringsmærkatpolitikker på Exchange elementer og bruger klassificeringen som en betingelse. **Hvis du ikke har en opbevaringspolitik, der automatisk anvender et opbevaringsmærkat på elementer Exchange en klassificering som en betingelse, skal du stoppe her.**

Når du bruger dine klassificeringer, kan det være en ide at øge præcisionen af de klassificeringer, de laver. Det gør du ved at evaluere kvaliteten af de klassificeringer, der er foretaget for elementer, den har identificeret som værende en match eller ej. Når du har foretaget 30 evalueringer for en klassificering, kræver det denne feedback og omskolinger automatisk sig selv.

Hvis du vil have mere at vide om den overordnede arbejdsproces for omskoling af en klassificering, skal du se [Procesflow til omskoling af en klassificering](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> En klassificering skal allerede være publiceret og i brug, før den kan omskolingeres.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Sådan omskoling af en klassificering i indholdsstifinder

1. Log på Microsoft 365 Overholdelsescenter med adgang til overholdelsesadministrator eller sikkerhedsadministratorrolle, og **åbn Microsoft 365 Overholdelsescenter** >  **Data** **classificationContent** >  Explorer. 
2. Under listen **Filtrer på etiketter, oplysningstyper eller** kategorier skal du udvide **Klassificeringer, der kan trænes**.

> [!IMPORTANT]
> Det kan tage op til otte dage, før samlede elementer vises under overskriften med de sammensatte klassificeringer.

3. Vælg den kørebare klassificering, du har brugt i din automatiske opbevaringsmærkatpolitik. Dette er den oplærende klassificering, du vil give feedback på.

> [!NOTE]
> Hvis et element har en post i kolonnen **Opbevaringsnavn** , betyder det, at elementet er blevet klassificeret som en `match`.  Hvis et element ikke har en post i kolonnen **Opbevaringsnavn** , betyder det, at det er klassificeret som en `close match`. Du kan forbedre klassificeringspræcisionen mest ved at give feedback på `close match` elementer. 

4. Vælg et element, og åbn det.
 
 > [!TIP]
> Du kan give feedback på flere elementer samtidig ved at vælge dem alle og derefter vælge **Forbedring af** klassificering på kommandolinjen.

5. Vælg **Giv feedback**.
6. Hvis elementet **i** ruden Detaljeret feedback er sandt, skal du vælge **Match**.  Hvis elementet er en falsk positiv, er det, at det er blevet medtaget forkert i kategorien, skal du **vælge Ikke et match**.
7. Hvis der er en anden klassificering, der er mere passende for elementet, kan du vælge den på listen Foreslå andre **klassificeringer, der kan bruges.** Dette udløser den anden klassificering til at evaluere elementet.
8. Vælg **Send feedback** for at sende din evaluering af `match`, `not a match` klassificeringer og foreslå andre klassificerede klassificeringer, der kan trænes. Når du har angivet 30 forekomster af feedback til en klassificering, omskolinger den automatisk. Omskoling kan tage fra én til fire timer. Klassificeringer kan kun omskoling to gange pr. dag.

> [!IMPORTANT]
> Disse oplysninger går til klassificeringen i din lejer og **går ikke tilbage til Microsoft**.

9. Åbn **Klassekammerater, der kan trænes**.
10. Den klassificering, der blev brugt i din politik for overholdelse af kommunikation, vises under **overskriften Genkursus** .

![klassificering i omskolingsstatus.](../media/classifier-retraining.png)

11. Når omskodningen er fuldført, skal du vælge klassificeringen for at åbne oversigten over omskoling.

![Oversigt over resultater ved omskoling af klassificering.](../media/classifier-retraining-overview.png)

12. Gennemse den anbefalede handling og forudsigelsessammenligninger af de omskolings- og aktuelt publicerede versioner af klassificeringen.
13. Hvis du er tilfreds med resultaterne af omskodningen, skal du **vælge Publicer igen**.
14. Hvis du ikke er tilfreds med resultaterne af omskodningen, kan du vælge at give yderligere feedback til klassificeringen i indholdsstifinderens grænseflade og starte en anden omskodningscyklus, eller du kan ikke gøre noget, hvorefter den aktuelt publicerede version af klassificeringen fortsat bruges. 

## <a name="details-on-republishing-recommendations"></a>Detaljer om genpublicering af anbefalinger

Her er lidt oplysninger om, hvordan vi formulerer anbefalingen om at udgive en omskolingsklasse eller foreslå yderligere omskoling. Dette kræver lidt større forståelse af, hvordan klassificerede klassificeringer, der kan trænes, fungerer.

Efter en omskoling evaluerer vi klassificeringens ydeevne på både elementerne med feedback og de elementer, der oprindeligt blev brugt til at oplære klassificeringen. 

- For indbyggede modeller er de elementer, der bruges til at oplære klassificeringen, de elementer, der bruges af Microsoft til at opbygge modellen.
- For brugerdefinerede modeller er de elementer, der blev brugt i det oprindelige kursus, klassificeringen, fra de websteder, du har tilføjet til test og gennemgang.

Vi sammenligner ydelsesnumrene på begge sæt af elementer for omskolings- og publiceret klassificering for at give en anbefaling om, hvorvidt der er sket en forbedring i forbindelse med genpublicering. 

## <a name="see-also"></a>Se også

- [Få mere at vide om klassekammerater, der kan trænes](classifier-learn-about.md)
- [Standard for gennemsøgte filtypenavne og fortolkede filtyper i SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)