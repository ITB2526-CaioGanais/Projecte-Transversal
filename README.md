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
