# Predicción de la Presencia de Artistas en Playlists Editoriales de Spotify

Proyecto final del curso DataXperience, 4to semestre, Universidad EAN.

## Pregunta principal

¿Qué tan precisamente puede un modelo de regresión, entrenado con las características de artistas
destacados en playlists editoriales de Spotify en Estados Unidos (seguidores, oyentes mensuales, género,
antigüedad) y los audio features de sus tracks, medidos entre el 1 de abril y el 9 de mayo de 2024, estimar
en cuántas playlists editoriales distintas aparecerá un artista que el modelo no vio durante el
entrenamiento?

## Estructura del repositorio

La carpeta `informe/` contiene el informe final del proyecto. La carpeta `presentacion/` tiene las diapositivas de la sustentación. La carpeta `notebook/` contiene `Spotify_Proyecto_Final.ipynb`, el cuaderno de Google Colab con el código completo: carga, diagnóstico, limpieza, normalización, EDA y modelo de regresión. La carpeta `data/` contiene los datasets originales (`dirty_spotify_artists_facil.csv`, `dirty_spotify_tracks_facil.csv`) y los generados por el notebook (`artist_limpio.csv`, `track_limpio.csv`, `tabla_modelo.csv`).

## Cómo ejecutar el notebook

1. Abrir `notebook/Spotify_Proyecto_Final.ipynb` en Google Colab.
2. Ejecutar las celdas en orden (Entorno de ejecución → Ejecutar todas).
3. La primera celda de código pide subir `dirty_spotify_artists_facil.csv` y `dirty_spotify_tracks_facil.csv`
   (están en `data/`). El notebook no depende de Google Drive: todo corre dentro de la sesión de Colab.

## Origen de los datos

Derivados (ensuciados a propósito para el ejercicio de limpieza) del dataset
[Featured Spotify artists/tracks with metadata](https://www.kaggle.com/datasets/sarahjeffreson/featured-spotify-artiststracks-with-metadata)
(Kaggle, sarahjeffreson).

## Resumen de resultados

- **Limpieza:** Artists 21,270 → 20,130 filas (5.4% eliminado); Tracks 15,811 → 14,341 filas (9.3% eliminado).
- **Hallazgo principal:** `monthly_listeners` es la variable que mejor predice la presencia en playlists
  editoriales (correlación 0.68), muy por encima de los audio features de las canciones (todos por debajo
  de 0.09).
- **Modelo final: Lasso (alpha=0.05).** Comparado contra regresión lineal y Ridge, iguala su desempeño en
  validación cruzada (R² = 0.483 vs. 0.498) usando solo 7 de las 27 variables. Sobre los artistas de test:
  RMSE = 0.893 playlists, MAE = 0.561 playlists, R² = 0.424.

## Equipo

Juan Sebastian Bonilla Urrego, Juan Andrés López Forero, Sael Andres Velasquez Torres, Helen Julieth Suarez Rodriguez
