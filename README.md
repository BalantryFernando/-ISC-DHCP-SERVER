# Práctica: Servidor DHCP y Agente de Retransmisión 🚀

Este repositorio contiene la documentación y el informe final de la práctica de Servicios de Red e Internet, centrada en la configuración avanzada del servicio DHCP en un entorno Linux (Debian 11).

El objetivo del proyecto es implementar una infraestructura de red robusta donde un único servidor **`isc-dhcp-server`** es capaz de asignar configuraciones IP a múltiples subredes.

La parte clave de la práctica es la implementación de un **`isc-dhcp-relay`** (Agente de Retransmisión), que permite al servidor DHCP centralizado dar servicio a una red remota a la que no tiene acceso directo.

---

## 📄 Documentación Completa

El informe completo de la práctica, con todas las capturas de pantalla, explicaciones detalladas, configuraciones de red, análisis de paquetes con `dhcpdump` y conclusiones, se encuentra en el siguiente documento PDF:

**➡️ [Ver PDF: Configuración del servidor ISC-DHCP-SERVER.pdf](https://github.com/BalantryFernando/-ISC-DHCP-SERVER/blob/main/Configuraci%C3%B3n%20del%20servidor%20ISC-DHCP-SERVER.pdf)**

---

## Diagrama de la Topología de Red

![Diagrama de la topología de red](https://github.com/BalantryFernando/-ISC-DHCP-SERVER/blob/main/topologia.png?raw=true)

---

## 🛠️ Tecnologías Utilizadas

* **SO:** Debian 11
* **Servicios:** `isc-dhcp-server`, `isc-dhcp-relay`
* **Gestión:** `systemd` / `systemctl`
* **Redes:** Enrutamiento estático (`ip route`), `net.ipv4.ip_forward`
* **Análisis:** `dhcpdump`

## 💡 Conceptos Clave del Proyecto

* **Diferenciación Host vs. Router:** Se demuestra la diferencia clave entre un *host* (el Servidor DHCP, que solo necesita un `gateway` para enviar sus propios paquetes) y un *router* (el Relay Agent, que necesita `ip_forward=1` para reenviar tráfico ajeno).
* **Mecanismo del Agente Relay:** Análisis de cómo el `Relay Agent` utiliza el campo `GIADDR` en los paquetes DHCP para informar al servidor sobre la red de origen del cliente.
* **Enrutamiento Estático:** Configuración de rutas para permitir la comunicación entre las diferentes subredes para la gestión y el reenvío de peticiones.
