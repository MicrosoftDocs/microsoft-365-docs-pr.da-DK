---
title: Administrere politikker for informationsbarrierer
description: Få mere at vide om, hvordan du redigerer eller fjerner politikker og segmenter for informationsbarrierer.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.openlocfilehash: fc8cc7e4fcbfb9fe9c2ee0f1c531511d9c2fa0b6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634355"
---
# <a name="manage-information-barriers-policies"></a>Administrere politikker for informationsbarrierer

Når du har [defineret informationsbarrierepolitikker](information-barriers-policies.md), kan det være nødvendigt at foretage ændringer i politikker eller brugersegmenter som en del [af fejlfindingen](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) eller til almindelig vedligeholdelse.

## <a name="what-do-you-want-to-do"></a>Hvad vil du gøre?

|**Handling**|**Beskrivelse**|
|:---------|:--------------|
| [Redigere attributter for brugerkonto](#edit-user-account-attributes) | Udfyld attributter i Azure Active Directory, der kan bruges til at definere segmenter. <br> Rediger brugerkontoattributter, når brugerne ikke er medtaget i segmenter, de skal være, for at ændre, hvilke segmenter brugerne er i, eller for at definere segmenter ved hjælp af forskellige attributter. |
| [Rediger et segment](#edit-a-segment) | Rediger segmenter, når du vil ændre, hvordan et segment defineres. <br> Det kan f.eks. være, at du har defineret segmenter ved hjælp *af Afdeling* og nu vil bruge en anden attribut, f.eks *. MemberOf*. |
| [Rediger en politik](#edit-a-policy) | Rediger en politik for informationsbarrierer, når du vil ændre, hvordan en politik fungerer.<br> I stedet for at blokere kommunikation mellem to segmenter kan du f.eks. beslutte, at du kun vil tillade kommunikation mellem bestemte segmenter. |
| [Angive en politik til inaktiv status](#set-a-policy-to-inactive-status) |Angiv en politik til inaktiv status, når du vil foretage ændringer i en politik, eller når du ikke ønsker, at en politik skal være gældende. |
| [Fjerne en politik](#remove-a-policy) | Fjern en politik for informationsbarrierer, når du ikke længere har brug for en bestemt politik. |
| [Fjern et segment](#remove-a-segment) | Fjern et informationsbarrieresegment, når du ikke længere har brug for et bestemt segment. |
| [Fjern en politik og et segment](#remove-a-policy-and-segment) | Fjern en politik for informationsbarrierer og et segment på samme tid. |
| [Stoppe et politikprogram](#stop-a-policy-application) | Gør dette, når du vil stoppe processen med at anvende informationsbarrierepolitikker. <br> Det er ikke muligt at stoppe et politikprogram med det samme, og det fortryder ikke politikker, der allerede er anvendt for brugere. |
| [Definer politikker for informationsbarrierer](information-barriers-policies.md) | Definer en politik for informationsbarrierer, når du ikke allerede har sådanne politikker på plads, og du skal begrænse eller begrænse kommunikationen mellem bestemte grupper af brugere. |
| [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Se denne artikel, når du løber ind i uventede problemer med informationsbarrierer. |

>[!IMPORTANT]
>For at udføre de opgaver, der er beskrevet i denne artikel, skal du have tildelt en passende rolle, f.eks. en af følgende:<br>- Microsoft 365 Enterprise global administrator<br>- Global administrator<br>- Overholdelsesadministrator<br>- Administration af IB-overholdelse (dette er en ny rolle!)<br><br>Du kan få mere at vide om forudsætninger for [informationsbarrierer under Forudsætninger (for politikker for informationsbarrierer)](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met).<br><br> Sørg for at [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Redigere attributter for brugerkonto

Brug denne fremgangsmåde til at redigere attributter, der bruges til segmentering af brugere. Hvis du f.eks. bruger attributten Afdeling, og en eller flere brugerkonti i øjeblikket ikke har nogen værdier angivet for Afdeling, skal du redigere disse brugerkonti, så de omfatter afdelingsoplysninger. Attributter for brugerkonti bruges til at definere segmenter, så politikker for informationsbarrierer kan tildeles.

1. Hvis du vil have vist detaljer om en bestemt brugerkonto, f.eks. attributværdier og tildelte segment(er), skal du bruge cmdlet'en **Get-InformationBarrierRecipientStatus** med identitetsparametre.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver enkelt bruger, f.eks. navn, alias, entydigt navn, ved navn, mailadresse eller GUID. <br> (Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> I dette eksempel henviser vi til to brugerkonti i Office 365: *Meganb* for *Megan* og *alexw* for *Alex*. |

2. Find ud af, hvilken attribut du vil redigere for din brugerkontoprofil.(e). Få mere at vide under [Attributter for informationsbarrierepolitikker](information-barriers-attributes.md).

3. Rediger en eller flere brugerkonti for at medtage værdier for den attribut, du valgte i forrige trin. Benyt en af følgende fremgangsmåder for at gøre dette:

    - Hvis du vil redigere en enkelt konto, [skal du se Tilføje eller opdatere en brugers profiloplysninger ved hjælp Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Hvis du vil redigere flere konti (eller bruge PowerShell til at redigere en enkelt konto), skal du se Konfigurere egenskaber [for brugerkonti Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Rediger et segment

Brug denne procedure til at redigere definitionen af et brugersegment. Du kan f.eks. ændre navnet på et segment eller det filter, der bruges til at bestemme, hvem der er medtaget i segmentet.

1. For at få vist alle eksisterende segmenter skal du **bruge cmdlet'en Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, dens UserGroupFilter-værdi, hvem der har oprettet eller senest ændret den, GUID osv.

    > [!TIP]
    > Udskriv eller gem listen over segmenter til senere brug. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificere værdi (dette bruges med identity-parameteren).

2. Hvis du vil redigere et segment, skal **du bruge cmdlet'en Set-OrganizationSegment** med **identitetsparameteren** og relevante detaljer.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> I dette eksempel har vi opdateret afdelingsnavnet til *HRDept* for segmentet med GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Når du er færdig med at redigere segmenter for organisationen, kan du enten [definere](information-barriers-policies.md#step-3-define-information-barrier-policies) eller [redigere politikker for](#edit-a-policy) informationsbarrierer.

## <a name="edit-a-policy"></a>Rediger en politik

1. Hvis du vil have vist en liste over aktuelle informationsbarrierepolitikker, skal du bruge **Get-InformationBarrierPolicy-cmdlet'en** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil ændre, på listen over resultater. Bemærk politikkens GUID og navn.

2. Brug **cmdlet'en Set-InformationBarrierPolicy med en Identity-parameter**, og angiv de ønskede ændringer.

    Eksempel: Antag, at en politik er defineret til at blokere *researchsegmentet* fra kommunikation *med salgs-* og *marketingsegmenter* . Politikken blev defineret ved hjælp af denne cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Antag, at vi vil ændre det, så personer i *researchsegmentet* kun kan kommunikere med personer i *HR-segmentet* . For at foretage denne ændring bruger vi denne cmdlet: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    I dette eksempel har vi ændret *SegmenterBlokeret* til *Tilladte segmenter og* angivet *HR-segmentet* .

3. Når du er færdig med at redigere en politik, skal du sørge for at anvende ændringerne. (Se [Anvend politikker for informationsbarrierer](information-barriers-policies.md#step-4-apply-information-barrier-policies).)

## <a name="set-a-policy-to-inactive-status"></a>Angive en politik til inaktiv status

1. Hvis du vil have vist en liste over aktuelle informationsbarrierepolitikker, skal du bruge **Get-InformationBarrierPolicy-cmdlet'en** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil ændre (eller fjerne), på listen over resultater. Bemærk politikkens GUID og navn.

2. Hvis du vil indstille politikkens status til inaktiv, skal du bruge cmdlet'en **Set-InformationBarrierPolicy med en Identity-parameter** og parameteren *Stat* angivet til *Inaktiv*.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> I dette eksempel er politikken for informationsbarrierer, der har GUID *43c37853-ea10-4b90-a23d-ab8c9377247* , indstillet til en inaktiv status. |

3. For at anvende dine ændringer skal du **bruge cmdlet'en Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Ændringerne anvendes for hver enkelt bruger i organisationen. Hvis din organisation er stor, kan det tage 24 timer (eller flere) at gennemføre denne proces. Som et generelt retningslinje tager det omkring en time at behandle 5.000 brugerkonti.

4. På nuværende tidspunkt er en eller flere oplysningsbarrierer indstillet til inaktiv status. Herfra kan du udføre en af følgende handlinger:

    - Behold den som den er (en politik, der er indstillet til inaktiv status, har ingen indflydelse på brugere)
    - [Rediger en politik](#edit-a-policy) 
    - [Fjerne en politik](#remove-a-policy)

## <a name="remove-a-policy"></a>Fjerne en politik

1. Hvis du vil have vist en liste over aktuelle informationsbarrierepolitikker, skal du bruge **Get-InformationBarrierPolicy-cmdlet'en** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil fjerne, på listen over resultater. Bemærk politikkens GUID og navn. 

2. Kontrollér, at politikken er indstillet til inaktiv status. Hvis du vil indstille politikkens status til inaktiv, skal du bruge Set-InformationBarrierPolicy med en identitetsparameter og statusparameteren angivet til Inaktiv.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> I dette eksempel har vi angivet en politik for informationsbarrierer, der har GUID *43c37853-ea10-4b90-a23d-ab8c9377247* til en inaktiv status. |

3. Hvis du vil anvende dine ændringer på politikken, skal **du bruge cmdlet'en Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Ændringerne anvendes for hver enkelt bruger i organisationen. Hvis din organisation er stor, kan det tage 24 timer (eller flere) at gennemføre denne proces. Som et generelt retningslinje tager det omkring en time at behandle 5.000 brugerkonti.

4. Brug **cmdlet'en Remove-InformationBarrierPolicy med en Identity-parameter** .

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> I dette eksempel fjerner vi politikken, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Når du bliver bedt om det, skal du bekræfte ændringen.

## <a name="remove-a-segment"></a>Fjern et segment

1. For at få vist alle eksisterende segmenter skal du **bruge cmdlet'en Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, dens UserGroupFilter-værdi, hvem der har oprettet eller senest ændret den, GUID osv.

    >[!TIP]
    >Udskriv eller gem listen over segmenter til senere brug. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificere værdi (dette bruges med identity-parameteren).

2. Identificer det segment, der skal fjernes, og kontrollér, at den IB-politik, der er knyttet til segmentet, er blevet fjernet. Se fremgangsmåden [Fjern en politik for at](#remove-a-policy) få mere at vide.

3. Rediger det segment, der fjernes, for at fjerne brugernes relation til det pågældende segment. Denne handling opdaterer segmentdefinitionen og fjerner alle brugere fra segmentet. Du skal bruge parameteren UserGroupFilter til at fjerne tilknytning mellem brugere og segmentet, før de fjernes.

    Hvis du vil redigere et segment, skal **du bruge cmdlet'en Set-OrganizationSegment** med *identitetsparameteren* og relevante detaljer.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> I dette eksempel, for det segment, der har GUID-c96e0837-c232-4a8a-841e-ef45787d8fcd, definerede vi afdelingsnavnet som *FalskDept* for at fjerne brugere fra segmentet. I dette eksempel bruges *attributten* Afdeling, men du kan bruge andre attributter efter behov. I eksemplet bruges *FalskDept* , da dette ikke findes og er sikkert, at de ikke indeholder nogen brugere. |

4. For at anvende dine ændringer skal du **bruge cmdlet'en Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*Attributten CleanupGroupSegmentLink* fjerner gruppe tilknytninger med segmentet uden brugersammenknytninger.

    Ændringerne anvendes for hver enkelt bruger i organisationen. Hvis din organisation er stor, kan det tage 24 timer (eller flere) at gennemføre denne proces. Som et generelt retningslinje tager det omkring en time at behandle 5.000 brugerkonti.

5. Hvis du vil fjerne et segment, skal **du bruge cmdlet'en Remove-OrganizationSegment** med *identity-parameteren* og relevante detaljer.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> I dette eksempel er det segment, der indeholder GUID-c96e0837-c232-4a8a-841e-ef45787d8fcd, fjernet. |

## <a name="remove-a-policy-and-segment"></a>Fjern en politik og et segment

1. Hvis du vil have vist en liste over aktuelle informationsbarrierepolitikker, skal du bruge **Get-InformationBarrierPolicy-cmdlet'en** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil fjerne, på listen over resultater. Bemærk politikkens GUID og navn.

2. For at få vist alle eksisterende segmenter skal du **bruge cmdlet'en Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, dens *UserGroupFilter-parameterværdi* , hvem der har oprettet eller senest ændret den, GUID osv.

    >[!TIP]
    >Udskriv eller gem listen over segmenter til senere brug. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificere værdi (dette bruges med identity-parameteren).

3. Hvis du vil angive status for den politik, der skal fjernes som inaktiv, skal du bruge **cmdlet'en Set-InformationBarrierPolicy** med parameteren *Identity* og parameteren *Stat* angivet til *Inaktiv*.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> I dette eksempel har vi angivet en politik for informationsbarrierer, der har GUID 43c37853-ea10-4b90-a23d-ab8c93772471 til en inaktiv status. |

4. Rediger det segment, der fjernes, for at fjerne brugernes relation til det pågældende segment. Denne handling opdaterer segmentdefinitionen og fjerner alle brugere fra segmentet. Du skal bruge *parameteren UserGroupFilter* til at fjerne tilknytning mellem brugere og segmentet, før de fjernes.

    Hvis du vil redigere et segment, skal **du bruge cmdlet'en Set-OrganizationSegment** med *identitetsparameteren* og relevante detaljer.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> I dette eksempel har vi for det segment, der indeholder GUID-c96e0837-c232-4a8a-841e-ef45787d8fcd, opdateret afdelingsnavnet til *FalskDept* for at fjerne brugere fra segmentet. I dette eksempel bruges *attributten* Afdeling, men du kan bruge andre attributter efter behov. I eksemplet bruges *FalskDept* , da dette ikke findes og er sikkert, at de ikke indeholder nogen brugere. |

5. For at anvende dine ændringer skal du **bruge cmdlet'en Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*Attributten CleanupGroupSegmentLink* fjerner gruppe tilknytninger med segmentet uden brugersammenknytninger.

    Ændringerne anvendes for hver enkelt bruger i organisationen. Hvis din organisation er stor, kan det tage 24 timer (eller flere) at gennemføre denne proces. Som et generelt retningslinje tager det omkring en time at behandle 5.000 brugerkonti.

6. Brug **cmdlet'en Remove-InformationBarrierPolicy** med en *Identity-parameter* .

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> I dette eksempel fjernes politikken, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471* . |

    Når du bliver bedt om det, skal du bekræfte ændringen.

7. Hvis du vil fjerne et segment, skal **du bruge cmdlet'en Remove-OrganizationSegment** med *identity-parameteren* og relevante detaljer.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> I dette eksempel blev segmentet med GUID c96e0837-c232-4a8a-841e-ef45787d8fcd fjernet. |

## <a name="stop-a-policy-application"></a>Stoppe et politikprogram

Når du er begyndt at anvende informationsbarrierepolitikker, og du vil forhindre, at disse politikker anvendes, skal du bruge følgende procedure. Det tager ca. 30-35 minutter, før processen starter.

1. Hvis du vil have vist status for det seneste program til informationsbarrierepolitik, skal du bruge **cmdlet'en Get-InformationBarrierPoliciesApplicationStatus** .

    Syntaks: `Get-InformationBarrierPoliciesApplicationStatus`

    Bemærk programmets GUID.

2. Brug **cmdlet'en Stop-InformationBarrierPoliciesApplication** med en Identity-parameter.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> I dette eksempel forhindrer vi brug af informationsbarrierepolitikker. |

## <a name="resources"></a>Ressourcer

- [Få et overblik over informationsbarrierer](information-barriers.md)
- [Definer politikker for informationsbarrierer](information-barriers-policies.md)
- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer OneDrive](/onedrive/information-barriers)
- [Attributter for politikker for informationsbarrierer](information-barriers-attributes.md)
- [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)