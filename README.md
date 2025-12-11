![alt text](d85576ee-54d2-4c74-bd27-47db4070ae90.png)


# IOT Biogas metingen
## Biogas groep: 2 

#### Opleiding: 3ITIOT1
#### Academiejaar: 2025-2026

#### studenten: Mathias Vansteensel, Berre Neyrinck
#### projectverantwoordeijke: Dirk van Merode
  
# Table of contents:
- [IOT Biogas metingen](#iot-biogas-metingen)
  - [Biogas groep: 2](#biogas-groep-2)
      - [Opleiding: 3ITIOT1](#opleiding-3itiot1)
      - [Academiejaar: 2025-2026](#academiejaar-2025-2026)
      - [studenten: Mathias Vansteensel, Berre Neyrinck](#studenten-mathias-vansteensel-berre-neyrinck)
      - [projectverantwoordeijke: Dirk van Merode](#projectverantwoordeijke-dirk-van-merode)
- [Table of contents:](#table-of-contents)
  - [Vakjargon](#vakjargon)
- [Introductie](#introductie)
  - [Huidige situatie](#huidige-situatie)
  - [Info over Ardhi University](#info-over-ardhi-university)
  - [Probleemstelling](#probleemstelling)
  - [Voorgestelde oplossing](#voorgestelde-oplossing)
- [Component keuzes:](#component-keuzes)
    - [Bill of Materials (BOM)](#bill-of-materials-bom)
      - [CO2/CH4 vergelijking](#co2ch4-vergelijking)
      - [waterlevel sensor vergelijking](#waterlevel-sensor-vergelijking)
      - [Temperatuur sensor vergelijking](#temperatuur-sensor-vergelijking)
- [Documentatie](#documentatie)
  - [Marktonderzoek](#marktonderzoek)
  - [Gasonderzoek](#gasonderzoek)
    - [Hydrolyse](#hydrolyse)
    - [Acidegonesis](#acidegonesis)
    - [Acetogenesis](#acetogenesis)
    - [Methanongenesis](#methanongenesis)
    - [Filtratie systeem output gas](#filtratie-systeem-output-gas)
  - [Gekozen sensoren](#gekozen-sensoren)
  - [Datacommunicatie](#datacommunicatie)
    - [MQTT + AT-Commands](#mqtt--at-commands)
  - [Code werking](#code-werking)
  - [PCB Design](#pcb-design)
  - [Communicatie](#communicatie)
  - [APTerra](#apterra)
    - [APTerra Documentatie](#apterra-documentatie)
      - [APTerra Devices](#apterra-devices)
  - [Tegengekomen Problemen](#tegengekomen-problemen)
  - [Display APterra](#display-apterra)
- [Bibliografie](#bibliografie)


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

# Introductie
## Huidige situatie

Dit project maakt deel uit van een groter project van Student for Energy in Afrea, Ardhi University en Vliruos. De meest gebruikte vorm van energie in Noord, Oost en West Afrika is energie gecreëerd door het branden van kolen en hout. De stad van aanpak *Mimbiji* valt ook onder deze norm. Om de schakel te maken naar de veel groenere biomassa zijn er plannen om over heel afrika, beginnend met de kleinere steden, Bioreactors te plaatsen die de lokale bevolking van groene energie voorzien die gebruikt kan worden als substituut voor hun momentele kool -en olie energie. Momenteel staat er een volledige biogas-plant geïnstalleerd in Kimbiji die lokaal groenafval gebruikt in een aerobic systeem om het afval te laten verteren en omzetten in biogas en inerte biomassa. Het geproduceerd gas wordt dan naar buiten gesluisd door een filtratie systeem dat de biogas combinatie van CO2, CH4 en enige resterende gassen door meerdere filters zal brengen met als eindproduct een zo zuiver mogelijk CH4-rijk gas dat ze kompressen in gasflessen aan het einde van de cyclus.De resterende, interte biomassa kan afgevoerd worden om te dienen als mest en het bewerkt water kan zijn nut vinden in industriele processen of zelfs irrigatie voor planten om meer biomassa te genereren. Deze opstelling werkt momenteel al aan een bepaalde efficiëntie maar deze valt niet te meten aangezien dat het volledige systeem geen enkel digitaal meetpunt bevat dat data opslaagd voor toekomstige verbetering. Om lokale bewoners te overtuigen hun bioafval af te geven aan de plantage zal er een initiatief opgesteld worden dat als bewoners hun bioafval naar de bio-reactor brengen ze een kleine hoeveelheid methaangas in ruil krijgen.

## Info over Ardhi University

Ardhi university is een publieke universiteit die aanwezig in in Dar es Salaam. Zij zijn ook ineens de organisator van meerdere biogas-reactor projecten rondom Dar es Salaam zelf. De universiteit werkt samen met AP-hogeschool en Uhasselt in een energieproject dat biogas reactoren gebruikt om biologisch afval zoals keukenresten, boomafval en fecale materie om te vormen naar een rauw biogas en dit te filteren naar een bruikbare-schone energie.

Momenteel bezit Ardhi een redelijke hoeveelheid bioreactoren van kleine 8L digesters, tot meer dan 1000+ liter installaties.

## Probleemstelling

De hoeveelheid Methaan-rijke biogas dat wordt geproduceerd is momenteel ongemeten. Hierdoor weten we niet exact hoe efficiënt het volledig proces is. De hoeveelheid water aanwezig in de bioafval verteerder ten opzichte van de hoeveelheid biomassa is momenteel ook niet opgemeten. Dit te samen met een onbekende temperatuur zorgt voor een incompleet overzicht over het volledig proces waardoor er mogelijke verbeteringen over het hoofd worden gezien. Er zal een volledig meetsysteem moeten komen dat het biogas over meerdere punten opmeet tijdens het proces en deze data kan opsturen naar een dashboard. Met een complete meetopstelling maken we het mogelijk de bioreactor te monitoren en optimaliseren alsook een leesbare output creëren voor de data, zoals de hoeveelheid CH4 in het eindproduct, te bekijken.

## Voorgestelde oplossing

Wij ontwerpen een systeem dat in de digester metingen zal uitvoeren.
In de ton zelf hebben we een CO2/CH4 sensor om een volume meting te doen van de gassen en op deze manier te achterhalen in welke stage van vertering we zitten. Een temperatuurmeter zal geïnstalleerd worden die ons kan helpen de efficiëntie van de productie van het biogas te berekenen. Een drukmeter en een waterlevel meter zullen gebruikt worden om ons te vertellen of er te weinig bioafval of water in de verteerder zit en ons zo notificeren dat mogelijks één van beide moet bijgevuld worden.  

# Component keuzes:

### Bill of Materials (BOM)

| Naam | Kost | hoeveelheid | link naar artikel |
| ----- | ----- | ----- | ----- |
| PLACEHOLDER | 0.99$ | 1 | www.smth.com |

#### CO2/CH4 vergelijking

|| MGP261 | MGP262 | ATO-ICDS-7042A | cubic CH4 sensor | GFG IR29 B |
| -------- | ------- | ------- | ----- | ----- |
| CH4 Range                     | 0-100% vol | 0-5% | 0-100% | 0-100% | 0-100% |
| CO2 Range                     | 0-100% vol  | 0-100% | 0% | 0% | N/A |
| Accuracy                      | +- 1% | +-1% | 0.1% | +-6% | 0.1% |
| Ex-rating                     | Zone 0/1 | ATEX/IECEx  | Zone 1/2  | N/A | IP68 |
| corrosion resistance          | IP66 | IP66 | N/A | N/A | N/A |
| Humidity rating               | 0-100%RH | 0-100%RH | 0-95%RH| 0-95% | N/A | 
| communcatie                   | rs-485 modbus  | rs-485 modbus | UART | UART | rs-485 modbus |
| prijs                         | Quote: 15.499$   | 99$  | 992.31$ | 283.25$ | 1670$ |
| voltage                       | 18-30V DC | 18-30V DC | 5V DC | 3.3-5V DC | 18-30V DC |
| stroom                        | 20mA  | 20mA | 60mA | 55mA | N/A |
| sustainability rating         | Ecovadis top5%  | Ecovadis top5% | N/A | N/A | N/A |

#### waterlevel sensor vergelijking

|| ENELSAN Ultrasonic | VEGAPULS C11 | IJINUS water level sensor |
| -------- | ------- | ------- | ----- |
| technologie               | ultrasonic | radar | ultrasonic | 
| Corrosion resistance      | IP65 | IP68 | IP68 | 
| communicatie              | rs-485 modbus | bluetooth | rs-485 modbus | 
| prijs                     | Quote: N/A | 550$ | Quote: N/A |
| voltage                   | 6V | 12-35V DC | 5-30V internal battery | 
| stroom                    | 300mA | 20mA | N/A | 

#### Temperatuur sensor vergelijking

|| Antratek FG6485A | Antratek  101991101 | TRU COMPONENTS PT100 Temperature sensor |
| -------- | ------- | ------- | ----- |
| Temp range                    | -40 - 120°C | -40 - 125°C | -100°C - 200°C | 
| Corrosion resistance          | N/A | N/A | stainless steel | 
| Humidity rating               | 0-99.9%RH | 0-10 0%RH | N/A |
| Bar sensor                    | N/A | 300 - 1100hpA | N/A |
| communicatie                  | rs-485 | rs-485 modbus | Analog | 
| prijs                         | 60,38$ | 72,54$ | 32.99$ |
| voltage                       | 9-36V DC | 4.5-18V DC | 3.3Vmin | 
| stroom                        | 15mA | 10mA | N/A | 

 
# Documentatie

## Marktonderzoek
In België zijn er een grote hoeveelheid verengingen die puur en alleen over Biogas en Biomethaan gaan. Een aantal van deze verenigingen hosten ook bijeenkomsten waar je “vrij” naartoe kan vermits je een ticket aankoopt. De meeste onderwerpen die voorbij komen tijdens deze evenementen is eerder wel wat bedrijven hun werkprocess is of wat voor soorten biogas metingen ze uitvoeren. 

Er zijn een heel aantal bedrijven die zich bezighouden met biogas waar je extra informatie aan kunt vragen, dit zal dan ook mogelijks zeer handig zijn voor een diepere kennis te vergaren van de industriële werking van Biogas generatie. Èen zo een bedrijf is bijvoorbeeld Inagro die sinds kort een groot project hebben afgesloten waarbij ze volledige testopstellinge en ontledingen deden voor het biogas-productie & meting process.

| Bedrijf / Conventie | Link |
| -------- | ------- |
| Inagro                    | https://inagro.be/projecten/biogas-mambo |
| EUBioweek                 | https://www.europeanbiomethaneweek.eu/   |
| bright-renewables         | https://www.bright-renewables.com/       |

 
## Gasonderzoek

![Degradatie Bioafval](image.png)
*Voorbeelddiagram conversie bioafval naar CH4, CO2 en reststoffen*


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

### Filtratie systeem output gas

Het gasproduct dat geproduceerd wordt door de digester zal door een uitlaat aan de bovenkant van de digester door een filtratiesysteem sturen. Eerst zal het rauwe biogas door een vocht-vanger die enige overblijfselen van waterdamp uit het gas haalt. Hierna zal de mix door een "desulfurizer" gaan die enige aanwezigheid van H2S zal verwijderen uit de mix om deze daarna naar een compressor en gasdebiet-meter om het resterende gas op te slagen.

## Gekozen sensoren

||Component|reden|
|------|---------|-------|
|CO2/CH4| | |
|Waterlevel sensor|  ||
|temperatuur sensor | TRU COMPONENTS PT100| beste prijs-kwaliteit, hogere temperatuurschaal voor foutdetectie, corrosie resistent|
|drukmeter |||

## Datacommunicatie

Bij dit project wordt er gebruik gemaakt van het communicatieprotocol "MQTT" oftewel "Message Queuing Telemetry Transport". Via MQTT kunnnen we makkelijk subscriben op de topic van ons apparaat dat via APTerra gegeven wordt. Ons transportprotocol zal 4G zijn via een ESP32-4G addon module dat een SIM kaart gebruikt voor dit te realiseren. 

### MQTT + AT-Commands

Eerst tests waren uitgevoerd via een mobiele app genaamd "MyMQTT". Dit gaf ons een snelle manier om de connectiviteit tussen een sender en de APTerra server te bekijken zonder enige opstelling of code. MyMQTT werkt door de topic op te geven waar er naar gestuurd moet worden en een text-prompt veld om data in te zetten met een parameter naam. Dit heeft ons dan na een redelijk korte tijd al een eerste resultaat opgeleverd om te beginnen met MQTT.

De 4TG module hebben we eerst getest met een Arduino prototype programma dat simpele AT-commands invoerbaar maakt om zo te werken met de module. Mathias had nog een stuk code liggen die hij hiervoor zeer snel kon retrofitten aan de 4G-module voor de ESP. Met een directe connectie van de module aan een laptop hebben we al snel een resultaat kunnen produceren voor onze module.

Onze twweede test die uitgevoerd werd op de 4G-module werd weer gedaan met prototype code maar dan in combinatie met de ESP-controller zelven. Via een aantal Arduino libraries, namelijk: SPI.h, PubSubClient.h en TinyGSMClient.h heeft Mathias een "first prototype" gecreërd dat een connectie vastlegd tussen de ESP-module en de 4G module en dan een MQTT connectie kan leggen tussen de ESP en de APTerra server.

## Code werking
## PCB Design
## Communicatie 
<!-- 
De communicatie tussen de componenten en de main controller zal gebeuren via rs-485 mdobus. Dit laat ons toe een simpele fysieke structuur op te bouwen om data terug te sturen naar de controller.

Als de data ge collect is zal deze doorgestuurd worden via 4G naar APTerra via MQTT -->

## APTerra

APTerra is het modulair dashboard van AP gemaakt door studenten van vorige jaren. Hierin zijn meerdere projecten en hun data beschikbaar om naar te kijken. één van deze projecten, namelijk "Biogas #2" is waar wij onze data naartoe zullen sturen en vertonen in grafieken en dergelijke presentatiemethoden. Aangezien de documentatie van APTerra zeer schaars is zullen wij proberen hier een kleine "how-to" te creëren om snel te werk te gaan met APTerra. 

### APTerra Documentatie

Met een stabiele internet connectie, surf naar "https://www.apterra.be/" en klik op "Log in". Eenmaal hier wordt de gebruiker gevraagd login-credentials te geven. Deze credentials zijn je studenten e-mail (Vb. Berre.neyrinck@student.ap.be) en je wachtwoord dat gelinkt is aan je AP-hogeschool account. Mogelijks is het nodig dat de leerkracht toegang verleend tot de werk-site van je project voordat je eenmaal devices kan aanmaken. Als dit eenmaal geregeld is, is het mogelijk om rechtsboven naar "My Projects" te gaan en zo een overzicht te krijgen van alle projecten waartoe jij rechten hebt.

Eenmaal dit afgerond is kan je clicken op "Launch AP_Terra" dit brengt je naar de "backend" waar je devices kan aanmaken & configureren alsook input data van deze sensoren lezen in een grafiek of dergelijke.

#### APTerra Devices

Om een device aan te maken, en zo een topic te krijgen voor datatransmissie, ga je naar: "Settings --> Create Device" Hierna wordt de gebruiker in een creation wizard gezet om hem door het process te leiden van een apparaaat configureren en klaar te maken voor gebruik.
De keuzes voor protocollen van het device zijn:

|soorten |
|-----|
| TTN Network |
| Wifi or LTE device using MQTT |
| Camera |
| (TTN) Gateway |

Eenmaal het soort device gekozen is wordt de gebruiker gevraagd naar een aantal extra informatie punten gevraagd zoals: naam, descriptie, *send first argument as timestamp, image for device en location

*"Send first argument as timestamp" wordt gebruikt bij situaties zoals: Het device heeft data gemeten maar kon deze niet direct opsturen. Door deze setting aan te klikken wordt de eerste parameter doorgestuurd met een timestamp eraan gekoppeld om nog altijd accurate tijdsgebonden data te krijgen.

Na deze informatie in te geven wordt de gebruiker gevraagd een aantal parameters in te geven. Deze parameters zullen het mogelijk maken verschillende soorten data naar APTerra te sturen en deze in grafieken te steken. De volgende pagina vraagt om een aantal parameters in te geven, de hoeveelheid komt hier overeen met de hoeveelheid data die doorgestuurd moet worden. 

Na al deze configuraties in te stellen toont de site de naam van de server die het device zich aan zal koppelen alsook de title van het topic dat de device gebruikt om zijn data uit te lezen. Het is best hier een screenshot van te nemen aangezien deze pagina niet terug opgeroepen kan worden.

## Tegengekomen Problemen

Halverwege door de onderzoeksfase is onze scope verkleint en bepaalde vastgelegde statistieken omgegooid

## Display APterra

![APTerra dashboard display](<Schermafbeelding 2025-11-14 142013.png>)

# Bibliografie

 