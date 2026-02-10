# GNS3 – Multivendor Network Monitoring with Cacti and Nagios

## Descripción
Proyecto de laboratorio desarrollado en GNS3 que simula una red pequeña
multivendor (Cisco y MikroTik), incorporando monitoreo de red mediante
Cacti y Nagios desde un servidor Ubuntu.

El objetivo del laboratorio es practicar diseño de red, conectividad,
y monitoreo de infraestructura TI en un entorno similar a uno real.

## Topología de red
La topología está compuesta por:

- Router principal Cisco 7200 (R1)
- Router MikroTik RB450G (R2)
- Router Cisco 7200 (R3)
- Switches MikroTik CRS326
- Hosts finales en dos redes LAN
- Servidor Ubuntu para monitoreo (Cacti y Nagios)

![Network Topology](topology/gns3-topology.jpg)

## Direccionamiento IP
- Red de monitoreo: `10.10.0.0/24`
- Enlaces punto a punto:
  - R1 ↔ R2: `10.10.1.0/30`
  - R1 ↔ R3: `10.10.2.0/30`
- LAN 1: `192.168.1.0/24`
- LAN 2: `192.168.2.0/24`

## Tecnologías y herramientas
- GNS3
- Cisco IOS (7200)
- MikroTik RouterOS
- Ubuntu Server
- Cacti
- Nagios
- ICMP
- SNMP

## Monitoreo implementado
### Cacti
- Monitoreo de tráfico de interfaces
- Recolección de métricas vía SNMP
- Visualización de uso de ancho de banda

### Nagios
- Monitoreo de disponibilidad de routers y hosts
- Verificación de conectividad (ping)
- Detección de caídas de dispositivos

## Funcionalidades
- Monitoreo centralizado desde servidor Ubuntu
- Supervisión de dispositivos multivendor
- Validación de conectividad entre segmentos
- Detección básica de fallos de red

