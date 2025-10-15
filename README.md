# Poems-Eater

## Buscador de Recitaciones de Poemas Dominicanos en YouTube

**Poems-Eater** es una herramienta automatizada para buscar y catalogar videos de YouTube donde se recitan poemas de la literatura dominicana. Utiliza web scraping (sin necesidad de API key) para encontrar recitaciones, dramatizaciones y lecturas de poesía dominicana.

---

## Características Principales

 - **Sin límites de API**: Usa `scrapetube` (no requiere YouTube API key)
 - **Dataset completo**: 100+ poemas de autores dominicanos clásicos y contemporáneos
 - **Búsqueda inteligente**: Encuentra recitaciones, dramatizaciones, lecturas y performances
 - **Múltiples formatos**: Exporta resultados a Excel y CSV
 - **Búsqueda personalizable**: Configura el número de videos a buscar por poema
 - **Estadísticas detalladas**: Tasas de éxito, géneros, autores más representados

---

## Estructura del Proyecto

```
poems-eater/
├── main.py                      # Punto de entrada principal
├── requirements.txt             # Dependencias
├── README.md                    # Este archivo
├── poems_list.txt              # Lista personalizada de poemas (opcional)
├── dominican_poems.xlsx        # Resultados en Excel
├── dominican_poems.csv         # Resultados en CSV
└── src/
    ├── __init__.py
    ├── clients/
    │   ├── __init__.py
    │   └── youtube_client.py   # Cliente de YouTube (scrapetube)
    ├── models/
    │   ├── __init__.py
    │   └── poem.py             # Modelo de datos Poem
    ├── services/
    │   ├── __init__.py
    │   └── poem_service.py     # Lógica de búsqueda
    └── utils/
        ├── __init__.py
        ├── config.py           # Configuración
        ├── dominican_poems.py  # Dataset de poemas
        └── file_handler.py     # Manejo de archivos
```

---

## Instalación

### 1. Clonar o descargar el proyecto

```bash
cd poems-eater
```

### 2. Crear entorno virtual (opcional pero recomendado)

```bash
python3 -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

---

## Uso

### Modo básico (usar dataset predefinido)

```bash
python main.py
```

Esto buscará los 100+ poemas incluidos en el dataset.

### Modo con archivo personalizado

Crea un archivo `poems_list.txt` con el formato:

```
Título Poema | Autor | Año | Género
A la Patria | Salomé Ureña | 1874 | Patriótico
Niágara | José María Heredia | 1824 | Romántico
Hay un País en el Mundo | Pedro Mir | 1949 | Épico
```

Luego ejecuta:

```bash
python main.py
```

El programa detectará automáticamente el archivo.

---

## Configuración

Edita `src/utils/config.py` para personalizar:

```python
# Número de videos a buscar por poema
VIDEOS_PER_SEARCH = 3

# Archivos de salida
OUTPUT_FILE = "dominican_poems.xlsx"
OUTPUT_CSV = "dominican_poems.csv"

# Archivo de entrada (opcional)
POEMS_FILE = "poems_list.txt"
```

---

## Dataset Incluido

El dataset predefinido incluye poemas de:

### Autores Clásicos (1800-1920)
- **Salomé Ureña** (1850-1897): La Poetisa Nacional
- **José María Heredia** (1803-1839): Poeta Romántico
- **Nicolás Ureña de Mendoza**: Poeta Patriótico
- **José Joaquín Pérez**: Poeta Romántico

### Poetas Nacionales (1900-1980)
- **Pedro Mir** (1913-2000): Poeta Nacional de RD
- **Manuel del Cabral** (1907-1999): Vanguardista
- **Franklin Mieses Burgos** (1907-1999): Poeta Cósmico

### Poetisas Modernas (1920-1990)
- **Aida Cartagena Portalatín** (1918-1994)
- **Virtudes Álvarez** (1922-)
- **Hilma Contreras** (1907-1996)

### Contemporáneos (1950-Presente)
- **José Acosta**, **Silveria Balbuena**, **Mateo Morrison**
- Y muchos más...

### Categorías Especiales
- Poemas Revolucionarios y Políticos
- Poemas de Amor y Romance
- Poemas de la Naturaleza Dominicana
- Poesía Popular y Tradicional
- Décimas y Coplas

---

## Tipos de Contenido Buscados

1. **Recitación Profesional**: Actores dominicanos recitando
2. **Dramatización**: Interpretación artística del poema
3. **Lectura**: Lectura en voz alta clara
4. **Performance**: Presentación artística o teatral
5. **Compilación**: Antologías de poesía dominicana
6. **Documental**: Videos educativos sobre el poema
7. **Audiopoesía**: Grabaciones de audio con imágenes

---

## Salida de Datos

### Formato Excel/CSV

| # | Poema | Autor | Año | Género | URL YouTube | Duración | Recitador | Tipo Contenido | Calidad | Notas |
|---|-------|-------|-----|--------|-------------|----------|-----------|----------------|---------|-------|
| 1 | A la Patria | Salomé Ureña | 1874 | Patriótico | https://youtube.com/... | 4:32 | Juan Pérez | Recitación | Excelente | Audio claro |

### Columnas del Dataset

- **#**: Número secuencial
- **Poema**: Título del poema
- **Autor**: Poeta dominicano
- **Año**: Año de publicación
- **Género**: Tipo de poema (romántico, patriótico, etc.)
- **URL YouTube**: Enlace directo al video
- **Duración**: Duración del video
- **Recitador**: Nombre de quien recita (si disponible)
- **Tipo Contenido**: Categoría del video
- **Calidad**: Evaluación de audio/video
- **Notas**: Información adicional

---

## Estadísticas Generadas

Al finalizar, obtendrás:

- Total de poemas encontrados
- Total parcial (fragmentos)
- Total no encontrados
- Tasa de éxito (%)
- Autores más representados
- Géneros más encontrados
- Duración promedio de videos

---

## Patrones de Búsqueda en YouTube

El programa usa estos patrones inteligentes:

```
- "[Nombre Poema] [Autor] recitación"
- "[Nombre Poema] poema dominicano"
- "[Autor] poema completo"
- "[Nombre Poema] dramatización"
- "Poesía dominicana [género]"
- "Recitación [Autor dominicano]"
```

---

## Tecnologías Usadas

- **Python 3.8+**
- **scrapetube**: Web scraping de YouTube (sin API key)
- **openpyxl**: Exportación a Excel
- **pandas**: Manipulación de datos

---

## Ejemplos de Uso

### Buscar solo poemas de Salomé Ureña

Crea `poems_list.txt`:
```
A la Patria | Salomé Ureña | 1874 | Patriótico
A la Educación | Salomé Ureña | 1876 | Educativo
La Gloria del Progreso | Salomé Ureña | N/A | Filosófico
```

### Buscar poemas revolucionarios

```
Canción Patriótica | Anónimo | N/A | Revolucionario
Grito de Libertad | Anónimo | N/A | Revolucionario
```

---

## Casos de Uso

1. **Investigación Académica**: Dataset para análisis literario
2. **Educación**: Recursos para enseñar poesía dominicana
3. **Machine Learning**: Entrenar modelos de reconocimiento de recitación
4. **Preservación Cultural**: Catalogar patrimonio poético oral
5. **Análisis de Performance**: Comparar interpretaciones del mismo poema

---

## Notas Importantes

 - Solo busca videos de acceso público
 - Respeta derechos de autor
 - Prioriza contenido educativo y cultural
 - La disponibilidad de videos puede cambiar
 - Algunos poemas pueden no tener recitaciones disponibles

---

## Contribuciones

Si conoces poemas dominicanos que deberían incluirse:

1. Agrega el poema a `src/utils/dominican_poems.py`
2. Sigue el formato: `("Título", "Autor", "Año", "Género")`
3. Haz un pull request

---

## Licencia

Este proyecto es de código abierto para fines educativos y culturales.

---

## Créditos

- **Literatura Dominicana**: Patrimonio cultural de República Dominicana
- **Poetas Dominicanos**: Por su invaluable contribución a las letras hispanas
- **Recitadores**: Por mantener viva la tradición oral poética

---

## Contacto

Para preguntas, sugerencias o colaboraciones sobre literatura dominicana.

---

**¡Preservemos la poesía dominicana en la era digital!**
