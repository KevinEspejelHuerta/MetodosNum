import java.text.DecimalFormat;

public class M1 {
    public static double[] calcular(double[] x, double[] y) {
        if (x.length != y.length || x.length < 2) {
            throw new IllegalArgumentException("Datos insuficientes o inconsistentes");
        }

        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;
        int n = x.length;

        for (int i = 0; i < n; i++) {
            sumX += x[i];
            sumY += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
        }

        double pendiente = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
        double intercepto = (sumY - pendiente * sumX) / n;

        return new double[]{intercepto, pendiente}; // y = a + bx
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {1.2, 1.9, 3.2, 4.1, 5.0};
        double[] resultado = calcular(x, y);
        
        System.out.printf("Ecuación: y = %.4f + %.4fx\n", resultado[0], resultado[1]);
        // Ejemplo: y = 0.2600 + 0.9400x
    }
}