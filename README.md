Modbus • OPC UA • CAN Bus • DNP3 • BACnet • PROFIBUS • EtherCAT

<img width="1248" height="832" alt="OIG2" src="https://github.com/user-attachments/assets/ba4862ab-7675-4333-bcb2-5dddd0fba30d" />


# <span style="color:#00ff00"> INDUSTRIAL PROTOCOLS MASTERY GUIDE </span>

## <span style="color:#00ff41">Modbus • OPC UA • CAN Bus • DNP3 • BACnet • PROFIBUS • EtherCAT</span>

### <span style="color:#00ff00"> ARCHITECTURE • CONFIGURATION • SECURITY • AUDIT • APPLICATIONS </span>

**Auteur : `hackers_tchad`**  
**Date de publication : `2026`**  
**Classification : Référence avancée - Industrial Cybersecurity & IIoT**

[![Matrix](https://img.shields.io/badge/MODE-GREEN_MATRIX-00ff00?style=for-the-badge&logo=matrix&logoColor=green)](https://matrix.org)
[![Industrial](https://img.shields.io/badge/INDUSTRIAL-PROTOCOLS-ff6600?style=for-the-badge)](https://)
[![Cybersecurity](https://img.shields.io/badge/OT-CYBERSECURITY-00ff00?style=for-the-badge)](https://)
[![Hackers_Tchad](https://img.shields.io/badge/AUTHOR-hackers__tchad-000000?style=for-the-badge&labelColor=00ff00)](https://)

</div>

---

##  Table des matières

1. [Introduction générale](#introduction-générale)
2. [Modbus](#modbus)
   - 2.1 [Définition et historique](#modbus-définition-et-historique)
   - 2.2 [Architecture](#modbus-architecture)
   - 2.3 [Modes de transmission](#modbus-modes-de-transmission)
   - 2.4 [Fonction codes](#modbus-fonction-codes)
   - 2.5 [Configuration détaillée](#modbus-configuration-détaillée)
   - 2.6 [Commandes de vérification](#modbus-commandes-de-vérification)
   - 2.7 [Applications](#modbus-applications)
   - 2.8 [Sécurité et vulnérabilités](#modbus-sécurité)
3. [OPC UA](#opc-ua)
   - 3.1 [Définition et historique](#opc-ua-définition-et-historique)
   - 3.2 [Architecture](#opc-ua-architecture)
   - 3.3 [Modèle d'information](#opc-ua-modèle-dinformation)
   - 3.4 [Configuration serveur et client](#opc-ua-configuration)
   - 3.5 [Commandes de vérification](#opc-ua-commandes-de-vérification)
   - 3.6 [Applications](#opc-ua-applications)
   - 3.7 [Sécurité](#opc-ua-sécurité)
4. [CAN Bus](#can-bus)
   - 4.1 [Définition et historique](#can-bus-définition-et-historique)
   - 4.2 [Architecture physique](#can-bus-architecture-physique)
   - 4.3 [Protocole de communication](#can-bus-protocole)
   - 4.4 [Configuration](#can-bus-configuration)
   - 4.5 [Commandes de vérification](#can-bus-commandes-de-vérification)
   - 4.6 [Applications](#can-bus-applications)
   - 4.7 [Sécurité](#can-bus-sécurité)
5. [DNP3](#dnp3)
   - 5.1 [Définition et historique](#dnp3-définition-et-historique)
   - 5.2 [Architecture](#dnp3-architecture)
   - 5.3 [Configuration](#dnp3-configuration)
   - 5.4 [Commandes de vérification](#dnp3-commandes-de-vérification)
   - 5.5 [Applications](#dnp3-applications)
   - 5.6 [Sécurité](#dnp3-sécurité)
6. [BACnet](#bacnet)
   - 6.1 [Définition et historique](#bacnet-définition-et-historique)
   - 6.2 [Architecture](#bacnet-architecture)
   - 6.3 [Configuration](#bacnet-configuration)
   - 6.4 [Commandes de vérification](#bacnet-commandes-de-vérification)
   - 6.5 [Applications](#bacnet-applications)
   - 6.6 [Sécurité](#bacnet-sécurité)
7. [PROFIBUS](#profibus)
   - 7.1 [Définition et historique](#profibus-définition-et-historique)
   - 7.2 [Architecture](#profibus-architecture)
   - 7.3 [Configuration](#profibus-configuration)
   - 7.4 [Commandes de vérification](#profibus-commandes-de-vérification)
   - 7.5 [Applications](#profibus-applications)
   - 7.6 [Sécurité](#profibus-sécurité)
8. [EtherCAT](#ethercat)
   - 8.1 [Définition et historique](#ethercat-définition-et-historique)
   - 8.2 [Architecture](#ethercat-architecture)
   - 8.3 [Configuration](#ethercat-configuration)
   - 8.4 [Commandes de vérification](#ethercat-commandes-de-vérification)
   - 8.5 [Applications](#ethercat-applications)
   - 8.6 [Sécurité](#ethercat-sécurité)
9. [Comparatif global](#comparatif-global)
10. [Matrice de sécurité OT/IT](#matrice-de-sécurité-otit)
11. [Outils d'analyse et de test](#outils-danalyse-et-de-test)
12. [Ressources, livres et liens](#ressources-livres-et-liens)
13. [Glossaire](#glossaire)
14. [Licence et crédits](#licence-et-crédits)

---

## Introduction générale

Les protocoles industriels constituent le socle de communication de l'Industrie 3.0, 4.0 et de l'IIoT (Industrial Internet of Things). Ils permettent l'échange de données entre capteurs, actionneurs, automates (PLC), systèmes de supervision (SCADA/HMI), systèmes de gestion d'énergie (EMS/BMS) et les clouds industriels.

Contrairement aux réseaux informatiques classiques (TCP/IP, HTTP), les protocoles industriels doivent garantir :

- **Déterminisme temporel** : respect strict des contraintes temps réel.
- **Résilience** : fonctionnement dans des environnements hostiles (bruit électromagnétique, température, vibrations).
- **Interopérabilité** : communication entre équipements de fabricants différents.
- **Sécurité** : protection contre les cyberattaques ciblant les infrastructures critiques (ICS/SCADA).
- **Évolutivité** : passage de quelques nœuds à plusieurs milliers sur un même réseau.

Ce guide explore en profondeur sept protocoles majeurs :

| Protocole | Domaine principal | Couche physique | Déterminisme | Sécurité native |
|-----------|-------------------|-----------------|--------------|-----------------|
| Modbus | Automatisme, énergie | RS-232/RS-485, Ethernet | Moyen | Faible |
| OPC UA | Interopérabilité IT/OT | Ethernet (TCP/IP) | Fort | Très forte |
| CAN Bus | Automobile, embarqué, industrie | Paire torsadée différentielle | Fort | Faible |
| DNP3 | Utilities, énergie, eau | Série, IP | Fort | Moyenne (DNP3-SA) |
| BACnet | Bâtiment intelligent (BMS) | MS/TP, IP, BACnet/SC | Moyen | Moyenne |
| PROFIBUS | Automatisme manufacturier | RS-485 | Très fort | Faible/Moyenne |
| EtherCAT | Motion control, robotique | Ethernet | Très fort | Moyenne (Safety over EtherCAT) |

Chaque section est conçue pour servir de référence avancée : historique, architecture, configuration, commandes de vérification, applications industrielles, sécurité offensive et défensive, ressources bibliographiques et liens.

---

## Modbus

### Modbus : Définition et historique

Modbus est un protocole de communication série créé en **1979** par **Modicon** (aujourd'hui Schneider Electric) pour connecter des automates programmables (PLC) avec des équipements périphériques. Il est devenu un standard ouvert et largement adopté dans l'industrie.

**Créateur** : Modicon (Gould Modicon), racheté par Schneider Electric.  
**Première version** : Modbus RTU en 1979.  
**Standardisation** : Géré depuis 2004 par **Modbus-IDA** (Interface for Distributed Automation), désormais **Modbus Organization**.  
**Site officiel** : https://modbus.org

Modbus est un protocole **maître/esclave** (ou client/serveur dans sa version TCP/IP) simple, robuste et interopérable. Il repose sur un modèle de requête/réponse où le maître interroge les esclaves pour lire ou écrire des registres.

### Modbus : Architecture

L'architecture Modbus est centralisée autour d'un maître unique qui contrôle les échanges. Les esclaves ne communiquent jamais spontanément.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           MODBUS ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────┐         Request (Function Code + Address + Data)         │
│   │   MASTER     │ ───────────────────────────────────────────────────────►  │
│   │  (Client)    │                                                          │
│   │   HMI/SCADA  │ ◄──────────────────────────────────────────────────────  │
│   └──────────────┘         Response (Data or Exception Code)                │
│          │                                                                  │
│          │                                                                  │
│   ═══════╪══════════════════════════════════════════════════════════════    │
│          │                                                                  │
│   ┌──────┴──────┐   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐    │
│   │  SLAVE 01   │   │  SLAVE 02   │   │  SLAVE 03   │   │  SLAVE N    │    │
│   │  PLC        │   │  Sensor     │   │  VFD        │   │  Meter      │    │
│   │  Address=1  │   │  Address=2  │   │  Address=3  │   │  Address=N  │    │
│   └─────────────┘   └─────────────┘   └─────────────┘   └─────────────┘    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Modèle de données Modbus** :

| Type de données | Nom objet | Plage d'adresses | Accès | Taille |
|-----------------|-----------|------------------|-------|--------|
| Discrete Inputs | Input Status | 10001-19999 | Lecture seule | 1 bit |
| Coils | Coil Status | 00001-09999 | Lecture/Écriture | 1 bit |
| Input Registers | Input Register | 30001-39999 | Lecture seule | 16 bits |
| Holding Registers | Holding Register | 40001-49999 | Lecture/Écriture | 16 bits |

**Adressage moderne (Modbus PLC)** :  
- `0x` pour Coils  
- `1x` pour Discrete Inputs  
- `3x` pour Input Registers  
- `4x` pour Holding Registers  

### Modbus : Modes de transmission

Modbus existe en trois variantes principales :

#### Modbus RTU (Remote Terminal Unit)
- **Support** : RS-232 ou RS-485.
- **Encodage** : binaire compact, CRC-16 pour l'intégrité.
- **Trame** : Adresse esclave (1 octet) + Function Code (1 octet) + Données (N octets) + CRC (2 octets).
- **Avantage** : efficace, faible overhead.
- **Inconvénient** : sensible au timing (silence inter-caractères ≥ 3,5 caractères).

#### Modbus ASCII
- **Support** : RS-232 ou RS-485.
- **Encodage** : caractères ASCII, LRC pour l'intégrité.
- **Trame** : `:` + Adresse hex ASCII (2) + Function hex ASCII (2) + Données + LRC + CR LF.
- **Avantage** : lisible humainement.
- **Inconvénient** : moins efficace que RTU.

#### Modbus TCP/IP
- **Support** : Ethernet.
- **Encapsulation** : MBAP Header (7 octets) + PDU Modbus.
- **Port par défaut** : **502/tcp**.
- **Avantage** : routable, intégration IT facile.
- **Inconvénient** : pas de chiffrement natif, authentification absente.

### Modbus : Fonction codes

Les codes fonction Modbus définissent l'opération demandée :

| Code | Fonction | Description |
|------|----------|-------------|
| 01 | Read Coils | Lire 1 à 2000 sorties binaires |
| 02 | Read Discrete Inputs | Lire 1 à 2000 entrées binaires |
| 03 | Read Holding Registers | Lire 1 à 125 registres 16 bits |
| 04 | Read Input Registers | Lire 1 à 125 registres d'entrée |
| 05 | Write Single Coil | Écrire une sortie binaire |
| 06 | Write Single Register | Écrire un registre 16 bits |
| 08 | Diagnostics | Tests de diagnostic (loopback) |
| 15 | Write Multiple Coils | Écrire 1 à 1968 coils |
| 16 | Write Multiple Registers | Écrire 1 à 123 registres |
| 17 | Report Slave ID | Identification de l'esclave |
| 22 | Mask Write Register | Modification masquée |
| 23 | Read/Write Multiple Registers | Lecture et écriture combinées |

### Modbus : Configuration détaillée

#### Exemple de configuration Modbus RTU

Pour un maître Modbus RTU sur port série RS-485 :

```bash
# Paramètres de ligne série typiques
Port        : /dev/ttyUSB0
Baud rate   : 9600 bps
Data bits   : 8
Parity      : None
Stop bits   : 1
Timeout     : 1 second
Mode        : RTU
```

Avec `pymodbus` (Python) :

```python
from pymodbus.client import ModbusSerialClient

client = ModbusSerialClient(
    port='/dev/ttyUSB0',
    baudrate=9600,
    bytesize=8,
    parity='N',
    stopbits=1,
    method='rtu',
    timeout=1
)

client.connect()
result = client.read_holding_registers(address=0, count=10, slave=1)
if not result.isError():
    print(result.registers)
client.close()
```

#### Exemple de configuration Modbus TCP

```python
from pymodbus.client import ModbusTcpClient

client = ModbusTcpClient(host='192.168.1.100', port=502, timeout=5)
client.connect()
result = client.read_holding_registers(address=0, count=10, slave=1)
print(result.registers)
client.close()
```

#### Configuration d'un esclave Modbus (serveur)

Avec `pymodbus` :

```python
from pymodbus.server import StartTcpServer
from pymodbus.datastore import ModbusSequentialDataBlock
from pymodbus.datastore import ModbusSlaveContext, ModbusServerContext

store = ModbusSlaveContext(
    di=ModbusSequentialDataBlock(0, [True]*100),
    co=ModbusSequentialDataBlock(0, [False]*100),
    hr=ModbusSequentialDataBlock(0, [0]*100),
    ir=ModbusSequentialDataBlock(0, [0]*100)
)
context = ModbusServerContext(slaves=store, single=True)
StartTcpServer(context=context, address=("0.0.0.0", 502))
```

### Modbus : Commandes de vérification

#### Scanner le réseau Modbus TCP

```bash
# Découverte des hôtes Modbus avec nmap
nmap -p 502 --open 192.168.1.0/24

# Script NSE Modbus pour récupérer l'UID
nmap -p 502 --script modbus-discover.nse 192.168.1.100
```

#### Test avec mbtget

```bash
# Lire un holding register
mbtget -r3 -a 1 -n 10 192.168.1.100

# Écrire un registre
mbtget -r6 -a 1 -v 1234 192.168.1.100
```

#### Test avec modpoll

```bash
# Lire 10 holding registers sur l'esclave 1
modpoll -m tcp -t4 -r 1 -c 10 192.168.1.100

# Lire des coils
modpoll -m tcp -t0 -r 1 -c 8 192.168.1.100
```

#### Test avec Python/pymodbus CLI

```bash
pymodbus.console tcp --host 192.168.1.100 --port 502
client.read_holding_registers address=0 count=10 slave=1
```

### Modbus : Applications

Modbus est omniprésent dans :

- **Automatisme industriel** : PLC Schneider, Siemens, Rockwell, Mitsubishi.
- **Compteurs d'énergie** : Energy meters, analyseurs de réseau.
- **Variateurs de vitesse** : VFD (Variable Frequency Drives).
- **Supervision** : SCADA (Wonderware, Ignition, WinCC).
- **Bâtiment intelligent** : intégration avec des passerelles BACnet/BMS.
- **Renouvelables** : onduleurs photovoltaïques, éoliennes.
- **Transport** : signalisation ferroviaire, gestion d'éclairage.

### Modbus : Sécurité

**Vulnérabilités principales** :

- Pas d'authentification.
- Pas de chiffrement natif.
- Pas de contrôle d'intégrité au-delà du CRC.
- Pas de protection contre la rejeu.
- Exception codes révélateurs (`ILLEGAL FUNCTION`, `ILLEGAL DATA ADDRESS`).
- Scanning facile sur le port 502.

**Attaques typiques** :

- **Man-in-the-middle** : interception et modification des trames.
- **Rejeu d'ordres de commande** : écriture répétée de coils.
- **Fuzzing de function codes** : découverte de fonctions non documentées.
- **DoS** : saturation du port TCP/502.

**Contre-mesures** :

- Isoler Modbus TCP dans un VLAN OT dédié.
- Utiliser des passerelles sécurisées (Modbus Security/TLS).
- Déployer des firewalls industriels avec deep packet inspection (DPI).
- Surveiller les changements anormaux de registres.
- Utiliser Modbus/TCP Security (TLS 1.2+ avec certificats X.509).
- Restreindre les adresses IP autorisées par ACL.

---

## OPC UA

### OPC UA : Définition et historique

**OPC UA** (Open Platform Communications Unified Architecture) est un protocole de communication machine-to-machine (M2M) pour l'industrie. Il a été développé par la **OPC Foundation** pour remplacer le standard OPC Classic (DA, HDA, A&E) basé sur Microsoft DCOM.

**Créateur** : OPC Foundation (fondée en 1996).  
**Publication OPC UA** : 2006.  
**Site officiel** : https://opcfoundation.org

OPC UA est conçu pour l'interopérabilité verticale et horizontale dans l'industrie. Il fournit un modèle d'information unifié, des services de découverte, de lecture/écriture, d'abonnement, de méthodes, d'appels distants, ainsi qu'un modèle de sécurité robuste.

### OPC UA : Architecture

L'architecture OPC UA est multicouche :

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                         OPC UA ARCHITECTURE                                  │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐    │
│   │                         APPLICATION LAYER                          │    │
│   │  Alarms & Conditions | Historical Access | Programs | Methods | Data │    │
│   └─────────────────────────────────────────────────────────────────────┘    │
│   ┌─────────────────────────────────────────────────────────────────────┐    │
│   │                        OPC UA INFORMATION MODEL                      │    │
│   │   Nodes : Objects | Variables | Methods | Views | ObjectTypes       │    │
│   │   References : HasComponent | HasProperty | Organizes | HasTypeDef  │    │
│   └─────────────────────────────────────────────────────────────────────┘    │
│   ┌─────────────────────────────────────────────────────────────────────┐    │
│   │                         OPC UA SERVICES                            │    │
│   │  Discovery | Session | NodeManagement | View | Attribute | Method   │    │
│   │  MonitoredItems | Subscription | Query | Condition                  │    │
│   └─────────────────────────────────────────────────────────────────────┘    │
│   ┌─────────────────────────────────────────────────────────────────────┐    │
│   │                          TRANSPORT LAYER                           │    │
│   │   OPC UA TCP (4840) | HTTPS (443) | MQTT | AMQP | PubSub (UDP)     │    │
│   └─────────────────────────────────────────────────────────────────────┘    │
│   ┌─────────────────────────────────────────────────────────────────────┐    │
│   │                          SECURITY LAYER                            │    │
│   │   X.509 Certificates | User Tokens | Encryption | Sign & Encrypt    │    │
│   └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

**Ports OPC UA** :

| Service | Port par défaut | Protocole |
|---------|-----------------|-----------|
| OPC UA Discovery Server | 4840/tcp | OPC UA TCP |
| OPC UA Server | 4840/tcp (ou autre) | OPC UA TCP |
| OPC UA HTTPS | 443/tcp | HTTPS |
| OPC UA PubSub | 4840/udp (multicast) | UDP |

### OPC UA : Modèle d'information

Le modèle d'information OPC UA repose sur un graphe de **nœuds** reliés par des **références**.

**Types de nœuds** :

| Type de nœud | Rôle |
|--------------|------|
| Object | Regroupement logique (ex. : DeviceSet) |
| Variable | Donnée mesurable/écrivable (ex. : Temperature) |
| Method | Fonction exécutable distante |
| ObjectType | Modèle de classe (ex. : TemperatureSensorType) |
| VariableType | Type de variable |
| DataType | Type de données (Int32, String, Structure) |
| ReferenceType | Type de relation entre nœuds |
| View | Sous-ensemble filtré de l'adressage |

**Références essentielles** :

- `Organizes` : relation hiérarchique.
- `HasComponent` : un objet contient un composant.
- `HasProperty` : un objet possède une propriété.
- `HasTypeDefinition` : un nœud est instance d'un type.

### OPC UA : Configuration serveur et client

#### Serveur OPC UA avec Python (freeopcua)

```python
from opcua import Server
from datetime import datetime

server = Server()
server.set_endpoint("opc.tcp://0.0.0.0:4840/freeopcua/server/")

# Namespace personnalisé
uri = "http://hackers_tchad.opcua.example"
idx = server.register_namespace(uri)

# Objet racine
objects = server.get_objects_node()
myobj = objects.add_object(idx, "MyObject")
myvar = myobj.add_variable(idx, "MyVariable", 6.7)
myvar.set_writable()

# Démarrer le serveur
server.start()
print("Serveur OPC UA démarré sur opc.tcp://0.0.0.0:4840")

try:
    while True:
        myvar.set_value(datetime.now().second)
finally:
    server.stop()
```

#### Client OPC UA avec Python

```python
from opcua import Client

client = Client("opc.tcp://192.168.1.100:4840/freeopcua/server/")
client.connect()

try:
    root = client.get_root_node()
    print("Root node:", root)
    
    # Parcourir l'arborescence
    objects = client.get_objects_node()
    children = objects.get_children()
    for child in children:
        print(child.get_browse_name())
    
    # Lire une variable
    var = client.get_node("ns=2;i=2")
    print("Valeur:", var.get_value())
    
    # Écrire une variable
    var.set_value(42)
finally:
    client.disconnect()
```

#### Configuration de la sécurité OPC UA

```python
from opcua import Client

client = Client("opc.tcp://192.168.1.100:4840")
client.set_user("operator")
client.set_password("SecurePass123!")
client.set_security_string("Basic256Sha256,SignAndEncrypt,cert.der,pkey.pem")
client.connect()
```

### OPC UA : Commandes de vérification

#### Découverte avec nmap

```bash
nmap -p 4840 --open 192.168.1.0/24
nmap -p 4840 --script opc-ua-discover 192.168.1.100
```

#### Test avec UaExpert (Unified Automation)

```bash
# UaExpert est un client OPC UA graphique
uaexpert &
```

#### Test avec command-line OPC UA

```bash
# Utilisation de opcua-client (freeopcua)
opcua-client opc.tcp://192.168.1.100:4840

# Lister les nœuds
ls
# Lire un nœud
read ns=2;i=2
# Écrire un nœud
write ns=2;i=2 1234
```

### OPC UA : Applications

- **Industrie 4.0** : plateformes de collecte et d'analyse de données.
- **Digital Twin** : jumeau numérique d'actifs industriels.
- **Cloud manufacturing** : connexion sécurisée des usines au cloud.
- **Automobile** : ligne d'assemblage connectée.
- **Pharmaceutique** : traçabilité batch (ISA-95, OPC UA pour Pharma).
- **Énergie** : gestion de réseaux électriques intelligents.
- **Smart Building** : intégration avec BACnet via OPC UA.

### OPC UA : Sécurité

**Forces** :

- Chiffrement symétrique et asymétrique.
- Certificats X.509 pour authentification des applications.
- Tokens utilisateur (anonyme, nom d'utilisateur/mot de passe, certificat).
- Modes de sécurité : None, Sign, SignAndEncrypt.
- Profils de sécurité : Basic128Rsa15, Basic256, Basic256Sha256, Aes128Sha256RsaOaep.

**Vulnérabilités** :

- Mauvaise gestion des certificats (auto-signés acceptés sans vérification).
- Authentification anonyme activée par défaut.
- Stratégies de mot de passe faibles.
- Exposition publique du port 4840.
- Attaques sur les implémentations (heap overflow, parsing malveillant).

**Contre-mesures** :

- Forcer SignAndEncrypt.
- PKI interne avec autorité de certification dédiée.
- Validation stricte des certificats.
- Désactiver l'accès anonyme.
- Segmentation réseau VLAN OT/IT.
- Audit des sessions et des accès.

---

## CAN Bus

### CAN Bus : Définition et historique

**CAN** (Controller Area Network) est un protocole de bus série développé par **Robert Bosch GmbH** au début des années 1980 pour l'industrie automobile. Il a été officiellement publié en **1986** et normalisé sous **ISO 11898**.

**Créateur** : Robert Bosch GmbH.  
**Première production** : Mercedes-Benz W140 (1991).  
**Standard** : ISO 11898-1 (couche liaison), ISO 11898-2 (couche physique haute vitesse).  
**Site** : https://www.bosch-mobility-solutions.com

CAN est un bus **multi-maître** avec accès aléatoire et arbitrage par priorité. Il est déterministe, fiable et robuste aux perturbations électromagnétiques.

### CAN Bus : Architecture physique

Le bus CAN utilise une paire torsadée différentielle **CAN_H** et **CAN_L** avec une terminaison de 120 Ω aux deux extrémités.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CAN BUS ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│    ┌─────────┐         ┌─────────┐         ┌─────────┐         ┌─────────┐  │
│    │  ECU 1  │         │  ECU 2  │         │  ECU 3  │         │  ECU N  │  │
│    │ Engine  │         │  ABS    │         │  HVAC   │         │ Gateway │  │
│    └────┬────┘         └────┬────┘         └────┬────┘         └────┬────┘  │
│         │ CAN_TX            │                   │                   │       │
│         │ CAN_RX            │                   │                   │       │
│    ┌────┴────┐         ┌────┴────┐         ┌────┴────┐         ┌────┴────┐  │
│    │CAN      │         │CAN      │         │CAN      │         │CAN      │  │
│    │Transceiver         Transceiver         Transceiver         Transceiver  │
│    └────┬────┘         └────┬────┘         └────┬────┘         └────┬────┘  │
│         │ CAN_H             │ CAN_H             │ CAN_H             │       │
│    ═════╪═══════════════════╪═══════════════════╪═══════════════════╪═════  │
│         │ CAN_L             │ CAN_L             │ CAN_L             │       │
│    ═════╪═══════════════════╪═══════════════════╪═══════════════════╪═════  │
│       120Ω                (nœuds)                              120Ω         │
│     Termination                                             Termination     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Vitesses CAN standard** :

| Vitesse | Longueur max bus |
|---------|------------------|
| 125 kbps | 500 m |
| 250 kbps | 250 m |
| 500 kbps | 100 m |
| 1 Mbps | 40 m |

### CAN Bus : Protocole de communication

**Trame CAN 2.0A (ID 11 bits)** :

| Champ | Taille | Description |
|-------|--------|-------------|
| SOF | 1 bit | Start of Frame |
| Identifier | 11 bits | Identifiant de message |
| RTR | 1 bit | Remote Transmission Request |
| Control | 6 bits | DLC, IDE, r0 |
| Data | 0-8 octets | Charge utile |
| CRC | 15 bits | Contrôle d'intégrité |
| ACK | 2 bits | Accusé de réception |
| EOF | 7 bits | End of Frame |

**CAN 2.0B (ID 29 bits)** : identifiants étendus pour plus de flexibilité.

**Arbitrage** : le bus CAN utilise la méthode **CSMA/CD+AMP** (Carrier Sense Multiple Access / Collision Detection with Arbitration on Message Priority). L'identifiant le plus faible (numériquement) gagne l'arbitrage.

**Types de trames** :

- Data Frame
- Remote Frame
- Error Frame
- Overload Frame
- Interframe Space

### CAN Bus : Configuration

#### Configuration d'une interface CAN sous Linux

```bash
# Charger le module CAN
sudo modprobe can
sudo modprobe can_raw
sudo modprobe vcan

# Configurer une interface CAN physique
sudo ip link set can0 type can bitrate 500000
sudo ip link set up can0

# Interface virtuelle (loopback/test)
sudo ip link add dev vcan0 type vcan
sudo ip link set up vcan0
```

#### Envoi et réception avec can-utils

```bash
# Envoyer une trame CAN standard
cansend vcan0 123#DEADBEEF

# Envoyer une trame avec données étendues
cansend vcan0 12345678#1122334455667788

# Écouter le bus CAN
candump vcan0

# Écouter avec filtre
candump vcan0,123:7FF

# Générer des statistiques
canbusload vcan0
```

#### Script Python avec python-can

```python
import can

bus = can.interface.Bus(channel='vcan0', bustype='socketcan')

# Envoi
msg = can.Message(arbitration_id=0x123, data=[0x11, 0x22, 0x33, 0x44], is_extended_id=False)
bus.send(msg)

# Réception
for msg in bus:
    print(f"ID: {hex(msg.arbitration_id)} Data: {msg.data.hex()}")
```

### CAN Bus : Commandes de vérification

```bash
# Vérifier l'état de l'interface
ip -details -statistics link show can0

# Découverte des trames actives
candump -tA can0

# Analyse du trafic avec candump formaté
candump -l can0

# Générer un fichier log pour analyse Wireshark
candump -L can0 > capture.log

# Wireshark avec CAN
wireshark -k -i can0
```

### CAN Bus : Applications

- **Automobile** : moteur, ABS, airbags, climatisation, infotainment.
- **Camions et bus** : SAE J1939.
- **Agriculture** : ISO 11783 (ISOBUS).
- **Aviation** : CANaerospace.
- **Industrie** : CANopen, DeviceNet.
- **Marine** : NMEA 2000.
- **Médical** : équipements de diagnostic.
- **Énergie** : gestion de batteries (Battery Management System).

### CAN Bus : Sécurité

**Vulnérabilités** :

- Aucune authentification des trames.
- Aucun chiffrement.
- Accès au bus = contrôle potentiel.
- Injection de messages (spoofing d'ID).
- Attaque par déni de service (bus off).
- Reverse engineering des signaux CAN.

**Attaques notables** :

- Charlie Miller & Chris Valasek : attaques Jeep Cherokee via CAN (2015).
- Injection de fausses valeurs de capteurs.
- Rejeu de commandes valides.

**Contre-mesures** :

- Segmentation du bus (gateway sécurisé).
- Authentification des messages (SecOC - Secure Onboard Communication).
- Intrusion Detection System (IDS) CAN.
- Chiffrement dans les protocoles applicatifs (CANsec, CANAuth).
- Contrôle d'accès physique au bus OBD-II.

---

## DNP3

### DNP3 : Définition et historique

**DNP3** (Distributed Network Protocol 3) est un protocole de communication développé par **Harris Controls Division** (aujourd'hui GE Grid Solutions) pour les infrastructures de distribution d'énergie électrique et les utilities.

**Créateur** : Harris Controls Division / Westronic, Inc.  
**Première version** : 1993.  
**Standardisation** : IEEE 1815-2010, IEEE 1815-2012.  
**Site** : https://www.dnp.org

DNP3 est conçu pour la **fiabilité** et la **sécurité** des communications entre les systèmes de contrôle centralisés (SCADA) et les équipements distants (RTU, IED).

### DNP3 : Architecture

DNP3 utilise un modèle **maître/esclave** ou **peer-to-peer** avec des classes de données et des mécanismes de report par exception.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          DNP3 ARCHITECTURE                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         SCADA MASTER                                │   │
│   │              Polling | Control | Time Sync | File Transfer          │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                               │                                             │
│          ═════════════════════╪═════════════════════                        │
│                               │                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │   RTU 1     │    │   RTU 2     │    │   IED 3     │    │   Substation│ │
│   │ Outstation  │    │ Outstation  │    │ Outstation  │    │ Gateway     │ │
│   │ Address 10  │    │ Address 20  │    │ Address 30  │    │ Address 40  │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│                                                                             │
│   Classes de données :                                                      │
│   - Class 0 : Static data (current values)                                  │
│   - Class 1, 2, 3 : Event data (changes, alarms, variations)                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Couches DNP3** :

| Couche | Rôle |
|--------|------|
| Application Layer | Objets, fonction codes, réponses |
| Transport Layer | Fragmentation des messages |
| Data Link Layer | Trames FT3, CRC, adressage |
| Physical Layer | Série RS-232/RS-485 ou TCP/IP |

### DNP3 : Configuration

#### Paramètres de liaison DNP3

```
Master Address     : 1
Outstation Address : 10
Link Status Period : 10 seconds
Data Link Confirm  : Sometimes / Always / Never
Application Confirm: Always for control
Time Sync          : Enabled
Unsolicited        : Class 1, 2, 3 enabled
```

#### Configuration avec opendnp3 (C++/Java/.NET)

```cpp
#include <opendnp3/DNP3Manager.h>

DNP3Manager manager(1, ConsoleLogger::Create());
auto channel = manager.AddTCPServer("server", LOG_LEVELS, ServerAcceptMode::CloseExisting, IPEndpoint("0.0.0.0", 20000), ChannelRetry::Default());

OutstationStackConfig config(DatabaseSizes::AllTypes(10));
config.outstation.eventBufferConfig = EventBufferConfig::AllTypes(100);
config.outstation.params.allowUnsolicited = true;

auto outstation = channel->AddOutstation("outstation", SuccessCommandHandler::Create(), DefaultOutstationApplication::Create(), config);
outstation->Enable();
```

### DNP3 : Commandes de vérification

```bash
# Scanner les ports DNP3
nmap -p 20000 --open 192.168.1.0/24

# Utilisation de dnp3-scanner ou outstation emulator
# Test avec outstation simulator

# Vérifier la connectivité DNP3 avec un client
./master-demo 192.168.1.100 20000
```

### DNP3 : Applications

- **Réseaux électriques** : SCADA de distribution et de transmission.
- **Eau et assainissement** : stations de pompage, traitement.
- **Pétrole et gaz** : pipelines, stations de compression.
- **Énergies renouvelables** : fermes solaires et éoliennes.
- **Transport** : signalisation ferroviaire.

### DNP3 : Sécurité

**DNP3 Secure Authentication (DNP3-SA)** :

- Ajoute une couche d'authentification au protocole.
- Utilise des clés pré-partagées (PSK) ou des certificats.
- Gère les challenges et les réponses basées sur HMAC-SHA256.
- Protège contre les commandes non autorisées.

**Vulnérabilités classiques** :

- Configuration par défaut sans authentification.
- Clés statiques faibles.
- Pas de chiffrement natif dans DNP3 classique.
- Man-in-the-middle sur les liens série/IP.

**Contre-mesures** :

- Activer DNP3-SA pour tous les ordres de commande.
- Utiliser des tunnels VPN/IPsec pour les liens WAN.
- Rotation régulière des clés.
- Audit des événements et des connexions.

---

## BACnet

### BACnet : Définition et historique

**BACnet** (Building Automation and Control Networks) est un protocole de communication pour les systèmes de gestion technique du bâtiment (GTB/BMS). Il a été développé par l'**ASHRAE** (American Society of Heating, Refrigerating and Air-Conditioning Engineers).

**Créateur** : ASHRAE BACnet Committee (SSPC 135).  
**Première version** : 1995.  
**Standard** : ANSI/ASHRAE Standard 135.  
**Site** : https://www.bacnet.org

BACnet permet l'interopérabilité entre systèmes HVAC, éclairage, accès, sécurité incendie, ascenseurs et compteurs d'énergie.

### BACnet : Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          BACnet ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         BMS Workstation                             │   │
│   │              Trends | Schedules | Alarms | Reports                  │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                               │                                             │
│          ═════════════════════╪═════════════════════                        │
│                               │                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │  VAV Box    │    │  Chiller    │    │  Lighting   │    │  Energy     │ │
│   │  Controller │    │  Controller │    │  Panel      │    │  Meter      │ │
│   │  Device 100 │    │  Device 200 │    │  Device 300 │    │  Device 400 │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│                                                                             │
│   Objets BACnet : Analog Input, Analog Output, Binary Value, Schedule,      │
│   Trend Log, Event Enrollment, Notification Class, File, Device...          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Modèles d'objets BACnet courants** :

| Objet | ID d'objet | Usage |
|-------|------------|-------|
| Analog Input (AI) | 0 | Capteurs analogiques |
| Analog Output (AO) | 1 | Commandes analogiques |
| Analog Value (AV) | 2 | Valeurs calculées |
| Binary Input (BI) | 3 | Entrées binaires |
| Binary Output (BO) | 4 | Sorties binaires |
| Binary Value (BV) | 5 | Valeurs binaires |
| Device | 8 | Propriétés du dispositif |
| Schedule | 17 | Programmations horaires |
| Trend Log | 20 | Historisation |

**Services BACnet** :

- Who-Is / I-Am (découverte)
- ReadProperty / WriteProperty
- ReadPropertyMultiple / WritePropertyMultiple
- SubscribeCOV (Change of Value)
- ConfirmedEventNotification
- TimeSynchronization
- ReinitializeDevice

### BACnet : Configuration

#### Ports et transports BACnet

| Transport | Port / Caractéristique |
|-----------|------------------------|
| BACnet/IP | 47808/udp (0xBAC0) |
| BACnet MS/TP | RS-485, master-slave token passing |
| BACnet/Ethernet | Ethernet II direct |
| BACnet/SC | WebSockets sécurisé (TLS 1.3) |
| BACnet/IPv6 | Port 47808/udp |

#### Exemple de configuration BACnet/IP

```python
from bacpypes.core import run
from bacpypes.pdu import Address
from bacpypes.app import BIPSimpleApplication
from bacpypes.object import AnalogValueObject, PropertyIdentifier
from bacpypes.local.device import LocalDeviceObject

this_device = LocalDeviceObject(
    objectName="HackersTchadDevice",
    objectIdentifier=599,
    maxApduLengthAccepted=1024,
    segmentationSupported="segmentedBoth",
    vendorIdentifier=15,
)

app = BIPSimpleApplication(this_device, "192.168.1.100/24")

av = AnalogValueObject(
    objectIdentifier=("analogValue", 1),
    objectName="Temperature",
    presentValue=22.5,
    statusFlags=[0, 0, 0, 0],
    covIncrement=1.0,
)
app.add_object(av)

run()
```

### BACnet : Commandes de vérification

```bash
# Scanner le port BACnet/IP
nmap -sU -p 47808 --open 192.168.1.0/24

# Who-Is avec bacpypes
python -m bacpypes.discover WhoIs

# Lire une propriété
python -m bacpypes.consolecmd --color
> read 192.168.1.100 device:599 objectName

# Wireshark avec filtre BACnet
bacnet
```

### BACnet : Applications

- **Bâtiments commerciaux** : HVAC, éclairage, stores.
- **Hôpitaux** : contrôle des zones critiques.
- **Aéroports** : gestion des terminaux.
- **Data centers** : refroidissement, monitoring énergie.
- **Campus universitaires** : supervision multi-bâtiments.
- **Smart cities** : gestion des infrastructures urbaines.

### BACnet : Sécurité

**BACnet/SC (Secure Connect)** :

- Introduit en 2016 (Addendum 135-2016bk).
- Utilise TLS 1.3, WebSockets et certificats X.509.
- Remplace ou complète BACnet/IP pour les connexions non fiables.

**Vulnérabilités** :

- Découverte Who-Is non authentifiée.
- ReinitializeDevice exploitable pour redémarrer des dispositifs.
- BACnet/IP non chiffré.
- Faibles mots de passe sur les interfaces web des contrôleurs.

**Contre-mesures** :

- Migrer vers BACnet/SC.
- Segmenter les réseaux BMS.
- Restreindre les broadcasts BACnet/IP.
- Auditer les configurations par défaut.

---

## PROFIBUS

### PROFIBUS : Définition et historique

**PROFIBUS** (Process Field Bus) est un standard de bus de terrain développé en **1989** par une alliance industrielle allemande avec le soutien du ministère fédéral de l'Éducation et de la Recherche (BMBF).

**Créateur** : PROFIBUS Nutzerorganisation e.V. (PNO), désormais PI (PROFIBUS & PROFINET International).  
**Première norme** : DIN 19245, puis EN 50170.  
**Standard actuel** : IEC 61158 / IEC 61784.  
**Site** : https://www.profibus.com

PROFIBUS existe en trois variantes :

- **PROFIBUS DP** (Decentralized Peripherals) : automatisme manufacturier.
- **PROFIBUS PA** (Process Automation) : environnements explosifs (norme IEC 61158-2).
- **PROFIBUS FMS** (Fieldbus Message Specification) : obsolète.

### PROFIBUS : Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PROFIBUS DP ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         PLC MASTER (Class 1)                        │   │
│   │              Cyclic Data Exchange | Diagnostics | Parameters        │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                               │                                             │
│          ═════════════════════╪═════════════════════                        │
│                               │                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │  Slave 1    │    │  Slave 2    │    │  Slave 3    │    │  Slave N    │ │
│   │  I/O Module │    │  Drive      │    │  Valve      │    │  Sensor     │ │
│   │  Address 3  │    │  Address 4  │    │  Address 5  │    │  Address 126│ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│                                                                             │
│   Vitesse : 9.6 kbps à 12 Mbps (selon longueur du bus)                      │
│   Medium : RS-485 pour DP, paire torsadée pour PA                           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Profils PROFIBUS DP** :

| Profil | Usage |
|--------|-------|
| DP-V0 | Échange cyclique de base, diagnostics |
| DP-V1 | Échange acyclique pour paramétrage |
| DP-V2 | Communication isochrone, décentralisée |

### PROFIBUS : Configuration

#### Paramètres de bus PROFIBUS DP

```
Baud rate     : 1.5 Mbps (typique)
Bus length    : 200 m (à 1.5 Mbps)
Termination   : 220 Ω active aux extrémités
Address range : 0-126 (0 et 126 réservés)
Cable         : PROFIBUS Type A (paire torsadée blindée)
```

#### Configuration avec TIA Portal (Siemens)

```
1. Créer un projet STEP 7.
2. Ajouter un PLC S7-1500 comme maître DP.
3. Insérer une carte CM DP ou un CPU avec interface PROFIBUS.
4. Configurer les esclaves via le catalogue de périphériques.
5. Assigner les adresses PROFIBUS (3, 4, 5...).
6. Configurer les modules d'E/S et les adresses mémoire.
7. Compiler et télécharger la configuration dans le PLC.
```

### PROFIBUS : Commandes de vérification

```bash
# Diagnostic PROFIBUS avec outils Siemens
# Simatic STEP 7 -> Diagnostic Buffer
# PDM (Process Device Manager) pour PROFIBUS PA

# Utilisation de PROFIBUS sniffers (ProfiTrace, NetTEST II)
profiTrace.exe

# Vérifier la qualité du signal avec oscilloscope différentiel
# Mesurer les tensions sur CAN_H / CAN_L équivalentes
```

### PROFIBUS : Applications

- **Automobile** : chaînes de montage robotisées.
- **Pharmaceutique** : process batch.
- **Alimentaire et boissons** : lignes de production.
- **Pétrochimie** : instrumentation de terrain (PA).
- **Traitement des eaux** : stations de pompage.
- **Minage** : convoyeurs, broyeurs.

### PROFIBUS : Sécurité

**Vulnérabilités** :

- Pas de chiffrement natif.
- Pas d'authentification des esclaves.
- Risque de substitution de dispositif.
- Accès physique au bus = compromission possible.

**Contre-mesures** :

- Sécurité physique des armoires et bus.
- Surveillance des changements de configuration.
- Passerelles sécurisées vers PROFINET ou IP.
- Segmentation réseau.

---

## EtherCAT

### EtherCAT : Définition et historique

**EtherCAT** (Ethernet for Control Automation Technology) est un protocole Ethernet temps réel développé par **Beckhoff Automation** en **2003**.

**Créateur** : Beckhoff Automation.  
**Standardisation** : IEC 61158 (depuis 2005), IEC 61784-2, SEMI E54.20.  
**Site** : https://www.ethercat.org

EtherCAT repose sur un principe de **traitement des trames à la volée** (on-the-fly processing). Chaque nœud lit et écrit des données dans la trame pendant qu'elle traverse le nœud, sans la copier entièrement.

### EtherCAT : Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          EtherCAT ARCHITECTURE                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         EtherCAT MASTER                             │   │
│   │           TwinCAT | IgH EtherCAT | SOEM | Acontis | KPA            │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                               │                                             │
│                               │ Ethernet (100 Mbps)                         │
│                               ▼                                             │
│   ┌───────────┐      ┌───────────┐      ┌───────────┐      ┌───────────┐   │
│   │  Slave 1  │──┬──▶│  Slave 2  │──┬──▶│  Slave 3  │──┬──▶│  Slave N  │   │
│   │  ESI      │  │   │  Drive    │  │   │  I/O      │  │   │  Terminator│   │
│   │  0x1001   │  │   │  0x2001   │  │   │  0x3001   │  │   │  0xFFFF   │   │
│   └───────────┘  │   └───────────┘  │   └───────────┘  │   └───────────┘   │
│                  │                  │                  │                   │
│   ◀──────────────┴──────────────────┴──────────────────┘                   │
│                            Return Path                                      │
│                                                                             │
│   Traitement à la volée : chaque nœud extrait et insère des données         │
│   pendant le passage de la trame.                                           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Topologies supportées** :

- Linéaire
- Étoile
- Arbre
- Anneau (redondance câble)
- Traversée (daisy-chain via EBUS)

### EtherCAT : Configuration

#### Configuration avec TwinCAT (Beckhoff)

```
1. Installer TwinCAT XAE (eXtended Automation Engineering).
2. Scanner le réseau EtherCAT pour découvrir les esclaves.
3. Charger les fichiers ESI (EtherCAT Slave Information).
4. Configurer les PDO (Process Data Objects) et SDO (Service Data Objects).
5. Mapper les variables PLC aux entrées/sorties EtherCAT.
6. Activer la configuration et passer en mode RUN.
```

#### Configuration avec SOEM (Simple Open EtherCAT Master)

```c
#include "ethercat.h"

char IOmap[4096];
int expectedWKC;

int main(int argc, char *argv[]) {
    if (ec_init("eth0")) {
        printf("Interface EtherCAT initialisée\n");
        
        if (ec_config_init(FALSE) > 0) {
            printf("%d esclaves trouvés\n", ec_slavecount);
            
            ec_config_map(&IOmap);
            ec_configdc();
            
            ec_statecheck(0, EC_STATE_SAFE_OP, EC_TIMEOUTSTATE);
            
            expectedWKC = (ec_group[0].outputsWKC * 2) + ec_group[0].inputsWKC;
            
            ec_slave[0].state = EC_STATE_OPERATIONAL;
            ec_writestate(0);
            ec_statecheck(0, EC_STATE_OPERATIONAL, EC_TIMEOUTSTATE);
            
            while(1) {
                ec_send_processdata();
                wkc = ec_receive_processdata(EC_TIMEOUTRET);
                if(wkc >= expectedWKC) {
                    // Traitement des données cycliques
                }
            }
        }
        ec_close();
    }
    return 0;
}
```

### EtherCAT : Commandes de vérification

```bash
# Scanner le bus EtherCAT avec outils Beckhoff
tcdiag

# Outils SOEM
./simple_test eth0

# Vérifier l'état des esclaves
cat /sys/bus/ec/devices/master0/slaves/slave0000/state

# Wireshark avec filtre EtherCAT
echmod or ecat
```

### EtherCAT : Applications

- **Machine-outil** : commande numérique, axes interpolés.
- **Robotique** : robots delta, SCARA, anthropomorphes.
- **Emballage** : machines d'emballage haute vitesse.
- **Systèmes de vision** : caméras industrielles synchronisées.
- **Semi-conducteurs** : machines de production de puces.
- **Impression 3D industrielle** : contrôle multi-axes.
- **Énergie éolienne** : contrôle des pales et des convertisseurs.

### EtherCAT : Sécurité

**Safety over EtherCAT (FSoE - Fail Safe over EtherCAT)** :

- Protocole de sécurité SIL3 intégré à EtherCAT.
- Transporte des signaux de sécurité (arrêts d'urgence, light curtains) dans la même trame.

**Vulnérabilités** :

- Pas de chiffrement natif des données cycliques.
- Sécurité dépendante de la conception réseau.
- Risques si le maître est compromis.

**Contre-mesures** :

- Isoler le réseau EtherCAT dans une zone industrielle dédiée.
- Contrôler l'accès physique aux switchs et esclaves.
- Utiliser des firewalls industriels pour les liaisons vers l'IT.
- Auditer les fichiers ESI et les configurations PDO.

---

## Comparatif global

| Critère | Modbus | OPC UA | CAN Bus | DNP3 | BACnet | PROFIBUS | EtherCAT |
|---------|--------|--------|---------|------|--------|----------|----------|
| Créateur | Modicon (Schneider) | OPC Foundation | Bosch | Harris / Westronic | ASHRAE | PNO / PI | Beckhoff |
| Année | 1979 | 2006 | 1986 | 1993 | 1995 | 1989 | 2003 |
| Topologie | Maître/Esclave | Client/Serveur, PubSub | Multi-maître bus | Maître/Outstation | Client/Serveur, MS/TP | Maître/Esclave | Maître/Esclave en anneau/line |
| Couche physique | RS-232/485, Ethernet | Ethernet, TCP/IP | Paire torsadée différentielle | RS-232/485, IP | MS/TP, IP, Ethernet | RS-485 (DP), paire torsadée (PA) | Ethernet 100 Mbps |
| Déterminisme | Moyen | Fort | Fort | Fort | Moyen | Très fort | Très fort |
| Taille données | 244 octets max | Illimitée | 8 octets par trame | Jusqu'à 2048 octets fragmentés | Jusqu'à 1476 octets | 244 octets | Jusqu'à 1486 octets par trame |
| Sécurité native | Faible | Très forte | Faible | Moyenne (DNP3-SA) | Moyenne (BACnet/SC) | Faible | Moyenne |
| Chiffrement | Non | Oui (TLS) | Non | Non natif | Oui (BACnet/SC) | Non | Non natif |
| Domaine principal | Industrie générale | Interopérabilité IT/OT | Automobile, embarqué | Utilities, énergie | Bâtiment intelligent | Automatisme manufacturier | Motion control, robotique |

---

## Matrice de sécurité OT/IT

```
┌────────────────────────────────────────────────────────────────────────────────┐
│                      MATRICE DE SÉCURITÉ OT/IT                                 │
├────────────────────────────────────────────────────────────────────────────────┤
│                                                                                │
│   Niveau 5 : Enterprise        ERP, MES, BI, Cloud                             │
│   ─────────────────────────────────────────────────────────────               │
│   Niveau 4 : Site / Business   Historiens, MES, Engineering stations          │
│   ─────────────────────────────────────────────────────────────               │
│   Niveau 3 : Operations        SCADA, HMI, OPC servers                         │
│   ─────────────────────────────────────────────────────────────               │
│   Niveau 2 : Supervisory       PLC, DCS, RTU                                   │
│   ─────────────────────────────────────────────────────────────               │
│   Niveau 1 : Control           Sensors, actuators, drives, I/O modules         │
│   ─────────────────────────────────────────────────────────────               │
│   Niveau 0 : Process           Physical process, robots, machines              │
│                                                                                │
│   Modbus, DNP3, BACnet, PROFIBUS, EtherCAT → Niveaux 0-3                      │
│   OPC UA → Niveaux 2-5 (pont IT/OT)                                           │
│   CAN Bus → Niveaux 0-2 (embarqué, automobile, machine)                       │
│                                                                                │
│   ZONE IT              DMZ / PARE-FEU INDUSTRIEL              ZONE OT          │
│   ┌─────────┐         ┌───────────────┐         ┌─────────────────────────┐   │
│   │  ERP    │◄───────►│  Data Diode   │◄───────►│  SCADA / OPC Server     │   │
│   │  MES    │         │  Jump Server  │         │  PLC / RTU / DCS        │   │
│   └─────────┘         └───────────────┘         └─────────────────────────┘   │
│                                                                                │
└────────────────────────────────────────────────────────────────────────────────┘
```

**Bonnes pratiques de sécurité OT** :

1. Segmenter les réseaux IT et OT avec des firewalls industriels.
2. Utiliser des VLANs par type de protocole et par zone.
3. Déployer des systèmes de détection d'intrusion (IDS/IPS) industriels.
4. Appliquer le principe du moindre privilège.
5. Maintenir un inventaire d'actifs OT à jour.
6. Sauvegarder les configurations des automates.
7. Planifier des exercices de réponse aux incidents.
8. Former les équipes OT à la cybersécurité.

---

## Outils d'analyse et de test

### Outils généraux

| Outil | Usage | Protocoles supportés |
|-------|-------|----------------------|
| Wireshark | Analyse protocolaire | Tous via Ethernet |
| nmap | Découverte de ports et scripts NSE | Modbus, OPC UA, DNP3, BACnet |
| Metasploit | Tests d'intrusion | Modbus, DNP3, SCADA |
| Python (scapy, pymodbus, opcua, bacpypes, python-can, SOEM) | Scripts personnalisés | Tous |

### Outils par protocole

#### Modbus
- `pymodbus` : bibliothèque Python.
- `modpoll` : client Modbus CLI.
- `mbtget` : client Modbus léger.
- `qModMaster` : client graphique.
- `ModbusPal` : simulateur Java.
- `mbtget`, `mbtserver`.

#### OPC UA
- `UaExpert` (Unified Automation) : client graphique.
- `Prosys OPC UA Client`.
- `freeopcua` : bibliothèque Python.
- `open62541` : implémentation C open source.
- `OPC Foundation .NET Standard stack`.

#### CAN Bus
- `can-utils` (Linux) : candump, cansend, canbusload.
- `python-can` : bibliothèque Python.
- `BusMaster` : outil d'analyse CAN.
- `Vector CANoe / CANalyzer` : outils professionnels.
- `PEAK PCAN-View`.

#### DNP3
- `opendnp3` : stack open source C++/.NET/Java.
- `DNP3 User Group` tools.
- `ATCom DNP3`.

#### BACnet
- `bacpypes` : bibliothèque Python.
- `BACnet Explorer` (Contemporary Controls).
- `Visual BACnet` (Optigo Networks).
- `Wireshark` avec dissector BACnet.

#### PROFIBUS
- `ProfiTrace` : analyse de bus.
- `NetTEST II` : testeur de câble et de protocole.
- `TIA Portal / STEP 7` : configuration Siemens.
- `PNO certification tools`.

#### EtherCAT
- `TwinCAT` (Beckhoff) : master et ingénierie.
- `SOEM` (Simple Open EtherCAT Master).
- `IgH EtherCAT Master` (Linux).
- `EtherCAT Network Information (ENI)` tools.

---

## Ressources, livres et liens

### Livres recommandés

1. **"Industrial Network Security"** — Eric D. Knapp, Joel Thomas Langill. Syngress, 2014.  
   ISBN : 978-0124201149

2. **"Applied Cyber Security and the Smart Grid"** — Eric D. Knapp, Raj Samani. Syngress, 2013.  
   ISBN : 978-1597499989

3. **"Hacking Exposed: Industrial Control Systems"** — Clint Bodungen et al. McGraw-Hill, 2016.  
   ISBN : 978-0071829489

4. **"Modbus Messaging on TCP/IP Implementation Guide"** — Modbus Organization.  
   Disponible sur : https://modbus.org/docs/Modbus_Messaging_Implementation_Guide_V1_0b.pdf

5. **"OPC Unified Architecture"** — Wolfgang Mahnke, Stefan-Helmut Leitner, Matthias Damm. Springer, 2009.  
   ISBN : 978-3540688983

6. **"Controller Area Network (CAN) Basics"** — Microchip Technology.  
   Application Note AN713.

7. **"DNP3 Users Group Technical Documents"** — https://www.dnp.org

8. **"BACnet: The Global Standard for Building Automation"** — Michael Newman.  
   ISBN : 978-1466552709

9. **"PROFIBUS PA / DP Engineering"** — Manfred Popp.  
   ISBN : 978-3800734639

10. **"EtherCAT Technology Introduction"** — EtherCAT Technology Group.  
    https://www.ethercat.org/download/documents/EtherCAT_Device_Protocol_Poster.pdf

### Liens officiels et communautaires

| Organisation | Lien |
|--------------|------|
| Modbus Organization | https://modbus.org |
| OPC Foundation | https://opcfoundation.org |
| CAN in Automation (CiA) | https://can-cia.org |
| DNP3 Users Group | https://www.dnp.org |
| ASHRAE BACnet | https://www.bacnet.org |
| PROFIBUS & PROFINET International | https://www.profibus.com |
| EtherCAT Technology Group | https://www.ethercat.org |
| ICS-CERT (CISA) | https://www.cisa.gov/ics |
| SANS ICS | https://ics.sans.org |
| Dragos | https://dragos.com |
| Claroty | https://claroty.com |
| Nozomi Networks | https://nozominetworks.com |

### Ressources de l'auteur hackers_tchad

- **GitHub** : https://github.com/hackers_tchad
- **Twitter/X** : https://x.com/hackers_tchad
- **LinkedIn** : https://linkedin.com/in/hackers_tchad
- **Blog** : https://hackers-tchad.medium.com
- **Chaîne YouTube** : https://youtube.com/@hackers_tchad
- **Discord** : https://discord.gg/hackers_tchad
- **Telegram** : https://t.me/hackers_tchad

---

## Glossaire

| Terme | Définition |
|-------|------------|
| **Actuator** | Actionneur, dispositif convertissant un signal de commande en action physique. |
| **BMS** | Building Management System, système de gestion technique du bâtiment. |
| **CRC** | Cyclic Redundancy Check, contrôle d'intégrité par redondance cyclique. |
| **DCS** | Distributed Control System, système de contrôle commande distribué. |
| **Determinism** | Propriété d'un système garantissant des temps de réponse prévisibles. |
| **EMS** | Energy Management System, système de gestion de l'énergie. |
| **ESI** | EtherCAT Slave Information, fichier XML décrivant un esclave EtherCAT. |
| **HMI** | Human-Machine Interface, interface homme-machine. |
| **IED** | Intelligent Electronic Device, dispositif électronique intelligent. |
| **IIoT** | Industrial Internet of Things, internet industriel des objets. |
| **MTU** | Master Terminal Unit, unité maître dans un système SCADA. |
| **OT** | Operational Technology, technologies opérationnelles. |
| **PLC** | Programmable Logic Controller, automate programmable industriel. |
| **RTU** | Remote Terminal Unit, unité terminale distante. |
| **SCADA** | Supervisory Control And Data Acquisition, supervision et acquisition de données. |
| **Sensor** | Capteur, dispositif mesurant une grandeur physique. |
| **VFD** | Variable Frequency Drive, variateur de fréquence/vitesse. |
| **VLAN** | Virtual Local Area Network, réseau local virtuel. |

---

## Licence et crédits

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   Document : Industrial Protocols Mastery Guide                              ║
║   Auteur   : hackers_tchad                                                   ║
║   Date     : 2026                                                            ║
║                                                                              ║
================================================================================
```

<div align="center">

```
██╗  ██╗ █████╗  ██████╗██╗  ██╗███████╗██████╗ ███████╗    ████████╗ ██████╗██╗  ██╗ █████╗ ██████╗ 
██║  ██║██╔══██╗██╔════╝██║ ██╔╝██╔════╝██╔══██╗██╔════╝    ╚══██╔══╝██╔════╝██║  ██║██╔══██╗██╔══██╗
███████║███████║██║     █████╔╝ █████╗  ██████╔╝███████╗       ██║   ██║     ███████║███████║██║  ██║
██╔══██║██╔══██║██║     ██╔═██╗ ██╔══╝  ██╔══██╗╚════██║       ██║   ██║     ██╔══██║██╔══██║██║  ██║
██║  ██║██║  ██║╚██████╗██║  ██╗███████╗██║  ██║███████║       ██║   ╚██████╗██║  ██║██║  ██║██████╔╝
╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚══════╝       ╚═╝    ╚═════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═════╝ 
```

**Hack The Planet — Know Your Protocols — Secure Your ICS**

</div>
