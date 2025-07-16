# Desafío técnico: API de Cajero Automático

Este esqueleto de proyecto está preparado en **Django 5.2 + Django REST Framework 3.16**.

El objetivo es construir una API que permita simular un cajero automático.

## 🚀 Requisitos

- [Python 3.10+](https://www.python.org/downloads/)
- [pip](https://pip.pypa.io/)
- (Recomendado) [Virtualenv](https://docs.python.org/3/library/venv.html)
- [Docker](https://www.docker.com/) (para levantar PostgreSQL)

## 📦 Instalación

```bash
# Clonar el proyecto
git clone https://github.com/correcto-com/backend-assignment.git
cd bank-api-challenge

# Crear entorno virtual
python3 -m venv venv        # macOS/Linux
py -m venv .venv            # Windows

# Activar entorno virtual
source venv/bin/activate    # macOS/Linux
.venv\Scripts\activate       # Windows

# Instalar dependencias
pip install -r requirements.txt
```

## 🎯 Objetivo de la prueba:
El reto consiste en implementar una API REST que simule las operaciones básicas de un cajero automático, siguiendo estas especificaciones:

### Endpoints a implementar

1. **Depositar dinero**
   - Debe actualizar el saldo.
   - Recibe un payload con la cantidad de dinero a ingresar.
   - Endpoint: `POST /api/deposit/`
   - **Payload JSON:**

   ```json
   {
   "amount": 100.50
   }
   ```

2. **Retirar dinero**
   - Debe retirar el saldo que se le indique, si es posible.
   - Recibe un payload con la cantidad a retirar.
   - Endpoint: `POST /api/withdraw/`
   - **Payload JSON:**

   ```json
   {
   "amount": 100.50
   }
   ```

3. **Consultar saldo**
   - Devuelve el saldo actual de la cuenta.
   - Endpoint: `GET /api/balance/`
   - **Payload JSON:**

   ```json
   {}
   ```

## ⚙️ Configuración del entorno
Para levantar la base de datos y conectar con el proyecto necesitas un archivo .env en la raíz del proyecto con las siguientes variables de entorno:

```bash
cp .env.example .env
```

## 🐘 Base de datos con Docker
Para levantar PostgreSQL localmente, asegúrate de tener [Docker instalado](https://www.docker.com/).

```bash
# Para levantar el docker con la base de datos ejecuta:
docker-compose up -d

# Verificar que el contenedor esté ejecutándose
docker ps

# Ver logs del contenedor
docker logs bank-api-database
```

#### Detener la base de datos

```bash
# Para detener la base de datos ejecuta:
docker-compose down
```

## 🚀 Ejecutar el proyecto

Una vez que tengas la base de datos corriendo, sigue estos pasos para iniciar el servidor de desarrollo:

```bash
# Asegúrate de que tu entorno virtual esté activado
source venv/bin/activate    # macOS/Linux
.venv\Scripts\activate       # Windows

# Ejecutar las migraciones de la base de datos
python manage.py migrate

# Crear un superusuario (opcional, para acceder al admin de Django)
python manage.py createsuperuser

# Iniciar el servidor de desarrollo
python manage.py runserver

# Abre tu navegador y accede al panel de administración de Django en:
http://localhost:8000/admin/

# Podrás iniciar sesión con el superusuario que creaste anteriomente.
```