# PIDz_circuitpython
Librería para PID discreto para Circuitpython. Está implementado en un objeto que actualiza los errores pasados y las variables de control dentro de una ecuación de diferencias.

## v1.0

### 
```python
class PID:
    def __init__(self):
        self.reset()
        self.Kp = 0
        self.Ki = 0
        self.Kd = 0
        self.Ts = 0
        self.update()
```
La clase inicializa declarando en valor cero las constantes de PID. En caso en medio del control se requiere una actualiación de las constantes, basta con cambiar los valores llamando la objeto para actualizar la matriz de constantes.  

Esta versión solo cuenta con la ecuación de diferencias por método de integración de sumas trapezoidales.

$$
c[k] = c[k-1] + q_0 \cdot e[k] + q_1 \cdot e[k-1] + q_2 \cdot e[k-2]
$$

Donde: 

$$
\mathbf{q} = \begin{bmatrix}
q_0 \\
q_1 \\
q_2 \\
\end{bmatrix} 
= \begin{bmatrix}
\text{self.Kp} + \frac{\text{self.Ki} \cdot \text{self.Ts}}{2} + \frac{\text{self.Kd}}{\text{self.Ts}} \\
-\text{self.Kp} + \frac{\text{self.Ki} \cdot \text{self.Ts}}{2} - \frac{2 \cdot \text{self.Kd}}{\text{self.Ts}} \\
\frac{\text{self.Kd}}{\text{self.Ts}} \\
\end{bmatrix}
$$




