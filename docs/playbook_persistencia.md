# 📖 SOC Playbook: Persistencia en Registro de Windows (T1547.001)

## 1. Descripción de la Alerta
* **Nombre:** Modificación o creación de valores en claves de inicio automático (`Run`/`RunOnce`).
* **Severidad:** Alta.
* **Origen de Telemetría:** Sysmon EventID 12 / 13 (Registry Modification).

---

## 2. Flujo de Investigación para el Analista

1. **Identificar la Clave Afectada (`TargetObject`):**
   * Verificar si la clave pertenece a `HKLM` o `HKCU` dentro de `...\CurrentVersion\Run`.
2. **Analizar el Valor y la Ruta (`Details`):**
   * Inspeccionar la ruta del binario o ejecutable que se configuró para arrancar automáticamente.
   * Verificar la firma digital del ejecutable registrado.
3. **Inspeccionar el Proceso Creador (`Image`):**
   * Analizar qué proceso o script realizó la modificación en el registro.

---

## 3. Acciones de Mitigación
* Eliminar la entrada maliciosa del registro utilizando `reg.exe` o PowerShell.
* Poner en cuarentena o eliminar el ejecutable referenciado en el campo `Details`.
* Analizar otros hosts de la red para descarta movimiento lateral o persistencia redundante.
