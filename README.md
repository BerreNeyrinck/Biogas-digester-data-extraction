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
      - [Druk sensor vergelijking](#druk-sensor-vergelijking)
- [Documentatie](#documentatie)
  - [Marktonderzoek](#marktonderzoek)
  - [Gasonderzoek](#gasonderzoek)
    - [Hydrolyse](#hydrolyse)
    - [Acidegonesis](#acidegonesis)
    - [Acetogenesis](#acetogenesis)
    - [Methanongenesis](#methanongenesis)
    - [Filtratie systeem output gas](#filtratie-systeem-output-gas)
  - [Gekozen sensoren](#gekozen-sensoren)
  - [Solar Power Manager - Waveshare](#solar-power-manager---waveshare)
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
| Firebeetle WROOM V2 | 16.36$ | 1 | [LINK](https://benl.rs-online.com/web/p/arduino-compatible-boards-kits/2473219?cm_mmc=BE-PLA-DS3A-_-google-_-CSS_BENL_NL_Pmax_1224-_--_-2473219&matchtype=&&gclsrc=aw.ds&gad_source=1&gad_campaignid=22040006570&gclid=CjwKCAiAuIDJBhBoEiwAxhgyFuIoyhnAeTN-a6PcChIT0EpC9Am6lveoA97EagpxEp1wtjasvj7d2hoC6_gQAvD_BwE) |
| Power management module | 18.99$ | 1 | [LINK](https://www.amazon.com.be/-/en/Waveshare-Management-Protection-Controller-Environmental/dp/B094FWZVFH/ref=sr_1_2?adgrpid=159150164620&dib=eyJ2IjoiMSJ9.-7uAVmJb6Q2IoRJlDG2jZxfqE3feKhcpABjlgmcOI_q-jf5bFsbR13tlN4E3IH_5rfy7pfGtnpTTycywrak_AowxqEfIUH5-Vtkq5tnqM-4ICpxMb3_2ryCOEAQgj1R21MRgbJlpGvsUWWGCxSr5vVOAosyYzMMztZpOxvvB5kqn_90rnCy6Np-fRpd6dQVk8EZfTos21ivpUewuBwCE23GU1iV5usYjbkdZeWX3z-J_zIRwlPY_mEia5XwOSD2wJrYKJNBBWRAx27FxBxJUEj7DaKGvFANNIWVS77L-Jec.SNQBdjrmV2BTxfnSwooLobFmH6_XcF5-ozsu4SXOzys&dib_tag=se&gad_source=1&hvadid=689276129506&hvdev=c&hvlocphy=9195878&hvnetw=g&hvqmt=e&hvrand=95786312923268170&hvtargid=kwd-1188393181890&hydadcr=22453_2319041&keywords=waveshare+solar+power+manager&mcid=22da17078e243cdcada981499cc22827&qid=1763713271&sr=8-2) |
| zonnepaneel AP-gekozen | 32,99$ | 1 | TBD |
| CBW Water-Resistant Digital Temperature Sensor | 24.99 | 1 | [LINK](https://controlbyweb.com/accessories/temperature-probe/) |
| ANTRATEK 750cm waterlevel sensor | 30.13$ | 1 | [LINK](https://www.antratek.be/rs485-750cm-ultrasonic-level-sensor?utm_source=google&utm_medium=cpc&utm_campaign=**Pmax%20shopping%20-%20BE&utm_id=21792943403&gad_source=1&gad_campaignid=21786496926&gclid=CjwKCAiAuIDJBhBoEiwAxhgyFho_ZDgAMGiGCt2ahdCN1k3Aabqb8qdzxSV2KZTifyXQ2oIeflyrpBoCCCYQAvD_BwE) | 
| PREMASGARD® SHD-Modbus 2.5 LCD | 551.75$ | 1 | [LINK](https://www.spluss.de/en/products/pressure-measuring-transducer-premasgard-shd-modbus-2-5-lcd-0-2-5-bar-1301-2214-5530-221-p22881?_pos=1&_fid=6c2a87c96&_ss=c) |
| PLACEHOLDER | 0.99$ | 1 | www.smth.com |


#### CO2/CH4 vergelijking

|| MGP261 | MGP262 | ATO-ICDS-7042A | cubic CH4 sensor | GFG IR29 B | M2A-XL Stand Alone Transmitter | 
| -------- | ------- | ------- | ----- | ----- | ----- | ----- |
| CH4 Range                     | 0-100% vol | 0-5%vol | 0-100%lel | 0-100%vol | 0-100%LEL | 0-100% vol |
| CO2 Range                     | 0-100% vol  | 0-100% | 0% | 0% | N/A | 0-100% |
| Accuracy                      | +- 1% | +-1% | 0.1% | +-6% | 0.1% | 2% |
| Ex-rating                     | Zone 0/1 | ATEX/IECEx  | Zone 1/2  | N/A | IP68 | NEMA 4X  |
| IP-rating                     | IP66 | IP66 | N/A | N/A | N/A | N/A |
| Humidity rating               | 0-100%RH | 0-100%RH | 0-95%RH| 0-95% | N/A | 5 - 95%| 
| communcatie                   | rs-485 modbus  | rs-485 modbus | UART | UART | rs-485 modbus | rs-485 modbus |
| prijs                         | Quote: 15.499$ | 99$ * 100 (bulk bestelling) | 992.31$ | 283.25$ | 1670$ | Quote:  |
| voltage                       | 18-30V DC | 18-30V DC | 5V DC | 3.3-5V DC | 18-30V DC | 24V DC |
| stroom                        | 20mA  | 20mA | 60mA | 55mA | N/A | N/A |
| sustainability rating         | Ecovadis top5%  | Ecovadis top5% | N/A | N/A | N/A | N/A |

#### waterlevel sensor vergelijking

|| ENELSAN Ultrasonic | VEGAPULS C11 | IJINUS water level sensor | **ANTRATEK 750cm waterlevel sensor** | 
| -------- | ------- | ------- | ----- | ----- | 
| technologie               | ultrasonic | radar | ultrasonic | ultrasonic |
| IP-rating                 | IP65 | IP68 | IP68 | N/A( IEC61000-4-2.) |
| communicatie              | rs-485 modbus | bluetooth | rs-485 modbus | rs-485 modbus |
| prijs                     | Quote: N/A | 550$ | Quote: N/A | 30.13$ |
| voltage                   | 6V DC | 12-35V DC | 5-30V DC internal battery | 5-12V DC |  
| stroom                    | 300mA | 20mA | N/A | <10mA |

#### Temperatuur sensor vergelijking

|| Antratek FG6485A | Antratek  101991101 | **CBW Water-Resistant Digital Temperature Sensor** |
| -------- | ------- | ------- | ----- |
| Temp range                    | -40 - 120°C | -40 - 125°C | -55°C - 125°C | 
| Corrosion resistance          | N/A | N/A | stainless steel | stainless steel |
| Humidity rating               | 0-99.9%RH | 0-10 0%RH | N/A | N/A |
| Bar sensor                    | N/A | 300 - 1100hpA | N/A | N/A |
| communicatie                  | rs-485 | rs-485 modbus | Analog | 1-wire | 
| prijs                         | 60,38$ | 72,54$ | 32.99$ |24.99$ | 
| voltage                       | 9-36V DC | 4.5-18V DC | 3.3Vmin | 5V DC |
| stroom                        | 15mA | 10mA | N/A | N/A |

#### Druk sensor vergelijking
|| PREMASGARD® SHD-Modbus 2.5 LCD |
| ----- | ----- |
| barmeting | 0-2.5bar |
| accuracy | 0.2% |
| voltage | 0-10VDC |
| temp range | -20~75°C |
| IP-rating | IP65 |
 

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

||Component|reden|link| prijs |
|------|---------|-------| | |
|CO2/CH4| | | | |
|Waterlevel sensor| RS485 750cm Ultrasonic Level Sensor | Mogelijke uitberijdingsmogelijkheden & preciese resolutie | [LINK](https://www.antratek.be/rs485-750cm-ultrasonic-level-sensor?utm_source=google&utm_medium=cpc&utm_campaign=**Pmax%20shopping%20-%20BE&utm_id=21792943403&gad_source=1&gad_campaignid=21786496926&gclid=CjwKCAiAraXJBhBJEiwAjz7MZaTOe1ODPodRPymIbMsYi_lZ0X0MeJzXyM4Ad2MUsQ6_v71vo3egPRoC53UQAvD_BwE) | 30.13$ |
|temperatuur sensor | CBW Water-Resistant Digital Temperature Sensor | beste temp range, goede prijs-kwaliteit, roestbestendig | [LINK](https://controlbyweb.com/accessories/temperature-probe/) | 24.99$ |
|drukmeter | PREMASGARD® SHD-Modbus 2.5 LCD | modbus output, grote bar meting, goede Atex-proofing | [LINK](https://www.spluss.de/en/products/pressure-measuring-transducer-premasgard-shd-modbus-2-5-lcd-0-2-5-bar-1301-2214-5530-221-p22881?_pos=1&_fid=6c2a87c96&_ss=c) | 551.75$ |

## Solar Power Manager - Waveshare

De Waveshare Solar Power Management Module is een pwoer manager voor 6V-24V zonnepanelen. Het is ontworpen om een 3.7V Li-ion batterij op te laden met behulp van zonne-energie. De module gebruikt MPPT-techniek om het zonnepaneel optimaal te benutten en er de maximale hoeveelheid vermogen uit te halen. Het zorgt ervoor dat de batterij veilig en betrouwbaar wordt opgeladen en biedt ook een gestabiliseerde 5V-uitgang aan waarmee kleine elektronische apparaten zoals: sensoren, microcontrollers of IoT-modules van stroom kunnen worden voorzien. De module kan daarnaast ook via USB worden gevoed en bevat de nodige beveiligingen tegen verkeerd aansluiten, over-laden en over-ontladen. Hierdoor is het perfect geschikt voor gebruik in ons project om ervoor te zorgen dat onze componenten niet zonder stroom vallen.

## Datacommunicatie

Bij dit project wordt er gebruik gemaakt van het communicatieprotocol "MQTT" oftewel "Message Queuing Telemetry Transport". Via MQTT kunnnen we makkelijk subscriben op de topic van ons apparaat dat via APTerra gegeven wordt(zie tutorial). Ons transportprotocol zal 4G zijn via een ESP32-4G addon module dat een SIM kaart gebruikt voor dit te realiseren. 

### MQTT + AT-Commands

Eerst tests waren uitgevoerd via een mobiele app genaamd "MyMQTT". Dit gaf ons een snelle manier om de connectiviteit tussen een sender en de APTerra server te bekijken zonder enige opstelling of code. MyMQTT werkt door de topic op te geven waar er naar gestuurd moet worden en een text-prompt veld om data in te zetten met een parameter naam. Dit heeft ons dan na een redelijk korte tijd al een eerste resultaat opgeleverd om te beginnen met MQTT.

De 4G module hebben we eerst getest met een Arduino prototype programma dat simpele AT-commands invoerbaar maakt om zo te werken met de module. Mathias had nog een stuk code liggen die hij hiervoor zeer snel kon retrofitten aan de 4G-module voor de ESP. Met een directe connectie van de module aan een laptop hebben we al snel een resultaat kunnen produceren voor onze module.

Onze tweede test die uitgevoerd werd op de 4G-module werd weer gedaan met prototype code maar dan in combinatie met de ESP-controller zelven. Via een aantal Arduino libraries, namelijk: SPI.h, PubSubClient.h en TinyGSMClient.h heeft Mathias een "first prototype" gecreërd dat een connectie vastlegd tussen de ESP-module en de 4G module en dan een MQTT connectie kan leggen tussen de ESP en de APTerra server.

Dus in kort: Success! Na een aantal minieme problemen hebben we succesvol een connectie kunnen maken tussen de 4G-module, de ESP32 en data kunnen doorsturen via MQTT naar de APTerra server!

## Code werking

Full MQTT stack prototype:

```cpp
#define USE_LTE true

#include <SPI.h>
#include <PubSubClient.h>
#include "esp_system.h"

#if USE_LTE

//#include <SoftwareSerial.h>
// ESP32 UART2 default pins: RX=16, TX=17
#define MODEM_RX 16  // Connect to SIM7600 TX
#define MODEM_TX 17  // Connect to SIM7600 RX
//SoftwareSerial SoftSerial;
#define SerialAT Serial2

#define TINY_GSM_MODEM_SIM7600 
#include <TinyGsmClient.h>

const char* apn      = "mworld.be";  
const char* gprsUser = "";
const char* gprsPass = "";
const char* simPIN = "1909";

TinyGsm modem(SerialAT);
TinyGsmClient gsmClient(modem);
PubSubClient client(gsmClient);

#else

#include <WiFi.h>

const char* ssid = "bletchley";
const char* password = "laptop!internet";

WiFiClient espClient;
PubSubClient client(espClient);

#endif

const char* mqtt_server = "bsaffer.iot-ap.be";
const char* topic = "device/8c549e7c-3383-429a-9d09-eb349e80d45d";

#if USE_LTE
void setup_Sim()
{
  SerialAT.begin(115200, SERIAL_8N1, MODEM_RX, MODEM_TX);
  delay(3000);

  Serial.println("Initializing modem...");

  int retries = 5;
  while (retries--) {
    if (modem.testAT()) {
      Serial.println("Modem responded to AT");
      break;
    }
    Serial.println("Modem not responding, retrying...");
    delay(1000);
  }
  
  if (retries < 0) {
    Serial.println("Failed to communicate with modem!");
    while(1);
  }

  // Get modem info
  String modemInfo = modem.getModemInfo();
  Serial.print("Modem Info: ");
  Serial.println(modemInfo);

  if (strlen(simPIN) && modem.getSimStatus() != 3 ) 
  {
    modem.simUnlock(simPIN);
  }

  // Wait for network registration
  Serial.println("Waiting for network...");
  if (!modem.waitForNetwork(60000L)) {
    Serial.println("Network registration failed!");
    return;
  }
  Serial.println("Network registered");

  // Check signal quality
  int csq = modem.getSignalQuality();
  Serial.print("Signal quality: ");
  Serial.println(csq);

  // Connect to GPRS
  Serial.print("Connecting to APN: ");
  Serial.println(apn[0] ? apn : "auto");

  if (!modem.gprsConnect(apn, gprsUser, gprsPass)) {
    Serial.println("Failed to connect to GPRS!");
    return;
  }

  Serial.println("GPRS connected!");
  
  // Verify connection
  if (modem.isGprsConnected()) {
    Serial.println("GPRS status: Connected");
  }
}

#else

void setup_wifi()
{
  delay(10);
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}
#endif

void reconnect() 
{
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");

    if (client.connect("arduinoClient")) {
      Serial.println("connected");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      delay(5000);
    }
  }
}

void publishMessage()
{
  String val = String(temperatureRead());
  val += ";";
  val += String(ESP.getCpuFreqMHz());
  val += ";";
  val += String(ESP.getFreeHeap());
  val += ";";
  val += String(random(-500, 500));
  val += ";";
  val += String(69);
  val += ";";
  Serial.print("publishing: ");
  Serial.println(val);
  client.publish(topic, val.c_str());
}

void setup()
{
  Serial.begin(115200);
  delay(1000);
  
  Serial.println("Starting...");
  
  client.setServer(mqtt_server, 1883);

#if USE_LTE
  setup_Sim();
#else
  setup_wifi();
#endif

  delay(1500);
}

void loop()
{
#if USE_LTE
  if (!modem.isGprsConnected()) {
    Serial.println("GPRS dropped — reconnecting...");
    setup_Sim();
  }
#else
  if (WiFi.status() != WL_CONNECTED) {
    Serial.println("WiFi dropped — reconnecting...");
    setup_wifi();
  }
#endif
  
  if (!client.connected()) {
    reconnect();
  }

  publishMessage();
  client.loop();
  
  delay(5000);
}
```

## PCB Design

<INSERT 3D RENDERS OF PCB BOARDS>

Voor dit project is er gekozen om 2 PCB's te maken om zo beter onderscheid te creëren tussen componenten die in de gevaarlijke zone terecht komen en degene die er buiten opereren. De "Master" PCB heeft als taak data opvragen van de Slave PCB, deze met stroom voeden en deze, via een 4G connectie, naar het APTerra dashboard te sturen. De Slave PCB heeft als taak de inkomende stroom te verdelen over de componenten en de mogelijkheid bieden om data terug te sturen naar de master PCB. 

De Slave PCB heeft een reeks connector pins om makkelijk uit te bereiden moesten er wensen zijn voor nog meer sensoren te plaatsen.

De Master PCH beschikt over een waveshare solar-power-manager module die een Li-ion batterij oplaad om ons systeem constant van stroom te voorzien. Hierbovenop is er ook een RS-248 bus controller aanwezig zich voordoet als de driver voor de rs-248 bus. Deze chip bezit ook de mogelijkheid voor full-duplex als dit ooit in de toekomst gewild is maar dient momenteel eerder als een "compatiblity" chip tussen onze ESP32 en het rs-485 protocol.

## Communicatie 

Serial1 kan je niet fatsoenlijk aanspreken en Serial2 heeft geen pre-assigned pinnen waardoor we manueel de pinnen in moeten stellen voor Serial2 om een MQTT connectie op te zetten.

<!-- 
De communicatie tussen de componenten en de main controller zal gebeuren via rs-485 mdobus. Dit laat ons toe een simpele fysieke structuur op te bouwen om data terug te sturen naar de controller.

Als de data ge collect is zal deze doorgestuurd worden via 4G naar APTerra via MQTT -->

De communicatie tussen onze componenten zal gebeuren via 2PCB's. Via een Slave & Master principe sturen we onze data naar de ESP32 en zo, met behulp van een 4G module, naar de APTerra server over het MQTT protocol.

De Slave PCB in ons project zal alle componenten van stroom voorzien en data verzamelen via de rs-485 modbus van de componenten. rs-485 modbubs werkt op een soort client-server principe waarbij we de master PCB een request kunnen laten sturen naar de clients voor data op te halen. De connectie tussen ons master PCB board en de slave zal gedaan worden via een RJ45 connector. We hebben RJ45 gekozen omdat deze kabels makkelijker te maken zijn & de mogelijkheid hebben om UV bestendig te zijn bovenop een grotere hoeveelheid datalijnen om dingen zoals stroom, data of uitberijdingsmogelijkheden over te brengen.

rs-485 modbus gebruikt 2 datalijnen omdat data doorgestuurd wordt in de vorm van een differentiaal tussen 2 geleiders. Dit maakt het systeem bestendig tegen externe ruis en effectief half-duplex. 

![Communicatie_Sketch](Communicatie_Sketch.png)

![Dataflow Diagram](<Schermafbeelding 2025-12-05 112910.png>)
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

Na aanvraag is er ook recentelijk een documentatie pagina voor APTerra geschreven: https://docs.apterra.be/#/AP-terra/manuals/sending-data

## Tegengekomen Problemen

De meeste sensoren die verkrijgbaar zijn & voldoen aan de lijst van vereisten worden meestal voorafgegaan door een quote aan te vragen bij het bedrijf. Dit is een zeer, zeer lang en uitputtend process van back & forth wat veel tijd in beslag neemt. Bij onze eerste sensor was de tijd om een quote te krijgen 3+ weken en een prijs van 14999$. 

Een aantal van de bedrijven waaraan een quote gevraagd werd hebben ook simpelweg geen antwoord gegeven na meerdere malen proberen in contact te komen wat voor frustraties kan zorgen. Samen met het internationale team hebben wij mails gestuurd naar bedrijven, instituten en ondernemeningen die bezig zijn met biogas & CH4 metingen zonder enig success in een CH4-sensor te vinden die betaalbaar genoeg is om in ons project te gebruiken.

Na een aantal weken wouden we opnieuw de APTerra connectie testen met 4G, Deze keer met een werkend Solarwave power management sensor. Toen we deze connecteerden spong er een flikkerend rood light aan op de ESP32 wat we dachten dat een warning was. Na onderzoek te doen betekent deze flikkerende LED dat de ESP32 geen geconnecteerde batterij detecteert (wat normaal was.). Uitijndelijk zijn we erachter gekomen dat deze rode LED normaal was bij het uitvoeren van de opstelling en hadden wij hier onze tijd aan verspilt.

Na een lange tijd testen waarom de wekrende code niet meer werkt voor communicatie te leggen met APTerra zijn we erachter gekomen dat, bij het krijgen van onze simkaart, de SIM nog nooit geactiveerd was wat betekent dat deze ook nooit gebruikt kan worden om data door te sturen. Na snel rond te vragen hoe andere hun SIM ge-activeerd hebben, hebben we al snel onze SIM werkende kunnen krijgen en verdergaan met de testopstelling.


## Display APterra

![APTerra dashboard display](<Schermafbeelding 2025-11-14 142013.png>)

# Bibliografie

Firebeetle shield footprint SnapEDA: https://www.snapeda.com/parts/DFR0654/DFRobot/view-part/ 

SN65HVD3080EDGSR rs485 ic footprint: https://www.snapeda.com/parts/SN65HVD3080EDGSR/Texas%20Instruments/view-part/?ref=search&t=SN65HVD308&ab_test_case=b 

Wurth 634108185421 RJ45 w/o transformer: https://www.digikey.sg/en/products/detail/würth-elektronik/634108185421/8021671 

ATO Methane sensor: https://www.ato.com/methane-sensor

Evikon Methane sensor: https://www.evikon.eu/competences-comp-1043/gas-detection-comp-1046/methane-comp-1065/methane-detector-p-196 

Ultrasonic level sensor directIndustry: https://www.directindustry.com/prod/siap-micros/product-158525-1615688.html

modbus level sensoren directIndustry: https://www.directindustry.com/industrial-manufacturer/modbus-level-sensor-142309.html

Evikon CO2 meter: https://www.evikon.eu/carbon-dioxide-transmitter-p-6c2a87c9

Vaisala multigas probe: https://docs.vaisala.com/v/u/B212246EN-C/en-US

directIndustry water level sensor LNU: https://www.directindustry.com/prod/ijinus/product-236533-2391191.html

directIndustry water level sensor ENELSAN: https://www.directindustry.com/prod/enelsan-endustriyel-elektronik-sanayi-as/product-224643-2651324.html

AINSTER rs-485 liquid mass flow meter: https://www.aistermeter.com/flowmeter/modbus-rs485-liquid-mass-flow-meter-coriolis-mass-flow-meters.html

Vaisala multigas probe alternative: https://www.alibaba.com/product-detail/Vaisala-Methane-and-Carbon-Dioxide-Multigas_1600920227298.html

ELSCOLAB multigas probe: https://elscolab.com/en-nl/products/biogas-analyser

VEGAPULS radar sensor: https://www.vega.com/nl-be/producten/product-catalog/continue-niveaumeting/radar/vegapuls-c-11

SenseCap CO2/Temp/Humidity sensorkit: https://th.cytron.io/p-sensecap-co2-temperature-and-humidity-sensor-with-rs485-and-sdi-12?srsltid=AfmBOopzfb6zNjqf_jQQtVkN4-IG3tCATVkgSteg4vAKojDfB8uGUJBJ 

cubic 100% vol methane sensor: https://www.co2meter.com/products/cubic-sjh-100-100-methane-sensor?variant=42393216876742

Infrasensing CH4 100%LEL module: https://infrasensing.com/sensors/sensor_gas_ch4.asp

shoptransmitter GFG IR29B gas detector: https://shoptransmitter.com/gfg-ir29-b-gas-detector-methane-ch4-0-100-lel-w-o-display-modbus-ip67/ 

KMC Q8-CH4 100LEL gas sensor: https://www.kmccontrols.com/product/aci-methanecatalytic-bead-0-100/

Inter automatika IR22 CO2 modbus sensor: https://www.interautomatika.eu/en/ir22-d-transmitter-w-o-sensor-with-display-rs485-modbus.html

TRU Components PT100: https://www.conrad.com/en/p/tru-components-pt100-temperature-sensor-100-up-to-200-c-open-end-cable-3-m-2444894.html?srsltid=AfmBOopDmYa95LGftWY_8OukjtX60WOtgFWoSMhu7Jpfbl8AeRAXSgLJ 

Ultrasonic water level sensor moduel: https://mikroelectron.com/product/waterproof-ultrasonic-water-level-sensor-module-for-tank-rs485-output-22cm-to-600cm-range?srsltid=AfmBOoq1e2NpkCom4aG6UIuCEs50eKQ6vHQQIBbX_vbDckYM-zPKQukN

Jayeshtraders CH4 100% Vol sensor: https://jayeshtraders.com/product/airatom-ch4-0-100vol-electrochemical-sensor/

RKI Instruments M2A-XL Stand Alone transmitter CH4 sensor: https://www.rkiinstruments.com/product/m2a-xl-gas-detector/

S+S regeltechnik Pressure transmitter: https://www.spluss.de/en/products/pressure-measuring-transducer-premasgard-shd-modbus-2-5-lcd-0-2-5-bar-1301-2214-5530-221-p22881?_pos=1&_fid=6c2a87c96&_ss=c 

RKI Instrumtn IJSTECH IR CH4 100% VOL sensor: https://www.jjstech.com/65-2658xl-ch4.html

dual gas cubic HC/CO2 sensor: https://www.processsensing.com/nl-nl/products/dual-Gas_HC_CO2_infrared_sensors.htm 

FIREBEETLE BOARD: https://benl.rs-online.com/web/p/arduino-compatible-boards-kits/2473219?cm_mmc=BE-PLA-DS3A-_-google-_-CSS_BENL_NL_Pmax_1224-_--_-2473219&matchtype=&&gclsrc=aw.ds&gad_source=1&gad_campaignid=22040006570&gclid=CjwKCAiAuIDJBhBoEiwAxhgyFuIoyhnAeTN-a6PcChIT0EpC9Am6lveoA97EagpxEp1wtjasvj7d2hoC6_gQAvD_BwE

Waveshare power management module: https://www.amazon.com.be/-/en/Waveshare-Management-Protection-Controller-Environmental/dp/B094FWZVFH/ref=sr_1_2?adgrpid=159150164620&dib=eyJ2IjoiMSJ9

gekozen PT100 Temp probe: https://controlbyweb.com/accessories/temperature-probe/ 

Biogas INAGRO onderzoek duurzame biologie collectie: https://inagro.be/projecten/biogas-mambo

BRIGHT renewables Biogas inquery: https://www.bright-renewables.com/solutions/renewable-gas/biogas-upgrading/?utm_source=google&utm_medium=cpc&utm_campaign=882311895&utm_adgroup=52715477028&gad_source=1&gad_campaignid=882311895&gclid=CjwKCAjw6P3GBhBVEiwAJPjmLmXiwVjFxpEeFP-EFpDfPxuPE_IymzWpHURYbJ-x1RbQ9zrvBeD54RoCJesQAvD_BwE

smartgas EU: https://www.smartgas.eu/en/gases/biogas-sensors

SIM7600G-H module infocheet: https://wiki.dfrobot.com/SKU_TEL0162_SIM7600G_H_CAT4_4G_Communication_Module