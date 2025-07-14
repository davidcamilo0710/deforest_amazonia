# Deforestation Monitoring in the Amazon (2000-2019)

This project analyzes the evolution of deforestation in the **Jamanxim National Forest**, located in the Brazilian Amazon, over a 20-year period (2000-2019). Using a satellite image processing pipeline, this work identifies and quantifies deforested areas to monitor the environmental impact in this critical region.

<table>
  <tr>
    <td align="center">
      <i>Evolution of deforestation in the Jamanxim National Forest (2000 vs. 2019).<br>
      The areas in red indicate detected deforestation.</i><br>
      <img width="303" height="667" alt="Annual and Cumulative Deforestation Graph" src="https://github.com/user-attachments/assets/17f21adb-97f7-4d29-be49-3bb54bcab9ff" />
    </td>
    <td align="right">
      <img src="https://github.com/user-attachments/assets/88f5cb71-0f34-4990-a150-0bb5dcd9a278" alt="Deforestation GIF" width="250" />
    </td>
  </tr>
</table>

---

## Methodology

The analysis was performed using an automated Python pipeline that processes annual satellite images from the [NASA Earth Observatory](https://earthobservatory.nasa.gov/). The goal is to segment non-forested (deforested) areas from those that still have vegetation cover.

The process consists of the following key stages:

1.  **Visual Preprocessing**: Techniques such as Contrast Limited Adaptive Histogram Equalization (**CLAHE**) and a **Bilateral Filter** are applied to enhance contrast and reduce noise in the images, while preserving the sharp edges between forested and deforested zones.
2.  **Cloud Detection**: An algorithm using **HSV** and **LAB** color spaces, combined with gradient analysis, was implemented to create a mask and exclude clouds, preventing them from interfering with area calculations.
3.  **Segmentation of Deforested Areas**: The identification of deforestation is primarily based on **color segmentation** in the **LAB** and **HSV** color spaces. These spaces effectively differentiate the tones of exposed soil (browns/yellows) from dense vegetation (greens).
4.  **Morphological Refinement**: To improve accuracy, **linear structures** (like roads) are detected using the **Hough Transform**, and morphological operations (opening and closing) are applied to clean the final mask from noise and connect fragmented areas.
5.  **Area Calculation**: Finally, the number of pixels classified as deforested in the final binary mask is counted and converted to square kilometers ($km^2$) using a calibrated scaling factor.

---

## Results

The quantitative analysis reveals a persistent and growing trend of deforestation in the region over the two decades studied.

* The deforested area increased from **4,002.77 $km^2$** in 2000 to **12,957.17 $km^2$** in 2019.
* An average linear increase of **52.15 $km^2$ per year** was identified.
* The years **2017, 2018, and 2019** recorded the highest levels of accumulated deforestation, indicating an intensification of the problem towards the end of the period.

The following graph shows both the annual deforestation (yellow bars) and the cumulative area over time (red line), highlighting the general upward trend and the peaks of deforestation in specific years.

<p align="center">
  <i>Comparison of annual vs. cumulative deforestation.</i><br>
  <img width="539" height="588" alt="Annual and Cumulative Deforestation Graph" src="https://github.com/user-attachments/assets/06a76f57-2d91-4770-b8e0-f8a81c9d401b" />
</p>

---

## Code and Resources

All resources, including the source code, data, and a detailed project report, are available in this repository.

* **Full Report**: For a comprehensive description of the methodology, results, and conclusions, you can consult the **[project article (in Spanish)](https://github.com/davidcamilo0710/deforest_amazonia/blob/main/deforest_amazonia.pdf)**.
* **Analysis Notebook**: The complete code for the image processing pipeline is implemented in a **[Jupyter Notebook](https://github.com/davidcamilo0710/deforest_amazonia/blob/main/src.ipynb)**.
* **Technologies Used**: The project was developed in **Python** using libraries such as **OpenCV**, **scikit-image**, **NumPy**, and **Matplotlib**.

---

## Conclusion

This study demonstrates the effectiveness of computer vision techniques for large-scale environmental monitoring. The developed methodology is replicable and provides a valuable tool for organizations and governments to track deforestation dynamics, evaluate the impact of conservation policies, and make informed decisions to protect vital ecosystems like the Amazon.

## Author

* **[David Camilo Muñoz Garcia](https://github.com/davidcamilo0710)**
