# 🚀 Proyecto Final SIS313  
## Sistema de Salas de Espera y Filas Virtuales (Virtual Queue)

**Asignatura:** SIS313: Infraestructura, Plataformas Tecnológicas y Redes  
**Semestre:** 2/2025  
**Docente:** Ing. Marcelo Quispe Ortega  

---

# 👥 Miembros del Equipo (Grupo “Virtual Queue”)

| Nombre Completo                     | Rol en el Proyecto                                                                 | Contacto                    |
|-------------------------------------|-------------------------------------------------------------------------------------|------------------------------|
| Duran Chambi Benjamin Ricardo       | Arquitecto de Backend & Proxy • Encargado de VM-PROXY y VM-APP                     | —                            |
| Escobar Moscoso Jorge Gabriel       | Administrador de Datos • Encargado de la VM-REDIS                                  | https://github.com/jogaesmo  |
| Onofre Alanoca Roy                  | Ingeniero de Observabilidad • Encargado de VM-MON                                   | https://github.com/RoyOnofre |

---

# 🎯 I. Objetivo del Proyecto
Diseñar e implementar una arquitectura de **Cola Virtual** que gestione saturación de usuarios para SUNiver mediante:

- Rate Limiting
- Sala de espera HTML
- Redis en RAM para contadores atómicos
- Proxy reverso Nginx entre clientes y servidores
- Observabilidad con Prometheus + Grafana

---

# 🎯 II. Justificación  
Garantizar estabilidad del sistema SUNiver evitando caída del servicio durante la inscripción mediante una sala de espera inteligente.

---

# 🛠️ III. Tecnologías Utilizadas

- **Nginx** (Proxy, Rate Limiting)
- **Node.js** (Lógica de cola)
- **Redis** (Contadores en RAM)
- **Prometheus/Grafana** (Monitoreo RED)
- **Tailscale / Avahi** (.local)
- **Systemd** (Arranque automático)

---

# 🌐 IV. Infraestructura del Proyecto

| VM | Rol | Hostname | Software |
|----|-----|----------|----------|
| VM-PROXY | Gateway | proxy-server.local | Nginx |
| VM-APP | Lógica de cola | app-server.local | Node.js |
| VM-REDIS | Estado global | redis-server.local | Redis |
| VM-MON | Observabilidad | monitor-server.local | Prometheus/Grafana |

---

# ⚙️ V. Implementación Completa Paso a Paso

---

# 🔧 **Parte 0 – Configuración Base (Todas las VMs)**

```bash
sudo apt update
sudo apt install -y net-tools curl avahi-daemon libnss-mdns
