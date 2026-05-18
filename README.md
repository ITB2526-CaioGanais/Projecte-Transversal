# Pro01: Projecte Transversal ASIXc1 - Innovate Tech 🚀

[cite_start]Este repositorio contiene la documentación técnica y el código de configuración correspondientes al **Proyecto Transversal** del CFGS Administració de Sistemes Informàtics en Xarxa (Curs 2025/2026).

[cite_start]El proyecto nace de la necesidad de **Innovate Tech**, una empresa dedicada a la provisión de servicios tecnológicos, de modernizar su capacidad operativa y comunicativa, integrando la gestión de personal con servicios multimedia avanzados[cite: 7, 8].

## 👥 Integrantes del Grupo
* [cite_start]**Nombre del grupo de trabajo:** `pro-asixc1[Grupo]-[GrupDeTreball]` (Ejemplo: `pro-asixcla-g1`) 
* **Miembros:**
  * Josué Amador([@UsuarioGitHub](https://github.com/ITB2526-JosueAmador))
  * Caio Ganais ([@UsuarioGitHub](https://github.com/ITB2526-CaioGanais))
  * Alex Capitán ([@UsuarioGitHub](https://github.com/ITB2526-AlexCapitan))
  * Ramiro Cori ([@UsuarioGitHub](https://github.com/ITB2526-RamiroCori))

---

## 📋 Módulos Implicados
[cite_start]El proyecto integra competencias transversales de los siguientes módulos profesionales[cite: 1, 4]:
* [cite_start]**M0371 Fonaments de Maquinari** (Diseño e infraestructura de CPD y Cloud AWS)[cite: 4, 102].
* [cite_start]**M0375 Serveis de Xarxes i Internet** (Streaming multimedia de audio, vídeo y videoconferencia)[cite: 4, 103, 104].
* [cite_start]**M0377 Administració de Bases de Dades** (Diseño relacional, seguridad, roles y auditoría)[cite: 4, 90].
* [cite_start]**M1665 Digitalització Aplicada als Sectors Productius** (Sostenibilidad, ciberseguridad y transformación digital)[cite: 4].

---

## 🛠️ Componentes del Proyecto

### 1. Propuesta e Infraestructura de CPD (Sostenible y Cloud) 🏢☁️
[cite_start]Diseño e implantación de un Centro de Procesamiento de Datos eficiente que garantice la continuidad de negocio con soluciones enfocadas a la sostenibilidad[cite: 9, 22].
* [cite_start]**Ubicación Física e Infraestructura IT:** Planificación de la climatización, salas camufladas, distribución de cableado (falso suelo/techo), estructuración de racks y cálculo de autonomía mediante SAIs[cite: 24, 25, 26, 30].
* [cite_start]**Arquitectura en la Nube (AWS):** Implementación de una infraestructura con al menos 4 servicios desplegados en instancias independientes[cite: 34, 37]:
  * [cite_start]Servicio Web corporativo[cite: 35].
  * [cite_start]Servicio de transferencia de ficheros seguro (SFTP) autenticado con Directorio Activo[cite: 35, 36].
  * [cite_start]Servicio de Directorio Activo para la gestión centralizada de usuarios[cite: 37].
  * [cite_start]Servicio de centralización de logs de auditoría de todos los equipos[cite: 36].
* [cite_start]**Automatización con Ansible:** Aprovisionamiento y configuración automatizada de (como mínimo) dos de las máquinas del entorno[cite: 38].
* [cite_start]**Seguridad:** Acceso exclusivo mediante par de claves pública/privada y administración con usuario específico (prohibido usuarios por defecto)[cite: 39].

### 2. Servicios Multimedia y Pruebas de Ancho de Banda 🎙️📺
[cite_start]Despliegue de tecnologías estándar para la comunicación interna de los departamentos de la empresa (Ventas, Soporte Técnico, Administración y Logística) y canales externos para clientes[cite: 40, 44, 73].
* [cite_start]**Servicio de Audio:** Servidor de streaming operativo en formatos digitales estándar (MP3, AAC, OGG) con acceso directo vía navegador web[cite: 47, 48].
* [cite_start]**Servicio de Vídeo:** Streaming multimedia mediante protocolos RTMP/HLS y codecs H.264/MP4 utilizando servidores dedicados (NGINX, Jellyfin o equivalente)[cite: 54, 55].
* [cite_start]**Videoconferencia:** Sistema corporativo basado en WebRTC a través de la herramienta Jitsi Meet para llamadas internas y soporte de clientes[cite: 56, 83].
* [cite_start]**Auditoría de Rendimiento:** Pruebas y análisis de ancho de banda (Download, Upload y Latencia) simulando entornos de concurrencia de servicios para evaluar la viabilidad de la red[cite: 63, 65, 66].

### 3. Diseño e Implementación de Base de Dades (Seguridad y Auditoría) 📊🔒
[cite_start]Modelado e implementación de un sistema relacional en un SGBD para la gestión organizativa interna y registros de uso multimedia[cite: 13, 77, 101].
* [cite_start]**Estructura:** Gestión de Empleados (DNI, datos personales) y Departamentos correspondientes[cite: 81, 82].
* [cite_start]**Gestión de Comunicaciones:** Control de usuarios del sistema de comunicación, estado de actividad, enlaces de videoconferencia y configuraciones de calidad QoS según el ancho de banda del cliente[cite: 85, 86, 88].
* [cite_start]**Control de Acceso Relacional (RBAC):** Creación e implementación estricta de usuarios y roles diferenciados (`admin`, `vendes`, `administracio`, etc.) con privilegios SQL debidamente restringidos[cite: 90, 91, 93].
* [cite_start]**Automatización y Auditoría mediante Triggers:** * Control de cuotas de minutos mensuales y cantidad diaria de llamadas por usuario[cite: 94, 95].
  * [cite_start]Generación de una tabla de avisos para registrar logs de auditoría ante intentos de modificación no autorizados en tablas sensibles[cite: 96, 97].

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
