package Pasos_Multiples;
import java.util.function.DoubleUnaryOperator;

public class PM2 {
    public static double[] resolver(DoubleUnaryOperator derivada, 
                                  double y0, double t0, double tf, double h) {
        // Primer paso con Runge-Kutta
        double y1 = y0 + h * derivada.applyAsDouble(y0);
        
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        y[1] = y1;

        for (int i = 2; i <= pasos; i++) {
            // Predictor (Adams-Bashforth)
            double yPred = y[i-1] + h * (1.5 * derivada.applyAsDouble(y[i-1]) - 0.5 * derivada.applyAsDouble(y[i-2]));
            // Corrector (Adams-Moulton)
            y[i] = y[i-1] + h * 0.5 * (derivada.applyAsDouble(yPred) + derivada.applyAsDouble(y[i-1]));
        }
        return y;
    }

    public static void main(String[] args) {
        DoubleUnaryOperator derivada = y -> y - Math.pow(y, 2); // dy/dt = y - y²
        double[] solucion = resolver(derivada, 0.5, 0.0, 2.0, 0.1);
        System.out.println("Adams-Moulton (2 pasos) en t=2: " + solucion[solucion.length - 1]);
    }
}