# Administración Segura y Hardening de Servicios (SSH)

En este laboratorio, cambiamos el rol de "atacante" a "administrador de sistemas". El objetivo fue configurar un acceso remoto seguro entre dos dispositivos en una red híbrida (Cable vs. Wi-Fi) y aplicar técnicas de robustecimiento (Hardening) para proteger el servidor.

## 🎯 Objetivos del Laboratorio
1. Configurar y desplegar un servidor **SSH (Secure Shell)** en Kali Linux.
2. Establecer una conexión remota desde una estación de trabajo externa (Portátil física).
3. Analizar la seguridad del protocolo mediante la captura de tráfico.
4. Aplicar técnicas de **Hardening** cambiando los parámetros por defecto del servicio.

## 🛠️ Entorno de Red
* **Servidor (Kali Linux):** Conexión vía Ethernet (Cable).
* **Cliente (Portátil):** Conexión vía Wi-Fi.
* **Interconectividad:** Validada mediante protocolos ICMP (Ping) y SSH a través del Router local.

## 🔍 Fase 1: Análisis de Tráfico (Wireshark)
A diferencia de los protocolos analizados en los días 7 y 8, SSH cifra la comunicación desde el inicio. 

* **Observación:** En Wireshark, el flujo entre la IP de la portátil (Origen) y la IP de Kali (Destino) muestra paquetes de tipo `Encrypted Packet`.
* **Resultado:** Al realizar un *Follow TCP Stream*, la información es totalmente ilegible, protegiendo tanto las credenciales como los comandos ejecutados (ls, top, etc.).



## 🛡️ Fase 2: Hardening (Fortalecimiento)
Para mejorar la seguridad, se modificó la configuración por defecto del demonio SSH (`sshd_config`):

1. **Cambio de Puerto:** Se migró del puerto estándar `22` al puerto personalizado `2222`.
   * *Razón:* Mitigar ataques de fuerza bruta automatizados que escanean puertos comunes.
2. **Comando de acceso actualizado:** `ssh -p 2222 usuario@IP_DE_KALI`

## 📊 Conclusiones
* El uso de **SSH** es indispensable para la administración remota, garantizando la confidencialidad frente a ataques de intercepción (MITM).
* La seguridad no solo depende del protocolo, sino de la configuración proactiva (cambio de puertos, gestión de accesos).
* Se validó con éxito la comunicación entre diferentes medios físicos (Red híbrida).

---
*Documentado por íkkii - Ruta de Ciberseguridad 2026*
