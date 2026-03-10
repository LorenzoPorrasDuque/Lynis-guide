# Instalación de Lynis

Lynis no requiere instalación en el sentido tradicional. Puede ejecutarse directamente desde el directorio donde se descargó. Sin embargo, hay varias formas de obtenerlo dependiendo de tu sistema operativo.

---

## Método : Desde el repositorio oficial de GitHub (recomendado)

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
