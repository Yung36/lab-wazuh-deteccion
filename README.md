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
# Laboratory: Intrusion Detection with Wazuh SIEM

## 1. General Information
* **Date:** 2026-06-16
* **Author:** Yung36
* **Objective:** Validate brute-force SSH attack detection capabilities using Wazuh SIEM.

## 2. Ethical and Legal Framework
* This laboratory was performed in a controlled virtualization environment.
* Simulated intrusion techniques were executed exclusively against proprietary resources, complying with cybersecurity ethics protocols and academic practice supervision guidelines.

## 3. Laboratory Objective
* Implement and verify communication between a security agent (Kali Linux) and a centralized manager (Wazuh).
* Identify SSH brute-force attacks through log analysis and event correlation.

## 4. Topology and Environment
* **Wazuh Manager:** Centralized server (Dashboard accessible via Web on Windows 11).
* **Agent:** Kali Purple (Kali Linux).
* **Agent IP:** 10.0.2.15.
* **Tools:** Wazuh Agent v4.14.5, OpenSSH Server, Journalctl.

## 5. Methodology
* **5.1 Preparation Phase:** Verification of agent-server communication via `/var/ossec/bin/wazuh-control info` and service status.
* **5.2 Execution Phase (Simulation):** Activation of SSH service on the agent and execution of failed authentication attempts with non-existent credentials.
* **5.3 Analysis Phase (Detection):** Log correlation in the Wazuh Dashboard identifying rule IDs 5710 and 2502.

## 6. Results and Evidence

### 6.1 Preparation Phase
Verification of the operational status of the agent on the system.
[Agent Status]<img width="432" height="110" alt="2026-06-16_13-32" src="https://github.com/user-attachments/assets/820bc23e-91d5-4ae0-a5d5-cf30db071402" />

### 6.2 Execution Phase (Simulation)
SSH brute-force attack simulation, generating authentication failure logs.
[Brute Force Attempt]<img width="645" height="341" alt="2026-06-16_13-41" src="https://github.com/user-attachments/assets/6b0fe82a-0e94-4dc3-85bc-fe459d13ec6e" />

### 6.3 Analysis Phase (Detection)
Wazuh Dashboard visualization showing event correlation and severity scale (Level 10).
[Wazuh Detection]<img width="1275" height="217" alt="2026-06-16_15-01" src="https://github.com/user-attachments/assets/bb90870b-67bb-406d-9b38-02627a932e90" />

## 7. Conclusions and Remediation
* **Conclusions:** The effectiveness of the SIEM in escalating incidents was demonstrated. Monitoring authentication logs is critical for detecting brute-force attacks.
* **Remediation:**
    1. Disable password authentication on SSH (use *Public Key Authentication*).
    2. Implement *Fail2Ban* for automatic IP blocking after failed attempts.
    3. Change the default port 22 to a non-standard one to reduce noise in the logs.

## 8. References
* Wazuh Documentation. (2026). *Wazuh agent deployment and rule set*. https://documentation.wazuh.com
* OpenSSH Security Best Practices. (2026). *Hardening and configuration guides*.

