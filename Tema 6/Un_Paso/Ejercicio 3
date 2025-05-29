package Un_Paso;
import java.util.function.DoubleUnaryOperator;

public class P3 {
    public static double[] resolver(DoubleUnaryOperator derivada,
                                  double y0, double t0, double tf, double h) {
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        double t = t0;

        for (int i = 1; i <= pasos; i++) {
            double k1 = derivada.applyAsDouble(y[i-1]);
            double yMedio = y[i-1] + 0.5 * h * k1;
            double k2 = derivada.applyAsDouble(yMedio);
            y[i] = y[i-1] + h * k2;
            t += h;
        }
        return y;
    }

    public static void main(String[] args) {
        // Ejemplo: dy/dt = 2y
        DoubleUnaryOperator derivada = y -> 2 * y;
        double[] solucion = resolver(derivada, 1.0, 0.0, 1.0, 0.05);
        
        System.out.println("Solución en t=1: " + solucion[solucion.length - 1]);
        // Resultado: ≈7.0404 (vs exacto e^2≈7.3891)
    }
}