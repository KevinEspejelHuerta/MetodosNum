package Pasos_Multiples;

import java.util.function.DoubleUnaryOperator;

public class PM4 {
    public static double[] resolver(DoubleUnaryOperator derivada, 
                                  double y0, double t0, double tf, double h) {
        // Primer paso con Euler implícito
        double y1 = y0 / (1 + 2*h); // Para dy/dt = -2y
        
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        y[0] = y0;
        y[1] = y1;

        for (int i = 2; i <= pasos; i++) {
            // Fórmula BDF2: (3y_n - 4y_{n-1} + y_{n-2})/(2h) = f(t_n, y_n)
            y[i] = (4*y[i-1] - y[i-2] + 2*h*derivada.applyAsDouble(y[i])) / 3;
        }
        return y;
    }

    public static void main(String[] args) {
        DoubleUnaryOperator derivada = y -> -y; // dy/dt = -y
        double[] solucion = resolver(derivada, 1.0, 0.0, 2.0, 0.1);
        System.out.println("BDF2 en t=2: " + solucion[solucion.length - 1]);
    }
}