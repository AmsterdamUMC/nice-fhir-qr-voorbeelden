# 2025Q1

In de 2025Q1 hebben we de volgende aanpassingen ten aanzien van 2024Q1 gemaakt.


## Verwijzingen van codesystemen zijn nu goed opgenomen in de voorbeelden 
In de 2024Q1 voorbeelden is in de url van de ValueCoding Items een fout gemaakt. In de url wordt  
verwezen naar de ValueSet. Dit moet volgens de FHIR standaard CodeSystem zijn. In het codesystem 
worden namelijk de concept gedefinieerd, terwijl een valueset wordt gebruikt om aan te geven welke  
codes uit een codesystem mogen worden gebruikt.  

Als voorbeeld het item adm_type uit de 2024Q1
~~~XML
<item>
	<linkId value="adm_type"/>
	<answer>
		<valueCoding>
			<system value="https://fhir.stichting-nice.nl/R4/ValueSet/adm-type-2023Q3"/>
			<code value="1"/>
		</valueCoding>
	</answer>
</item>
~~~

De nieuwe url voor het item adm_type, waarbij alleen `ValueSet` is vervangen door `CodeSystem`. Het 
id van het codesystem (hier `adm-type2023Q3`) blijft ongewijzigd.
~~~XML
<item>
	<linkId value="adm_type"/>
	<answer>
		<valueCoding>
			<system value="https://fhir.stichting-nice.nl/R4/CodeSystem/adm-type-2023Q3"/>
			<code value="1"/>
		</valueCoding>
	</answer>
</item>
~~~

Dit geldt voor alle verwijzingen met het system waarbij de url begint met fhir.stichting-nice.nl.

Op de huidige server wordt het system niet gecontroleerd. Op de nieuwe FHIR server wordt wel gecontroleerd 
op het system. Met als gevolg dat het bericht niet zal voldoen aan de FHIR validatie (het komt niet overeen met d
questionnaire en/of profile). Met de bovenstaande wijziging voldoet het berichten aan de nieuwe validatie 
regels.
 
Het is nog onbekend wanneer de nieuwe fhir server in productie wordt genomen, maar we hopen op de eerste helft van 2025.

## Complicatie_day tabel is nu gewijzigd naar complicatie_kalenderdag
De FHIR standaard staat het niet toe dat items dezelfde linkId hebben. Op de nieuwe server werd de complicatie_day
geweigerd, omdat dit linkId `complicatie_day` twee keer werd gebruikt. Namelijk in als tabelnaam en als veldnaam in 
dezelfde tabel. Omdat het veld complicatie_day onderdeel is van de primary key, is er besloten de tabelnaam 
aan te passen naar `complicatie_kalenderdag`.

Voor de datasets (msAccess, CSV) geldt dat beide namen, dus complicatie_day en complicatie_kalenderdag worden 
geaccepteerd. Hier hoeft dus geen wijziging in plaats te vinden, mag wel.


## In de sofa-2025Q1 is het veld vasopressine toegevoegd
In de datadictionary update van 2024Q3 was de wijziging in de sofa aangekondigd. Nu is dit ook opgenomen in de FHIR.
Zie ook [https://stichting-nice.nl/dd/#11466](https://stichting-nice.nl/dd/#11466).

## MDS velden (adm_date_hosp, dis_date_hosp) zijn veranderd van DATE naar DATETIME 
In de datadictionary update was ook aangegeven dat het ziekenhuisopname en -ontslag wordt aangepast, zodat er ook een tijd
kan worden meegestuurd. Omdit in FHIR mogelijk te maken is het datatype van de veld `adm_date_hosp` en `dis_date_hosp` 
aangepast naar het type `datetime`.

