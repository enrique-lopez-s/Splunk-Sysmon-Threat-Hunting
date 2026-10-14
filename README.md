# 🛡️ Splunk Sysmon Threat Hunting

Este proyecto documenta el análisis de logs de **Sysmon** en **Splunk Enterprise** para la detección proactiva de amenazas mapeadas en la matriz **MITRE ATT&CK**.

---

## 📊 Dashboards & Threat Hunting Visualizations

### 1. Detección de Ejecución de PowerShell (T1059.001)
Este panel monitorea las ejecuciones de comandos de PowerShell e interfaces de gestión (`appcmd.exe`, `pwsh.exe`) capturadas por Sysmon (**EventID 1**).

* **Filtro SPL:**
  ```spl
  index=sysmon_attack powershell 
  | table _time, host, EventID, CommandLine, User
  | sort - _time
