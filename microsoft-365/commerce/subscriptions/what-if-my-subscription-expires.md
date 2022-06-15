---
title: Hvad sker der med mine data og adgang, når mit abonnement slutter?
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sgautam, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Få mere at vide om, hvad der sker med dine data, når dit abonnement på Microsoft 365 til virksomheder udløber, deaktiveres, eller hvis du annullerer.
ms.date: 09/16/2021
ms.openlocfilehash: a96ef700c522577e8d22f734ea6a8a94b410d83a
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102300"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Hvad sker der med mine data og adgang, når mit abonnement på Microsoft 365 til virksomheder ophører?

Hvis dit abonnement slutter – enten fordi det udløber, eller fordi du beslutter dig for at annullere – går din adgang til Microsoft 365 tjenester, programmer og kundedata gennem flere tilstande, før abonnementet er helt deaktiveret eller *slettet*. Hvis du er opmærksom på dette fremskridt, er du bedre i stand til at returnere dit abonnement til en aktiv tilstand, før det er for sent, eller – hvis du forlader Microsoft 365 – sikkerhedskopiere dine data, før de i sidste ende slettes.

Læs disse vigtige oplysninger, før du kontakter [Microsoft 365 support](../../admin/get-help-support.md).

> [!NOTE]
> For nogle abonnementer kan du kun annullere i løbet af et begrænset tidsrum, når du har købt eller fornyet dit abonnement. Hvis annulleringsvinduet er gået, skal du deaktivere tilbagevendende fakturering for at annullere abonnementet i slutningen af dets løbetid.
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Hvad sker der med data, når et abonnement udløber?

- Hvis dit abonnement udløber, gennemgås følgende faser: Udløbet/Deaktiveret/Slettet. Fasen Udløbet starter med det samme, når abonnementet har nået slutdatoen.
- Hvis du slår tilbagevendende fakturering fra på dit årlige abonnement, gennemgår det de samme faser som et udløbet abonnement. Den første fase starter, er årsdagen for det årlige abonnement og starter ikke den dato, hvor du deaktiverede abonnementets tilbagevendende faktureringsindstilling.
- Hvis du annullerer dit månedlige abonnement, deaktiveres det med det samme (på datoen for annulleringen). Det betyder, at brugerne mister adgangen til de Microsoft 365 aktiver med det samme, og det er kun administratorer, der har adgang til dataene i de næste 90 dage.

I følgende tabel forklares det, hvad du kan forvente, når et betalt Microsoft 365 for virksomhedsabonnement udløber.

| Aktive | Udløbet <br/>(30 dage\*) | Deaktiveret <br/>(90 dage\*) | Slettet |
|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| *Data, der er tilgængelige for alle*                                               | *Data, der er tilgængelige for alle*                                                     | *Data, der kun er tilgængelige for administratorer*                                             | **Slettede<br/> data Azure Active Directory fjernes, hvis de ikke bruges af andre tjenester** |
| Brugerne har normal adgang til Microsoft 365, filer og programmer   | Brugerne har normal adgang til Microsoft 365, filer og programmer              | Brugerne kan ikke få adgang til Microsoft 365, filer eller programmer                        | Brugerne kan ikke få adgang til Microsoft 365, filer eller programmer                                     |
| Administratorer har normal adgang til Microsoft 365, data og Office programmer | Administratorer kan få adgang til Administration                                           | Administratorer kan få adgang til Administration, men kan ikke tildele licenser til brugere       | Administratorer kan få adgang til Administration for at købe og administrere andre abonnementer             |
|                                                                        | Globale administratorer eller faktureringsadministratorer kan genaktivere abonnementet i Administration | Globale administratorer eller faktureringsadministratorer kan genaktivere abonnementet i Administration |                                                                                           |

* For de fleste tilbud, i de fleste lande og områder.
  
> [!NOTE]
>
> **Hvad er "kundedata"?** Kundedata, som defineret i [servicevilkårene for Microsoft Online](https://go.microsoft.com/fwlink/p/?LinkId=613649), refererer til alle data, herunder alle tekst-, lyd- eller billedfiler, der leveres til Microsoft af kunden eller på vegne af kunden gennem kundens brug af Microsoft 365-tjenester. Hvis du vil vide mere om beskyttelse af kundedata, skal du se [Kom i gang med Microsoft Service Trust Portal](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Hvad sker der, hvis jeg annullerer et abonnement?

Hvis du annullerer dit abonnement før slutdatoen for dets løbetid, springer abonnementet fasen Udløbet over og flytter direkte til fasen Deaktiveret, hvilket er 90 dage for de fleste abonnementer, i de fleste lande og områder. Vi anbefaler, at du [sikkerhedskopierer dine data](back-up-data-before-switching-plans.md) , før du annullerer, men som administrator kan du stadig få adgang til og sikkerhedskopiere data for din organisation, mens de er i fasen Deaktiveret. Alle kundedata, du efterlader dig, kan slettes efter 90 dage og slettes senest 180 dage efter annulleringen.
  
Her er, hvad du kan forvente for dig og dine brugere, hvis du annullerer et abonnement.
  
- **Administration adgangsadministratorer** kan stadig logge på og få adgang til Administration og købe andre abonnementer efter behov. Som global administrator eller faktureringsadministrator har du 90 dage til at [genaktivere abonnementet](reactivate-your-subscription.md) med alle data intakte.

- **Brugeradgang** Brugerne kan ikke bruge tjenester som OneDrive for Business eller få adgang til kundedata, f.eks. mail eller dokumenter på teamwebsteder. Office programmer, f.eks. Word og Excel, flyttes til sidst til skrivebeskyttet tilstand med reduceret funktionalitet og viser [meddelelser om produkt uden licens](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

Du kan få mere at vide om, hvordan du annullerer, under [Annuller dit abonnement](cancel-your-subscription.md).
  
> [!IMPORTANT]
> Hvis du ønsker, at dine abonnementsdata skal slettes, før den typiske fase Deaktiveret er slut, kan du [lukke din konto](../close-your-account.md).
  
> [!NOTE]
>
> Hvis du udtrykkeligt sletter et abonnement, springes faserne Udløbet og Deaktiveret over, og SharePoint Online-data og -indhold, herunder OneDrive, slettes med det samme.

## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Hvilke muligheder har jeg, hvis mit abonnement er ved at udløbe?

Mens et abonnement er aktivt, har du og dine slutbrugere normal adgang til dine data, tjenester som mail og OneDrive for Business og Office programmer. Som administrator modtager du en række meddelelser via mail og i Administration, efterhånden som dit abonnement nærmer sig udløbsdatoen.
  
Før abonnementet faktisk når udløbsdatoen, har du et par muligheder:
  
- **Aktivér tilbagevendende fakturering for abonnementet.**
  - Hvis **tilbagevendende fakturering** allerede er slået til, behøver du ikke at foretage dig noget. Dit abonnement faktureres automatisk, og du opkræves for et ekstra år eller en ekstra måned, afhængigt af din aktuelle betalingshyppighed. Hvis du af en eller anden grund har slået **tilbagevendende fakturering** fra, kan du altid [slå tilbagevendende fakturering til igen](renew-your-subscription.md).
  - Hvis du har købt Microsoft 365 Apps for business med et forudbetalt kort, kan du [aktivere tilbagevendende fakturering](renew-your-subscription.md) for dit abonnement.
  - Hvis du er open volume licensing-kunde med et forudbetalt abonnement på ét år, skal du kontakte din partner for at købe en ny produktnøgle. Du modtager instruktioner via mail om at aktivere din nøgle i [Volume Licensing Service Center](https://go.microsoft.com/fwlink/p/?LinkID=282016). Hvis du vil vide mere om, hvordan du finder en ny partner eller den partner, du tidligere har arbejdet med, skal du se [Find din partner eller forhandler](../../admin/manage/find-your-partner-or-reseller.md).
  - Hvis du har Microsoft 365 Apps for business, skal du se [Administrer tilbagevendende fakturering for dit abonnement](renew-your-subscription.md).
- **Lad abonnementet udløbe.**
  - Hvis du betaler med kreditkort eller faktura, og du ikke vil fortsætte dit abonnement, skal du [slå Tilbagevendende fakturering fra](renew-your-subscription.md). Dit abonnement slutter på udløbsdatoen, og du kan ignorere alle relaterede mailmeddelelser.
  - Hvis du er open volume licensing-kunde, der arbejder sammen med en partner, kan du lade dit abonnement udløbe ved ikke at foretage dig noget.
  - Hvis du er Microsoft 365 Business Standard kunde, og du har forudbetalt dit abonnement og aktiveret det med en produktnøgle, kan du lade dit abonnement udløbe ved ikke at foretage dig noget.
- **Annuller, før abonnementet udløber.** Du kan finde flere oplysninger under [Annuller dit abonnement](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Hvad sker der, når mit abonnement udløber?

Hvis du lader dit abonnement udløbe, går det gennem flere tilstande, før det i sidste ende slettes. Dette giver dig som administrator tid til at genaktivere, hvis du vil fortsætte tjenesten, eller til at sikkerhedskopiere dine data, hvis du beslutter, at du ikke længere vil have abonnementet.
  
Her er, hvad du kan forvente, når dit abonnement er i hver enkelt tilstand.
  
### <a name="state-expired"></a>Tilstand: Udløbet

**Hvad du kan forvente:** Fasen Udløbet varer 30 dage for de fleste abonnementer, herunder abonnementer, der er købt via [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), i de fleste lande og områder. For volumenlicensprodukter, undtagen Microsoft Open, varer fasen Udløbet 90 dage.

I denne tilstand har brugerne normal adgang til Microsoft 365-portalen, Office-programmer og -tjenester, f.eks. mail og SharePoint Online.
  
Som administrator har du stadig adgang til Administration. Bare rolig – globale administratorer eller faktureringsadministratorer kan [genaktivere abonnementet](reactivate-your-subscription.md) og fortsætte med at bruge Microsoft 365. Hvis du ikke genaktiverer, [skal du sikkerhedskopiere dine data](back-up-data-before-switching-plans.md).
  
### <a name="state-disabled"></a>Tilstand: Deaktiveret

**Hvad du kan forvente:** Hvis du ikke genaktiverer dit abonnement, mens det er i fasen Udløbet, flyttes det til en Deaktiveret fase, der varer i 90 dage for de fleste abonnementer i de fleste lande og områder. I forbindelse med volumenlicensprodukter varer fasen Deaktiveret 30 dage.

I denne tilstand reduceres din adgang betydeligt. Brugerne kan ikke logge på eller få adgang til tjenester som mail eller SharePoint Online. Office programmer flyttes til sidst til skrivebeskyttet tilstand med reduceret funktionalitet og viser [meddelelser om produkt uden licens](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). Du kan stadig logge på og få adgang til Administration, men du kan ikke tildele licenser til brugere. Dine kundedata, herunder alle brugerdata, mail og filer på teamwebsteder, er kun tilgængelige for dig og andre administratorer.

Som global administrator eller faktureringsadministrator kan du [genaktivere abonnementet](reactivate-your-subscription.md) og fortsætte med at bruge Microsoft 365 med alle dine kundedata intakte. Hvis du vælger ikke at genaktivere, [skal du sikkerhedskopiere dine data](back-up-data-before-switching-plans.md).

### <a name="state-deleted"></a>Tilstand: Slettet
  
**Hvad du kan forvente:** Hvis du ikke genaktiverer dit abonnement, mens det er udløbet eller deaktiveret, slettes abonnementet.
  
Administratorer og brugere har ikke længere adgang til de tjenester eller Office programmer, der fulgte med abonnementet. Alle kundedata – fra brugerdata til dokumenter og mail – slettes permanent og kan ikke genoprettes.
  
På nuværende tidspunkt kan du ikke genaktivere abonnementet. Som global administrator eller faktureringsadministrator kan du dog stadig få adgang til Administration for at administrere andre abonnementer eller for at købe nye abonnementer, der opfylder dine forretningsbehov.
  
> [!NOTE]
>
> - Tilføjelse af et nyt abonnement af samme type, der er blevet slettet, gendanner ikke de data, der er knyttet til det slettede abonnement.
> - Hvis en CSP-licens er suspenderet, er der ingen 30-dages udløbet fase, og tjenester deaktiveres med det samme. Data slettes efter 90 dage, hvis lejeren ikke genaktiveres, ved at tilføje en ny licens.

### <a name="what-happens-when-my-trial-ends"></a>Hvad sker der, når min prøveversion udløber?

Når din prøveversion udløber, kan du ikke fortsætte med at bruge Microsoft 365 gratis. Du har et par muligheder:

- **Køb Microsoft 365.** Når din prøveversion udløber, flyttes den til fasen Udløbet, hvilket giver dig yderligere 30 dage (for de fleste prøveversioner i de fleste lande og områder) til at købe Microsoft 365. Hvis du vil vide mere om, hvordan du konverterer din prøveversion til et betalt abonnement, skal du se [Køb et abonnement fra din gratis prøveversion](../try-or-buy-microsoft-365.md#buy-a-subscription-from-your-free-trial).
- **Forlæng din prøveversion.** Har du brug for mere tid til at evaluere Microsoft 365? I visse tilfælde kan du [forlænge din prøveversion](../extend-your-trial.md).
- **Annuller prøveversionen, eller lad den udløbe.** Hvis du beslutter dig for ikke at købe Microsoft 365, kan du lade din prøveversion udløbe eller [annullere den](cancel-your-subscription.md). Sikkerhedskopiér de data, du vil beholde. Kort efter fasen Udløbet på 30 dage slettes dine kontooplysninger og data for prøvekontoen permanent.

> [!NOTE]
>
> Oplysningerne på denne side er underlagt [Microsofts politikfraskrivelse og ændringsmeddelelse](https://go.microsoft.com/fwlink/p/?LinkId=613651). Vend jævnligt tilbage til dette websted for at gennemse eventuelle ændringer.

## <a name="related-content"></a>Relateret indhold

[Annuller dit abonnement](./cancel-your-subscription.md) (artikel)\
[Forny Microsoft 365 til virksomheder](./renew-your-subscription.md) (artikel)\
[Genaktiver dit abonnement](./reactivate-your-subscription.md) (artikel)
