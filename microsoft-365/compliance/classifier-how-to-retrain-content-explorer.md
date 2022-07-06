---
title: Sådan genoplæres en klassificering i Indholdsviser
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
description: Få mere at vide om, hvordan du giver feedback til en klassificering, der kan oplæres, i Indholdsoversigt.
ms.openlocfilehash: bde570b8bbb104d7f89523eb12bd8b9ac9210ad7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637433"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Sådan genoplæres en klassificering i Indholdsviser

En Klassificering, der kan oplæres i Microsoft 365, er et værktøj, du kan oplære til at genkende forskellige typer indhold ved at give den eksempler, du kan se på. Når du har oplært, kan du bruge den til at identificere elementer til anvendelse af Office-følsomhedsmærkater, politikker for overholdelse af kommunikation og politikker for opbevaringsmærkater.

I denne artikel kan du se, hvordan du kan forbedre ydeevnen for brugerdefinerede klassificeringer ved at give dem yderligere feedback.

Hvis du vil vide mere om de forskellige klassificeringstyper, skal [du se Få mere at vide om klassificeringer, der kan oplæres](classifier-learn-about.md).

Se denne video for at få en hurtig oversigt over justerings- og genoplæringsprocessen. Du skal stadig læse denne komplette artikel for at få detaljerne.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Færdiguddannede klassificeringer kan ikke oplæres igen.

## <a name="permissions"></a>Tilladelser

Sådan får du adgang til klassificeringer i Microsoft Purview-compliance-portal:

- Rollen som administrator af overholdelse eller administrator af overholdelsesdata kræves for at oplære en klassificering

Du skal bruge konti med disse tilladelser for at bruge klassificeringer i disse scenarier:

- Politikscenarie for opbevaringsmærkat: Roller til administration af poster og opbevaringsstyring 

## <a name="overall-workflow"></a>Overordnet arbejdsproces

> [!IMPORTANT]
> Du giver feedback i Indholdsoversigt for politikker for automatisk anvendelse af opbevaringsmærkat på Exchange-elementer og bruger klassificeringen som en betingelse. **Hvis du ikke har en opbevaringspolitik, der automatisk anvender en opbevaringsmærkat på Exchange-elementer og bruger en klassificering som en betingelse, skal du stoppe her.**

Når du bruger dine klassificeringer, kan det være en god idé at øge nøjagtigheden af de klassificeringer, de foretager. Det gør du ved at evaluere kvaliteten af de klassificeringer, der er foretaget for elementer, som den har identificeret som værende et match eller ikke et match. Når du har foretaget 30 evalueringer for en klassificering, tager den denne feedback og oplærer sig selv automatisk.

Hvis du vil vide mere om den overordnede arbejdsproces til genoplæring af en klassificering, skal du se [Procesforløb til genoplæring af en klassificering](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> En klassificering skal allerede publiceres og bruges, før den kan oplæres igen.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Sådan genoplæres en klassificering i Indholdsviser

1. Log på Microsoft Purview-compliance-portal med rolleadgang som overholdelsesadministrator eller sikkerhedsadministrator, og åbn **Microsoft Purview-compliance-portal** >  **Dataklassificeringsindholdsoversigt** > . 
2. Under listen **Filtrer efter mærkater, oplysningstyper eller kategorier** skal du udvide **Klassificeringer, der kan oplæres**.

> [!IMPORTANT]
> Det kan tage op til otte dage, før aggregerede elementer vises under overskriften klassificeringer, der kan oplæres.

3. Vælg den klassificering, der kan oplæres, som du brugte i politikken for automatisk anvendelse af opbevaringsmærkat. Dette er den klassificering, der kan oplæres, og som du vil give feedback på.

> [!NOTE]
> Hvis et element har en post i kolonnen **Opbevaringsmærkat** , betyder det, at elementet blev klassificeret som en `match`.  Hvis et element ikke har en post i kolonnen **Opbevaringsmærkat** , betyder det, at det er klassificeret som en `close match`. Du kan forbedre klassificeringspræcisionen mest ved at give feedback på `close match` elementer. 

4. Vælg et element, og åbn det.
 
 > [!TIP]
> Du kan give feedback på flere elementer samtidig ved at vælge dem alle og derefter vælge **Gør klassificeringen bedre** på kommandolinjen.

5. Vælg **Angiv feedback**.
6. Hvis elementet er en sand positiv i ruden **Detaljeret feedback** , skal du vælge **Match**.  Hvis elementet er falsk positivt, dvs. at det er inkluderet forkert i kategorien, skal du vælge **Ikke et match**.
7. Hvis der er en anden klassificering, der passer bedre til elementet, kan du vælge den på listen **Foreslå andre klassificeringer, der kan oplæres** . Dette udløser den anden klassificering for at evaluere elementet.
8. Vælg **Send feedback** for at sende din evaluering af klassificeringerne `match`, `not a match` og foreslå andre klassificeringer, der kan oplæres. Når du har givet 30 forekomster af feedback til en klassificering, oplæres den automatisk igen. Omskoling kan tage fra en til fire timer. Klassificeringer kan kun oplæres igen to gange om dagen.

> [!IMPORTANT]
> Disse oplysninger sendes til klassificeringen i din lejer. **De går ikke tilbage til Microsoft**.

9. Åbn **Klassificeringer, der kan oplæres**.
10. Den klassificering, der blev brugt i politikken for overholdelse af angivne standarder for kommunikation, vises under overskriften **Videreuddan** .

![klassificering i omskolingsstatus.](../media/classifier-retraining.png)

11. Når genoplæring er fuldført, skal du vælge klassificeringen for at åbne oversigten over genoplæring.

![oversigt over resultater for klassificerings omskoling.](../media/classifier-retraining-overview.png)

12. Gennemse den anbefalede handling og forudsigelsessammenligningerne for de videreudlærte og aktuelt publicerede versioner af klassificeringen.
13. Hvis du er tilfreds med resultaterne af genoplæring, skal du vælge **Publicer igen**.
14. Hvis du ikke er tilfreds med resultaterne af genoplæring, kan du vælge at give yderligere feedback til klassificeringen i grænsefladen i Indholdsoversigt og starte en anden genoplæringscyklus eller ikke gøre noget, i hvilket tilfælde den aktuelt publicerede version af klassificeringen fortsat vil blive brugt. 

## <a name="details-on-republishing-recommendations"></a>Oplysninger om genudgivelse af anbefalinger

Her er lidt information om, hvordan vi formulerer anbefalingen om at genudgive en omskolet klassificering eller foreslå yderligere omskoling. Dette kræver en lidt dybere forståelse af, hvordan klassificeringer, der kan oplæres, fungerer.

Efter en oplæring evaluerer vi klassificeringens ydeevne for både elementer med feedback og alle elementer, der oprindeligt blev brugt til at oplære klassificeringen. 

- For indbyggede modeller er elementer, der bruges til at oplære klassificeringen, de elementer, der bruges af Microsoft til at bygge modellen.
- For brugerdefinerede modeller er elementer, der bruges i den oprindelige oplæring, klassificeringen fra de websteder, du havde tilføjet til test og gennemgang.

Vi sammenligner ydelsesnumrene på begge sæt elementer for den omskolede og publicerede klassificering for at angive en anbefaling om, hvorvidt der var en forbedring ved at publicere igen. 

## <a name="see-also"></a>Se også

- [Få mere at vide om trænbare klassificeringer](classifier-learn-about.md)
- [Standardfilnavneudvidelser og fortolkede filtyper i SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
