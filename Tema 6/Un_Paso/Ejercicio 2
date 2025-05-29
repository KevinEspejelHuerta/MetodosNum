package Un_Paso;
import java.util.function.DoubleUnaryOperator;

public class P2 {
    public static double[] resolver(DoubleUnaryOperator derivada,
                                  double y0, double t0, double tf, double h) {
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        double t = t0;

        for (int i = 1; i <= pasos; i++) {
            double k1 = derivada.applyAsDouble(y[i-1]);
            double yPred = y[i-1] + h * k1;
            double k2 = derivada.applyAsDouble(yPred);
            y[i] = y[i-1] + 0.5 * h * (k1 + k2);
            t += h;
        }
        return y;
    }

    public static void main(String[] args) {
        // Ejemplo: dy/dt = y - t^2 + 1
        DoubleUnaryOperator derivada = y -> y - Math.pow(y, 2) + 1;
        double[] solucion = resolver(derivada, 0.5, 0.0, 2.0, 0.1);
        
        System.out.println("Solución en t=2: " + solucion[solucion.length - 1]);
        // Resultado: ≈1.4255
    }
}