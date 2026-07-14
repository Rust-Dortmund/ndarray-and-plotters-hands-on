# Least mean square basics

Least mean square can be used to determine a line that fits a set of points best. It minimizes the squared differences from the line.

## Calculation

\\( a=\dfrac{\sum\limits_{i=1}^{\text{n}} (x_i-\bar{x})y_i}{\sum\limits_{i=1}^{\text{n}} (x_i-\bar{x})^2}=\dfrac{\sum\limits_{i=1}^{\text{n}} x_iy_i-\left(\dfrac{1}{\text{n}}\right) \left(\sum\limits_{i=1}^{\text{n}} x_i\right) \left(\sum\limits_{i=1}^{\text{n}} y_i\right)}{\sum\limits_{i=1}^{\text{n}} x^2_i-\left(\dfrac{1}{\text{n}}\right) \left(\sum\limits_{i=1}^{\text{n}} x_i\right)^2}\\)

\\( b=\dfrac{\sum\limits_{i=1}^{\text{n}} y_i - a \sum\limits_{i=1}^{\text{n}} x_i}{\text{n}}\\)