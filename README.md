# Sistema Web de Clínica Dental con Django

## Integrantes

- Velasquez Puma Brigitte Karolay
- Ticona Nina Valeria Abigai
- Lerma Ccopa Jhonatan Javier

## Descripción del proyecto

Este proyecto consiste en el desarrollo de una aplicación web orientada a la administración de una clínica dental utilizando el framework Django.

La aplicación permite gestionar información relacionada con pacientes, administración de datos clínicos y operaciones internas mediante un panel administrativo personalizado usanto templates y views.

El sistema fue desarrollado utilizando:

- Python
- Django
- SQLite/PostgreSQL
- Django Admin
- Entorno virtual (`myvenv`)

---

# Objetivos del proyecto

- Implementar un entorno de desarrollo aislado con Python.
- Utilizar Django como framework principal.
- Administrar información mediante modelos ORM.
- Utilizar migraciones para la construcción de la base de datos.
- Aprovechar el sistema Auto CRUD integrado en Django Admin.
- Centralizar la administración de la clínica dental en una interfaz web.

---

# Estructura general del proyecto

```text
├── clinic
│   ├── __init__.py
│   ├── __pycache__
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   │   ├── 0001_initial.py
│   │   ├── __init__.py
│   │   └── __pycache__
│   ├── models
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   ├── appointment.py
│   │   ├── budget.py
│   │   ├── budget_detail.py
│   │   ├── medical_record.py
│   │   ├── patient.py
│   │   ├── payment.py
│   │   ├── procedure.py
│   │   ├── specialist.py
│   │   ├── specialty.py
│   │   └── suggested_treatment.py
│   ├── models.txt
│   ├── templates
│   │   ├── appointments
│   │   ├── budget_details
│   │   ├── budgets
│   │   ├── home.html
│   │   ├── medical_records
│   │   ├── patients
│   │   ├── payments
│   │   ├── procedures
│   │   ├── specialists
│   │   ├── specialties
│   │   └── suggested_treatments
│   ├── tests.py
│   ├── urls.py
│   ├── views
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   ├── appointment_view.py
│   │   ├── budget_detail_view.py
│   │   ├── budget_view.py
│   │   ├── home_view.py
│   │   ├── medical_record_view.py
│   │   ├── patient_view.py
│   │   ├── payment_view.py
│   │   ├── procedure_view.py
│   │   ├── specialist_view.py
│   │   ├── specialty_view.py
│   │   └── suggested_treatment_view.py
│   └── views.txt
├── config
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-311.pyc
│   │   ├── settings.cpython-311.pyc
│   │   ├── urls.cpython-311.pyc
│   │   └── wsgi.cpython-311.pyc
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── myvenv
└── requirements.txt
```

---

# Requisitos previos

Software y Version en la que fue testado

- Python 3.14.4
- pip 26.0.1
- git version 2.54.0.windows.1
- Entorno virtual de Python

---

# Instalación y ejecución del proyecto

## 1. Clonar el repositorio

```powershell
git clone https://github.com/jlerma1250/Laboratorio07
```

---

## 2. Ingresar al proyecto

```powershell
cd Laboratorio07
```

---

## 3. Crear el entorno virtual

```powershell
python -m venv myvenv
```

### ¿Qué es un entorno virtual?

Un entorno virtual permite aislar las dependencias de Python utilizadas en el proyecto, evitando conflictos con otras aplicaciones instaladas en el sistema.

---

## 4. Activar el entorno virtual

### PowerShell

```powershell
.\myvenv\Scripts\activate
```

### CMD

```cmd
myvenv\Scripts\activate.bat
```

### Ubuntu/dEBIAN
```bash
source myenv/bin/activate
```

---

## 5. Instalar dependencias

```powershell
pip install -r requirements.txt
```

### Archivo requirements.txt

Este archivo contiene todas las dependencias necesarias para ejecutar correctamente el proyecto.

---
## 8. Ejecutar el servidor

```powershell
python manage.py runserver
```

Por defecto, Django iniciará el servidor en:

```text
http://127.0.0.1:8000/
```

---

## Ingresar al administrador

Abrir en el navegador:

```text
http://127.0.0.1:8000/
```

Luego iniciar sesión con el superusuario creado anteriormente.

---

# Funcionalidades del Django Admin

Desde el panel administrativo es posible:

- Crear registros
- Editar información
- Eliminar datos
- Gestionar usuarios
- Administrar modelos registrados
- Consultar información almacenada

---

# Views de Django

Los View en Django representan la logica de la aplicacion, se basa en declarar funciones que posteriormente se pasara como parametro al metodo path() para indicar a django que respuesta dar, devuelve un objeto de tipo HttpResponse mediante el metodo render() de django.shortcouts

Ejemplo:

```python
def patient_list(request):
    patients = Patient.objects.all()
    return render(request, 'patients/list.html', {
        'patients': patients    
    })
```

---

# Lista urlpatterns

La lista `urlpatterns` que se encuentra en el archivo `urls.py` almacena objetos de tipo URLPattern, toma como argumento un string que esla url a la que se accedera, y como segundo parametro la funcion en si (sin las `()`)

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('clinic.urls')),
]
```
---

# Archivo .gitignore

El archivo `.gitignore` evita subir archivos innecesarios al repositorio.

Ejemplo:

```text
myvenv/
__pycache__/
db.sqlite3
```

---

# Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| Python | Lenguaje principal |
| Django | Framework web |
| SQLite/PostgreSQL | Base de datos |
| HTML | Plantillas |
| Git | Control de versiones |

---

# Posibles mejoras futuras

- Sistema de archivos estaticos (para el css)
- Mayor manejo de errores 
- Integración con PostgreSQL en producción
- Diseño responsivo
- Paneles estadísticos

---

# Conclusión

El proyecto demuestra el uso de Django como framework de desarrollo rápido para aplicaciones web administrativas.

Gracias al principio MTV, es posible construir operaciones CRUD completas con una cantidad reducida de código, facilitando la administración de la información dentro de la clínica dental.