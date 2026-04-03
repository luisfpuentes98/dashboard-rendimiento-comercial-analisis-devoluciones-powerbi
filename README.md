# 📊 Análisis Integral de Ventas y Devoluciones E-Commerce

> **Análisis integral de datos y visualización de ventas y tasas de retorno de e-commerce usando Power BI.**

## 📌 Resumen del Proyecto
Las devoluciones de productos representan uno de los mayores riesgos financieros y operativos para las empresas de comercio electrónico. Este proyecto de Inteligencia Empresarial (BI) tiene como objetivo analizar el rendimiento de ventas de una multinacional, identificar las causas raíz de las devoluciones y cuantificar su impacto directo en el margen de beneficio.

A través de un modelo de datos robusto y cálculos DAX avanzados, el panel interactivo transforma datos brutos en insights accionables para la toma de decisiones estratégicas.

## 🛠️ Stack Tecnológico y Metodología
* **Herramienta Principal:** Power BI
* **Volumen y Arquitectura:** Procesamiento y optimización de **más de 1 millón de registros** distribuidos en un modelo de **5 tablas relacionales** (`Orders`, `Returns`, `Customers`, `Products`, `Regions`).
* **Extracción y Limpieza (ETL):** Power Query (Manejo de inconsistencias en IDs, limpieza de caracteres nulos y estandarización de formatos CSV a gran escala).
* **Modelado de Datos:** Esquema en Estrella (Star Schema). Resolución de problemas complejos de propagación de filtros (implementación de filtros cruzados bidireccionales entre tablas de Ventas y Devoluciones).
* **Lógica de Negocio:** Desarrollo de +15 medidas con DAX (Time Intelligence, iteradores, lógicas condicionales) optimizadas para grandes volúmenes de datos.

## 💡 Descubrimientos Clave (Key Insights)

1. **El Mito Logístico desmentido:** El análisis demostró que no existe correlación estadística entre el tiempo de entrega (promedio de 3.9 días) y la tasa de devoluciones. Esto permite redirigir el presupuesto destinado a "envíos más rápidos" hacia auditorías de control de calidad.
2. **El Riesgo en la Cartera VIP:** Los 5 productos que generan las mayores pérdidas financieras por devoluciones son devueltos *exclusivamente* por los clientes del segmento "Oro" y "Plata". Curiosamente, los clientes "Bronce" tienen una tasa de devolución del 0% en estos artículos específicos.
3. **Impacto Financiero (Bottom Line):** Las devoluciones están reteniendo actualmente el **9.23%** de los ingresos totales generados (aprox. €22.4M), lo que subraya la necesidad urgente de evaluar y retirar o mejorar el Top 3 de productos más devueltos del catálogo.

## 📸 Vista del Dashboard Principal
<img width="1230" height="701" alt="dashboard_principal" src="https://github.com/user-attachments/assets/fe205387-5c50-4b5f-80e7-0fc53be1ee28" />

## 📸 Vista del Dashboard Principal con filtros
<img width="1221" height="702" alt="dashboard_principal_filter2" src="https://github.com/user-attachments/assets/8dd6e264-0e5b-4937-8fff-4561804656b4" />

## 📸 Vista del Modelo Relacional
<img width="852" height="737" alt="modelo_datos" src="https://github.com/user-attachments/assets/35c9bec0-23ef-4959-bb64-8b46ecf6d67a" />

## 📂 Archivos del Proyecto (Data & .pbix)

Debido al gran volumen de datos manejado en este proyecto (más de 1 millón de registros), los archivos originales superan el límite de tamaño de GitHub. 

Puedes descargar el archivo interactivo de Power BI (`.pbix`) y los datasets originales (archivos `.csv`) desde el siguiente enlace seguro:

👉 **[Descargar Proyecto Completo en Google Drive](https://drive.google.com/drive/folders/1bT7-D_xsA3KjFd8GYGUfPwgR-JXsA7M3?usp=sharing)**

## ⚙️ Muestra de Código (DAX)
Para lograr este nivel de análisis y manejar el alto volumen de datos de manera eficiente, se desarrollaron métricas avanzadas. Aquí destaco tres enfoques clave:

**1. Inteligencia de Tiempo (Crecimiento YoY):**
Para evaluar el rendimiento mensual contra el año anterior, aislando la estacionalidad del negocio.
```dax
Ventas Año Anterior = 
CALCULATE(
    [Ingresos Totales], 
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

**2. Lógica Condicional y Relacional (Etiquetado de Devoluciones):**
Identificación del estado de cada pedido cruzando tablas de hechos de manera dinámica.
```dax
Estado Devolucion = 
IF(
    CALCULATE(COUNTROWS('returns')) > 0, 
    "Sí Devuelto", 
    "No Devuelto"
)
```

**3. Cuantificación del Riesgo Financiero:**
```dax
Ingresos Perdidos = 
CALCULATE(
    [Ingresos Totales], 
    'orders'[Estado Devolucion] = "Sí Devuelto"
)
```

## 👨‍💻 Autor
**Luis Fernando Puentes**
*Analista de Datos | Máster en Análisis de Datos e Inteligencia Empresarial*
www.linkedin.com/in/luis-fernando-puentes-rodriguez-7576b6213
