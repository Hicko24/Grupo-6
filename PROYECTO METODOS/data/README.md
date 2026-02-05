
# Carpeta de Datos
Esta carpeta contiene el archivo de datos original utilizado en el desarrollo del proyecto. Este dataset corresponde a partidas clasificatorias del videojuego League of Legends, obtenidas a partir de la API oficial de Riot Games.

## Archivos

- league_data_etapa1_limpio_equipo.csv  
  Dataset filtrado y limpiado a nivel equipo–partida.  
  Este archivo se utiliza como entrada para los análisis posteriores.

- league_data_etapa2_estadisticos.csv  
  Tabla de estadística descriptiva que incluye media, desviación estándar,
  valores mínimos, máximos y cuartiles para las variables numéricas.

- league_data_etapa3_normalizado.csv  
  Dataset con las variables numéricas normalizadas mediante el método
  Z-score, listo para análisis y modelado posteriores.

## Observación
Los archivos reflejan la evolución del preprocesamiento y análisis de los
datos a lo largo del proyecto.

## Uso del dataset

Los archivos almacenados en esta carpeta fue utilizado como fuente primaria de información para:

- La etapa de análisis y limpieza de datos.
- La selección de variables de macrojuego.
- La formulación del modelo predictivo basado en métodos numéricos.
- Se recomienda no modificar el archivo original, ya que todas las transformaciones y limpiezas fueron realizadas a nivel de código, preservando la integridad de los datos fuente.