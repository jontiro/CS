# Instalación de Python

Guía para instalar Python en diferentes sistemas operativos.

## Windows

### Método 1: Instalador oficial

1. Visita [python.org](https://www.python.org/downloads/)
2. Descarga el instalador para Windows
3. Ejecuta el instalador
4. **IMPORTANTE**: Marca la casilla "Add Python to PATH"
5. Click en "Install Now"
6. Espera a que termine la instalación

### Verificación

```bash
python --version
pip --version
```

## macOS

### Método 1: Homebrew (Recomendado)

```bash
# Instalar Homebrew si no lo tienes
# Visita https://brew.sh/ para más información
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar Python
brew install python
```

### Método 2: Instalador oficial

1. Visita [python.org](https://www.python.org/downloads/)
2. Descarga el instalador para macOS
3. Ejecuta el .pkg descargado
4. Sigue las instrucciones del instalador

## Linux (Ubuntu/Debian)

```bash
# Actualizar repositorios
sudo apt update

# Instalar Python 3
sudo apt install python3 python3-pip

# Verificar instalación
python3 --version
pip3 --version
```

## Configuración de Entorno Virtual

Es una buena práctica usar entornos virtuales:

```bash
# Crear entorno virtual
python -m venv mi_entorno

# Activar entorno virtual
# Windows:
mi_entorno\Scripts\activate
# macOS/Linux:
source mi_entorno/bin/activate

# Desactivar entorno virtual
deactivate
```

## Instalación de Paquetes

```bash
# Instalar un paquete
pip install nombre_paquete

# Instalar desde requirements.txt
pip install -r requirements.txt

# Listar paquetes instalados
pip list

# Crear requirements.txt
pip freeze > requirements.txt
```

## Problemas Comunes

### Windows: "python no se reconoce como comando"

**Solución**: Agregar Python al PATH manualmente
1. Buscar "Variables de entorno" en el menú inicio
2. Agregar la ruta de instalación de Python al PATH

### macOS: Conflicto entre Python 2 y Python 3

**Solución**: Usar alias en `.zshrc` o `.bash_profile`
```bash
alias python=python3
alias pip=pip3
```

## Editores Recomendados

- Visual Studio Code + extensión Python
- PyCharm
- Jupyter Notebook
- Sublime Text
