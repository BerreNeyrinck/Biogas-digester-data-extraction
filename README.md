![alt text](d85576ee-54d2-4c74-bd27-47db4070ae90.png)


# 1. IOT Biogas metingen
## Biogas groep: 2 

#### Opleiding: 3ITIOT1
#### Academiejaar: 2025-2026

#### studenten: Mathias Vansteensel, Berre Neyrinck
#### projectverantwoordeijke: Dirk van Merode
  
# Table of contents:
- [1. IOT Biogas metingen](#1-iot-biogas-metingen)
  - [Biogas groep: 2](#biogas-groep-2)
      - [Opleiding: 3ITIOT1](#opleiding-3itiot1)
      - [Academiejaar: 2025-2026](#academiejaar-2025-2026)
      - [studenten: Mathias Vansteensel, Berre Neyrinck](#studenten-mathias-vansteensel-berre-neyrinck)
      - [projectverantwoordeijke: Dirk van Merode](#projectverantwoordeijke-dirk-van-merode)
- [Table of contents:](#table-of-contents)
  - [Vakjargon](#vakjargon)
- [1.	Introductie](#1introductie)
  - [1.1.	Huidige situatie](#11huidige-situatie)
  - [1.2. Info over Ardhi University](#12-info-over-ardhi-university)
  - [1.3.	Probleemstelling](#13probleemstelling)
  - [1.4.	Voorgestelde oplossing](#14voorgestelde-oplossing)
- [2. Component keuzes:](#2-component-keuzes)
    - [2.1 Bill of Materials (BOM)](#21-bill-of-materials-bom)
      - [2.2.1 CO2/CH4 vergelijking](#221-co2ch4-vergelijking)
      - [2.2. waterlevel sensor vergelijking](#22-waterlevel-sensor-vergelijking)
      - [2.3. Temperatuur sensor vergelijking](#23-temperatuur-sensor-vergelijking)
- [3.	Documentatie](#3documentatie)
  - [3.1.	Marktonderzoek](#31marktonderzoek)
  - [3.2.	Gasonderzoek](#32gasonderzoek)
    - [Hydrolyse](#hydrolyse)
    - [Acidegonesis](#acidegonesis)
    - [Acetogenesis](#acetogenesis)
    - [Methanongenesis](#methanongenesis)
    - [3.2.1. Filtratie systeem output gas](#321-filtratie-systeem-output-gas)
  - [3.3.	Gekozen sensoren](#33gekozen-sensoren)
  - [3.4.	Code werking](#34code-werking)
  - [3.5.	PCB Design](#35pcb-design)
  - [3.6.	Communicatie](#36communicatie)
  - [3.7.	Tegengekomen Problemen](#37tegengekomen-problemen)
  - [3.8.	Display APterra](#38display-apterra)
- [4.	Bibliografie](#4bibliografie)


## Vakjargon
| Afkorting / Term | Betekenis |
|------------------|------------|
| **IoT** | *Internet of Things* – netwerk van fysieke apparaten die via internet gegevens verzamelen en uitwisselen. |
| **RS-485** | Industriële communicatiestandaard voor seriële dataoverdracht tussen sensoren en controllers. |
| **Modbus** | Communicatieprotocol dat gebruikt wordt voor het verzenden van gegevens via RS-485 tussen meetinstrumenten en controllers. |
| **MQTT** | Lichtgewicht protocol voor datatransport tussen IoT-apparaten en een online dashboard of server. |
| **APTerra** | Online platform waarop sensordata van het IoT-systeem visueel weergegeven wordt. |
| **Biogas** | Gasmengsel (hoofdzakelijk methaan en koolstofdioxide) dat ontstaat door de vergisting van organisch afval. |
| **CH₄ (Methaan)** | Hoofdbestanddeel van biogas; brandbaar gas dat energie levert bij verbranding. |
| **CO₂ (Koolstofdioxide)** | Gas dat samen met methaan ontstaat tijdens vergisting; niet-brandbaar. |
| **Digester / Vergister** | Afgesloten tank waarin biologisch afval onder anaerobe omstandigheden wordt afgebroken tot biogas. |
| **Anaeroob proces** | Biologisch proces dat plaatsvindt zonder zuurstof, typisch voor biogasproductie. |
| **Waterlevel sensor** | Sensor die het vloeistofniveau in de vergister meet. |
| **Temperatuursensor** | Meetinstrument dat de temperatuur meet |
| **Druksensor** | Sensor die de gasdruk in een systeem meet|
| **PCB (Printed Circuit Board)** | printbord waarop elektronische componenten gemonteerd zijn. |
| **Ecovadis** | Beoordelingssysteem dat bedrijven evalueert op duurzaamheid en maatschappelijk verantwoord ondernemen. |
| **ATEX / IECEx** | Certificeringsnormen die aanduiden dat apparatuur veilig is voor gebruik in explosiegevaarlijke omgevingen. |
| **IP-rating (Ingress Protection)** | Internationale standaard die de mate van bescherming van een apparaat tegen stof en water aangeeft. |
| **Desulfurizer** | Onderdeel dat zwavelhoudende gassen (zoals H₂S) uit biogas verwijdert. |
| **Vochtvanger / Condensafscheider** | Filter die waterdamp uit het biogas verwijdert om corrosie te voorkomen. |
| **Compressor** | Apparaat dat gas samenperst voor opslag in tanks. |
| **Dashboard** | Digitale gebruikersinterface waar de meetdata van het systeem in real time wordt weergegeven. |
| **Kimbiji** | Plaats in Tanzania waar de biogasinstallatie van het project zich bevindt. |
| **Biomassa** | Organisch materiaal (zoals plantaardig afval) dat als grondstof dient voor energieproductie. |
| **VLIROUS** | Vlaams samenwerkingsprogramma dat partnerschappen ondersteunt tussen Vlaamse en Afrikaanse universiteiten. |

# 1.	Introductie
## 1.1.	Huidige situatie

Dit project maakt deel uit van een groter project van Student for Energy in Afrea, Ardhi University en Vliruos. De meest gebruikte vorm van energie in Noord, Oost en West Afrika is energie gecreëerd door het branden van kolen en hout. De stad van aanpak *Mimbiji* valt ook onder deze norm. Om de schakel te maken naar de veel groenere biomassa zijn er plannen om over heel afrika, beginnend met de kleinere steden, Bioreactors te plaatsen die de lokale bevolking van groene energie voorzien die gebruikt kan worden als substituut voor hun momentele kool -en olie energie. Momenteel staat er een volledige biogas-plant geïnstalleerd in Kimbiji die lokaal groenafval gebruikt in een aerobic systeem om het afval te laten verteren en omzetten in biogas en inerte biomassa. Het geproduceerd gas wordt dan naar buiten gesluisd door een filtratie systeem dat de biogas combinatie van CO2, CH4 en enige resterende gassen door meerdere filters zal brengen met als eindproduct een zo zuiver mogelijk CH4-rijk gas dat ze kompressen in gasflessen aan het einde van de cyclus.De resterende, interte biomassa kan afgevoerd worden om te dienen als mest en het bewerkt water kan zijn nut vinden in industriele processen of zelfs irrigatie voor planten om meer biomassa te genereren. Deze opstelling werkt momenteel al aan een bepaalde efficiëntie maar deze valt niet te meten aangezien dat het volledige systeem geen enkel digitaal meetpunt bevat dat data opslaagd voor toekomstige verbetering. Om lokale bewoners te overtuigen hun bioafval af te geven aan de plantage zal er een initiatief opgesteld worden dat als bewoners hun bioafval naar de bio-reactor brengen ze een kleine hoeveelheid methaangas in ruil krijgen.

## 1.2. Info over Ardhi University

Ardhi university is een publieke universiteit die aanwezig in in Dar es Salaam. Zij zijn ook ineens de organisator van meerdere biogas-reactor projecten rondom Dar es Salaam zelf. De universiteit werkt samen met AP-hogeschool en Uhasselt in een energieproject dat biogas reactoren gebruikt om biologisch afval zoals keukenresten, boomafval en fecale materie om te vormen naar een rauw biogas en dit te filteren naar een bruikbare-schone energie.

Momenteel bezit Ardhi een redelijke hoeveelheid bioreactoren van kleine 8L digesters, tot meer dan 1000+ liter installaties.

## 1.3.	Probleemstelling

De hoeveelheid Methaan-rijke biogas dat wordt geproduceerd is momenteel ongemeten. Hierdoor weten we niet exact hoe efficiënt het volledig proces is. De hoeveelheid water aanwezig in de bioafval verteerder ten opzichte van de hoeveelheid biomassa is momenteel ook niet opgemeten. Dit te samen met een onbekende temperatuur zorgt voor een incompleet overzicht over het volledig proces waardoor er mogelijke verbeteringen over het hoofd worden gezien. Er zal een volledig meetsysteem moeten komen dat het biogas over meerdere punten opmeet tijdens het proces en deze data kan opsturen naar een dashboard. Met een complete meetopstelling maken we het mogelijk de bioreactor te monitoren en optimaliseren alsook een leesbare output creëren voor de data, zoals de hoeveelheid CH4 in het eindproduct, te bekijken.

## 1.4.	Voorgestelde oplossing

Wij ontwerpen een systeem dat in de digester metingen zal uitvoeren.
In de ton zelf hebben we een CO2/CH4 sensor om een volume meting te doen van de gassen en op deze manier te achterhalen in welke stage van vertering we zitten. Een temperatuurmeter zal geïnstalleerd worden die ons kan helpen de efficiëntie van de productie van het biogas te berekenen. Een drukmeter en een waterlevel meter zullen gebruikt worden om ons te vertellen of er te weinig bioafval of water in de verteerder zit en ons zo notificeren dat mogelijks één van beide moet bijgevuld worden.  

# 2. Component keuzes:

### 2.1 Bill of Materials (BOM)

| Naam | Kost | hoeveelheid | link naar artikel |
| ----- | ----- | ----- | ----- |
| PLACEHOLDER | 0.99$ | 1 | www.smth.com |

#### 2.2.1 CO2/CH4 vergelijking

|| MGP261 | MGP262 | ATO-ICDS-7042A | cubic CH4 sensor | 
| -------- | ------- | ------- | ----- | ----- |
| CH4 Range                     | 0-100% vol | 0-5% | 0-100% | 0-100% |
| CO2 Range                     | 0-100% vol  | 0-100% | 0% | 0% |
| Accuracy                      | +- 1% | +-1% | 0.1% | +-6% |
| Ex-rating                     | Zone 0/1 | ATEX/IECEx  | Zone 1/2  | N/A |
| corrosion resistance          | IP66 | IP66 | N/A | N/A |
| Humidity rating               | 0-100%RH | 0-100%RH | 0-95%RH| 0-95% | 
| communcatie                   | rs-485 modbus  | rs-485 modbus | UART | UART |
| prijs                         | Quote: 15.499$   | 99$  | 992.31$ | 283.25$ |
| voltage                       | 18-30V DC | 18-30V DC | 5V DC | 3.3-5V DC |
| stroom                        | 20mA  | 20mA | 60mA | 55mA |
| sustainability rating         | Ecovadis top5%  | Ecovadis top5% | N/A | N/A | 

#### 2.2. waterlevel sensor vergelijking

|| ENELSAN Ultrasonic | VEGAPULS C11 | IJINUS water level sensor |
| -------- | ------- | ------- | ----- |
| technologie               | ultrasonic | radar | ultrasonic | 
| Corrosion resistance      | IP65 | IP68 | IP68 | 
| communicatie              | rs-485 modbus | bluetooth | rs-485 modbus | 
| prijs                     | Quote: N/A | 550$ | Quote: N/A |
| voltage                   | 6V | 12-35V DC | 5-30V internal battery | 
| stroom                    | 300mA | 20mA | N/A | 

#### 2.3. Temperatuur sensor vergelijking

|| Antratek FG6485A | Antratek  101991101 |  |
| -------- | ------- | ------- | ----- |
| Temp range                    | -40 - 120°C | -40 - 125°C |  | 
| Corrosion resistance          | N/A | N/A |  | 
| Humidity rating               | 0-99.9%RH | 0-10 0%RH |  |
| Bar sensor                    | no | 300 - 1100hpA | |
| communicatie                  | rs-485 | rs-485 modbus |  | 
| prijs                         | 60,38$ | 72,54$ |  |
| voltage                       | 9-36V DC | 4.5-18V DC |  | 
| stroom                        | 15mA | 10mA | | 

 
# 3.	Documentatie

## 3.1.	Marktonderzoek
In België zijn er een grote hoeveelheid verengingen die puur en alleen over Biogas en Biomethaan gaan. Een aantal van deze verenigingen hosten ook bijeenkomsten waar je “vrij” naartoe kan vermits je een ticket aankoopt.

Er zijn ook een heel aantal bedrijven die zich bezighouden met biogas waar je extra informatie aan kunt vragen, dit zal dan ook mogelijks zeer handig zijn voor een diepere kennis te vergaren van de industriële werking van Biogas generatie.

| Bedrijf / Conventie | Link |
| -------- | ------- |
| Inagro                    | https://inagro.be/projecten/biogas-mambo |
| EUBioweek                 | https://www.europeanbiomethaneweek.eu/   |
| bright-renewables         | https://www.bright-renewables.com/       |

 
## 3.2.	Gasonderzoek

![Degradatie Bioafval](image.png)
*Voorbeelddiagram conversie bioafval naar CH4, CO2*


| Verzameling thesis -en onderzoekslinks:| |
| ----- | ----- | 
| Cheng Denmark University| [Thesis PDF](https://backend.orbit.dtu.dk/ws/portalfiles/portal/5245572/ENV2010-283.pdf) |
| Thesis UHasselt Corthouts, Vanhoudt | [Thesis PDF ](https://documentserver.uhasselt.be/bitstream/1942/35064/1/e4357d7c-3aea-4cc1-a09b-78bb3e2e0138.pdf) |

Het process dat we gaan bekijken is een "anaerobisch process" Wat simpelweg betekent dat dit een luchtvrij systeem is waar bacteriën het bioafval afbreken in simpele stoffen die zich weer samen zullen voegen tot er uitijndelijk een stabiel gas "CH4 fo CO2" uitkomt.

### Hydrolyse
De eerste stap in het vergisten van het complex bioafval is de Hydrolyse. Het hydrolyse process in het systeem zal ervoor zorgen dat de bacteriën deze materie afbreken in simpele stoffen zoals: suikers, acetaten, enzymen, vetzuren en aminozuren. Deze materialen zullen de basis vormen van onze methaan productie in de digester van de biogas reactor. 

### Acidegonesis 
Eenmaal afgebroken, zullen de fermentatieve bacteriën deze simpele materies omvormen naar: Waterstof, ammonia en onverzadigd vetzuur. 

### Acetogenesis
Onverzadigd vetzuur zal zich weer opsplitsen in meerdere delen materie namelijk: acetaten, koolstofdioxide(CO2) en waterstof. Deze acetaten en waterstof zullen in de volgende fase samebinden om als product methaangas(CH4) op te leveren. 

### Methanongenesis
Als de laatste stap zullen methagonese bacteriën deze acetaten en waterstof samenbinden tot een methaan. Deze conversie is allesins niet perfect aangezien een bijproduct van de binding nog meer CO2 is.

Tegen het einde van de cyclus, ervanuitgaande dat onze reactor schommelt tussen 40°C & 90°C zullen we een schattelijk eindproduct krijgen van 65% CH4 en 35% CO2 inclusief reststoffen die er later uit ge filterd moeten worden.

### 3.2.1. Filtratie systeem output gas

Het gasproduct dat geproduceerd wordt door de digester zal door een uitlaat aan de bovenkant van de digester door een filtratiesysteem sturen. Eerst zal het rauwe biogas door een vocht-vanger die enige overblijfselen van waterdamp uit het gas haalt. Hierna zal de mix door een "desulfurizer" gaan die enige aanwezigheid van H2S zal verwijderen uit de mix om deze daarna naar een compressor en gasdebiet-meter om het resterende gas op te slagen.

## 3.3.	Gekozen sensoren

||Component|reden|
|------|---------|-------|
|CO2/CH4| MGP261| beste range CH4/CO2, Ecovadis top 5%, IP68|
|Waterlevel sensor| ENELSAN ultrasonic| IP65, rs-485 modbus |
|temperatuur sensor |||
|drukmeter |||

## 3.4.	Code werking
## 3.5.	PCB Design
## 3.6.	Communicatie 

De communicatie tussen de componenten en de main controller zal gebeuren via rs-485 mdobus. Dit laat ons toe een simpele fysieke structuur op te bouwen om data terug te sturen naar de controller.

Als de data ge collect is zal deze doorgestuurd worden via 4G naar APTerra via MQTT

## 3.7.	Tegengekomen Problemen

Halverwege door de onderzoeksfase is onze scope verkleint en bepaalde vastgelegde statistieken omgegooid

## 3.8.	Display APterra

# 4.	Bibliografie

 