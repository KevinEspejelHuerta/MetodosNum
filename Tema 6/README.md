<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
</head>
<body>

<h1> Tema 6: Resolución Numérica de Ecuaciones Diferenciales Ordinarias (EDOs)</h1>

<p>Este tema aborda los métodos numéricos utilizados para resolver ecuaciones diferenciales ordinarias (EDOs), esenciales para modelar fenómenos físicos, químicos, biológicos e ingenieriles. Se estudian métodos de un paso, múltiples pasos y sistemas de EDOs.</p>

<h1> Índice</h1>
<ul>
  <li><a href="#metodos-un-paso">6.1  Métodos de Un Paso</a></li>
  <li><a href="#metodos-multiples-pasos">6.2  Métodos de Pasos Múltiples</a></li>
  <li><a href="#sistemas-edos">6.3  Sistemas de Ecuaciones Diferenciales Ordinarias</a></li>
</ul>

<div class="subtema">
<h2 id="metodos-un-paso">6.1  Métodos de Un Paso</h2>
  <p>Estos métodos calculan la solución en el siguiente punto solo a partir de la información actual.</p>

  <h3> Método de Euler</h3>
  <p>Fórmula básica:</p>
  <pre><code>y_{n+1} = y_n + h * f(x_n, y_n)</code></pre>

  **Pseudocódigo**
  ```plaintext
Inicio
    Definir función funcion(x, y):
        Retornar x + y

    Definir variables:
        x = valor inicial de x (no dado en el fragmento)
        y = valor inicial de y (no dado en el fragmento)
        h = tamaño del paso
        pasos = número de iteraciones

    Para i desde 0 hasta pasos - 1 hacer:
        Imprimir "x=" + x formateado a 2 decimales + ", y=" + y formateado a 5 decimales
        y = y + h * funcion(x, y)
        x = x + h
    FinPara
Fin
  ```

  <p><strong>Ejemplo en Java:</strong></p>
  <pre><code>public class MetodoEuler {
    public static void main(String[] args) {
        double x = 0, y = 1, h = 0.1;
        int pasos = 10;

        for (int i = 0; i < pasos; i++) {
            System.out.printf("x=%.2f, y=%.5f%n", x, y);
            y = y + h * funcion(x, y);
            x += h;
        }
    }

    static double funcion(double x, double y) {
        return x + y; // Ejemplo: y' = x + y
    }
}</code></pre>

**Casos de prueba**

![alt text](image.png)

  <h3> Método de Runge-Kutta de 4to Orden (RK4)</h3>
  <p>Más preciso que Euler:</p>
  <pre><code>k1 = f(x_n, y_n)
k2 = f(x_n + h/2, y_n + h*k1/2)
k3 = f(x_n + h/2, y_n + h*k2/2)
k4 = f(x_n + h, y_n + h*k3)
y_{n+1} = y_n + (h/6)*(k1 + 2*k2 + 2*k3 + k4)</code></pre>

**Pseudocódigo**
```plaintext
Inicio
    Definir función funcion(x, y):
        Retornar x + y

    Definir variables:
        x = valor inicial de x (no dado en el fragmento)
        y = valor inicial de y (no dado en el fragmento)
        h = tamaño del paso
        pasos = número de iteraciones

    Para i desde 0 hasta pasos - 1 hacer:
        k1 = h * funcion(x, y)
        k2 = h * funcion(x + h/2, y + k1/2)
        k3 = h * funcion(x + h/2, y + k2/2)
        k4 = h * funcion(x + h, y + k3)

        y = y + (k1 + 2*k2 + 2*k3 + k4) / 6
        x = x + h

        Imprimir "x=" + x formateado a 2 decimales + ", y=" + y formateado a 5 decimales
    FinPara
Fin
```

  <p><strong>Ejemplo en Java:</strong></p>
  <pre><code>public class MetodoRK4 {
    public static void main(String[] args) {
        double x = 0, y = 1, h = 0.1;
        int pasos = 10;

        for (int i = 0; i < pasos; i++) {
            double k1 = h * funcion(x, y);
            double k2 = h * funcion(x + h/2, y + k1/2);
            double k3 = h * funcion(x + h/2, y + k2/2);
            double k4 = h * funcion(x + h, y + k3);
            y += (k1 + 2*k2 + 2*k3 + k4) / 6;
            x += h;
            System.out.printf("x=%.2f, y=%.5f%n", x, y);
        }
    }

    static double funcion(double x, double y) {
        return x + y;
    }
}</code></pre>

**Casos de prueba**

![alt text](image-1.png)
</div>

<div class="subtema">
<h2 id="metodos-multiples-pasos">6.2  Métodos de Pasos Múltiples</h2>
  <p>Usan valores de pasos anteriores para calcular el siguiente. Requieren pasos iniciales (por ejemplo, con RK4).</p>

  <h3> Método de Adams-Bashforth (2 pasos)</h3>
  <pre><code>y_{n+1} = y_n + h/2 * [3f(x_n, y_n) - f(x_{n-1}, y_{n-1})]</code></pre>

  <h3> Método de Adams-Moulton (implícito)</h3>
  <pre><code>y_{n+1} = y_n + h/2 * [f(x_{n+1}, y_{n+1}) + f(x_n, y_n)]</code></pre>

  <p><strong>Nota:</strong> Generalmente se implementan junto con un predictor (e.g. Adams-Bashforth) para estimar <code>y_{n+1}</code> y luego corregir.</p>
</div>

<div class="subtema">
<h2 id="sistemas-edos">6.3  Sistemas de Ecuaciones Diferenciales Ordinarias</h2>
  <p>Cuando hay varias funciones dependientes, se utiliza un sistema de EDOs. Por ejemplo:</p>
  <pre><code>y1' = f1(x, y1, y2)
y2' = f2(x, y1, y2)</code></pre>

**Pseudocódigo**
```plaintext
Inicio
    Definir función f1(x, y1, y2):
        Retornar y2  // y1' = y2

    Definir función f2(x, y1, y2):
        Retornar -y1  // y2' = -y1 (oscilador armónico)

    Definir variables:
        x = valor inicial de x (no dado en el fragmento)
        y1 = valor inicial de y1
        y2 = valor inicial de y2
        h = tamaño del paso
        pasos = número de iteraciones

    Para i desde 0 hasta pasos - 1 hacer:
        Imprimir "x=" + x formateado a 2 decimales + ", y1=" + y1 formateado a 5 decimales + ", y2=" + y2 formateado a 5 decimales

        k1 = h * f1(x, y1, y2)
        l1 = h * f2(x, y1, y2)

        k2 = h * f1(x + h/2, y1 + k1/2, y2 + l1/2)
        l2 = h * f2(x + h/2, y1 + k1/2, y2 + l1/2)

        k3 = h * f1(x + h/2, y1 + k2/2, y2 + l2/2)
        l3 = h * f2(x + h/2, y1 + k2/2, y2 + l2/2)

        k4 = h * f1(x + h, y1 + k3, y2 + l3)
        l4 = h * f2(x + h, y1 + k3, y2 + l3)

        y1 = y1 + (k1 + 2*k2 + 2*k3 + k4) / 6
        y2 = y2 + (l1 + 2*l2 + 2*l3 + l4) / 6
        x = x + h
    FinPara
Fin
```

  <h3> Ejemplo en Java con Runge-Kutta (Sistema 2x2)</h3>
  <pre><code>public class SistemaEDOs {
    public static void main(String[] args) {
        double x = 0, y1 = 1, y2 = 0, h = 0.1;
        int pasos = 10;

        for (int i = 0; i < pasos; i++) {
            System.out.printf("x=%.2f, y1=%.5f, y2=%.5f%n", x, y1, y2);

            double k1 = h * f1(x, y1, y2);
            double l1 = h * f2(x, y1, y2);

            double k2 = h * f1(x + h/2, y1 + k1/2, y2 + l1/2);
            double l2 = h * f2(x + h/2, y1 + k1/2, y2 + l1/2);

            double k3 = h * f1(x + h/2, y1 + k2/2, y2 + l2/2);
            double l3 = h * f2(x + h/2, y1 + k2/2, y2 + l2/2);

            double k4 = h * f1(x + h, y1 + k3, y2 + l3);
            double l4 = h * f2(x + h, y1 + k3, y2 + l3);

            y1 += (k1 + 2*k2 + 2*k3 + k4) / 6;
            y2 += (l1 + 2*l2 + 2*l3 + l4) / 6;
            x += h;
        }
    }

    static double f1(double x, double y1, double y2) {
        return y2; // Ejemplo: y1' = y2
    }

    static double f2(double x, double y1, double y2) {
        return -y1; // Ejemplo: y2' = -y1 → y1'' = -y1 (oscilador armónico)
    }
}</code></pre>

**Casos de prueba**
![alt text](image-2.png)

</div>

<h2> Conclusión</h2>
<p>
  Los métodos numéricos para EDOs permiten resolver problemas donde las soluciones analíticas no son factibles. Elegir entre métodos de un paso, pasos múltiples o para sistemas dependerá del tipo de problema y precisión requerida.
</p>

</body>
</html>
