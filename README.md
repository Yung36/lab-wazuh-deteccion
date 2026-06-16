**Idiomas/Languages:** [Español](#español) | [English](#english)

<a name="español"></a>
## 🇪🇸 Versión en Español

# Laboratorio: Detección de Intrusiones con Wazuh SIEM

## 1. Información General
* **Fecha:** 2026-06-16
* **Autor:** Yung36
* **Objetivo:** Validar la capacidad de detección de ataques de fuerza bruta SSH mediante el SIEM Wazuh.

## 2. Marco Ético y Legal
* Este laboratorio se realizó en un entorno de virtualización controlado.
* Las técnicas de intrusión simuladas se ejecutaron exclusivamente contra recursos propios, cumpliendo con los protocolos de ética en ciberseguridad y las guías de supervisión de prácticas académicas.

## 3. Objetivo del Laboratorio
* Implementar y verificar la comunicación entre un agente de seguridad (Kali Linux) y un gestor centralizado (Wazuh).
* Identificar, mediante el análisis de logs y correlación de eventos, un ataque de fuerza bruta SSH.

## 4. Topología y Entorno
* **Wazuh Manager:** Servidor centralizado (Dashboard accesible vía Web en Windows 11).
* **Agente:** Kali Purple (Kali Linux).
* **IP Agente:** 10.0.2.15.
* **Herramientas:** Wazuh Agent v4.14.5, OpenSSH Server, Journalctl.

## 5. Metodología
* **5.1 Fase de Preparación:** Verificación de la comunicación agente-servidor mediante `/var/ossec/bin/wazuh-control info` y estado del servicio.
* **5.2 Fase de Ejecución (Simulación):** Activación del servicio SSH en el agente y ejecución de intentos de autenticación fallidos con credenciales inexistentes.
* **5.3 Fase de Análisis (Detección):** Correlación de logs en el Dashboard de Wazuh identificando los IDs de regla 5710 y 2502.

## 6. Resultados y Evidencias

### 6.1 Fase de Preparación
Verificación del estado operativo del agente en el sistema.
[Estado del Agente]<img width="432" height="110" alt="2026-06-16_13-32" src="https://github.com/user-attachments/assets/820bc23e-91d5-4ae0-a5d5-cf30db071402" />
### 6.2 Fase de Ejecución (Simulación)
Simulación de ataque de fuerza bruta SSH, generando registros de fallos de autenticación.
[Intento de Fuerza Bruta]<img width="645" height="341" alt="2026-06-16_13-41" src="https://github.com/user-attachments/assets/6b0fe82a-0e94-4dc3-85bc-fe459d13ec6e" />
### 6.3 Fase de Análisis (Detección)
Visualización del Dashboard de Wazuh mostrando la correlación de eventos y la escala de severidad (Nivel 10).
[Detección en Wazuh]<img width="1275" height="217" alt="2026-06-16_15-01" src="https://github.com/user-attachments/assets/bb90870b-67bb-406d-9b38-02627a932e90" />

## 7. Conclusiones y Remediación
* **Conclusiones:** Se demostró la eficacia del SIEM para escalar incidentes. La monitorización de logs de autenticación es crítica para la detección de ataques de fuerza bruta.
* **Remediación:**
    1. Deshabilitar autenticación por contraseña en SSH (usar *Public Key Authentication*).
    2. Implementar *Fail2Ban* para bloqueo automático de IPs tras intentos fallidos.
    3. Cambiar el puerto 22 a uno no estándar para reducir el ruido en los logs.

## 8. Referencias
* Wazuh Documentation. (2026). *Wazuh agent deployment and rule set*. https://documentation.wazuh.com
* OpenSSH Security Best Practices. (2026). *Hardening and configuration guides*.

-----------------------------------------------------------------------------------------------------------------------
<a name="english"></a>
## 🇺🇸 English Version


