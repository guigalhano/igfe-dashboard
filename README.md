# IGFE Dashboard — Gestión Financiera del Estado

Dashboard interactivo para visualizar el **Informe de Gestión Financiera del Estado (IGFE)** publicado trimestralmente por la Contraloría General de la República de Chile.

![Dashboard preview](preview.png)

## Características

- **Selector de trimestre** — navega entre Q1, Q2, Q3 y Q4
- **KPIs ejecutivos** — resumen de cifras clave en tarjetas
- **Gráficos por sector** — Sector Público, Municipal, Empresas del Estado, Educación Superior
- **Rankings ministeriales** — mayores y menores ejecuciones presupuestarias
- **FCM por región** — participación del Fondo Común Municipal
- **Deuda pública e inversiones** — evolución histórica como % del PIB
- **Transferencias MINEDUC** — cobertura gratuidad 2021–2025

## Tecnologías

- HTML + CSS + JavaScript (vanilla)
- [Chart.js 4.4](https://www.chartjs.org/) — gráficos de barras, líneas y mixtos
- Sin frameworks ni dependencias de build

## Uso local

Clona el repositorio y abre `index.html` en cualquier navegador moderno:

```bash
git clone https://github.com/TU_USUARIO/igfe-dashboard.git
cd igfe-dashboard
open index.html
```

O con Python para evitar restricciones CORS locales:

```bash
python3 -m http.server 8000
# Luego abre http://localhost:8000
```

## Publicar en GitHub Pages

1. Ve a **Settings → Pages** en tu repositorio
2. Selecciona `main` como rama y `/ (root)` como carpeta
3. Guarda — el dashboard estará en `https://TU_USUARIO.github.io/igfe-dashboard/`

## Actualizar datos para un nuevo trimestre

Edita el objeto `DATA` en `index.html` (cerca de la línea 360):

```js
const DATA = {
  // Añade o actualiza el trimestre correspondiente
  3: {
    period: "Ene–Sep 2025",
    kpis: [
      { label: "Gasto total estado", value: "124,6", unit: "B$", delta: "+4,5% vs 2024", up: true },
      // ...
    ]
  }
}
```

Luego actualiza las series de datos de los gráficos estáticos en las funciones `build*()`.

## Estructura del proyecto

```
igfe-dashboard/
├── index.html      # Dashboard completo (single-file)
└── README.md       # Este archivo
```

## Fuente de datos

- Contraloría General de la República de Chile
- [IGFE Trimestral](https://www.contraloria.cl)
- PIB: Banco Central de Chile

## Licencia

MIT — libre para usar, adaptar y redistribuir con atribución.
