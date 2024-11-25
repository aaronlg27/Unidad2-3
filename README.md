# Unidad2-3
Sistema de Gestión de Usuarios con Aseguramiento de Calidad
Descripción del Proyecto
Este proyecto implementa un sistema de gestión de usuarios que incluye funcionalidades como creación, eliminación, inicio de sesión y actualización de perfiles. Se aplicaron herramientas y prácticas de aseguramiento de calidad del software, como pruebas unitarias, integración continua (CI/CD) y análisis estático, para garantizar su robustez y mantenibilidad.

Características Principales
Crear usuarios: Registra nuevos usuarios, asegurando que no existan duplicados.
Eliminar usuarios: Elimina usuarios del sistema.
Inicio de sesión: Verifica credenciales para autenticación.
Actualizar perfil: Permite modificar datos del usuario, excepto el correo electrónico.
Estructura del Proyecto
El proyecto sigue una estructura organizada y profesional:


Unidad2-3/
├── app/
│   ├── __init__.py
│   ├── user_management.py         # Código principal del sistema
├── tests/
│   ├── __init__.py
│   ├── test_user_management.py    # Pruebas unitarias con Pytest
├── .github/
│   ├── workflows/
│   │   ├── ci.yml                 # Configuración de GitHub Actions
├── requirements.txt               # Dependencias necesarias
├── README.md                      # Documentación del proyecto
├── sonar-project.properties       # Configuración de SonarCloud

Tecnologías Utilizadas
Lenguaje: Python 3.12
Pruebas: Pytest
CI/CD: GitHub Actions
Análisis Estático: SonarCloud
Control de Versiones: Git y GitHub

Instalación

1. Clonar el Repositorio
Clona el repositorio en tu máquina local:
git clone https://github.com/tu_usuario/Unidad2-3.git
cd Unidad2-3

2. Crear y Activar un Entorno Virtual
Crea un entorno virtual para gestionar las dependencias:
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

3. Instalar Dependencias
Instala las dependencias del proyecto:
pip install -r requirements.txt

Ejecución

1. Ejecutar las Pruebas
Para verificar el funcionamiento del sistema, ejecuta las pruebas unitarias:
pytest -v

2. Ver Análisis de Cobertura
Si has configurado SonarCloud, el pipeline CI/CD generará un análisis estático y mostrará métricas de calidad directamente en el tablero de SonarCloud.

Automatización con GitHub Actions
El proyecto incluye un pipeline de CI/CD configurado en GitHub Actions para:

Ejecutar las pruebas automáticamente con cada commit o pull request.
Analizar la calidad del código con SonarCloud.
Garantizar que los cambios cumplen con los estándares de calidad antes de ser fusionados.
Pruebas Unitarias
Se implementaron 5 pruebas unitarias para cubrir los casos funcionales y de límites del sistema:

Crear un usuario válido.
Detectar usuarios duplicados.
Manejar inicio de sesión con credenciales incorrectas.
Detectar intentos de actualizar el correo electrónico (no permitido).
Manejar eliminación de usuarios inexistentes.
Diagramas del Sistema
Diagrama de Clases

+-----------------------+
|      UserManagement    |
+-----------------------+
| - users: dict         |
+-----------------------+
| + create_user(email: str, password: str) -> str     |
| + delete_user(email: str) -> str                   |
| + login(email: str, password: str) -> str          |
| + update_profile(email: str, **kwargs: dict) -> str|
+-----------------------+

            |
            |
            v
+-----------------------+
|      User             |
+-----------------------+
| - email: str          |
| - password: str       |
+-----------------------+
| + __init__(email: str, password: str)                |
| + set_password(password: str) -> None                |
| + update_data(key: str, value: str) -> None           |
+-----------------------+

Diagrama de Arquitectura

+---------------------+        +-----------------------+
|  Frontend (Cliente) | <----> |   Backend (API)       |
+---------------------+        +-----------------------+
                                   |
                                   v
                           +--------------------+
                           | UserManagement     |
                           | (Controlador de    |
                           |  lógica del sistema)|
                           +--------------------+
                                   |
                                   v
                        +---------------------+
                        |  Database (In-Memory)|
                        |  Users (users dict)  |
                        +---------------------+

