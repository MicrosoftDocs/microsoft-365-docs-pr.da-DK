---
title: Fejlfinding af informationsbarrierer
description: Brug denne artikel som en vejledning til fejlfinding af informationsbarrierer.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de415ba7b68df786ead038bb72465c445a86ba5a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 09/12/2021
ms.locfileid: "63587680"
---
# <a name="troubleshooting-information-barriers"></a>Fejlfinding af informationsbarrierer

[Informationsbarrierer](information-barriers.md) kan hjælpe organisationen med at overholde lovmæssige krav og branchebestemmelser. Med informationsbarrierer kan du f.eks. begrænse kommunikationen mellem bestemte grupper af brugere for at undgå en i konflikt med hinanden eller andre problemer. (Du kan få mere at vide om, hvordan du konfigurerer informationsbarrierer under [Definere politikker for informationsbarrierer](information-barriers-policies.md).)

I tilfælde af at folk løber ind i uventede problemer, når informationsbarriererne er på plads, er der nogle trin, du kan tage for at løse disse problemer. Brug denne artikel som vejledning.

> [!IMPORTANT]
> For at udføre de opgaver, der er beskrevet i denne artikel, skal du have tildelt en passende rolle, f.eks. en af følgende:<br/>- Microsoft 365 Enterprise global administrator<br/>- global administrator<br/>- Overholdelsesadministrator<br/>- Administration af IB-overholdelse (dette er en ny rolle!)<p>Du kan få mere at vide om forudsætninger for informationsbarrierer under Forudsætninger [(for informationsbarrierepolitikker)](information-barriers-policies.md#prerequisites).<p>Sørg for at [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="issue-users-are-unexpectedly-blocked-from-communicating-with-others-in-microsoft-teams"></a>Problem: Brugere er uventet blokeret fra at kommunikere med andre Microsoft Teams 

I dette tilfælde rapporterer folk uventede problemer med at kommunikere med andre Microsoft Teams. Her er nogle eksempler:

- En bruger søger efter, men kan ikke finde, en anden bruger i Microsoft Teams.
- En bruger kan finde, men kan ikke vælge, en anden bruger Microsoft Teams.
- En bruger kan se en anden bruger, men kan ikke sende meddelelser til den anden bruger Microsoft Teams.

### <a name="what-to-do"></a>Hvad kan du gøre?

Afgør, om brugerne påvirkes af en informationsbarrierepolitik. Afhængigt af hvordan politikkerne er konfigureret, fungerer informationsbarrierer muligvis som forventet. Eller det kan være, at du er nødt til at indskrænke organisationens politikker.

1. Brug **cmdlet'en Get-InformationBarrierRecipientStatus** med identity-parameteren. 

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity` <p> Du kan bruge en hvilken som helst identitetsværdi, der entydigt identificerer hver modtager, f.eks. Navn, Alias, Entydigt navn (DN), Canonical DN, Mailadresse eller GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb` <p> I dette eksempel bruger vi et alias (*meganb*) for identity-parameteren. Denne cmdlet returnerer oplysninger, der angiver, om brugeren er påvirket af en informationsbarrierepolitik. (Se efter *ExoPolicyId: \<GUID>.) |

    **Hvis brugerne ikke er inkluderet i informationsbarrierepolitikker, skal du kontakte support**. Ellers skal du fortsætte til næste trin.

2. Find ud af, hvilke segmenter der er inkluderet i en informationsbarrierepolitik. For at gøre dette skal du bruge `Get-InformationBarrierPolicy` cmdlet'en med Identity-parameteren. 

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-InformationBarrierPolicy` <p> Brug oplysninger, f.eks. den politik-GUID (ExoPolicyId), du modtog i det forrige trin, som en identitetsværdi. | `Get-InformationBarrierPolicy -Identity b42c3d0f-49e9-4506-a0a5-bf2853b5df6f` <p> I dette eksempel får vi detaljerede oplysninger om informationsbarrierepolitikken, der har ExoPolicyId *b42c3d0f-49e9-4506-a0a5-bf2853b5df6f*. |

    Når du har kørt cmdlet'en, skal du i resultaterne se efter **Værdierne TildeltSegment****,** Tilladte Segmenter og **SegmenterBlokerede** værdier.

    Når du f.eks. har kørt `Get-InformationBarrierPolicy` cmdlet'en, så vi følgende i vores liste over resultater:

    ```powershell
    AssignedSegment : Sales
    SegmentsAllowed : {}
    SegmentsBlocked : {Research}
    ```

    I dette tilfælde kan vi se, at en informationsbarrierepolitik påvirker personer, der er i segmenterne Salg og Research. I dette tilfælde er sælgere forhindret i at kommunikere med personer i Research.

    Hvis det ser rigtigt ud, fungerer informationsbarrierer som forventet. Hvis ikke, skal du fortsætte til næste trin.

3. Sørg for, at dine segmenter er defineret korrekt. For at gøre dette skal du bruge `Get-OrganizationSegment` cmdlet'en og gennemse listen over resultater.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-OrganizationSegment`<p> Brug denne cmdlet sammen med en identitetsparameter. | `Get-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <p> I dette eksempel får vi oplysninger om det segment, der har GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

    Gennemgå detaljerne for segmentet. Hvis det er [nødvendigt, skal](information-barriers-edit-segments-policies.md#edit-a-segment) du redigere et segment og derefter bruge `Start-InformationBarrierPoliciesApplication` cmdlet'en igen.

    **Hvis du stadig har problemer med din politik for informationsbarrierer, skal du kontakte support**.

## <a name="issue-communications-are-allowed-between-users-who-should-be-blocked-in-microsoft-teams"></a>Problem: Kommunikation er tilladt mellem brugere, der skal blokeres i Microsoft Teams

I dette tilfælde kan personer, der skulle være forhindret i at kommunikere med hinanden, på en eller anden måde chatte med og ringe til hinanden i Microsoft Teams, selvom der er definerede, aktive informationsbarrierer.

### <a name="what-to-do"></a>Hvad kan du gøre?

Kontrollér, at de pågældende brugere er inkluderet i en informationsbarrierepolitik. 

1. Brug **cmdlet'en Get-InformationBarrierRecipientStatus** med identitetsparametre.

    |**Syntaks** _|_ *Example**|
    |:----------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver enkelt bruger, f.eks. navn, alias, entydigt navn, ved navn, mailadresse eller GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> I dette eksempel henviser vi til to brugerkonti i Office 365: *Meganb* for *Megan* og *alexw* for *Alex*. |

    > [!TIP]
    > Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`

2. Gennemgå resultaterne. **Cmdlet'en Get-InformationBarrierRecipientStatus** returnerer oplysninger om brugere, f.eks. attributværdier og eventuelle politikker for informationsbarrierer, der anvendes.

    Gennemse resultaterne, og tag derefter de næste skridt, som beskrevet i følgende tabel:

    |**Resultater**|**Hvad du så skal gøre**|
    |:----------|:------------------|
    | Der vises ingen segmenter for de valgte brugere | Gør et af følgende:<br/>- Tildel brugere til et eksisterende segment ved at redigere deres brugerprofiler i Azure Active Directory. (Se [Konfigurer egenskaber for brugerkonti med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).)<br/>- Definere et segment ud fra en [understøttet attribut for informationsbarrierer](information-barriers-attributes.md). Derefter skal du enten [definere en ny politik](information-barriers-policies.md#part-2-define-information-barrier-policies) eller [redigere en eksisterende politik for](information-barriers-edit-segments-policies.md#edit-a-policy) at medtage det pågældende segment. |
    | Segmenter vises, men der tildeles ingen politikker for informationsbarrierer til disse segmenter | Gør et af følgende:<br/>- [Definer en ny politik for informationsbarrierer](information-barriers-policies.md#part-2-define-information-barrier-policies) for hvert segment, der er tale om <br/>- [Rediger en eksisterende politik for informationsbarriere](information-barriers-edit-segments-policies.md#edit-a-policy) for at tildele den til det korrekte segment |
    | Segmenter vises, og hver af dem er inkluderet i en informationsbarrierepolitik | - Kør `Get-InformationBarrierPolicy` cmdlet'en for at bekræfte, at politikker for informationsbarrierer er aktive<br/>- Kør `Get-InformationBarrierPoliciesApplicationStatus` cmdlet'en for at bekræfte, at politikkerne anvendes<br/>- Kør `Start-InformationBarrierPoliciesApplication` cmdlet'en for at anvende alle politikker for barriere for aktive oplysninger |

## <a name="issue-i-need-to-remove-a-single-user-from-an-information-barrier-policy"></a>Problem: Jeg er nødt til at fjerne en enkelt bruger fra en politik for informationsbarriere

I dette tilfælde træder politikker for informationsbarrierer i kraft, og en eller flere brugere er uventet blokeret fra at kommunikere med andre Microsoft Teams. I stedet for helt at fjerne informationsbarrierepolitikker kan du fjerne en eller flere individuelle brugere fra politikker for informationsbarrierer.

### <a name="what-to-do"></a>Hvad kan du gøre?

Politikker for informationsbarrierer tildeles til segmenter af brugere. Segmenter defineres ved hjælp af [bestemte attributter i brugerkontoprofiler](information-barriers-attributes.md). Hvis du skal fjerne en politik fra en enkelt bruger, bør du overveje at redigere den pågældende brugers profil i Azure Active Directory således, at brugeren ikke længere er en del af et segment, der er påvirket af informationsbarrierer.

1. Brug **cmdlet'en Get-InformationBarrierRecipientStatus** med identitetsparametre. Denne cmdlet returnerer oplysninger om brugere, f.eks. attributværdier og eventuelle politikker for informationsbarrierer, der anvendes.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver enkelt bruger, f.eks. navn, alias, entydigt navn, ved navn, mailadresse eller GUID. | `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> I dette eksempel henviser vi til to brugerkonti i Office 365: *Meganb* for *Megan* og *alexw* for *Alex*.          |
    | `Get-InformationBarrierRecipientStatus -Identity <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer brugeren, f.eks. navn, alias, entydigt navn, ved navn, mailadresse eller GUID.|`Get-InformationBarrierRecipientStatus -Identity jeanp`<p> I dette eksempel henviser vi til en enkelt konto i Office 365: *jeanp*. |

2. Gennemse resultaterne for at se, om politikker for informationsbarrierer er tildelt, og til hvilke segment(er) brugeren/brugerne tilhører.

3. Hvis du vil fjerne en bruger fra et segment, der er påvirket af informationsbarrierer, skal du opdatere brugerens [profiloplysninger Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

4. Vent ca. 30 minutter, før FwdSync forekommer. Eller kør `Start-InformationBarrierPoliciesApplication` cmdlet'en for at anvende alle politikker for barriere for aktive oplysninger.

## <a name="issue-the-information-barrier-application-process-is-taking-too-long"></a>Problem: Processen med at applikationen af informationsbarrierer tager for lang tid

Når du har **kørt cmdlet'en Start-InformationBarrierPoliciesApplication** , tager det meget lang tid at afslutte processen.

### <a name="what-to-do"></a>Hvad kan du gøre?

Husk på, at når du kører cmdlet'en med politikprogrammet, anvendes (eller fjernes informationsbarrierepolitikker), bruger efter bruger, for alle konti i organisationen. Hvis du har mange brugere, tager det et stykke tid at behandle dem. (Som en generel retningslinje tager det omkring en time at behandle 5.000 brugerkonti).)

1. Brug **cmdlet'en Get-InformationBarrierPoliciesApplicationStatus** til at bekræfte status for det seneste politikprogram.

    |**Sådan får du vist det seneste politikprogram**|**Sådan får du vist status for alle politikprogrammer**|
    |:---------------------------------------------|:---------------------------------------------|
    | `Get-InformationBarrierPoliciesApplicationStatus` | `Get-InformationBarrierPoliciesApplicationStatus -All $true` |

    Dette viser oplysninger om, hvorvidt politikprogrammet er afsluttet, mislykket eller er i gang.

2. Afhængigt af resultaterne af det forrige trin skal du gøre et af følgende:
  
    |**Status**|**Næste trin**|
    |:---------|:------------|
    | **Ikke startet** | Hvis der er gået mere end 45 minutter, siden cmdlet'en **Start-InformationBarrierPoliciesApplication** blev kørt, skal du gennemse overvågningsloggen for at se, om der er nogen fejl i politikdefinitioner eller en anden årsag til, at programmet ikke er startet. |
    | **Mislykkedes** | Hvis programmet mislykkes, skal du gennemse overvågningsloggen. Gennemse også dine segmenter og politikker. Er der nogen brugere, der er tildelt mere end ét segment? Er der nogen segmenter tildelt mere end én poliicy? Hvis det er [nødvendigt, skal](information-barriers-edit-segments-policies.md#edit-a-segment) du redigere [](information-barriers-edit-segments-policies.md#edit-a-policy)segmenter og/eller redigere politikker og derefter køre **cmdlet'en Start-InformationBarrierPoliciesApplication** igen. |
    | **I gang** | Hvis programmet stadig er i gang, kan du give mere tid til, at det fuldføres. Hvis der er gået flere dage, skal du indsamle dine overvågningslogfiler og derefter kontakte support. |

## <a name="issue-information-barrier-policies-are-not-being-applied-at-all"></a>Problem: Politikker for informationsbarrierer anvendes slet ikke

I dette tilfælde har du defineret segmenter, defineret politikker for informationsbarrierer og forsøgt at anvende disse politikker. Men når du kører cmdlet'en `Get-InformationBarrierPoliciesApplicationStatus` , kan du se, at politikprogrammet mislykkedes.

### <a name="what-to-do"></a>Hvad kan du gøre?

Sørg for, at organisationen ikke har Exchange [politikkerne for adressekartoteket](/exchange/address-books/address-book-policies/address-book-policies) på plads. Sådanne politikker vil forhindre, at der anvendes politikker for informationsbarrierer.

1. Forbind til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør [cmdlet'en Get-AddressBookPolicy](/powershell/module/exchange/get-addressbookpolicy) , og gennemse resultaterne.

    |**Resultater**|**Næste trin**|
    |:----------|:------------|
    | Exchange adressekartotekspolitikker vises | [Fjerne politikker for adressekartotek](/exchange/address-books/address-book-policies/remove-an-address-book-policy) |
    | Der findes ingen politikker for adressekartotek |Gennemse dine overvågningslogfiler for at finde ud af, hvorfor politikprogrammet mislykkes |

3. [Få vist status for brugerkonti, segmenter, politikker eller politikprogram](information-barriers-policies.md#view-status-of-user-accounts-segments-policies-or-policy-application).

## <a name="issue-information-barrier-policy-not-applied-to-all-designated-users"></a>Problem: Politik for informationsbarrierer gælder ikke for alle angivne brugere

Når du har defineret segmenter, defineret politikker for informationsbarrierer og forsøgt at anvende disse politikker, kan du opleve, at politikken gælder for nogle modtagere, men ikke for andre.
Når du kører `Get-InformationBarrierPoliciesApplicationStatus` cmdlet'en, kan du søge efter tekst på denne måde i outputtet.

> Identitet: `<application guid>`
>
> Modtagere i alt: 81527
>
> Mislykkede modtagere: 2
>
> Fejlkategori: Ingen
>
> Status: Fuldført

### <a name="what-to-do"></a>Hvad kan du gøre?

1. Søg efter i overvågningsloggen efter `<application guid>`. Du kan kopiere denne PowerShell-kode og redigere for dine variabler.

```powershell
$DetailedLogs = Search-UnifiedAuditLog -EndDate <yyyy-mm-ddThh:mm:ss>  -StartDate <yyyy-mm-ddThh:mm:ss> -RecordType InformationBarrierPolicyApplication -ResultSize 1000 |?{$_.AuditData.Contains(<application guid>)} 
```

2. Kontrollér de detaljerede resultater fra overvågningsloggen for værdierne i felterne `"UserId"` og `"ErrorDetails"` . Dette giver dig årsagen til fejlen. Du kan kopiere denne PowerShell-kode og redigere for dine variabler.

```powershell
   $DetailedLogs[1] |fl
```

Eksempel:

> "Bruger-id": Bruger1
>
>"Fejldetaljer":"Status: IBPolicyConflict. Fejl: IB-segment "segment-id1" og IB-segment "segment-id2" er i konflikt og kan ikke tildeles til modtageren.

3. Normalt vil du opdage, at en bruger er blevet inkluderet i mere end ét segment. Det kan du løse ved at opdatere `-UserGroupFilter` værdien i `OrganizationSegments`.

4. Anvend politikker for informationsbarrierer igen ved hjælp af disse procedurer [politikker for informationsbarrierer](information-barriers-policies.md#part-3-apply-information-barrier-policies).

## <a name="resources"></a>Ressourcer

- [Definer politikker for informationsbarrierer i Microsoft Teams](information-barriers-policies.md)
- [Informationsbarrierer](information-barriers.md)