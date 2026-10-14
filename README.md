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

---

## 🗺️ 2. Matriz de Cobertura MITRE ATT&CK

| Táctica | Técnica | Subtécnica | Evento Sysmon | Regla SPL | Regla Sigma | Playbook |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Execution** | T1059 | T1059.001 (PowerShell) | EventID 1 | `queries/soc_detections.spl` | `sigma/powershell_suspicious.yml` | `docs/playbook_powershell.md` |
| **Persistence** | T1547 | T1547.001 (Registry Run Keys) | EventID 13 | `queries/soc_detections.spl` | `sigma/registry_persistence.yml` | `docs/playbook_persistencia.md` |
| **Command and Control** | T1071 | T1071.001 (Web Protocols) | EventID 3 | `queries/soc_detections.spl` | — | — |

---

## 📚 3. Documentación y Playbooks de Respuesta
* [SOC Playbook: Detección de PowerShell](docs/playbook_powershell.md)
* [SOC Playbook: Persistencia en Registro](docs/playbook_persistencia.md)
