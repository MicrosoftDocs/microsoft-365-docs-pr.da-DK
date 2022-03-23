---
title: Designe en politik til forebyggelse af datatab
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Få mere at vide om, hvordan du designer en politik til forebyggelse af datatab (DLP)
ms.openlocfilehash: 14e9fbb5efd20ddcf3d0a47da41a0cce89c88cee
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594706"
---
# <a name="design-a-data-loss-prevention-policy"></a>Designe en politik til forebyggelse af datatab

Hvis du bruger tid på at designe en politik, før du implementerer den, får du hurtigere de ønskede resultater og færre utilsigtede problemer end at oprette den og derefter justere efter prøveversion og fejl alene. Hvis du har dokumenteret dine politikdesign, kan det også hjælpe dig med kommunikation, gennemgang af politikker, fejlfinding og yderligere justering.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

Hvis du er ny bruger af Microsoft 365 DLP, er det nyttigt at gennemgå disse artikler, før du begynder at designe en politik:

- [Få mere at vide om forebyggelse af](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) datatab – denne artikel introducerer dig til disciplinen til forebyggelse af datatab og Microsofts implementering af DLP
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) – ved at arbejde gennem denne artikel vil du:
    - [Identificere interessenter](dlp-overview-plan-for-dlp.md#identify-stakeholders)
    - [Beskriv kategorierne for følsomme oplysninger, der skal beskyttes](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
    - [Angiv mål og strategi](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Reference til politik til forebyggelse af datatab](dlp-policy-reference.md#data-loss-prevention-policy-reference) – i denne artikel introduceres alle komponenterne i en DLP-politik, og hvordan hver enkelt af dem påvirker en politiks funktionsmåde

## <a name="policy-design-overview"></a>Oversigt over politikdesign

[At designe en politik](#policy-design-process) handler primært om tydeligt at definere dine forretningsmæssige behov [,](#define-intent-for-the-policy) dokumentere dem i en politikerklæring og derefter tilknytte [disse behov til politikkonfiguration](#map-business-needs-to-policy-configuration). Du skal bruge de beslutninger, du har truffet i planlægningsfasen, til at informere nogle af dine beslutninger om politikdesign. 

### <a name="define-intent-for-the-policy"></a>Definere formålet med politikken 

Du bør kunne opsummere forretningsformålet for hver politik, du har i en enkelt sætning. Udvikling af denne erklæring vil føre samtaler i din organisation og, når det fulde udviklingsmæssige samarbejde, sammenkæder denne erklæring direkte politikken med et forretningsformål og giver en oversigt over politikdesign. Trinnene i artiklen [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) hjælper dig med at komme i gang med din politikerklæring.  

Husk fra [DLP-politikkonfigurationsoversigten](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) , at alle DLP-politikker kræver, at du:

- Vælg, hvad du vil overvåge
- Vælg, hvor du vil overvåge
- Vælg de betingelser, der skal matches, for at en politik kan anvendes på et element
- Vælg den handling, der skal sker, når politikbetingelserne er opfyldt 

Her er f.eks. et fiktivt første udkast til en formålserklæring, der giver svar på alle fire spørgsmål: 

*"Vi er en amerikansk baseret organisation, og vi er nødt til at registrere Office-dokumenter, der indeholder følsomme sundhedsplejeoplysninger, som er omfattet af HIPPA, og som er gemt i OneDrive/SharePoint, og beskyttes mod, at disse oplysninger deles i Teams-chat og kanalmeddelelser, og begrænser alles adgang til at dele dem med uautoriserede tredjeparter".* 

Når du udvikler et politikdesign, vil du sandsynligvis ændre og udvide sætningen.

### <a name="map-business-needs-to-policy-configuration"></a>Tilknytning af forretningsbehov ved politikkonfiguration

Lad os bryde eksempeludkastet ned og knytte den til konfigurationspunkter for DLP-politik.

|Sætning  |Besvaret konfigurationsspørgsmål og konfigurationstilknytning  |
|---------|---------|
| "Vi er en amerikansk baseret organisation, og vi er nødt til at registrere Office, der indeholder følsomme oplysninger om sundhedspleje, som er dækket af HIPPA...  |- **Hvad du skal** overvåge: Office dokumenter skal du bruge den [amerikanske HIPAA-skabelon (Health Insurance Act)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) </br>- Betingelser for match: (forudkonfigureret, men kan redigeres) – element indeholder amerikanske SSN- og Enforcement Agency (DEA), indhold, der er international klassificering afhierarkier (ICD-9-CM), International klassificering afkontinen (ICD-10-CM), indhold deles med personer uden **for** organisationen  </br> - driver samtaler for at tydeliggøre den udløsende grænseværdi for registrering som f.eks. [tillidsniveauer](sensitive-information-type-learn-about.md#more-on-confidence-levels) og antal [forekomster](dlp-policy-reference.md#content-contains) (kaldet lækagetolerance).|
|... der er gemt i OneDrive/SharePoint og beskyttes mod, at disse oplysninger deles Teams chat- og kanalmeddelelser ... |- **Hvor skal du overvåge**: [Placeringsplacering](dlp-policy-reference.md#locations) ved at medtage eller OneDrive websteder SharePoint og Teams chat-/kanalkonti eller distributionsgrupper. |
|... og begrænse alles adgang til at dele disse elementer med uautoriserede tredjeparter."  | - **Handlinger, der skal** [udføre](dlp-policy-reference.md#actions): *Du tilføjer Begræns adgang eller krypterer indholdet Microsoft 365 placeringer* </br> - styrer samtaler om, hvilke handlinger der skal tages, når en politik udløses, herunder beskyttende handlinger som delingsbegrænsninger, opmærksomhedshandlinger som f.eks. meddelelser og beskeder og handlinger i forbindelse med brugeraktivering som f.eks. tillade brugertilsidesættelse af en blokeringshandling |

Dette eksempel dækker ikke alle konfigurationspunkterne i en DLP-politik. Det skal udvides. Men det bør få dig til at tænke i den rigtige retning, når du udvikler dine egne DLP-politikformål.

> [!IMPORTANT]
> Husk på, at den eller de placeringer, du vælger, påvirker, om du kan bruge følsomme oplysningstyper, følsomhedsmærkater og opbevaringsmærkater samt de handlinger, der er tilgængelige. Se Reference [til politik til forebyggelse af datatab](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>Politikdesignproces

1. Fuldfør trinnene i:
    1. [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) – ved at arbejde gennem denne artikel vil du:
        1. [Identificer dine interessenter](dlp-overview-plan-for-dlp.md#identify-stakeholders)
        1. [Beskriv kategorierne for følsomme oplysninger, der skal beskyttes](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
        1. [Angiv mål og strategi](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
        1. [Definer din politikinstallationsplan](dlp-overview-plan-for-dlp.md#policy-deployment)

1. Gør dig [bekendt med en](dlp-policy-reference.md#data-loss-prevention-policy-reference) reference til politik til forebyggelse af datatab, så du forstår alle komponenterne i en DLP-politik, og hvordan hver enkelt af dem påvirker en politiks funktionsmåde.

1. Gør dig bekendt med [Hvad DLP-politikskabelonerne indeholder](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

1. Udvikd din politikerklæring med dine vigtigste interessenter. Se eksemplet tidligere i denne artikel.

1. Bestem, hvordan denne politik passer til din overordnede DLP-politikstrategi.

> [!IMPORTANT]
> Politikker kan ikke omdøbes, når de først er blevet oprettet. Hvis du skal omdøbe en politik, skal du oprette en ny med det ønskede navn og lade den gamle udgå. Så beslut dig for den navngivningsstruktur, som alle dine politikker skal bruge nu. 

6. Knyt elementerne i politikerklæringen til konfigurationsindstillingerne.

7. Beslut, hvilken politikskabelon du vil starte fra, foruddefineret eller brugerdefineret.

8. Gennemgå skabelonen, og saml alle nødvendige oplysninger, før du opretter politikken. Det er sandsynligt, at du vil opdage, at der er nogle konfigurationspunkter, som ikke er dækket af din politikerklæring. Dette er ok. Gå tilbage til dine interessenter for at opfylde kravene til manglende konfigurationspunkter. 

9. Dokumenter konfigurationen af alle politikindstillinger, og gennemgå dem med dine interessenter. Du kan bruge din politiks formålstilknytning til konfigurationspunkter, som nu er fuldt konkret.

10. [Opret en kladdepolitik](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) , og referer tilbage til [din implementeringsplan for](dlp-overview-plan-for-dlp.md#policy-deployment) politikker.

<!--## Policy design examples

|Customer business needs description  | approach  |
|---------|---------|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft| - Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.     |- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users       |
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices     |- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage      |


1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally



–   For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**


  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
–   (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

<!--


> [!TIP] The more locations you include ensures broader application of the policy and more consistent coverage. If you include locations that are mostly used for internal collaboration, the responsiveness of collaboration may be impacted.


- whether the protective actions you need are supported throught the associated location or if you need to compromise to extend coverage
    - also usefule for identifying the most restrictive actions available 
    - (we shouldn't mention here that the "content contains" condition is the primary staple for a DLP policy and should be utilized as a starting point for policy creation. The other workload-specific conditions can be ustilized as an extended or granular control of company's DLP policy. Useful for when "too much" data is being restricted and known sensitive data typically falls under certain conditions.)
    - (We can mention here that their quantitative goal such as "protect X% of data across all locations while maintaining x productivity" can be monitored throught alerts or reports. If protection is too high of working against their established goals, they can come back to policy and tweak their conditions/actions)
- Finally, you should have a union of what, hwo and when to be covered which will easily map to generating a live policy via Microsoft DLP. 
- 
5. At this stage you should asses how you should start this policy. ***LINK OUT TO DEPLOYING A POLICY COVERED IN THE PLANNING TOPIC TOO***
    - Test: your company is very large, conservative or the actions established are pretty restrictive
    - Test w/ notifications: same as above, but you get to test out investigation cadence or volume
    - Live: immediately start this policy in your environment. Useful for when data protection is needed immediately, such as a reactive policy creation, or if you're confident in your planning, or if the risk is low (liek audit actions, etc.)
    - keep it off:
-->

<!--## Policy Design Examples

Here are some examples of more detailed policy intent statement to configuration mappings.

*We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information and prevent it from egressing outside of our company’s borders. We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices. We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item. We have a Microsoft 365 E5 subscription and want to protect all locations and first party apps that are available to us because we can’t afford to have any data leaks. If an event occurs or is prevented, we want to alert our compliance admin and educate our end-users where necessary.*

|Statement  |Configuration question answered and configuration mapping  |
|---------|---------|
| We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
| ...and prevent it from egressing outside of our company’s borders... |- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...| - **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
| ...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....| - **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages... |- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups. |
|...and restrict everyone from sharing those items with unauthorized third parties."  | - **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action |

-->


## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Reference til politik til forebyggelse af datatab](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Reference til tip til politik til forebyggelse af datatab](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)