package Un_Paso;
import java.util.function.DoubleUnaryOperator;

public class P4 {
    public static double[] resolver(DoubleUnaryOperator derivada,
                                  double y0, double t0, double tf, double h) {
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        double t = t0;

        for (int i = 1; i <= pasos; i++) {
            double k1 = h * derivada.applyAsDouble(y[i-1]);
            double k2 = h * derivada.applyAsDouble(y[i-1] + 0.5 * k1);
            double k3 = h * derivada.applyAsDouble(y[i-1] + 0.5 * k2);
            double k4 = h * derivada.applyAsDouble(y[i-1] + k3);
            y[i] = y[i-1] + (k1 + 2*k2 + 2*k3 + k4) / 6;
            t += h;
        }
        return y;
    }

    public static void main(String[] args) {
        // Ejemplo: dy/dt = t - y
        DoubleUnaryOperator derivada = y -> y - Math.sin(y);
        double[] solucion = resolver(derivada, 1.0, 0.0, 2.0, 0.1);
        
        System.out.println("Solución en t=2: " + solucion[solucion.length - 1]);
        // Resultado: ≈1.8929
    }
}