# MetricKitReporter Dashboard

Dashboard web estático para visualizar métricas de iOS exportadas en JSON

## Qué hace

Permite cargar un archivo JSON generado por el paquete Swift `MetricKitReporter` y explorar visualmente todas las métricas de rendimiento de una app iOS: lanzamiento, CPU, memoria, red, animaciones, diagnósticos y más.

Todo se procesa en el navegador. No se envía nada a ningún servidor.

## Funcionalidades

- **Carga local de JSON** mediante botón o arrastrando el archivo
- **Datos de demo** para previsualizar el dashboard sin necesidad de archivo
- **Vista general** con semáforo de salud global e información del dispositivo/app
- **11 tarjetas de métricas**: Launch, Responsiveness, CPU, GPU, Memory, Disk, Network, Display, App Runtime, Animation y App Exits
- **5 gráficos interactivos** (Chart.js):
  - Barras con métricas clave del reporte
  - Donut con distribución de estados de salud
  - Línea temporal con selector de métrica (si hay varios reportes)
  - Polar area de red WiFi vs Cellular
  - Barras horizontales de salidas de la app (foreground/background)
- **Tabla de diagnósticos** con crashes, hangs, excepciones de CPU, escritura a disco y stack traces
- **Selector de reportes** cuando el JSON contiene más de uno
- **Evaluación de salud** por categoría con badges de color (saludable, atención, perjudicial, contextual, sin referencia)
- **Fallback gracioso**: los campos ausentes se muestran como "N/D"

## Diseño

- Dark mode con glassmorphism estilo Apple
- Layout Bento Grid responsive (4 columnas en desktop, adaptable a móvil)
- Animaciones de entrada escalonadas
- Tipografía SF Pro / system font

## Estructura del JSON esperado

El dashboard espera un JSON con la estructura que genera `MetricKitReporter`:

```json
{
  "exportedAt": "2026-03-24T10:00:00Z",
  "reports": [
    {
      "reportID": "...",
      "generatedAt": "...",
      "appVersion": "2.1.0",
      "buildVersion": "123",
      "deviceType": "iPhone16,2",
      "osVersion": "18.3",
      "launch": { ... },
      "cpu": { ... },
      "memory": { ... },
      "network": { ... },
      "health": { ... },
      "diagnostics": { ... }
    }
  ]
}
```
## Tecnologías

- HTML, CSS y JavaScript puro (sin frameworks)
- [Chart.js](https://www.chartjs.org/) desde CDN para gráficos
- [Luxon](https://moment.github.io/luxon/) como adaptador de fechas para Chart.js
- GitHub Pages para el hosting

También puedes pulsar **Demo** para ver el dashboard con datos de ejemplo.
