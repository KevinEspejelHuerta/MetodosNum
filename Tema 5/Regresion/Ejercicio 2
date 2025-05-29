import java.text.DecimalFormat;

public class R2 {
    public static void analizar(double[] x, double[] y) {
        double[] coef = RegresionLinealSimple.calcular(x, y);
        double a = coef[0], b = coef[1];
        
        double ssTotal = 0, ssResidual = 0;
        double yPromedio = 0;
        for (double yi : y) yPromedio += yi;
        yPromedio /= y.length;
        
        for (int i = 0; i < y.length; i++) {
            double yPred = a + b * x[i];
            ssTotal += Math.pow(y[i] - yPromedio, 2);
            ssResidual += Math.pow(y[i] - yPred, 2);
        }
        
        double r2 = 1 - (ssResidual / ssTotal);
        
        System.out.printf("Ecuación: y = %.3f + %.3fx\n", a, b);
        System.out.printf("R² = %.3f\n", r2);
        // Ejemplo: R² = 0.6000 (para los datos anteriores)
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {2, 4, 5, 4, 6};
        analizar(x, y);
    }
}