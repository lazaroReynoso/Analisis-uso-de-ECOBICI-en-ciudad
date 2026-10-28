# Uso de EcoBici en Ciudad Universitaria (UBA)

Análisis del uso del sistema **EcoBici** del Gobierno de la Ciudad de Buenos Aires en las dos estaciones de Ciudad Universitaria:
- **Estación 420:** Ciudad Universitaria I (Pabellón 0+Infinito, FCEN)
- **Estación 464:** Ciudad Universitaria III (Pabellón III, FADU)

El proyecto recorre el procesamiento, el análisis descriptivo y exploratorio y el modelado con regresión lineal.

## Qué hice

### 1. Procesamiento
- Traducción de columnas y días al español, tratamiento de valores faltantes en el día de la semana.
- Conversión de fechas y horarios a `datetime` y creación de variables de año, mes, día, hora y estación del año.

### 2. Análisis descriptivo
- Disponibilidad de bicicletas y puertos por estación del año, por día de la semana y por hora.
- El patrón diario sigue los **turnos de cursada** (mañana, tarde y noche) de lunes a viernes, mientras que los fines de semana la curva es casi plana.
- Se detectó un valle atípico de disponibilidad a las 21 h, presente en ambas estaciones, y se analizaron posibles causas.

### 3. Análisis exploratorio
- Comparación entre las dos estaciones y evolución por mes y semana según el **calendario académico** (primer y segundo cuatrimestre).
- **Clima:** la llovizna casi no afecta el uso, pero la lluvia y las tormentas reducen los viajes de forma marcada.
- **Día de la semana:** el uso depende casi por completo de los días hábiles.

### 4. Regresión lineal
- Con un dataset de viajes diarios de toda la Ciudad, se modelaron los viajes con **origen en Plaza Italia (estación 005)**.
- Se compararon tres modelos con validación cruzada (k-fold) y RMSE. El mejor fue el más simple: predecir los viajes **desde** Plaza Italia a partir de los viajes **hacia** Plaza Italia.

## Datos
| Archivo | Contenido |
|---|---|
| `full_data.csv` | Estado de las estaciones 420 y 464 (formato GBFS), tomado del repositorio [FedeGiovannetti/Eco_bici_Ciudad_Universitaria](https://github.com/FedeGiovannetti/Eco_bici_Ciudad_Universitaria) |
| `clima.csv` | Datos de clima diario para cruzar con el uso |
| `viajes_diarios.csv` | Viajes diarios por estación de origen y destino |

Fuente original: API de transporte del GCBA (https://api-transporte.buenosaires.gob.ar).

## Cómo correrlo
```bash
pip install -r requirements.txt
jupyter notebook "EcoBicis en Ciudad.ipynb"
```

## Tecnologías
Python · pandas · NumPy · Matplotlib · Seaborn · scikit-learn · formulaic

## Autor
Lázaro Reynoso
