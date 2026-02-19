# TelecomX — Analisis de Churn de Clientes

Proyecto de analisis exploratorio de datos orientado a comprender los factores que llevan a la cancelacion del servicio (churn) en TelecomX. El trabajo forma parte del challenge de Data Science para LATAM y cubre el ciclo completo de ETL, analisis exploratorio, visualizacion e informe de conclusiones.

---

## Descripcion del problema

TelecomX enfrenta una tasa de cancelacion significativa entre sus clientes. Identificar los perfiles y comportamientos asociados al abandono permite al equipo de Data Science avanzar hacia modelos predictivos y al area comercial disenar estrategias de retencion mas efectivas.

---

## Estructura del repositorio

```
├── TelecomX_LATAM-IzzatFalco.ipynb   # Notebook principal con todo el analisis
├── TelecomX_Data.json     # Dataset de clientes (fuente: API del repositorio)
└── README.md
```

---

## Pipeline de trabajo

### 1. Extraccion
Los datos se obtienen directamente desde la API del repositorio en formato JSON y se convierten a un DataFrame de pandas mediante `json_normalize` para aplanar la estructura anidada.

### 2. Transformacion
- Renombre de columnas al español
- Conversion de tipos de datos (`cargo_total` a numerico)
- Imputacion de nulos con la mediana
- Eliminacion de duplicados
- Encoding binario de variables Yes/No a 1/0
- Creacion de `cargo_diario` (cargo mensual / 30)
- Creacion de `total_servicios` (suma de servicios adicionales contratados)

### 3. Analisis exploratorio
- Estadisticas descriptivas: media, mediana, desviacion estandar, coeficiente de variacion, asimetria y curtosis
- Distribucion de la variable churn
- Tasa de cancelacion por variables categoricas: tipo de contrato, metodo de pago, servicio de internet, genero, adulto mayor, factura digital
- Distribucion de variables numericas comparada entre clientes activos y cancelados
- Analisis de churn segun cantidad de servicios adicionales contratados
- Matriz de correlacion y ranking de variables por correlacion con el churn

---

## Principales hallazgos

- La tasa de churn general es de aproximadamente el 26%.
- Los clientes con contrato mes a mes tienen una tasa de cancelacion cercana al 43%, frente al 11% de contratos anuales y 3% de bianuales.
- Los usuarios de fibra optica cancelan en mayor proporcion (aprox. 42%) que los de DSL (aprox. 19%).
- El cheque electronico es el metodo de pago con mayor churn (aprox. 45%).
- La mayoria de las cancelaciones ocurren en los primeros meses de contrato.
- A mayor cantidad de servicios adicionales contratados, menor tasa de churn.

---

## Tecnologias utilizadas

- Python 3
- pandas
- numpy
- matplotlib
- seaborn
- requests

---

## Como ejecutar el proyecto

1. Clonar el repositorio:
```bash
git clone https://github.com/tu-usuario/tu-repo.git
```

2. Instalar las dependencias:
```bash
pip install pandas numpy matplotlib seaborn requests
```

3. Abrir el notebook:
```bash
jupyter notebook TelecomX_LATAM.ipynb
```

El notebook descarga los datos automaticamente desde la API al ejecutar la primera celda, por lo que no es necesario tener el archivo JSON de forma local.

---

## Fuente de datos

API del challenge: [TelecomX_Data.json](https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json)
