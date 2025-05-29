import java.text.DecimalFormat;

public class R1 {
    public static double[] calcular(double[] x, double[] y) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        
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
        double[] y = {2, 4, 5, 4, 6};
        
        double[] coeficientes = calcular(x, y);
        System.out.printf("Ecuación: y = %.3f + %.3fx\n", coeficientes[0], coeficientes[1]);
        // Ejemplo: y = 1.4000 + 0.8000x
    }
}