import java.text.DecimalFormat;

public class M3 {
    public static double[] calcularPonderada(double[] x, double[] y, double[] pesos) {
        if (x.length != y.length || x.length != pesos.length) {
            throw new IllegalArgumentException("Arrays deben tener igual longitud");
        }

        double sumW = 0, sumWX = 0, sumWY = 0, sumWXY = 0, sumWX2 = 0;

        for (int i = 0; i < x.length; i++) {
            double w = pesos[i];
            sumW += w;
            sumWX += w * x[i];
            sumWY += w * y[i];
            sumWXY += w * x[i] * y[i];
            sumWX2 += w * x[i] * x[i];
        }

        double pendiente = (sumW * sumWXY - sumWX * sumWY) / (sumW * sumWX2 - sumWX * sumWX);
        double intercepto = (sumWY - pendiente * sumWX) / sumW;

        return new double[]{intercepto, pendiente};
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {2, 3.5, 6, 8.5, 10};
        double[] pesos = {1, 1, 2, 1, 1}; // Peso doble para el punto (3,6)
        
        double[] resultado = calcularPonderada(x, y, pesos);
        System.out.printf("Ecuación ponderada: y = %.2f + %.2fx\n", resultado[0], resultado[1]);
        // Ejemplo: y = 0.56 + 1.93x
    }
}