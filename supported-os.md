# Sistemas operativos soportados

Lynis se ejecuta en prácticamente todos los sistemas basados en UNIX, independientemente de la versión. Su diseño modular y sin dependencias externas hace que sea compatible con una enorme variedad de plataformas.

---

## Sistemas operativos compatibles

| Sistema operativo | Notas |
|---|---|
| **AIX** | IBM AIX, todas las versiones principales |
| **FreeBSD** | FreeBSD y derivados |
| **HP-UX** | Hewlett-Packard UNIX |
| **Linux** | Todas las distribuciones principales (Debian, Ubuntu, RHEL, CentOS, Arch, etc.) |
| **macOS** | Sistemas Apple macOS (anteriormente OS X) |
| **NetBSD** | NetBSD y derivados |
| **NixOS** | Distribución Linux basada en Nix |
| **OpenBSD** | OpenBSD y derivados |
| **Solaris** | Oracle Solaris |
| **Otros** | Cualquier sistema UNIX-like con shell compatible |

---

## Dispositivos especiales

Lynis no solo funciona en servidores y estaciones de trabajo tradicionales. También ha sido probado y funciona correctamente en:

- **Raspberry Pi** – Dispositivos de computación de bajo costo.
- **Dispositivos IoT** – Sistemas embebidos con Linux u otros UNIX.
- **Dispositivos de almacenamiento QNAP** – NAS con sistemas operativos propietarios basados en Linux.
- **Contenedores Docker** – Imágenes Linux en entornos containerizados.
- **Máquinas virtuales** – Cualquier VM que ejecute un sistema UNIX-based.

---

## Distribuciones Linux verificadas

Las siguientes distribuciones de Linux han sido verificadas específicamente con Lynis:

- Ubuntu / Debian
- Red Hat Enterprise Linux (RHEL)
- CentOS / Rocky Linux / AlmaLinux
- Fedora
- SUSE / openSUSE
- Arch Linux / Manjaro
- Alpine Linux
- Kali Linux
- Parrot OS
- NixOS

---

## Requisitos mínimos

| Requisito | Detalle |
|---|---|
| **Shell** | `bash`, `sh`, `ksh` o cualquier shell POSIX compatible |
| **Privilegios** | Puede ejecutarse sin root, pero un escaneo completo requiere `sudo` o root |
| **Espacio en disco** | < 10 MB para los archivos de Lynis |
| **Memoria RAM** | Mínima – Lynis es extremadamente ligero |
| **Conexión a internet** | No requerida para el escaneo básico |

> **Nota:** Lynis funciona mejor con privilegios de root o sudo.

---

Continúa con:
- [Cómo funciona Lynis](how-it-works.md)
- [Instalación](installation.md)
