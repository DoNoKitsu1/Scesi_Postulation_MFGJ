# Scesi-Postulation
_Scesi postulation 2026_
_Mateo Fabian Gonzales Jimenez_
---

# Apuntes Completos de Git & GitHub

##  Clase 1: Introducción y Configuración
### ¿Qué es Git?
Git es un **MVC (Model Version Control)** o Sistema de Control de Versiones. Es una herramienta que realiza un seguimiento de los cambios en los archivos a lo largo del tiempo, permitiendo:
* Revertir a versiones anteriores.
* Colaborar con otros desarrolladores.
* Gestionar diferentes ramas de código.

### Historia de Git
* **1990:** Primeras herramientas (RCS y CVS).
* **2005:** Linus Torvalds crea Git para el kernel de Linux.
  ![Linus meme](Linuseadas/xsdtv.jpg)
* **2008:** Lanzamiento de GitHub (inicialmente en Ruby).
* **2018:** Microsoft adquiere GitHub.
* **2025:** GitHub lidera con funciones de IA.

### Instalación y Configuración Inicial
* **Descarga:** [git-scm.com](https://git-scm.com/install/)
* **Linux (Arch/CachyOS):** `sudo pacman -S git`
* **Verificación:** `git --version`

#### Comandos de configuración global:
| Comando | Descripción |
| :--- | :--- |
| `git config --global user.name "Tu Nombre"` | Configura tu nombre de usuario |
| `git config --global user.email "tu@correo.com"` | Configura tu correo electrónico |
| `git config --global core.autocrlf true` | Maneja finales de línea automáticamente |

---

## Clase 2: Estados, Flujo de Trabajo y Commits
Git gestiona los archivos a través de tres áreas principales:

### 1. Directorio de Trabajo (Modified)
Donde creas o modificas archivos.
* **Untracked:** Archivos nuevos que Git aún no conoce.
* **Modified:** Archivos que Git ya rastrea pero han sido cambiados.
* **Comando:** `git restore <archivo>` (descarta cambios y vuelve al estado original).


### 2. Stage Area
El área de espera para los archivos que quieres incluir en el siguiente "punto de guardado".
* **Agregar:** `git add <archivo>` o `git add .` (para todo).
* **Quitar de Stage:** `git restore --staged <archivo>`.

### 3. Repositorio Local (Committed)
Donde se guarda el historial definitivo (Checkpoint).
* **Crear commit:** `git commit -m "mensaje"`
* **Modificar último commit:** `git commit --amend`
* **Deshacer último commit:** `git reset --soft HEAD~1` (mantiene los cambios en stage).

### El archivo `.gitignore`
Sirve para listar archivos o carpetas que Git debe ignorar (no rastrear).
* `*.log`: Ignora todos los archivos de registro.
* `node_modules/`: Ignora carpetas de dependencias.
* `secrets.env`: Ignora archivos con credenciales.

### Buenas Prácticas de Commits
* **Frecuencia:** Hacer commits pequeños y atómicos (un cambio lógico a la vez).
* **Mensajes:** Máximo 50 caracteres, sin punto final, usando verbos imperativos (`Add`, `Fix`, `Remove`).
* **Prefijos Semánticos:**
    * `feat`: Nueva funcionalidad.
    * `fix`: Corrección de errores.
    * `docs`: Documentación.
    * `refactor`: Mejora de código sin cambiar funcionalidad.
    * `perf`: Mejoras de rendimiento.
