# Scesi-Postulation
_Scesi postulation 2026_
_Trabajo individual_
_Mateo Fabian Gonzales Jimenez_
__
---

# Apuntes Completos de Git & GitHub

##  Clase 1: Introducción y Configuración
### ¿Qué es Git?
Git es un **MVC (Model Version Control)** o Sistema de Control de Versiones.
Es una herramienta que realiza seguimiento a los cambios de los archivos a lo largo del tiempo, permitiendo:
* Revertir a versiones anteriores.
* Colaborar con otros desarrolladores.
* Gestionar diferentes ramas de código.

### Historia de Git
* **1990:** Primeras herramientas que son RCS y CVS.
* **2005:** Linus Torvalds crea Git.
  ![Linus meme](Linuseadas/xsdtv.jpg)
* **2008:** Lanzamiento de GitHub.
* **2018:** Microsoft adquiere GitHub.

### Instalación y Configuración Inicial
* **Descarga:** [git-scm.com](https://git-scm.com/install/)
* **Linux (Arch/EndevourOS (My os)):** `sudo pacman -S git`
* **Verificación:** `git --version`

#### Comandos de configuración global:
| Comando | Descripción |
| :--- | :--- |
| `git config --global user.name "Tu Nombre"` | Configura un nombre de usuario |
| `git config --global user.email "tu@correo.com"` | Configura un correo electrónico |
| `git config --global core.autocrlf true` | Maneja finales de línea automáticamente |

---

## Clase 2: Estados, Flujo de Trabajo y Commits
Git gestiona los archivos a través de tres áreas principales:

### 1. Directorio de Trabajo
Donde creas o modificas archivos.
* **Untracked:** Archivos nuevos que Git aún desconoce.
* **Modified:** Archivos que Git ya rastrea pero han sido modificados.
* **Comando:** `git restore <archivo>` descarta cambios y vuelve al estado original.


### 2. Stage Area
El área de espera para los archivos que quieres incluir en el siguiente "punto de guardado".
* **Agregar:** `git add <archivo>` o `git add .` para todo.
* **Quitar de Stage:** `git restore --staged <archivo>`.

### 3. Repositorio Local (Committed)
Donde se guarda el historial definitivo.
* **Crear commit:** `git commit -m "mensaje"`
* **Modificar último commit:** `git commit --amend`
* **Deshacer último commit:** `git reset --soft HEAD~1` mantiene los cambios en stage.

### El archivo `.gitignore`
Sirve para listar archivos o carpetas que Git debe ignorar o no rastrear.
* `*.log`: Ignora todos los archivos de registro.
* `node_modules/`: Ignora carpetas de dependencias.
* `secrets.env`: Ignora archivos con credenciales.

### Buenas Prácticas de Commits
* **Frecuencia:** Hacer commits pequeños y atómicos o sea un cambio lógico a la vez.
* **Mensajes:** Máximo 50 caracteres, sin punto final, usando verbos imperativos `Add`, `Fix`, `Remove`.
* **Prefijos Semánticos:**
    * `feat`: Nueva funcionalidad.
    * `fix`: Corrección de errores.
    * `docs`: Documentación.
    * `refactor`: Mejora de código sin cambiar funcionalidad.
    * `perf`: Mejoras de rendimiento.

---

## Clase 3: GitHub y Conexión Remota
### ¿Qué es GitHub?
Es una plataforma en la nube la "red social de programadores" que permite alojar repositorios de Git y colaborar con otros.

### Protocolos de Conexión
1. **HTTPS:** Fácil de usar, pero requiere autenticación frecuente o token personal.
    ![HTTPS-Info](Linuseadas/Httpssecureprotocol.jpg)
3. **SSH:** Usa claves criptográficas. Más seguro y profesional; no pide contraseña tras la configuración inicial.
    ![SSH-Reference](Linuseadas/descripcion-del-protocolo-ssh.webp)
5. **CLI (gh):** Herramienta de línea de comandos de GitHub para mayor productividad.
    ![Linus meme](Linuseadas/cli(gh).jpg)

### Configuración SSH
1. **Generar:** `ssh-keygen -t ed25519 -C "correo@ejemplo.com"`
2. **Verificar clave pública:** `cat ~/.ssh/id_ed25519.pub`
3. **Vincular:** Copiar el contenido en *Settings > SSH keys* en GitHub.
4. **Probar:** `ssh -T git@github.com`

### Conectar Local con Remoto
Si ya tienes un proyecto local:
```bash
git remote add origin <url-del-repo>
git branch -M main
git push -u origin main
```

---

## Clase 4: Remotos Avanzados y Múltiple SSH
### Gestión de Remotos
* `git remote -v`: Ver conexiones actuales.
* `git remote set-url origin <nueva-url>`: Cambiar la dirección del repositorio remoto.

### Configuración de Múltiples Cuentas SSH
Para usar una cuenta de trabajo y una personal en la misma PC, se edita el archivo `~/.ssh/config`:
```text
Host github-personal
    HostName github.com
    IdentityFile ~/.ssh/id_ed25519_personal

Host github-trabajo
    HostName github.com
    IdentityFile ~/.ssh/id_ed25519_trabajo
```

### Jerarquía de Configuración
1. **Local:** `--local` Solo el repositorio actual. **Mayor prioridad.**
2. **Global:** `--global` Para el usuario del sistema.
3. **System:** Para todos los usuarios de la máquina.

---
## Clase 5: Ramas, Navegación y Gitflow
### Ramas
Permiten crear "universos alternos" para probar funciones sin romper la rama principal (`main`).
* **Crear y cambiar:** `git switch -c <nombre-rama>` o `git checkout -b <nombre-rama>`.
* **Cambiar a rama existente:** `git switch <nombre>` o `git checkout <nombre>`.

### Navegación por Commits
* **Ver historial:** `git log --oneline`.
* **Viajar al pasado:** `git checkout <id-commit>`.
    * **Detached HEAD:** Ocurre cuando apuntas a un commit y no a una rama. Para guardar cambios aquí, usa `git checkout -b nueva-rama`.
* **Regresar definitivamente:** `git reset --hard <id-commit>`.

### Gitflow
* **Ramas Principales:** `main` producción y `develop` desarrollo.
* **Ramas Secundarias:** `feature/` nuevas funciones, `release/` preparar versiones y `hotfix/` arreglos urgentes.

### Sincronización
* **Pull:** `git pull origin <rama>` Baja cambios y los fusiona.
* **Push:** `git push origin <rama>` Sube tus commits.

---
