Het beperkte complex data type EMLstructure520 gebruikt het type EMLstructureKR als base type, en maakt child elementen ManagingAuthority en kr:CreationDateTime verplicht. Het child element IssueDate is niet toegestaan.

![](../media/image71.png)

Het beperkte complex data type ElectionIdentifierStructure520 gebruikt het type ElectionIdentifierStructureKR als base type en staat het child element kr:NominationDate niet toe.

![](../media/image72.png)

Het beperkte complex data type CandidateStructure520 gebruikt het type CandidateStructureKR als base type, beperkt het type van het child element CandidateIdentifier tot CandidateIdentifierStructure520, en staat child elementen DateOfBirth, Contact, Agent, kr:DateOfBirthAnnex en kr:NationalIdentificationNumber niet toe. Child elementen CandidateFullName en QualifyingAddress zijn verplicht gemaakt.

![](../media/image73.png)

Het beperkte complex data type CandidateIdentifierStructure520 gebruikt het type CandidateIdentifierStructureKR als base type, maakt het Id attribuut verplicht, en beperkt de waarde tot positieve decimale cijfers.

Het Id attribuut is hier verplicht gemaakt *maar heeft niet dezelfde betekenis al in de* CandidateIdentifierStructure510*\!* Hier refereert het Id attribuut naar de volgorde waarin de zetels verdeeld zijn, waarbij de kandidaat die de eerste zetel van een partij toebedeeld heeft gekregen Id=1 krijgt, de tweede zetel Id=2 etc.

![](../media/image74.png)

Het beperkte complex data type AffiliationIdentifierStructure520 gebruikt het type AffiliationIdentifierStructureKR als base type, maakt het Id attribuut verplicht en beperkt de waarden tot decimale nummers.

![57\_AffiliationIdentifierStructure520](../media/image75.png)

Het base type van het EML (root) element is beperkt tot EMLstructure520. Het is daarna uitgebreid op dezelfde manier als de originele EML V5.0 definitie door het child element Result.

![](../media/image76.png)

Het element Result is beperkt compatible in een aantal opzichten in vergelijking tot het originele EML element. Election is toegestaan. Het maximale aantal kardinale getallen Election is teruggebracht naar één. Het "any" extension point is behouden.

![](../media/image77.png)

Het type van het child element ElectionIdentifier is beperkt tot ElectionIdentifierStructure520.

Voor het child element Contest, alleen child elementen ContestIdentifier, en de opvolging van Selection zijn toegestaan. Het type van het child element ContestIdentifier is beperkt tot ContestIdentifierStructureKR.

Het element Selection is in een aantal opzichten beperkt compatibel. Het bestaat uit child element Candidate, of child element AffiliationIdentifier, optioneel gevolgd door het aantal gekregen stemmen met element Votes, gevolgd door zowel een opvolging van twee elementen van Ranking en Elected (voor kandidaten), of alleen het element Elected (voor affiliaties). Het type van het child element Candidate is beperkt tot CandidateStructure520. Het type van het child element AffiliationIdentifier is beperkt tot AffiliationIndentifier520. Het element Ranking kan slechts twee waarden hebben: 1 (voor kandidaten die verkozen zijn over voorkeursdrempel ), of 2 (voor andere kandidaten).

Een voorbeeld van de EML\_NL 520 voor een Tweede Kamerverkiezing is hieronder afgebeeld. Ook hier geldt dat ShortCodes worden gebruikt zodat de kandidaten gekoppeld kunnen worden aan de kandidatenlijsten. Het CandidateIdentifier Id is hier de volgorde waarin de kandidaten gekozen zijn *en dus niet het nummer op de kandidatenlijst*:

```xml
<EML xmlns="urn:oasis:names:tc:evs:schema:eml" xmlns:ds="http://www.w3.org/2000/09/xmldsig#" xmlns:kr="http://www.kiesraad.nl/extensions" xmlns:xal="urn:oasis:names:tc:ciq:xsdschema:xAL:2.0" xmlns:xnl="urn:oasis:names:tc:ciq:xsdschema:xNL:2.0" Id="520" SchemaVersion="5">
  <TransactionId>1</TransactionId>
  <ManagingAuthority>
    <AuthorityIdentifier Id="CSB">De Kiesraad</AuthorityIdentifier>
    <AuthorityAddress/>
  </ManagingAuthority>
  <kr:Schema Version="1.3"/>
  <kr:CreationDateTime>2023-12-03T14:22:26.741</kr:CreationDateTime>
  <ds:CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315#WithComments"/>
  <Result>
    <Election>
      <ElectionIdentifier Id="TK2023">
        <ElectionName>Tweede Kamer der Staten-Generaal 2023</ElectionName>
        <ElectionCategory>TK</ElectionCategory>
        <kr:ElectionSubcategory>TK</kr:ElectionSubcategory>
        <kr:ElectionDate>2023-11-22</kr:ElectionDate>
      </ElectionIdentifier>
      <Contest>
        <ContestIdentifier Id="alle"/>
        <Selection>
          <AffiliationIdentifier Id="1">
            <RegisteredName>De Partij</RegisteredName>
          </AffiliationIdentifier>
          <Elected>yes</Elected>
        </Selection>
        <Selection>
          <Candidate>
            <CandidateIdentifier Id="1" ShortCode="BakkerA"/>
            <CandidateFullName>
              <xnl:PersonName>
                <xnl:NameLine NameType="Initials">A.</xnl:NameLine>
                <xnl:FirstName>André</xnl:FirstName>
                <xnl:NamePrefix/>
                <xnl:LastName>Bakker</xnl:LastName>
              </xnl:PersonName>
            </CandidateFullName>
            <Gender>male</Gender>
            <QualifyingAddress>
              <xal:Locality>
                <xal:LocalityName>Bunnik</xal:LocalityName>
              </xal:Locality>
            </QualifyingAddress>
          </Candidate>
          <Ranking>1</Ranking>
          <Elected>yes</Elected>
        </Selection>
        ...
      </Contest>
    </Election>
  </Result>
</EML>
```