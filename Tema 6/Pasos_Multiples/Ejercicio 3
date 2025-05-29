package Pasos_Multiples;
import java.util.function.DoubleUnaryOperator;

public class PM3 {
    public static double[] resolver(DoubleUnaryOperator derivada, 
                                  double y0, double t0, double tf, double h) {
        // Inicialización con Runge-Kutta de 4 pasos
        double[] yInicial = RungeKutta4.resolver(derivada, y0, t0, t0 + 3*h, h);
        
        int pasos = (int) ((tf - t0) / h);
        double[] y = new double[pasos + 1];
        System.arraycopy(yInicial, 0, y, 0, 4);

        for (int i = 4; i <= pasos; i++) {
            // Predictor (Milne)
            double yPred = y[i-4] + 4*h/3 * (2*derivada.applyAsDouble(y[i-3]) 
                          - derivada.applyAsDouble(y[i-2]) + 2*derivada.applyAsDouble(y[i-1]));
            // Corrector (Simpson)
            y[i] = y[i-2] + h/3 * (derivada.applyAsDouble(y[i-2]) 
                   + 4*derivada.applyAsDouble(y[i-1]) + derivada.applyAsDouble(yPred));
        }
        return y;
    }

    public static void main(String[] args) {
        DoubleUnaryOperator derivada = y -> Math.sin(y); // dy/dt = sin(y)
        double[] solucion = resolver(derivada, 0.5, 0.0, 2.0, 0.1);
        System.out.println("Milne-Simpson en t=2: " + solucion[solucion.length - 1]);
    }
}