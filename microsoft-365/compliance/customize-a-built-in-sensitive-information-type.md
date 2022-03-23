---
title: Tilpasse en indbygget følsom oplysningstype
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du opretter en brugerdefineret type af følsomme oplysninger, der gør det muligt at bruge regler, der opfylder din organisations behov.
ms.openlocfilehash: 8393da8e2b2607692983010783d9ae110f268f4c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63587272"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Tilpasse en indbygget følsom oplysningstype

Når du søger efter følsomme oplysninger i indhold, skal du beskrive oplysningerne i det, der kaldes en *regel*. Forebyggelse af datatab (DLP) indeholder regler for de mest almindelige typer af følsomme oplysninger, som du kan bruge med det samme. Hvis du vil bruge disse regler, skal du medtage dem i en politik. Det kan være, at du vil justere disse indbyggede regler, så de opfylder din organisations specifikke behov, og det kan du gøre ved at oprette en brugerdefineret type af følsomme oplysninger. I dette emne kan du se, hvordan du kan tilpasse XML-filen, der indeholder den eksisterende regelsamling, til at registrere en bredere række potentielle kreditkortoplysninger.

Du kan tage dette eksempel og anvende det på andre indbyggede typer af følsomme oplysninger. Du kan finde en liste over standardtyper for følsomme oplysninger og XML-definitioner [i Enhedsdefinitioner for følsomme oplysninger.](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Eksportere XML-filen med de aktuelle regler

Hvis du vil eksportere XML'en, skal [du oprette forbindelse til Security and Compliance Center via Remote PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. I PowerShell skal du skrive følgende for at få vist din organisations regler på skærmen. Hvis du ikke har oprettet din egen, får du kun vist de indbyggede standardregler med navnet "Microsoft Rule Package".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Store din organisations regler i en variabel ved at skrive følgende. Når du gemmer noget i en variabel, bliver det nemt tilgængeligt senere i et format, der fungerer med PowerShell-fjernkommandoer.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Lav en formateret XML-fil med alle dataene ved at skrive følgende.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Sørg for at bruge den filplacering, hvor regelpakken rent faktisk er gemt. `C:\custompath\` er en pladsholder.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>Finde den regel, du vil ændre i XML

Cmdlet'erne ovenfor eksporterede hele samlingen *af regler*, hvilket omfatter de standardregler, vi angiver. Derefter skal du søge specifikt efter den kreditkortnummerregel, du vil ændre.

1. Brug en teksteditor til at åbne XML-filen, du eksporterede i forrige afsnit.

2. Rul ned til mærket `<Rules>` , som er starten af den sektion, der indeholder DLP-reglerne. Da denne XML-fil indeholder oplysningerne for hele regelsamlingen, indeholder den andre oplysninger øverst, som du skal rulle forbi for at komme til reglerne.

3. Se efter *Func_credit_card* for at finde definitionen af reglen Kreditkortnummer. I XML-koden må regelnavne ikke indeholde mellemrum, så mellemrummene erstattes normalt med understregningstegn, og regelnavne er nogle gange forkortet. Et eksempel på dette er den amerikanske cpr-regel, der er forkortet _SSN_. XML-reglen Kreditkortnummer skal ligne følgende kodeeksempel.

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

Nu hvor du har placeret definitionen af kreditkortnummer i XML-koden, kan du tilpasse reglens XML, så den opfylder dine behov. Du kan finde en opdatering af XML-definitionerne [i Ordliste](#term-glossary) til sidst i dette emne.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>Redigere XML og oprette en ny type af følsomme oplysninger

Først skal du oprette en ny type af følsomme oplysninger, da du ikke kan ændre standardreglerne direkte. Du kan gøre en lang række forskellige ting med brugerdefinerede typer af følsomme oplysninger, som er beskrevet i Opret en brugerdefineret type af følsomme oplysninger i [Security & Compliance Center PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md). I dette eksempel holder vi det enkelt og fjerner kun bekræftende beviser og føjer nøgleord til kreditkortnummerreglen.

Alle XML-regeldefinitioner er baseret på følgende generelle skabelon. Du skal kopiere og indsætte XML'en til definition af kreditkortnummer i skabelonen, redigere nogle værdier (bemærk ". . ." i følgende eksempel), og derefter overføre den ændrede XML som en ny regel, der kan bruges i politikker.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

Nu har du noget, der ligner følgende XML. Da regelpakker og regler identificeres af deres entydige GUID'er, skal du oprette to GUID'er: én for regelpakken og én til at erstatte GUID'et for kreditkortnummerreglen. GUID'et for enheds-id'et i følgende kodeprøve er eksemplet for vores indbyggede regeldefinition, som du skal erstatte med en ny. Der er flere måder at oprette GUID'er på, men du kan nemt gøre det i PowerShell ved at skrive **[guid]::NewGuid()**.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Fjern bekræftelseskravet fra en følsom oplysningstype

Nu hvor du har en ny type af følsomme oplysninger, som du kan overføre til Security &amp; Compliance Center, er næste trin at gøre reglen mere specifik. Rediger reglen, så den kun søger efter et 16-cifret tal, der består kontrolsummet, men ikke kræver yderligere (bekræftende) beviser, f.eks. nøgleord. For at gøre dette skal du fjerne den del af XML, der søger efter bekræftende beviser. Bekræftende beviser er meget nyttige til at reducere falske positive. I dette tilfælde er der normalt visse nøgleord eller en udløbsdato i nærheden af kreditkortnummeret. Hvis du fjerner dette bevis, `confidenceLevel`skal du også justere, hvor sikker du er på, at du har fundet et kreditkortnummer, ved at sænke , hvilket er 85 i eksemplet.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Se efter nøgleord, der er specifikke for din organisation

Det kan være en ide at kræve bekræftende beviser, men ønsker forskellige eller yderligere nøgleord, og måske vil du ændre, hvor du skal lede efter beviserne. Du kan justere for `patternsProximity` at udvide eller formindske vinduet for bekræftende beviser omkring det 16-cifrede tal. Hvis du vil tilføje dine egne nøgleord, skal du definere en nøgleordsliste og henvise til den i din regel. Følgende XML tilføjer nøgleordene "firmakort" og "Contoso-kort", så alle meddelelser, der indeholder disse udtryk inden for 150 tegn af et kreditkortnummer, identificeres som et kreditkortnummer.

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>Upload din regel

Hvis du vil overføre reglen, skal du gøre følgende.

1. Gem den som en .xml med Unicode-kodning. Dette er vigtigt, fordi reglen ikke fungerer, hvis filen gemmes med en anden kodning.

2. [Forbind til Security and Compliance Center via Remote PowerShell.](/powershell/exchange/connect-to-scc-powershell)

3. I PowerShell skal du skrive følgende.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Sørg for at bruge den filplacering, hvor regelpakken rent faktisk er gemt. `C:\custompath\` er en pladsholder.

4. Skriv Y for at bekræfte, og tryk derefter på **Enter**.

5. Kontrollér, at den nye regel er blevet overført og dens viste navn ved at skrive:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

For at begynde at bruge den nye regel til at registrere følsomme oplysninger skal du føje reglen til en DLP-politik. Du kan få mere at vide om, hvordan du føjer reglen til en politik, [under Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Ordliste

Dette er definitionerne for de udtryk, du stødte på under denne procedure.

<br>

****

|Ord|Definition|
|---|---|
|Enhed|Enheder er det, vi kalder følsomme oplysningstyper, f.eks kreditkortnumre. Hver enhed har et entydigt GUID som dets id. Hvis du kopierer et GUID og søger efter det i XML, kan du finde XML-regeldefinitionen og alle de oversatte oversættelser af den pågældende XML-regel. Du kan også finde denne definition ved at finde GUID'et til oversættelsen og derefter søge efter det pågældende GUID.|
|Funktioner|XML-filreferencerne `Func_credit_card`, som er en funktion i kompileret kode. Funktioner bruges til at køre komplekse regexes og kontrollere, at kontrolsum svarer til vores indbyggede regler.) Da dette sker i koden, vises nogle af variablerne ikke i XML-filen.|
|IdMatch|Dette er den identifikator, som mønsteret forsøger at matche – f.eks. et kreditkortnummer.|
|Lister over nøgleord|XML-filen henviser også til `keyword_cc_verification` og `keyword_cc_name`, som er lister med nøgleord, hvorfra vi leder efter match i `patternsProximity` til enheden. Disse vises ikke i øjeblikket i XML-format.|
|Mønster|Mønsteret indeholder listen over, hvad den følsomme type leder efter. Dette omfatter nøgleord, regexes og interne funktioner, som udfører opgaver som bekræftelse af kontrolsum. Typer af følsomme oplysninger kan have flere mønstre med entydige tillidsmønstre. Dette er nyttigt, når du opretter en følsom oplysningstype, der returnerer en høj grad af tillid, hvis der findes bekræftende beviser, og en lavere grad af tillid, hvis der kun er få eller ingen bekræftende beviser.|
|MønstertillidssikkerhedNiveau|Dette er tillidsniveauet til, at DLP-programmet fandt et match. Dette tillidsniveau er knyttet til et match for mønsteret, hvis mønsteret krav er opfyldt. Dette er den tillidsforanstaltning, du bør overveje, Exchange regler for mailflow (også kaldet transportregler).|
|PatternsProximity|Når vi finder ud af, hvad der ligner et mønster for kreditkortnummer, `patternsProximity` er afstanden omkring det tal, hvor vi skal lede efter bekræftende beviser.|
|recommendedConfidence|Dette er tillidsniveauet, vi anbefaler til denne regel. Den anbefalede tillid gælder for enheder og affiniteter. For enheder evalueres dette tal aldrig i forhold til `confidenceLevel` mønsteret. Det er blot et forslag, der kan hjælpe dig med at vælge et tillidsniveau, hvis du vil anvende et. For affiniteter skal mønsteret `confidenceLevel` være `recommendedConfidence` højere end tallet, for at en regelhandling for mailflow kan aktiveres. Det `recommendedConfidence` er standardtillidsniveauet, der bruges i regler for mailflow, der aktiverer en handling. Hvis du vil, kan du manuelt ændre reglen for mailflow, så den aktiveres på basis af mønsteret's tillidsniveau, i stedet.|
|

## <a name="for-more-information"></a>Du kan finde flere oplysninger

- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Oprette en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
