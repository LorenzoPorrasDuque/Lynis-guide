# Uso de Lynis

## Comandos básicos

La sintaxis general de Lynis es:

```bash
lynis <comando> [opciones]
```

El comando más utilizado es `audit system`, que ejecuta una auditoría completa del sistema local.

---

## Auditoría del sistema

### Auditoría completa (recomendada)

```bash
sudo lynis audit system
```

Este comando ejecuta todos los módulos de prueba disponibles y genera un reporte completo.

### Auditoría sin interacción (modo no interactivo)

Útil para scripts automáticos o pipelines CI/CD:

```bash
sudo lynis audit system --non-interactive
```

### Auditoría en modo rápido (omite pausas)

```bash
sudo lynis audit system --quick
```

### Auditoría sin colores en la salida

```bash
sudo lynis audit system --no-colors
```

---

## Auditar un sistema remoto (via SSH)

```bash
# Lynis se copia temporalmente al sistema remoto y ejecuta el escaneo
lynis audit system --remote user@192.168.1.100
```

---

## Auditar una imagen Docker

```bash
# Primero monta el sistema de archivos de la imagen
docker export $(docker create nombre-imagen) | tar -C /tmp/imagen -xf -

# Luego ejecuta Lynis sobre el directorio raíz exportado
sudo lynis audit system --rootdir /tmp/imagen
```

---

## Opciones útiles

| Opción | Descripción |
|---|---|
| `--auditor "Nombre"` | Especifica el nombre del auditor en el reporte |
| `--cronjob` | Modo para ejecución en cron (no interactivo + salida reducida) |
| `--logfile /ruta/lynis.log` | Especifica la ruta del archivo de log |
| `--no-log` | No genera archivo de log |
| `--pentest` | Modo pentesting (algunos tests adicionales de seguridad ofensiva) |
| `--profile /ruta/perfil.prf` | Usa un perfil de configuración personalizado |
| `--tests "TEST-ID-001 TEST-ID-002"` | Ejecuta solo los tests especificados |
| `--skip-plugins` | Omite la ejecución de plugins |
| `--verbose` | Muestra información adicional durante el escaneo |
| `--warnings-only` | Solo muestra advertencias y problemas encontrados |

---

## Entendiendo la salida del escaneo

### Pantalla durante el escaneo

Durante la ejecución, Lynis muestra el progreso con indicadores de estado:

```
[+] System tools
------------------------------------
  - Scanning available tools...
  - Checking system binaries...

[+] Plugins (phase 1)
------------------------------------
 Note: plugins have more extensive tests and may take more time to complete
  - Plugin: pam
      [..]

[+] Boot and services
------------------------------------
  - Service manager                                           [ systemd ]
  - Checking UEFI boot                                        [ DISABLED ]
  - Checking presence GRUB2                                   [ FOUND ]
```

Los indicadores más comunes son:

| Indicador | Significado |
|---|---|
| `[ OK ]` | Configuración correcta y segura |
| `[ WARNING ]` | Problema de seguridad que debe atenderse |
| `[ SUGGESTION ]` | Mejora recomendada, no crítica |
| `[ FOUND ]` | Elemento encontrado/detectado |
| `[ NOT FOUND ]` | Elemento no encontrado |
| `[ DISABLED ]` | Característica deshabilitada |
| `[ ENABLED ]` | Característica habilitada |

### Resumen final

Al finalizar el escaneo, Lynis muestra un resumen:

```
================================================================================
  Lynis security scan details:

  Hardening index : [65]          [#############       ]
  Tests performed : 283
  Plugins enabled : 2

  Components:
  - Firewall               [V]
  - Malware scanner        [X]

  Lynis modules:
  - Compliance status      [?]
  - Security audit         [V]
  - Vulnerability scan     [V]

  Files:
  - Test and debug information      : /var/log/lynis.log
  - Report data                     : /var/log/lynis-report.dat
================================================================================
```

---

## Revisando el reporte

### Archivo de log (`lynis.log`)

Contiene el detalle completo del escaneo, incluyendo los comandos ejecutados y sus resultados:

```bash
# Ver el log completo
sudo cat /var/log/lynis.log

# Filtrar solo las advertencias
sudo grep "Warning" /var/log/lynis.log

# Filtrar sugerencias
sudo grep "Suggestion" /var/log/lynis.log
```

### Archivo de reporte (`lynis-report.dat`)

Contiene datos estructurados del escaneo, útiles para integración con otras herramientas:

```bash
# Ver el reporte
sudo cat /var/log/lynis-report.dat

# Ver solo advertencias del reporte
sudo grep "^warning" /var/log/lynis-report.dat

# Ver el índice de hardening
sudo grep "hardening_index" /var/log/lynis-report.dat
```

---

## Automatización con cron

Para ejecutar Lynis automáticamente de forma periódica:

```bash
# Editar el crontab de root
sudo crontab -e
```

Agregar una línea para ejecutar el escaneo diariamente a las 3:00 AM:

```cron
0 3 * * * /usr/bin/lynis audit system --cronjob --logfile /var/log/lynis-$(date +\%Y\%m\%d).log
```

> **Nota:** En crontab, el carácter `%` debe escaparse como `\%`. El ejemplo anterior es correcto para su uso directo en un archivo crontab.
```

---

## Perfiles de configuración

Lynis permite usar perfiles personalizados para adaptar el comportamiento del escaneo:

```bash
# Usar un perfil personalizado
sudo lynis audit system --profile /etc/lynis/custom.prf
```

Ejemplo de archivo de perfil (`custom.prf`):

```ini
# Definir el nombre del auditor
auditor=Equipo de Seguridad

# Omitir tests específicos
skip-test=BOOT-5122
skip-test=FILE-6310

# Definir la ruta del reporte
report-file=/var/log/lynis-custom-report.dat

# Activar modo verbose
verbose=yes
```

---

## Consejos de uso

1. **Ejecutar siempre como root o con sudo** – Un escaneo sin privilegios omite muchas comprobaciones críticas.
2. **Guardar los reportes** – Mantén un historial de escaneos para comparar la evolución de la seguridad.
3. **Priorizar las advertencias** – Las advertencias (`WARNING`) deben atenderse antes que las sugerencias (`SUGGESTION`).
4. **Aplicar cambios gradualmente** – Implementa las recomendaciones de forma incremental y verifica que no afecten los servicios.
5. **Combinar con otras herramientas** – Lynis complementa herramientas como OpenVAS, Nessus o Nikto para una auditoría más completa.

---

Volver a:
- [Cómo funciona Lynis](how-it-works.md)
- [Inicio](README.md)
