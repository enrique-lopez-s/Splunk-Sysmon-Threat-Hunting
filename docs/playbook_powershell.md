# 📖 SOC Playbook: Detección de PowerShell Sospechoso (T1059.001)

## 1. Descripción de la Alerta
* **Nombre:** Ejecución de PowerShell con parámetros de evasión.
* **Severidad:** Alta.
* **Origen de Telemetría:** Sysmon EventID 1 (Process Creation).

---

## 2. Flujo de Investigación para el Analista

1. **Verificar el comando ejecutado (`CommandLine`):**
   * Buscar flags comunes de evasión: `-nop`, `-w hidden`, `-encodedcommand`, `downloadstring`.
2. **Analizar el Proceso Padre (`ParentImage`):**
   * ¿Fue lanzado por un usuario en consola (`explorer.exe`, `cmd.exe`) o por un servicio expuesto (`w3wp.exe`, `sqlserver.exe`)?
3. **Inspeccionar la Red (Sysmon EventID 3):**
   * Filtrar por el `ProcessId` para verificar si estableció conexiones hacia IPs externas desconocidas.

---

## 3. Acciones de Mitigación
* Aislar la máquina de la red si se confirma descarga de artefactos no autorizados.
* Revocar sesiones del usuario involucrado si se sospecha compromiso de credenciales.
