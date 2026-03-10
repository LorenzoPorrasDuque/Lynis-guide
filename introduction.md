# Introducción a Lynis

## ¿Qué es Lynis?

**Lynis** es una herramienta de auditoría de seguridad open-source para sistemas basados en UNIX. Realiza escaneos exhaustivos del sistema operativo y el software instalado con el fin de detectar vulnerabilidades, configuraciones inseguras y áreas de mejora en el hardening del sistema.

Lynis está desarrollado por **CISOfy** y es distribuido bajo licencia GPL. Es ampliamente utilizado por profesionales de seguridad, administradores de sistemas y auditores de TI en todo el mundo.

---

## Objetivos del proyecto

Dado que Lynis es flexible, se utiliza para varios propósitos distintos. Los casos de uso más comunes incluyen:

| Objetivo | Descripción |
|---|---|
| **Auditoría de seguridad** | Evaluar el estado de seguridad de un sistema de forma integral |
| **Pruebas de cumplimiento** | Verificar adherencia a estándares como PCI-DSS, HIPAA, SOX |
| **Pruebas de penetración** | Identificar debilidades que podrían ser explotadas por un atacante |
| **Detección de vulnerabilidades** | Descubrir software desactualizado, configuraciones inseguras y exposiciones |
| **Hardening de sistemas** | Obtener recomendaciones concretas para endurecer la configuración del sistema |

---

## Audiencia y casos de uso

Lynis es utilizado por perfiles muy distintos dentro del mundo de la seguridad informática:

### 🛠️ Desarrolladores

- Prueba la seguridad de tus imágenes Docker antes de desplegarlas.
- Mejora el hardening de tus aplicaciones web en producción.
- Integra Lynis en tu pipeline de CI/CD para auditorías continuas.

### 🖥️ Administradores de sistemas

- Ejecuta escaneos diarios de salud para descubrir nuevas debilidades.
- Mantén un historial de cambios en la postura de seguridad del sistema.
- Recibe alertas sobre configuraciones que se han vuelto inseguras con el tiempo.

### 📋 Auditores de TI

- Demuestra a colegas o clientes qué puede hacerse para mejorar la seguridad.
- Genera reportes detallados para auditorías internas y externas.
- Valida el cumplimiento de políticas de seguridad corporativas.

### 🔍 Pentesters

- Descubre debilidades de seguridad en sistemas de clientes.
- Identifica vectores de ataque que podrían resultar en compromiso del sistema.
- Complementa otras herramientas de pentesting con una perspectiva desde el sistema.

---

## ¿Por qué usar Lynis?

- **Open-source y gratuito** – Disponible para cualquier organización sin costo.
- **Sin instalación de dependencias** – No requiere instalar software adicional en el sistema objetivo.
- **Resultados accionables** – Cada hallazgo incluye sugerencias concretas de mejora.
- **Amplia comunidad** – Mantenido activamente y con una gran base de usuarios.
- **Integración sencilla** – Puede ejecutarse como parte de scripts de automatización o pipelines CI/CD.

---

Continúa con:
- [Sistemas operativos soportados](supported-os.md)
- [Cómo funciona Lynis](how-it-works.md)
- [Instalación](installation.md)
