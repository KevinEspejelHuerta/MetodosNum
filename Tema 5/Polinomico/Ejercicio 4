import java.text.DecimalFormat;

public class P4 {
    public static double interpolar4Puntos(double[] x, double[] y, double xTarget) {
        if (x.length != 4 || y.length != 4) throw new IllegalArgumentException("Requiere 4 puntos");
        double resultado = 0;
        for (int i = 0; i < 4; i++) {
            double term = y[i];
            for (int j = 0; j < 4; j++) {
                if (i != j) term *= (xTarget - x[j])/(x[i] - x[j]);
            }
            resultado += term;
        }
        return resultado;
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 4, 5};
        double[] y = {0, 1, 8, 27};
        System.out.printf("y(3) = %.3f%n", interpolar4Puntos(x, y, 3)); // y(3) = 6.000
    }
}