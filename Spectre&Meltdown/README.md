# Laboratorio de Ataques Spectre y Meltdown

Este repositorio contiene el código fuente y las instrucciones para realizar ataques de canal lateral conocidos como **Spectre** y **Meltdown**. Este proyecto fue desarrollado como parte de la asignatura **Técnicas de Hacking**, donde se proporcionó código base para realizar prácticas y entender el funcionamiento de estos ataques a bajo nivel.

---

## 📁 Estructura del Proyecto

El proyecto está organizado en las siguientes carpetas:

- **`kernel_module/`**: Contiene el módulo del kernel necesario para el ataque Meltdown.
- **`meltdown/`**: Programas de usuario que implementan variantes del ataque Meltdown.
- **`spectre/`**: Programas de usuario que implementan variantes del ataque Spectre.
- **`utils/`**: Utilidades auxiliares para medir tiempos de acceso a caché, manejar excepciones, etc.

---

## 📂 Contenido de las Carpetas

### `kernel_module/`
- `MeltdownKernel.c`: Código fuente del módulo del kernel que expone datos secretos a través de `/proc/secret_data`.
- `Makefile`: Script para compilar el módulo usando las herramientas del kernel.
- `.gitignore`: Para evitar subir archivos generados automáticamente.

### `meltdown/`
- `MeltdownExperiment.c`: Demostración básica del ataque Meltdown.
- `MeltdownAttack.c`: Versión más robusta y precisa del ataque.

### `spectre/`
- `SpectreExperiment.c`: Demostración básica del ataque Spectre.
- `SpectreAttack.c`: Implementación inicial del ataque.
- `SpectreAttackImproved.c`: Versión mejorada con repetición y puntuación.

### `utils/`
- `CacheTime.c`: Mide tiempos de acceso a memoria para detectar caché.
- `ExceptionHandling.c`: Manejo de excepciones con señales.
- `FlushReload.c`: Implementación de la técnica Flush+Reload.

---

## ⚙️ Instrucciones de Compilación y Ejecución

### Módulo del Kernel

```bash
cd kernel_module/
make
sudo insmod MeltdownKernel.ko
dmesg | tail  # Ver dirección del secreto
cat /proc/secret_data
sudo rmmod MeltdownKernel
```

### Programas de Usuario

```bash
gcc -o ataque ataque.c
./ataque
```

> Reemplaza `ataque.c` por el archivo que quieras ejecutar (por ejemplo, `MeltdownAttack.c`, `SpectreAttackImproved.c`, etc.).

---

## ⚠️ Advertencia

Estos programas están diseñados **exclusivamente con fines educativos** y deben ejecutarse en **entornos controlados** (máquinas virtuales o sistemas de laboratorio). No deben utilizarse en sistemas de producción ni contra equipos sin autorización.
