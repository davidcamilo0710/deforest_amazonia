# Monitoreo de Deforestación en la Amazonía (2000-2019)

[cite_start]Este proyecto analiza la evolución de la deforestación en el **Bosque Nacional Jamanxim**, en la Amazonía brasileña, durante un período de 20 años (2000-2019). [cite: 4] [cite_start]Utilizando un pipeline de procesamiento de imágenes satelitales, se identifican y cuantifican las áreas deforestadas para monitorear el impacto ambiental en esta región crítica. [cite: 4, 13]

<p align="center">
  <i>Evolución de la deforestación en el Bosque Nacional Jamanxim (2000 vs. 2019). Las áreas en rojo indican la deforestación detectada.</i><br>
  <img src="URL_IMAGEN_1_COMPARATIVA_AÑOS" alt="Comparativa de Deforestación 2000-2019"/>
</p>

---

## Metodología

[cite_start]El análisis se realizó mediante un pipeline automatizado en Python que procesa imágenes satelitales anuales del [NASA Earth Observatory](https://earthobservatory.nasa.gov/). [cite: 33, 26] El objetivo es segmentar las áreas no boscosas (deforestadas) de las que conservan su vegetación.

El proceso se compone de las siguientes etapas clave:

1.  [cite_start]**Preprocesamiento Visual**: Se aplican técnicas como la ecualización adaptativa de histograma (**CLAHE**) y el **filtro bilateral** para mejorar el contraste y reducir el ruido de las imágenes, preservando los bordes entre zonas boscosas y deforestadas. [cite: 51, 40]
2.  [cite_start]**Detección de Nubes**: Se implementó un algoritmo que utiliza los espacios de color **HSV** y **LAB** junto con un análisis de gradiente para crear una máscara y excluir las nubes, evitando que interfieran en el cálculo del área. [cite: 55, 56]
3.  [cite_start]**Segmentación de Áreas Deforestadas**: La identificación de la deforestación se basa principalmente en la **segmentación por color** en los espacios **LAB** y **HSV**. [cite: 64] [cite_start]Estos espacios permiten diferenciar eficazmente los tonos de suelo expuesto (marrones/amarillos) de la vegetación densa (verdes). [cite: 67, 69]
4.  [cite_start]**Refinamiento Morfológico**: Para mejorar la precisión, se detectan **estructuras lineales** (carreteras) usando la **Transformada de Hough** y se aplican operaciones morfológicas (apertura y cierre) para limpiar la máscara final de ruido y conectar áreas fragmentadas. [cite: 78, 83]
5.  [cite_start]**Cálculo de Área**: Finalmente, se cuenta el número de píxeles clasificados como deforestados en la máscara binaria final y se convierte a kilómetros cuadrados ($km^2$) utilizando una relación de escala calibrada. [cite: 91, 92]

---

## Resultados

El análisis cuantitativo revela una tendencia creciente y persistente de la deforestación en la región durante las dos décadas estudiadas.

* [cite_start]El área deforestada pasó de **4,002.77 $km^2$** en el año 2000 a **12,957.17 $km^2$** en 2019. [cite: 125]
* [cite_start]Se identificó un **aumento lineal promedio de 52.15 $km^2$ por año**. [cite: 6, 189]
* [cite_start]Los años **2017, 2018 y 2019** registraron los niveles más altos de deforestación acumulada, lo que indica una intensificación del problema en el tramo final del período. [cite: 184]

El siguiente gráfico muestra tanto la deforestación anual (barras amarillas) como el área acumulada a lo largo del tiempo (línea roja), evidenciando la tendencia general al alza y los picos de deforestación en años específicos.

<p align="center">
  <i>Comparación de la deforestación anual vs. la acumulada.</i><br>
  <img src="URL_IMAGEN_2_GRAFICO_ACUMULADO" alt="Gráfico de Deforestación Anual y Acumulada"/>
</p>

---

## Code and Resources

Todos los recursos, incluyendo el código fuente, los datos y el informe detallado del proyecto, están disponibles en este repositorio.

* **Informe Completo**: Para una descripción exhaustiva de la metodología, los resultados y las conclusiones, puedes consultar el **[artículo del proyecto](https://github.com/davidcamilo0710/deforest_amazonia/blob/main/deforest_amazonia.pdf)**.
* **Notebook de Análisis**: El código completo del pipeline de procesamiento de imágenes está implementado en un **[Jupyter Notebook](https://github.com/davidcamilo0710/deforest_amazonia/blob/main/src.ipynb)**.
* [cite_start]**Tecnologías Utilizadas**: El proyecto fue desarrollado en **Python** utilizando librerías como **OpenCV**, **scikit-image**, **NumPy** y **Matplotlib**. [cite: 26-30]

---

## Conclusión

[cite_start]Este estudio demuestra la eficacia de las técnicas de visión por computador para el monitoreo ambiental a gran escala. [cite: 188] [cite_start]La metodología desarrollada es replicable y proporciona una herramienta valiosa para que organizaciones y gobiernos puedan seguir la dinámica de la deforestación, evaluar el impacto de las políticas de conservación y tomar decisiones informadas para proteger ecosistemas vitales como la Amazonía. [cite: 7, 203]

## Autor

* **[David Camilo Muñoz Garcia](https://github.com/davidcamilo0710)**
