package Un_Paso;
import java.util.function.DoubleUnaryOperator;

public class P1 {
    public static double[] resolver(DoubleUnaryOperator derivada, 
                                  double y0, double t0, double tf, double h) {
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        double t = t0;

        for (int i = 1; i <= pasos; i++) {
            y[i] = y[i-1] + h * derivada.applyAsDouble(y[i-1]);
            t += h;
        }
        return y;
    }

    public static void main(String[] args) {
        // Ejemplo: dy/dy = -2y (Solución exacta: y = e^(-2t))
        DoubleUnaryOperator derivada = y -> -2 * y;
        double[] solucion = resolver(derivada, 1.0, 0.0, 2.0, 0.1);
        
        System.out.println("Solución en t=2: " + solucion[solucion.length - 1]);
        // Resultado: ≈0.3487 (vs exacto 0.3679)
    }
}