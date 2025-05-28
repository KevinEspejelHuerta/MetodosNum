# Tema-3
<h2 align = "center"> <font color = "darkorange" size = "+6"  font face = "bauhaus 93">  Indice </font> </h2>
<header> <font color = "red" size="+1" font face = "aharoni">
                <nav class="navegacion">
                    <ul class="Indice">
                       <li> <a href="#Descripción"> Descripción del Problemario </a> <br> </li>
                        <li> <a href="#Sobre la materia"> Sobre la materia </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Competencia de la Asignatura"> Competencia de la Asignatura </a> </li>
                                <li> <a href="#Competencia del tema"> Competencia del TEMA </a> </li>
                            </ul>
     <li> <a href="#Métodos numéricos para encontrar las raíces de ecuaciones que se encuentran en nuestro repositorio"> Sistemas de ecuaciones </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Eliminacion"> Eliminación-Gaussiana </a> </li>
                                <li> <a href="#Gauss"> Gauss-Jordan </a> </li>
                                <li> <a href="#Seidel"> Gauss-Seidel </a> </li> 
                                <li> <a href="#Jacobi"> Método de Jacobi </a> </li> 
                            </ul>
                    </ul>
                </nav>
            </font> </header>

# Descripción
En este documento vamos a ver varios ejercicios sobre los distintos metodos como lo son:
  <li>1.- Eliminación-Gaussiana</li>
  <li>2.- Gauss-Jordan</li>
  <li>3.- Gauss-Seidel</li>
  <li>4.- Jacobi</li>
  
# Sobre la materia 
<h2 align = "center"> <font  size = "+6" > <a name="Competencia de la Asignatura">Competencia de la asignatura</font></a> </h2>
Aplica los métodos numéricos para resolver problemas científicos y de ingeniería utilizando la computadora.
<h2 align = "center"> <font size = "+6"  > <a name="Competencia del tema">Competencia del tema</font> </a></h2>
Aplica los métodos numéricos con el objeto de solucionar ecuaciones mediante los métodos de intervalo e interpolación apoyada de un lenguaje de programación.  

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1 align = "center"> <font  font face = "bauhaus 93"> <a name="Sistemas de ecuaciones"> Sistemas de ecuaciones </font></a> </h1>

<h2 align = "center"> <font font face = "forte"><a name="Eliminacion">  1. Eliminación Gaussiana </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La eliminación gaussiana es un método utilizado en álgebra lineal para resolver sistemas de ecuaciones lineales de una manera sistemática y paso a paso. Este método consiste en llevar un sistema de ecuaciones a una forma matricial, convertir una matriz cuadrada en una matriz triangular superior equivalente a la original y luego resolver el sistema sustituyendo las variables en cada ecuación resultante:

<h3> <font font face = "arial">Pasos de la eliminación Gaussiana:</h3>
<h5>Formar la matriz aumentada:</h5> Combinar la matriz de coeficientes y el vector de términos independientes en una sola matriz aumentada.
<h5>Pivoteo parcial: </h5> Si es necesario, intercambiar filas para asegurar que el elemento en la posición de pivote sea el mayor en valor absoluto en su columna.
<h5>Escalonar la matriz: </h5> Comenzar con la primera fila y hacer ceros debajo del elemento de pivote, utilizando operaciones elementales de fila.
<h5>Repetir el proceso: </h5> Aplicar el mismo procedimiento a las filas restantes, avanzando hacia abajo y creando ceros debajo de los pivotes.
<h5>Sustitución hacia atrás: </h5> Una vez que la matriz está en forma triangular superior, resolver el sistema de ecuaciones resultante mediante sustitución hacia atrás, empezando por la última ecuación y despejando las incógnitas hacia arriba.
<h5>Verificar la solución: </h5> Sustituir las soluciones encontradas en las ecuaciones originales para comprobar si satisfacen todas las ecuaciones del sistema.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

import java.util.Scanner;

public class EliminacionGaussiana {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese el número de incógnitas: ");
        int n = scanner.nextInt();

        double[][] A = new double[n][n];
        double[] b = new double[n];

        System.out.println("Ingrese los elementos de la matriz de coeficientes:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                A[i][j] = scanner.nextDouble();
            }
        }

        System.out.println("Ingrese los valores del vector de términos independientes:");
        for (int i = 0; i < n; i++) {
            b[i] = scanner.nextDouble();
        }

        // Escalonar la matriz
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                double factor = A[j][i] / A[i][i];
                for (int k = i; k < n; k++) {
                    A[j][k] -= factor * A[i][k];
                }
                b[j] -= factor * b[i];
            }
        }

        // Sustitución hacia atrás
        double[] x = new double[n];
        for (int i = n - 1; i >= 0; i--) {
            x[i] = b[i];
            for (int j = i + 1; j < n; j++) {
                x[i] -= A[i][j] * x[j];
            }
            x[i] /= A[i][i];
        }

        System.out.println("La solución del sistema de ecuaciones es:");
         for (int i = 0; i < n; i++) {
            System.out.println("x[" + i + "] = " + x[i]);
        }
    }}
    
<h2 align = "center"> <font font face = "forte"> <a name="Gauss">  2.- Gauss-Jordan </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Gauss-Jordan es una variante del método de eliminación gaussiana que se utiliza para resolver sistemas de ecuaciones lineales. En este método, al igual que en la eliminación gaussiana, se busca llevar la matriz de coeficientes a una forma escalonada, pero con la diferencia de que se busca obtener una matriz escalonada reducida a su forma más simple, conocida como forma escalonada reducida por filas o forma canónica.

<h3> <font font face = "arial">Pasos del Método de Gauss Jordan: </h3>
<h5>Formar la Matriz Aumentada: </h5> Se comienza escribiendo el sistema de ecuaciones en forma matricial, creando una matriz aumentada que incluya tanto los coeficientes de las variables como los términos independientes.
<h5>Escalonar la Matriz: </h5>Se aplican operaciones elementales de fila para obtener ceros debajo de la diagonal principal y unos en la diagonal principal. Esto implica realizar operaciones como intercambiar filas, multiplicar filas por constantes y sumar múltiplos de unas filas a otras.
<h5>Reducir la Matriz a su Forma Escalonada Reducida: </h5>Se continúa escalonando la matriz hasta obtener una forma escalonada reducida, donde la parte de los coeficientes de las variables se convierte en una matriz identidad.
<h5>Obtener las Soluciones: </h5>Una vez se ha alcanzado la forma escalonada reducida, se leen las soluciones directamente de la matriz identidad. Cada fila de la matriz identidad corresponde a una variable del sistema de ecuaciones.
<h5>Verificar las Soluciones: </h5> Es importante comprobar las soluciones obtenidas sustituyéndolas en las ecuaciones originales para asegurarse de que satisfacen todas las ecuaciones del sistema.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

import java.util.Scanner;

public class GaussJordan {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese el número de incógnitas: ");
        int n = scanner.nextInt();

        double[][] A = new double[n][n];
        double[] b = new double[n];

        System.out.println("Ingrese los elementos de la matriz de coeficientes:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                A[i][j] = scanner.nextDouble();
            }
        }

        System.out.println("Ingrese los valores del vector de términos independientes:");
        for (int i = 0; i < n; i++) {
            b[i] = scanner.nextDouble();
        }

        // Escalonar la matriz
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i != j) {
                    double factor = A[j][i] / A[i][i];
                    for (int k = 0; k < n; k++) {
                        A[j][k] -= factor * A[i][k];
                    }
                    b[j] -= factor * b[i];
                }
            }
        }

        // Normalizar la matriz
        for (int i = 0; i < n; i++) {
            double divisor = A[i][i];
            for (int j = 0; j < n; j++) {
                A[i][j] /= divisor;
            }
            b[i] /= divisor;
        }

        System.out.println("Las soluciones del sistema de ecuaciones son:");
        for (int i = 0; i < n; i++) {
            System.out.println("x[" + i + "] = " + b[i]);
        }
    }}
    
<h2 align = "center"> <font font face = "forte"> <a name="Seidel">  3.- Gauss-Seidel </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Gauss-Seidel es una técnica iterativa utilizada para resolver sistemas de ecuaciones lineales. En este método, se mejora el método de Jacobi al utilizar las soluciones más recientes a medida que se calculan, en lugar de esperar a completar una iteración completa. Esto significa que las soluciones se actualizan en cada paso, lo que puede acelerar la convergencia del método.

<h3> <font font face = "arial">Pasos de Gauss-Seidel:</h3>
<h5>Inicialización de las Variables: </h5> Se comienza con una estimación inicial de las soluciones del sistema de ecuaciones lineales.
<h5>Iteración:</h5>Para cada ecuación en el sistema:
<li>Utilizar los valores más recientes de las variables ya calculadas.</li>
<li>Resolver la ecuación para encontrar una nueva estimación de la variable.</li>
<li>Actualizar el valor de la variable con la nueva estimación.</li>
<li>Repetir este proceso para todas las ecuaciones del sistema en cada iteración.</li>
<h5>Criterio de parada:</h5><li>Establecer un criterio de convergencia, como una tolerancia o un número máximo de iteraciones.</li>
<li>Verificar si se ha alcanzado la precisión deseada o el número máximo de iteraciones.</li>
<h5>Convergencia:</h5><li> Comprobar si el método converge hacia la solución del sistema de ecuaciones lineales.</li>
<li>Ajustar los parámetros, como la elección inicial y la precisión, si es necesario para mejorar la convergencia.</li>
<h5>Obtencion de soluciones:</h5> <li>Una vez que se alcanza la convergencia, las soluciones obtenidas en la última iteración se consideran como las soluciones aproximadas del sistema de ecuaciones lineales.</li>
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

 import java.util.Scanner;

public class GaussSeidel {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese el número de incógnitas: ");
        int n = scanner.nextInt();

        double[][] A = new double[n][n];
        double[] b = new double[n];
        double[] x = new double[n];
        double[] xAnterior = new double[n];

        System.out.println("Ingrese los elementos de la matriz de coeficientes:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                A[i][j] = scanner.nextDouble();
            }
        }

        System.out.println("Ingrese los valores del vector de términos independientes:");
        for (int i = 0; i < n; i++) {
            b[i] = scanner.nextDouble();
        }

        System.out.println("Ingrese las aproximaciones iniciales:");
        for (int i = 0; i < n; i++) {
            x[i] = scanner.nextDouble();
        }

        double epsilon = 0.0001;
        int iteracionesMaximas = 1000;
        int iteracion = 0;

        while (iteracion < iteracionesMaximas) {
            for (int i = 0; i < n; i++) {
                xAnterior[i] = x[i];
            }

            for (int i = 0; i < n; i++) {
                double suma = 0.0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * x[j];
                    }
                }
                x[i] = (b[i] - suma) / A[i][i];
            }

            double error = 0.0;
            for (int i = 0; i < n; i++) {
                error += Math.abs(x[i] - xAnterior[i]);
            }

            if (error < epsilon) {
                break;
            }

            iteracion++;
        }

        System.out.println("Las soluciones del sistema de ecuaciones son:");
        for (int i = 0; i < n; i++) {
            System.out.println("x[" + i + "] = " + x[i]);
        }
    }}
    
<h2 align = "center"> <font font face = "forte"> <a name="Jacobi">  4. Jacobi </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Jacobi es un algoritmo iterativo utilizado para resolver sistemas de ecuaciones lineales. En este método, se descompone la matriz de coeficientes del sistema en una suma de una matriz diagonal y dos matrices complementarias. Luego, se utiliza esta descomposición para iterar y encontrar soluciones aproximadas para el sistema de ecuaciones.

<h3> <font font face = "arial">Pasos del método de Jacobi:</h3>
<h5>Descomposición de la matriz: </h5><li> Descomponer la matriz de coeficientes del sistema en una matriz diagonal 
D y dos matrices complementarias L y U, de forma que = ++A=D+L+U, donde:</li>
<li>D es la matriz diagonal que contiene los elementos diagonales de A.
<li>L es la matriz triangular inferior con ceros en la diagonal.</li>
<li>U es la matriz triangular superior con ceros en la diagonal.</li>
<h5>Inicialización: </h5><li>Inicializar un vector de soluciones inicial x(0).</li>
<li>Establecer un criterio de convergencia, como una tolerancia ϵ o un número máximo de iteraciones.</li>
<h5>Iteración: </h5><li>Establecer un criterio de convergencia, como una tolerancia o un número máximo de iteraciones.</li>
<li>Verificar si se ha alcanzado la precisión deseada o el número máximo de iteraciones.</li>
<h5>Criterio de Parada: </h5><li>Verificar si se ha alcanzado la convergencia comparando la diferencia entre las soluciones actuales y las anteriores con la tolerancia establecida.</li>
<li>Detener las iteraciones si se cumple el criterio de convergencia o se alcanza el número máximo de iteraciones.</li>
<h5>Obtencion de soluciones:</h5> <li>Las soluciones aproximadas obtenidas en la última iteración se consideran como las soluciones del sistema de ecuaciones lineales.</li>
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

import java.util.Scanner;

public class Jacobi {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese el número de incógnitas: ");
        int n = scanner.nextInt();

        double[][] A = new double[n][n];
        double[] b = new double[n];
        double[] x = new double[n];
        double[] xAnterior = new double[n];

        System.out.println("Ingrese los elementos de la matriz de coeficientes:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                A[i][j] = scanner.nextDouble();
            }
        }

        System.out.println("Ingrese los valores del vector de términos independientes:");
        for (int i = 0; i < n; i++) {
            b[i] = scanner.nextDouble();
        }

        System.out.println("Ingrese las aproximaciones iniciales:");
        for (int i = 0; i < n; i++) {
            x[i] = scanner.nextDouble();
        }

        double epsilon = 0.0001;
        int iteracionesMaximas = 1000;
        int iteracion = 0;

        while (iteracion < iteracionesMaximas) {
            for (int i = 0; i < n; i++) {
                xAnterior[i] = x[i];
            }

            for (int i = 0; i < n; i++) {
                double suma = 0.0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * xAnterior[j];
                    }
                }
                x[i] = (b[i] - suma) / A[i][i];
            }

            double error = 0.0;
            for (int i = 0; i < n; i++) {
                error += Math.abs(x[i] - xAnterior[i]);
            }

            if (error < epsilon) {
                break;
            }

            iteracion++;
        }

        System.out.println("Las soluciones del sistema de ecuaciones son:");
        for (int i = 0; i < n; i++) {
            System.out.println("x[" + i + "] = " + x[i]);
        }
    }}
    
Realizado por:

  <li>Kevin Espejel Huerta  </li>
