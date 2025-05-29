package Pasos_Multiples;

import java.util.function.DoubleUnaryOperator;

public class PM1 {
    public static double[] resolver(DoubleUnaryOperator derivada, 
                                  double y0, double t0, double tf, double h) {
        // Primer paso con Runge-Kutta
        double y1 = y0 + h * derivada.applyAsDouble(y0);
        
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        y[1] = y1;

        for (int i = 2; i <= pasos; i++) {
            y[i] = y[i-1] + h * (1.5 * derivada.applyAsDouble(y[i-1]) - 0.5 * derivada.applyAsDouble(y[i-2]));
        }
        return y;
    }

    public static void main(String[] args) {
        DoubleUnaryOperator derivada = y -> -2 * y; // dy/dt = -2y
        double[] solucion = resolver(derivada, 1.0, 0.0, 2.0, 0.1);
        System.out.println("Adams-Bashforth (2 pasos) en t=2: " + solucion[solucion.length - 1]);
    }
}