# Instalación de Lynis

Lynis no requiere instalación en el sentido tradicional. Puede ejecutarse directamente desde el directorio donde se descargó. Sin embargo, hay varias formas de obtenerlo dependiendo de tu sistema operativo.

---

## Método 1: Desde el repositorio oficial de GitHub (recomendado)

Esta es la forma más directa de obtener siempre la última versión de Lynis.

```bash
# Clonar el repositorio
git clone https://github.com/CISOfy/lynis

# Entrar al directorio
cd lynis

# Verificar que el script es ejecutable
chmod +x lynis

# Ejecutar Lynis (requiere root o sudo para escaneo completo)
sudo ./lynis audit system
```

> **Ventaja:** Siempre tendrás la versión más actualizada. Para actualizar, simplemente ejecuta `git pull`.

---

## Método 2: Descarga directa del tarball

```bash
# Descargar la última versión
# Reemplaza "3.x.x" con la versión actual que encuentres en:
# https://github.com/CISOfy/lynis/releases
wget https://downloads.cisofy.com/lynis/lynis-3.x.x.tar.gz

# Verificar la integridad del archivo (recomendado)
sha256sum lynis-3.x.x.tar.gz

# Extraer el archivo
tar -xzf lynis-3.x.x.tar.gz

# Entrar al directorio
cd lynis

# Ejecutar Lynis
sudo ./lynis audit system
```

---

## Método 3: Gestor de paquetes del sistema

### Debian / Ubuntu

```bash
# Opción A: Repositorio oficial de CISOfy (versión más actualizada)
sudo apt-get install apt-transport-https

wget -O - https://packages.cisofy.com/keys/cisofy-software-public.key | sudo apt-key add -

echo "deb https://packages.cisofy.com/community/lynis/deb/ stable main" | \
  sudo tee /etc/apt/sources.list.d/cisofy-lynis.list

sudo apt-get update
sudo apt-get install lynis

# Opción B: Repositorio de Ubuntu/Debian (puede ser versión antigua)
sudo apt-get install lynis
```

### Red Hat / CentOS / Fedora / Rocky Linux

```bash
# Opción A: Repositorio oficial de CISOfy
wget -O /etc/yum.repos.d/cisofy-lynis.repo \
  https://packages.cisofy.com/community/lynis/rpm/cisofy-lynis.repo

sudo yum install lynis
# o con dnf:
sudo dnf install lynis
```

### macOS (con Homebrew)

```bash
brew install lynis
```

### FreeBSD / OpenBSD / NetBSD

```bash
# FreeBSD
pkg install lynis

# OpenBSD
pkg_add lynis
```

### Arch Linux / Manjaro

```bash
sudo pacman -S lynis
```

---

## Verificación de la instalación

Una vez instalado, verifica que Lynis funciona correctamente:

```bash
# Verificar la versión instalada
lynis show version

# Ver información del sistema y configuración
lynis show settings

# Realizar una comprobación rápida de integridad
lynis show dbdir
```

Salida esperada:

```
[ Lynis 3.x.x ]
```

---

## Actualización de Lynis

### Si instalaste desde GitHub

```bash
cd lynis
git pull
```

### Si instalaste desde un gestor de paquetes

```bash
# Debian/Ubuntu
sudo apt-get update && sudo apt-get upgrade lynis

# RHEL/CentOS/Fedora
sudo yum update lynis
# o
sudo dnf update lynis

# macOS
brew upgrade lynis
```

---

## Estructura de archivos de Lynis

Tras la instalación o descarga, encontrarás la siguiente estructura:

```
lynis/
├── lynis              # Script principal ejecutable
├── db/                # Base de datos de tests y definiciones
├── include/           # Módulos de prueba por categoría
├── plugins/           # Plugins adicionales
├── extras/            # Archivos extra y utilidades
└── README.md          # Documentación básica
```

Archivos generados tras un escaneo:

```
/var/log/lynis.log           # Log detallado del escaneo
/var/log/lynis-report.dat    # Reporte estructurado con datos del escaneo
```

---

Continúa con:
- [Uso de Lynis](usage.md)
- [Cómo funciona](how-it-works.md)
