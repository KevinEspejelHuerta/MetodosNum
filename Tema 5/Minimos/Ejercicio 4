import org.apache.commons.math3.fitting.PolynomialCurveFitter;
import org.apache.commons.math3.fitting.WeightedObservedPoints;

public class M4 {
    public static double[] regresionPolinomial(double[] x, double[] y, int grado) {
        WeightedObservedPoints points = new WeightedObservedPoints();
        for (int i = 0; i < x.length; i++) {
            points.add(x[i], y[i]);
        }
        return PolynomialCurveFitter.create(grado).fit(points.toList());
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {2.1, 3.9, 10.2, 15.8, 24.9};
        double[] coeficientes = regresionPolinomial(x, y, 2);
        
        System.out.printf("Ecuación: y = %.2f + %.2fx + %.2fx²\n", 
            coeficientes[0], coeficientes[1], coeficientes[2]);
        // Ejemplo: y = 0.57 + 0.45x + 0.92x²
    }
}