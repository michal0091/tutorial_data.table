# Tutorial Completo de data.table en R

![data.table](https://img.shields.io/badge/data.table-1.14%2B-2E8B57?style=for-the-badge)
![Quarto](https://img.shields.io/badge/Quarto-1.3%2B-276DC3?style=for-the-badge)
![R](https://img.shields.io/badge/R-4.0%2B-276DC3?style=for-the-badge)

Un tutorial completo e interactivo para dominar `data.table`, el paquete más rápido para manipulación de datos en R. Desde conceptos básicos hasta técnicas avanzadas de optimización.

## 🎯 ¿Para quién es este tutorial?

- **Principiantes** que quieren aprender manipulación de datos eficiente
- **Usuarios de dplyr** que necesitan manejar datasets más grandes
- **Data Scientists** que buscan maximizar la velocidad de sus análisis
- **Desarrolladores R** que quieren dominar técnicas avanzadas

## 📚 Contenido del Tutorial

### **Módulo 1: Fundamentos y Sintaxis Esencial**
- ¿Qué es `data.table` y por qué usarlo?
- La sintaxis `DT[i, j, by]` en profundidad
- Símbolos especiales: `.N`, `.SD`, `.I`, `.GRP`

### **Módulo 2: Manipulación de Datos Intermedia**
- Encadenamiento de operaciones
- Joins entre data.tables
- Modificación por referencia con `:=`

### **Módulo 3: Técnicas Avanzadas**
- Rolling joins para series temporales
- Non-equi joins para rangos
- Reshape de datos con `melt()` y `dcast()`

### **Módulo 4: Optimización y Performance**
- Configuración de threading
- Keys e índices para velocidad máxima
- Do's y Don'ts definitivos

### **Módulo 5: Integración con el Ecosistema R**
- Workflows con `ggplot2` y `shiny`
- Machine learning con `tidymodels`
- El paquete `dtplyr`

## 🚀 Inicio Rápido

### Prerrequisitos

```r
# Instalar paquetes necesarios
install.packages(c(
  "data.table",
  "ggplot2", 
  "DT",
  "microbenchmark",
  "knitr"
))

# Opcional para ejemplos avanzados
install.packages(c(
  "shiny",
  "plotly", 
  "dtplyr",
  "tidymodels"
))
```

### Generar el Tutorial

```bash
# Clonar o descargar este repositorio
cd tutorial_data.table

# Renderizar el libro completo
quarto render

# O previsualizar en modo desarrollo
quarto preview
```

### Ver Online

El tutorial estará disponible en `_book/index.html` después del renderizado.

## 📊 Lo que Aprenderás

Al completar este tutorial, serás capaz de:

✅ **Dominar la sintaxis `DT[i, j, by]`** como un experto  
✅ **Procesar datasets gigantes** con eficiencia extrema  
✅ **Implementar rolling joins** para análisis temporal  
✅ **Optimizar código** para maximum performance  
✅ **Integrar data.table** con ggplot2, shiny y más  
✅ **Debuggear y perfilar** código complejo  

## 🏆 Características Destacadas

- **🎮 Ejercicios interactivos** con soluciones paso a paso
- **⚡ Comparaciones de performance** data.table vs dplyr vs R base
- **📈 Ejemplos del mundo real** con datasets grandes
- **💡 Tips y trucos** de la comunidad de expertos
- **🔗 Referencias cruzadas** entre capítulos
- **📱 Responsive design** para móvil y desktop

## 🛠️ Estructura del Proyecto

```
tutorial_data.table/
├── _quarto.yml           # Configuración del proyecto
├── _brand.yml            # Branding y colores personalizados
├── styles.css            # Estilos CSS personalizados
├── index.qmd             # Página de inicio
├── intro.qmd             # Introducción
├── cap01-fundamentos.qmd # Capítulo 1: Fundamentos
├── cap02-manipulacion.qmd# Capítulo 2: Manipulación
├── cap03-avanzadas.qmd   # Capítulo 3: Técnicas Avanzadas
├── cap04-optimizacion.qmd# Capítulo 4: Optimización
├── cap05-integracion.qmd # Capítulo 5: Integración
├── conclusion.qmd        # Conclusiones
├── references.bib        # Bibliografía
├── references.qmd        # Página de referencias
├── data/                 # Datasets de ejemplo
├── images/               # Imágenes y gráficos
└── _book/               # Salida del libro (generada)
```

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Puedes:

- **🐛 Reportar bugs** o errores en el contenido
- **💡 Sugerir mejoras** o nuevos ejemplos
- **📝 Corregir typos** o mejorar explicaciones
- **🧪 Probar** el tutorial en diferentes versiones de R
- **📚 Añadir** más ejercicios o casos de uso

### Cómo Contribuir

1. Fork este repositorio
2. Crea una branch para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la branch (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este tutorial está bajo licencia [MIT](LICENSE). Siéntete libre de usarlo, modificarlo y distribuirlo.

## 🙏 Agradecimientos

- **Matt Dowle** y el equipo de desarrollo de `data.table`
- **La comunidad R** por mantener el ecosistema vibrante
- **Posit/RStudio** por Quarto y las herramientas de desarrollo
- **Todos los contribuidores** que hacen este tutorial mejor

## 📞 Contacto y Soporte

- **Issues**: [GitHub Issues](https://github.com/michal0091/tutorial_data.table/issues)
- **Discussions**: [GitHub Discussions](https://github.com/michal0091/tutorial_data.table/discussions)
- **Stack Overflow**: Tag con `[data.table]` para preguntas técnicas

---

### 🌟 Si este tutorial te ayudó, ¡considera darle una estrella!

**¡Feliz aprendizaje con data.table!** 🎉

---

*Última actualización: Diciembre 2024*  
*Versión del tutorial: 1.0*  
*Compatible con data.table >= 1.14.0*