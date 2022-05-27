---
title: Tilpas en indbygget type af følsomme oplysninger
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
description: Få mere at vide om, hvordan du opretter en brugerdefineret type følsomme oplysninger, der giver dig mulighed for at bruge regler, der opfylder organisationens behov.
ms.openlocfilehash: f0ebc1bb4b13f9e31ca1a8a1967fce007105cfe6
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753886"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Tilpas en indbygget type af følsomme oplysninger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du søger efter følsomme oplysninger i indhold, skal du beskrive disse oplysninger i det, der kaldes en *regel*. Microsoft Purview Forebyggelse af datatab (DLP) indeholder regler for de mest almindelige typer følsomme oplysninger, som du kan bruge med det samme. Hvis du vil bruge disse regler, skal du inkludere dem i en politik. Det kan være, at du vil justere disse indbyggede regler, så de opfylder organisationens specifikke behov, og det kan du gøre ved at oprette en brugerdefineret type følsomme oplysninger. I dette emne kan du se, hvordan du tilpasser den XML-fil, der indeholder den eksisterende regelsamling, for at registrere et større udvalg af potentielle kreditkortoplysninger.

Du kan tage dette eksempel og anvende det på andre indbyggede typer følsomme oplysninger. Du kan se en liste over standardtyper for følsomme oplysninger og XML-definitioner under [Objektdefinitioner for følsomme oplysninger.](sensitive-information-type-entity-definitions.md)

## <a name="export-the-xml-file-of-the-current-rules"></a>Eksportér XML-filen for de aktuelle regler

Hvis du vil eksportere XML-koden, skal du [oprette forbindelse til Security and Compliance Center via Remote PowerShell.](/powershell/exchange/connect-to-scc-powershell)

1. I PowerShell skal du skrive følgende for at få vist organisationens regler på skærmen. Hvis du ikke har oprettet dine egne, kan du kun se de indbyggede standardregler, der er forsynet med mærkaten "Microsoft Rule Package".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Store organisationens regler i en variabel ved at skrive følgende. Lagring af noget i en variabel gør det let tilgængeligt senere i et format, der fungerer til fjernkommandoer i PowerShell.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Opret en formateret XML-fil med alle disse data ved at skrive følgende.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Sørg for at bruge den filplacering, hvor regelpakken faktisk er gemt. `C:\custompath\` er en pladsholder.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>Find den regel, du vil ændre, i XML-filen

Cmdlet'erne ovenfor eksporterede hele *regelsamlingen*, som indeholder de standardregler, vi angiver. Derefter skal du kigge specifikt efter den kreditkortnummerregel, du vil ændre.

1. Brug en teksteditor til at åbne den XML-fil, du eksporterede i forrige afsnit.

2. Rul ned til `<Rules>` mærket, som er starten på den sektion, der indeholder DLP-reglerne. Da denne XML-fil indeholder oplysningerne for hele regelsamlingen, indeholder den andre oplysninger øverst, som du skal rulle forbi for at få adgang til reglerne.

3. Søg efter *Func_credit_card* for at finde definitionen af reglen Kreditkortnummer. I XML må regelnavne ikke indeholde mellemrum, så mellemrummene erstattes normalt med understregningstegn, og regelnavne forkortes nogle gange. Et eksempel på dette er den amerikanske cpr-nummerregel, som forkortes _SSN_. XML-koden kreditkortnummer skal ligne følgende kodeeksempel.

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

Nu, hvor du har fundet definitionen af reglen Kreditkortnummer i XML-koden, kan du tilpasse reglens XML, så den opfylder dine behov. Hvis du vil have en opdatering af XML-definitioner, skal du se [ordlisten](#term-glossary) i slutningen af dette emne.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>Rediger XML-koden, og opret en ny type følsomme oplysninger

Først skal du oprette en ny type følsomme oplysninger, fordi du ikke kan ændre standardreglerne direkte. Du kan gøre en lang række ting med brugerdefinerede typer følsomme oplysninger, som er beskrevet i [Opret en brugerdefineret type følsomme oplysninger i Security & Compliance Center PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md). I dette eksempel holder vi det enkelt og fjerner kun bekræftende beviser og føjer nøgleord til reglen Kreditkortnummer.

Alle definitioner af XML-regler er baseret på følgende generelle skabelon. Du skal kopiere og indsætte XML-koden til definitionen af kreditkortnummer i skabelonen, redigere nogle værdier (bemærk ". . ." pladsholdere i følgende eksempel), og upload derefter den ændrede XML som en ny regel, der kan bruges i politikker.

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

Nu har du noget, der ligner følgende XML. Da regelpakker og regler identificeres af deres entydige GUID'er, skal du generere to GUID'er: én for regelpakken og én for at erstatte GUID'et for reglen for kreditkortnummer. GUID'et for enheds-id'et i følgende kodeeksempel er det samme som for vores indbyggede regeldefinition, som du skal erstatte med en ny. Der er flere måder at generere GUID'er på, men du kan nemt gøre det i PowerShell ved at skrive **[guid]::NewGuid()**.

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

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Fjern det bekræftede beviskrav fra en type følsomme oplysninger

Nu, hvor du har en ny type følsomme oplysninger, som du kan uploade til Microsoft Purview-compliance-portal, er det næste trin at gøre reglen mere specifik. Rediger reglen, så den kun søger efter et 16-cifret tal, der består kontrolsummen, men som ikke kræver yderligere (bekræftende) beviser, f.eks. nøgleord. Hvis du vil gøre dette, skal du fjerne den del af XML, der søger efter bekræftende beviser. Korrative beviser er meget nyttige til at reducere falske positiver. I dette tilfælde er der normalt visse nøgleord eller en udløbsdato i nærheden af kreditkortnummeret. Hvis du fjerner disse beviser, skal du også justere, hvor sikker du er på, at du har fundet et kreditkortnummer ved at `confidenceLevel`sænke , hvilket er 85 i eksemplet.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Søg efter nøgleord, der er specifikke for din organisation

Du vil måske kræve bekræftende beviser, men ønsker forskellige eller yderligere nøgleord, og måske vil du ændre, hvor du skal lede efter disse beviser. Du kan justere `patternsProximity` for at udvide eller formindske vinduet for at få bekræftet beviser omkring det 16-cifrede tal. Hvis du vil tilføje dine egne nøgleord, skal du definere en nøgleordsliste og referere til den i din regel. Følgende XML tilføjer nøgleordene "firmakort" og "Contoso-kort", så alle meddelelser, der indeholder disse udtryk inden for 150 tegn fra et kreditkortnummer, identificeres som et kreditkortnummer.

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

## <a name="upload-your-rule"></a>Upload reglen

Hvis du vil uploade din regel, skal du gøre følgende.

1. Gem den som en .xml fil med Unicode-kodning. Dette er vigtigt, da reglen ikke fungerer, hvis filen gemmes med en anden kodning.

2. [Forbind til Security and Compliance Center via Remote PowerShell.](/powershell/exchange/connect-to-scc-powershell)

3. I PowerShell skal du skrive følgende.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Sørg for at bruge den filplacering, hvor regelpakken faktisk er gemt. `C:\custompath\` er en pladsholder.

4. Du kan bekræfte ved at skrive Y og derefter trykke på **Enter**.

5. Bekræft, at den nye regel blev overført, og dens viste navn ved at skrive:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Hvis du vil bruge den nye regel til at registrere følsomme oplysninger, skal du føje reglen til en DLP-politik. Hvis du vil vide mere om, hvordan du føjer reglen til en politik, skal du se [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Ordliste

Dette er definitionerne for de ord, du oplevede under denne procedure.

<br>

****

|Udtrykket|Definition|
|---|---|
|Enhed|Objekter er, hvad vi kalder typer af følsomme oplysninger, f.eks. kreditkortnumre. Hvert objekt har et entydigt GUID som id. Hvis du kopierer et GUID og søger efter det i XML, kan du finde definitionen af XML-reglen og alle lokaliserede oversættelser af den pågældende XML-regel. Du kan også finde denne definition ved at finde GUID'et til oversættelsen og derefter søge efter det pågældende GUID.|
|Funktioner|XML-filen henviser til `Func_credit_card`, som er en funktion i kompileret kode. Funktioner bruges til at køre komplekse regexes og kontrollere, at kontrolsummen stemmer overens med vores indbyggede regler. Da dette sker i koden, vises nogle af variablerne ikke i XML-filen.|
|IdMatch|Dette er det id, som mønsteret skal forsøge at matche – f.eks. et kreditkortnummer.|
|Nøgleordslister|XML-filen henviser også til `keyword_cc_verification` og `keyword_cc_name`, som er lister over nøgleord, som vi søger efter match fra i `patternsProximity` for objektet . Disse vises i øjeblikket ikke i XML-koden.|
|Mønster|Mønsteret indeholder en liste over, hvad den følsomme type søger efter. Dette omfatter nøgleord, regexes og interne funktioner, der udfører opgaver som f.eks. at kontrollere kontrolsummene. Følsomme informationstyper kan have flere mønstre med entydige konfidenser. Dette er nyttigt, når du opretter en følsom informationstype, der returnerer en høj tillid, hvis der findes bekræftende beviser, og en lavere tillid, hvis der findes lidt eller ingen bekræftende beviser.|
|Mønster konfidensniveau|Dette er graden af tillid til, at DLP-programmet fandt et match. Dette konfidensniveau er knyttet til et match for mønsteret, hvis mønsterets krav er opfyldt. Dette er den tillidsmåling, du bør overveje, når du bruger Exchange regler for mailflow (også kaldet transportregler).|
|patternsProximity|Når vi finder, hvad der ligner et kreditkortnummer mønster, `patternsProximity` er nærhed omkring det tal, hvor vi vil søge bekræftende beviser.|
|recommendedConfidence|Dette er det tillidsniveau, vi anbefaler til denne regel. Den anbefalede tillid gælder for objekter og tilhørsforhold. For objekter evalueres dette tal aldrig i forhold til `confidenceLevel` mønsteret for . Det er blot et forslag, der kan hjælpe dig med at vælge et tillidsniveau, hvis du vil anvende et. I forbindelse `confidenceLevel` med tilhørsforhold skal mønsteret være højere end antallet for `recommendedConfidence` en regelhandling i et mailflow, der skal aktiveres. `recommendedConfidence` er det standardsikkerhedsniveau, der bruges i regler for mailflow, der aktiverer en handling. Hvis du vil, kan du manuelt ændre den regel for mailflowet, der skal aktiveres, på baggrund af mønsterets konfidensniveau i stedet.|
|

## <a name="for-more-information"></a>Du kan få flere oplysninger

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
