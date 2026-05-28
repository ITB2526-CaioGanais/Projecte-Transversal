# Pro01: Projecte Transversal ASIXc1 - Innovate Tech 🚀

Este repositorio contiene la documentación técnica y el código de configuración correspondientes al **Proyecto Transversal** del CFGS Administració de Sistemes Informàtics en Xarxa (Curs 2025/2026).

El proyecto nace de la necesidad de **Innovate Tech**, una empresa dedicada a la provisión de servicios tecnológicos, de modernizar su capacidad operativa y comunicativa, integrando la gestión de personal con servicios multimedia avanzados.

## 👥 Integrantes del Grupo
* **Nombre del grupo de trabajo:** `pro-asixc1[Grupo]-[GrupDeTreball]` (Ejemplo: `pro-asixcla-g1`) 
* **Miembros:**
  * Josué Amador ([@JosueGitHub](https://github.com/ITB2526-JosueAmador))
  * Caio Ganais ([@CaioGitHub](https://github.com/ITB2526-CaioGanais))
  * Alex Capitán ([@AlexGitHub](https://github.com/ITB2526-AlexCapitan))
  * Ramiro Cori ([@RamiroGitHub](https://github.com/ITB2526-RamiroCori))

---

## 📋 Módulos Implicados
El proyecto integra competencias transversales de los siguientes módulos profesionales:
* **M0371 Fonaments de Maquinari** (Diseño e infraestructura de CPD y Cloud AWS).
* **M0375 Serveis de Xarxes i Internet** (Streaming multimedia de audio, vídeo y videoconferencia).
* **M0377 Administració de Bases de Dades** (Diseño relacional, seguridad, roles y auditoría).
* **M1665 Digitalització Aplicada als Sectors Productius** (Sostenibilidad, ciberseguridad y transformación digital).

---

## 🛠️ Componentes del Proyecto

### 1. Propuesta e Infraestructura de CPD (Sostenible y Cloud) 🏢☁️
Diseño e implantación de un Centro de Procesamiento de Datos eficiente que garantice la continuidad de negocio con soluciones enfocadas a la sostenibilidad.
* **Ubicación Física e Infraestructura IT:** Planificación de la climatización, salas camufladas, distribución de cableado (falso suelo/techo), estructuración de racks y cálculo de autonomía mediante SAIs.
* **Arquitectura en la Nube (AWS):** Implementación de una infraestructura con al menos 4 servicios desplegados en instancias independientes:
  * Servicio Web corporativo.
  * Servicio de transferencia de ficheros seguro (SFTP) autenticado con Directorio Activo.
  * Servicio de Directorio Activo para la gestión centralizada de usuarios.
  * Servicio de centralización de logs de auditoría de todos los equipos.
* **Automatización con Ansible:** Aprovisionamiento y configuración automatizada de (como mínimo) dos de las máquinas del entorno.
* **Seguridad:** Acceso exclusivo mediante par de claves pública/privada y administración con usuario específico (prohibido usuarios por defecto).

### 2. Servicios Multimedia y Pruebas de Ancho de Banda 🎙️📺
Despliegue de tecnologías estándar para la comunicación interna de los departamentos de la empresa (Ventas, Soporte Técnico, Administración y Logística) y canales externos para clientes.
* **Servicio de Audio:** Servidor de streaming operativo en formatos digitales estándar (MP3, AAC, OGG) con acceso directo vía navegador web.
* **Servicio de Vídeo:** Streaming multimedia mediante protocolos RTMP/HLS y codecs H.264/MP4 utilizando servidores dedicados (NGINX, Jellyfin o equivalente).
* **Videoconferencia:** Sistema corporativo basado en WebRTC a través de la herramienta Jitsi Meet para llamadas internas y soporte de clientes.
* **Auditoría de Rendimiento:** Pruebas y análisis de ancho de banda (Download, Upload y Latencia) simulando entornos de concurrencia de servicios para evaluar la viabilidad de la red.

### 3. Diseño e Implementación de Base de Dades (Seguridad y Auditoría) 📊🔒
Modelado e implementación de un sistema relacional en un SGBD para la gestión organizativa interna y registros de uso multimedia.
* **Estructura:** Gestión de Empleados (DNI, datos personales) y Departamentos correspondientes.
* **Gestión de Comunicaciones:** Control de usuarios del sistema de comunicación, estado de actividad, enlaces de videoconferencia y configuraciones de calidad QoS según el ancho de banda del cliente.
* **Control de Acceso Relacional (RBAC):** Creación e implementación estricta de usuarios y roles diferenciados (`admin`, `vendes`, `administracio`, etc.) con privilegios SQL debidamente restringidos.
* **Automatización y Auditoría mediante Triggers:** * Control de cuotas de minutos mensuales y cantidad diaria de llamadas por usuario.
  * Generación de una tabla de avisos para registrar logs de auditoría ante intentos de modificación no autorizados en tablas sensibles.

---

## 📂 Estructura del Repositorio

El repositorio está estructurado de la siguiente manera:

```text
├── ansible/               # Playbooks y roles de Ansible para configuración de servidores
├── database/              # Scripts SQL (Esquema, triggers, inserción de datos de prueba)
│   ├── ER_Diagram/        # Diagrama Entidad-Relació y Esquema Relacional
│   └── scripts/           # Triggers y procedimientos
├── cpd-infraestructura/   # Documentación del diseño del CPD (climatización, SAIs, planos)
├── multimedia/            # Configuraciones de los servicios de Audio, Vídeo y Jitsi
└── docs/                  # Informe detallado del proyecto en formato Markdown

Treball Resumit!

# Projecte Transversal: Disseny de CPD, Infraestructura de Xarxa i Serveis al Núvol

Aquest repositori conté la memòria tècnica, els scripts d'automatització i els detalls de configuració per al desplegament de la infraestructura tecnològica d'**InnovateTech**. El projecte abasta des del disseny físic del Centre de Processament de Dades (CPD) local fins a la implementació d'una arquitectura híbrida al núvol d'Amazon Web Services (AWS).

---

## 1. Proposta de CPD: Infraestructura Física i Seguretat

### 1.1 Ubicació Física de la Sala a l'Edifici
El Centre de Processament de Dades (CPD) local s'ha projectat seguint estrictes criteris de seguretat ambiental i eficiència energètica:

* **Situació Física:** Es posiciona a la **Primera Planta** de l'edifici, en una **zona interior central** totalment aïllada (sense parets exteriors ni finestres).
  * *Planta Baixa descartada:* Per evitar riscos d'inundacions per avaries d'aigua o catàstrofes naturals, així com l'alt trànsit de personal.
  * *Segona Planta descartada:* Per minimitzar la radiació solar directa del teulat, millorant la sostenibilitat energètica i reduint la càrrega tèrmica.
* **Mesures d'Ofuscació:** La porta del CPD serà totalment opaca, blindada i **sense cap retolació o cartell indicador** (evitant textos com "Sala de Servidors"). Als mapes públics de l'edifici se li assignarà la nomenclatura genèrica de *"Sala Tècnica d'Instal·lacions"*.

### 1.2 Climatització i Condicionament Ambiental
* **Sistemes de Climatització:** S'implementa un sistema de refrigeració basat en **Inrow Cooling** amb contenció de **passadís tancat fred/calent** (*Hot/Cold Aisle Containment*). Això optimitza el flux de l'aire, evita la barreja tèrmica i redueix dràsticament la petjada ecològica del sistema de clima.
* **Humitat:** Mantinguda de forma automàtica entre el **40% i el 55%** per prevenir l'acumulació d'electricitat estàtica o problemes de condensació als circuits.
* **Neteja de l'Aire:** S'instal·len filtres d'aire mecànics **HEPA G4/F7** per mantenir la sala lliure de pols en suspensió i partícules abrasives.

### 1.3 Distribució, Sostre i Terra Tècnic
* **Terra Tècnic:** S'instal·la un terra elevat de **40 cm** amb rajoles antiestàtiques intercanviables. S'utilitza exclusivament com a plenum per a la impulsió de l'aire fred des de les màquines de clima cap al passadís fred.
* **Sostre Tècnic:** Sostre fals rebaixat que s'utilitza com a plenum de retorn per recollir l'aire calent generat pels racks i redirigir-lo cap als equips de refrigeració.
* **Gestió del Cablejat (Top-of-Rack):** Per evitar turbulències en el flux d'aire de sota el terra, el cablejat de xarxa i elèctric es distribueix per la part superior (sostre) mitjançant **safates metàl·liques perforades** (tipus *Relefil*) totalment independents:
  * *Safata A:* Dedicada en exclusiva a corrent elèctric.
  * *Safata B:* Dedicada a fibra òptica i coure per evitar interferències electromagnètiques (EMI).

---

## 2. Estructuració dels Racks i Infraestructura IT

Es dissenya un entorn modular compost per un mínim de **2 racks** estàndard de 19 polzades i 42U d'alçada:

### Rack 1: Comunicacions i Seguretat Perimetral (Networking)
* **Patch Panels:** 2 Patch Panels de 24 ports Cat6A per centralitzar el cablejat estructurat de les oficines.
* **Switches:** 2 Switches Gigabit gestionables configurats en **Stack** per garantir alta disponibilitat i redundància a la xarxa local.
* **Firewall/Router:** Equip físic per gestionar les diferents VLANs de l'oficina i aixecar el túnel **VPN segur** cap al núvol d'AWS.

### Rack 2: Servidors Locals i Backups
* **Servidors:** 2 Servidors en rack (format 2U) per a serveis crítics de contingència local.
* **NAS:** Servidor d'emmagatzematge en xarxa destinat a rebre i custodiar les còpies de seguretat de la base de dades d'AWS.
* **SAI (UPS):** Sistema d'Alimentació Ininterrompuda en format rack (3U).

---

## 3. Infraestructura Elèctrica i Càlcul del SAI

### 3.1 Alimentació Redundant
Cada rack disposa de dues línies elèctriques totalment independents connectades a **PDUs (Power Distribution Units) intel·ligents**:
* **Línia A:** Alimentació directa de la xarxa elèctrica de l'edifici.
* **Línia B:** Alimentació filtrada i protegida a través del SAI.

### 3.2 Càlcul de la Capacitat del SAI Corporatiu
Per dimensionar correctament el SAI de la sala local, es computen els consums actius dels equips elèctrics:

| Equip | Consum Actiu (W) |
| :--- | :--- |
| Switches (Stack) | 150 W |
| Router / Firewall | 100 W |
| Servidors i NAS | 400 W |
| **Total Consum Actiu** | **650 W** |

* **Autonomia Desitjada:** 20 minuts (temps calculat per rebre alertes automatitzades i procedir a un tancament lògic controlat o *shutdown* dels serveis en cas que no arranqui el grup electrogen).
* **Factor de Seguretat:** S'aplica un marge del **30%** per a futures expansions:
  $$\text{Potència Activa Requerida} = 650\text{ W} \times 1.3 = 845\text{ W}$$
* **Càlcul de la Potència Aparent:** Considerant un Factor de Potència ($\text{FP}$) típic de l'electrònica d'IT de $0.8$:
  $$\text{Potència Aparent} = \frac{845\text{ W}}{0.8} = 1056.25\text{ VA}$$

> **Conclusió Tècnica:** Es requereix un SAI d'un mínim de **1100 VA (1.1 kVA)** per garantir els 20 minuts d'autonomia a la càrrega calculada.

---

## 4. Seguretat Física, Lògica i Prevenció de Riscos (PRL)

### 4.1 Seguretat Física
* **Control d'Accés:** Lector biomètric de petjada dactilar combinat amb targeta de proximitat RFID a la porta d'entrada. Totes les obertures i denegacions es registren digitalment al SGBD.
* **Videovigilància:** Dues càmeres IP d'alta definició dins de la sala amb visió nocturna i gravació automàtica per detecció de moviment cap a un gravador local tancat.
* **Extinció d'Incendis:** Sistema de detecció precoç de fums per aspiració (**VESDA**). L'extinció és automàtica mitjançant inundació de **gas inert (Inergen o Novec 1230)**, extingint el foc per desplaçament d'oxigen sense danyar els components elèctrics. **Es prohibeix taxativament l'ús d'aigua.**
* **Evacuació:** La porta del CPD compta amb obertura cap enfora i barra antipànic.

### 4.2 Seguretat Lògica
* **Firewalls i Segmentació:** Implementació de regles tallafocs tant a l'oficina (físic) com a AWS mitjançant **Security Groups** segmentats per servei (aïllant LDAP, Web, etc.).
* **Tolerància a Fallades (RAID):** Els servidors utilitzen **RAID 1 (Mirall)** per al sistema operatiu i **RAID 5 / RAID 6** al NAS per a l'emmagatzematge de dades, garantint la continuïtat del servei davant la pèrdua de discs físics.

### 4.3 Prevenció de Riscos Laborals (PRL)
* **Risc d'Asfíxia (Gas Inundable):** Donat que el gas de seguretat desplaci l'oxigen, la sala disposa d'un polsador de "Parada de Descàrrega" a l'interior i un cartell lluminós exterior que indica *"No entrar - Gas Extingit"*. El personal té l'obligació de formar-se en el protocol d'evacuació davant de pre-alarmes.
* **Protecció Acústica:** Els ventiladors de climatització i servidors superen els 70-75 dB de forma contínua. És **obligatori l'ús d'auriculars o taps de protecció auditiva (EPI)** per a permanències superiors a 15 minuts.
* **Risc Elèctric (Equipotencialitat):** Totes les estructures metàl·liques (Racks, safates Relefil i l'esquelet del terra tècnic) estan connectades a la **Terra General de l'edifici** per evitar contactes indirectes per derivació.
* **Ergonomia i Seguretat d'Obra:** Ús d'elevadors manuals per a components que superin els 25 kg. Senyalització immediata amb cons quan s'aixequin rajoles del terra tècnic. Il·luminació d'emergència LED autònoma independent de la línia elèctrica general.

## 5. Administració i Disseny de la Base de Dades (MariaDB)

### 5.1 Justificació del SGBD
S'ha seleccionat **MariaDB** com a motor de base de dades relacional per a **InnovateTech** basant-se en els següents criteris tècnics:
* **Compatibilitat i Migració:** Compatibilitat total a nivell de codi i sintaxi amb MySQL, facilitant l'ús d'eines estàndard sense necessitat d'adaptar scripts.
* **Eficiència en Costos:** En tractar-se d'una llicència lliure (GPL) instal·lada directament sobre una instància **AWS EC2**, s'eliminen els sobrecostos de serveis gestionats com Amazon RDS.
* **Rendiment i Seguretat:** Ofereix un rendiment superior en consultes complexes i concurrència de connexions. A més, inclou suport natiu per a la gestió de rols d'usuari (essencial per a la directiva de seguretat del projecte).

---

### 5.2 Instal·lació, Configuració i Securització

La instal·lació es realitza al servidor EC2 mitjançant connexió SSH segura amb parell de claus. Els comandaments executats per al desplegament i securització són:

```bash
# Actualització dels repositoris del sistema operatiu
sudo apt update && sudo apt upgrade -y

# Instal·lació del servidor i el client de MariaDB
sudo apt install mariadb-server mariadb-client -y

# Inicialització i habilitació del servei en l'arrencada del sistema
sudo systemctl start mariadb
sudo systemctl enable mariadb

sudo mariadb-secure-installation

[DEPARTAMENTS] -- (1)-----------(N) -> [EMPLEATS] -- (1)-----(1) -> [QUOTA_USUARIS]
                                                 |      |
                                                 |      +--(1)-------(N) -> [REGISTRE_TRUCADES] (Originador)
                                                 |      +--(1)-------(N) -> [REGISTRE_TRUCADES] (Destinatari)
                                                 |      +--(1)-------(N) -> [MESURES_AMPLADA]
                                                 |      +--(1)-------(N) -> [AVISOS] (Auditoria)
                                                 |
                                               (N)
                                                 |
                                          [EMPLEATS_GRUP] (Taula Intermèdia N:M)
                                                 |
                                               (M)
                                                 |
[CATEGORIES_VIDEO] -- (1)----(N) -> [VIDEOS]   [GRUPS_QUALITAT] -- (1)---(N) -> [REGISTRE_TRUCADES]

5.4 Creació i Implementació en MariaDB
S'utilitza el joc de caràcters utf8mb4 per garantir el suport complet d'accents i caràcters especials.

5.4 Creació i Implementació en MariaDB
S'utilitza el joc de caràcters utf8mb4 per garantir el suport complet d'accents i caràcters especials.

5.5 Creació de Rols, Permisos i Automatització d'Usuaris
Es dissenya una política de control d'accés basada en rols (RBAC) per limitar els privilegis en l'entorn:

Script Bash d'automatització: crear_usuaris.sh
Per evitar tasques repetitives, s'ha implementat un script en Bash que valida la contrasenya del superusuari, descarta duplicats, comprova de manera estricta que els rols introduïts siguin vàlids, mapeja els usuaris amb els rols corresponents i genera una auditoria en un fitxer .sql.

Els usuaris corporatius de prova mapejats mitjançant l'script són:

it_admin -> Mapejat amb el rol admin

usuari_vendes -> Mapejat amb el rol vendes

usuari_admin -> Mapejat amb el rol administracio

usuari_traballador -> Mapejat amb el rol treballador

5.6 Triggers de Control de Seguretat i Auditoria
S'han desenvolupat 5 triggers en capa de base de dades per actuar com a restricció estricta de negoci en temps real:

trg_quota_minuts (BEFORE INSERT a registre_trucades): Suma els minuts utilitzats per l'empleat durant el mes en curs. Si la inserció supera el valor de max_minuts_mes a quota_usuaris, es llança un error SIGNAL SQLSTATE '45000' i es registra una entrada d'advertència a la taula avisos.

trg_quota_trucades_dia (BEFORE INSERT a registre_trucades): Controla que l'usuari no superi la capacitat límit diària de trucades assignada per contracte.

trg_bloqueig_usuari (BEFORE INSERT a registre_trucades): Abans d'establir una comunicació, intercepta si el DNI originador o el DNI destinatari tenen el seu estat catalogat com a bloquejat. En cas afirmatiu, avorta el procés de manera fulminant.

trg_audit_empleats_update (BEFORE UPDATE a empleats): Qualsevol intent de modificació de dades de personal fet per un usuari connectat amb rol treballador o vendes és denegat de forma fulminant i enviat directament al log d'avisos per a la seva posterior revisió.

trg_audit_administracio_trucades (BEFORE INSERT a registre_trucades): Evita el conflicte d'interessos impedint per motius de privacitat que el personal del rol d'administració pugui afegir entrades al trànsit i registre de trucades de clients.

Demostració i validació de fallada de Trigger:
Quan s'intenta forçar manualment una trucada des d'un usuari amb l'estat bloquejat

5.7 Política i Planificació d'Events de Còpia de Seguretat (Backup)
Justificació de la Periodicitat: S'ha establert una planificació diària. Atès que l'activitat comercial i el trànsit de trucades fluctuen contínuament, un marge de 24 hores és la finestra de pèrdua de dades màxima admissible per a l'empresa sense penalitzar el rendiment de la instància d'AWS.

### 5.8 Funcionament i Flux de l'Esdeveniment (Event)

L'esdeveniment `evt_backup_diari` s'executa de manera cíclica cada 24 hores i realitza de forma totalment automatitzada les següents tasques d'exportació:

| Taula | Fitxer Generat | Contingut Descrit |
| :--- | :--- | :--- |
| **`empleats`** | `/tmp/backup_empleats_YYYYMMDD.csv` | Tot el personal intern i usuaris de l'empresa. |
| **`departaments`** | `/tmp/backup_departaments_YYYYMMDD.csv` | Estructura organitzativa i de contacte interna. |
| **`registre_trucades`** | `/tmp/backup_trucades_YYYYMMDD.csv` | Historial exhaustiu de totes les trucades. |
| **`mesures_amplada`** | `/tmp/backup_mesures_YYYYMMDD.csv` | Resultats complets de les mètriques de xarxa. |

Cada fitxer es genera estructuralment en format **CSV** seguint les següents regles de sintaxi de dades:
* Camps delimitats i separats de forma estricta per comes (`,`).
* Valors de cadenes de text encasellats entre cometes dobles (`"`).
* Salts de línia (`\n`) independents per a cada registre de la taula.

---

### 5.9 Verificació, Prova Manual i Validació dels Fitxers CSV

Per assegurar que el planificador funciona de manera silent al servidor, s'executa la comprovació d'estat:
```sql
SHOW EVENTS FROM innovatetech;

Validació Mitjançant Prova Manual de Contingut:
Per certificar la integritat del codi sense dependre del temporitzador de 24 hores, es força manualment una crida de preparació d'escriptura exactament igual a la de l'esdeveniment, registrant la traça a la taula de control.

⚠️ Nota de Laboratori: Durant l'execució forçada del test manual, el motor va llançar un error de tipus File '/tmp/backup_empleats_20260526.csv' already exists. Això es tradueix com una validació d'èxit absoluta: l'esdeveniment periòdic s'havia disparat de manera totalment autònoma exactament a les 07:55:02 del matí, blindant el fitxer abans de la intervenció manual de l'administrador.

Verificació del pes i la persistència física dels binaris a la ruta d'emmagatzematge de la instància d'AWS:

6. Comprovacions i Auditories d'Amplada de Banda (Network Performance)6.1 Objectiu del Test de CàrregaL'objectiu crític d'aquestes proves consisteix a garantir de manera empírica que el dimensionament de la xarxa i la infraestructura de la instància d'AWS és capaç de tolerar consums concurrents i sostinguts de trànsit multimèdia multimediat (vídeo en streaming, àudio en alta definició i videoconferències en temps real) sense patir pèrdua de paquets ni latències de degradació.Per fer-ho, s'audita el rendiment del servidor multimèdia (Jellyfin) mitjançant el programari d'escaneig de xarxa speedtest-cli en dos escenaris completament oposats:Prova 1 (Benchmark en Repòs): Servidor totalment alliberat de processos externs, establint la base de rendiment màxim.Prova 2 (Stress Test en Càrrega): Servidor amb tasques multimèdia actives executant streaming de vídeo i àudio simultàniament.6.2 Projecció de Capacitat de Concurrència SimultàniaPrenent com a referència mètrica el pitjor dels escenaris simulats (la Prova 2, sota estrès sostingut), les capacitats de suport estimades de manera robusta per a les línies de negoci d'InnovateTech queden estructurades de la següent manera:Tipus de Servei MultimèdiaConsum d'Ample de Banda EstàndardCapacitat d'Usuaris Concurrents SuportatsVideoconferència Multiusuari~ 25 Mbps / connexió+ 150 usuaris simultanisVideo Streaming (HD - Jellyfin)~ 20 Mbps / flux+ 157 usuaris en paral·lelAudio Streaming (Alta Fidelitat)~ 320 kbps / flux+ 7.800 usuaris actius de forma concurrentTotes aquestes dades es recullen, es verifiquen i queden emmagatzemades automàticament a la base de dades persistent dins de la taula mesures_amplada de l'esquema d'auditoria per fer un seguiment evolutiu del rendiment de la infraestructura.6.3 Conclusió Tècnica d'Infraestructura i XarxaL'entorn cloud desplegat a AWS demostra un comportament de rendiment d'alt nivell empresarial. Presenta unes mètriques extremadament sòlides amb latències d'enrutament inferiors a 2 ms i amples de banda de baixada que superen de forma massiva els 3.9 Gbps.Aquestes dades certifiquen amb escreix que la capacitat de xarxa està sobredimensionada per respondre amb total solvència i sense cap mena de coll d'ampolla a pics d'alta demanda del servei. Per tant, es determina un estat de rendiment excel·lent i no es requereix cap intervenció ni canvi d'arquitectura en aquest component.
