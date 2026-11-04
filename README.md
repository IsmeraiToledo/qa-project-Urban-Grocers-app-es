# 🛒 Urban Grocers
### Automatización de pruebas de API · QA Engineering · TripleTen

Validación del campo `name` al crear kits para un usuario mediante pruebas automatizadas con **Python y pytest**.

**9 casos de prueba** · **Autenticación con token** · **Valores límite**

---

## 🎯 Objetivo

Comprobar cómo responde la API de Urban Grocers al crear kits con nombres válidos e inválidos.

Las pruebas cubren límites de longitud, caracteres especiales, espacios, dígitos, ausencia del campo y tipos de datos incorrectos.

## 🛠️ Herramientas y técnicas

- **Python y pytest:** automatización de pruebas.
- **API Testing:** envío de solicitudes y validación de respuestas HTTP y JSON.
- **Análisis de valores límite:** nombres de 0, 1, 511 y 512 caracteres.
- **Clases de equivalencia:** datos válidos, inválidos y campo ausente.
- **Token de autenticación:** creación de kits asociados a un usuario.

## 🔎 Cobertura de pruebas

| Caso | Dato utilizado | Respuesta esperada |
|---|---|---|
| Longitud mínima válida | 1 carácter | HTTP `201` |
| Longitud máxima válida | 511 caracteres | HTTP `201` |
| Nombre vacío | 0 caracteres | HTTP `400` |
| Encima del máximo | 512 caracteres | HTTP `400` |
| Caracteres especiales | `'№%@",'` | HTTP `201` |
| Espacios | `" A Aaa "` | HTTP `201` |
| Dígitos como texto | `"123"` | HTTP `201` |
| Campo ausente | Sin `name` | HTTP `400` |
| Tipo de dato incorrecto | Número `123` | HTTP `400` |

### Comprobaciones adicionales

- **Casos positivos:** el nombre del kit devuelto por la API debe coincidir exactamente con el enviado.
- **Casos negativos:** la respuesta debe tener el estado HTTP `400`.

## 🔐 Preparación de cada prueba

1. Preparar los datos del kit.
2. Crear un usuario mediante la API.
3. Obtener su `authToken`.
4. Enviar la solicitud de creación del kit con ese token.
5. Comprobar el código HTTP y, en los casos positivos, el nombre devuelto.

## 👩‍💻 Mi contribución

Implementé nueve pruebas para validar el campo `name` durante la creación de kits.

Organicé funciones auxiliares para preparar los datos, obtener el token de un nuevo usuario y comprobar las respuestas de los casos positivos y negativos.

## 📂 Estructura del proyecto

| Archivo | Función |
|---|---|
| `create_kit_name_kit_test.py` | Pruebas del nombre del kit y funciones auxiliares |
| `sender_stand_request.py` | Funciones para enviar solicitudes a la API |
| `data.py` | Datos utilizados para usuarios y kits |
| `configuration.py` | Configuración de conexión al servidor |

## ▶️ Cómo ejecutar las pruebas

### 1. Clonar el repositorio

```bash
git clone https://github.com/IsmeraiToledo/qa-project-Urban-Grocers-app-es.git
cd qa-project-Urban-Grocers-app-es
```

### 2. Instalar las dependencias

```bash
pip install pytest requests
```

### 3. Configurar el entorno

Actualizar la dirección del servidor en `configuration.py`.

El servidor de Urban Grocers debe estar activo y accesible para crear usuarios y kits.

### 4. Ejecutar las pruebas

```bash
pytest -v create_kit_name_kit_test.py
```

## 📋 Alcance y resultados

La suite contiene **9 casos automatizados** centrados en la validación del nombre de los kits.

La tabla muestra las respuestas esperadas según las comprobaciones implementadas. Los resultados obtenidos deben confirmarse ejecutando las pruebas contra un servidor activo.

---

Desarrollado por **Ismerai Toledo Contreras** durante su formación en QA Engineering en **TripleTen**.
