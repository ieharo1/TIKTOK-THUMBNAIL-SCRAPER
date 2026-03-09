# 🎬 TikTok Thumbnail Scraper

Scraper profesional para extraer y descargar thumbnails (miniaturas) de videos de TikTok. Desarrollado por **Isaac Esteban Haro Torres**.

---

## 📝 Descripción

Sistema automatizado para obtener miniaturas de videos de TikTok a partir de usernames o URLs. Ideal para investigadores de marketing, analistas de contenido y creadores.

### ¿Qué hace este proyecto?

- **Extracción por usuario**: Descarga todos los thumbnails de un perfil
- **Extracción por URL**: Videos específicos mediante URLs
- **Metadatos completos**: Guarda info del video (likes, views, fecha)
- **Procesamiento de imágenes**: Redimensiona y optimiza thumbnails
- **Detección de tendencias**: Identifica videos más populares
- **Exportación múltiple**: CSV, JSON, Excel con análisis

---

## ✨ Características Principales

| Característica | Descripción |
|----------------|-------------|
| 🔍 **Por username** | Todos los videos de un perfil |
| 🔗 **Por URL** | Videos específicos |
| 📊 **Metadatos** | Likes, shares, comentarios, fecha |
| 🖼️ **Múltiples calidades** | HD, SD, threshold |
| 📈 **Análisis** | Stats de videos más populares |
| ⚡ **Alto rendimiento** | Descarga paralela de thumbnails |

---

## 🛠️ Stack Tecnológico

- **Lenguaje**: Python 3.10+
- **Web Scraping**: BeautifulSoup, requests
- **API TikTok**: TikTokApi (opcional)
- **Imágenes**: Pillow, opencv-python
- **Datos**: Pandas, NumPy
- **Async**: aiohttp, asyncio

---

## 🚀 Instalación y Uso

### Instalación

```bash
pip install beautifulsoup4 requests pillow pandas aiohttp
```

### Uso básico - Por username

```python
from tiktok_scraper import TikTokScraper

scraper = TikTokScraper()

# Descargar thumbnails de un usuario
resultado = scraper.descargar_perfil(
    username='usuario_ejemplo',
    destino='./thumbnails/',
    calidad='hd'
)

print(f"Descargados: {resultado['descargados']} thumbnails")
```

### Uso por URL

```python
# Descargar thumbnail específico
scraper.descargar_url(
    url='https://www.tiktok.com/@usuario/video/123456789',
    destino='./single/'
)
```

### Con metadatos

```python
# Obtener thumbnails con info del video
videos = scraper.extraer_perfil(
    username='marce',
    limite=50,
    incluir_metadatos=True
)

# Guardar a CSV
scraper.guardar_csv(videos, 'videos_analysis.csv')

# Análisis de tendencias
analisis = scraper.analizar_tendencias(videos)
print(analisis)
```

---

## 📊 Metadatos Extraídos

```python
{
    'video_id': '7234567890123456789',
    'username': 'marce.oficial',
    'thumbnail_url': 'https://p16-sign-sg.tiktokcdn.com/...',
    'likes': 125000,
    'comments': 2300,
    'shares': 450,
    'views': 2500000,
    'fecha_publicacion': '2025-12-15',
    'duracion': 15,
    'descripcion': '#viral #trending #fyp',
    'musica': 'Sound original - Artista'
}
```

---

## 📁 Estructura de Archivos

```
thumbnails/
├── username_ejemplo/
│   ├── 2026-01/
│   │   ├── video_001.jpg
│   │   ├── video_002.jpg
│   │   └── video_003.jpg
│   └── 2026-02/
│       └── ...
├── metadata/
│   └── username_ejemplo.json
└── reporte_analisis.csv
```

---

## 📈 Dashboard de Análisis

```
╔═══════════════════════════════════════════════════════╗
║       🎬 TIKTOK THUMBNAIL SCRAPER - ANÁLISIS         ║
╠═══════════════════════════════════════════════════════╣
║                                                       ║
║  📊 Usuario: @marce.oficial                          ║
║  📹 Videos analizados: 45                            ║
║                                                       ║
║  📈 MÉTRICAS:                                        ║
║  ┌─────────────────────────────────────────────┐     ║
║  │ Vistas totales:    45.2M                     │     ║
║  │ Promedio vistas:   1.0M                       │     ║
║  │ Promedio likes:   125K                       │     ║
║  │ Engagement rate:   6.8%                       │     ║
║  └─────────────────────────────────────────────┘     ║
║                                                       ║
║  🔝 Top 5 Videos:                                   ║
║  1. 🟢 Video viral - 5.2M vistas                    ║
║  2. 🟢 Challenge - 3.8M vistas                      ║
║  3. 🟢 Tutorial - 2.1M vistas                       ║
║                                                       ║
╚═══════════════════════════════════════════════════════╝
```

---

## 💡 Casos de Uso

1. **Análisis de competencia**: Estudia thumbnails de competidores
2. **Investigación de mercado**: Tendencias en TikTok
3. **Inspiración para creators**: Mejora tus miniaturas
4. **Investigación académica**: Estudios de comportamiento
5. **Monitoreo de marca**: следау за mentions de marca

---

## 🔧 Opciones Avanzadas

```python
# Configuración avanzada
scraper = TikTokScraper(
    calidad='hd',              # hd, sd, low
    delay=2,                   # segundos entre requests
    proxy='http://proxy:port', # proxy rotativo
    user_agent='Custom UA',    # custom User-Agent
    headless=True              # modo sin navegador
)

# Filtrar por métricas
videos_filtrados = scraper.filtrar(
    videos,
    min_likes=10000,
    max_videos=20,
    ordenar_por='views'
)
```

---

## 📊 Análisis de Thumbnails

```python
# Análisis de colores dominantes
from PIL import Image

for thumbnail in thumbnails:
    colores = analizador.obtener_colores_dominantes(thumbnail)
    print(f"Colores: {colores}")

# Detectar texto en thumbnail
for thumbnail in thumbnails:
    tiene_texto = detector.tiene_texto(thumbnail)
    print(f"Tiene texto: {tiene_texto}")
```

---

## ⚠️ Notas Importantes

- Respeta los Términos de Servicio de TikTok
- Usa con responsabilidad y moderación
- No spam requests - implementa delays
- Algunos perfiles pueden ser privados

---

## 🔄 Diferencias con APIs Oficiales

| Método | Pros | Contras |
|--------|------|---------|
| Web Scraping | Gratis, flexible | Menos estable |
| TikTok API | Oficial, estable | Requiere aprobación |
|第三方库 | Fácil de usar | Puede romperse |


---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.
