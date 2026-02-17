# Biogas Digester Data Extraction

> Documentation and implementation guide for deploying an array of sensors inside a biogas digester to collect and transmit real-time environmental data. Developed in collaboration with **Students for Energy in Africa**, **Ardhi University** (Tanzania), and **Vlirous**.

---

##  Project Overview

This project tackles a real-world energy challenge in Sub-Saharan Africa: monitoring the internal conditions of biogas digesters to optimize gas production and ensure safe operation. By deploying a network of embedded sensors inside the digester, the system continuously gathers critical environmental data and transmits it to a central backend for processing and visualization.

The project was developed as part of an international collaboration between AP University College (Belgium), Ardhi University (Tanzania), and the NGO Students for Energy in Africa.

---

##  What It Measures

The sensor array monitors the internal conditions of the biogas digester, including:

-  **Temperature** 
-  **Humidity** 
-  **Gas concentration** 
-  **Additional environmental parameters** 

---

## My Contributions

### 1. Sensor Hardware Analysis
This means selecting appropriate sensors for the harsh conditions inside a biogas digester(looking at aspects like corrosion, explosion proofing, pressure and temperature ratings).

### 2. Firmware & Embedded Code
Wrote and tested the embedded firmware responsible for reading sensor data, handling I2C/SPI communication between the microcontroller and sensor modules, and preparing data payloads for transmission over MQTT.

### 3. Documentation & Diagrams
Authored the full technical documentation for the project using **Docsify**, a lightweight docs-as-code framework. This includes communication architecture sketches, sensor breakout schematics, and setup guides — ensuring the project can be continued and extended by future contributors in both Belgium and Tanzania.

---

##  Tech Stack

| Layer | Technology |
|---|---|
| Communication Protocol | MQTT |
| Backend Deployment | Docker / Docker Compose |
| Docs Framework | Docsify |
| CI/CD | GitLab CI (`gitlab-ci.yml`) |
| Diagrams & Schematics | PNG-based architecture diagrams |

---

##  Repository Structure

```
Biogas-digester-data-extraction/
├── docs.md                        # Main project documentation
├── index.html                     # Docsify docs entry point
├── _sidebar.md                    # Docsify navigation sidebar
├── docker-compose.yml             # Backend service orchestration
├── caddy/conf/                    # Caddy reverse proxy config
├── .gitlab-ci.yml                 # CI/CD pipeline definition
├── BiogasSensorBreakout.png       # Sensor breakout board diagram
├── Slave_Breakout_schem.png       # Slave node schematic
├── Communicatie_Sketch.png        # System communication architecture
└── [additional diagrams & assets]
```

---

##  Running the Docs Locally

The documentation is built with [Docsify](https://docsify.js.org/) and can be served locally with a simple static server:

```bash
# Using Node.js
npx serve .

# Or using Python
python -m http.server 3000
```

Then open `http://localhost:3000` in your browser.

---

##  International Collaboration

This project was developed in partnership with:

| Partner | Role |
|---|---|
| **AP University College** (Belgium) | Engineering & development |
| **Ardhi University** (Tanzania) | Field deployment & local expertise |
| **Students for Energy in Africa** | NGO coordination & impact direction |
| **Vlirous** | Project backing & support |

---

##  Author

**Berre Neyrinck**
Contributor — Hardware, Firmware, Backend & Documentation
[GitHub Profile](https://github.com/BerreNeyrinck)
