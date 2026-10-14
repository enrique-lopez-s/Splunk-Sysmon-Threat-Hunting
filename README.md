# 🛡️ Splunk & Sigma Threat Hunting Portfolio

Portafolio profesional de Threat Hunting enfocado en el análisis de telemetría de **Sysmon**, modelado de amenazas con **MITRE ATT&CK**, desarrollo de reglas analíticas en **Splunk (SPL)** y estandarización multiplataforma mediante **Sigma**.

---

## 🛠️ Entorno y Tecnologías
* **SIEM / Motor de Análisis:** Splunk Enterprise (ejecutándose en Linux Mint).
* **Dataset de Pruebas:** Muestras de eventos de Sysmon (`EVTX-ATTACK-SAMPLES`) cargadas en el índice `sysmon_attack`.
* **Control de Versiones:** Git (Flujo de trabajo mediante línea de comandos).

---

## 📊 1. Dashboards & Threat Visualizations

### Detección de Ejecución de PowerShell (T1059.001)
Monitoreo de procesos y comandos sospechosos de PowerShell capturados por Sysmon (**EventID 1**).
* **Consulta SPL:**
  ```spl
  index=sysmon_attack powershell 
  | table _time, host, EventID, CommandLine, User
  | sort - _time
