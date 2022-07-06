---
title: Administrer politikker for informationsbarrierer
description: Få mere at vide om, hvordan du redigerer eller fjerner politikker for informationsbarrierer.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, informationsbarrierer
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
ms.openlocfilehash: a84b8e712de53b0abae81a05bbe1b2bef3237beb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635299"
---
# <a name="manage-information-barriers-policies"></a>Administrer politikker for informationsbarrierer

Når du har [defineret politikker for informationsbarrierer (IB),](information-barriers-policies.md) skal du muligvis foretage ændringer af disse politikker eller af dine brugersegmenter som en del af [fejlfinding](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) eller som regelmæssig vedligeholdelse.

## <a name="what-do-you-want-to-do"></a>Hvad vil du foretage dig?

|**Handling**|**Beskrivelse**|
|:---------|:--------------|
| [Rediger brugerkontoattributter](#edit-user-account-attributes) | Udfyld attributter i Azure Active Directory, der kan bruges til at definere segmenter. <br> Rediger brugerkontoattributter, når brugerne ikke er inkluderet i de segmenter, de skal være, for at ændre, hvilke segmenter brugerne befinder sig i, eller for at definere segmenter ved hjælp af forskellige attributter. |
| [Rediger et segment](#edit-a-segment) | Rediger segmenter, når du vil ændre, hvordan et segment defineres. <br> Du kan f.eks. have defineret segmenter, der bruger *Afdeling* , og nu vil bruge en anden attribut, f.eks *. MemberOf*. |
| [Rediger en politik](#edit-a-policy) | Rediger en politik for informationsbarrierer, når du vil ændre, hvordan en politik fungerer.<br> I stedet for at blokere kommunikation mellem to segmenter kan du f.eks. beslutte, at du kun vil tillade kommunikation mellem bestemte segmenter. |
| [Angiv en politik til inaktiv status](#set-a-policy-to-inactive-status) |Angiv en politik til inaktiv status, når du vil foretage ændringer af en politik, eller når du ikke ønsker, at en politik skal være i kraft. |
| [Fjern en politik](#remove-a-policy) | Fjern en politik for informationsbarrierer, når du ikke længere har brug for en bestemt politik på plads. |
| [Fjern et segment](#remove-a-segment) | Fjern et informationsbarrieresegment, når du ikke længere har brug for et bestemt segment. |
| [Fjern en politik og et segment](#remove-a-policy-and-segment) | Fjerne en politik for informationsbarrierer og et segment på samme tid. |
| [Stop et politikprogram](#stop-a-policy-application) | Tag denne handling, når du ønsker at stoppe processen med at gennemføre politikker om informationsbarrierer. <br> Det er ikke øjeblikkeligt at stoppe et politikprogram, og det fortryder ikke politikker, der allerede er anvendt på brugere. |
| [Definer politikker for informationsbarrierer](information-barriers-policies.md) | Definer en politik for informationsbarrierer, når du ikke allerede har sådanne politikker på plads, og du skal begrænse eller begrænse kommunikationen mellem bestemte grupper af brugere. |
| [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Se denne artikel, når du støder på uventede problemer med informationsbarrierer. |

>[!IMPORTANT]
>Hvis du vil udføre de opgaver, der er beskrevet i denne artikel, skal du have tildelt en passende rolle, f.eks. en af følgende:<br>- Microsoft 365 Enterprise global administrator<br>- Global administrator<br>- Overholdelsesadministrator<br>- Administration af IB-overholdelse (dette er en ny rolle!)<br><br>Hvis du vil vide mere om forudsætninger for informationsbarrierer, skal du se [Forudsætninger (for politikker om informationsbarrierer).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Sørg for at [oprette forbindelse til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Rediger brugerkontoattributter

Brug denne procedure til at redigere attributter, der bruges til segmentering af brugere. Hvis du f.eks. bruger attributten Afdeling, og en eller flere brugerkonti i øjeblikket ikke har nogen værdier angivet for Afdeling, skal du redigere disse brugerkonti, så de indeholder oplysninger om afdeling. Brugerkontoattributter bruges til at definere segmenter, så politikker for informationsbarrierer kan tildeles.

1. Hvis du vil have vist oplysninger om en bestemt brugerkonto, f.eks. attributværdier og tildelte segmenter, skal du bruge cmdlet'en **Get-InformationBarrierRecipientStatus** med identitetsparametre.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver bruger, f.eks. navn, alias, entydigt navn, vedtaget domænenavn, mailadresse eller GUID. <br> (Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> I dette eksempel henviser vi til to brugerkonti i Office 365: *meganb* for *Megan* og *alexw* for *Alex*. |

2. Find ud af, hvilken attribut du vil redigere for din eller dine brugerprofiler. Du kan få flere oplysninger under [Attributter for politikker om informationsbarrierer](information-barriers-attributes.md).

3. Rediger en eller flere brugerkonti for at medtage værdier for den attribut, du valgte i det forrige trin. Benyt en af følgende fremgangsmåder for at udføre denne handling:

    - Hvis du vil redigere en enkelt konto, skal du se [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Hvis du vil redigere flere konti (eller bruge PowerShell til at redigere en enkelt konto), skal du se [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Rediger et segment

Brug denne procedure til at redigere definitionen af et brugersegment. Du kan f.eks. ændre navnet på et segment eller det filter, der bruges til at bestemme, hvem der er inkluderet i segmentet.

1. Hvis du vil have vist alle eksisterende segmenter, skal du bruge cmdlet'en **Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, værdien UserGroupFilter, hvem der oprettede eller senest ændrede den, GUID osv.

    > [!TIP]
    > Udskriv eller gem listen over segmenter til reference senere. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificeringsværdi (dette bruges sammen med parameteren Identity).

2. Hvis du vil redigere et segment, skal du bruge Cmdlet'en **Set-OrganizationSegment** med parameteren **Identity** og relevante oplysninger.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> I dette eksempel har vi opdateret afdelingsnavnet til *HRDept* for segmentet med GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Når du er færdig med at redigere segmenter for din organisation, kan du enten [definere](information-barriers-policies.md#step-3-create-ib-policies) eller [redigere](#edit-a-policy) politikker for informationsbarrierer.

## <a name="edit-a-policy"></a>Rediger en politik

1. Hvis du vil have vist en liste over aktuelle politikker for informationsbarrierer, skal du bruge cmdlet'en **Get-InformationBarrierPolicy** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil ændre, på listen over resultater. Bemærk politikkens GUID og navn.

2. Brug Cmdlet'en **Set-InformationBarrierPolicy** med parameteren **Identity** , og angiv de ændringer, du vil foretage.

    Eksempel: Lad os antage, at der er defineret en politik for at forhindre, at segmentet *Opslag* kommunikerer med segmenterne *Salg* og *Marketing* . Politikken blev defineret ved hjælp af denne cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Lad os antage, at vi vil ændre det, så personer i segmentet *Opslag* kun kan kommunikere med personer i *HR-segmentet* . Vi bruger denne cmdlet til at foretage denne ændring: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    I dette eksempel har vi ændret *SegmentBlokeret* til *Segmenter Tilladt* og angivet *HR-segmentet* .

3. Når du er færdig med at redigere en politik, skal du sørge for at anvende dine ændringer. (Se [Anvendelse af politikker for informationsbarrierer](information-barriers-policies.md#step-4-apply-ib-policies)).

## <a name="set-a-policy-to-inactive-status"></a>Angiv en politik til inaktiv status

1. Hvis du vil have vist en liste over aktuelle politikker for informationsbarrierer, skal du bruge cmdlet'en **Get-InformationBarrierPolicy** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil ændre (eller fjerne), på listen over resultater. Bemærk politikkens GUID og navn.

2. Hvis du vil angive politikkens status til inaktiv, skal du bruge **Set-InformationBarrierPolicy-cmdlet'en** med parameteren *Identity* og parameteren *State* angivet til *Inactive*.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> I dette eksempel angives politikken for informationsbarrierer med GUID *43c37853-ea10-4b90-a23d-ab8c9377247* til en inaktiv status. |

3. Hvis du vil anvende dine ændringer, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Ændringer anvendes bruger for bruger for din organisation. Hvis din organisation er stor, kan det tage 24 timer (eller mere), før processen er fuldført. Som en generel retningslinje tager det ca. en time at behandle 5.000 brugerkonti.

4. På nuværende tidspunkt er en eller flere politikker for informationsbarrierer indstillet til inaktiv status. Herfra kan du udføre en af følgende handlinger:

    - Bevar den, som den er (en politik, der er angivet til inaktiv status, påvirker ikke brugerne)
    - [Rediger en politik](#edit-a-policy) 
    - [Fjern en politik](#remove-a-policy)

## <a name="remove-a-policy"></a>Fjern en politik

1. Hvis du vil have vist en liste over aktuelle politikker for informationsbarrierer, skal du bruge cmdlet'en **Get-InformationBarrierPolicy** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil fjerne, på listen over resultater. Bemærk politikkens GUID og navn. 

2. Sørg for, at politikken er angivet til inaktiv status. Hvis du vil angive politikkens status til inaktiv, skal du bruge cmdlet'en Set-InformationBarrierPolicy med parameteren Identity og parameteren State angivet til Inactive.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> I dette eksempel angiver vi en politik for informationsbarrierer, der har GUID *43c37853-ea10-4b90-a23d-ab8c9377247* til en inaktiv status. |

3. Hvis du vil anvende dine ændringer på politikken, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Ændringer anvendes bruger for bruger for din organisation. Hvis din organisation er stor, kan det tage 24 timer (eller mere), før processen er fuldført. Som en generel retningslinje tager det ca. en time at behandle 5.000 brugerkonti.

4. Brug cmdlet'en **Remove-InformationBarrierPolicy** med parameteren Identity.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> I dette eksempel fjerner vi politikken med GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Når du bliver bedt om det, skal du bekræfte ændringen.

## <a name="remove-a-segment"></a>Fjern et segment

1. Hvis du vil have vist alle eksisterende segmenter, skal du bruge cmdlet'en **Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, værdien UserGroupFilter, hvem der oprettede eller senest ændrede den, GUID osv.

    >[!TIP]
    >Udskriv eller gem listen over segmenter til reference senere. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificeringsværdi (dette bruges sammen med parameteren Identity).

2. Identificer det segment, der skal fjernes, og sørg for, at den IB-politik, der er knyttet til segmentet, er fjernet. Du kan finde flere oplysninger i proceduren [Fjern en politik](#remove-a-policy) .

3. Rediger det segment, der fjernes, for at fjerne relationen mellem brugere og det pågældende segment. Denne handling opdaterer segmentdefinitionen og fjerner alle brugere fra segmentet. Du skal bruge parameteren UserGroupFilter til at fjerne tilknytningen af brugere fra segmentet, før de fjernes.

    Hvis du vil redigere et segment, skal du bruge Cmdlet'en **Set-OrganizationSegment** med parameteren *Identity* og relevante oplysninger.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> I dette eksempel har vi for det segment, der har GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, defineret afdelingsnavnet som *FakeDept* for at fjerne brugere fra segmentet. I dette eksempel bruges attributten *Afdeling* , men du kan bruge andre attributter efter behov. I eksemplet bruges *FakeDept* , fordi dette ikke findes, og det er sikkert, at det ikke indeholder nogen brugere. |

4. Hvis du vil anvende dine ændringer, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Attributten *CleanupGroupSegmentLink* fjerner gruppetilknytninger med segmentet uden brugertilknytninger.

    Ændringer anvendes bruger for bruger for din organisation. Hvis din organisation er stor, kan det tage 24 timer (eller mere), før processen er fuldført. Som en generel retningslinje tager det ca. en time at behandle 5.000 brugerkonti.

5. Hvis du vil fjerne et segment, skal du bruge cmdlet'en **Remove-OrganizationSegment** med parameteren *Identity* og relevante oplysninger.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> I dette eksempel blev det segment, der har GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, fjernet. |

## <a name="remove-a-policy-and-segment"></a>Fjern en politik og et segment

1. Hvis du vil have vist en liste over aktuelle politikker for informationsbarrierer, skal du bruge cmdlet'en **Get-InformationBarrierPolicy** .

    Syntaks: `Get-InformationBarrierPolicy`

    Identificer den politik, du vil fjerne, på listen over resultater. Bemærk politikkens GUID og navn.

2. Hvis du vil have vist alle eksisterende segmenter, skal du bruge cmdlet'en **Get-OrganizationSegment** .

    Syntaks: `Get-OrganizationSegment`

    Du får vist en liste over segmenter og detaljer for hver, f.eks. segmenttype, parameterværdien *UserGroupFilter* , hvem der oprettede eller senest ændrede den, GUID osv.

    >[!TIP]
    >Udskriv eller gem listen over segmenter til reference senere. Hvis du f.eks. vil redigere et segment, skal du kende dets navn eller identificeringsværdi (dette bruges sammen med parameteren Identity).

3. Hvis du vil angive status for politikken, der skal fjernes til inaktiv, skal du bruge **Set-InformationBarrierPolicy-cmdlet'en** med parameteren *Identity* og parameteren *State* angivet til *Inactive*.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> I dette eksempel angiver vi en politik for informationsbarrierer, der har GUID 43c37853-ea10-4b90-a23d-ab8c93772471 til en inaktiv status. |

4. Rediger det segment, der fjernes, for at fjerne relationen mellem brugere og det pågældende segment. Denne handling opdaterer segmentdefinitionen og fjerner alle brugere fra segmentet. Du skal bruge parameteren *UserGroupFilter* til at fjerne tilknytningen af brugere fra segmentet, før de fjernes.

    Hvis du vil redigere et segment, skal du bruge Cmdlet'en **Set-OrganizationSegment** med parameteren *Identity* og relevante oplysninger.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> I dette eksempel har vi for det segment, der har GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, opdateret afdelingsnavnet til *FakeDept* for at fjerne brugere fra segmentet. I dette eksempel bruges attributten *Afdeling* , men du kan bruge andre attributter efter behov. I eksemplet bruges *FakeDept* , fordi dette ikke findes og sikkert ikke indeholder nogen brugere. |

5. Hvis du vil anvende dine ændringer, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** .

    Syntaks: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Attributten *CleanupGroupSegmentLink* fjerner gruppetilknytninger med segmentet uden brugertilknytninger.

    Ændringer anvendes bruger for bruger for din organisation. Hvis din organisation er stor, kan det tage 24 timer (eller mere), før processen er fuldført. Som en generel retningslinje tager det ca. en time at behandle 5.000 brugerkonti.

6. Brug cmdlet'en **Remove-InformationBarrierPolicy** med parameteren *Identity* .

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> I dette eksempel fjernes den politik, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471* . |

    Når du bliver bedt om det, skal du bekræfte ændringen.

7. Hvis du vil fjerne et segment, skal du bruge cmdlet'en **Remove-OrganizationSegment** med parameteren *Identity* og relevante oplysninger.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> I dette eksempel blev segmentet med GUID c96e0837-c232-4a8a-841e-ef45787d8fcd fjernet. |

## <a name="stop-a-policy-application"></a>Stop et politikprogram

Når du er begyndt at anvende politikker for informationsbarrierer, skal du benytte følgende procedure, hvis du vil forhindre, at disse politikker anvendes. Det tager ca. 30-35 minutter, før processen starter.

1. Hvis du vil se status for den seneste programpolitik for informationsbarrierer, skal du bruge cmdlet'en **Get-InformationBarrierPoliciesApplicationStatus** .

    Syntaks: `Get-InformationBarrierPoliciesApplicationStatus`

    Bemærk programmets GUID.

2. Brug cmdlet'en **Stop-InformationBarrierPoliciesApplication** med parameteren Identity.

    |**Syntaks**|**Eksempel**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> I dette eksempel forhindrer vi, at politikker for informationsbarrierer anvendes. |

## <a name="resources"></a>Ressourcer

- [Få et overblik over informationsbarrierer](information-barriers.md)
- [Definer politikker for informationsbarrierer](information-barriers-policies.md)
- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer i OneDrive](/onedrive/information-barriers)
- [Attributter for IB-politikker](information-barriers-attributes.md)
- [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
