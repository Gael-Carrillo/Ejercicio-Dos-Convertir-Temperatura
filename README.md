# Ejercicio 2 – API Conversor de Temperaturas

API REST desarrollada con Python y Flask que convierte temperaturas entre las escalas Celsius y Fahrenheit.

---

## Requisitos

- Python 3.8 o superior
- pip

---

## Instalación

### 1. Clonar o descargar el proyecto

```bash
git clone <url-del-repositorio>
cd ejercicio2
```

### 2. Crear y activar el entorno virtual

```bash
python -m venv venv
```

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / Mac:**
```bash
source venv/bin/activate
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

---

## Ejecución

```bash
python app.py
```

El servidor se iniciará en: `http://127.0.0.1:5001`

---

## Fórmulas de conversión

| Conversión | Fórmula |
|---|---|
| Celsius → Fahrenheit | `(°C × 9/5) + 32` |
| Fahrenheit → Celsius | `(°F − 32) × 5/9` |

---

## Endpoint

### `POST /convertir-temperatura`

Convierte un valor de temperatura entre Celsius y Fahrenheit.

**URL:** `http://127.0.0.1:5001/convertir-temperatura`

**Headers:**
```
Content-Type: application/json
```

**Body (JSON):**
```json
{
  "valor": 100,
  "escala": "Celsius"
}
```

> El campo `escala` acepta: `"Celsius"` o `"Fahrenheit"` (sin distinguir mayúsculas/minúsculas).

**Respuesta exitosa – Celsius a Fahrenheit (200):**
```json
{
  "valor_original": 100,
  "escala_origen": "Celsius",
  "resultado": 212.0,
  "escala_destino": "Fahrenheit"
}
```

**Respuesta exitosa – Fahrenheit a Celsius (200):**
```json
{
  "valor_original": 32,
  "escala_origen": "Fahrenheit",
  "resultado": 0.0,
  "escala_destino": "Celsius"
}
```

**Respuesta de error – datos faltantes (400):**
```json
{
  "error": "Se requiere 'valor' (número) y 'escala' (Celsius o Fahrenheit)"
}
```

**Respuesta de error – escala inválida (400):**
```json
{
  "error": "Escala inválida. Use 'Celsius' o 'Fahrenheit'"
}
```

---

## Prueba con Postman

1. Abrir Postman
2. Crear una nueva petición
3. Seleccionar método: **POST**
4. Ingresar la URL: `http://127.0.0.1:5001/convertir-temperatura`
5. En la pestaña **Body** → seleccionar **raw** → elegir **JSON**
6. Pegar uno de los siguientes ejemplos:

**Celsius → Fahrenheit:**
```json
{
  "valor": 100,
  "escala": "Celsius"
}
```

**Fahrenheit → Celsius:**
```json
{
  "valor": 32,
  "escala": "Fahrenheit"
}
```

7. Hacer clic en **Send**

---

## Casos de prueba sugeridos

| Valor | Escala origen | Resultado esperado | Escala destino |
|---|---|---|---|
| 0 | Celsius | 32.0 | Fahrenheit |
| 100 | Celsius | 212.0 | Fahrenheit |
| 37 | Celsius | 98.6 | Fahrenheit |
| 32 | Fahrenheit | 0.0 | Celsius |
| 212 | Fahrenheit | 100.0 | Celsius |
| -40 | Celsius | -40.0 | Fahrenheit |

---

## Estructura del proyecto

```
ejercicio2/
│
├── venv/               # Entorno virtual (no se sube al repositorio)
├── app.py              # Código principal de la API
├── requirements.txt    # Dependencias del proyecto
├── .gitignore          # Archivos ignorados por Git
└── README.md           # Este archivo
```

---

## Tecnologías utilizadas

- [Python](https://www.python.org/)
- [Flask](https://flask.palletsprojects.com/)


## Prueba en Postman

![Prueba Postman](imagenes/pruebas.png)