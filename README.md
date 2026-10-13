Splunk-Sysmon-Threat-Hunting
🛡️ Splunk & Sysmon Threat Hunting Lab (MITRE ATT&CK)

Splunk Sysmon MITRE ATT&CK Linux Mint
📌 Descripción del Proyecto

Este proyecto documenta un entorno práctico de Threat Hunting y Análisis de Logs de Seguridad utilizando Splunk Enterprise sobre Linux Mint y telemetría avanzada de Microsoft Sysmon.

A través del análisis de datasets reales de ciberataques (EVTX-ATTACK-SAMPLES por Samir Bousseaden), se desarrollaron e implementaron consultas analíticas en SPL (Splunk Processing Language) orientadas a la identificación de técnicas adversarias mapeadas en el marco MITRE ATT&CK.
🎯 Casos de Uso y Cobertura MITRE ATT&CK
Caso de Uso 	ID MITRE 	Técnica / Táctica 	Telemetría Sysmon
PowerShell Sospechoso 	T1059.001 	Execution: PowerShell con bypass de políticas y encodificación Base64 	Event ID 1 (Process Creation)
Persistencia en Registro 	T1547.001 	Persistence: Modificación de claves de inicio automático (Run/Services) 	Event ID 12/13 (Registry Modification)
Conexiones C2 de Red 	T1071 	Command & Control: Procesos de sistema (powershell/cmd) abriendo tráfico saliente 	Event ID 3 (Network Connection)
🏗️ Arquitectura del Laboratorio

    SIEM / Engine: Splunk Enterprise 9.4.0 instalado localmente en entorno Linux Mint.
    Dataset: Ingesta e indexación de telemetría de eventos Sysmon/Windows (evtx_data.csv).
    Análisis: Desarrollo de reglas analíticas SPL y paneles de monitoreo.

